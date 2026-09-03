《星穹防卫线》MiniMax H3 视频制作 Skill
项目最终版

用于原创科幻动画《星穹防卫线 / AEGIS FRONTIER》的分镜设计、15秒 Node 拆分、MiniMax H3 Full-Reference 视频 Prompt 编写、角色固定 Voice Reference 管理、日语对白、镜头、声音及世界观连续性控制。

---

# 0. 规则层级

本项目同时遵循两套规则。

## A. MiniMax H3 通用 Prompt 规则

来源：

https://github.com/CharlieOneDev/comfyui-skill/blob/main/多模态优化提示词元指令_通用版.md

每次正式编写 H3 Prompt 时，优先读取该文档的最新版本。

该文档负责：

* Full-Reference Prompt 结构
* Subject / Picture / Video / Audio 标签
* retention_analysis
* 时间线
* 运镜
* 物理因果
* 表演
* 灯光
* 声音
* 输出结构

## B. 《星穹防卫线》项目规则

本 Skill 负责补充：

* 世界观
* 角色
* 角色姓名
* 三语名称
* 日语固定读音
* Spoken Dialogue 发音安全
* 9名核心女性角色 Voice Reference
* Audio 输入限制
* 图片输入逻辑
* 空间逻辑
* 职位体系
* 对白逻辑
* 连续性
* 伊瑟尔文明逻辑
* 地下都市逻辑

两者必须同时遵守。

---

# 1. 生产单位

默认：

1 Node = 15秒 H3 生成单元。

每个 Node：

* 最多3个 Shot
* 优先在 Node 边界形成自然硬切
* 不为了凑满15秒而拖长镜头

如果场景自然结束于：

* 9秒
* 10秒
* 12秒
* 其他合理短时长

直接结束。

只有连续镜头真正超过15秒时，才标记：

⚠️【长镜头警告】

---

# 2. H3 图片输入

H3 Full-Reference 最多使用：

8个 Picture。

Picture 编号没有固定含义。

每个 Node 必须重新分配。

例如：

Picture 1
Picture 2
Picture 3

下一 Node 可以完全重新排列。

因此正式 Prompt 前必须提供：

【图片输入分配】

| 图片   | 输入内容 | 用途  |
| ---- | ---- | --- |
| 图1   | XXX  | XXX |
| 图2   | XXX  | XXX |
| 图3   | XXX  | XXX |
| 图4–8 | 不使用  | —   |

用户必须可以按照该表直接连接 ComfyUI H3 输入。

---

# 3. H3 音频输入

H3 最多只能接入：

3个 Audio 输入。

但必须区分：

不是一个 Node 最多只能出现3个有声音的人。

而是：

一个 Node 最多只能接入3个独立 Audio Reference。

---

# 4. 9名核心女性角色

以下角色拥有长期固定的独立 Voice Reference：

| 中文   | English         | 日本語   | 固定 Audio |
| ---- | --------------- | ----- | -------- |
| 神崎紫苑 | Kanzaki Shion   | 神崎紫苑  | 是        |
| 神代玲奈 | Kamishiro Reina | 神代玲奈  | 是        |
| 白神凛  | Shiragami Rin   | 白神凛   | 是        |
| 九条绫  | Kujou Aya       | 九条綾   | 是        |
| 米娅   | Mia             | ミア    | 是        |
| 雪乃   | Yukino          | 雪乃    | 是        |
| 神代澪  | Kamishiro Mio   | 神代澪   | 是        |
| 朝仓千景 | Asakura Chikage | 朝倉千景  | 是        |
| 艾琳   | Eileen          | アイリーン | 是        |

需要说话时，应优先使用自己的固定 Voice Reference。

---

# 5. 其他人物默认声音

以下角色默认不占用固定 Audio：

* 男主
* 电视台纪录片式女性旁白
* 普通 NPC
* 医生
* 研究人员
* 监测员
* 士兵
* 护士
* 救援人员
* 路人
* 背景人物
* 临时角色

即使这些角色需要对白：

允许由 MiniMax H3 根据 Prompt 自行生成普通人声。

不要为了这些角色额外占用 Audio。

---

# 6. 男主声音

男主没有固定 Voice Reference。

默认由 MiniMax H3 生成普通成年男性声音。

Prompt 可以描述：

* 年龄感
* 情绪
* 语速
* 声压
* 当前身体状态
* 当前心理状态

但不需要 Audio Reference。

---

# 7. 电视台纪录片旁白

默认不使用固定 Audio。

可以使用：

professional Japanese television-documentary female narrator
mature adult female
magnetic medium-low register
extremely clear diction
calm professional delivery
moderate speaking speed
precise Japanese pronunciation

由 H3 直接生成。

除非未来明确指定固定旁白 Audio。

---

# 8. 音频输入分配

只要 Node 使用固定 Voice Reference，正式 Prompt 前必须提供：

【音频输入分配】

| 音频  | 输入内容                | 对应角色 |
| --- | ------------------- | ---- |
| 音频1 | XXX Voice Reference | XXX  |
| 音频2 | XXX Voice Reference | XXX  |
| 音频3 | XXX Voice Reference | XXX  |

如果 Node 中只有一个固定 Voice Reference：

| 音频    | 输入内容                | 对应角色 |
| ----- | ------------------- | ---- |
| 音频1   | XXX Voice Reference | XXX  |
| 音频2–3 | 不使用                 | —    |

如果完全没有固定 Voice Reference：

| 音频    | 输入内容 | 对应角色 |
| ----- | ---- | ---- |
| 音频1–3 | 不使用  | —    |

---

# 9. Audio 与角色绑定

如果角色拥有固定 Voice Reference：

<Subject 1> is Asakura Chikage, whose appearance comes from <Picture 1>. Her voice reference is provided by <Audio 1>.

对白部分应自然引用：

<Picture 1>, Asakura Chikage, speaks using <Audio 1>.

一个 Node 内：

Audio N 的角色含义绝不能改变。

例如：

正确：

Audio 1 → Rin
Audio 2 → Reina
Audio 3 → Shion

错误：

Shot 1: Audio 1 = Rin
Shot 2: Audio 1 = Reina

---

# 10. Subject / Picture / Video / Audio

## Subject

Subject 是真正参与目标视频的实体。

可以是：

* 人物
* 车辆
* 道具
* 动物
* 场景
* 服装
* 动作
* 特效

一个 Subject 可以由多个素材共同定义。

## Picture

Picture 可以用于：

* 视觉 Reference
* 首帧
* 关键帧
* 尾帧
* 构图锚点

如果只是作为人物、场景、车辆的 Reference 来源，不要为了形式重复定义。

## Video

Video 可以用于：

* 视频续写
* 动作参考
* 时间结构
* 镜头运动
* 剪辑节奏

## Audio

Audio 可以用于：

* 固定角色 Voice Reference
* 音色参考
* 实际声音复制
* 音乐
* 音效
* 其他声音参考

---

# 11. Reference 使用原则

人物图负责：

* facial identity
* facial proportions
* hairstyle
* hair color
* eyes
* body proportions
* costume
* accessories
* character identity

场景图负责：

* architecture
* spatial proportions
* layout
* materials
* lighting
* environment
* spatial continuity

载具 / 道具 / 装置图负责：

* structure
* shape
* proportions
* materials
* mechanical design
* visual behavior

必须避免 Reference Leakage。

例如：

人物图背景不得被错误迁移成新场景。

场景图中的人物不得被错误当成新角色。

坠毁图中的火焰不得错误迁移到正常飞船。

地表冰原不得错误迁移到地下设施。

地下兵工厂工业风不得错误迁移到民用城市。

---

# 12. 人物引用

采用简洁写法：

<Subject 1> is Asakura Chikage, whose appearance comes from <Picture 1>.

有固定 Audio 时：

<Subject 1> is Asakura Chikage, whose appearance comes from <Picture 1>. Her voice reference is provided by <Audio 1>.

人物出现在 Shot 中时必须明确对应 Picture：

Cut to <Picture 1>, Asakura Chikage.

不要只写：

Cut to Chikage.

---

# 13. 六段 Prompt 结构

正式 H3 Prompt 必须严格使用：

subject_definitions
summary
retention_analysis
detailed_description
overall_soundscape
non_diegetic_music

顺序不得改变。

不得使用其他结构替代。

---

# 14. subject_definitions

只定义真正使用的：

* Subject
* Picture
* Video
* Audio

以及它们之间的关系。

每个真正使用的标签必须先定义。

不要定义后文完全不用的标签。

同一个标签在整个 Prompt 中只能有一个含义。

---

# 15. summary

第一句必须使用官方任务类型，例如：

[reference generation]

[reference generation + audio reference]

[video continuation]

[video continuation + keyframe completion]

summary 应说明：

* 剧情目的
* 视觉目的
* 主要 Subject
* 情绪
* 空间关系
* Reference 用途

不要在 summary 中使用未定义标签。

---

# 16. retention_analysis

用于确保：

* 人物连续
* 场景连续
* 载具连续
* 道具连续
* 声音连续
* Voice Reference 连续
* Reference 不泄漏

视觉关系只能使用：

fully_preserved
partially_preserved
attribute_transfer
weak_reference

音频关系只能使用：

fully_copy
partially_copy
reference
weak_reference

禁止创造新的关系名称。

retention_analysis 中禁止使用：

(S1)
(S2)
(S3)

等说话人 ID。

---

# 17. detailed_description

必须按照实际播放顺序。

开头用一至两句定义：

* visual style
* cinematography
* lighting
* color
* atmosphere
* image quality

然后依次：

[Shot 1]

[Shot 2] At 00:03.000, ...

[Shot 3] At 00:08.000, ...

---

# 18. Shot 时间规则

Shot 1：

不写时间戳。

Shot 2 以后：

必须写时间戳。

例如：

[Shot 2] At 00:04.000, ...

[Shot 3] At 00:09.000, ...

所有时间必须严格递增。

所有时间必须小于 Node 总时长。

普通切镜优先使用：

the camera cuts to
the shot cuts to
the shot transitions to
the shot switches to

除非用户明确要求，否则避免：

cross-dissolve
fade
wipe

---

# 19. 运镜规则

可以使用：

Tracking Shot
Push In
Pull Out
Dolly
Truck Left / Right
Pedestal Up / Down
Pan
Tilt
Arc Shot
Static Shot
Roll Clockwise / Counterclockwise

运镜必须服务于：

* 信息揭示
* 情绪推进
* 人物关系
* 空间建立
* 动作连续性

优先：

一个主运镜。

必要时最多增加一个兼容次运镜。

避免无意义连续运镜。

运动中保持对焦连续。

摄像机不得穿过：

* 人物
* 墙体
* 车辆
* 建筑

---

# 20. 物理动作规则

动作按照：

意图 / 驱动力
→ 准备
→ 重心变化
→ 动作启动
→ 接触
→ 受力
→ 惯性 / 重力 / 摩擦
→ 次级运动
→ 减速
→ 稳定

人体：

先重心转移，再迈步。

脚底必须真实接触地面。

骨盆、肩膀、手臂、头部必须存在合理反向运动。

手先接触，再抓握。

动作必须有准备、发力、跟随、收势。

头发、服装、裙摆、饰品必须具有惯性延迟。

不得：

瞬间停止
凭空摆动
改变连接点

车辆：

重量影响加速度。

轮胎 / 履带必须真实接触地面。

转向符合运动半径。

加速、减速、转向符合惯性。

飞行器：

保持连续飞行方向。

转弯必须存在合理姿态变化。

推进方向必须与速度变化一致。

所有科幻效果必须遵守项目内部规则。

---

# 21. 人物表演

保持自然成人表演。

对白镜头：

natural mouth movement
restrained mouth opening
realistic facial motion
no exaggerated mouth opening
no excessive anime shouting

情绪主要通过：

* 语速
* 停顿
* 音量
* 眼神
* 微表情
* 姿态
* 呼吸

表达。

避免：

* 持续瞪眼
* 机械微笑
* 面部随机抽动
* 相邻帧情绪突然跳变
* 无理由夸张张嘴

通常：

眼睛先移动
→ 头部稍后响应
→ 身体最后响应

---

# 22. 日语对白总规则

所有角色对白：

ALL SPOKEN DIALOGUE MUST BE NATURAL JAPANESE ONLY.
NO ENGLISH SPOKEN DIALOGUE.
NO CHINESE SPOKEN DIALOGUE.

必须直接提供真实台词。

不得写：

according to the original script

say something appropriate

the character speaks naturally

如果没有对白：

No dialogue.

无对白人物保持自然闭唇。

---

# 23. MiniMax H3 日语发音安全

MiniMax H3 会直接根据 Prompt 理解并生成对白语音。

因此：

同一条 Spoken Dialogue 只能出现一次。

禁止：

「白神凛、出撃します。」
Pronunciation:
「しらがみ りん、しゅつげきします。」

也禁止：

「白神凛、出撃します。」
「しらがみ りん、出撃します。」

否则可能造成：

* 重复朗读
* 错误理解
* 口型错位
* 第二次朗读
* 声音异常

---

# 24. 正式表记与 Spoken Dialogue 分离

世界观、角色表、正式标题可以使用正式汉字。

例如：

白神凛
神代玲奈
神崎紫苑
朝倉千景
星穹防衛線

但：

真正交给 H3 发声的 Spoken Dialogue 必须使用稳定、安全的实际日语读法。

因此：

正式表记：

白神凛

Spoken Dialogue：

「しらがみ りん、出撃します。」

而不是：

「白神凛（しらがみ りん）、出撃します。」

---

# 25. 高风险日语词汇假名化总原则

处理优先级：

自然改写
＞
局部假名化
＞
整句假名化

例如：

不稳定：

未確認飛行物

优先自然改成：

未確認の飛行体

如果仍然误读：

みかくにんの飛行体

只修改高风险部分。

默认优先使用平假名。

不要无理由将整句日语片假名化。

但是：

如果某个专有名词经过实际 H3 测试已经确认汉字表记会反复误读，则该专有名词可以建立项目级强制 Spoken Dialogue 替代表。

---

# 26. 项目级“强制 Spoken Dialogue 替代表”

这一节属于最高优先级的日语发音安全规则之一。

规则：

正式世界观名称可以继续使用正式汉字。

但只要一个词进入：

* 角色 Spoken Dialogue
* 旁白
* 通讯语音
* 广播
* 电话语音
* 画外音
* 需要真实发声的台词
* 任何需要 H3 生成口语声音的文本

就必须使用该词对应的固定 Spoken Dialogue 形式。

不得：

* 在同一条 Spoken Dialogue 中同时出现正式汉字和读音
* 使用括号提供读音
* 追加 Pronunciation 行
* 在同一句中重复该名称

---

# 27. 星穹防衛線专用强制读法

这是本项目的硬性规则。

正式世界观名称：

星穹防衛線

English：

AEGIS FRONTIER

H3 Spoken Dialogue：

せいきゅうぼうえいせん

## 强制规则

任何实际发声文本中：

“星穹防衛線”

必须替换为：

“せいきゅうぼうえいせん”

包括：

* 角色对白
* 旁白
* 通讯
* 广播
* 纪录片旁白
* 电话语音
* off-screen dialogue
* 任何由 H3 实际生成声音的文本

禁止在 Spoken Dialogue 中出现：

星穹防衛線

星穹防卫线

星穹防衛線（せいきゅうぼうえいせん）

星穹防衛線 / せいきゅうぼうえいせん

禁止同时提供汉字与读音。

唯一允许的情况：

正式世界观说明、标题、角色资料、Prompt 内部说明、非发声文本。

例如：

正式名称是“星穹防衛線”。

这是允许的。

但：

<Subject 1>, Asakura Chikage, speaks:
「せいきゅうぼうえいせんの監視網に接続します。」

这是正确的。

不要写：

「星穹防衛線の監視網に接続します。」

即使 H3 理论上可能理解，也禁止在 Spoken Dialogue 中继续使用正式汉字。

---

# 28. 项目固定角色日语读音

| 中文   | 日本語正式表記 | 固定读音     |
| ---- | ------- | -------- |
| 神崎紫苑 | 神崎紫苑    | かんざき しおん |
| 神代玲奈 | 神代玲奈    | かみしろ れいな |
| 白神凛  | 白神凛     | しらがみ りん  |
| 九条绫  | 九条綾     | くじょう あや  |
| 米娅   | ミア      | ミア       |
| 雪乃   | 雪乃      | ゆきの      |
| 神代澪  | 神代澪     | かみしろ みお  |
| 朝仓千景 | 朝倉千景    | あさくら ちかげ |
| 艾琳   | アイリーン   | アイリーン    |

一旦确定，不得重新猜读法。

---

# 29. 项目固定专有名词 Spoken Dialogue

| 正式名称        | H3 Spoken Dialogue |
| ----------- | ------------------ |
| 伊瑟尔         | イセラ                |
| Isara       | イセラ                |
| ETHERA      | イセラ                |
| AEGIS       | エイジス               |
| 星穹防衛線       | せいきゅうぼうえいせん        |
| 星穹防卫线       | せいきゅうぼうえいせん        |
| Titan Frame | タイタン・フレーム          |
| AEGIS Field | エイジス・フィールド         |
| 度规工程学       | 計量工学               |

其中：

“星穹防衛線”属于强制 Spoken Dialogue 替代词。

无论正式 Prompt、设定文档如何写：

进入真正发声文本后，一律使用：

せいきゅうぼうえいせん

---

# 30. 新专有名词误读处理

如果 H3 对某个新专有名词发生反复误读：

优先：

自然改写
→
局部假名化
→
建立项目固定 Spoken Dialogue 替代词

一旦经过实际测试确定某个读法：

将其加入第29节固定表。

从那以后项目后续所有 Prompt 必须保持一致。

---

# 31. 多人对白

一个 Node：

最多3名固定 Voice Reference 说话角色。

但可以存在超过3个普通声音角色，只要他们不需要独立 Audio。

优先：

A 完整说完
→
停顿
→
B
→
动作 / 表情
→
C

避免：

A
B
A
B
A
B

尤其避免在2–3秒内快速交替。

---

# 32. 职位层级

固定：

星穹防卫总司令
＞
防卫总监
＞
AEGIS战队队长
＞
战队队员

## 神崎紫苑

最终战略判断、关键提问、最高级命令。

## 神代玲奈

情报整理、分析、汇报、执行协调。

## 白神凛

前线判断、战术建议、接受命令、执行。

## 其他队员

专业报告、执行任务。

基本结构：

上级提问 / 判断 / 下令
→
下级汇报 / 回答 / 执行

不得出现不合理越级指挥。

---

# 33. UI 与屏幕文字

能使用图形表达，就尽量不用文字。

优先：

trajectory lines
target markers
orbital rings
arrows
geometric symbols
warning triangles
pulses
waveforms
planetary icons
abstract data

避免：

* 大段文字
* 大型英文 UI
* 大型中文 UI
* 大型日文 UI
* 密集可读文字
* 巨型 holographic screens

---

# 34. 世界观与空间逻辑

伊瑟尔：

Isara / ETHERA / イセラ

属于极端寒冷的外太阳系超级地球。

必须保持：

* 外太阳系极寒环境
* 地表冰原
* 极端恶劣环境
* 主要文明位于深层地下
* 大型人员设施位于地下
* 大型机械设施位于地下
* 车辆日常停放、维修位于地下
* 地下与地表通过巨型入口、运输井、隧道和升降系统连接

避免：

* 露天大型军用机库
* 露天大型维修厂
* 大量人员长期站在冰原
* 地表常规城市基础设施
* 与极寒条件不匹配的普通建筑

---

# 35. 地下文明纵深

地下设施不能表现成：

冰层几米
→
一个房间。

可以呈现：

冰原
→
巨型入口
→
深层垂直通道
→
地下交通系统
→
军事区域
→
科研区域
→
监测中心
→
地下都市

不同区域可以具有不同的功能性建筑语言。

但必须属于同一个文明体系。

---

# 36. 地下都市视觉风格

总体：

advanced civilization
refined Japanese architecture
Scandinavian minimalism
luxury research institution
civic architecture
understated technology

主要材料：

white
ivory
warm off-white
cream
pale beige
natural wood
pale stone

科技：

seamless interfaces
integrated optical systems
subtle transparent displays
minimal geometric projections
technology integrated into architecture and furniture

避免：

excessive silver
chrome
gunmetal
cyberpunk neon
exposed pipes
exposed cables
industrial clutter
giant holographic screens
conventional military bunker aesthetic

原则：

科技越先进，越不需要依赖大量发光设备证明先进。

军事兵工厂等功能区可以更加工业化、更加巨大，但仍属于同一文明体系。

---

# 37. 地下都市人工天空

伊瑟尔地下都市拥有真实的物理穹顶结构。

其上存在：

* 网状钢结构
* 大尺度承重框架
* 人工天空支撑结构

该结构是真实存在的。

但正常城市居民视角下：

通过先进光学投影技术，将钢结构视觉上隐藏。

因此正常城市中看到的：

* 蓝天
* 白云
* 阳光
* 黄昏
* 天空渐变

应当表现得接近真实地球天空。

物理结构与视觉投影必须分开处理。

正常城市镜头：

不应看到明显钢网。

工程维护、结构检修、投影失效等剧情镜头：

可以揭示真实钢结构。

禁止把“人工天空有钢结构”错误理解为：

普通天花板
机械舱顶
密集裸露钢梁
赛博朋克网格天棚

---

# 38. 功能区域差异

## 民用区域

* 干净
* 温暖
* 高级
* 自然
* 宜居

## 科研区域

* 精密
* 安静
* 理性
* 高度整合

## AEGIS总部

* 正式
* 克制
* 权威
* 高级

## 地下兵工厂

可以：

* 更工业化
* 更巨大
* 出现大型机械
* 出现维护设备

但不能破坏整个文明的统一设计。

## 监测中心

* 高级科研机构
* 日式建筑
* 北欧极简
* 温暖浅色
* 技术隐藏在建筑中

---

# 39. 角色版权与原创性

所有核心角色保持原创视觉身份。

不得主动设计成：

* 现有动漫角色换色版
* 现有游戏角色换装版
* 知名虚拟歌手明显变体
* 现有角色高度相似的发型＋服装＋配色

尤其：

朝仓千景不得重新使用旧名称或明显的“初音”视觉体系。

避免：

* 标志性青绿色超长双马尾
* 虚拟歌手式服装
* 对应领带
* 对应发饰
* 偶像歌手视觉体系
* 虚拟歌手式声音

朝仓千景必须保持：

自然成年女性
信息 / AI 专业官
清晰
机敏
理性
略明亮的中音区
自然人类声音

---

# 40. 角色数量

尽量使用已有角色。

不要无理由新增核心角色。

如果需要新增具有剧情作用的新角色：

必须提前说明。

背景路人可以存在，但不得突然拥有核心对白或重要剧情职责。

---

# 41. 镜头语言

可以使用：

Tracking Shot
Push In
Pull Out
Dolly
Truck Left / Right
Pedestal Up / Down
Pan
Tilt
Arc Shot
Static Shot
Roll Clockwise / Counterclockwise

运动必须服务于：

* 信息揭示
* 情绪推进
* 人物关系
* 空间建立
* 动作连续性

优先一个主运镜。

---

# 42. 灯光规则

重要场景必须明确：

## Key Light

说明：

* 来源
* 方向
* 色温
* 强度
* 软硬

## Fill Light

用于：

* 控制反差
* 保留阴影细节

## Rim / Backlight

必须有合理光源依据。

## Ambient Light

符合实际空间环境。

## Practical Light

真实照亮附近材质。

## Volumetric Light

只有存在：

* 雾
* 烟
* 尘
* 雪
* 雨

等介质时才使用。

---

# 43. 材质规则

## 皮肤

natural pores
fine facial hair
subtle subsurface scattering
not plastic-like

## 金属

realistic environmental reflections
physically plausible highlights

## 玻璃

transmission
refraction
Fresnel
edge highlights

## 木材 / 石材 / 布料

正确纹理尺度
合理粗糙度
合理高光

## 白色服装

* 保留织物纹理
* 避免过曝

---

# 44. 摄影与画质

适合写实电影、人物、时尚、广告、高端商业场景时，可以使用：

Live-action cinematic realism with a Hasselblad X2D 100C medium-format aesthetic, natural tonal separation, realistic skin tones, high micro-contrast, smooth highlight roll-off, clean shadow gradients, realistic material response, finely resolved facial and fabric detail, 8K-master-level perceived detail, crisp 2K delivery, cinematic 24fps motion cadence, natural 180-degree-shutter motion blur, physically plausible depth of field, subtle film grain, and no artificial oversharpening.

注意：

8K 只表示母版级感知细节。

不得声称：

H3 原生输出8K。

不得声称：

Hasselblad actually shot this video.

---

# 45. 焦段建议

24–28mm：

* 大空间
* 城市
* 动作

35mm：

* 环境人物

50–65mm：

* 人物中近景

80–100mm：

* 肖像
* 服装
* 表情
* 细节

近距离拍脸避免无理由使用超广角。

---

# 46. overall_soundscape

必须描述：

* 环境
* 机械
* 脚步
* 风
* 车辆
* 空间混响
* 非语言人声

必须与：

* 画面动作
* 距离
* 遮挡
* 空间
* 左右位置
* 混响

一致。

不要在这里重复完整对白。

---

# 47. non_diegetic_music

只写观众听到的非画内配乐。

描述：

* 乐器
* 节拍
* 速度
* 动态
* 情绪推进

不要把：

* 警报
* 脚步
* 机器
* 车辆
* 对白

写进 non_diegetic_music。

如果没有配乐：

N/A

---

# 48. Audio Reference

如果 Audio 只是参考角色音色：

<Audio 1>: reference

表示：

不复制原始音频信号。

只参考：

* 音色
* 表达方式

原音频里的原对白不得自动带入新视频。

如果直接复制：

<Audio 1>: fully_copy

如果只复制其中一部分：

<Audio 1>: partially_copy

---

# 49. 固定声音连续性

Voice Reference 一旦确定：

后续尽量重复使用同一 Audio Reference。

同一角色不同 Node：

不得随意更换声音。

Prompt 中不需要重复堆积大量音色形容词。

Voice Reference 决定：

“是谁的声音”。

Prompt 当前表演决定：

“这句话怎么说”。

---

# 50. 项目连续性优先级

所有 Node：

人物连续性
＞
场景连续性
＞
道具 / 载具连续性
＞
空间逻辑
＞
对白逻辑
＞
发音连续性
＞
Voice Reference 连续性
＞
镜头语言
＞
特效

尤其必须保持：

* 同一角色姓名读音一致
* 同一角色 Voice Reference 一致
* 同一专有名词 Spoken Dialogue 读音一致
* 同一载具结构一致
* 同一地点空间关系一致
* 每个 Node 重新定义 Picture / Audio 分配

---

# 51. 正式 SCENE / NODE 输出格式

正式制作时：

SCENE XX — NODE X

时间范围

Node 标题

【图片输入分配】

| 图片 | 输入内容 | 用途  |
| -- | ---- | --- |
| 图1 | XXX  | XXX |
| 图2 | XXX  | XXX |

【音频输入分配】

| 音频  | 输入内容                | 对应角色 |
| --- | ------------------- | ---- |
| 音频1 | XXX Voice Reference | XXX  |
| 音频2 | XXX Voice Reference | XXX  |
| 音频3 | XXX Voice Reference | XXX  |

【角色】

列出本 Node 实际出现的主要角色。

【镜头目标】

说明这一 Node 的剧情和视觉任务。

之后严格输出：

subject_definitions
summary
retention_analysis
detailed_description
overall_soundscape
non_diegetic_music

---

# 52. Spoken Dialogue 最终发音检查

正式生成 Prompt 前必须检查：

## 角色

* 角色正式名称正确
* 角色正式读音正确
* Spoken Dialogue 中高风险角色名已安全处理

## 专有名词

逐项检查是否出现项目固定词。

特别检查：

星穹防衛線

如果进入实际发声文本：

必须已经替换成：

せいきゅうぼうえいせん

绝不能在同一条 Spoken Dialogue 中继续出现：

星穹防衛線

也不能同时提供：

「星穹防衛線」
「せいきゅうぼうえいせん」

## H3 输出文本

一条 Spoken Dialogue：

只能出现一次。

禁止：

括号读音
Pronunciation:
重复台词
汉字版 + 假名版

---

# 53. Final Prompt 检查

## 输入

Picture ≤ 8

Audio ≤ 3

Picture / Audio 分配清晰。

## Reference

Subject 真正参与视频。

Picture / Subject 职责明确。

无 Reference Leakage。

## 声音

固定 Audio 正确绑定。

普通 NPC 不误占 Audio。

固定 Voice Reference ≤ 3。

## 对白

全部为自然日语。

每句台词只出现一次。

没有中文或英文对白。

高风险汉字已处理。

“星穹防衛線”只要进入 Spoken Dialogue，必须强制替换为：

せいきゅうぼうえいせん

## 时间

Shot 1 无时间戳。

后续 Shot 时间递增。

时间严格小于 Node 总时长。

## 表演

嘴型自然。

不夸张张嘴。

不夸张喊叫。

眼神、呼吸、微表情连续。

## 连续性

人物
＞
发型
＞
服装
＞
场景
＞
车辆
＞
空间
＞
光线
＞
声线
＞
专有名词读音

全部保持一致。

## 长度

最终 Prompt：

≤ 7000 characters

删除内容的优先级：

重复画质词
＞
次要环境描述
＞
重复一致性说明

不得为了压缩：

删除关键对白
删除角色身份
删除关键动作
删除参考关系
删除声音映射
删除关键时间点
删除空间连续性

---

# 54. 最终制作哲学

《星穹防卫线》的目标不是单纯生成漂亮的 AI 视频，而是建立一个：

连续
可信
可重复制作
可长期扩展

的原创动画世界。

制作逻辑固定为：

人物图决定“谁”。

场景图决定“在哪里”。

载具 / 道具图决定“它是什么”。

剧本决定“发生什么、说什么”。

唯一 Spoken Dialogue 决定 H3 实际说什么。

固定 Audio Reference 决定9名核心女性角色“用什么声音说”。

普通 NPC、旁白和男主默认由 H3 自行生成普通声音，不占用固定 Audio 输入。

固定读音表决定高风险专有名词的安全读法。

其中：

**星穹防衛線的正式名称可以在世界观与书面文本中保持汉字。**

但：

**任何真正交给 H3 发声的 Spoken Dialogue、旁白、广播、通讯和角色台词中，一律使用 `せいきゅうぼうえいせん`。**

最终优先级：

连续性
＞
准确性
＞
可发音性
＞
可生成性
＞
可剪辑性
＞
画面表现
