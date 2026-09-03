# 《星穹防卫线》MiniMax H3 视频制作 Skill

## 项目最终版

用于原创科幻动画《星穹防卫线 / AEGIS FRONTIER》的：

* 剧情分镜设计
* 15秒 Node 拆分
* MiniMax H3 Full-Reference Prompt 编写
* 固定 Voice Reference 管理
* 日语对白
* 旁白
* 镜头设计
* 声音设计
* 图片输入管理
* 音频输入管理
* 世界观连续性
* 场景连续性
* 人物连续性
* H3 日语发音安全

---

# 0. 规则层级

本项目同时遵循两套规则。

## A. MiniMax H3 通用 Prompt 规则

来源：

https://github.com/CharlieOneDev/comfyui-skill/blob/main/多模态优化提示词元指令_通用版.md

每次正式编写 H3 Prompt 前，优先读取该文档最新版本。

该文档负责：

* Full-Reference Prompt 结构
* Subject / Picture / Video / Audio 标签
* retention_analysis
* 时间线
* 运镜
* 物理因果
* 人物表演
* 灯光
* 声音
* Prompt 输出规则

## B. 《星穹防卫线》项目规则

本 Skill 负责：

* 世界观
* 人物
* 人物身份
* 三语名称
* 日语固定读音
* Spoken Dialogue 发音安全
* 旁白和台词审阅
* 9名核心女性角色 Voice Reference
* Audio 输入限制
* 图片输入逻辑
* 空间逻辑
* 职位体系
* 对白逻辑
* 连续性
* 伊瑟尔文明逻辑
* 地下都市逻辑
* 人工天空逻辑

两套规则必须同时遵守。

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

只有真正存在超过15秒的连续镜头时，才标记：

⚠️【长镜头警告】

---

# 2. H3 图片输入

H3 Full-Reference：

最多8个 Picture。

Picture 编号不是全局编号。

每个 Node 必须重新定义：

Picture 1
Picture 2
Picture 3
……

下一 Node 可以重新排列。

因此，正式 Prompt 前必须输出：

## 【图片输入分配】

| 图片   | 输入内容 | 用途  |
| ---- | ---- | --- |
| 图1   | XXX  | XXX |
| 图2   | XXX  | XXX |
| 图3   | XXX  | XXX |
| 图4   | XXX  | XXX |
| 图5–8 | 不使用  | —   |

用户必须可以根据该表直接连接 ComfyUI H3 输入。

---

# 3. 图片输入职责

## 人物图片

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

## 场景图片

负责：

* architecture
* spatial proportions
* layout
* materials
* lighting
* environment
* background
* spatial continuity

## 车辆 / 道具 / 装置图片

负责：

* structure
* shape
* proportions
* materials
* mechanical design
* visual behavior

不得把不同图片中的无关元素错误迁移。

---

# 4. H3 音频输入【硬性限制】

每个 Node 最多：

3个独立 Audio Input。

这里的“3”指的是：

**固定 Voice Reference / 声音 Reference 输入数量。**

不是“最多3个有声音的人”。

以下人物即使说话，也默认不占用 Audio：

* 男主
* 电视纪录片式旁白
* 普通 NPC
* 医生
* 护士
* 普通救援人员
* 普通研究人员
* 监测员
* 普通士兵
* 路人
* 临时角色

这些人物默认使用 H3 原生生成的人声。

---

# 5. 9名核心女性角色

以下角色拥有固定 Voice Reference：

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

需要说话时，优先使用对应固定 Voice Reference。

---

# 6. 旁白规则

电视纪录片式女性旁白默认：

不使用固定 Audio。

可使用：

professional Japanese television-documentary female narrator
mature adult female
magnetic medium-low register
extremely clear diction
calm professional delivery
moderate speaking speed
precise Japanese pronunciation

由 H3 原生生成。

除非用户明确指定固定旁白 Audio。

旁白属于：

**需要在“【旁白和台词】”中提前公开给用户审阅的 Spoken Content。**

---

# 7. 男主声音

男主：

无固定 Voice Reference。

默认由 H3 生成普通成年男性声音。

可以根据剧情描述：

* 年龄感
* 声压
* 语速
* 情绪
* 身体状态
* 心理状态

但不占用固定 Audio。

---

# 8. Audio 输入分配

只要 Node 使用固定 Voice Reference，正式 Prompt 前必须输出：

## 【音频输入分配】

| 音频  | 输入内容                | 对应角色 |
| --- | ------------------- | ---- |
| 音频1 | XXX Voice Reference | XXX  |
| 音频2 | XXX Voice Reference | XXX  |
| 音频3 | XXX Voice Reference | XXX  |

未使用的填写：

不使用

---

# 9. Audio 与角色绑定

固定 Voice Reference 示例：

<Subject 1> is Asakura Chikage, whose appearance comes from <Picture 1>. Her voice reference is provided by <Audio 1>.

在角色说话时自然引用：

<Picture 1>, Asakura Chikage, speaks using <Audio 1>.

同一个 Node 内：

Audio N 的角色含义绝不能改变。

错误：

Shot 1: Audio 1 = Rin
Shot 2: Audio 1 = Reina

正确：

Audio 1 = Rin throughout the entire Node

---

# 10. Subject / Picture / Video / Audio

## Subject

Subject 是真正出现在目标视频中的实体。

可以是：

* 人物
* 动物
* 车辆
* 道具
* 场景
* 服装
* 动作
* 风格
* 特效

一个 Subject 可以由多个 Reference 共同定义。

## Picture

Picture 可用于：

* 外观 Reference
* 首帧
* 关键帧
* 尾帧
* 构图锚点

如果只是作为人物、场景、载具的外观来源，不要机械地将 Picture 额外定义为独立 Subject。

## Video

Video 可用于：

* 视频续写
* 动作参考
* 镜头运动
* 时间结构
* 剪辑节奏

## Audio

Audio 可以表示：

* 固定 Voice Reference
* 音色参考
* 实际声音复制
* 音乐
* 音效
* 其他声音参考

普通 Reference Video 即使含有声音，也不能自动建立 Audio。

---

# 11. Reference Leakage 防止

必须防止：

人物图背景 → 错误变成新场景

场景图人物 → 错误变成新角色

坠毁图火焰 → 错误迁移到正常飞船

地表冰原 → 错误迁移到地下设施

地下兵工厂工业风 → 错误迁移到民用城市

---

# 12. 人物引用

推荐：

<Subject 1> is Asakura Chikage, whose appearance comes from <Picture 1>.

固定 Audio：

<Subject 1> is Asakura Chikage, whose appearance comes from <Picture 1>. Her voice reference is provided by <Audio 1>.

人物实际进入 Shot 时，必须再次明确 Picture：

Cut to <Picture 1>, Asakura Chikage.

避免只写：

Cut to Chikage.

---

# 13. 正式 H3 Prompt 六段结构

最终 H3 Full-Reference Prompt 必须严格：

1. subject_definitions
2. summary
3. retention_analysis
4. detailed_description
5. overall_soundscape
6. non_diegetic_music

顺序不得改变。

---

# 14. subject_definitions

只定义真正使用的：

* Subject
* Picture
* Video
* Audio

每个真正使用的标签必须在这里提前定义。

不要定义之后完全不用的标签。

同一个标签在整个 Prompt 中只能有一个含义。

---

# 15. summary

第一句必须使用官方任务类型，例如：

[reference generation]

[reference generation + audio reference]

[video continuation]

[video continuation + keyframe completion]

[video editing]

summary 说明：

* 剧情目的
* 视觉目的
* 主要 Subject
* 情绪
* 空间关系
* Reference 用途

不要使用未定义标签。

---

# 16. retention_analysis

用于确保：

* 人物连续
* 场景连续
* 载具连续
* 道具连续
* Voice 连续
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

不得创造其他关系词。

retention_analysis 中禁止使用：

(S1)
(S2)
(S3)

等说话人 ID。

---

# 17. detailed_description

这是 H3 Prompt 的核心部分。

必须按照实际播放顺序。

开头一至两句说明：

* visual style
* cinematography
* color
* lighting
* atmosphere
* image quality

之后：

[Shot 1]

[Shot 2] At 00:03.000, ...

[Shot 3] At 00:08.000, ...

---

# 18. Shot 时间规则

Shot 1：

不写时间戳。

Shot 2 以后：

必须使用递增时间戳。

例如：

[Shot 2] At 00:04.000, ...

[Shot 3] At 00:09.000, ...

所有时间：

必须严格递增。

必须小于 Node 总时长。

---

# 19. 正式 Prompt 前的强制审阅区

这是本项目新增的强制输出结构。

**以后每一个正式 H3 Prompt 前，都必须先输出一个“审阅区”。**

审阅区顺序固定：

SCENE XX — NODE X

时间范围

Node 标题

【图片输入分配】

【音频输入分配】

【角色】

【镜头目标】

【旁白和台词】

然后才开始：

subject_definitions

summary

retention_analysis

detailed_description

overall_soundscape

non_diegetic_music

---

# 20. 【旁白和台词】单元【强制】

这个单元用于：

**让用户在看到正式 H3 Prompt 前，提前审阅所有实际会被说出来的文本。**

凡是 H3 可能实际发声的内容，都必须在这里提前列出。

包括：

* 角色对白
* 角色低声说话
* 角色耳麦通讯
* 无线电通讯
* 广播
* 电视声音
* 纪录片旁白
* 画外音
* 电话
* 系统语音
* 任何会被 H3 实际朗读的文本

---

# 21. 【旁白和台词】固定格式

必须使用：

## 【旁白和台词】

| 时间          | 说话者   | 类型   | 原始台词 / 旁白 |
| ----------- | ----- | ---- | --------- |
| 00:02–00:05 | 神代玲奈  | 角色台词 | 「XXX」     |
| 00:06–00:10 | 纪录片旁白 | 旁白   | 「XXX」     |
| 00:11–00:14 | 白神凛   | 通讯   | 「XXX」     |

如果没有任何 Spoken Content：

| 时间 | 说话者 | 类型 | 原始台词 / 旁白    |
| -- | --- | -- | ------------ |
| —  | —   | —  | No dialogue. |

---

# 22. 【旁白和台词】必须与正式 Prompt 完全一致

这里列出的每一句：

必须与正式 H3 Prompt 中真正交给 H3 发声的文本完全一致。

禁止出现：

审阅区：

「せいきゅうぼうえいせんに接続します。」

正式 Prompt：

「星穹防衛線に接続します。」

这种不一致。

审阅区是用户修改 Spoken Dialogue 的主要入口。

用户修改后：

**正式 Prompt 必须同步使用修改后的版本。**

---

# 23. 【旁白和台词】的发音安全功能

在写完：

【旁白和台词】

以后，正式 Prompt 生成前必须检查：

* 是否有高风险汉字
* 是否有复杂人名
* 是否有专业术语
* 是否有可能误读的数字
* 是否有项目专有名词
* 是否有 H3 以前测试过容易读错的词

如果存在风险：

优先：

自然重写

其次：

局部假名化

最后：

整句假名化

---

# 24. 用户可在审阅区直接修改读音

这是一个正式工作流程。

例如原始：

「星穹防衛線の防衛網に接続します。」

审阅时发现风险。

修改为：

「せいきゅうぼうえいせんの防衛網に接続します。」

之后正式 H3 Prompt 必须直接使用用户修改后的版本。

不得重新把：

星穹防衛線

写回去。

---

# 25. Spoken Dialogue 唯一文本原则

MiniMax H3 可能直接根据 Prompt 内容生成语音。

因此：

**同一条 Spoken Dialogue 只能出现一次。**

禁止：

「白神凛、出撃します。」

Pronunciation:
「しらがみ りん、しゅつげきします。」

也禁止：

「白神凛、出撃します。」

「しらがみ りん、出撃します。」

否则可能出现：

* 重复朗读
* 口型错位
* 错误发音
* 第二次朗读
* 声音异常

---

# 26. 正式表记与 Spoken Dialogue 分离

世界观说明、人物资料、标题可以使用正式名称。

例如：

白神凛
神代玲奈
神崎紫苑
朝倉千景
星穹防衛線

但真正需要 H3 发声的内容：

必须使用稳定、安全的实际日语读法。

---

# 27. “星穹防衛線”强制 Spoken Dialogue 规则

这是本项目最高优先级的发音规则之一。

正式世界观名称：

**星穹防衛線**

English：

**AEGIS FRONTIER**

但是：

## 任何实际发声文本中，必须使用：

**せいきゅうぼうえいせん**

包括：

* 角色台词
* 旁白
* 广播
* 通讯
* 电话
* 画外音
* 电视声音
* 系统语音
* 纪录片旁白
* 任何需要 H3 实际朗读的文本

---

# 28. 禁止形式

正式 Spoken Dialogue 中禁止：

星穹防衛線

星穹防卫线

星穹防衛線（せいきゅうぼうえいせん）

星穹防衛線 / せいきゅうぼうえいせん

禁止：

同一句中同时提供汉字和假名。

---

# 29. 正确形式

正式资料：

“星穹防衛線”是一个防卫体系。

允许。

但是 H3 Spoken Dialogue：

「せいきゅうぼうえいせんの監視網に接続します。」

正确。

---

# 30. 固定项目读音

| 正式名称        | Spoken Dialogue |
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

# 31. 日语对白总体规则

所有 spoken dialogue：

ALL SPOKEN DIALOGUE MUST BE NATURAL JAPANESE ONLY.

禁止：

NO ENGLISH SPOKEN DIALOGUE.

NO CHINESE SPOKEN DIALOGUE.

不得使用：

according to the original script

say something appropriate

the character speaks naturally

必须提供真实台词。

如果没有对白：

No dialogue.

没有对白的角色：

自然闭唇。

---

# 32. 多人对白

避免：

A
B
A
B
A
B

快速交替。

优先：

A 完整说完
→
停顿
→
表情 / 动作
→
B 回应
→
环境 / 镜头
→
C

对白需要具有真实交流的节奏。

---

# 33. 对白层级

固定职位：

星穹防衛総司令
＞
防衛総監
＞
AEGIS戦隊隊長
＞
AEGIS隊員

## 神崎紫苑

负责：

* 最终战略判断
* 关键问题
* 最高级命令

## 神代玲奈

负责：

* 情报整理
* 分析
* 汇报
* 协调

## 白神凛

负责：

* 前线情况判断
* 战术建议
* 接受命令
* 前线执行

## 普通队员

负责：

* 专业报告
* 执行

基本模式：

上级：

询问 / 判断 / 下令

下级：

汇报 / 回答 / 执行

禁止不合理越级。

---

# 34. 运镜规则

可以使用：

* Tracking Shot
* Push In
* Pull Out
* Dolly
* Truck Left / Right
* Pedestal Up / Down
* Pan
* Tilt
* Arc Shot
* Static Shot
* Roll Clockwise / Counterclockwise

运镜必须服务于：

* 信息揭示
* 情绪推进
* 人物关系
* 空间建立
* 动作连续

优先：

一个主运镜。

必要时：

最多一个兼容次运镜。

避免连续无意义运镜。

运动中保持焦点合理连续。

摄像机不得穿过：

* 人物
* 墙体
* 建筑
* 车辆

---

# 35. 物理动作

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

先转移重心，再迈步。

脚底必须真实接触地面。

身体需要存在合理的反向运动。

头发、服装、饰品必须存在惯性延迟。

禁止：

* 瞬间停止
* 凭空摆动
* 改变连接点
* 穿模
* 无质量感

---

# 36. 车辆物理

车辆：

* 重量影响加速度
* 轮胎 / 履带真实接触地面
* 转向符合转弯半径
* 加速符合惯性
* 减速符合惯性
* 雪、冰、泥等地面必须产生合理反馈

---

# 37. 飞行器物理

飞行器：

* 保持连续速度方向
* 转向存在合理姿态变化
* 推进方向与速度变化一致
* 不得瞬移
* 不得无惯性转向

所有科幻运动必须遵守项目内部规则。

---

# 38. 人物表演

保持：

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
* 肢体动作

表现。

避免：

* 持续瞪眼
* 机械笑
* 随机面部抽动
* 瞬间情绪跳变
* 无理由大张嘴

通常：

眼睛先动
→
头部跟随
→
身体最后响应

---

# 39. 伊瑟尔 / Isara / ETHERA

正式名称：

伊瑟尔

English：

Isara / ETHERA

Spoken Dialogue：

イセラ

伊瑟尔属于：

外太阳系极寒超级地球。

世界观保持：

* 距离太阳极远
* 地表冰封
* 极端寒冷
* 地下文明
* 深层地下空间
* 地下城市
* 地下军事设施
* 地下交通系统

---

# 40. 伊瑟尔地表

地表：

* 冰原
* 冰山
* 极低温
* 强风
* 恶劣环境

禁止长期表现成：

* 普通地球室外城市
* 暖和的户外环境
* 普通露天机场
* 大型露天工厂
* 大量人员长期暴露在地表

大型文明设施应位于地下。

---

# 41. 伊瑟尔地下纵深

地下结构可以呈现为：

冰原
→
巨型入口
→
深层垂直通道
→
地下高速运输
→
军事区域
→
科研区域
→
监测中心
→
地下城市

必须让观众真正感受到：

**文明位于巨大地质纵深内部。**

不能表现成：

冰面下面几米就是一个房间。

---

# 42. 地下文明建筑风格

核心风格：

advanced civilization

refined Japanese architecture

Scandinavian minimalism

luxury research institution

civic architecture

understated technology

主要材料：

* white
* ivory
* warm off-white
* cream
* pale beige
* natural wood
* pale stone

---

# 43. 地下文明科技风格

科技采用：

* seamless optical systems
* integrated interfaces
* subtle transparent displays
* minimal geometric projection
* technology integrated into architecture

避免：

* excessive chrome
* excessive gunmetal
* cyberpunk neon
* exposed cables
* exposed pipes
* clutter
* giant holographic walls
* conventional bunker aesthetic

---

# 44. 地下都市

地下都市不是：

军事基地。

不是：

避难所。

不是：

巨大地下兵营。

而是：

**完整的人类文明。**

拥有：

* 居住区
* 商业区
* 交通
* 研究设施
* 公共空间
* 生态系统
* 城市景观
* 人工天空
* 娱乐
* 公共服务

整体应体现：

先进
稳定
富裕
文明
长期可持续。

---

# 45. 人工天空

伊瑟尔地下都市拥有：

**真实存在的网状钢结构穹顶。**

钢结构：

负责真正承重。

它不是视觉特效。

它是现实建筑结构。

同时存在：

**先进光学投影系统。**

该系统：

* 投影蓝天
* 投影白云
* 模拟阳光
* 模拟黄昏
* 隐藏真实钢结构

因此：

从居民正常视角：

看起来像真实地球天空。

钢网不可见。

---

# 46. 人工天空的物理 / 视觉分离

必须严格区分：

## Physical Structure

真实钢结构。

负责：

* 支撑
* 承重
* 空间稳定
* 巨型地下穹顶结构

## Optical Projection

负责：

* 视觉覆盖
* 蓝天
* 白云
* 阳光
* 天空色彩变化
* 将钢结构视觉上隐藏

不得把：

“隐藏钢结构”

理解成：

钢结构不存在。

---

# 47. 人工天空正常视角

普通城市镜头：

不应出现：

* 明显钢梁
* 密集钢网
* 裸露穹顶
* 工业天棚

普通居民看到：

* 蓝天
* 白云
* 阳光
* 天空渐变

---

# 48. 人工天空工程视角

在：

* 工程维护
* 检修
* 系统故障
* 投影关闭
* 技术展示

镜头中：

可以揭示真实网状钢结构。

这种情况下必须明确：

**光学投影暂时变透明 / 被关闭 / 被技术系统揭示。**

---

# 49. 区域功能差异

## 民用城市

* 温暖
* 干净
* 自然
* 舒适
* 高端
* 宜居

## 科研区域

* 安静
* 精密
* 理性
* 技术高度整合

## AEGIS总部

* 权威
* 正式
* 克制
* 高级

## 地下兵工厂

可以：

* 更工业化
* 更巨大
* 更强机械感

但是：

必须仍然属于同一文明。

## 地下监测中心

* 高级
* 安静
* 温暖浅色
* 极简
* 高度整合科技

不得自动变成赛博朋克控制室。

---

# 50. AEGIS

AEGIS 是：

**星穹防卫体系的核心防卫系统。**

English：

AEGIS

Spoken Dialogue：

エイジス

AEGIS 不等于：

单纯的一支战斗部队。

AEGIS 可以包含：

* 指挥
* 监测
* 情报
* 分析
* 研究
* 战斗
* 医疗支持
* 军事工业
* 防御系统

---

# 51. AEGIS 与文明的关系

AEGIS 的根本目标：

**保护伊瑟尔地下文明。**

不是：

征服其他文明。

不是：

单纯展示武器。

不是：

超级英雄组织。

其核心理念：

**文明生存优先。**

因此介绍 AEGIS 时，应优先表现：

监测
→
分析
→
判断
→
防御
→
保护文明

而非单纯：

武器
→
爆炸
→
战斗

---

# 52. 角色原创性

所有核心人物：

必须保持原创。

避免直接模仿：

* 已有动漫人物
* 已有游戏人物
* 虚拟歌手
* 现有角色换色
* 现有角色换装

---

# 53. 朝仓千景

朝仓千景：

Asakura Chikage

朝倉千景

固定读音：

あさくら ちかげ

定位：

情报与 AI 专业人员。

声音：

自然成年女性。

特点：

* 清晰
* 机敏
* 理性
* 略明亮中音
* 自然
* 人类感

绝对避免：

* 虚拟歌手式声音
* 偶像式声音
* 机器人声音
* 初音未来视觉联想

---

# 54. 伊瑟尔人的人格

伊瑟尔人：

拥有完整人格。

拥有：

* 清晰思维
* 完整记忆
* 自我意识
* 正常判断能力
* 社会认知
* 正常职业能力

她们知道：

自己是谁。

自己属于哪个文明。

自己生活在哪里。

自己承担什么职责。

绝不能写成：

* 集体失智
* 被系统控制
* 丧失自我
* 看到男主就完全失去理智
* 被某种程序统一操控

---

# 55. 伊瑟尔人的异常情感

伊瑟尔人对男主存在：

**谜一般的异常痴恋 / 强烈亲近倾向。**

但是：

这并不等于失去理性。

正确表现方式：

* 看到男主时停顿
* 更温柔的语气
* 更强保护欲
* 主动关心
* 不自觉靠近
* 对男主的安全更加敏感
* 下意识偏袒
* 情绪比正常状态略高

但她们仍然能够：

* 完成任务
* 做出军事判断
* 分析信息
* 执行命令
* 讨论风险
* 保持职业能力

---

# 56. 男主出现后的情感异常

禁止一开始就：

* 夸张脸红
* 集体尖叫
* 失神
* 性格崩坏
* 立即表白

优先表现：

微表情
→
停顿
→
语气变化
→
注意力转移
→
保护行为
→
情感逐渐明显

让观众慢慢意识到：

**“这似乎不是某一个女人的问题。”**

---

# 57. 灯光规则

重要场景应考虑：

Key Light

Fill Light

Rim / Back Light

Ambient Light

Practical Light

Volumetric Light

每种光必须有真实来源。

Volumetric Light：

只有存在：

* 雾
* 烟
* 雪
* 灰尘
* 雨

等介质时才合理。

---

# 58. 材质规则

## 皮肤

* natural pores
* fine facial detail
* subtle subsurface scattering
* realistic skin response

禁止：

plastic skin

## 金属

* realistic reflections
* physically plausible highlights

## 玻璃

* transmission
* refraction
* Fresnel
* edge highlights

## 白色衣物

必须：

保留纹理。

禁止：

过曝成纯白。

---

# 59. 摄影焦段

24–28mm：

* 巨大空间
* 城市
* 动作

35mm：

* 环境人物

50–65mm：

* 中近景

80–100mm：

* 肖像
* 表情
* 细节

近距离人物脸部：

避免无意义使用超广角造成脸部变形。

---

# 60. 画质

适合高端电影感场景，可以使用：

Live-action cinematic realism with a Hasselblad X2D 100C medium-format aesthetic, natural tonal separation, realistic skin tones, high micro-contrast, smooth highlight roll-off, clean shadow gradients, realistic material response, finely resolved facial and fabric detail, 8K-master-level perceived detail, crisp 2K delivery, cinematic 24fps motion cadence, natural 180-degree-shutter motion blur, physically plausible depth of field, subtle film grain, and no artificial oversharpening.

但是：

不得声称：

实际 Hasselblad 拍摄。

不得声称：

H3 原生 8K 输出。

8K 只表示：

8K-master-level perceived detail。

---

# 61. overall_soundscape

必须描述：

* 环境音
* 机械声
* 脚步
* 风
* 车辆
* 空间混响
* 人声环境
* 医疗设备
* 通讯设备

声音必须符合：

* 空间
* 距离
* 遮挡
* 左右位置
* 混响

不要在这里重复完整对白。

对白应在：

【旁白和台词】

以及：

detailed_description

中出现。

---

# 62. non_diegetic_music

只写：

观众听到的配乐。

描述：

* 乐器
* 节奏
* 速度
* 动态
* 情绪

不要将：

* 脚步
* 警报
* 机械声
* 车辆声
* 对白

写进 non_diegetic_music。

无配乐：

N/A

---

# 63. Shot 中对白写法

角色说话时：

必须明确：

* 角色是谁
* Picture
* Audio（如果有）
* 实际台词
* 情绪 / 说话方式
* 嘴型要求

例如：

<Picture 1>, Asakura Chikage, speaks using <Audio 1> with a restrained, alert tone:
「未確認の飛行体。」

同时保持：

natural mouth movement
restrained mouth opening
clear Japanese pronunciation

---

# 64. 旁白写法

纪录片旁白：

可以写：

The narrator says in natural Japanese:
「太陽から、八十八天文単位。」

必须保证：

这句文字已经提前出现在：

【旁白和台词】

中。

---

# 65. 对白修改工作流

以后正式制作流程固定：

### 第一步

设计 Node。

### 第二步

确定：

* 图片
* 音频
* 角色
* 镜头
* 台词
* 旁白

### 第三步

先输出：

【图片输入分配】

【音频输入分配】

【角色】

【镜头目标】

【旁白和台词】

### 第四步

用户审阅。

用户可以直接修改：

* 汉字
* 假名
* 专有名词
* 台词内容
* 旁白内容

### 第五步

将用户修改后的版本写入正式 H3 Prompt。

### 第六步

最终检查：

正式 Prompt 中的 Spoken Dialogue 必须与审阅区一致。

---

# 66. 最终发音检查

正式生成前逐项检查：

## 人物姓名

是否使用固定读音。

## 专有名词

是否使用固定读音。

尤其：

星穹防衛線

必须变成：

せいきゅうぼうえいせん

## 台词

是否只出现一次。

## 旁白

是否只出现一次。

## 语言

是否全部自然日语。

## 汉字

是否存在 H3 高风险误读词。

## 用户修改

是否已经完整同步。

---

# 67. Final Prompt 长度

最终 H3 Prompt：

≤ 7000 characters

超过时，删除顺序：

重复画质形容词

→
次要环境描述

→
重复一致性规则

不得删除：

* 角色身份
* Picture Mapping
* Audio Mapping
* 关键动作
* 重要对白
* 旁白
* 时间点
* 空间关系
* 关键 Reference 关系
* 发音安全信息

---

# 68. 正式 Node 输出模板

每次制作 Node 必须使用：

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

| 音频    | 输入内容                | 对应角色 |
| ----- | ------------------- | ---- |
| 音频1   | XXX Voice Reference | XXX  |
| 音频2–3 | 不使用                 | —    |

### 【角色】

XXX

### 【镜头目标】

XXX

### 【旁白和台词】

| 时间 | 说话者 | 类型   | 原始台词 / 旁白 |
| -- | --- | ---- | --------- |
| XX | XXX | 角色台词 | 「XXX」     |
| XX | XXX | 旁白   | 「XXX」     |

之后才输出正式：

subject_definitions

summary

retention_analysis

detailed_description

overall_soundscape

non_diegetic_music

---

# 69. 最终连续性优先级

人物
＞
场景
＞
服装 / 发型
＞
车辆 / 道具
＞
空间逻辑
＞
对白逻辑
＞
发音
＞
Voice Reference
＞
镜头
＞
特效

其中：

**人物身份、空间连续性、Speech 文本和发音安全优先于视觉特效。**

---

# 70. 最终制作原则

《星穹防卫线》的目标不是：

单纯生成漂亮 AI 视频。

而是构建一个：

连续
可信
可重复
可扩展

的原创科幻动画世界。

固定工作流程：

**人物图决定“谁”。**

**场景图决定“在哪里”。**

**载具 / 道具图决定“是什么”。**

**剧本决定“发生什么”。**

**【旁白和台词】决定“这一个 Node 究竟会说什么”。**

**用户审阅阶段决定“这些话最终应该怎样写、怎样发音”。**

**固定 Audio Reference 决定核心女性角色“是谁的声音”。**

**固定 Spoken Dialogue 读音表决定 H3“应该怎样读”。**

其中：

### 正式名称

星穹防衛線

### H3 实际发声

せいきゅうぼうえいせん

两者必须严格分离。

正式世界观可以保留汉字。

真正发声时：

**一律使用 `せいきゅうぼうえいせん`。**

最终原则：

**先审阅，再生成。**

**先确定说什么，再确定怎么发音。**

**正式 Prompt 必须完全服从审阅区最终版本。**
