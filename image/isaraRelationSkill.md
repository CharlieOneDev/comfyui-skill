《星穹防卫线》通用剧情关系编译 Skill
0. Skill 目的

本 Skill 不负责直接编写最终视频 Prompt。

本 Skill 的唯一职责，是把用户以自然语言、剧情摘要、分镜描述、对白、动作说明、视觉想法或零散片段提供的内容，转换为结构明确、时间连续、空间清楚、因果可执行、状态可追踪的视频关系描述。

最终流程：

用户自然语言剧情 → 剧情事实提取 → Entity Map → State Map → Event Map → Temporal Relations → Causal Relations → Spatial Relations → Interaction Relations → Perception / Reveal Relations → Visual / Physical Relations → Camera / Audio Relations → Continuity Check → Relation Sheet → isaraskill.md → H3 Prompt

本 Skill 不追求把剧情写得更加文学化，也不追求增加大量描述；目标是减少关系歧义、状态跳变、因果缺失、空间冲突和动作压缩。

1. 第一原则：不要直接改写剧情

用户说：

男队员回头看到一个怪物。

不得直接改写成：

The soldier turns around and sees a terrifying creature.

必须先解析成：

Entity： Soldier / Creature
Initial State： Soldier facing forward / Creature not directly visible
Event： Soldier turns
Perception Relation： Soldier's visual attention reaches Creature
Result State： Soldier is facing the creature

只有完成关系编译后，才能进入 Prompt 生成阶段。

核心原则：

剧情不是 Prompt，剧情必须先经过关系编译。

2. 第二原则：剧情不等于全部事实

用户提供的信息分成三类。

Explicit Fact： 用户明确说出的事实，必须保留。

Necessary Inference： 为了让动作、空间或因果可以成立而必须推导的信息，可以补充。

Optional Interpretation： 不影响剧情成立、只是模型可以自由决定的信息，不应擅自写死。

例如用户说：

A 走到门口，然后打开门。

可以推导：

A 必须先接近门，然后才能打开门。

但不能擅自增加：

A 先看了一眼手机。

3. 第三原则：允许补齐“执行逻辑”，禁止创造“剧情事实”

允许补齐：

动作完成所需的中间状态
基础空间关系
动作方向
视觉连续性
物理事件所需的最小条件
状态变化顺序

禁止无授权创造：

新角色
新对白
新剧情事件
新动机
新道具
新世界观
新重大视觉揭示

例如：

“角色拿起杯子。”

可以推导“手靠近杯子 → 抓取 → 抬起”。

但不能推导“角色先喝了一口”。

4. Entity Map

首先识别所有会影响剧情的视频实体。

实体类型不限于人物。

统一使用：

PERSON / CREATURE / OBJECT / ENVIRONMENT / LOCATION / CAMERA / LIGHT / SOUND SOURCE / ABSTRACT FORCE / DERIVED PHENOMENON / UI / CROWD / VEHICLE / EFFECT

实体不是越多越好。

只有真正影响剧情、动作、空间或视觉结果的对象才建立 Entity。

5. Entity 不等于视觉元素

一个剧情中的“东西”可能是：

实际实体： 人、怪物、枪、门。

环境实体： 墙、地板、房间、街道。

抽象实体： 精神控制、幻觉、重力异常。

派生现象： 影子、倒影、烟尘中的轮廓、镜像、屏幕映像。

感知结果： 角色“看到的东西”，不一定等于真实存在的东西。

因此不得机械地把所有名词都当作独立 Subject。

6. Derived Phenomenon 模块

以下内容默认作为可选模块，只有剧情需要时启用：

Shadow
Reflection
Mirror Image
Projection
Hologram
Screen Image
Smoke Silhouette
Water Reflection
Light Pattern
Echo
Distortion
Visual Illusion

基本关系：

Source Entity → Mechanism → Derived Phenomenon → Destination

例如：

Person → blocks light → Shadow → Wall

或者：

Person → reflected by mirror → Mirror Image → Mirror

这样可以避免把“影子”“倒影”等错误地当成第二个独立角色。

7. State Map

每个主要实体必须建立与剧情有关的当前状态。

状态不是角色简介。

状态应该描述：

Position / Orientation / Posture / Visibility / Attention / Possession / Interaction / Emotional State / Physical State / Scene State

例如：

Soldier： facing forward / standing / visible / alert

Door： closed

Weapon： in soldier's right hand

剧情推进后：

Soldier： facing backward / tense

Door： open

状态只记录会影响后续事件的内容。

8. Initial State

每段剧情必须先回答：

事件开始之前，世界是什么状态？

例如：

A stands near the door. The door is closed.

而不是直接从：

A opens the door.

开始。

因为 Initial State 是后续动作是否成立的基础。

9. Event Atom

把剧情拆成最小的“可观察事件”。

例如：

“A 快速跑过去拿起枪。”

拆成：

A1：A begins running.
A2：A reaches the weapon.
A3：A stops or stabilizes sufficiently to interact.
A4：A grasps the weapon.
A5：A lifts the weapon.

不要求每个微动作都进入最终 Prompt。

它们首先用于关系分析。

10. Major Event 与 Micro-Beat 分层

剧情同时存在两个层级。

Major Event： 用户真正关心的事件。

Micro-Beat： 让 Major Event 能够连续发生的中间状态。

例如：

Major Event：角色回头。

内部可以拆成：

头部开始转动 → 视线改变 → 肩部跟随 → 躯干转动 → 最终停住。

但最终 H3 是否需要全部写出来，要交给 isaraskill.md 根据复杂度决定。

因此：

plot2relation 要完整分析，不等于最终 Prompt 必须完整描述。

11. Temporal Relation

所有事件建立时间关系。

基本关系：

BEFORE / AFTER / DURING / OVERLAP / SIMULTANEOUS / CONTINUOUS / INTERRUPTED / REPEATED

例如：

A turns before B speaks。

A reaches for the door while looking at B。

The alarm and the red light occur simultaneously。

12. Causal Relation

时间顺序和因果关系必须分开。

例如：

A happens before B

不代表：

A causes B

建立：

CAUSES / ENABLES / TRIGGERS / PREVENTS / INTERRUPTS / RESULTS_IN / MAINTAINS

例如：

Character pulls the trigger → causes gunshot

Character hears noise → triggers turning reaction

Wall blocks movement → prevents character from entering

13. Action Chain

任何关键动作都使用：

Initial State → Action Onset → Continuous Change → Interaction / Reaction → Final State

例如：

Facing forward → begins turning → turns head and torso → gaze reaches rear area → fully facing backward

这样可以防止模型只生成动作的“起点和终点”。

14. Action Actor

每个主要动作必须明确：

WHO performs the action

不能：

“the weapon rises”

而不知道是谁导致它上升。

应判断是：

Character raises weapon

还是：

External force moves weapon

还是：

Weapon fires automatically

动作主体不同，生成结果会完全不同。

15. Action Target

复杂动作同时明确：

Actor → Action → Target

例如：

Soldier → reaches for → weapon

Soldier → opens → door

Creature → strikes → wall

这样可以避免模型把相邻物体错误绑定。

16. Motion Source

把运动来源分开：

Subject Motion / Object Motion / Environment Motion / Camera Motion / External Force

例如：

Subject: soldier turns.

Object: door moves.

Environment: smoke drifts.

Camera: remains static.

External Force: invisible force pushes the weapon.

这个区分对于所有动作场景都有效，不只是特殊视觉效果。

17. Spatial Graph

所有需要空间关系的剧情建立空间图。

至少检查：

LEFT / RIGHT / FRONT / BEHIND / ABOVE / BELOW / NEAR / FAR / INSIDE / OUTSIDE / BETWEEN / FACING / TOUCHING / BLOCKING / CONTAINING

例如：

A is in front of B.

C is between A and B.

A faces B.

18. Spatial Anchor

复杂场景先选择一个稳定空间 Anchor。

可以是：

Wall
Floor
Door
Vehicle
Table
Room
Corridor
Building
Horizon
Camera

然后让其他实体相对于 Anchor 定位。

例如：

Wall = spatial anchor

Soldier = 1 meter in front of wall

Object = on floor near soldier

这样比让每一个物体都独立描述更稳定。

19. Spatial Persistence

如果剧情连续发生在同一空间：

除非剧情明确改变，否则默认保持：

空间布局
相对位置
地面关系
墙体关系
物体关系
Camera side

变化必须有事件支持。

20. Perception Chain

遇到：

看到
听到
注意到
发现
意识到
闻到
感受到
察觉异常

不要直接当作普通动作。

建立：

External Event → Sensory Input → Perception → Interpretation → Reaction

例如：

Unknown movement occurs → soldier sees it → realizes something is behind him → turns

这样可以避免：

“发现怪物”

被模型直接解释为：

“怪物已经出现在镜头中”。

21. Knowledge State

剧情中的：

真实存在

与：

角色知道什么

必须分开。

例如：

Creature exists = TRUE

但：

Soldier knows creature exists = FALSE

直到：

Perception Event → Knowledge State changes to TRUE

这个模块对悬疑、惊悚、推理、谍战尤其重要。

22. Reveal Logic

所有：

隐藏 → 暗示 → 发现 → 揭示

的剧情，都必须明确：

What is hidden?

What is visible before discovery?

What causes discovery?

What becomes visible afterward?

What remains hidden?

例如：

怪物一直在房间里，但直到角色看到镜子才发现。

这里：

Monster = always present

Monster direct visibility = false

Mirror reflection = visible

Character knowledge = false → true

23. Ambiguity Preservation

剧情如果故意保持未知：

不要替用户把未知内容解释清楚。

例如：

“他看到了某种恐怖的东西。”

不要擅自决定：

是一只克苏鲁怪物。

除非用户已经明确。

可以编译成：

Unknown Presence

并继续处理：

Character turns → perception occurs → reaction

但保持对象身份未知。

这对于悬疑、恐怖、梦境、伏笔非常重要。

24. Reality Layer

复杂剧情可建立：

REAL / PERCEIVED / HALLUCINATED / RECORDED / REFLECTED / PROJECTED / DREAM / MEMORY

因为：

“角色看到一个人”

不一定意味着：

“这个人真实存在于当前空间。”

例如：

Reality Layer = real room

Perception Layer = hallucinated creature

Visual Layer = reflected figure

这些不能混为一谈。

25. Physical / Visual Relation

这一模块也是可选模块。

只有视觉结果依赖物理或几何关系时启用。

例如：

Shadow / Reflection / Water / Glass / Smoke / Fire / Cloth / Collision / Destruction / Weight / Gravity / Projectile / Lighting

基本结构：

Source → Mechanism → Result

例如：

Light → blocked by object → shadow

Glass → refracts light → distorted background

Object hits wall → wall fractures

26. Physical Constraint

只记录决定画面结果的物理关系。

不要把 Prompt 编译成物理学论文。

例如：

heavy object falls downward

足够。

不需要自动写：

gravitational acceleration = 9.81 m/s²

除非用户特别要求。

27. Interaction Graph

人物与物体、人物与人物之间建立：

LOOKS_AT / TOUCHES / HOLDS / PUSHES / PULLS / FOLLOWS / CHASES / AVOIDS / ATTACKS / SUPPORTS / BLOCKS / HANDS_TO / TAKES_FROM

复杂互动尤其需要明确双方。

例如：

A grabs B's wrist

不是：

A moves toward B

因为后者没有表达 Interaction。

28. Multi-Character Logic

多人场景必须区分：

谁行动

谁反应

谁保持不动

谁负责下一事件

例如：

A stands still. B walks toward A. A watches B.

不要把三个人都默认成 active agents。

29. Simultaneous Events

如果两个事件同时发生：

明确：

A and B happen simultaneously

例如：

The alarm starts while the soldier turns around.

不要因为叙事句子的先后顺序，而错误理解为：

A 完成后才发生 B。

30. Interruptions

剧情中：

A 正在做 X，突然发生 Y。

必须表示：

X begins → X is interrupted → Y occurs → new state

例如：

Soldier reaches for the weapon → alarm interrupts him → he turns toward the alarm.

不要让模型把两个动作完整执行后才进入 Y。

31. Transformation

对于：

变身
融合
崩坏
爆炸
生长
消失
穿衣
脱衣
机械变形

建立：

Before State → Trigger → Transformation Process → After State

不要只写：

“The character transforms.”

32. Destruction / Creation

对于物体损坏或生成：

Before → Trigger → Transformation → Result

例如：

Wall intact → creature strikes wall → cracks spread → wall breaks open

这样可以防止模型直接从：

完整墙

跳到：

已经破墙。

33. Environmental Response

如果一个事件会影响环境：

建立：

Primary Event → Secondary Effect

例如：

Door opens → light from room spills into corridor

Explosion → dust expands → visibility decreases

Creature lands → floor vibrates

这样可以控制副作用，而不是让模型随机增加环境变化。

34. Camera Relation

Camera 作为独立系统处理。

至少确定：

Camera Position / View Direction / Framing / Movement / Cut

Camera 不应该被当成普通角色。

35. Camera 不得替代剧情

先确定：

事件发生什么

再决定：

镜头怎么观察事件

不要为了“电影感”修改剧情的空间关系。

36. Audio Relation

声音分成：

Diegetic Source / Environmental Sound / Dialogue / Reaction Sound / Non-diegetic Music

其中：

Dialogue → Speaker

Sound Effect → Source Event

Music → Scene

例如：

Gun fires → gunshot

而不是：

“dramatic sound occurs.”

37. Continuity Check

每个事件之后检查：

Position

Orientation

Possession

Visibility

Posture

Object State

Knowledge State

Environment State

Camera State

是否保持连续。

38. State Ledger

对于复杂剧情，每个重大时间节点建立一个简短状态快照：

T0：Initial State

T1：After Event 1

T2：After Event 2

不要写成完整 Prompt，只记录状态变化。

例如：

T0：Door closed / A outside

T1：Door opened / A at doorway

T2：A inside / Door remains open

39. Failure Mode Prediction

关系编译结束以后，主动预测模型最容易犯的错误。

格式：

Failure → Cause → Missing Relation → Protection

例如：

Creature appears too early → visibility state unspecified → direct visibility relation missing → keep creature unseen until reveal

或者：

Object moves by itself → actor relation unclear → action ownership missing → explicitly assign actor

或者：

Two shadows behave independently → derived phenomenon undefined → projection relation missing → bind both to common physical source

40. Minimal Correction Principle

发现关系缺失时，只增加解决问题所需要的最小信息。

不要因为发现：

空间关系不明确

就突然加入一大段环境设定。

应该只补：

A stands in front of B.

41. Relation Priority

当信息很多时，优先级固定为：

Identity → State → Causality → Temporal Order → Spatial Relation → Interaction → Perception → Physical Relation → Camera → Audio → Optional Detail

42. Relation Compression

多个事件如果共享同一关系，可以合并。

例如：

A walks toward B and reaches B.

如果中间没有剧情意义，可以编译成：

A approaches B and stops within arm's reach.

不要为了“完整”制造大量无意义 Micro-Beat。

43. 用户提供分镜时

如果用户已经提供：

Shot
Camera
Duration
Framing
Cut

不要重新设计。

只检查：

剧情关系是否与分镜一致。

如果存在冲突：

优先指出冲突，而不是偷偷修改用户分镜。

44. 用户只提供一句剧情时

不要要求用户先写完整分镜。

Skill 应该自动完成：

Entity → Initial State → Major Events → Temporal Chain → Causal Chain → Spatial Relations → State Changes

然后将不确定部分标记为：

UNSPECIFIED

而不是擅自创造。

45. 用户提供大量剧情时

不要逐字解释。

先压缩成：

Scene Goal + Entities + States + Events + Relations + Timeline + Failure Risks

最终 Relation Sheet 应尽可能比原剧情更短、更结构化。

46. Relation Sheet

本 Skill 的最终输出不是 Prompt，而是：

RELATION SHEET

推荐结构：

Scene Goal：这一段真正要表现什么。

Entities：有哪些重要实体。

Initial State：开始时世界是什么状态。

Event Chain：发生了哪些核心事件。

Temporal Relations：哪些事件先后/同时。

Causal Relations：谁导致谁。

Spatial Relations：谁在哪里、相对谁在哪里。

Interaction Relations：谁操作谁。

Perception / Knowledge：谁看到、知道、误解什么。

Physical / Visual Relations：如果需要，说明现象如何产生。

Final State：最后停在哪里。

Camera Logic：镜头承担什么观察任务。

Audio Logic：声音来自什么事件。

Continuity Risks：最可能失败的关系。

47. 不是所有模块都必须启用

这是这个 Skill 和我上一版最大的区别。

简单剧情：

只需要：

Entity + State + Event + Temporal + Causal

多人对话：

增加：

Interaction + Speaker / Perception

动作戏：

增加：

Action Chain + Motion Source + Spatial

悬疑：

增加：

Knowledge + Perception + Reveal + Ambiguity

影子/倒影/幻觉：

增加：

Derived Visual + Reality Layer + Physical Relation

爆炸/变形/破坏：

增加：

Transformation + Environmental Response

因此这个 Skill 是一个：

模块化编译器，而不是固定模板。

48. 最终编译规则

无论剧情是什么，都至少回答：

谁？

开始时什么状态？

发生什么？

谁导致什么？

什么时候发生？

在哪里发生？

谁与谁发生关系？

发生之后状态变成什么？

然后再问：

是否存在感知问题？

是否存在物理/视觉派生关系？

是否存在 Camera 问题？

是否存在 Audio 问题？

模型最容易错在哪里？

49. 最终原则

整个 Skill 可以浓缩成一句话：

不要把人类的剧情直接翻译成 AI Prompt；先把人类剧情编译成一个“可观察、可定位、可排序、可因果追踪、可状态更新”的事件系统，再把这个事件系统转换成视频 Prompt。
