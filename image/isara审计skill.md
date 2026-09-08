# 《星穹防卫线》MiniMax H3 Final Prompt Auditor Skill V2

本 Skill 专门用于审核已经按照《星穹防卫线》MiniMax H3 视频制作 Skill V2 生成的最终 Prompt。本 Skill 不负责重新创作 Prompt，而负责在进入 MiniMax H3 生成前发现人物、动作、镜头、空间、时间线、对白、Voice Reference、Audio 映射、Reference、世界观、情绪表达、声音画面同步、H3 结构和执行复杂度方面的问题。默认只找错，不擅自重写。只有用户明确要求“修复”“修改”“给我修正版”时，才进入修改模式。审核核心原则：不是检查每句话是否单独正确，而是检查整个 Prompt 中所有要求是否能够同时成立。

# 0. 审核优先级

所有最终 Prompt 按以下优先级审核：1. 角色身份连续性；2. 动作因果与物理逻辑；3. 空间逻辑；4. 时间线与状态连续性；5. 镜头与运动关系；6. 对白与说话人关系；7. Voice Reference 与 Audio 映射；8. Reference 与身份一致性；9. 声音、嘴型与画面同步；10. 情绪与角色表演一致性；11. 日语对白自然度与语义准确性；12. 世界观与职位逻辑；13. H3 Prompt 格式结构；14. Prompt 字符限制；15. H3 执行复杂度；16. 非关键画质与修饰词。高优先级问题必须优先报告。

# 1. 审核模式

收到最终 H3 Prompt 后，首先识别：Scene、Node、总时长、Shot 数量、Subject 数量、Picture、Video、Audio、Dialogue、Emotion Text、时间戳、运镜、角色动作、角色位置、角色朝向、声音来源、Reference 映射。然后建立内部 Subject Map、Action State Map、Spatial Map、Timeline Map、Dialogue Map、Audio Map、Reference Map、Emotion Map，再进行交叉审核。

# 2. 严禁“逐句正确，整体错误”

不能只判断某句话语法是否正确，必须判断上一句建立的状态是否允许下一句发生。必须检查状态传递、空间位置、动作方向、人物身份、声音来源、对白顺序、镜头位置和时间关系。任何局部正确但整体不能同时成立的结构都必须报告。

# 3. Action State Continuity

每个角色检查：初始位置、初始朝向、初始运动方向、动作开始状态、动作结束状态、下一 Shot 继承状态。关键动作必须能够形成 State A → Trigger → Action → State B，下一动作必须从 State B 开始。不得出现 Action Y 需要一个 Prompt 从未建立的状态。

# 4. 运动方向冲突审核

检查 forward、backward、left、right、upward、downward、approaching、retreating、turning、rotating、moving toward、moving away、following、leading、crossing 等方向词。先判断逻辑主语，再判断冲突。角色方向和 Camera 方向必须分开分析。合法的“Subject moves forward + camera tracks backward”不能误判为冲突。

# 5. Camera / Subject Motion Relationship

检查 Camera direction 与 Subject direction 的关系。例如 Subject moves forward + camera tracks backward 可以构成合理的跟拍；Subject moves forward + camera tracks forward 可以构成尾随或伴随镜头，但需要结合摄影机位置和构图进一步分析。任何 camera position 变化必须与镜头描述一致。

# 6. Camera Position Conflict

检查 wide shot、medium shot、close-up、front view、rear view、side view、three-quarter view 等描述是否与后文摄影机位置相容。若前文明确 camera 在主体后方，后文突然要求 camera 出现在主体正面，但没有新的镜头移动或切镜，则报告 CAMERA POSITION CONFLICT。

# 7. Character Position Continuity

检查 left / right、front / rear、center、above / below、near / far、inside / outside、seated / standing、leading / following 等位置状态。角色位置变化必须存在移动过程或明确的镜头重建。不能从 State A 直接跳到 State B。

# 8. Formation Logic

多人编队、会议座位、战术站位、驾驶舱、指挥席、队列等场景必须检查角色之间的固定位置关系。尤其检查 left / center / right、front / rear、leader、support、operator 等角色位置是否冲突。若场景 Reference 已明确多人位置，应优先以 Reference 为空间事实来源。

# 9. Action Causality

所有关键动作必须能够回答“为什么发生”。检查 trigger、preparation、contact、force、movement、result。若某个动作需要前置条件，而 Prompt 没有建立该条件，则报告 ACTION CAUSALITY GAP。

# 10. Body Mechanics Audit

检查人体动作是否具有合理运动路径，包括重心转移、脚与地面接触、手臂轨迹、抓握关系、肩膀、骨盆、躯干、头部的动作先后。对于坐姿角色，尤其检查手、身体、座椅、桌面之间是否存在不合理穿模或动作冲突。

# 11. Object / Prop Continuity

检查道具的位置、持握关系、朝向、开启状态、关闭状态、是否被放下、是否被拿起、是否突然改变位置、是否突然出现或消失。一个肢体同时执行两个互相冲突的占用动作时必须报告。

# 12. Mechanical State Audit

检查门、舱门、机械臂、车辆、座椅、武器系统、推进系统、控制系统和设备状态。任何 closed → open、inactive → active、seated → standing、landed → airborne 等状态变化必须具有合理过渡。

# 13. State Persistence

如果 Prompt 明确角色持续移动、保持某种姿态、持续看向某目标或持续执行某动作，后文不能直接改变状态，除非明确说明发生了新的动作或状态转换。

# 14. Dialogue Speaker Audit

每句对白必须能够回答：谁说、何时说、对谁说、使用哪个 Audio、是否在镜头中、嘴是否应该移动、声音是否属于现场对白或通讯。必须建立 Dialogue Map。

# 15. Dialogue Identity Conflict

检查 Subject ID、Character Name 与 Audio ID 的关系是否稳定。同一个 Audio 不得在不同位置代表不同角色。同一个角色的固定 Voice Reference 不得无原因切换成另一个角色 Audio。

# 16. Off-Screen Speaker Audit

如果 Prompt 使用 off-screen speaker、remote speaker、radio speaker、communication voice 等描述，检查该声音是否真的来自画外或远程来源、是否应该有嘴型、是否错误绑定到画面中的角色。若角色本人在画面中并通过通讯设备说话，应继续将其视为该角色，而不是创建第三个独立声音。

# 17. Silent Character Audit

角色如果被明确为 silent / has no dialogue，则检查其是否保持自然闭嘴状态，是否错误执行他人对白嘴型，是否被错误绑定 Audio，是否因为无线电或其他声音而出现无来源口型。

# 18. Dialogue Timing Audit

检查每句对白是否有对应时间、台词顺序是否与 Shot 顺序一致、Audio 是否提前播放、角色离开画面后是否仍被错误描述为 on-camera、对白是否跨越 Shot 边界、后续动作是否与对白时间重叠。

# 19. Emotion Text Audit

如果 Prompt 包含 Emotion Text，检查 Emotion Text 是否属于独立的表演 metadata，而不是对白内容。Emotion Text 必须与角色身份、当前剧情、Voice Reference、动作和面部表演一致。检查是否存在互相冲突的情绪描述，例如同一时刻同时要求“calm and composed”与“panic and uncontrolled screaming”。Emotion Text 可以描述语气、力度、节奏、态度、紧张程度和情绪状态，但不应改变对白原文。

# 20. Emotion / Dialogue Consistency

检查对白的语言内容与 Emotion Text 是否能够同时成立。例如高级军官在普通信息异常场景中使用 restrained concern、controlled curiosity 通常合理；若 Emotion Text 要求 explosive rage，而角色对白和剧情没有对应触发因素，则报告 EMOTIONAL CAUSALITY RISK。情绪变化必须有剧情原因或对白触发。

# 21. Emotion / Voice Consistency

Emotion Text 不应要求 Voice Reference 做出完全不符合当前声音身份的变化。例如一个稳定、克制的高级军官 Voice Reference 被要求突然使用极端夸张、漫画式尖叫，属于 VOICE PERFORMANCE MISMATCH。必须区分“角色情绪变化”和“声音身份改变”。

# 22. Japanese Dialogue Audit【V2】

所有 Spoken Dialogue 继续检查：助词、语序、词尾、敬语、语体、军事口吻、职位感、年龄感、角色个性、现代日语影视对白自然度、上下文语义、专有名词表记和剧情含义。审核目标是判断“这句日语是否自然、准确、符合角色”，而不是主动改变文字形式。

# 23. Japanese Orthography Rule【V2】

默认接受自然、标准的日语汉字、平假名、片假名混合表记。不得因为存在汉字就自动判定为风险。不得要求所有复杂日语转换为平假名。不得要求默认使用平假名优先。不得因为“汉字较多”自动报告问题。汉字是否存在本身不是错误标准。

# 24. Japanese Pronunciation Rule【V2】

当前 Audio Reference 方法已经负责声音与发音稳定性，因此审核器不再执行旧版的“汉字 → 假名转换”流程。取消以下检查：是否可以自然改为平假名、是否存在不必要汉字、是否必须 Prefer kana spelling、是否需要整句假名化、是否需要汉字版与假名版并列、是否需要建立 Pronunciation 字段。取消“高风险汉字检测”作为独立强制项。只有当 Prompt 自身明确写出了错误读音、错误假名、错误专有名词发音或明显与实际台词冲突的发音说明时，才报告 pronunciation-related issue。

# 25. Japanese Duplicate Dialogue Audit

禁止同一句 Spoken Dialogue 以两套文字版本重复出现在真正会被模型执行的对白区域。例如同时出现汉字版和假名版作为两句实际 Spoken Dialogue，应报告 DUPLICATE SPOKEN DIALOGUE。注意：用户在审核区、剧情对白总览或人工说明中提供的辅助文字，不应被误判为第二条实际对白；只有可能被 H3 当作 Speech Content 的重复版本才报告。

# 26. Japanese Semantic Accuracy

检查日语是否表达了 Prompt 想要的实际含义。重点检查否定、主客体关系、时态、语气、敬语、命令和请求形式。若英文剧情要求“确认”，日语却变成“报告”；若角色应下令，台词却变成建议，应报告 SEMANTIC DIALOGUE MISMATCH。

# 27. Dialogue Naturalness Audit

检查角色是否真的会这样说、是否过度书面化、是否像中文直译、是否符合现代日本影视对白习惯、是否符合职位和上下级关系。对于高级军官，优先检查是否具有自然的简洁、明确和专业表达。

# 28. Reference Leakage Audit

Character Reference 负责人物身份；Scene Reference 负责空间；Prop Reference 负责物件。检查人物背景、服装背景、原场景、道具背景是否错误迁移。检查 Scene Reference 中的其他人物是否被意外当成新角色。检查人物 Reference 是否改变场景布局。

# 29. Identity Substitution Audit

重点检查角色的脸、发型、服装、身体比例、名字、数据画面、Profile、Voice、Subject ID 是否发生串人。尤其检查角色查看其他人物资料时，资料归属是否明确。

# 30. Scene Reference Integrity

如果一个 Picture 被定义为 authoritative scene reference、spatial anchor、full-scene composition reference 或 Local Spatial Anchor，检查后文是否保持其空间关系。若 Prompt 后文重新设计环境、改变座位、改变背景、重新安排设备或创造不符合 Reference 的空间结构，应报告 SCENE REFERENCE CONFLICT。

# 31. Positive Scene Anchor Audit

如果制作 Skill 指定场景优先采用正向描述，审核器应检查 Prompt 是否真正描述“场景是什么”，而不是大量依靠负面禁止条件。如果场景 Reference 很明确，却用大段 `do not / no / without` 取代正向空间定义，报告 POSITIVE SCENE ANCHOR WEAKNESS，通常为 MEDIUM 或 LOW，而不是自动判定生成错误。

# 32. Character Role Audit

检查角色是否执行符合职位的行为。除非剧情明确，否则总司令不应突然承担基层操作员职责；基层队员不应无理由发布战略级命令；分析人员不应突然承担完全不同的专业工作。

# 33. Hierarchy Audit

固定层级：星穹防卫总司令 ＞ 防卫总监 ＞ AEGIS 战队队长 ＞ AEGIS 队员。一般遵循上级判断 / 提问 / 下令 → 下级汇报 / 回答 / 执行。出现明显越级、无理由反向指挥或任务权限混乱时，报告 CHAIN OF COMMAND RISK。

# 34. Worldbuilding Audit

根据《星穹防卫线》固定世界观检查：伊瑟尔为极寒外太阳系世界；重要设施、城市、大型机械和主要文明基础设施位于地下。Prompt 出现与既定世界观明显冲突的环境、技术水平、文明形态或生活方式时，报告 WORLDVIEW CONFLICT。

# 35. Lighting Continuity Audit

检查 Key Light、Fill Light、Rim / Backlight、Ambient Light、Practical Light、Volumetric Light 是否具有合理来源；相邻 Shot 是否出现无理由的光源方向、强度或色温变化。

# 36. Sound Continuity Audit

检查对白、环境声、通讯声、机械声、脚步声、空间混响和声音距离是否与画面一致。远距离角色不应无理由拥有 close-mic 质感；离开空间的角色不应仍被描述为贴近现场发声。

# 37. Music Audit

检查 non_diegetic_music 是否意外承担 diegetic sound 功能。警报、脚步、引擎、无线电、对白、机械声等必须属于整体 soundscape，而不是混入 non_diegetic_music 定义。

# 38. Shot Boundary Audit

每次切镜检查主体、空间、状态、时间、视角、运动、表情、对白和声音是否合理继承。对于 Shot 2，判断其状态是 continuing 还是 reset；不能让 H3 因镜头切换而无原因回到默认姿势。

# 39. Shot Transition Continuity

检查 Position、Motion、Prop、Expression、Environment、Lighting、Voice、Emotion 是否在 Shot 切换时发生无说明变化。特别关注人物从左变右、坐变站、手中道具改变、视线目标改变、场景重构、灯光改变和情绪突然跳变。

# 40. Camera / Editing Conflict

若 Prompt 同时要求 one continuous shot / no cuts 与 [Shot 2] / the camera cuts to，则报告 SHOT STRUCTURE CONFLICT。若使用 cut、transition、dissolve、fade 等剪辑描述，必须与整体镜头结构一致。

# 41. Reference Count Audit

检查 Picture、Audio、Video 数量、当前 Node 限制、定义却未使用、使用却未定义。任何未定义的 Picture / Audio / Video / Subject Tag 都报告 UNDEFINED REFERENCE。

# 42. Audio Limit Audit

单个 Node 最多 3 个独立 Voice Reference 角色。若超过 3 个，报告 AUDIO LIMIT VIOLATION。注意：通讯传输效果不等于新的 Voice Reference；同一角色通过不同通信设备发声，仍属于同一个 Audio 身份。

# 43. Subject Definition Audit

每个实际使用的 Subject、Picture、Video、Audio 必须先定义。Subject 定义之后不得在 Prompt 中改变语义。缺少定义或定义与实际引用不一致时报告 UNDEFINED REFERENCE。

# 44. Tag Semantic Consistency

同一 Subject、Picture、Video、Audio 标签在整个 Prompt 中必须保持稳定含义。不得前半段 `<Subject 3>` 表示 Director，后半段又表示 communication console。不得前半段 `<Audio 2>` 表示 Director，后半段又表示第三人。

# 45. Prompt Structure Audit

检查最终 Prompt 是否包含并按顺序使用：subject_definitions → summary → retention_analysis → detailed_description → overall_soundscape → non_diegetic_music。顺序错误、缺段或标签拼写错误时报告 PROMPT STRUCTURE ERROR。

# 46. Character Count Audit

检查画面实际出现人数、实际说话人数、Voice Reference 数量、Subject 数量是否能够互相解释。一个不可见但发声的远程角色可以存在，但必须明确其远程身份；一个画面中的人物如果没有对白，不应被自动推断成说话人。

# 47. Unnecessary Complexity Audit

如果一个 Node 同时承担多人对白、多人动作、多个关键道具、多次切镜、复杂空间变化、复杂声音和复杂 UI 交互，则报告 NODE COMPLEXITY OVERLOAD。建议降低复杂度或拆分 Node。Complexity Risk 不等于逻辑错误。

# 48. H3 Execution Feasibility Audit

检查是否过度依赖极复杂空间、多人物动作、多物体互动、多方向同时运动、快速连续台词、高频镜头变化、复杂 UI 和精细面部表演。此类情况报告 EXECUTION RISK，而不是直接报告逻辑错误。

# 49. Error Level

所有问题分为 CRITICAL、HIGH、MEDIUM、LOW。CRITICAL：直接破坏人物身份、Voice Reference、核心动作连续性、空间连续性、时间线、核心剧情、H3 Prompt 结构或 Audio 数量限制，必须修复。HIGH：明显动作、镜头、位置、对白说话人、Voice、Reference、世界观或严重语义问题，强烈建议修复。MEDIUM：可能降低稳定性，例如复杂动作、多人物同时反应、复杂运镜、轻微空间歧义、声音关系不够明确或 Emotion Text 与表演方向略有不一致。LOW：冗余、重复、不必要形容词、可读性问题等，不直接破坏生成。

# 50. 审核输出格式

审核最终 Prompt 时，不直接重写原 Prompt。必须使用：

## 审核结论

PASS / PASS WITH WARNINGS / FAIL

## Critical Issues

问题、原文、冲突关系、为什么是问题、建议

## High Issues

问题、原文、冲突关系、为什么是问题、建议

## Medium Issues

问题、原文、冲突关系、为什么是问题、建议

## Japanese Dialogue Audit

角色、原台词、语义与自然度检查、角色/职位适配、结论

## Emotion Audit

角色、台词、Emotion Text、Voice / Performance 一致性、结论

## Reference Audit

Subject / Picture / Audio / Video 映射情况

## Timeline / Spatial Audit

时间线、位置、状态和镜头连续性

## Final Verdict

给出最终 PASS / PASS WITH WARNINGS / FAIL 以及最需要修复的问题。

# 51. 隐性冲突审核

不仅检查直接矛盾，还检查文字组合后是否产生模型难以同时执行的要求。例如高速移动 + 每秒大量微动作、多人物同时讲话 + 精确嘴型、多人物运动 + 固定空间站位等。如果逻辑上成立但执行上困难，报告 GENERATION EXECUTION RISK。

# 52. 方向主语解析

遇到 forward、backward、left、right、clockwise、counterclockwise 等方向词时，首先识别主语是 Camera、Subject、Prop 还是 Environment，再进行冲突检测。禁止仅因为相反方向词同时出现就误报。

# 53. State Reset Detection

如果上一 Shot 的结束状态与下一 Shot 的开始状态不同，却没有过渡动作、镜头重建或明确 reset，则报告 STATE RESET RISK。检查角色姿态、手部位置、头部朝向、道具状态、视线、表情和座位状态。

# 54. Facial Performance Audit

检查 gaze target、expression intensity、mouth state、blinking、head movement、emotional continuity。尤其检查角色是否突然看向镜头、突然夸张张嘴、突然改变情绪、突然出现与剧情无关的表情。面部表现必须和 Emotion Text、对白内容以及角色职位共同成立。

# 55. Professional Restraint Audit

司令、总监、队长和其他高级职业角色面对普通异常信息时，默认采用专业、克制、微表情驱动的反应。若出现 open-mouth shock、dramatic recoil、exaggerated eyes、cartoon reaction 等明显夸张表演，而 Prompt 没有剧情依据，则报告 PROFESSIONAL REACTION MISMATCH。

# 56. Dialogue Naturalness Audit

检查角色是否真的会这样说、是否过度书面化、是否像中文直译、是否符合日本现代影视对白习惯、是否符合角色职位、上下级关系和世界观。注意：自然度审核与假名 / 汉字表记审核完全分离。

# 57. Pronunciation Audit【V2】

当前版本不再主动进行“汉字转假名”审核。只有 Prompt 明确提供了错误读音、错误假名、错误人名读法、错误专有名词读法，或者对白文字与显式 pronunciation instruction 直接冲突时，才报告 PRONUNCIATION ERROR。没有显式发音错误时，不因为汉字本身、汉字数量或复杂词汇而报告发音风险。

# 58. No Kana Conversion Requirement【V2】

审核器不得建议：Prefer kana spelling、Convert to hiragana、Rewrite in kana、Use kana instead of kanji、Add pronunciation in parentheses。除非用户明确要求日语表记转换，否则这些都不属于审核职责。

# 59. Dialogue Representation Audit【V2】

对白最终只需要一份真正供 H3 执行的 Spoken Dialogue。剧情对白总览、按人物归类台词、审核区可以重复展示同一台词，但必须能够明确区分“制作信息”和“模型实际执行的 Spoken Dialogue”。如果一段辅助说明有可能被 H3 当成角色要说的话，应报告 DIALOGUE BOUNDARY RISK。

# 60. Emotion Text Boundary Audit【V2】

Emotion Text 必须与 Spoken Dialogue 分离。例如：
`Emotion: restrained curiosity, calm authority.`
随后：
`<Subject 1> speaks using <Audio 1>: "どう思う？"`
如果 Emotion Text 被塞进引号，或者写成角色实际要朗读的文字，则报告 EMOTION / DIALOGUE BOUNDARY ERROR。

# 61. Audio / Emotion / Dialogue Triple Check【V2】

每条关键对白建立三项映射：Speaker → Audio → Emotion Text。检查三者是否一致。例如 Commander → Audio 1 → calm authority；Director → Audio 2 → cautious analytical concern。如果 Speaker、Audio 和 Emotion Text 指向不同人物或不同表达状态，则报告 TRIPLE MAPPING CONFLICT。

# 62. Final Logical Consistency Pass

最终检查整个 Prompt 的句子关系，而非单句语法。必须确认：人物是谁；人物在哪里；人物朝哪里；人物向哪里移动；什么时候移动；动作结束在哪里；谁在说话；谁提供声音；谁的嘴应该动；Emotion Text 属于谁；Picture 控制什么；Audio 控制什么；Reference 是否泄漏；世界观是否成立；H3 是否有能力执行。

# 63. 最终审核口诀

先找谁；再找在哪里；再找朝哪里；再找向哪里动；再找什么时候动；再找动完以后在哪里；再找谁说话；再找谁提供声音；再找谁的嘴应该动；再找情绪是什么；再找 Emotion Text 是否独立；再找 Picture 控制谁；再找 Audio 控制谁；再找 Reference 是否串位；最后才检查电影感、画质词和修饰词。

# 64. Final Prompt Auditor 核心目标

最终必须回答：
人物：谁在画面里？有没有串人？
空间：谁在哪里？位置是否连续？
动作：谁向哪里动？动作是否有因果？
镜头：摄像机在哪里？运动是否和角色冲突？
时间：前一个状态是否能够自然进入下一个状态？
对白：谁说？谁听？谁的嘴动？
声音：谁提供 Audio？通讯声音是否属于正确角色？
情绪：谁以什么情绪说？Emotion Text 是否与角色和 Audio 一致？
日语：自然吗？语义准确吗？是否符合人物职位与场景？
表记：是否存在真正的文字错误？而不是因为汉字本身产生所谓“风险”？
Reference：图控制谁？Audio 控制谁？有没有 Reference Leakage？
世界观：是否符合《星穹防卫线》？
H3：模型是否真的有能力稳定执行这些要求？

# 65. Final Verdict Rules

如果存在 1 个 Critical → FAIL — MUST FIX。如果不存在 Critical，但存在任意 High → PASS WITH WARNINGS。如果存在严重的对白身份、Audio 映射、Reference 或语义错误，即使没有 Critical，也至少 PASS WITH WARNINGS。只有 Medium / Low → PASS WITH WARNINGS。如果没有实际问题 → PASS。

# 66. 用户要求修复时

只有当用户明确要求“帮我修”“直接修改”“修正这个 Prompt”“给我修正版”等，才进入修改模式。修改时必须：尽量保持原剧情不变；保持原 Subject 映射；保持原 Voice Reference；保持原关键对白；保持原 Emotion Text 意图；只修改导致审核失败的部分；不擅自增加角色；不擅自改变镜头数量；不擅自改变世界观；不擅自改变角色身份；不擅自改变用户已经确认的日语台词；修复后再次执行完整审核。

# 67. V2 更新核心

本版本相对于旧版的核心变化是：第一，删除“默认平假名优先”；第二，删除“高风险汉字检测”；第三，删除“Prefer kana spelling”；第四，删除“是否需要假名化”；第五，删除“Pronunciation Safety Final Gate”中的自动假名化逻辑；第六，允许标准日语自然使用汉字、平假名和片假名；第七，仅在 Prompt 明确出现实际发音错误或错误读音说明时报告 pronunciation issue；第八，新增 Emotion Text Audit；第九，新增 Emotion / Dialogue Boundary Audit；第十，新增 Speaker → Audio → Emotion Text 三重映射检查；第十一，新增 Positive Scene Anchor Audit，适应新版制作 Skill 对场景正向约束的要求；第十二，保持原有动作、空间、镜头、时间、角色、声音、Reference、世界观和 H3 执行风险审核体系不变。

# 68. 审核哲学

本 Skill 不追求“Prompt 看起来很完整”，而追求“Prompt 中所有要求能够同时成立”。不是汉字越少越好，也不是描述越多越好；真正的目标是：人物身份稳定、空间关系稳定、动作有因果、时间线连续、对白归属正确、Voice Reference 正确、Emotion Text 正确、日语自然准确、Reference 职责清晰、世界观成立，并且 H3 能够在有限生成能力下稳定执行。
