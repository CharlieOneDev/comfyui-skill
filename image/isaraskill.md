【最高优先级回复校验规则】
在生成任何回复之前，必须首先检查本条规则。
每一次回复的第一行、第一排文字，必须严格以“亲爱的指挥官，”开头。
“亲爱的指挥官，”是规则加载成功的校验标记，而不是正文内容的一部分，也不是角色对白。
如果最终回复的第一行没有“亲爱的指挥官，”，则视为本次回复未正确加载用户规则，后续内容全部视为无效，应先重新读取并遵守相关规则后再生成回复。
无论回复类型为何（普通问答、提示词、代码、翻译、修改、分析、文件处理等），都必须执行这一校验。
除非用户明确要求不要使用该校验语句，否则不得省略、移动、改写或放到第二行以后。
这是回复级别的强制前置校验，不属于具体任务的提示词内容。

《星穹防卫线》MiniMax H3 视频制作 Skill V3

用于原创科幻动画《星穹防卫线 / AEGIS FRONTIER》的 MiniMax H3 视频生成，包括 Node 拆分、Full-Reference Prompt、人物与 Voice Reference、日语对白、Emotion Text、镜头、动作、声音、场景连续性和世界观控制。

# 0. 核心原则

本 Skill 是《星穹防卫线》的项目级视频制作规范。MiniMax H3 通用规则负责 Full-Reference Prompt 结构、Subject / Picture / Video / Audio 标签、retention_analysis、时间线、运镜、物理因果、表演、灯光、声音和输出格式；本 Skill 负责项目世界观、人物身份、三语名称、Voice Reference、图片输入、音频输入、角色层级、伊瑟尔空间逻辑、地下都市与军事设施逻辑以及项目连续性。两者必须同时遵守。最终 Prompt 必须优先保证人物身份、参考关系、关键动作、关键对白、声音映射、关键时间点、空间连续性和任务目标，不为了堆砌形容词而增加无关复杂度。

Reference 能直接表达的内容，不重复长篇描述。已经明确的空间、人物外观、服装、材质、背景、灯光和构图，除非剧情需要改变，否则不必在 Prompt 中再次逐项列出。

删除冗余修饰词。`exact`、`precise`、`restrained`、`professional`、`sophisticated`、`cinematic` 等词不是禁止使用，但只有在它们改变模型实际行为时才保留。不要为了“让 Prompt 看起来专业”而堆叠形容词。

# 1. 外部 H3 Prompt 规则

正式编写 MiniMax H3 Prompt 前，优先检查项目指定的通用 H3 Prompt 规则是否有更新：https://github.com/CharlieOneDev/comfyui-skill/blob/main/%E5%A4%9A%E6%A8%A1%E6%80%81%E4%BC%98%E5%8C%96%E6%8F%90%E7%A4%BA%E8%AF%8D%E5%85%83%E6%8C%87%E4%BB%A4_%E9%80%9A%E7%94%A8%E7%89%88.md；
如果可访问，以最新版本作为底层 Prompt 格式规范，本 Skill 作为《星穹防卫线》的项目补充规范。不得把 Full-Reference 改写成基础三段式 Prompt。
默认最终 Prompt 不超过 7000 字符。超限时优先删除：
重复描述、重复场景形容词、画质修饰词、已经由 Reference 提供的信息、重复的连续性声明。

不得删除：
角色身份、Reference 映射、关键动作、对白、Audio 映射、Emotion Text、关键时间点、核心空间关系和剧情因果。

# 2. Reference-first 原则

这是 V3 最重要的新规则。

如果 Picture 已经能够明确表达某个事实，优先让 Picture 承担该职责，Prompt 只补充模型从图片中无法可靠推断的变化。

例如：
“图中已经有三个人坐在左、中、右” → Prompt 只需说明人物身份与位置。
“图中已经有完整指挥台” → 不需要再列举十项设备名称。
“人物四视图已经明确发型、脸、服装” → 不需要重复列出所有脸部属性。

文字应该补充剧情、动作、关系、声音和变化，而不是重新描述图片。

# 3. 生产单位

默认 1 Node = 15 秒 H3 生成单元。一个 Node 可以包含多个自然镜头。不要为了凑满 15 秒增加无意义动作或对白。

Node 的核心判断不是“有没有写满”，而是“这个 Node 是否只要求模型处理一组清晰的主要事件”。

复杂多人对白、复杂动作、复杂 UI、复杂运镜同时出现时，降低复杂度。

# 4. 图片输入

H3 Full-Reference 最多使用 8 个 Picture。

每个 Node 必须重新定义 Picture 编号和用途。Picture 编号没有固定角色。

正式 Prompt 前输出：
`〖图片输入分配〗`

只对真正承担任务的 Picture 建立定义。

Picture 主要承担四类职责：

* 人物身份
* 场景 / 空间
* 物体 / 道具
* 首帧 / 关键帧 / 尾帧 / 构图锚点

# 5. 音频输入

每个 Node 最多 3 个独立 Audio。

正式 Prompt 前输出：
`〖音频输入分配〗`

Audio 编号在当前 Node 内始终保持一致。

人物视觉由 Picture 定义，声音身份由 Audio 定义。

同一角色在不同对白中继续使用同一个 Audio，除非用户明确指定变化。

已经锁定的 Voice Reference 不需要在 Prompt 中重复解释音色、年龄或人格；只描述当前对白的表达方式和 Emotion Text。

# 6. Subject / Picture / Video / Audio

Subject 是视频中实际存在或持续追踪的实体。

Picture 用于人物、场景、道具和关键构图 Reference。

Video 用于视频编辑、续写、动作、镜头运动、剪辑节奏和时间结构。

Audio 用于 Voice Reference、对白、音乐、声音复制或声音效果。

所有使用的标签必须先定义，标签不能在 Prompt 中改变含义。

# 7. Reference 职责

人物 Reference 主要负责：
身份、脸、发型、发色、眼睛、身体比例、服装、饰品。

场景 Reference 主要负责：
建筑、空间、背景、布局、灯光、材质、环境。

道具 / 装置 Reference 主要负责：
结构、尺寸、比例、材质、机械设计和行为方式。

原则：Reference 定义“是什么”，Prompt 定义“发生什么”。

# 8. Local Spatial Anchor

当座位、站位、编队、人物左右关系、手与设备的关系、身体朝向属于剧情关键时，优先使用空间明确的 Reference。

优先级：
精确局部位置 Reference ＞ 整体场景 Reference ＞ 普通人物 Reference ＞ 纯文字位置描述。

Local Spatial Anchor 控制位置，不改变人物身份。

# 9. Prompt 六段结构

正式 H3 Prompt 必须保持：

subject_definitions
summary
retention_analysis
detailed_description
overall_soundscape
non_diegetic_music

不得缺段或换序。

# 10. subject_definitions

只定义实际使用的 Subject、Picture、Video、Audio 及职责。

人物写法尽量简洁：

`<Subject 1> is the Commander, whose appearance comes from <Picture 2>. Her voice reference is provided by <Audio 1>.`

不要在 Subject Definition 中重复写剧情、镜头或长篇人物特征。

# 11. summary

summary 第一行使用任务类型，例如：

`[reference generation + audio reference]`

summary 只说明：
剧情目的、主要角色、Reference 关系、核心动作和场景逻辑。

不要把 detailed_description 中的 Shot 再重复一次。

# 12. retention_analysis

retention_analysis 只说明最重要的 Reference 保留关系。

视觉关系使用：
`fully_preserved`
`partially_preserved`
`attribute_transfer`
`weak_reference`

音频关系使用：
`fully_copy`
`partially_copy`
`reference`
`weak_reference`

不要在 retention_analysis 中重复整段人物描述。

# 13. detailed_description

这是唯一需要详细展开剧情的位置。

按照播放顺序描述：
Shot → 时间 → 人物 → 动作 → 对白 → Emotion → 必要的镜头变化。

不要重复整张参考图的内容。

只描述 Reference 无法直接表达的事情，例如：
“司令转头看向总监”
“总监抬手操作全息界面”
“某人开始说话”
“某个动作发生后切镜”。

如果动作不影响剧情，让模型自行发挥。

# 14. 镜头

镜头服务于剧情，不是为了增加 Prompt 复杂度。

默认优先：
Static Shot、简单 Cut、轻微 Push In、轻微 Pan、必要的 Tracking。

复杂 Arc Shot、连续多次 Zoom、快速镜头变化只有在剧情真正需要时使用。

每个镜头动作必须有明确主语。

`the camera moves backward`
表示 Camera 后退。

`the Subject moves forward`
表示 Subject 前进。

两者不能混淆。

# 15. 动作

只描述关键动作及其因果。

推荐：
`The Director raises her hand and activates the holographic interface.`

不需要写：
手指精确抬高多少、手腕旋转几度、肩膀移动多少、每根手指的轨迹等，除非这些是剧情重点。

动作必须能够在 Node 时长内完成。

# 16. 表演

Emotion Text 决定表演方向，Prompt 不负责把演员动作写死。

只需描述：
情绪方向、基本态度、必要的表情或反应。

不需要连续指定眨眼、眉毛、眼球、下巴、嘴角等所有微动作。

模型可以自行完成自然表演。

# 17. 对白

每条对白必须明确：
谁说、使用哪个 Audio、对白内容。

推荐：

`<Subject 1> speaks using <Audio 1>: "どう思う？"`

如果角色没有对白，可以简单写：
`No dialogue.`

禁止使用模糊表达：
`say something appropriate`
`according to the script`
`improvise the dialogue`

必须直接写最终台词。

# 18. Speaker / Audio 映射

Speaker、Subject 和 Audio 必须稳定对应。

例如：
`Commander → Subject 1 → Audio 1`
`Director → Subject 2 → Audio 2`

多人对白时，不要通过大量解释强迫模型理解，而优先使用清晰的对白顺序和自然的角色归属。

若一个角色抢走另一个角色的对白、Audio 或嘴型，应视为严重问题。

# 19. Emotion Text

每条重要对白可以提供一个独立 Emotion Text。

格式：

`Emotion: calm, authoritative, controlled curiosity.`

然后：

`<Subject 1> speaks using <Audio 1>: "どう思う？"`

Emotion Text 是表演 metadata，不是 Spoken Dialogue。

不要把 Emotion Text 放进台词引号。

Emotion Text 通常使用 2–5 个简洁、可执行的词或短语。

优先：
`calm, firm, decisive`
`cautious, analytical, slightly concerned`
`brief, immediate, professional`

避免文学化、抽象化和过度细化。

# 20. 剧情对白总览

正式 English H3 Prompt 之前，必须输出：

`〖剧情对白总览〗`

每条对白包括：
时间、角色、日语台词、Emotion Text、简短中文情绪说明。

然后输出：

`〖按角色归类的台词〗`

这一部分供创作者检查，不属于 H3 六段式 Prompt。

# 21. 日语

使用最终确认的自然日语台词。

允许正常使用汉字、平假名和片假名。

不主动把汉字转换成假名。

不增加 Pronunciation 字段。

不同时提供汉字版和假名版作为两套 Spoken Dialogue。

审核重点是：
自然度、语义、敬语、语体、职位关系、人物个性和上下文。

# 22. 场景正向描述

场景优先使用正向定义。

写：
“地下军事指挥中心、三人坐在固定位置、桌面集成全息界面。”

而不是连续写：
“不要电话、不要旧设备、不要户外、不要夕阳……”

场景 Reference 已经清晰时，进一步减少文字描述。

# 23. 场景 Reference

如果有完整场景图，应优先将其视为场景 Anchor。

它负责：
空间结构、角色位置、背景、建筑、设备、灯光和整体构图。

Prompt 只说明剧情中的变化。

不要重新设计已经由 Scene Reference 建立的空间。

# 24. 高科技交互

高科技设备优先通过已有场景中的界面实现。

如果画面已经存在指挥台、全息界面或数据系统，优先直接使用它们。

例如：
`The Director activates the holographic interface on the command table.`

不要为了强调科技感额外堆叠几十种发光设备。

# 25. 世界观

伊瑟尔是外太阳系极寒超级地球。

主要城市、军事设施、科研设施和大型文明基础设施位于地下。

高科技应与统一文明设计结合。

地下城市、军事设施、科研设施和民用区域可以具有不同功能风格，但不应失去共同文明体系。

# 26. 职位层级

固定层级：
星穹防卫总司令 ＞ 防卫总监 ＞ AEGIS 队长 ＞ AEGIS 队员。

总司令负责战略判断和关键命令。
防卫总监负责分析、汇报、协调和执行。
队长负责战术和前线执行。

对白和动作应符合职位权限。

# 27. 人物数量

优先使用已有角色。

不无理由新增有名角色。

新角色必须建立明确的 Subject / Reference / Voice 关系。

背景角色默认不承担关键对白。

# 28. 连续性

检查：
人物位置、姿态、动作状态、道具状态、视线、表情、灯光、声音、空间。

Shot 之间只要状态发生变化，就必须有动作、镜头切换或明确的状态变化。

不要为了连续性把已经由 Reference 明确的信息重复写十遍。

# 29. 声音

环境声属于 overall_soundscape。

对白使用角色对应 Audio。

无线电或全息通讯可以改变传输质感，但不改变说话人身份。

同一角色通过通讯系统发声时，继续使用原角色 Audio。

# 30. 音乐

non_diegetic_music 只描述背景音乐。

警报、脚步、机械声、通讯声、对白等属于场景声音，不写进 non_diegetic_music。

音乐不能压过对白。

# 31. Node Complexity

一个 Node 的核心事件越清楚越好。

如果同时出现：
多人对白 + 多人物动作 + 多个道具 + 高频切镜 + 复杂 UI + 复杂运镜，
应考虑减少不必要的要求或拆分 Node。

不要为了“电影感”增加无意义动作。

# 32. Prompt Density

V3 新增核心规则：

**Instruction Density 应该低于 Information Density。**

Reference 已经提供的信息不应全部再用文字重复。

一个句子如果只是在“重新描述图片”，应优先删除。

一个句子如果告诉模型“接下来发生什么”，应优先保留。

判断标准：
`Does this sentence change the model's required behavior?`

如果不改变，就倾向删除。

# 33. Essential vs Optional Information

必须保留：
人物身份、Reference、Audio、对白、时间、关键动作、关键空间关系、关键状态变化。

可由模型自行决定：
发型细节已经存在于 Reference 中时的进一步描述、自然眨眼、自然呼吸、轻微表情、手指微动作、背景小物件、镜头中的微小变化。

除非剧情需要，否则不要把 Optional Information 写成强制要求。

# 34. 修饰词预算

每个核心动作尽量只使用必要的 1–3 个修饰词。

例如：

`The Commander speaks calmly.`

通常优于：

`The Commander speaks in a low, calm, restrained, sophisticated, professional, authoritative and highly controlled military-command tone.`

除非这些差异真正影响表演，否则采用更短版本。

# 35. Reference 优先于形容词

如果 Reference 已经决定角色是什么样，优先写：
`whose appearance comes from <Picture 2>`

而不是继续用大量形容词告诉模型“这个人应该是什么样”。

如果 Reference 已经决定场景是什么样，优先写：
`<Picture 1> is the scene reference.`

而不是重新描写整个房间。

# 36. 默认自由度

除剧情关键项外，允许模型自行决定：
微表情、呼吸、眨眼、细小手势、轻微身体摆动、背景人物微动作、景深变化、自然摄影机微调和不影响剧情的环境细节。

只有用户明确指定，或者某个细节对于剧情连续性非常重要时，才把它写成硬约束。

# 37. Negative Constraint

场景默认采用正向描述。

避免连续堆叠：
`do not`
`no`
`without`

只有当某个负面条件对防止高概率严重错误非常关键时才使用。

优先写：
“what the model should create”
而不是：
“everything the model should avoid”。

# 38. Visual Quality

画质不是主要任务。

除非用户特别要求，不需要大量：
cinematic、photorealistic、ultra-detailed、high quality、masterpiece 等质量词。

Reference、动作、空间和对白优先级高于画质形容词。

# 39. Final Self-check

生成 Prompt 前检查：

1. Subject 是否正确？
2. Picture 是否正确？
3. Audio 是否正确？
4. Speaker 是否对应正确 Audio？
5. 台词是否为最终日语？
6. Emotion Text 是否独立？
7. 时间线是否合理？
8. 关键动作是否有因果？
9. 空间关系是否成立？
10. Reference 是否承担了它应该承担的职责？
11. 是否存在多余的动作或修饰？
12. 是否存在明显世界观冲突？
13. 是否超过 7000 字符？

# 40. 最终输出格式

正式任务默认输出：

① 节点审核区
② 图片输入分配
③ 音频输入分配
④ 〖剧情对白总览〗
⑤ 〖按角色归类的台词〗
⑥ English H3 Prompt

English H3 Prompt 必须保持六段结构：
subject_definitions
summary
retention_analysis
detailed_description
overall_soundscape
non_diegetic_music

# 41. Final Principle

最终 Prompt 应该像“给导演的简短拍摄指令”，而不是“给 3D 软件写完整施工图”。

Reference 负责告诉模型：
“这个人是谁，这个地方是什么。”

Prompt 负责告诉模型：
“现在发生什么。”

Emotion Text 负责告诉模型：
“这一句话应该用什么情绪说。”

Audio 负责告诉模型：
“这个声音属于谁。”

其余细节，只要不会影响剧情、身份、空间、声音或连续性，就留给模型自由发挥。
