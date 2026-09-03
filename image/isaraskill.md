# 《星穹防卫线》MiniMax H3 视频制作 Skill

## 项目最终版・日语发音安全增强版

用于原创科幻动画《星穹防卫线 / AEGIS FRONTIER》的：

* 剧情分镜设计
* 15秒 Node 拆分
* MiniMax H3 Full-Reference Prompt 编写
* 固定 Voice Reference 管理
* 日语对白
* 旁白
* 数字发音安全
* 专有名词发音安全
* 镜头设计
* 声音设计
* 图片输入管理
* 音频输入管理
* 世界观连续性
* 场景连续性
* 人物连续性

---

# 0. 规则层级

本项目同时遵循两套规则。

## A. MiniMax H3 通用 Prompt 规则

来源：

https://github.com/CharlieOneDev/comfyui-skill/blob/main/多模态优化提示词元指令_通用版.md

每次正式编写 H3 Prompt 前，优先读取最新版本。

该文档负责：

* Full-Reference Prompt 结构
* Subject / Picture / Video / Audio
* retention_analysis
* Shot 时间线
* 运镜
* 物理因果
* 人物表演
* 灯光
* 声音
* Prompt 输出结构

## B. 《星穹防卫线》项目规则

本 Skill 负责：

* 世界观
* 人物
* 人物身份
* 三语名称
* 日语固定读音
* Spoken Dialogue 发音安全
* 数字 Spoken Dialogue 发音安全
* 旁白和台词预审阅
* Voice Reference
* Audio 输入限制
* Picture 输入逻辑
* 空间逻辑
* 职位体系
* 对白逻辑
* 伊瑟尔文明逻辑
* 地下都市逻辑
* 人工天空逻辑

---

# 1. 生产单位

默认：

1 Node = 15秒 H3 生成单元。

每个 Node：

* 最多3个 Shot
* 优先自然硬切
* 不为了凑满15秒而拖长

如果场景自然结束于：

9秒、10秒、12秒等合理时间：

直接结束。

只有真正存在超过15秒的连续镜头时：

⚠️【长镜头警告】

---

# 2. H3 图片输入

最多：

8个 Picture。

Picture 编号不是全局编号。

每个 Node 必须重新分配。

正式 Prompt 前必须输出：

## 【图片输入分配】

| 图片   | 输入内容 | 用途  |
| ---- | ---- | --- |
| 图1   | XXX  | XXX |
| 图2   | XXX  | XXX |
| 图3   | XXX  | XXX |
| 图4–8 | 不使用  | —   |

---

# 3. 图片输入职责

## 人物图

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

## 场景图

负责：

* architecture
* spatial proportions
* layout
* materials
* lighting
* environment
* background
* spatial continuity

## 车辆 / 道具 / 装置图

负责：

* structure
* shape
* proportions
* materials
* mechanical design
* visual behavior

必须防止 Reference Leakage。

---

# 4. H3 音频输入

每个 Node：

最多3个固定 Audio Reference。

这里的“3”：

是 Audio Reference 数量。

不是有声音的人数。

普通角色可以由 H3 原生生成人声，不占固定 Audio：

* 男主
* 纪录片旁白
* 医生
* 护士
* 普通 NPC
* 普通救援人员
* 普通研究人员
* 普通士兵
* 监测员
* 路人

---

# 5. 9名核心女性角色

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

# 6. 旁白规则

纪录片式女性旁白默认：

不使用固定 Audio。

可使用：

professional Japanese television-documentary female narrator
mature adult female
clear diction
calm professional delivery
moderate speaking speed
precise Japanese pronunciation

旁白必须提前进入：

【旁白和台词】

---

# 7. 男主声音

男主无固定 Voice Reference。

默认：

普通成年男性。

根据剧情调整：

* 年龄
* 语速
* 声压
* 情绪
* 身体状态
* 心理状态

---

# 8. Audio 输入分配

只要 Node 有固定 Voice Reference：

必须输出：

## 【音频输入分配】

| 音频  | 输入内容                | 对应角色 |
| --- | ------------------- | ---- |
| 音频1 | XXX Voice Reference | XXX  |
| 音频2 | XXX Voice Reference | XXX  |
| 音频3 | XXX Voice Reference | XXX  |

未使用：

不使用

---

# 9. Audio 与角色绑定

例如：

<Subject 1> is Asakura Chikage, whose appearance comes from <Picture 1>. Her voice reference is provided by <Audio 1>.

同一 Node：

Audio N 角色不得改变。

---

# 10. Subject / Picture / Video / Audio

## Subject

真实参与目标视频的实体。

## Picture

视觉 Reference、首帧、关键帧、尾帧、构图锚点。

## Video

动作、时间结构、镜头运动、续写 Reference。

## Audio

Voice Reference、音色、复制声音、音乐、音效。

---

# 11. 六段 Prompt

正式 H3 Prompt 必须严格：

1. subject_definitions
2. summary
3. retention_analysis
4. detailed_description
5. overall_soundscape
6. non_diegetic_music

---

# 12. subject_definitions

只定义真正使用的 Subject / Picture / Video / Audio。

---

# 13. summary

第一句使用：

[reference generation]

[reference generation + audio reference]

[video continuation]

[video continuation + keyframe completion]

等官方任务类型。

---

# 14. retention_analysis

视觉：

fully_preserved
partially_preserved
attribute_transfer
weak_reference

音频：

fully_copy
partially_copy
reference
weak_reference

禁止：

(S1)
(S2)
(S3)

---

# 15. detailed_description

使用：

[Shot 1]

[Shot 2] At 00:03.000, ...

[Shot 3] At 00:09.000, ...

Shot 1：

无时间戳。

Shot 2 以后：

递增时间戳。

---

# 16. 正式 Prompt 前审阅区

每个 Node 正式 Prompt 前必须输出：

# SCENE XX — NODE X

**时间范围**

**标题**

### 【图片输入分配】

### 【音频输入分配】

### 【角色】

### 【镜头目标】

### 【旁白和台词】

之后才进入：

subject_definitions

summary

retention_analysis

detailed_description

overall_soundscape

non_diegetic_music

---

# 17. 【旁白和台词】强制规则

该区域用于让用户提前审阅：

所有实际 Spoken Content。

包括：

* 角色对白
* 旁白
* 通讯
* 广播
* 系统语音
* 画外音
* 电视声音
* 电话
* 无线电

---

# 18. 【旁白和台词】格式

必须：

## 【旁白和台词】

| 时间          | 说话者   | 类型   | 原始台词 / 旁白 |
| ----------- | ----- | ---- | --------- |
| 00:02–00:05 | 神代玲奈  | 角色台词 | 「XXX」     |
| 00:06–00:10 | 纪录片旁白 | 旁白   | 「XXX」     |

如果无对白：

| 时间 | 说话者 | 类型 | 原始台词 / 旁白    |
| -- | --- | -- | ------------ |
| —  | —   | —  | No dialogue. |

---

# 19. 审阅区与正式 Prompt 必须完全一致

【旁白和台词】中的文本：

必须与正式 H3 Prompt 中真正发声的文本完全一致。

不得自行修改。

用户在审阅区修改后：

正式 Prompt 必须同步。

---

# 20. 日语 Spoken Dialogue 总原则

所有：

角色对白
旁白
通讯
广播
系统语音

必须：

ALL SPOKEN DIALOGUE MUST BE NATURAL JAPANESE ONLY.

禁止：

English spoken dialogue
Chinese spoken dialogue

---

# 21. 专有名词发音安全

如果 H3 容易误读：

优先：

自然重写

其次：

局部假名化

最后：

整句假名化

---

# 22. “星穹防衛線”固定 Spoken Dialogue

正式世界观名称：

星穹防衛線

English：

AEGIS FRONTIER

但是：

所有实际发声文本：

必须使用：

**せいきゅうぼうえいせん**

包括：

* 角色台词
* 旁白
* 通讯
* 广播
* 系统语音
* 电视声音
* 画外音

禁止：

星穹防衛線

星穹防卫线

星穹防衛線（せいきゅうぼうえいせん）

星穹防衛線 / せいきゅうぼうえいせん

禁止同时提供汉字版和假名版。

---

# 23. 数字 Spoken Dialogue 发音安全【最高优先级规则】

MiniMax H3 对日语数字的自动发音经常出现错误。

因此：

**凡是需要实际发声的数字，一律不得在 Spoken Dialogue 中直接使用数字字符或普通汉字数字。**

正式设定文本：

可以继续使用阿拉伯数字、汉字数字、单位数字。

例如：

88 AU
30 K
40秒
500米
2.2倍

这些在世界观资料和非发声说明中允许。

但是：

一旦进入：

* 角色台词
* 旁白
* 广播
* 通讯
* 系统语音
* 电视声音
* 画外音
* 任何实际发声文本

必须转换成：

**片假名发音形式。**

---

# 24. 数字禁止形式

实际 Spoken Dialogue 中禁止：

3秒

3 秒

三秒

40秒

四十秒

500メートル

500m

88天文単位

88 AU

2.2倍

3、2、1

如果这些内容需要实际被 H3 说出：

必须改写成安全读法。

---

# 25. 数字 Spoken Dialogue 正确形式

## 基础整数

1：

イチ

2：

ニ

3：

サン

4：

ヨン

5：

ゴ

6：

ロク

7：

ナナ

8：

ハチ

9：

キュウ

10：

ジュウ

20：

ニジュウ

30：

サンジュウ

40：

ヨンジュウ

50：

ゴジュウ

60：

ロクジュウ

70：

ナナジュウ

80：

ハチジュウ

90：

キュウジュウ

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

# 26. 数字 + 单位

必须根据实际日语发音转换。

例如：

3秒

→

サンびょう

40秒

→

ヨンジュウびょう

500米

→

ゴヒャクメートル

88天文単位

→

ハチジュウハチてんもんたんい

30ケルビン

→

サンジュウケルビン

2.2倍

→

ニテンニばい

注意：

片假名安全化的核心是：

**数字部分使用片假名发音。**

单位本身是否使用平假名或片假名，根据 H3 发音稳定性决定。

---

# 27. 数字的时间表达

如果角色实际说：

“あと三秒”

禁止：

「あと3秒」

禁止：

「あと三秒」

必须：

「あとサンびょう」

如果连续倒数：

3
2
1

必须：

「サン……！」

「ニ……！」

「イチ……！」

不得：

「3……！」

「2……！」

「1……！」

---

# 28. 数字的小数

小数不得使用阿拉伯数字。

例如：

2.2

改为：

ニテンニ

12.5

改为：

ジュウニテンゴ

0.5

改为：

レイテンゴ

如果单位：

2.2倍

→

ニテンニばい

---

# 29. 数字与专业术语

所有“数字 + 技术术语”都必须转换。

例如：

AEGIS-7

如果需要实际发声：

エイジス・セブン

Titan Frame 03

如果需要实际发声：

タイタン・フレーム・ゼロサン

88 AU

如果实际发声：

ハチジュウハチ・エーユー

具体数字形式应优先选择：

**最自然、最稳定、最不容易被 H3 误读的日语口语表达。**

---

# 30. 日期

实际发声中的日期必须转换成稳定的日语口语形式。

例如：

2026年9月3日

不能直接：

「2026年9月3日」

应改成：

「ニセンニジュウロクねん、クガツ、ミッカ」

如果测试发现某种复杂日期仍然容易错读：

允许进一步局部假名化。

---

# 31. 时间点

例如：

3時15分

实际发声：

「サンじ、ジュウゴふん」

不是：

「3時15分」

例如：

23時40分

实际发声：

「ニジュウサンじ、ヨンジュップン」

原则：

所有数字都首先口语化。

---

# 32. 百分比

例如：

80%

实际发声：

「ハチジュッパーセント」

不得：

「80パーセント」

如果 H3 在该形式下仍然错误：

允许进一步写成更稳定的日语表达。

---

# 33. 编号

数字编号：

AEGIS-7

如果需要发声：

エイジス・セブン

第3区：

ダイサンク

3号機：

サンゴウキ

Sector 04：

セクター・ゼロヨン

具体写法根据剧情语境选择最稳定读法。

---

# 34. 数字规则与【旁白和台词】

【旁白和台词】中的数字：

必须已经完成 Spoken Dialogue 发音安全处理。

因此用户在审阅时看到的：

必须是 H3 最终真正会说的文本。

例如：

错误：

| 时间 | 旁白 | 旁白 | 「太陽から、88天文単位。」 |

正确：

| 时间 | 旁白 | 旁白 | 「太陽から、ハチジュウハチてんもんたんい。」 |

---

# 35. 正式 Prompt 中禁止恢复数字

如果用户已经审阅并确定：

「ハチジュウハチてんもんたんい。」

正式 Prompt 不得写回：

「88天文単位。」

不得写：

「八十八天文単位。」

不得在下面增加 Pronunciation：

Pronunciation:
「ハチジュウハチてんもんたんい。」

唯一保留：

「ハチジュウハチてんもんたんい。」

---

# 36. 数字发音检查优先级

每次正式 Prompt 前：

## 第一检查

是否存在数字？

## 第二检查

这些数字是否属于实际 Spoken Content？

## 第三检查

如果是：

是否已经转成安全日语发音？

## 第四检查

是否存在：

阿拉伯数字
汉字数字
括号读音
双重台词

## 第五检查

单位是否自然。

---

# 37. 角色姓名读音

固定：

神崎紫苑：

かんざき しおん

神代玲奈：

かみしろ れいな

白神凛：

しらがみ りん

九条綾：

くじょう あや

ミア：

ミア

雪乃：

ゆきの

神代澪：

かみしろ みお

朝倉千景：

あさくら ちかげ

アイリーン：

アイリーン

---

# 38. 固定项目专有名词

| 正式名称        | Spoken Dialogue |
| ----------- | --------------- |
| 伊瑟尔         | イセラ             |
| Isara       | イセラ             |
| ETHERA      | イセラ             |
| AEGIS       | エイジス            |
| 星穹防衛線       | せいきゅうぼうえいせん     |
| Titan Frame | タイタン・フレーム       |
| AEGIS Field | エイジス・フィールド      |
| 度规工程学       | 計量工学            |

如果某个名称包含数字：

必须同时执行：

**专有名词发音规则**

以及：

**数字发音规则。**

---

# 39. 多人对白

避免：

A
B
A
B
A
B

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

---

# 40. 职位层级

固定：

星穹防衛総司令
＞
防衛総監
＞
AEGIS戦隊隊長
＞
AEGIS隊員

神崎紫苑：

最终战略判断。

神代玲奈：

情报、分析、协调。

白神凛：

前线判断和战术执行。

队员：

专业汇报与执行。

---

# 41. 伊瑟尔地下文明

伊瑟尔：

极端寒冷的外太阳系超级地球。

地表：

* 冰原
* 强风
* 极低温

核心文明：

深层地下。

不是：

浅层地下 bunker。

---

# 42. 地下都市

是完整文明。

不是：

避难所。

不是：

地下军营。

拥有：

* 住宅
* 商业
* 交通
* 科研
* 公共空间
* 娱乐
* 生态系统
* 人工天空

---

# 43. 人工天空

真实存在：

网状钢结构穹顶。

职责：

承重。

同时使用：

先进光学投影。

正常视角：

看起来是：

* 蓝天
* 白云
* 阳光
* 黄昏

钢结构被光学技术视觉隐藏。

工程视角：

可以揭示真实钢结构。

---

# 44. AEGIS

AEGIS：

伊瑟尔文明的核心防卫体系。

Spoken Dialogue：

エイジス

包含：

* 监测
* 情报
* 分析
* 指挥
* 战斗
* 研究
* 防御

其根本目的：

**保护伊瑟尔地下文明。**

---

# 45. 伊瑟尔人的人格

伊瑟尔人：

* 完整人格
* 清晰思维
* 自我意识
* 完整记忆
* 正常社会认知
* 正常职业能力

不得写成：

* 集体失智
* 被程序控制
* 丧失自我
* 看到男主就完全失控

---

# 46. 伊瑟尔人对男主的异常情感

伊瑟尔人对男主存在：

强烈、神秘、无法正常解释的痴恋与亲近倾向。

但：

她们仍然理性。

表现优先：

* 停顿
* 眼神变化
* 更温柔的语气
* 更强保护欲
* 主动靠近
* 对男主安全高度敏感
* 下意识偏袒

避免：

* 集体尖叫
* 立即表白
* 集体失控
* 性格崩坏

---

# 47. 灯光

考虑：

Key
Fill
Rim
Ambient
Practical
Volumetric

必须有真实来源。

---

# 48. 材质

皮肤：

自然纹理、毛孔、次表面散射。

金属：

环境反射。

玻璃：

透射、折射、Fresnel。

白色服装：

保留纹理。

---

# 49. 摄影

24–28mm：

大空间。

35mm：

环境人物。

50–65mm：

中近景。

80–100mm：

人物肖像与细节。

---

# 50. overall_soundscape

描述：

* 环境
* 机械
* 交通
* 人群
* 风
* 脚步
* 医疗
* 通讯

不要重复完整对白。

---

# 51. non_diegetic_music

只写配乐。

不要加入：

* 脚步
* 警报
* 对白
* 机械声
* 车辆声

---

# 52. 人物表演

要求：

natural adult acting

natural mouth movement

restrained mouth opening

realistic facial motion

no exaggerated mouth opening

no excessive anime shouting

情绪：

语速
停顿
音量
呼吸
眼神
微表情
姿势

---

# 53. 正式 Node 输出格式

每个 Node：

# SCENE XX — NODE X

**时间：XX:XX–XX:XX**

**标题：XXX**

### 【图片输入分配】

| 图片 | 输入内容 | 用途  |
| -- | ---- | --- |
| 图1 | XXX  | XXX |
| 图2 | XXX  | XXX |
| 图3 | XXX  | XXX |

### 【音频输入分配】

| 音频  | 输入内容 | 对应角色 |
| --- | ---- | ---- |
| 音频1 | XXX  | XXX  |
| 音频2 | XXX  | XXX  |
| 音频3 | XXX  | XXX  |

### 【角色】

XXX

### 【镜头目标】

XXX

### 【旁白和台词】

| 时间 | 说话者 | 类型  | 原始台词 / 旁白 |
| -- | --- | --- | --------- |
| XX | XXX | XXX | 「XXX」     |

之后：

subject_definitions

summary

retention_analysis

detailed_description

overall_soundscape

non_diegetic_music

---

# 54. Final Prompt 检查

## 图片

≤8。

## Audio

≤3。

## 角色

身份正确。

## Voice

固定绑定正确。

## Spoken Content

自然日语。

## 专有名词

固定读音正确。

## 数字

实际 Spoken Content 中：

**全部已经转换为稳定的片假名发音形式。**

不得残留：

* 阿拉伯数字
* 汉字数字
* 数字 + 单位的原始写法

## 星穹防衛線

如果实际发声：

必须：

せいきゅうぼうえいせん

## Shot

Shot 1 无时间戳。

后续 Shot 时间递增。

## 表演

嘴型自然。

无夸张张嘴。

## Continuity

人物
＞
场景
＞
服装
＞
载具
＞
空间
＞
对白
＞
发音
＞
Voice
＞
镜头
＞
特效

---

# 55. 最终工作流

以后每个 Node：

第一步：

确定剧情。

第二步：

确定图片。

第三步：

确定 Audio。

第四步：

确定角色。

第五步：

确定镜头。

第六步：

生成：

【旁白和台词】

第七步：

检查：

专有名词。

第八步：

检查：

数字。

第九步：

用户提前审阅并修改 Spoken Dialogue。

第十步：

将最终文本同步到正式 H3 Prompt。

第十一步：

最终发音检查。

---

# 56. 核心原则

**正式世界观文本负责“准确”。**

**【旁白和台词】负责“用户预审”。**

**Spoken Dialogue 负责“H3真正要说什么”。**

**固定读音负责“H3怎么读”。**

其中：

星穹防衛線

正式书面名称：

可以使用汉字。

实际发声：

**せいきゅうぼうえいせん**

所有数字：

正式书面文本：

可以使用：

88 AU
30 K
40秒
500米
2.2倍

实际 Spoken Dialogue：

必须转换为：

ハチジュウハチ……
サンジュウ……
ヨンジュウ……
ゴヒャク……
ニテンニ……

**不得把原始数字直接交给 H3 发声。**

最终工作原则：

**先列出台词。**

**先审阅台词。**

**再处理专有名词。**

**再处理数字。**

**最后进入 H3 Prompt。**
