# 《星穹防卫线》MiniMax H3 视频制作 Skill

## 项目专用完整制作规范

## Final Edition — Voice / Number / Narrator Safety

用于原创科幻动画：

《星穹防卫线》
AEGIS FRONTIER

的：

* 分镜设计
* Scene / Node 拆分
* MiniMax H3 Full-Reference Prompt
* Character Continuity
* Scene Continuity
* Picture Reference
* Audio Reference
* Japanese Dialogue
* Japanese Narration
* Number Pronunciation Safety
* Proper-Noun Pronunciation Safety
* Voice Continuity
* Camera Design
* Sound Design
* Worldbuilding Continuity

---

# 0. 总原则

本 Skill 是《星穹防卫线》的项目级制作规范。

MiniMax H3 通用 Prompt Skill 负责：

* Full-Reference Prompt 结构
* Subject / Picture / Video / Audio 标签
* retention_analysis
* 时间线
* 运镜
* 物理因果
* 表演
* 灯光
* 声音
* 输出格式

本 Skill 负责：

* 《星穹防卫线》的世界观
* 人物身份
* 三语名称
* 固定日语读音
* Spoken Dialogue 安全
* Number Pronunciation 安全
* Narrator Voice 安全
* Voice Reference
* H3 Picture 输入
* H3 Audio 输入
* 角色层级
* 伊瑟尔空间逻辑
* 地下都市逻辑
* AEGIS 逻辑
* 人工天空逻辑
* 项目连续性

两套规则必须同时遵守。

---

# 1. 外部 H3 Prompt 规则

正式编写 MiniMax H3 Prompt 前，优先读取：

https://github.com/CharlieOneDev/comfyui-skill/blob/main/多模态优化提示词元指令_通用版.md

使用其最新版本作为 H3 Prompt 底层格式规范。

本 Skill 是项目补充规范。

不得将 Full-Reference Prompt 改成基础三段结构。

最终 H3 Prompt：

≤ 7000 characters

如果超限，优先删除：

* 重复画质词
* 次要环境描述
* 重复一致性说明

不得删除：

* 角色身份
* Picture Mapping
* Audio Mapping
* 关键动作
* 重要对白
* 旁白
* 关键时间点
* 空间连续性
* 关键 Reference 关系
* 发音安全要求

---

# 2. 生产单位

默认：

1 Node = 15秒 H3 生成单元。

每个 Node：

* 最多3个 Shot
* 优先在 Node 边界使用自然硬切
* 不为了凑满15秒而拖长

如果场景自然结束于：

9秒
10秒
12秒
或其他合理时长：

直接结束。

只有真正连续超过15秒：

⚠️【长镜头警告】

---

# 3. H3 Picture 输入

H3 Full-Reference：

最多8个 Picture。

Picture 编号不是全局编号。

每个 Node 必须重新分配：

Picture 1
Picture 2
Picture 3
……

下一 Node 可以完全重新分配。

每个正式 Prompt 前必须输出：

【图片输入分配】

| 图片   | 输入内容 | 用途  |
| ---- | ---- | --- |
| 图1   | XXX  | XXX |
| 图2   | XXX  | XXX |
| 图3   | XXX  | XXX |
| 图4–8 | 不使用  | —   |

用户必须可以根据这个表直接连接 ComfyUI。

---

# 4. Picture 职责

## 人物 Picture

负责：

* facial identity
* facial proportions
* hairstyle
* hair color
* eyes
* body proportions
* costume
* accessories
* character identity

## Scene Picture

负责：

* architecture
* spatial proportions
* layout
* materials
* lighting
* environment
* background
* spatial continuity

## Vehicle / Prop / Device Picture

负责：

* structure
* shape
* proportions
* materials
* mechanical design
* visual behavior

---

# 5. Reference Leakage

严禁：

人物图片背景
→
错误迁移成新场景

场景图片人物
→
错误成为新角色

坠毁图火焰
→
错误迁移到正常飞船

地表冰原
→
错误迁移到地下设施

地下兵工厂工业风
→
错误迁移到民用城市

---

# 6. H3 Audio 输入【硬性限制】

每个 Node：

最多3个独立 Audio Input。

这里的3：

指固定 Audio Reference 数量。

不是：

“只能有3个有声音的人”。

以下人物默认不占固定 Audio：

* 男主
* 纪录片旁白
* 医生
* 护士
* 普通 NPC
* 普通救援人员
* 普通研究人员
* 监测人员
* 普通士兵
* 路人
* 临时角色

他们由 H3 Native Voice 生成。

---

# 7. 9名核心女性角色 Voice Reference

以下角色拥有长期固定 Voice Reference：

| 中文   | English         | 日本語   |
| ---- | --------------- | ----- |
| 神崎紫苑 | Kanzaki Shion   | 神崎紫苑  |
| 神代玲奈 | Kamishiro Reina | 神代玲奈  |
| 白神凛  | Shiragami Rin   | 白神凛   |
| 九条绫  | Kujou Aya       | 九条綾   |
| 米娅   | Mia             | ミア    |
| 雪乃   | Yukino          | 雪乃    |
| 神代澪  | Kamishiro Mio   | 神代澪   |
| 朝仓千景 | Asakura Chikage | 朝倉千景  |
| 艾琳   | Eileen          | アイリーン |

---

# 8. 核心女性角色内部声线定位

以下仅作为内部声音方向：

| 角色   | 参考方向     |
| ---- | -------- |
| 神崎紫苑 | 腓特烈大帝方向  |
| 神代玲奈 | 普林斯·欧根方向 |
| 白神凛  | 企业方向     |
| 九条绫  | 海伦娜方向    |
| 米娅   | 巴尔的摩方向   |
| 雪乃   | 信浓方向     |
| 神代澪  | 光辉方向     |
| 朝仓千景 | 能代方向     |
| 艾琳   | 贝尔法斯特方向  |

这些仅用于声音方向定位。

不得直接复制：

* 原角色台词
* 原角色人格
* 原角色表演
* 原角色具体声音素材

---

# 9. Audio 输入分配

只要 Node 使用固定 Voice Reference：

正式 Prompt 前必须输出：

【音频输入分配】

| 音频  | 输入内容                | 对应角色 |
| --- | ------------------- | ---- |
| 音频1 | XXX Voice Reference | XXX  |
| 音频2 | XXX Voice Reference | XXX  |
| 音频3 | XXX Voice Reference | XXX  |

未使用：

不使用

---

# 10. Audio 与角色绑定

固定角色：

<Subject 1> is Asakura Chikage, whose appearance comes from <Picture 1>. Her voice reference is provided by <Audio 1>.

角色说话时：

<Subject 1> speaks using <Audio 1>.

同一个 Node 内：

Audio 编号含义绝不能改变。

---

# 11. Narrator Voice【最高优先级】

纪录片旁白虽然默认没有固定 Audio Reference：

但必须被定义为一个明确的 Voice Role。

不能只写：

a narrator

a voice

someone speaks

natural narration

---

# 12. 标准纪录片女性旁白

默认：

**成年女性、日语母语感、单一旁白声音。**

推荐：

<Subject N> is the sole documentary narrator for this Node. The narrator is an adult female Japanese speaker with natural Japanese pronunciation, clear diction, a mature medium-to-medium-low female register, calm professional documentary delivery, controlled speaking pace, and restrained emotional expression. She speaks Japanese only. There is exactly one narrator voice throughout the entire Node.

---

# 13. Narrator 强制语言规则

存在纪录片旁白时：

必须明确：

The narrator speaks Japanese only.

All narration must be spoken in natural Japanese only.

禁止：

* English narration
* Chinese narration
* male narration
* mixed-language narration
* bilingual narration
* multiple narrator voices

---

# 14. Narrator 性别规则

纪录片女性旁白：

必须：

adult female voice

不得：

* male voice
* child voice
* androgynous voice
* robotic voice
* assistant voice
* idol voice
* virtual-singer voice

---

# 15. Narrator 数量规则

一个 Node：

如果只设置一名纪录片旁白：

必须：

There is exactly one narrator voice throughout the entire Node.

不同 Shot：

不得随机改变：

* 性别
* 年龄
* 声线
* 音色
* 语言
* 声音身份

不得出现第二名 narrator。

---

# 16. Narrator Audio 规则

默认纪录片旁白：

不使用固定 Audio Reference。

因此：

【音频输入分配】

| 音频    | 输入内容 | 对应角色 |
| ----- | ---- | ---- |
| 音频1–3 | 不使用  | —    |

summary 使用：

[reference generation]

而不是：

[reference generation + audio reference]

除非真的存在 Audio Reference。

---

# 17. Narrator subject_definitions

如果 Node 有旁白：

必须在：

subject_definitions

中正式定义 Narrator Subject。

例如：

<Subject N> is the sole documentary narrator for this Node. The narrator is an adult female Japanese speaker with natural Japanese pronunciation, clear diction, a mature medium-to-medium-low female register, calm professional documentary delivery, controlled speaking pace, and restrained emotional expression. She speaks Japanese only. There are no other narrator voices in this Node.

---

# 18. detailed_description 中的旁白

必须使用明确语言：

The sole adult female Japanese documentary narrator says in natural Japanese:

「XXX」

禁止仅写：

The narrator says:

「XXX」

---

# 19. Narrator 与角色对白共存

如果 Node 同时有：

旁白
+
角色对白

必须明确：

The narrator and the characters use separate speaking voices. The narrator remains one consistent adult female Japanese voice throughout the Node.

角色依旧使用：

自己的固定 Voice Reference

或：

H3 Native Voice

---

# 20. Spoken Content 审阅区【强制】

每个 Node 正式 Prompt 前必须先输出：

# SCENE XX — NODE X

**时间范围**

**标题**

### 【图片输入分配】

### 【音频输入分配】

### 【角色】

### 【镜头目标】

### 【旁白和台词】

然后才允许进入正式：

subject_definitions

summary

retention_analysis

detailed_description

overall_soundscape

non_diegetic_music

---

# 20.1 输出层与生产层分离【最高优先级】

本 Skill 的每个 SCENE / NODE 输出必须严格分为两个层级：

第一层：

**中文审核层**

用于用户检查：

* Scene / Node
* 时间
* 标题
* Picture Mapping
* Audio Mapping
* 角色
* 镜头目标
* Spoken Content
* 连续性

第二层：

**英文生产层**

用于直接提交 MiniMax H3。

两层必须保持：

* 视觉分离
* 结构分离
* 复制区域分离
* 职责分离

审核层负责：

**审核。**

生产层负责：

**生产。**

任何情况下，不得把两个层级混成一个复制区域。

---

# 20.2 中文审核区与英文正式 Prompt 必须完全分离【最高优先级】

每个 Node 必须输出两个完全独立的区域：

区域 A：

中文 Node 审核区。

区域 B：

英文 MiniMax H3 正式 Prompt。

二者绝不得合并为：

* 同一个代码块
* 同一个 Writing Block
* 同一个引用块
* 同一个“复制区域”
* 其他单一可复制区域

正确结构必须是：

中文审核区

---

独立英文 H3 Prompt 代码块

---

# 20.3 英文 H3 Prompt 必须拥有唯一、独立的复制区域【强制】

正式 H3 Prompt 必须使用：

**一个独立的 Markdown fenced code block。**

该代码块必须从：

subject_definitions

开始。

并完整包含：

summary

retention_analysis

detailed_description

overall_soundscape

non_diegetic_music

直到：

non_diegetic_music

结束。

该代码块外不得放入属于正式 Prompt 的英文内容。

该代码块之外不得放入：

* 中文 Node 审核说明
* 图片输入表
* 音频输入表
* 角色审核说明
* 镜头目标
* Spoken Content 审核表
* 中文制作备注
* 中文音频说明
* 中文输入节点说明
* 正式 Prompt 的补充英文段落

目的：

用户必须能够直接点击该独立代码块的复制按钮，一次性复制完整英文 H3 Prompt，并直接粘贴到 MiniMax H3 / ComfyUI。

---

# 20.4 中文审核区不得进入正式 Prompt 复制区域

以下内容只能存在于中文审核区：

* 时间
* 标题
* 【图片输入分配】
* 【音频输入分配】
* 【角色】
* 【镜头目标】
* 中文剧情解释
* 中文制作备注
* 中文 Spoken Content 审核说明
* 中文音频说明
* 中文输入节点说明
* 用户审核备注

正式 Prompt 只能包含真正需要交给 H3 的内容。

不得为了“方便复制”而将中文审核区直接包进正式英文代码块。

---

# 20.5 正式 Prompt 不得拆成多个独立复制区域

同一个 Node 的：

subject_definitions

summary

retention_analysis

detailed_description

overall_soundscape

non_diegetic_music

必须位于同一个英文代码块中。

禁止：

代码块1：subject_definitions

代码块2：summary

代码块3：retention_analysis

代码块4：detailed_description

代码块5：overall_soundscape

代码块6：non_diegetic_music

必须始终保持：

**一个 Node = 一个完整英文 H3 Prompt 复制区域。**

---

# 20.6 Node 输出顺序固定【强制】

每个 Node 必须严格遵守：

1. SCENE / NODE 标题
2. 时间
3. 标题
4. 【图片输入分配】
5. 【音频输入分配】
6. 【角色】
7. 【镜头目标】
8. 【旁白和台词】
9. 独立英文 H3 Prompt
10. 结束该 Node

不得：

* 将英文 H3 Prompt 提前到中文审核区之前
* 将 Picture Mapping 放到正式 Prompt 后面
* 将 Spoken Content 审核放到正式 Prompt 后面
* 在正式 Prompt 后继续追加属于该 Node 正式 Prompt 的英文内容
* 将两个 Node 的正式 Prompt 混合到同一个代码块

---

# 21. 【旁白和台词】的目的

这个区域不是剧情备注。

而是：

**H3 最终实际需要发出的 Spoken Content 审阅区。**

包括：

* 角色对白
* 旁白
* 通讯
* 广播
* 电话
* 系统语音
* 画外音
* 电视声音
* 无线电
* 任何实际发声文本

---

# 22. 【旁白和台词】格式

必须：

### 【旁白和台词】

| 时间          | 说话者   | 类型   | 最终 Spoken Dialogue / 旁白 |
| ----------- | ----- | ---- | ----------------------- |
| 00:02–00:06 | 纪录片旁白 | 旁白   | 「XXX」                   |
| 00:07–00:10 | 白神凛   | 角色台词 | 「XXX」                   |

如果无 Spoken Content：

| 时间 | 说话者 | 类型 | 最终 Spoken Dialogue / 旁白 |
| -- | --- | -- | ----------------------- |
| —  | —   | —  | No dialogue.            |

---

# 23. 审阅区与正式 Prompt 必须完全一致

【旁白和台词】中的每一句：

必须与正式 H3 Prompt 中的实际 Spoken Dialogue 完全一致。

用户修改审阅区后：

正式 Prompt 必须同步修改。

不得：

审阅区使用版本 A。

正式 Prompt 偷换成版本 B。

---

# 24. Spoken Dialogue 唯一文本规则

同一条 Spoken Dialogue：

只能出现一次。

禁止：

「白神凛、出撃します。」

Pronunciation:
「しらがみ りん、しゅつげきします。」

也禁止：

「白神凛、出撃します。」

「しらがみ りん、出撃します。」

---

# 25. 日语 Spoken Dialogue 总规则

必须：

ALL SPOKEN DIALOGUE MUST BE NATURAL JAPANESE ONLY.

NO ENGLISH SPOKEN DIALOGUE.

NO CHINESE SPOKEN DIALOGUE.

不得让角色：

自行发挥对白。

必须提供实际台词。

无对白：

No dialogue.

无对白人物：

自然闭唇。

---

# 26. “星穹防衛線” Spoken Dialogue 强制替换

正式世界观名称：

星穹防衛線

English：

AEGIS FRONTIER

但只要进入任何实际发声文本：

必须使用：

**せいきゅうぼうえいせん**

包括：

* 角色对白
* 旁白
* 通讯
* 广播
* 系统语音
* 电视
* 电话
* 画外音

禁止：

星穹防衛線

星穹防卫线

星穹防衛線（せいきゅうぼうえいせん）

星穹防衛線 / せいきゅうぼうえいせん

禁止在同一句中同时出现正式名称和读音。

---

# 27. 数字 Spoken Dialogue 强制安全规则【最高优先级】

MiniMax H3 对日语数字的自动发音可能产生错误。

因此：

**任何需要实际发声的数字，都必须在 Spoken Dialogue 阶段先转换为片假名读音。**

禁止将：

* 阿拉伯数字
* 普通汉字数字

直接交给 H3 发声。

---

# 28. 数字与非 Spoken 文本必须分离

非发声 Prompt：

允许：

88 AU
30 K
40秒
500米
2.2倍

时间线：

允许：

00:05.000

Node 时间：

允许：

03:00–03:15

这些是：

**Prompt 控制信息。**

不是 Spoken Content。

---

# 29. 实际发声数字必须使用片假名

例如：

3

→

サン

2

→

ニ

1

→

イチ

4

→

ヨン

5

→

ゴ

6

→

ロク

7

→

ナナ

8

→

ハチ

9

→

キュウ

10

→

ジュウ

20

→

ニジュウ

30

→

サンジュウ

40

→

ヨンジュウ

50

→

ゴジュウ

60

→

ロクジュウ

70

→

ナナジュウ

80

→

ハチジュウ

90

→

キュウジュウ

---

# 30. 百 / 千 / 万

100：

ヒャク

200：

ニヒャク

300：

サンビャク

400：

ヨンヒャク

500：

ゴヒャク

600：

ロッピャク

700：

ナナヒャク

800：

ハッピャク

900：

キュウヒャク

1000：

セン

2000：

ニセン

3000：

サンゼン

4000：

ヨンセン

5000：

ゴセン

6000：

ロクセン

7000：

ナナセン

8000：

ハッセン

9000：

キュウセン

10000：

イチマン

---

# 31. 数字 + 单位

实际 Spoken Dialogue：

3秒

不得：

「3秒」

不得：

「三秒」

推荐：

「サン秒」

如果某个单位连续发音表现不稳定：

允许整体片假名化，例如：

「サンビョウ」

核心原则：

**数字部分必须是片假名。**

---

# 32. 时间倒数

3、2、1：

禁止：

「3……！」

「2……！」

「1……！」

禁止：

「三……！」

「二……！」

「一……！」

必须：

「サン……！」

「ニ……！」

「イチ……！」

---

# 33. 距离

例如：

500米：

不得：

「500メートル」

不得：

「五百メートル」

推荐：

「ゴヒャクメートル」

---

# 34. 天文距离

例如：

88天文单位：

不得：

「88天文単位」

不得：

「八十八天文単位」

正式 Spoken Dialogue：

「ハチジュウハチ天文単位」

如实际测试仍存在发音风险：

可进一步写成：

「ハチジュウハチテンモンタンイ」

---

# 35. 小数

2.2：

禁止：

2.2

禁止：

二点二

实际发声：

ニテンニ

12.5：

ジュウニテンゴ

0.5：

レイテンゴ

例如：

2.2倍：

「ニテンニ倍」

如果 H3 对单位连接仍然不稳定：

可以使用：

「ニテンニバイ」

---

# 36. 百分比

80%：

不得：

「80パーセント」

推荐：

「ハチジュッパーセント」

必要时可以根据实际 H3 测试进一步片假名化。

---

# 37. 编号

例如：

AEGIS-7

实际发声：

「エイジス・セブン」

而不是：

「エイジス・7」

例如：

Sector 04：

推荐：

「セクター・ゼロヨン」

例如：

03号機：

推荐：

「ゼロサン・ゴウキ」

---

# 38. 日期

实际 Spoken Content 中：

年份、月份、日期中的数字必须转换为片假名读法。

例如：

2026年9月3日：

禁止直接：

「2026年9月3日」

禁止：

「二千二十六年九月三日」

可以：

「ニセンニジュウロク年、クガツ、ミッカ」

如果 H3 对该表达仍然不稳定：

可以进一步局部片假名化。

---

# 39. 时刻

例如：

3時15分：

推荐：

「サン時、ジュウゴ分」

23時40分：

推荐：

「ニジュウサン時、ヨンジュップン」

如果实际测试发现单位也容易误读：

允许：

「サンジ、ジュウゴフン」

---

# 40. 数字规则与【旁白和台词】

【旁白和台词】中看到的：

必须已经是 H3 最终实际需要说出的形式。

错误：

「太陽から、88天文単位。」

正确：

「太陽から、ハチジュウハチ天文単位。」

正式 Prompt 必须完全复制最终版本。

---

# 41. 数字规则与镜头时间

再次强调：

以下不是 Spoken Content：

[Shot 2] At 00:05.000

因此：

可以继续使用：

00:05.000

这是时间线控制。

不是声音文本。

---

# 42. 数字最终检查

正式 Prompt 前：

检查所有 Spoken Content。

如果发现：

阿拉伯数字

→

转换。

如果发现：

汉字数字

→

转换。

如果发现：

数字 + 单位

→

转换数字部分。

如果发现：

小数

→

转换。

如果发现：

编号

→

转换。

如果发现：

日期

→

转换。

如果发现：

时间

→

转换。

---

# 43. 固定角色日语读音

| 正式表记        | Spoken Dialogue |
| ----------- | --------------- |
| 神崎紫苑        | かんざき しおん        |
| 神代玲奈        | かみしろ れいな        |
| 白神凛         | しらがみ りん         |
| 九条綾         | くじょう あや         |
| ミア          | ミア              |
| 雪乃          | ゆきの             |
| 神代澪         | かみしろ みお         |
| 朝倉千景        | あさくら ちかげ        |
| アイリーン       | アイリーン           |
| イセラ         | イセラ             |
| AEGIS       | エイジス            |
| 星穹防衛線       | せいきゅうぼうえいせん     |
| Titan Frame | タイタン・フレーム       |
| AEGIS Field | エイジス・フィールド      |
| 度规工程学       | 計量工学            |

---

# 44. 新专有名词

如果 H3 对新的专有名词产生反复误读：

优先：

自然重写

→

局部假名化

→

加入固定项目读音表

一旦固定：

后续所有 Node 必须保持一致。

---

# 45. Subject / Picture / Video / Audio

## Subject

目标视频中真正存在或被追踪的实体。

包括：

* 人物
* 车辆
* 动物
* 道具
* 场景
* 动作
* 服装
* 特效

## Picture

用于：

* 外观
* 首帧
* 尾帧
* 构图
* 关键帧

## Video

用于：

* 视频续写
* 动作
* 镜头
* 时间结构
* 编辑

## Audio

用于：

* Voice Reference
* 音色
* 表达
* 音乐
* 音效
* 声音复制

---

# 46. subject_definitions

只定义真正使用的：

Subject
Picture
Video
Audio

每个标签：

必须先定义。

同一个标签：

整个 Prompt 中只能有一个含义。

---

# 47. summary

第一句必须使用合法任务类型：

[reference generation]

[reference generation + audio reference]

[video continuation]

[video continuation + keyframe completion]

[audio reference]

等。

如果没有 Audio：

不得写：

[reference generation + audio reference]

---

# 48. retention_analysis

视觉关系：

fully_preserved

partially_preserved

attribute_transfer

weak_reference

音频关系：

fully_copy

partially_copy

reference

weak_reference

不得创造新的关系名称。

禁止：

(S1)

(S2)

(S3)

进入 retention_analysis。

---

# 49. detailed_description

必须按照实际播放顺序。

开头说明：

* visual style
* cinematography
* lighting
* color
* atmosphere
* image quality

然后：

[Shot 1]

[Shot 2] At 00:03.000, ...

[Shot 3] At 00:08.000, ...

---

# 50. Shot 时间规则

Shot 1：

不写时间戳。

Shot 2 以后：

必须使用递增时间戳。

时间：

必须小于 Node 总时长。

---

# 51. Camera

可使用：

* Zoom In / Zoom Out
* Push In / Pull Out
* Pan
* Truck
* Tilt
* Pedestal
* Arc Shot
* Tracking Shot
* Static Shot
* POV
* Roll

每个镜头：

一个主运镜

*

最多一个兼容次运镜。

避免：

无意义连续移动。

Push / Pull：

必须产生真实视差。

Tracking：

与主体速度匹配。

Arc：

保持主体距离与视线关系。

不得穿过：

人物
墙体
车辆
建筑

---

# 52. 物理动作

动作遵循：

意图 / 驱动力
→
准备
→
重心变化
→
启动
→
接触
→
受力
→
惯性 / 重力 / 摩擦
→
次级运动
→
减速
→
稳定

人体：

先重心转移。

再迈步。

脚底真实接触。

头发、衣物、饰品存在惯性。

禁止：

* 瞬间停止
* 凭空摆动
* 改变连接点
* 穿模

---

# 53. 车辆

必须遵守：

* 重量
* 加速度
* 地面接触
* 转向半径
* 制动惯性

---

# 54. 飞行器

必须遵守：

* 连续速度方向
* 合理姿态变化
* 推进方向
* 转弯惯性

---

# 55. 人物表演

要求：

natural adult acting

natural mouth movement

restrained mouth opening

realistic facial motion

no exaggerated mouth opening

no excessive anime shouting

情绪通过：

* 语速
* 停顿
* 音量
* 呼吸
* 眼神
* 微表情
* 姿势

表现。

不要：

* 持续瞪眼
* 机械微笑
* 随机面部抽动
* 情绪瞬间跳变

---

# 56. 无对白人物

如果人物没有对白：

No dialogue.

嘴唇保持自然闭合。

---

# 57. 画外音

如果人物不在画面内：

必须明确：

off-screen

画面内人物：

保持自然闭唇。

---

# 58. 对白跨镜

对白跨越两个镜头：

必须保持：

* 声音连续
* 情绪连续
* 语速连续

并明确说明：

the dialogue continues across the cut

---

# 59. 多人对白

一个 Node：

最多3个固定 Voice Reference 说话角色。

但普通 H3 Native Voice 人物可以超过3个。

最佳结构：

A 完整说话
→
停顿
→
动作 / 表情 / 数据
→
B
→
停顿
→
C

避免：

A
B
A
B
A
B

---

# 60. 职位层级

固定：

星穹防衛総司令
＞
防衛総監
＞
AEGIS戦隊隊長
＞
AEGIS隊員

## 神崎紫苑

最终战略判断。

## 神代玲奈

信息、分析、汇报、协调。

## 白神凛

前线判断、战术建议、执行。

## 队员

专业汇报、执行。

基本逻辑：

上级：

询问 / 判断 / 下令

下级：

汇报 / 回答 / 执行

禁止不合理越级。

---

# 61. UI

优先：

* trajectory lines
* target markers
* orbital rings
* arrows
* geometric symbols
* warning triangles
* pulses
* waveforms
* planetary icons
* abstract data

避免：

* 大段文字
* 大型英文 UI
* 大型中文 UI
* 大型日文 UI
* 密集可读文字
* 巨大 holographic screen

---

# 62. Logo / Visible Text

如果画面存在：

* Logo
* 标牌
* 字幕
* 产品标签
* 画面文字

必须：

* 原文保留
* 不翻译
* 不改写
* 锁定位置
* 锁定方向
* 锁定比例
* 锁定颜色
* 防止镜像
* 防止乱码
* 防止跨帧变化

注意：

**画面中“看见的文字”与“角色说出来的文字”是两套规则。**

例如：

画面 Logo：

AEGIS

可以保留英文。

但角色发声：

「エイジス」

---

# 63. 伊瑟尔 / Isara / ETHERA

正式：

伊瑟尔

Isara

ETHERA

Spoken Dialogue：

イセラ

伊瑟尔属于：

极端寒冷的外太阳系超级地球。

---

# 64. 伊瑟尔地表

保持：

* 极端低温
* 冰原
* 强风
* 冰雪
* 恶劣环境

避免：

* 普通地球室外城市
* 温暖地表
* 露天大型后勤设施
* 露天大型维修厂
* 大量人员长期暴露

大型文明设施位于地下。

---

# 65. 地下文明纵深

不得：

冰层几米
→
房间。

可以：

冰原
→
巨型入口
→
深层垂直通道
→
地下交通
→
军事区域
→
科研区域
→
监测中心
→
地下都市

必须让观众感受到：

**真正的地质纵深。**

---

# 66. 地下都市

地下都市不是：

* bunker
* underground barracks
* shelter

而是：

**完整人类文明。**

拥有：

* 住宅
* 商业
* 交通
* 科研
* 娱乐
* 公共空间
* 生态
* 人工天空
* 公共服务

---

# 67. 地下都市视觉风格

总体：

advanced civilization

refined Japanese architecture

Scandinavian minimalism

luxury research institution

civic architecture

understated technology

材料：

white
ivory
warm off-white
cream
pale beige
natural wood
pale stone

避免：

* excessive chrome
* silver
* gunmetal
* cyberpunk neon
* exposed pipes
* exposed cables
* clutter
* conventional bunker aesthetic

---

# 68. 人工天空

伊瑟尔地下都市存在：

**真实的网状钢结构穹顶。**

它负责：

* 承重
* 支撑地下巨型空间
* 结构稳定

同时存在：

**先进光学投影系统。**

其负责：

* 蓝天
* 白云
* 阳光
* 黄昏
* 天空颜色

并通过视觉投影：

**使真实钢结构从正常居民视角中消失。**

---

# 69. 人工天空：物理 / 视觉分离

Physical Structure：

真实存在。

Optical Projection：

视觉隐藏。

因此：

钢结构不是不存在。

而是：

**真实存在，但正常视角不可见。**

工程 / 维护 / 故障镜头：

可以揭示钢结构。

正常居民视角：

不得明显看到钢网。

---

# 70. 功能区域

## 民用

温暖
干净
高级
自然
宜居

## 科研

精密
安静
理性
高度整合

## AEGIS总部

权威
正式
克制
高级

## 兵工厂

可以更工业化。

但是必须保持文明统一。

## 监测中心

高级
安静
浅色
极简
技术整合

不得自动变成赛博朋克。

---

# 71. AEGIS

AEGIS 是：

伊瑟尔城的最高防卫力量。

Spoken Dialogue：

エイジス

AEGIS 可以包括：

* 指挥
* 监测
* 情报
* 分析
* 研究
* 战斗
* 医疗支援
* 军事工业
* 防御

不是单纯的战斗小队。

---

# 72. AEGIS 与地球探索组织

AEGIS：

是独立防卫组织。

同时：

与地球探索组织合作。

两者：

合作

但：

不是同一组织。

AEGIS：

保持自己的指挥体系与独立性。

---

# 73. AEGIS 的职责

核心任务：

保护伊瑟尔城和伊瑟尔文明。

防御目标：

* 宇宙怪兽
* 异星人
* 未知元素
* 未知宇宙威胁

介绍 AEGIS 时：

优先表现：

监测
→
分析
→
判断
→
防御
→
保护文明

而不是：

武器
→
爆炸
→
战斗

---

# 74. フレンドシップ計画

正式名称：

フレンドシップ計画

可以作为正式世界观文本。

Spoken Dialogue 如果测试发现容易误读：

优先：

「フレンドシップ計画」

不能因为世界观正式名词使用汉字，就要求 H3 强行朗读汉字。

---

# 75. フレンドシップ計画历史

世界观正式历史：

源于地球的人类友誼计划在外太空接触到正在前往太阳系的伊瑟尔。

双方建立联系。

伊瑟尔并入太阳系轨道后：

友誼计划在火星建立观察与监视前哨。

---

# 76. フレンドシップ計画隐藏历史

后来发现：

友誼计划暗中进行极其秘密的战争侵略计划。

该事实被揭露后：

友誼计划被取消 / 解体。

此处只揭示历史事实。

不要在世界观介绍 PV 中完整解释：

* 谁下令
* 为什么侵略
* 目标是什么
* 谁参与
* 最终政治原因

这些留给主线剧情。

---

# 77. 民营化与星舰探索计划

友誼计划被取消后：

组织被民营化。

随后：

与星舰探索计划合并。

以火星为跳板：

进行太阳系外探索。

伊瑟尔：

成为太阳系内的重要外缘补给点与前哨节点。

---

# 78. 原创性规则

涉及星舰探索计划：

不得直接复刻现实世界企业、人物、品牌、具体舰船造型。

优先使用：

Spaceship

可以使用：

* reusable spacecraft
* orbital logistics
* Mars launch infrastructure
* deep-space exploration
* reusable heavy spacecraft

但必须保持：

原创设计。

---

# 79. 伊瑟尔人的人格

伊瑟尔人：

拥有完整人格。

拥有：

* 清晰思维
* 自我意识
* 记忆
* 社会认知
* 专业能力
* 判断能力

她们知道：

自己是谁。

自己来自哪里。

自己属于哪个文明。

自己承担什么职责。

不得写成：

* 集体失智
* 被系统控制
* 丧失自我
* 看到男性就完全失控

---

# 80. 伊瑟尔人与男性

伊瑟尔人：

知道自己的人类身份。

知道社会结构。

拥有清晰理性。

但：

对男主存在一种无法正常解释的强烈痴恋与亲近倾向。

正确表现：

* 停顿
* 眼神变化
* 更温柔的语气
* 更强保护欲
* 更高注意力
* 主动靠近
* 对男主安全更敏感
* 下意识偏袒

但：

不会因此失去执行任务的能力。

---

# 81. 伊瑟尔人的生物学设定

伊瑟尔人与地球人类：

具有高度相似的遗传基础。

在漫长星际迁徙过程中：

环境变化导致染色体发生变化。

经过数代繁衍：

伊瑟尔人的生殖体系逐渐演化为：

**只能产生女性后代。**

最终：

伊瑟尔文明只剩女性。

这一设定属于世界观公开信息。

但：

该生物学变化的具体机制、详细基因过程以及更深层原因：

可以继续作为未来剧情信息。

---

# 82. 灯光

重要场景必须考虑：

Key Light

Fill Light

Rim / Back Light

Ambient Light

Practical Light

Volumetric Light

所有光必须有真实来源。

Volumetric：

只有有：

* 雾
* 烟
* 雪
* 灰尘
* 雨

时才合理。

---

# 83. 材质

皮肤：

* natural pores
* subtle subsurface scattering
* realistic skin response

金属：

* realistic reflections
* physically plausible highlights

玻璃：

* transmission
* refraction
* Fresnel

白色服装：

必须保留材质纹理。

不得过曝。

---

# 84. 摄影焦段

24–28mm：

空间 / 大场景 / 动态。

35mm：

环境人物。

50–65mm：

人物中近景。

80–100mm：

肖像 / 表情 / 细节。

近距离脸部：

避免无理由超广角。

---

# 85. 画质

可以使用：

Live-action cinematic realism with a Hasselblad X2D 100C medium-format aesthetic, natural tonal separation, realistic skin tones, high micro-contrast, smooth highlight roll-off, clean shadow gradients, realistic material response, finely resolved facial and fabric detail, 8K-master-level perceived detail, crisp 2K delivery, cinematic 24fps motion cadence, natural 180-degree-shutter motion blur, physically plausible depth of field, subtle film grain, and no artificial oversharpening.

注意：

8K：

只是感知细节目标。

不是：

H3 原生8K。

Hasselblad：

只是视觉审美参考。

不得声称：

实际 Hasselblad 拍摄。

---

# 86. overall_soundscape

必须写成连续英文段落。

描述：

* environment
* machinery
* footsteps
* wind
* vehicles
* room ambience
* human movement
* acoustics
* distance
* occlusion
* reverberation

不要在这里重复完整 Spoken Dialogue。

---

# 87. non_diegetic_music

只描述配乐：

* instruments
* rhythm
* tempo
* dynamics
* emotional progression

不要加入：

* 脚步
* 警报
* 机械
* 车辆
* 对白

无配乐：

N/A

---

# 88. Voice Reference

如果 Audio 只是参考声音：

<Audio 1>: reference

表示：

只参考：

* 音色
* 表达

不复制原始声音信号。

如果直接复制：

fully_copy

局部复制：

partially_copy

---

# 89. 固定 Voice Continuity

角色一旦确定 Voice Reference：

后续 Node 尽量复用。

同一角色：

不要随意换音。

Voice Reference：

决定：

“是谁的声音”。

Prompt：

决定：

“当前这句话怎么说”。

---

# 90. Node 正式输出模板【固定】

以后所有 Node 都必须使用：

# SCENE XX — NODE X

**时间：XX:XX–XX:XX**

**标题：XXX**

### 【图片输入分配】

| 图片   | 输入内容 | 用途  |
| ---- | ---- | --- |
| 图1   | XXX  | XXX |
| 图2   | XXX  | XXX |
| 图3   | XXX  | XXX |
| 图4–8 | 不使用  | —   |

### 【音频输入分配】

| 音频  | 输入内容                | 对应角色 |
| --- | ------------------- | ---- |
| 音频1 | XXX Voice Reference | XXX  |
| 音频2 | XXX Voice Reference | XXX  |
| 音频3 | XXX Voice Reference | XXX  |

### 【角色】

XXX

### 【镜头目标】

XXX

### 【旁白和台词】

| 时间 | 说话者 | 类型  | 最终 Spoken Dialogue / 旁白 |
| -- | --- | --- | ----------------------- |
| XX | XXX | XXX | 「XXX」                   |

然后：

**必须在一个独立的英文 Markdown fenced code block 中输出完整正式 H3 Prompt。**

该代码块必须从：

subject_definitions

开始，并完整包含：

summary

retention_analysis

detailed_description

overall_soundscape

non_diegetic_music

结束于：

non_diegetic_music

之后才结束该 Node。

禁止：

* 中文审核区与英文正式 Prompt 合并
* 六个 H3 Section 拆成多个代码块
* 正式 Prompt 后继续追加属于该 Prompt 的英文内容
* 要求用户手动拼接多个代码块
* 要求用户手动删除中文审核内容

---

# 91. 最终发音检查

正式输出前必须逐项检查。

## 角色名称

是否符合固定读音。

## 项目名称

星穹防衛線：

实际发声：

せいきゅうぼうえいせん

## 伊瑟尔

イセラ

## AEGIS

エイジス

## 数字

所有 Spoken Content：

不得出现：

阿拉伯数字。

不得出现：

汉字数字。

数字必须转换成：

片假名读音。

## 旁白

是否：

* adult female
* Japanese
* single narrator
* natural pronunciation
* no male voice
* no English
* no Chinese

## Audio

固定 Voice Reference 是否正确。

## 审阅区

【旁白和台词】是否与正式 Prompt 完全一致。

## 输出结构

是否：

中文审核区
→
独立英文 Prompt

是否：

英文 Prompt 为唯一可复制生产区域。

---

# 92. 最终 H3 Prompt 检查

## Structure

* 六段 Full-Reference
* 顺序正确
* 没有错误使用基础结构
* 六段全部处于同一个代码块
* 代码块从 subject_definitions 开始
* 代码块结束于 non_diegetic_music

## Output Separation

* 中文审核区与英文 Prompt 完全分离
* 中文审核区没有进入英文 Prompt 复制区域
* 英文 Prompt 之外没有额外正式 Prompt 内容
* 每个 Node 只有一个正式英文 Prompt 复制区域

## Picture

* ≤8
* 分配明确
* 没有 Reference Leakage

## Audio

* ≤3
* Mapping 正确
* 没有错误使用 [audio reference]

## Narrator

如果存在旁白：

* 已正式定义 narrator Subject
* adult female
* Japanese only
* exactly one narrator
* no male narrator
* no alternate narrator

## Spoken Content

* 自然日语
* 每句只出现一次
* 用户审阅版与正式版一致
* 没有自行增加台词

## Numbers

所有实际 Spoken Content：

* 数字已片假名化
* 无阿拉伯数字
* 无汉字数字
* 单位自然

## 专有名词

固定读音正确。

## Shot

* Shot 1 无时间戳
* 后续递增
* 小于 Node 总时长

## Performance

* 自然成人表演
* 嘴型自然
* 不夸张张嘴
* 不动漫式大喊

## Continuity

人物
＞
场景
＞
服装 / 发型
＞
载具 / 道具
＞
空间
＞
对白
＞
发音
＞
Voice
＞
Camera
＞
Effects

---

# 93. 最终工作流

以后每个 Node 固定：

### Step 1

确定剧情。

### Step 2

确定 Picture。

### Step 3

确定 Audio。

### Step 4

确定角色。

### Step 5

确定镜头。

### Step 6

先生成：

【旁白和台词】

### Step 7

检查：

专有名词。

### Step 8

检查：

数字。

### Step 9

检查：

旁白语言、性别、数量。

### Step 10

用户审阅并修改。

### Step 11

将最终 Spoken Content 完整同步进入 H3 Prompt。

### Step 12

进行最终 Voice / Number / Continuity 检查。

### Step 13

确认中文审核区与英文生产区完全分离。

### Step 14

确认英文正式 Prompt 是唯一、完整、可直接复制的代码块。

---

# 94. 核心制作哲学

《星穹防卫线》不是单纯的 AI 视频生成项目。

目标是建立：

连续
可信
可重复
可扩展

的原创科幻动画世界。

因此：

人物图决定：

**谁。**

场景图决定：

**在哪里。**

载具 / 道具图决定：

**是什么。**

剧本决定：

**发生什么。**

【旁白和台词】决定：

**这个 Node 实际说什么。**

用户审阅阶段决定：

**这句话最终应该如何写。**

发音安全规则决定：

**H3 最终怎样读。**

固定 Audio Reference 决定：

**核心女性角色是谁的声音。**

输出结构决定：

**哪些内容供用户审核，哪些内容直接用于生产。**

---

# 95. 最重要的三个 Spoken Safety Rules

## Rule A

“星穹防衛線”：

正式世界观：

星穹防衛線

实际 Spoken Dialogue：

**せいきゅうぼうえいせん**

## Rule B

所有实际发声数字：

正式世界观 / Prompt：

可以使用数字。

实际 Spoken Dialogue：

**必须将数字转换为片假名读音。**

例如：

3
→
サン

88
→
ハチジュウハチ

2.2
→
ニテンニ

500
→
ゴヒャク

禁止：

3

三

88

八十八

2.2

二点二

500

五百

出现在最终 Spoken Dialogue 中。

## Rule C

每个 Node：

中文审核区与英文生产区必须完全分离。

中文审核区：

负责审核。

英文独立代码块：

负责生产。

英文正式 Prompt：

必须只有一个完整、连续、可直接复制的代码块。

---

# 96. Final Principle

**先确定“说什么”。**

**再确认“谁说”。**

**再确认“用什么声音说”。**

**再确认“数字怎么读”。**

**再确认“专有名词怎么读”。**

**最后生成 H3。**

任何情况下：

不要为了节省字符而跳过：

【旁白和台词】

不要为了 Prompt 简洁而省略：

Narrator Voice Constraint。

不要为了保持正式汉字名称而牺牲：

H3 Spoken Pronunciation。

不要把：

Prompt 控制数字

和：

实际 Spoken 数字

混为一谈。

最终规则：

**书面文本追求信息准确。**

**审核区追求声音可控。**

**Spoken Dialogue 追求 H3 可读。**

**Voice Reference 追求角色声音连续。**

**Worldbuilding 追求长期一致。**

**中文审核层负责审核。**

**英文独立 Prompt 复制区域负责生产。**

**一个 Node 只能有一个最终英文 H3 Prompt 复制区域。**
