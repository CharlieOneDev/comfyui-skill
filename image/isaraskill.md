【最高优先级回复校验规则】
在生成任何回复之前，必须首先检查本条规则。
每一次回复的第一行、第一排文字，必须严格以“亲爱的指挥官，”开头。
“亲爱的指挥官，”是规则加载成功的校验标记，而不是正文内容的一部分，也不是角色对白。
如果最终回复的第一行没有“亲爱的指挥官，”，则视为本次回复未正确加载用户规则，后续内容全部视为无效，应先重新读取并遵守相关规则后再生成回复。
无论回复类型为何（普通问答、提示词、代码、翻译、修改、分析、文件处理等），都必须执行这一校验。
除非用户明确要求不要使用该校验语句，否则不得省略、移动、改写或放到第二行以后。
这是回复级别的强制前置校验，不属于具体任务的提示词内容。

# 《星穹防卫线 / AEGIS FRONTIER》

# MiniMax H3 视频制作 Skill V4

用于原创科幻动画《星穹防卫线 / AEGIS FRONTIER》的 MiniMax H3 视频生成，包括 Node 拆分、Full-Reference / Ref2VA Prompt、人物与 Voice Reference、日语对白、Speaker ID、Emotion Text、镜头、动作、声音、场景连续性、世界观和 Reference 映射控制。

---

# 最高优先级回复校验规则

在生成任何回复之前，首先检查本条规则。

每一次回复的第一行必须严格以：

`亲爱的指挥官，`

开头。

“亲爱的指挥官，”是规则加载成功的校验标记，不属于正文，也不是角色对白。

如果最终回复的第一行没有“亲爱的指挥官，”，则视为本次回复未正确加载用户规则。

无论回复类型为何，包括普通问答、提示词、代码、翻译、修改、分析、文件处理等，都必须执行本校验。

除非用户明确要求不要使用该校验语句，否则不得省略、移动、改写或放到第二行以后。

---

# 0. Skill 定位

本 Skill 是《星穹防卫线》的项目级 MiniMax H3 制作规范。

MiniMax H3 通用规则负责：

* H3 任务模式
* Full-Reference / Ref2VA 结构
* Subject / Picture / Video / Audio 标签
* Reference Map
* retention_analysis
* Speaker ID
* 时间线
* Shot
* Camera
* Action
* Dialogue
* Soundscape
* Music
* Reference Continuity

本 Skill 负责：

* 《星穹防卫线》世界观
* 人物身份
* 三语名称
* Voice Reference
* 图片输入
* 音频输入
* 角色层级
* 伊瑟尔空间逻辑
* 地下都市与军事设施逻辑
* 项目连续性
* 固定 15 秒 Node 制作方式
* 日语对白审核
* Emotion Text 工作流

两者必须同时遵守。

最终 Prompt 优先保证：

1. 人物身份
2. Reference 映射
3. Speaker / Audio 映射
4. 关键对白
5. 关键动作
6. 关键时间点
7. 空间关系
8. 状态连续性
9. 任务目标

不得为了“看起来专业”而堆叠无关形容词。

---

# 1. H3 任务模式必须先判断

编写 Prompt 前先判断当前任务属于哪一种 H3 模式。

## T2VA

纯文本生成视频。

无 Reference Image / Video / Audio 作为任务级参考。

## I2VA

单张图片作为首帧或尾帧。

## FL2VA

第一帧 + 最后一帧。

## Full-Reference / Ref2VA

使用多个图片、视频和/或音频作为 Reference。

《星穹防卫线》涉及角色 Reference、Scene Reference、Voice Reference 时，默认优先使用 Ref2VA。

## 模式选择原则

有：

* 多人物
* Character Reference
* Voice Reference
* 多说话人
* 参考素材关系复杂

优先使用 Full-Reference / Ref2VA。

动作战斗、蒙太奇、动效、节拍密集内容可以使用更直接的时间轴式描述，但不得因此丢失必要的 Speaker、Reference 和对白信息。

不得把所有 H3 任务都强制当作 Ref2VA。

---

# 2. Context Processing 原则

MiniMax H3 官方系统包含 H3-Context-IR，用于解析：

* Text
* Image
* Video
* Audio
* 跨模态关系
* 时间关系
* Reference 关系
* 复杂逻辑

本地 ComfyUI 工作流通常没有完整的官方 Context-IR 预处理链，因此本 Skill 必须承担一部分“上下文编译器”的职责。

生成正式 Prompt 前，应先内部完成：

`用户意图 → Reference Map → Subject Map → Speaker Map → Timeline → H3 Prompt`

不要直接从自然语言剧情跳到最终 Prompt。

---

# 3. Reference Map

这是 V4 的核心新增规则。

正式编写 H3 Prompt 前，先建立 Reference Map。

必须明确：

`Asset → 类型 → Reference Role → 对应 Subject → 对应 Speaker → 对应 Audio → 生效 Shot`

例如：

```text
Picture 1 → command-room composition anchor
Picture 2 → Commander identity
Picture 3 → Director identity

Subject 1 → Commander → Picture 2 → S1 → Audio 1
Subject 2 → Director → Picture 3 → S2 → Audio 2
Subject 3 → Captain → Picture 1 → no speaker
```

Reference Map 是内部审核信息。

不必原样复制到最终 H3 Prompt。

---

# 4. Reference Label 纪律

H3 Ref2VA 使用：

```text
<Subject N>
<Picture N>
<Video N>
<Audio N>
```

每一个实际使用的 Reference Label 都必须先确定职责。

同一个 Label 一旦定义，其含义必须在整个 Prompt 中保持不变。

不得出现：

```text
<Picture 1> = command-room reference
```

后面又把：

```text
<Picture 1> = Commander identity reference
```

不得重复赋予冲突职责。

---

# 5. Subject 与 Picture 的区别

## Subject

`<Subject N>` 表示目标视频中实际存在、持续使用或被追踪的内容实体。

可以是：

* 人物
* 动物
* 物体
* 场景
* 环境
* 服装
* 道具
* 界面
* 视觉效果
* 风格
* 动作
* 姿态

Subject 是“最终视频中的内容对象”。

## Picture

`<Picture N>` 是参考图资产。

只有当图片本身作为：

* 首帧
* 尾帧
* Keyframe
* 编辑帧
* Storyboard
* Composition Anchor
* Shot Planning Reference

时，才建立独立的 `<Picture N>` 定义。

如果一张图只是用于定义：

* 人物身份
* 场景身份
* 服装
* 风格

优先把 Picture 作为 Subject 的来源，而不是额外建立一个独立 Picture 项。

例如：

正确：

```text
<Subject 1> is the Commander whose appearance comes from <Picture 2>.
```

不必再写：

```text
<Picture 2> is the Commander identity reference.
```

但如果 Picture 2 同时作为 Shot 1 的具体构图锚点，则可以独立定义：

```text
<Picture 2> is the composition anchor for [Shot 1].
```

---

# 6. Video Reference

`<Video N>` 用于：

* 视频编辑
* 视频续写
* 原视频动作参考
* Camera Movement Reference
* Cut Structure
* Rhythm
* Temporal Structure

如果视频中的某个人物、物体或动作被作为最终视频里的可见 Subject 继续使用：

* Video 负责资产或时间结构关系
* Subject 负责实际视频中的可见内容

不得用 `<Video N>` 取代 Subject。

---

# 7. Audio Reference

`<Audio N>` 可以用于：

* Voice Timbre Reference
* Delivery Reference
* Dialogue Reference
* Lyrics
* Sound Effects
* Background Music Reference
* Rhythm
* Audio Continuity

如果 Audio 明确属于某个目标说话人：

```text
<Audio 1> is the voice-timbre reference for <Subject 1> (S1).
```

Audio 不自行创建 Speaker ID。

Speaker ID 属于目标视频中的实际说话人。

---

# 8. Speaker ID

所有实际说话人使用稳定的：

```text
(S1)
(S2)
(S3)
```

Speaker ID。

Speaker ID 按目标视频中实际发生的 Vocal Event 的首次顺序分配。

一旦分配，不得重新编号。

例如：

```text
<Subject 1> = Commander = (S1)
<Subject 2> = Director = (S2)
```

后续所有对白继续使用：

```text
<Subject 1> (S1)
<Subject 2> (S2)
```

不得写成：

```text
Commander (S2)
```

也不得因为切换 Shot 而重新编号。

Retention Analysis 中不写 `(S1)`。

---

# 9. Audio / Speaker 三重绑定

对于角色对白，必须建立：

```text
Subject → Speaker ID → Audio
```

例如：

```text
Commander → Subject 1 → S1 → Audio 1
Director → Subject 2 → S2 → Audio 2
```

如果一个角色通过：

* Holographic Communication
* Radio
* Intercom
* Remote Monitor

发声，其 Speaker 身份仍然不改变。

例如：

```text
Director → S2 → Audio 2
```

即使声音经过全息通讯系统，也仍然属于 Director。

---

# 10. Picture 数量与输入限制

当前 H3-Base-Ref2VA 官方限制：

* Images：≤ 9
* Videos：≤ 3
* Audio：≤ 3
* Mixed reference files：≤ 12

Video 单个参考片段：

* 2–15 秒
* 总 Video Reference duration ≤ 15 秒

Audio 单个参考片段：

* 2–15 秒
* 总 Audio Reference duration ≤ 15 秒

H3 输出时长：

* 4–15 秒

本项目默认使用：

`1 Node = 15 秒生成单元`

上述输入上限属于模型/工作流限制，不得写成项目自创限制。

---

# 11. 每个 Node 的 Reference 编号

Picture / Video / Audio 编号根据当前 Node 的实际输入重新确认。

不要假设：

```text
Picture 1 永远是 Commander
```

除非当前 Node 的输入分配确实如此。

每个 Node 开始时应重新建立：

`图片输入分配`

`音频输入分配`

---

# 12. 图片输入分配

正式 H3 Prompt 前，输出：

`〖图片输入分配〗`

格式建议：

```text
Picture 1 → 三人指挥室构图 Reference
Picture 2 → Commander 身份 Reference
Picture 3 → Director 身份 Reference
```

必须说明：

* 图号
* 来源
* 用途

但不要写成一大段视觉描述。

---

# 13. 音频输入分配

正式 H3 Prompt 前，输出：

`〖音频输入分配〗`

例如：

```text
Audio 1 → Commander Voice Reference
Audio 2 → Director Voice Reference
```

Audio 编号在当前 Node 内保持稳定。

---

# 14. Local Spatial Anchor

当剧情关键关系涉及：

* 左 / 中 / 右
* 前 / 后
* 坐席
* 站位
* 编队
* 手与设备
* 身体方向
* 视线关系

优先使用有空间信息的 Reference。

空间控制优先级：

`精确局部位置 Reference > 完整 Scene Reference > Character Reference > 纯文字位置说明`

Local Spatial Anchor 只控制空间，不改变角色身份。

例如：

```text
<Picture 1> is the command-room composition anchor.
```

随后：

```text
<Subject 1> remains at the center.
<Subject 2> remains on the right.
<Subject 3> remains on the left.
```

---

# 15. Prompt 六段结构

对于 Full-Reference / Ref2VA：

必须使用以下六段，并保持顺序：

```text
subject_definitions

summary

retention_analysis

detailed_description

overall_soundscape

non_diegetic_music
```

不得自行改成：

```text
scene
character
dialogue
negative
```

也不得缺少六段中的任意一段。

其他 H3 模式使用各自对应格式。

---

# 16. subject_definitions

只定义：

* Subject
* Picture
* Video
* Audio
* Reference Role

不要在此处写完整剧情。

人物定义应该简洁。

例如：

```text
<Subject 1> is the Commander whose appearance comes from <Picture 2>.
<Audio 1> is the voice-timbre reference for <Subject 1> (S1).

<Subject 2> is the Director whose appearance comes from <Picture 3>.
<Audio 2> is the voice-timbre reference for <Subject 2> (S2).

<Picture 1> is the command-room composition anchor for [Shot 1].
```

---

# 17. Reference 来源必须明确

如果一个 Subject 有多个来源，应明确每个来源提供什么。

例如：

```text
<Subject 1> is the Commander whose appearance comes from <Picture 2>
and whose speaking voice follows <Audio 1>.
```

如果一个 Reference 只定义某一属性：

```text
<Subject 1> retains the appearance from <Picture 1>
and the walking motion from <Video 1>.
```

---

# 18. Summary

`summary` 第一行必须提供任务类型。

例如：

```text
[reference generation + audio reference]
```

或者：

```text
[reference generation + video reference + audio reference]
```

Summary 只说明：

* 任务目标
* 核心角色
* Reference 关系
* 核心动作
* 场景逻辑

不要把详细 Shot 全部重复进去。

---

# 19. Retention Analysis

`retention_analysis` 必须覆盖所有需要在后续 Prompt 中持续追踪的 Reference Label。

每个 Reference Label 使用一条关系记录。

视觉关系：

```text
fully_preserved
partially_preserved
attribute_transfer
weak_reference
```

Audio 关系：

```text
fully_copy
partially_copy
reference
weak_reference
```

例如：

```text
<Subject 1> (appears throughout): fully_preserved - identity and appearance remain consistent.

<Subject 2> (appears throughout): fully_preserved - identity and costume remain consistent.

<Picture 1> ([Shot 1] composition): fully_preserved - spatial layout and framing are retained.

<Audio 1>: reference - the target speaker follows its voice timbre and delivery characteristics without copying the original signal.
```

不得在 retention_analysis 中重复整段人物描述。

---

# 20. `fully_preserved` 与 `reference` 的区别

不要滥用 `fully_preserved`。

如果仅仅是：

> 使用某人的声音特点

应使用：

```text
reference
```

而不是：

```text
fully_copy
```

`fully_copy` 仅用于真正复制音频信号。

角色外观如果只是部分借用：

```text
partially_preserved
```

如果把某个属性转移给另一个 Subject：

```text
attribute_transfer
```

---

# 21. Detailed Description

这是整个 H3 Prompt 的核心。

官方要求详细描述：

* 当前构图
* Subject 外观
* Subject 位置
* 环境
* 灯光
* 动作
* 状态变化
* Camera
* 当前声音
* Reference 在何时生效
* 对白

必须按照播放顺序描述。

不要把 Detailed Description 写成剧情简介。

不要只写：

```text
The Commander talks to the Director.
```

而应写出：

```text
[Shot 1]
The shot begins with the command-room composition established by <Picture 1>.
<Subject 1> (S1) remains at the center and turns toward <Subject 2> on the right.
She asks...

<Subject 2> (S2) listens and replies...
```

---

# 22. Reference 允许必要的当前镜头重建

V3 中：

> Reference 已经有 → 不再描述

V4 改为：

> Reference 已经有 → 不机械复制。

在一个重要 Subject 第一次清晰出现时，仍然需要说明当前 Shot 中实际可见的：

* 身份
* 位置
* 关键外观
* 当前动作
* 当前状态

例如：

```text
<Subject 1> appears in the center of the frame, wearing the purple command uniform established by <Picture 2>, and turns toward the Director.
```

但不要把 Picture 2 中已经明确的：

* 每个发丝
* 每件饰品
* 每个服装材质
* 每个背景细节

全部重新写一遍。

---

# 23. Reference 不是“绝对禁止重复”

正确原则：

```text
不要机械复制 Reference。
必要时重新确认当前镜头的可见信息。
```

判断标准：

`这句话是否改变模型当前 Shot 所需的视觉行为？`

如果是：

保留。

如果只是：

“重新介绍整张图”

删除。

---

# 24. Shot 格式

第一镜：

```text
[Shot 1]
```

后续镜头：

```text
[Shot 2] At 00:04.000,
[Shot 3] At 00:08.500,
[Shot 4] At 00:12.000,
```

时间必须严格递增。

不能：

```text
[Shot 2] At 00:08.000
[Shot 3] At 00:05.000
```

15 秒 Node 中：

* 最后时间点必须位于视频长度范围内
* 不要为了形式而增加无意义镜头
* 每个 Cut 都应该带来新的视觉或剧情信息

---

# 25. 连续 Shot 与 Cut

如果只是 Camera 轻微变化：

优先使用 Camera Movement。

不要无理由 Cut。

优先：

* Static Shot
* Push In
* Pull Out
* Pan
* Tracking
* Tilt
* Truck

只有剧情发生明显信息变化时才增加新 Shot。

---

# 26. Camera Movement

每个 Camera 动作必须有明确主语。

例如：

```text
The camera slowly pushes in.
```

表示 Camera 向前。

而：

```text
The Commander moves forward.
```

表示人物向前。

禁止把：

```text
the camera moves backward
```

理解成：

```text
the subject moves backward
```

---

# 27. 动作

只描述：

* 关键动作
* 因果动作
* 导致下一状态的动作

推荐：

```text
The Director raises her hand and activates the holographic interface on the command console.
```

不要无意义描述：

* 手腕转动几度
* 手指轨迹
* 肩膀移动多少
* 每次眨眼

除非这些本身就是剧情。

动作必须能够在当前 Node 的时间内完成。

---

# 28. 动作因果

状态发生变化时，尽量建立因果关系。

推荐：

```text
The Director receives the order, then reaches toward the holographic interface.
```

而不是：

```text
The Director receives the order. She touches the interface.
```

前者更清楚地表达：

`事件 A → 动作 B`

有助于维持连续性。

---

# 29. 表演

允许模型自行完成：

* 自然呼吸
* 眨眼
* 微笑
* 轻微目光变化
* 微小身体摆动
* 自然手势

不要把所有微动作硬编码。

只有：

* 剧情关键
* 人物身份关键
* 台词表达关键
* 连续性关键

才写成明确动作。

---

# 30. Emotion Text

Emotion Text 是内部表演 metadata。

例如：

```text
Emotion: calm, authoritative, controlled curiosity.
```

它不是 Spoken Dialogue。

不得放进台词引用中。

Emotion Text 建议：

* 2–5 个词或短语
* 可执行
* 具体
* 不文学化

推荐：

```text
calm, firm, decisive
```

```text
cautious, analytical, slightly concerned
```

```text
brief, immediate, professional
```

不要：

```text
with the sorrow of a woman carrying the burden of civilization for decades
```

---

# 31. Emotion Text 必须最终转译进 H3 语言

Emotion Text 可以作为创作者审核 metadata。

但正式 H3 Prompt 不应依赖模型去猜：

```text
Emotion: calm
```

真正进入 `detailed_description` 时，应把表演方向自然转成英文：

```text
<Subject 1> (S1) speaks calmly and with controlled authority.
```

所以：

```text
中文审核 Emotion
↓
内部 Emotion Metadata
↓
最终英文表演描述
```

---

# 32. Dialogue

正式 H3 Prompt 中，台词必须直接写最终版本。

推荐使用官方 `<d>`：

```text
<Subject 1> (S1) asks calmly:
<d>[Japanese]どう思う？</d>
```

第二位角色：

```text
<Subject 2> (S2) replies with restrained concern:
<d>[Japanese]どうにも妙ですね。地球側からは、何も知らされていません。</d>
```

不得写：

```text
she says something appropriate
```

不得写：

```text
according to the script
```

不得写：

```text
improvise
```

---

# 33. 日语对白

日语使用最终确认版本。

允许：

* 漢字
* ひらがな
* カタカナ

不得擅自把汉字全部转换成假名。

不要添加：

```text
Pronunciation:
```

不要同时提供两套 Spoken Dialogue。

---

# 34. 台词标点

完整陈述使用：

```text
.
```

疑问使用：

```text
?
```

感叹使用：

```text
!
```

不要堆叠：

```text
～～～～！！！
```

不要使用装饰性 Emoji 作为 Spoken Dialogue 的必要组成。

原始台词如果需要规范化，只调整必要标点，不改变语义。

---

# 35. Spoken Dialogue 与 Audio Reference

当 Audio 只是参考音色：

不要复制 Audio 原本说过的内容。

例如：

```text
<Audio 1> is the voice-timbre reference for <Subject 1> (S1).
```

然后：

```text
<Subject 1> (S1) says:
<d>[Japanese]どう思う？</d>
```

只继承：

* timbre
* delivery
* rhythm
* relevant expressive characteristics

不得把参考录音中的旧台词带入新视频。

---

# 36. 多人对白

多角色对白严格使用：

`Subject + Speaker ID + Dialogue`

例如：

```text
<Subject 1> (S1): ...
<Subject 2> (S2): ...
```

对白顺序必须与视频中的实际发言顺序一致。

不要让：

* Character A 使用 Character B 的 Audio
* Character A 使用 Character B 的 Speaker ID
* Character B 说了 A 的台词

这是严重错误。

---

# 37. 背景角色

背景角色默认：

* 不承担关键对白
* 不抢镜
* 不主动引发剧情事件

如果需要保持沉默，应明确：

```text
<Subject 3> remains silent throughout the shot.
```

如果只作为背景人物：

```text
<Subject 3> remains a silent background participant.
```

---

# 38. `off-screen` Speaker

如果角色不在画面内但仍然是同一说话人：

保持原 Speaker ID。

例如：

```text
<Subject 2> (S2), off-screen, responds:
<d>[Japanese]はい。</d>
```

不得因此产生一个新的 `(S3)`。

---

# 39. `<scenetrans>`

如果对白或连续声音跨越 Shot，并且不应该被视为完整结束：

可以使用：

```text
<scenetrans>
```

用于表达场景过渡或声音/话语连续性。

不得滥用。

---

# 40. `<cutoff>`

如果完整视频结束时：

* Dialogue 被截断
* Voiceover 未完成
* 声音被画面结束切断

使用：

```text
<cutoff>
```

不要写一个看似完整、实际上没有时间完成的长台词。

---

# 41. 剧情对白总览

正式 English H3 Prompt 前必须输出：

`〖剧情对白总览〗`

每条对白包括：

* 时间
* 角色
* Speaker
* Audio
* 日语台词
* Emotion Text
* 简短中文情绪说明

例如：

```text
00:00–00:03
Commander
S1 / Audio 1
「どう思う？」
Emotion: calm, curious, authoritative.
中文：平静地询问，希望得到判断。
```

---

# 42. 按角色归类的台词

然后输出：

`〖按角色归类的台词〗`

例如：

```text
Commander
- どう思う？
- 地球側に確認してくれ。

Director
- どうにも妙ですね。地球側からは、何も知らされていません。
- はい。
```

这部分用于创作者审核。

不属于最终 H3 六段式 Prompt。

---

# 43. Scene Positive Constraint

场景优先使用正向描述。

优先写：

```text
an isolated outer-Solar-System icefield under weak indirect illumination
```

而不是：

```text
no Earth
no sunset
no warm sunlight
no normal sky
```

但是负面约束并非绝对禁止。

当某一个严重错误具有高度复发概率，而且正向描述不足以稳定阻止时，可以加入少量 Negative Constraint。

原则：

`正向定义优先，负向约束兜底。`

---

# 44. 伊瑟尔外部环境

伊瑟尔是：

* 外太阳系极寒超级地球
* 远离太阳
* 极低太阳辐照
* 冰雪覆盖
* 非地球环境

如果场景位于伊瑟尔表面：

优先描述：

* 深黑星空
* 弱光
* 冷色环境光
* 广阔冰原
* 厚重冻结地表
* 远离太阳的空间环境

不得让画面默认漂移到：

* Earth-like sunset
* Earth-like sky
* 普通地球山脉
* 热带环境
* 普通日落景观

---

# 45. 伊瑟尔地下都市

主要城市、军事设施、科研设施和大型文明基础设施位于地下。

地下环境可以具有：

* 城市化空间
* 花园
* 民用区域
* 军事区域
* 科研区域
* 商业区域
* 高端住宅
* 学校
* 医疗设施

但必须保持统一文明设计。

不要把所有空间都做成：

* 普通赛博朋克蓝色摩天楼
* 游戏科幻工厂
* 无逻辑机械堆叠

---

# 46. 地下都市的核聚变光照

伊瑟尔地下文明掌握先进核聚变技术。

地下大型城市可以拥有接近地表日光的照明效果。

但这种照明是：

`人工文明照明`

不是：

`太阳直射`

因此地下城市可以出现明亮、开放、具有天空感的巨大公共空间，但不应该无理由表现成地球室外环境。

---

# 47. 透明穹顶

伊瑟尔地下城市上方可能存在：

* 巨型透明或半透明穹顶
* 冰层支撑结构
* 外部冰原
* 遥远的外部空间

如果出现穹顶：

优先作为结构的一部分描述。

不要把它误写成：

* 普通玻璃屋顶
* 地球温室
* 观光大厅

---

# 48. 高科技交互

高科技设备优先利用已有环境中的：

* Command Console
* Holographic Interface
* Data Display
* Tactical Table
* Embedded UI

例如：

```text
The Director activates the holographic interface on the command console.
```

不要为了体现“高科技”而增加：

* 几十个发光屏幕
* 浮空机械
* 无意义 HUD
* 随机蓝色光条

---

# 49. 通讯方式

当剧情是：

* Holographic Call
* Command Console Communication
* Remote Visual Link
* Tactical Communication

直接描述为高科技通讯系统。

例如：

```text
The Director activates the holographic communication interface on the command console.
```

不要无理由变成：

```text
telephone
smartphone
handheld phone
```

如果用户没有明确要求传统电话，不应自行引入。

---

# 50. AEGIS 组织层级

固定层级：

`星穹防卫总司令 ＞ 防卫总监 ＞ AEGIS 队长 ＞ AEGIS 队员`

权限必须与角色身份匹配。

总司令：

* 战略判断
* 重大命令
* 最高层决策

防卫总监：

* 分析
* 汇报
* 协调
* 执行

AEGIS 队长：

* 战术
* 前线执行
* 队伍指挥

AEGIS 队员：

* 执行任务
* 战术行动
* 现场反馈

不要让低级队员无理由下达战略命令。

---

# 51. 角色名称规则

《星穹防卫线》正式角色名称必须保持当前项目词典。

不得擅自：

* 更名
* 改写罗马字
* 混用旧名
* 使用已经废弃的角色名称

特别注意：

旧角色名称“初音”已经废弃。

当前正式名称：

`朝倉千景 / Asakura Chikage`

未来 Prompt、剧本、表格、Glossary、角色定义中不得重新使用旧名称。

---

# 52. 人物数量

优先使用已经存在的角色。

不要无理由新增有名角色。

新角色必须建立：

```text
Subject
Reference
Voice
Speaker
```

关系。

背景人物默认不承担关键对白。

---

# 53. Scene Anchor

如果存在完整 Scene Reference：

它优先控制：

* 空间结构
* 角色位置
* 背景
* 建筑
* 设备
* 灯光
* 构图

Prompt 只告诉模型：

`剧情中发生了什么变化`

而不是：

`重新设计整个房间`

---

# 54. 角色 Anchor 与 Scene Anchor 可以同时存在

例如：

```text
Picture 1 → Scene / Composition Anchor
Picture 2 → Commander Identity
Picture 3 → Director Identity
```

三张图可以共同工作。

Scene Anchor 不改变 Character Identity。

Character Reference 不自动改变 Scene Geometry。

---

# 55. Reference Conflict 处理

如果两个 Reference 对同一属性产生冲突：

优先级：

1. 用户当前 Node 明确指定
2. Current Scene Anchor
3. Character Identity Reference
4. Audio Reference
5. 文字默认描述
6. 模型自由发挥

不得为了“看起来完整”强行兼容冲突 Reference。

应该明确哪个 Reference 控制哪个属性。

---

# 56. 连续性

Shot 之间检查：

* 人物位置
* 人物姿态
* 动作状态
* 道具状态
* 视线
* 表情
* 灯光
* 声音
* 空间
* Camera
* UI 状态

如果状态发生变化，应有：

* 动作
* Camera Movement
* Cut
* 明确状态变化

不要让状态无原因跳变。

---

# 57. Prompt Density

V4 不再使用：

`Instruction Density < Information Density`

这种容易造成误解的抽象说法作为硬规则。

改为：

> Prompt 必须优先保留能改变模型行为的信息。

每句话都问：

`Does this sentence change the model's required behavior?`

如果：

* 只是重新介绍图片
* 只是堆形容词
* 只是重复世界观
* 只是重复已有 Reference

优先删除。

如果它规定：

* 身份
* 声音
* 台词
* 时间
* 动作
* 位置
* 状态
* 因果
* 关键场景条件

优先保留。

---

# 58. Essential Information

必须保留：

* Subject Identity
* Reference Mapping
* Audio Mapping
* Speaker ID
* Dialogue
* Key Time
* Key Action
* Key Spatial Relation
* Key State Change
* Important Environment Constraint
* Important Continuity

---

# 59. Optional Information

通常交给模型自行处理：

* 自然眨眼
* 呼吸
* 轻微身体摆动
* 微小背景动作
* 小型景深变化
* 轻微光照波动
* 不影响剧情的手指动作
* 不影响剧情的 Camera 微调

除非用户明确要求，不得把这些变成大量硬约束。

---

# 60. 修饰词预算

每个主要动作通常使用：

`1–3 个`

必要修饰词。

推荐：

```text
The Commander speaks calmly and firmly.
```

不推荐：

```text
The Commander speaks in a deeply restrained, sophisticated, professionally controlled, calm, authoritative and highly disciplined military-command voice.
```

除非这些差异真的会改变模型行为。

---

# 61. Reference 优先于形容词

如果 Reference 已经决定：

* 角色长相
* 发型
* 服装
* 场景
* 构图

优先使用：

```text
whose appearance comes from <Picture 2>
```

或者：

```text
<Picture 1> is the scene composition anchor.
```

而不是大量重新描述。

---

# 62. 但禁止“Reference-only Prompt”

不得因为 Reference 很强而把 Prompt 简化成：

```text
Use <Picture 1>.
The character talks.
```

这是错误的。

Reference 可以提供身份和视觉基础，但 Prompt 仍必须描述：

* 当前发生的动作
* 当前人物位置
* 当前 Shot
* Dialogue
* 状态变化
* Camera
* 必要的声音

---

# 63. Soundscape

`overall_soundscape` 用于：

* Environment Ambience
* Physical Sounds
* Mechanical Sounds
* Room Tone
* Footsteps
* Interface Sounds
* Communication Noise
* Environmental Audio

Dialogue 和特定 Shot 的同步声音应保留在 `detailed_description`。

例如：

```text
overall_soundscape:
A quiet command-center room tone with low ventilation hum and subtle holographic interface sounds.
```

---

# 64. Non-diegetic Music

`non_diegetic_music` 只描述：

* 观众听得到
* 角色听不到

的背景音乐。

描述：

* 乐器
* Tempo
* 强度
* Dynamic Development

不要主要使用抽象情绪词。

例如：

```text
non_diegetic_music:
A restrained low-string score at a slow tempo, with sparse electronic textures and no dramatic swell.
```

没有音乐：

```text
non_diegetic_music:
N/A
```

---

# 65. 音乐不能压过对白

如果存在对白：

背景音乐不能成为声音主体。

Dialogue 优先。

---

# 66. Node 默认长度

本项目：

`1 Node = 15 秒`

一个 Node 可以包含：

* 1 Shot
* 2 Shots
* 3 Shots

必要时可以更多，但不应为了凑满 15 秒而增加无意义动作。

Node 判断标准：

> 这一段是否围绕一个清晰的主要事件？

而不是：

> 有没有刚好填满 15 秒？

---

# 67. Node Complexity

以下内容同时大量出现时，应降低复杂度：

* 多人对白
* 多人物动作
* 多个道具
* 高频切镜
* 复杂 UI
* 复杂 Camera
* Voice Reference
* 多重环境变化

必要时：

`减少动作`

或者：

`拆分 Node`

而不是继续无限增加 Prompt。

---

# 68. 一句话一个行为原则

复杂句子可以保留，但每个句子应尽量围绕一个清晰行为。

例如：

```text
The Director turns toward the Commander.
She listens briefly.
She then raises her hand and activates the holographic console.
```

比：

```text
The Director, while listening attentively and processing the information with restrained concern, turns toward the Commander, raises her hand, activates the display, and begins speaking while the camera slowly moves...
```

更容易调试。

---

# 69. 世界观一致性

所有未来《星穹防卫线》Prompt 必须遵守：

* 伊瑟尔是外太阳系极寒超级地球
* 主要文明基础设施位于地下
* 地下文明拥有先进核聚变能源
* 地下城市可以模拟大尺度自然光照
* 外部环境远离太阳
* 外部环境不应默认呈现 Earth-like sky
* 高科技属于统一文明体系
* AEGIS 是正式军事组织
* 军事和科研设施应具有功能逻辑

---

# 70. 夕阳 / 地球环境问题

当用户明确要求外太阳系伊瑟尔表面：

优先描述：

* distant stars
* deep black sky
* weak indirect illumination
* frozen planetary surface
* blue-white ice
* enormous frozen terrain
* extreme isolation

不要只靠：

```text
no sunset
no Earth
no terrestrial atmosphere
```

来解决。

必要时可以增加一条极简 Negative Constraint，但不得连续堆叠。

---

# 71. 科幻设施逻辑

不要把所有科幻设备默认处理为：

* blue glowing panels
* giant holograms
* random cables
* floating screens
* generic cyberpunk architecture

科技设计必须服务于：

* 指挥
* 医疗
* 研究
* 生活
* 交通
* 防御

等实际功能。

---

# 72. 角色行为与职位

角色行为必须符合：

* 职位
* 年龄
* 性格
* 当前压力
* 当前剧情

例如 Commander：

优先：

* 短
* 稳定
* 判断
* 命令

而非：

* 长篇情绪化解释

Director：

优先：

* 分析
* 汇报
* 解释
* 执行

Captain：

优先：

* 战术观察
* 前线信息
* 队员协调

---

# 73. 台词自然度

生成或修改日语台词时，检查：

* 是否像真实日语
* 敬语是否符合职位
* 口语程度是否合理
* 是否符合人物身份
* 是否符合时代与世界观
* 是否符合当前上下文

禁止出现明显“中国式日语”。

不为了“听起来正式”而过度增加敬语。

---

# 74. 输出前自检：Reference

正式 Prompt 生成前检查：

1. Subject 是否正确？
2. Picture 是否正确？
3. Video 是否正确？
4. Audio 是否正确？
5. Reference Role 是否明确？
6. 是否存在 Reference 冲突？
7. Picture 是否被错误当成 Subject？
8. 仅作为 Subject source 的 Picture 是否被错误独立定义？

---

# 75. 输出前自检：Speaker

检查：

1. 每个实际说话人是否有 Speaker ID？
2. Speaker ID 是否稳定？
3. Subject 与 Speaker 是否正确？
4. Audio 与 Speaker 是否正确？
5. 是否有角色抢走另一个角色的声音？
6. 通讯场景是否错误地产生新 Speaker？

---

# 76. 输出前自检：Dialogue

检查：

1. 台词是否为最终版本？
2. 是否直接写入 `<d>`？
3. 是否保留原语言？
4. 是否没有临时占位符？
5. 是否没有“say something”？
6. 是否没有“according to the script”？
7. 是否没有把 Emotion 写入对白？
8. 是否与时间线一致？

---

# 77. 输出前自检：Timeline

检查：

1. `[Shot 1]` 是否为第一镜？
2. 后续 Shot 是否带递增时间？
3. 是否超过 Node 时长？
4. 是否有无意义 Cut？
5. 是否有动作因果？
6. 是否存在无法在 15 秒内完成的行为？
7. 是否需要 `<scenetrans>`？
8. 是否需要 `<cutoff>`？

---

# 78. 输出前自检：Scene

检查：

1. 空间关系是否正确？
2. Local Spatial Anchor 是否正确？
3. 人物左右关系是否正确？
4. 人物与设备关系是否正确？
5. Scene Reference 是否被错误重新设计？
6. 伊瑟尔环境是否正确？
7. 是否错误出现 Earth-like environment？
8. 是否错误出现 sunset？
9. 是否引入无理由新设施？
10. 是否引入不符合世界观的新人物？

---

# 79. 输出前自检：Prompt Density

检查：

1. 是否重复整张 Reference？
2. 是否重复世界观？
3. 是否堆叠无意义形容词？
4. 是否添加没有剧情意义的动作？
5. 是否可以删掉某句话而不改变模型行为？

如果可以：

删除。

---

# 80. 7000 字符项目预算

默认最终 Prompt：

`≤ 7000 characters`

这是《星穹防卫线》的**项目级可读性和复杂度预算**，不是 MiniMax H3 官方硬性字符上限。

如果接近预算：

优先删除：

* 重复视觉描述
* 重复环境描述
* 画质形容词
* 重复 Reference 信息
* 重复连续性声明
* 无意义镜头修饰

不得删除：

* Subject
* Reference Mapping
* Audio
* Speaker ID
* Dialogue
* Emotion direction
* Key Action
* Key Time
* Key Spatial Relation
* Core Scene Constraint

---

# 81. Detailed Description 长度原则

对于生成型 Full-Reference 任务：

`detailed_description` 应足够具体。

不机械追求字数。

可以将约：

`350–500 English words`

作为复杂 Generation Task 的常用参考范围。

Dialogue-dense Node 优先保证：

* 完整台词
* 时间
* Speaker
* Action
* Reference

而不是为了凑字数。

---

# 82. 最终输出格式

正式任务默认输出：

```text
亲爱的指挥官，

① 节点审核区

② 图片输入分配

③ 音频输入分配

④ 〖剧情对白总览〗

⑤ 〖按角色归类的台词〗

⑥ English H3 Prompt
```

---

# 83. 节点审核区

节点审核区使用中文。

至少包含：

* Node
* 时间
* 标题
* 场景
* 图片输入
* 音频输入
* Subject
* Speaker
* 主要动作
* Camera
* Dialogue
* Emotion
* 连续性重点

审核区不是 H3 Prompt。

---

# 84. English H3 Prompt

最终正式 Prompt 必须全部使用英文。

除了：

* Spoken Dialogue
* Lyrics
* Scene 中明确出现的文字

其他内容全部使用英文。

完整 Ref2VA：

```text
subject_definitions

summary

retention_analysis

detailed_description

overall_soundscape

non_diegetic_music
```

---

# 85. Dialogue 格式模板

推荐：

```text
<Subject 1> (S1) turns toward <Subject 2> and speaks calmly:
<d>[Japanese]どう思う？</d>
```

如果角色是：

```text
off-screen
```

则：

```text
<Subject 2> (S2), off-screen, responds:
<d>[Japanese]はい。</d>
```

---

# 86. Reference Shot 模板

```text
[Shot 1]
The scene begins with <Picture 1> as the composition anchor.
<Subject 1> appears at the center of the frame...
```

后续：

```text
[Shot 2] At 00:04.000,
the camera...
```

---

# 87. 典型多人对白模板

```text
[Shot 1]
The shot begins with <Picture 1> as the command-room composition anchor.
<Subject 1> (S1) stands at the center.
<Subject 2> (S2) remains on the right.
<Subject 3> remains a silent background participant.

<Subject 1> (S1) turns toward <Subject 2> and asks calmly:
<d>[Japanese]どう思う？</d>

[Shot 2] At 00:03.500,
<Subject 2> (S2) responds with restrained concern:
<d>[Japanese]どうにも妙ですね。地球側からは、何も知らされていません。</d>
```

---

# 88. 禁止的写法

不得使用：

```text
say something appropriate
say something natural
according to the script
improvise
continue the conversation naturally
make the character look similar
make the character sound similar
```

因为这些属于不可执行或模糊指令。

---

# 89. 不得把角色关系写成抽象概念

不要只写：

```text
A senior officer talks to a subordinate.
```

如果具体角色已知，应直接使用：

```text
<Subject 1> (S1)
<Subject 2> (S2)
```

让 Subject、Speaker 和 Reference 显式关联。

---

# 90. 不得把 Reference 当“灵感”

如果用户指定：

```text
Picture 2 = Commander
```

这不是“风格参考”。

它应被视为明确 Identity Reference。

不得自行改变：

* 发型
* 脸
* 制服
* 身体比例
* 基本身份

除非用户明确要求。

---

# 91. Reference 与剧情变化

如果剧情需要角色：

* 脱下帽子
* 换衣服
* 受伤
* 湿身
* 戴上设备
* 表情发生巨大变化

Reference 仍然负责基础身份。

Prompt 负责变化。

例如：

```text
<Subject 1> retains the identity and uniform from <Picture 2>,
but her right sleeve is visibly damaged during the current scene.
```

---

# 92. Scene Reference 与剧情变化

如果 Reference 已经有完整房间：

不要重建房间。

如果剧情需要：

* 灯光变红
* 全息界面开启
* 门打开
* 警报启动

只描述变化：

```text
The command-room lighting shifts to a muted red emergency state.
```

---

# 93. 世界观与生成自由度

允许模型自行决定：

* 微表情
* 背景小动作
* 微小环境变化
* 细小 Camera 修正

不允许模型自行决定：

* 新角色
* 新职位
* 新通讯设备
* 新重大建筑
* 新关键武器
* 新剧情事件

除非用户授权。

---

# 94. 最终 Principle

《星穹防卫线》的 H3 Prompt 不应该是：

“给模型的一篇小说”。

也不应该是：

“给 3D 软件写的工程施工图”。

它应该是：

> **一份结构化、可执行、可检查的视听导演指令。**

Reference 告诉模型：

`这个人是谁。`

`这个地方是什么。`

`这个资产来自哪里。`

Speaker 告诉模型：

`是谁在说话。`

Audio 告诉模型：

`这个声音属于谁，以及应参考什么声音特征。`

Emotion 告诉模型：

`这一句应该以什么表演方向说出来。`

Timeline 告诉模型：

`什么时候发生。`

Detailed Description 告诉模型：

`现在发生什么。`

Soundscape 告诉模型：

`环境中听见什么。`

Non-diegetic Music 告诉模型：

`观众听见什么背景音乐。`

其余不会改变剧情、身份、空间、声音或连续性的细节，都应尽量留给模型自由发挥。

---

# 95. Final Self-Check

在输出最终 H3 Prompt 前，必须完成以下检查：

### Reference

* [ ] Subject 正确
* [ ] Picture 正确
* [ ] Video 正确
* [ ] Audio 正确
* [ ] Reference Role 明确
* [ ] Label 没有含义漂移
* [ ] Subject 与来源一致
* [ ] Scene Anchor 与 Character Anchor 没有冲突

### Speaker

* [ ] 每个说话人有正确 Speaker ID
* [ ] Speaker ID 没有重新编号
* [ ] Speaker 与 Subject 对应
* [ ] Speaker 与 Audio 对应
* [ ] 通讯没有产生错误新 Speaker

### Dialogue

* [ ] 台词是最终版本
* [ ] 使用正确语言
* [ ] 使用 `<d>[Language]...`
* [ ] 没有占位符
* [ ] 没有模糊对白
* [ ] Emotion 没进入 Spoken Dialogue

### Shot

* [ ] Shot 顺序正确
* [ ] 时间严格递增
* [ ] 所有时间点在 Node 时长内
* [ ] 每个 Cut 有明确意义
* [ ] 动作有因果
* [ ] Camera 主语明确

### Scene

* [ ] 空间关系正确
* [ ] 人物位置正确
* [ ] Scene Reference 没有被重新设计
* [ ] 伊瑟尔世界观正确
* [ ] 没有无理由 Earth-like Drift
* [ ] 没有无理由夕阳
* [ ] 没有无理由新增角色或设备

### Prompt

* [ ] 没有机械复述 Reference
* [ ] 首次出现的关键 Subject 有必要的当前 Shot 描述
* [ ] 没有无意义形容词
* [ ] 没有无意义动作
* [ ] 没有过度 Negative Constraint
* [ ] 六段结构正确
* [ ] 默认目标 ≤7000 characters
* [ ] 没有因为压缩而删除必要信息

---

# 96. 当前版本核心变化摘要

V4 相比 V3 的核心变化：

```text
V3
Reference-first
+
少重复描述

V4
Reference-first
+
Reference Map
+
Subject / Asset 分离
+
Speaker ID
+
Audio / Speaker 强绑定
+
必要的首个 Shot 视觉重建
+
完整 retention coverage
+
官方 Shot / Dialogue syntax
+
Context-IR 思维
+
Ref2VA 与其他 H3 模式分离
```

最终原则：

```text
不是“少写”。

而是“只写真正改变模型行为的信息”。
```

---

# 97. 官方依据

本 Skill 的 H3 通用部分应以 MiniMax 最新官方文档为底层依据：

MiniMax H3 Repository:
https://github.com/MiniMax-AI/MiniMax-H3

Full-Reference Prompt Writing Guide:
https://huggingface.co/MiniMaxAI/MiniMax-H3/blob/main/docs/VIDEO_PROMPT_WRITING_GUIDE_ref_en.md

项目级 Skill：
本文件 `isaraskill.md`

当官方 H3 文档未来发生变化时：

1. 优先更新 H3 通用规则
2. 再检查本 Skill 的项目规则
3. 只有在两者冲突时，才修改项目级规则
4. 不为了追求“格式完整”而违反官方输入限制或语法

---

# 98. 永久原则

永远优先：

`Identity > Reference Mapping > Speaker / Audio > Dialogue > Key Action > Spatial Continuity > Timeline > Scene Logic > Sound > Optional Detail > Adjectives`

不要本末倒置。

不要为了让 Prompt 看起来复杂，而削弱真正重要的信息。

不要把 H3 当成“关键词生成器”。

把 H3 当成：

**一个需要明确 Reference、角色、声音、时间、空间与因果关系的视听生成系统。**
