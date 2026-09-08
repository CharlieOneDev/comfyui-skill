【最高优先级回复校验规则】
在生成任何回复之前，必须首先检查本条规则。
每一次回复的第一行、第一排文字，必须严格以“亲爱的指挥官，”开头。
“亲爱的指挥官，”是规则加载成功的校验标记，而不是正文内容的一部分，也不是角色对白。
如果最终回复的第一行没有“亲爱的指挥官，”，则视为本次回复未正确加载用户规则，后续内容全部视为无效，应先重新读取并遵守相关规则后再生成回复。
无论回复类型为何（普通问答、提示词、代码、翻译、修改、分析、文件处理等），都必须执行这一校验。
除非用户明确要求不要使用该校验语句，否则不得省略、移动、改写或放到第二行以后。
这是回复级别的强制前置校验，不属于具体任务的提示词内容。

# 《星穹防卫线》MiniMax H3 视频制作 Skill V2

项目专用完整制作规范，用于原创科幻动画《星穹防卫线 / AEGIS FRONTIER》的分镜设计、Node 拆分、MiniMax H3 Full-Reference 视频 Prompt 编写、角色固定 Voice Reference 管理、日语对白制作、镜头设计、声音设计、情绪表达与连续性监督。

## 0. 总原则

本 Skill 是《星穹防卫线》的项目级视频制作规范。MiniMax H3 通用规则负责 Full-Reference Prompt 结构、Subject / Picture / Video / Audio 标签、retention_analysis、时间线、运镜、物理因果、表演、灯光、声音和输出格式；本 Skill 负责项目世界观、人物身份、三语名称、Voice Reference、图片输入、音频输入、角色层级、伊瑟尔空间逻辑、地下都市与军事设施逻辑以及项目连续性。两者必须同时遵守。最终 Prompt 必须优先保证人物身份、参考关系、关键动作、关键对白、声音映射、关键时间点、空间连续性和任务目标，不为了堆砌形容词而增加无关复杂度。

## 1. 外部 H3 Prompt 规则

正式编写 MiniMax H3 Prompt 前，优先检查项目指定的通用 H3 Prompt 规则是否有更新：https://github.com/CharlieOneDev/comfyui-skill/blob/main/%E5%A4%9A%E6%A8%A1%E6%80%81%E4%BC%98%E5%8C%96%E6%8F%90%E7%A4%BA%E8%AF%8D%E5%85%83%E6%8C%87%E4%BB%A4_%E9%80%9A%E7%94%A8%E7%89%88.md；
如果可访问，以最新版本作为底层 Prompt 格式规范，本 Skill 作为《星穹防卫线》的项目补充规范。不得把 Full-Reference 改写成基础三段式 Prompt。默认最终 H3 Prompt 不超过 7000 个字符；如果超限，优先删除重复画质词、重复环境描述和冗余一致性说明，不得删除角色身份、关键参考关系、关键动作、对白、声音映射、关键时间点、空间连续性和核心剧情。

## 2. 生产单位

默认 1 Node = 15 秒 H3 生成单元。一个 Node 可以包含 1–3 个 Shot。优先在 Node 边界形成自然硬切，不为了凑满 15 秒而拖长镜头；如果剧情自然结束，可以使用 9 秒、10 秒、12 秒等真实时长。只有连续镜头真正超过 15 秒时才使用“长镜头警告”。多人对白、多人表演、关键道具动作、复杂镜头变化和复杂空间变化同时发生时，应主动评估 Node Complexity Risk。

## 3. H3 图片输入

H3 Full-Reference 最多使用 8 个 Picture 输入。Picture 编号没有固定意义，每个 Node 必须重新定义其用途。正式 Prompt 前必须输出“图片输入分配”，明确图1、图2、图3……分别连接什么输入。一个 Picture 只承担一个稳定职责；如果同一张图既负责整体空间，又负责人物座位和构图，必须明确写出其职责。人物 Reference 负责人物外观；场景 Reference 负责建筑、空间、材质、灯光、环境、布局、背景和空间连续性；局部位置 Reference 优先级高于整体空间 Reference，整体空间 Reference 优先级高于普通人物 Reference。

## 4. H3 音频输入

每个 Node 最多使用 3 个独立 Audio 输入。正式 Prompt 前必须输出“音频输入分配”，例如 Audio 1 = Commander，Audio 2 = Director。Audio 编号在同一个 Node 内始终保持相同含义。同一角色的视觉身份由人物 Reference 定义，声音身份由 Audio 定义。角色第一次发声时必须明确绑定 Audio，后续继续使用相同 Audio。Audio 可以用于声音身份、声音表达、直接复用或通信传输效果。已锁定的 Voice Reference 不需要在 Prompt 中重复长篇描述音色，Prompt 主要负责当前场景中的表达、语气和情绪。

## 5. Subject / Picture / Video / Audio 职责

Subject 表示目标视频中真正存在、复用、迁移、修改或持续追踪的实体，可以是人物、动物、车辆、产品、道具、场景、服装、动作、风格或特效。Picture 只有在承担首帧、关键帧、尾帧、精确构图或构图锚点时才需要单独定义；单纯作为人物外观来源时直接在 Subject 中引用即可。Video 用于视频编辑、视频续写、动作、镜头运动、剪辑节奏和时间结构。Audio 用于直接复制声音、Voice Reference、对白、表达、音乐或音效。每一个真正使用的标签都必须先定义；不要定义后文完全不用的标签；同一标签整个 Prompt 中不能改变含义。

## 6. Reference Leakage 防止

人物 Reference 只负责脸、五官比例、发型、发色、眼睛、皮肤、身体比例、服装、饰品和角色身份。场景 Reference 负责建筑、空间、材质、灯光、环境、布局、背景和空间连续性。载具、道具和装置 Reference 负责轮廓、尺寸、比例、材质、结构、机械设计和行为方式。不得把人物图背景迁移为新场景，也不得把场景图中的人物直接当作独立人物 Reference。人物视觉 Reference 与场景 Reference 发生职责交叉时，应明确各自负责什么。

## 7. Local Spatial Anchor

当人物的座位、站位、左右顺序、身体朝向、手的位置、人与设备之间的相对位置属于剧情关键时，应优先把具备明确空间关系的图片作为 Local Spatial Anchor。优先级为：精确局部位置 Reference ＞ 整体空间 Reference ＞ 普通人物 Reference ＞ 纯文字位置描述。Local Spatial Anchor 负责空间位置，不改变人物身份和外观。对于三人并排、驾驶席、指挥席、会议桌、战术操作台等场景，应首先锁定空间关系，再进行人物外观迁移。

## 8. 固定 Prompt 六段结构

最终 H3 Full-Reference Prompt 必须严格按照以下顺序：subject_definitions → summary → retention_analysis → detailed_description → overall_soundscape → non_diegetic_music。不得缺段、换序或替换为其他字段。

## 9. subject_definitions

subject_definitions 只定义实际使用的 Subject、Picture、Video、Audio 及其职责。每个真正使用的标签必须先定义。人物定义应简洁而明确，例如：`<Subject 1> is the Commander, whose appearance comes from <Picture 2>. Her voice reference is provided by <Audio 1>.` 如果一个 Picture 是整个场景的空间锚点，则必须明确其负责完整场景构图和空间关系。不要在这一段写大量剧情和动作。

## 10. summary

summary 第一行必须使用官方任务类型，例如 `[reference generation]`、`[reference generation + audio reference]`、`[video continuation + keyframe completion]`、`[audio reuse]` 等。summary 用于说明剧情目的、视觉目的、主要 Subject、参考关系、情绪方向和空间逻辑。summary 不得加入未定义标签，也不应该详细展开 Shot 级别动作。

## 11. retention_analysis

retention_analysis 必须逐条说明已经定义的 Reference 如何保留。视觉关系只能使用：`fully_preserved`、`partially_preserved`、`attribute_transfer`、`weak_reference`。音频关系只能使用：`fully_copy`、`partially_copy`、`reference`、`weak_reference`。不得自行创造新的关系词。retention_analysis 中禁止使用 `(S1)`、`(S2)` 等说话人 ID。人物和场景的 Reference 职责要分别写清楚。

## 12. detailed_description

这是整个 Prompt 最重要的部分，必须按照实际播放顺序书写。开头用一至两句定义整体视觉风格、摄影语言、色彩、灯光和画质基调，然后依次写 `[Shot 1]`、`[Shot 2] At 00:03.000, ...`、`[Shot 3] At 00:08.000, ...`。Shot 1 不写时间戳；后续 Shot 必须使用递增时间戳；所有时间必须小于视频总时长。普通切镜优先使用 `the camera cuts to`、`the shot cuts to`、`the shot transitions to`、`the shot changes to`、`the shot switches to`。只有用户明确要求时才使用 cross-dissolve、fade、wipe。每次切镜都必须重新说明必要的主体、状态、空间、视角和时间信息。仅改变一点角度时优先使用运镜，不要为了形式强行切镜。

## 13. 运镜

常用运镜包括 Zoom In、Zoom Out、Push In、Pull Out、Pan Left、Pan Right、Truck Left、Truck Right、Tilt Up、Tilt Down、Pedestal Up、Pedestal Down、Arc Shot、Tracking Shot 和 Static Shot。镜头运动必须有明确主语；例如 `the camera tracks backward` 的 backward 是 Camera 的运动，不是 Subject 的运动。摄影机移动与角色移动同时存在时必须明确区分。

## 14. 表演与动作

动作描述必须符合物理因果和时间顺序。避免同时要求高速复杂运动和大量精细微动作。人物自然表演时，眼睛先动，头部稍后，身体最后响应。表情变化应连续、渐进、符合台词情绪；避免机械微笑、持续瞪眼、随机面部抽动和相邻帧情绪突然跳变。高级军官、科学家和指挥人员通常采用克制、专业和微表情驱动的表演，除非剧情明确要求强烈情绪。

## 15. 对白与说话人

每条对白必须明确：谁说、何时说、对谁说、使用哪个 Audio、嘴型如何与声音同步以及呼吸和停顿如何同步。角色没有对白时使用 `No dialogue.` 并保持嘴唇自然闭合。画外音或远程通讯必须明确声音来源。若说话者同时实际出现在画面中，则继续使用该角色的 Subject 和 Audio，不得为同一个角色错误创建第三个独立 Voice。对白跨镜头时必须明确声音连续。禁止角色自行发挥对白，禁止使用 `according to the original script`、`say something appropriate` 或类似含糊表达，必须直接写最终真实台词。

## 16. 日语对白规则【V2 更新】

所有角色对白必须是自然、现代、符合语境的日语。Prompt 必须明确包含：`ALL SPOKEN DIALOGUE MUST BE NATURAL JAPANESE ONLY.`、`NO ENGLISH SPOKEN DIALOGUE.`、`NO CHINESE SPOKEN DIALOGUE.`。真正用于 H3 的对白直接写最终确定的日语台词，不需要额外生成假名版本，不需要对复杂日语进行假名转换，不需要同时提供汉字版和假名版，也不需要在 Prompt 中提供 Pronunciation 字段。正式名称、角色姓名和世界观资料仍可按照项目需要使用正式汉字或固定表记。日语对白的重点从“人工假名化”调整为“最终台词准确、自然、完整”。如果用户已经提供了经过确认的日语台词，默认保持原台词，不擅自改写其语言形式；只有明显的语法或语境错误才建议修改。

## 17. 日语对白的发音处理【旧规则废弃】

旧版中的“假名优先”“整句假名化”“逐词寻找汉字误读风险”“汉字版 + 假名版并列检查”等流程全部取消。当前音频 Reference 方法已经承担角色声音与发音稳定性的主要约束，因此不再执行额外的人工假名转换。除非用户明确要求，否则不要把日语台词中的汉字改写为平假名，不要添加括号读音，不要追加 Pronunciation 行，不要在一句台词中同时出现两套表记。

## 18. 剧情对白总览【新增】

在正式 English H3 Prompt 之前，必须增加一个“剧情对白总览”区域。该区域只用于帮助创作者快速检查整段剧情的对白顺序、说话人、情绪和表演方向，不属于发送给 H3 的六段式 Prompt。推荐格式：`【剧情对白总览】` → `角色：台词` → `Emotion Text：英文情绪描述`。每一句对白都应有对应的 Emotion Text。Emotion Text 应描述角色此刻如何说，而不是解释剧情，也不是修改台词。建议使用简洁、可表演化的英语，例如 `restrained curiosity`、`calm authority`、`cautious concern`、`immediate acknowledgment`、`professional operational focus`。Emotion Text 不得塞进台词引号内部。

## 19. Emotion Text 规则【新增】

Emotion Text 是“表演与情绪 metadata”，不是对白内容。Emotion Text 应独立存在于对白之外，优先使用简短、具体、可执行的描述，例如 `low, calm, authoritative, controlled curiosity`、`measured, analytical, slightly concerned`、`brief, obedient, professional`、`direct, operational, concise`。避免使用过于文学化、抽象或无法执行的表达，例如“有一种宇宙深处的悲凉”。Emotion Text 可以描述语气、节奏、力度、态度、紧张程度和情绪状态，但不得改写用户提供的台词。每一条重要对白最好只使用一组核心 Emotion Text，不要堆叠十几个相互冲突的情绪词。

## 20. Emotion Text 在 English Prompt 中的使用

Emotion Text 可以写进 detailed_description，但必须作为独立元信息存在，并与实际 Spoken Dialogue 分开。例如：`Emotion: restrained curiosity, calm and authoritative.` 下一句再写：`<Subject 1> speaks using <Audio 1>: "どう思う？"`。禁止写成：`<Subject 1> says nervously "どう思う？"` 或把 `[emotion: calm]` 放入引号中。Emotion Text 可以帮助模型理解表演方向，但真正的 Spoken Dialogue 必须保持纯粹，只包含要说出的日语。若用户要求的音频已经高度锁定表达方式，Emotion Text 应作为辅助表演指导，不应与 Voice Reference 发生冲突。

## 21. 声线与 Voice Reference

Voice Reference 主要负责锁定声音身份和基础声音特征；Prompt 中的 Emotion Text 与表演描述负责当前句子的具体表达。不要在 Prompt 中重新定义与 Voice Reference 冲突的音色、年龄或人格。一个角色可以在不同句子中具有不同的情绪，但 Voice Identity 必须稳定。最后一句如果仍由同一角色通过通讯系统说出，仍然使用该角色原本的 Audio。

## 22. 多人对白

一个 Node 最多 3 名独立 Voice Reference 角色。多人对白优先采用“角色 A 完整对白 → 停顿 / 反应 → 角色 B 完整对白 → 动作或反应”的结构，避免 A → B → A → B 高频交替。多人同 Node 时必须明确主动作角色、辅助反应角色和保持稳定的角色。对白越密集，越应该减少额外动作和复杂镜头变化。

## 23. 职位层级

《星穹防卫线》固定层级为：星穹防卫总司令 ＞ 防卫总监 ＞ AEGIS 战队队长 ＞ AEGIS 战队队员。上级负责最终战略判断、关键提问和最高命令；防卫总监负责信息整理、分析、汇报、协调和执行；队长负责前线判断、战术建议、接受命令和执行；队员负责专业汇报和执行任务。一般遵循“上级提问 / 判断 / 下令 → 下级汇报 / 回答 / 执行”，不得出现无理由越级指挥。

## 24. UI 与高科技交互

UI 优先使用 trajectory lines、target markers、orbital rings、arrows、geometric symbols、warning triangles、pulses、waveforms、planetary icons 和 abstract data patterns。界面信息应优先通过图形表达，而不是大量可读文字。对于高度先进的伊瑟尔科技，优先描述科技整合在建筑、家具和指挥台中的状态，不要依赖大量发光设备证明先进。高科技通讯优先采用无缝全息界面、悬浮数据层、空间投影、桌面集成式控制面板和直接呼叫界面等表现方式。若画面已有高科技控制台，应优先描述其原有的交互方式，而不是自行添加传统电话或老式通讯设备。

## 25. 伊瑟尔世界观

伊瑟尔 / Isara / ETHERA / イセラ是极端寒冷的外太阳系超级地球。地表环境极寒，冰原恶劣；主要人员设施、城市、大型机械和军事设施位于地下。地下与地表通过巨大入口、运输井、隧道和升降系统连接。世界观中的高科技设施应保持统一文明设计，不应随意从地下文明切换成普通露天现代基地。

## 26. 地下文明纵深

伊瑟尔地下设施应具有明显纵深、层级和空间秩序。大型空间可以表现出巨大的尺度，但要保持建筑和人物之间合理比例。地下设施的科技通常整合在建筑、墙体、地面、家具和操作台中，避免堆砌工业管线与杂乱设备。

## 27. 功能区域差异

民用区域：干净、温暖、高级、自然、宜居。科研区域：精密、安静、理性、高度整合。AEGIS 总部：正式、克制、权威、高级。地下兵工厂：可以更工业化、更大尺度、更具机械感，但必须保持整体文明设计统一。监测中心：高级科研机构、日式建筑、北欧极简、温暖浅色、技术隐藏于建筑中。

## 28. 人物数量

尽量使用现有角色，不无理由新增核心角色。背景无名人员可以存在，但不得突然承担对白或关键剧情职责。新增有名角色时必须提前说明并建立完整 Subject / Reference / Voice 关系。

## 29. 灯光

每个重要场景应有合理的 Key Light、Fill Light、Rim / Backlight、Ambient Light 和 Practical Light 来源。屏幕、灯具、全息界面等实际光源应合理影响附近表面。Volumetric Light 只有在存在雾、烟、尘、雨等介质时使用。连续 Shot 中光源方向、强度和色温必须保持合理连续。

## 30. 材质

皮肤应具有自然毛孔、细小绒毛和柔和次表面散射；金属具有真实环境反射和合理高光；玻璃具有透射、折射、Fresnel 与边缘高光；木材、石材和布料具有正确纹理尺度、粗糙度与高光。白色服装应保留织物纹理并避免过曝。

## 31. 摄影与画质

写实电影人物、时尚、高端商业和适合的科幻场景可以使用高质量电影级质感。摄影语言应服务剧情，不为了“高级”而持续推拉镜头。人物对白场景优先保证面部表情、嘴型、空间关系和声音可懂度。

## 32. 空间连续性

每个 Shot 必须在内部空间图上保持一致。左、右、前、后、上、下、入口、出口、桌面、设备和角色座位应保持清晰。镜头切换后，角色不得无原因地改变空间位置。若发生位置变化，必须在 Prompt 中明确移动过程或新的空间状态。

## 33. Shot 连续性

每次 Shot 切换检查主体、状态、运动、位置、台词、镜头、空间、灯光和情绪。若 Shot 2 继承 Shot 1 的动作或表情，应明确说明 continuing；若有新的动作或状态，应明确说明变化。不得让人物在相邻 Shot 中突然改变表情、姿势、位置或道具状态。

## 34. 声音连续性

声音必须与空间和画面一致。角色远距离说话时，不应同时描述成贴脸录音；无线电、通讯系统和全息通信应有适当的设备传输特征。角色真正说话时，使用其固定 Audio；远程角色如未实际出现在画面中，应明确 off-screen / radio communication speaker；如果远程声音属于画面中的同一角色，则继续使用原角色 Audio。

## 35. 音乐

non_diegetic_music 只描述非叙事音乐，不混入警报、引擎、脚步、机械、无线电或对白等 diegetic sound。对白密集场景中音乐必须低于对白。音乐情绪应与剧情一致，但不得压过人物 Voice。

## 36. Node Complexity Budget

当一个 Node 同时包含多人对白、多人动作、多个关键道具、复杂车辆动作、复杂空间变化、高频镜头切换和复杂声音设计时，需要评估 EXECUTION RISK。优先保证一个 Node 有一个主要剧情动作、一个主要对白行为或一个主要表演目标。15 秒不是必须塞满所有信息；宁可减少动作，也不要损害人物身份、对白和空间稳定性。

## 37. H3 Prompt 中的负面约束

对于场景生成，优先采用正向定义，不依赖长串负面场景提示。应明确描述“这个空间是什么、由哪些结构组成、光线如何、人物在哪里、设备如何工作、空间关系是什么”。除非某个负面条件对于防止严重错误不可替代，否则减少 `do not / no / without` 的连续堆叠。尤其对于场景 Reference，应以正向空间 Anchor 为核心，让模型首先理解正确环境，再通过少量必要约束辅助稳定。

## 38. 正向场景锚定

如果用户提供整张场景图，优先将其定义为 authoritative spatial reference / scene anchor。重点描述图中的已有建筑、布局、角色位置、桌面、设备、背景、灯光和空间关系。不要把场景图重新解释成“某种风格的科幻房间”；应让其成为整个 Node 的实际空间来源。人物图只补充人物身份，不改变场景 Reference 已经建立的空间。

## 39. 对白与 Emotion Text 的标准写法

推荐结构：
`Emotion: calm, restrained authority.`
`<Subject 1> speaks using <Audio 1> to <Subject 2>: "どう思う？"`
`Synchronize lip movement, breathing, pauses, and facial motion precisely with <Audio 1>.`
Emotion Text 永远独立于 Spoken Dialogue。不要把 `[calm]`、`(angry)`、`emotion: ...` 等文字塞入台词引号。不要在真正的日语台词后面追加情绪词。

## 40. 剧情对白总览的标准输出

正式 H3 Prompt 前，必须先给出：
`【剧情对白总览】`
`角色：台词`
`Emotion Text：英文情绪描述`
如果剧情有多句对白，则按照实际发生顺序列出。然后再提供：
`【按角色归类的台词】`
用于让用户快速查看每个角色完整说了什么。最后才进入 English H3 Prompt。

## 41. 按角色归类

在用户要求剧情设计或对白 Prompt 时，应在最终 Prompt 之外额外给出按角色归类的台词。该区域不是给 H3 的，因此可以使用中文角色名称、中文解释和正式世界观名称。角色归类必须与实际 Audio 映射一致。若角色在通讯中仍然是同一个角色，仍归入该角色名下，不创建“无线电声音”作为独立角色。

## 42. Audio 与 Emotion 的映射原则

一个角色的所有对白默认使用该角色绑定的 Audio，除非用户明确指定不同声音。不同句子可以具有不同 Emotion Text，但不得把情绪变化误写成新的 Voice Reference。通信设备可以改变声音的传输质感，但不改变说话者身份。对于全息通讯、无线电、耳机和远程连接，应在声音层说明传输效果，在角色层仍保持正确 Subject + Audio。

## 43. Final H3 Prompt 输出要求

当用户要求正式 H3 Prompt 时，输出顺序应为：
① 节点审核区
② 图片输入分配
③ 音频输入分配
④ 剧情对白总览
⑤ 按角色归类的台词
⑥ English H3 Prompt
English H3 Prompt 必须严格使用六段：subject_definitions、summary、retention_analysis、detailed_description、overall_soundscape、non_diegetic_music。除非用户明确要求，否则不要把上述中文审核区内容复制进 H3 Prompt。

## 44. Prompt 可执行性

每一个重要动作都必须有明确的主语。每个角色的对白必须明确对应 Audio。每个关键动作必须能够在 15 秒内完成。复杂的动作链、快速多人轮流讲话、高频切镜和复杂 UI 操作同时存在时，应降低复杂度。Prompt 的目标不是描述尽可能多的信息，而是让 H3 能够同时正确执行人物、环境、动作、对白、情绪、声音和镜头。

## 45. 最终自检

提交最终 H3 Prompt 前检查：角色数量是否正确；Subject 是否全部定义；Picture 是否全部正确映射；Audio 是否全部正确映射；每个说话人是否绑定正确 Audio；对白是否完整且仅为最终日语版本；Emotion Text 是否独立于对白；时间线是否递增；Shot 是否连续；人物位置是否连续；场景 Reference 是否保持；灯光是否连续；声音是否连续；是否出现未定义角色或第三声音；是否超过 Audio 限制；是否存在不必要的复杂动作；是否出现明显世界观冲突；最终 Prompt 是否保持六段结构；是否控制在 7000 字符以内。

## 46. V2 更新说明

本版本相对于旧版最重要的变化如下：第一，删除“复杂日语 → 假名转换 → 发音检查 → 假名优先”的人工流程，默认直接使用最终确认的自然日语台词；第二，在 English H3 Prompt 之前新增“剧情对白总览”；第三，为每句关键对白增加独立的 Emotion Text；第四，明确 Emotion Text 是 metadata，不属于 Spoken Dialogue，不得放入台词引号；第五，English Prompt 内部允许使用独立的 Emotion / Emotional performance 描述帮助 H3 理解表演，但不得让情绪说明成为角色需要朗读的内容；第六，强化场景正向描述和 Reference Anchor，降低长串场景负面提示的依赖；第七，明确同一角色通过全息通讯、无线电或其他通讯系统继续说话时，仍使用原角色 Subject 与 Audio，不创建新的声音角色。
