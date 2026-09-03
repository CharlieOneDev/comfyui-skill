《星穹防卫线》MiniMax H3 视频制作 Skill																									
项目专用完整制作规范																									
																									
用于原创科幻动画《星穹防卫线 / AEGIS FRONTIER》的分镜设计、Node 拆分、MiniMax H3 Full-Reference 视频 Prompt 编写、角色固定 Voice Reference 管理、日语对白制作、镜头设计、声音设计与连续性监督。																									
																									
0. 总原则																									
																									
本 Skill 是《星穹防卫线》的项目级制作规范。																									
																									
MiniMax H3 通用 Prompt 规则负责：																									
																									
Full-Reference Prompt 结构																									
																									
Subject / Picture / Video / Audio 标签																									
																									
retention_analysis																									
																									
时间线																									
																									
运镜																									
																									
物理因果																									
																									
表演																									
																									
灯光																									
																									
声音																									
																									
输出格式																									
																									
本 Skill 负责：																									
																									
《星穹防卫线》的世界观																									
																									
人物身份																									
																									
三语名称																									
																									
日语固定读音																									
																									
Voice Reference																									
																									
H3 图片输入																									
																									
H3 音频输入																									
																									
每 Node 最多3个独立声音输入																									
																									
角色层级																									
																									
伊瑟尔空间逻辑																									
																									
地下都市与军事设施逻辑																									
																									
项目连续性																									
																									
两者必须同时遵守。																									
																									
1. 外部 H3 Prompt 规则																									
																									
正式编写 MiniMax H3 Prompt 前，优先读取：																									
																									
https://github.com/CharlieOneDev/comfyui-skill/blob/main/多模态优化提示词元指令_通用版.md																									
																									
使用规则：																									
																									
每次开始新的 H3 Prompt 任务时，优先检查该文档是否有更新。																									
																									
可访问时，以其最新规则作为 H3 Prompt 的底层格式规范。																									
																									
本 Skill 作为《星穹防卫线》的项目补充规范。																									
																									
不得把 Full-Reference 改写成基础模式的三段式结构。																									
																									
最终 H3 Prompt 不超过 7000 个字符。																									
																									
如果字符超限，优先删除重复的画质形容词、次要环境细节和重复一致性规则。																									
																									
不得压缩或删除：																									
																									
角色身份																									
																									
关键参考关系																									
																									
关键动作																									
																									
重要对白																									
																									
声音映射																									
																									
关键时间点																									
																									
空间连续性																									
2. 生产单位																									
																									
默认 1 Node = 15秒 H3 生成单元。																									
																									
一个 Node 可以包含 1–3 个 Shot。																									
																									
优先在 Node 边界形成自然硬切。																									
																									
不为了凑满15秒而拖长镜头。																									
																									
场景自然结束时可以使用 9秒、10秒、12秒等真实时长。																									
																									
连续镜头真正超过15秒时才使用：																									
⚠️【长镜头警告】																									
3. H3 图片输入																									
																									
H3 Full-Reference 最多使用 8 个图片输入。																									
																									
Picture 编号没有固定含义。																									
																									
每个 Node 必须重新定义：																									
																									
图1																									
																									
图2																									
																									
图3																									
																									
…																									
																									
下一 Node 可以完全重新分配。																									
																									
因此每个正式 Prompt 前必须输出：																									
																									
【图片输入分配】																									
图片	输入内容	用途																							
图1	XXX	XXX																							
图2	XXX	XXX																							
图3	XXX	XXX																							
图4–8	不使用	—																							
																									
用户必须可以根据这张表直接连接 ComfyUI H3 输入。																									
																									
4. H3 音频输入【硬性限制】																									
																									
每个 Node 最多使用3个独立 Audio 输入。																									
																									
因此：																									
																									
一个15秒 Node 最多支持3个需要固定 Voice Reference 的明确说话角色。																									
																									
例如：																									
																									
音频	对应角色																								
Audio 1	神崎紫苑																								
Audio 2	神代玲奈																								
Audio 3	白神凛																								
																									
不得让第四个独立 Voice Reference 角色在同一个 Node 中说话。																									
																									
4.1 音频输入分配																									
																									
只要 Node 中存在固定 Voice Reference 的对白角色，正式 Prompt 前必须输出：																									
																									
【音频输入分配】																									
音频	输入内容	对应角色																							
音频1	XXX Voice Reference	XXX																							
音频2	XXX Voice Reference	XXX																							
音频3	XXX Voice Reference	XXX																							
																									
如果不使用音频：																									
																									
音频	输入内容	对应角色																							
音频1–3	不使用	—																							
4.2 Audio 与角色绑定																									
																									
在 subject_definitions 中明确：																									
																									
<Subject 1> is Shiragami Rin, whose appearance comes from <Picture 1>. Her voice reference is provided by <Audio 1>.																									
																									
在 detailed_description 中，角色说话时再次自然引用：																									
																									
<Subject 1> speaks using <Audio 1>.																									
																									
Audio 编号在当前 Node 内始终保持相同含义。																									
																									
4.3 一个角色同时占用图片和音频																									
																									
同一角色：																									
																									
人物图负责视觉身份。																									
																									
Audio 负责声音身份。																									
																									
例如：																									
																									
<Subject 1> is Asakura Chikage, whose appearance comes from <Picture 1>. Her voice reference is provided by <Audio 2>.																									
5. Subject / Picture / Video / Audio 的职责																									
Subject																									
																									
Subject 表示目标视频中真正存在、复用、迁移、修改或持续追踪的实体。																									
																									
可以是：																									
																									
人物																									
																									
动物																									
																									
车辆																									
																									
产品																									
																									
道具																									
																									
场景																									
																									
服装																									
																									
动作																									
																									
风格																									
																									
特效																									
																									
一个 Subject 可以由多个素材共同定义。																									
																									
例如：																									
																									
<Subject 1> is Shiragami Rin, whose appearance comes from <Picture 1> and whose movement pattern comes from <Video 1>.																									
Picture																									
																									
只有当图片本身承担：																									
																									
首帧																									
																									
关键帧																									
																									
尾帧																									
																									
精确构图																									
																									
构图锚点																									
																									
时，才额外建立 <Picture N> 条目。																									
																									
如果一张图只是人物外观来源，则应在 Subject 中引用，不必为了形式单独定义一个 Picture Subject。																									
																									
Video																									
																									
Video 表示：																									
																									
视频编辑																									
																									
视频续写																									
																									
整段动作																									
																									
镜头运动																									
																									
剪辑节奏																									
																									
时间结构																									
																									
Video 不能代替其中的人物、车辆、道具或动作 Subject。																									
																									
Audio																									
																									
Audio 可以表示：																									
																									
直接复制音频																									
																									
参考声音音色																									
																									
参考人物表达																									
																									
参考对白																									
																									
参考歌词																									
																									
参考音乐																									
																									
参考节奏																									
																									
参考音效																									
																									
普通参考视频即使包含声音，也不能自动建立 Audio。																									
																									
只有目标视频真正使用或参考该声音时才建立 Audio。																									
																									
6. Reference Leakage 防止规则																									
																									
人物 Reference：																									
																									
负责：																									
																									
脸																									
																									
五官比例																									
																									
发型																									
																									
发色																									
																									
眼睛																									
																									
身材比例																									
																									
服装																									
																									
饰品																									
																									
身份																									
																									
场景 Reference：																									
																									
负责：																									
																									
建筑																									
																									
空间																									
																									
材质																									
																									
灯光																									
																									
环境																									
																									
布局																									
																									
背景																									
																									
空间连续性																									
																									
载具 / 道具 / 装置 Reference：																									
																									
负责：																									
																									
轮廓																									
																									
尺寸																									
																									
比例																									
																									
材质																									
																									
结构																									
																									
机械设计																									
																									
行为方式																									
																									
不得把：																									
																									
人物图背景 → 新场景																									
																									
场景图人物 → 新角色																									
																									
坠毁图火焰 → 正常飞船																									
																									
地表冰原 → 地下设施																									
																									
兵工厂工业风 → 民用城市																									
																									
错误迁移。																									
																									
7. 人物引用规则																									
																									
人物定义使用简洁写法：																									
																									
<Subject 1> is Asakura Chikage, whose appearance comes from <Picture 1>.																									
																									
避免反复写：																									
																									
<Picture 1> controls only...																									
Whenever...																									
<Picture 1> is the sole...																									
																									
但人物出现在 Shot 中时，必须明确对应 Picture：																									
																									
Cut to <Picture 2>, Kamishiro Reina.																									
																									
不能只写：																									
																									
Cut to Reina.																									
8. 固定 Prompt 六段结构																									
																									
最终 H3 Full-Reference Prompt 必须严格按照以下顺序：																									
																									
subject_definitions																									
summary																									
retention_analysis																									
detailed_description																									
overall_soundscape																									
non_diegetic_music																									
																									
不得：																									
																									
缺段																									
																									
换序																									
																									
用其他字段替代																									
																									
改成 integrated_multimodal_description																									
9. subject_definitions																									
																									
只定义：																									
																									
Subject																									
																									
Picture																									
																									
Video																									
																									
Audio																									
																									
以及它们的职责。																									
																									
每个真正使用的标签都必须先定义。																									
																									
不要定义后文完全不用的标签。																									
																									
同一标签整个 Prompt 中只能有一个含义。																									
																									
10. summary																									
																									
第一句必须使用官方任务类型：																									
																									
[reference generation]																									
																									
或：																									
																									
[reference generation + audio reference]																									
																									
或：																									
																									
[video continuation + keyframe completion]																									
																									
等。																									
																									
官方任务类型包括：																									
																									
keyframe completion																									
																									
reference generation																									
																									
video editing																									
																									
video continuation																									
																									
audio reuse																									
																									
audio reference																									
																									
summary 用于：																									
																									
剧情目的																									
																									
视觉目的																									
																									
主要 Subject																									
																									
参考关系																									
																									
情绪与空间逻辑																									
																									
不要在 summary 里添加未定义标签。																									
																									
11. retention_analysis																									
																									
逐条说明所有已定义参考的保留关系。																									
																									
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
																									
例如：																									
																									
<Subject 1> (appears in [Shot 1], [Shot 2]): fully_preserved - ...																									
<Audio 1>: reference - ...																									
																									
retention_analysis 中禁止使用 (S1)、(S2) 等说话人 ID。																									
																									
12. detailed_description																									
																									
这是整个 Prompt 最重要的部分。																									
																									
必须按照实际播放顺序写。																									
																									
开头用一至两句定义：																									
																									
整体视觉风格																									
																									
摄影语言																									
																									
色彩																									
																									
灯光																									
																									
画质基调																									
																									
然后依次写：																									
																									
[Shot 1]																									
[Shot 2] At 00:03.000, ...																									
[Shot 3] At 00:08.000, ...																									
12.1 Shot 时间规则																									
																									
[Shot 1] 不写时间戳。																									
																									
后续 Shot 必须使用递增时间戳。																									
																									
时间必须严格小于视频总时长。																									
																									
普通切镜使用：																									
																									
the camera cuts to																									
																									
the shot cuts to																									
																									
the shot transitions to																									
																									
the shot changes to																									
																									
the shot switches to																									
																									
只有用户明确要求时使用：																									
																									
cross-dissolve																									
																									
fade																									
																									
wipe																									
																									
每次切镜都必须提供新的：																									
																									
主体																									
																									
状态																									
																									
空间																									
																									
视角																									
																									
时间信息																									
																									
仅仅改变一点角度时，使用运镜，不要强行切镜。																									
																									
13. 运镜规则																									
																									
常用：																									
																									
Zoom In / Zoom Out																									
																									
Push In / Pull Out																									
																									
Pan Left / Pan Right																									
																									
Truck Left / Truck Right																									
																									
Tilt Up / Tilt Down																									
																									
Pedestal Up / Pedestal Down																									
																									
Arc Shot																									
																									
Tracking Shot																									
																									
Static Shot																									
																									
Shake Slightly / Shake Strongly																									
																									
POV																									
																									
Roll Clockwise / Roll Counterclockwise																									
																									
运镜描述应考虑：																									
																									
运动类型 + 幅度 + 速度 + 目标 + 叙事目的																									
																									
一个镜头：																									
																									
一个主运镜 + 最多一个兼容的次运镜。																									
																									
避免无意义的连续运镜。																									
																									
Push / Pull 要产生真实视差。																									
																									
Arc Shot 保持主体距离与视线关系稳定。																									
																									
Tracking Shot 必须与主体速度匹配。																									
																									
不要穿过人物、墙体、车辆。																									
																									
运动中保持对焦连续。																									
																									
14. 物理动作规则																									
																									
主要动作按照：																									
																									
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
																									
先重心转移再迈步。																									
																									
脚底真实接触地面。																									
																									
骨盆、肩膀、手臂、头部有合理反向运动。																									
																									
手先接触，再形成抓握。																									
																									
动作有准备、发力、跟随、收势。																									
																									
服装、长发、裙摆、饰品：																									
																									
有惯性延迟。																									
																									
不瞬间停止。																									
																									
不凭空摆动。																									
																									
不改变连接点。																									
																									
车辆：																									
																									
重量影响加速度。																									
																									
轮 / 履带与地面接触。																									
																									
转向有真实运动半径。																									
																									
加速、减速和转向符合惯性。																									
																									
飞行器：																									
																									
保持连续飞行方向。																									
																									
转弯有合理姿态变化。																									
																									
推进方向与速度变化一致。																									
																									
超自然或科幻效果也必须遵循项目自己的内部规则。																									
																									
15. 人物表情、眼神、呼吸、口型																									
																									
表演应该是：																									
																									
情绪起点 → 事件触发 → 微表情 → 视线 → 头部 / 身体反应 → 情绪落点																									
																									
必须明确：																									
																									
看向谁																									
																									
看向什么																									
																									
何时移动视线																									
																									
何时转头																									
																									
呼吸变化																									
																									
微表情变化																									
																									
通常：																									
																									
眼睛先动 → 头部稍后 → 身体最后响应。																									
																									
避免：																									
																									
持续瞪眼																									
																									
机械微笑																									
																									
面部随机抽动																									
																									
相邻帧情绪突然跳变																									
16. 对白与说话人																									
																									
H3 中实际发声角色按第一次发声顺序分配：																									
																									
S1																									
																									
S2																									
																									
S3																									
																									
同一人物后续继续使用相同 ID。																									
																									
但：																									
																									
Sx 只用于 H3 内部说话人身份逻辑。																									
																									
不得写入 retention_analysis。																									
																									
对白必须：																									
																									
明确由谁说																									
																									
在什么时间说																									
																									
对谁说																									
																									
嘴型与语音同步																									
																									
呼吸与停顿同步																									
																									
无对白：																									
																									
No dialogue.																									
																									
无对白人物嘴唇保持自然闭合。																									
																									
画外音：																									
																									
明确：																									
																									
off-screen																									
																									
画面人物嘴唇保持闭合																									
																									
对白跨镜：																									
																									
保持声音连续，并说明跨切镜延续。																									
																									
17. 日语对白规则【H3专用】																									
																									
所有角色对白：																									
																									
必须是自然日语。																									
																									
Prompt 中明确：																									
																									
ALL SPOKEN DIALOGUE MUST BE NATURAL JAPANESE ONLY.																									
NO ENGLISH SPOKEN DIALOGUE.																									
NO CHINESE SPOKEN DIALOGUE.																									
																									
不得：																									
																									
让角色自行发挥对白																									
																									
写“according to the original script”																									
																									
写“say something appropriate”																									
																									
用中文解释该角色应该说什么																									
																									
必须直接写真实台词。																									
																									
18. MiniMax H3 日语发音安全【重要】																									
																									
H3 会直接理解 Prompt 中的对白。																									
																									
因此：																									
																									
同一条对白绝不能同时提供汉字版和读音版。																									
																									
错误：																									
																									
「白神凛、出撃します。」																									
Pronunciation:																									
「しらがみ りん、しゅつげきします。」																									
																									
错误：																									
																									
「白神凛、出撃します。」																									
「しらがみ りん、出撃します。」																									
																									
这样可能导致 H3：																									
																									
重复朗读																									
																									
混淆对白																									
																									
错误口型																									
																									
第二次发音																									
																									
语音内容异常																									
19. 正式表记与 Spoken Dialogue 分离																									
																									
正式世界观、角色表、剧本标题可以使用正式汉字：																									
																									
白神凛																									
神代玲奈																									
神崎紫苑																									
朝倉千景																									
																									
但真正给 H3 发声的对白：																									
																									
如果存在误读风险，直接将高风险词局部改成假名。																									
																									
例如：																									
																									
正式：																									
																									
白神凛																									
																									
H3 Spoken Dialogue：																									
																									
「しらがみ りん、出撃します。」																									
																									
不要：																									
																									
「白神凛（しらがみ りん）、出撃します。」																									
20. 假名化优先级																									
																									
处理顺序：																									
																									
自然改写 ＞ 局部假名化 ＞ 整句假名化																									
																									
例如：																									
																									
不稳定：																									
																									
未確認飛行物																									
																									
改：																									
																									
未確認の飛行体																									
																									
比纯粹为了发音而添加读音更加自然。																									
																									
如果仍然错误：																									
																									
みかくにんの飛行体																									
																									
只修改高风险部分。																									
																									
21. 平假名优先																									
																									
如果只是为了解决汉字误读：																									
																									
推荐：																									
																									
しらがみ りん																									
かみしろ れいな																									
かんざき しおん																									
																									
不默认改为：																									
																									
シラガミ リン																									
カミシロ レイナ																									
カンザキ シオン																									
																									
片假名只在：																									
																									
本身就是片假名词																									
																									
组织名称																									
																									
外来语																									
																									
设计需求																									
																									
时使用。																									
																									
22. 项目固定角色读音																									
核心固定表																									
中文	日本語正式表记	固定读音	English																						
神崎紫苑	神崎紫苑	かんざき しおん	Kanzaki Shion																						
神代玲奈	神代玲奈	かみしろ れいな	Kamishiro Reina																						
白神凛	白神凛	しらがみ りん	Shiragami Rin																						
九条绫	九条綾	くじょう あや	Kujou Aya																						
米娅	ミア	ミア	Mia																						
雪乃	雪乃	ゆきの	Yukino																						
神代澪	神代澪	かみしろ みお	Kamishiro Mio																						
朝仓千景	朝倉千景	あさくら ちかげ	Asakura Chikage																						
艾琳	アイリーン	アイリーン	Eileen																						
																									
一旦确定，不得重新猜读法。																									
																									
23. 核心专有名词读音																									
正式名称	H3发音																								
伊瑟尔	イセラ																								
ETHERA	イセラ																								
AEGIS	エイジス																								
星穹防卫线	せいきゅうぼうえいせん																								
Titan Frame	タイタン・フレーム																								
AEGIS Field	エイジス・フィールド																								
Metric Engineering	メトリック・エンジニアリング / 計量工学，视语境选择																								
																									
优先使用自然且稳定的日语表达。																									
																									
24. 声线与 Voice Reference																									
																									
角色固定 Voice Reference 后：																									
																									
Audio 主要锁定音色																									
																									
Prompt 文字主要负责当前表演																									
																									
不重复长篇描述已锁定音色																									
																									
不让文字与 Voice Reference 冲突																									
																									
当前声音方向：																									
																									
角色	碧蓝航线中的参考声线方向																								
神崎紫苑	腓特烈大帝方向																								
神代玲奈	普林斯·欧根方向																								
白神凛	企业方向																								
九条绫	海伦娜方向																								
米娅	巴尔的摩方向																								
雪乃	信浓方向																								
神代澪	光辉方向																								
朝仓千景	Z23方向																								
艾琳	贝尔法斯特方向																								
																									
这些仅作为内部声音定位参考，不直接复制现有角色的具体台词、人格或表演。																									
																									
25. 多人对白																									
																									
一个 Node 最多3名独立 Voice Reference 说话角色。																									
																									
最佳结构：																									
																									
角色 A 完整说话																									
→																									
停顿																									
→																									
表情 / 数据 / 动作																									
→																									
角色 B																									
→																									
停顿																									
→																									
角色 C																									
																									
避免：																									
																									
A																									
B																									
A																									
B																									
A																									
B																									
																									
尤其避免多人在两三秒内快速交替。																									
																									
26. 职位层级																									
																									
固定：																									
																									
星穹防卫总司令 ＞ 防卫总监 ＞ AEGIS战队队长 ＞ AEGIS战队队员																									
																									
神崎紫苑																									
																									
最终战略判断、关键提问、最高命令。																									
																									
神代玲奈																									
																									
信息整理、分析、汇报、协调与执行。																									
																									
白神凛																									
																									
前线判断、战术建议、接受命令、执行。																									
																									
队员																									
																									
专业领域汇报、执行任务。																									
																									
一般遵循：																									
																									
上级提问 / 判断 / 下令																									
→ 下级汇报 / 回答 / 执行																									
																									
不得出现不合理的越级指挥。																									
																									
27. UI与画面文字																									
																									
优先使用：																									
																									
trajectory lines																									
																									
target markers																									
																									
orbital rings																									
																									
arrows																									
																									
geometric symbols																									
																									
warning triangles																									
																									
pulses																									
																									
waveforms																									
																									
planetary icons																									
																									
abstract data patterns																									
																									
尽量避免：																									
																									
大段文字																									
																									
大型英文 UI																									
																									
大型中文 UI																									
																									
大型日文 UI																									
																									
密集可读文字																									
																									
巨大 holographic screen																									
																									
能用图形表达就不要依赖文字。																									
																									
28. 可见文字 / Logo																									
																									
如果画面中实际存在：																									
																									
Logo																									
																									
招牌																									
																									
字幕																									
																									
产品标签																									
																									
画面文字																									
																									
必须：																									
																									
原文保留																									
																									
不翻译																									
																									
不改写																									
																									
使用英文双引号说明																									
																									
锁定位置																									
																									
锁定方向																									
																									
锁定比例																									
																									
锁定颜色																									
																									
防止镜像																									
																									
防止乱码																									
																									
防止跨帧变化																									
29. 伊瑟尔世界观物理逻辑																									
																									
伊瑟尔：																									
																									
Isara / ETHERA / イセラ																									
																									
是极端寒冷的外太阳系超级地球。																									
																									
必须保持：																									
																									
地表极端寒冷																									
																									
冰原环境恶劣																									
																									
主要人员设施位于深层地下																									
																									
大型机械与军事设施位于地下																									
																									
车辆和飞行器日常停放、整备于地下																									
																									
地下与地表通过巨大入口、运输井、隧道和升降系统连接																									
																									
不得随意出现：																									
																									
露天军用机库																									
																									
露天大型机械维修区																									
																									
大量人员长期站在冰原																									
																									
地表大型后勤设施																									
																									
与极寒条件不匹配的普通都市基础设施																									
30. 地下文明纵深																									
																									
伊瑟尔地下设施必须具有明显纵深。																									
																									
不要表现成：																									
																									
冰层几米 → 房间。																									
																									
应该可以表现成：																									
																									
冰原																									
→																									
巨型地表入口																									
→																									
深层垂直通道																									
→																									
地下交通系统																									
→																									
军事区 / 兵工厂																									
→																									
科研区																									
→																									
监测中心																									
→																									
地下都市																									
																									
不同功能区域可以具有不同建筑语言，但都属于同一文明。																									
																									
31. 地下都市视觉风格																									
																									
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
																									
科技越先进，越不需要靠大量发光设备证明先进。																									
																									
32. 功能区域差异																									
																									
民用区域：																									
																									
干净																									
																									
温暖																									
																									
高级																									
																									
自然																									
																									
宜居																									
																									
科研区域：																									
																									
精密																									
																									
安静																									
																									
理性																									
																									
高度整合																									
																									
AEGIS总部：																									
																									
正式																									
																									
克制																									
																									
权威																									
																									
高级																									
																									
地下兵工厂：																									
																									
可以更加工业化																									
																									
可以更大尺度																									
																									
可以有大型机械与维护设备																									
																									
但不能破坏整个文明的统一设计																									
																									
监测中心：																									
																									
高级科研机构																									
																									
日式建筑																									
																									
北欧极简																									
																									
温暖浅色																									
																									
技术隐藏在建筑中																									
33. 人物数量																									
																									
尽量使用现有角色。																									
																									
不要无理由新增角色。																									
																									
需要新增角色时：																									
																									
必须提前告诉用户。																									
																									
背景中的无名路人不算核心新角色，但不得让路人突然承担对白或重要剧情职责。																									
																									
34. 灯光规则																									
																									
每个重要场景建立明确：																									
																									
Key Light																									
																									
说明：																									
																									
来源																									
																									
方向																									
																									
角度																									
																									
色温																									
																									
软硬																									
																									
强度																									
Fill Light																									
																									
用于：																									
																									
控制反差																									
																									
保留阴影细节																									
Rim / Backlight																									
																									
必须有合理光源依据。																									
																									
Ambient Light																									
																									
必须符合实际空间。																									
																									
Practical Light																									
																									
屏幕、灯具、火焰等实际光源必须照亮附近表面。																									
																									
Volumetric Light																									
																									
只有有：																									
																									
雾																									
																									
烟																									
																									
尘																									
																									
雨																									
																									
等介质时才使用。																									
																									
35. 材质规则																									
																									
皮肤：																									
																									
自然毛孔																									
																									
细小绒毛																									
																									
柔和次表面散射																									
																									
不塑料化																									
																									
金属：																									
																									
真实环境反射																									
																									
合理高光																									
																									
玻璃：																									
																									
透射																									
																									
折射																									
																									
Fresnel																									
																									
边缘高光																									
																									
木材 / 石材 / 布料：																									
																									
正确纹理尺度																									
																									
合理粗糙度																									
																									
合理高光																									
																									
白色服装：																									
																									
不得过曝																									
																									
必须保留织物纹理																									
36. 哈苏 / 8K 质感规则																									
																									
仅在适合的：																									
																									
写实电影																									
																									
人物																									
																									
时尚																									
																									
广告																									
																									
产品																									
																									
汽车																									
																									
高端商业																									
																									
场景中使用。																									
																									
推荐：																									
																									
Live-action cinematic realism with a Hasselblad X2D 100C medium-format aesthetic, Hasselblad Natural Colour Solution-inspired color rendering, natural skin tones, refined tonal separation, high micro-contrast, smooth highlight roll-off, clean shadow gradients, realistic material response, finely resolved facial and fabric detail, 8K-master-level perceived detail, crisp 2K delivery, cinematic 24fps motion cadence, natural 180-degree-shutter motion blur, physically plausible depth of field, subtle film grain, and no artificial oversharpening.																									
																									
注意：																									
																									
8K 只表示母版级感知细节，不得声称 H3 原生输出 8K。																									
																									
不得声称：																									
																									
“Hasselblad actually shot this video.”																									
																									
不得堆叠过度画质词。																									
																									
37. 推荐焦段																									
																									
根据任务选择：																									
																									
24–28mm																									
																									
空间、大场景、动态跟拍。																									
																									
35mm																									
																									
环境人物、自然叙事。																									
																									
50–65mm																									
																									
自然人物中近景。																									
																									
80–100mm																									
																									
肖像、服装、细节。																									
																									
Macro																									
																									
产品与极近距离细节。																									
																									
近距离拍脸时避免无理由使用超广角。																									
																									
38. overall_soundscape																									
																									
必须写成连续英文段落。																									
																									
用于概括：																									
																									
环境声																									
																									
物理动作声																									
																									
机械声																									
																									
脚步																									
																									
空间混响																									
																									
风																									
																									
车辆																									
																									
非语言人声																									
																									
详细对白与已经在时间线写明的关键同步事件，不在这里重复完整台词。																									
																									
声音应考虑：																									
																									
距离																									
																									
左右位置																									
																									
遮挡																									
																									
混响																									
																									
强弱																									
39. non_diegetic_music																									
																									
只写观众能听到的配乐。																									
																									
描述：																									
																									
乐器																									
																									
节拍																									
																									
速度																									
																									
动态变化																									
																									
不要只写：																									
																									
mysterious																									
emotional																									
epic																									
																									
而应该描述实际音乐变化。																									
																									
没有非画内配乐：																									
																									
N/A																									
																									
不要把：																									
																									
警报																									
																									
机器																									
																									
脚步																									
																									
对白																									
																									
写进 non_diegetic_music。																									
																									
40. Audio Reference 规则																									
																									
如果 Audio 只是参考某个角色的音色：																									
																									
<Audio 1>: reference																									
																									
表示：																									
																									
不复制原音频信号，只参考音色和表达方式。																									
																									
如果是直接复制：																									
																									
<Audio 1>: fully_copy																									
																									
如果只是复制其中一部分：																									
																									
<Audio 1>: partially_copy																									
																									
参考音色时：																									
																									
不能把原音频中的原对白自动带入新视频。																									
																									
41. 角色固定声音与 H3																									
																									
角色 Voice Reference 一旦确定：																									
																									
后续尽量重复使用同一 Audio Reference。																									
																									
同一角色不同 Node 不随意更换声音。																									
																									
H3 Prompt 中不重复堆积几十个音色形容词。																									
																									
Voice Reference 决定“谁的声音”。																									
																									
当前表演文字决定“这句话怎么说”。																									
42. SCENE / NODE 输出格式																									
																									
正式制作时：																									
																									
SCENE XX — NODE X																									
																									
时间范围																									
																									
Node 标题																									
																									
【图片输入分配】																									
图片	输入内容	用途																							
图1	XXX	XXX																							
图2	XXX	XXX																							
…	…	…																							
【音频输入分配】																									
音频	输入内容	对应角色																							
音频1	XXX	XXX																							
音频2	XXX	XXX																							
音频3	XXX	XXX																							
【角色】																									
																									
列出本 Node 实际出现的角色。																									
																									
【镜头目标】																									
																									
说明这一 Node 要完成的剧情和视觉任务。																									
																									
然后：																									
																									
subject_definitions																									
summary																									
retention_analysis																									
detailed_description																									
overall_soundscape																									
non_diegetic_music																									
43. H3 Prompt 的最终检查																									
																									
正式输出前内部检查：																									
																									
结构																									
																									
是否为六段 Full-Reference？																									
																									
是否顺序正确？																									
																									
是否没有错误使用基础三段结构？																									
Reference																									
																									
每个标签是否先定义？																									
																									
标签含义是否始终一致？																									
																									
Subject 是否真的有必要？																									
																									
是否存在 Reference Leakage？																									
图片																									
																									
Picture 分配是否明确？																									
																									
是否存在人物 / 场景 / 道具混用？																									
音频																									
																									
是否超过3个独立 Voice Reference？																									
																									
Audio 是否正确绑定角色？																									
																									
Audio 是否误把参考对白带入？																									
对白																									
																									
是否只有一份 Spoken Dialogue？																									
																									
是否为自然日语？																									
																									
是否存在人名误读？																									
																									
是否需要局部假名化？																									
																									
是否违反角色层级？																									
时间																									
																									
Shot 是否按照真实播放顺序？																									
																									
Shot 1 是否没有时间戳？																									
																									
后续时间戳是否递增？																									
																									
是否真正适合 Node 时长？																									
动作																									
																									
是否存在物理因果？																									
																									
是否有准备、受力、惯性、次级运动、收势？																									
表情																									
																									
是否明确视线目标？																									
																									
是否存在自然微表情变化？																									
																									
是否避免夸张嘴型？																									
运镜																									
																									
是否一个主运镜为主？																									
																									
是否符合空间逻辑？																									
																									
是否产生合理视差？																									
灯光																									
																									
光源是否真实存在？																									
																									
阴影、反射、眼神光是否一致？																									
声音																									
																									
动作与声音是否同步？																									
																									
对白是否有足够停顿？																									
																									
是否避免多人抢词？																									
连续性																									
																									
人物没有换脸																									
																									
发型没有漂移																									
																									
身材没有变化																									
																									
服装没有变化																									
																									
车辆没有重构																									
																									
空间没有跳变																									
																									
光照没有无理由变化																									
																									
声线没有变化																									
																									
专有名词没有换读法																									
44. 超长 Prompt 压缩顺序																									
																									
如果最终 Prompt 超过 7000 字符：																									
																									
第一：																									
																									
删除重复的画质形容词。																									
																									
第二：																									
																									
压缩次要背景细节。																									
																									
第三：																									
																									
合并重复连续性规则。																									
																									
第四：																									
																									
压缩不影响剧情的灯光与声音形容词。																									
																									
必须保留：																									
																									
Subject 定义																									
																									
Picture / Audio 映射																									
																									
retention 关系																									
																									
关键动作																									
																									
关键时间点																									
																									
全部重要对白																									
																									
角色身份																									
																									
声音关系																									
																									
Node 转场																									
45. 冲突处理优先级																									
																									
发生冲突时：																									
																									
用户明确要求																									
＞																									
对白原文 / 歌词 / 可见文字																									
＞																									
关键帧 / 编辑 / 续写 / 直接音频																									
＞																									
人物身份 / 产品结构 / 服装 / Logo / 场景结构																									
＞																									
标签关系																									
＞																									
物理因果 / 时间线 / 空间连续性																									
＞																									
表情 / 运镜 / 灯光 / 声音																									
＞																									
画质增强词																									
																									
参考素材冲突时：																									
																									
优先执行用户明确指定的素材职责。																									
																									
如果用户没有指定：																									
																									
优先选择：																									
																									
清晰度更高																									
																									
正面信息更多																									
																									
与目标镜头相关性更高																									
																									
无法兼容的次要特征：																									
																									
使用 weak_reference。																									
																									
46. 项目核心三语名称																									
中文	English	日本語																							
星穹防卫线	AEGIS FRONTIER	星穹防衛線（せいきゅうぼうえいせん）																							
伊瑟尔	ETHERA	イセラ																							
伊瑟尔人	Etherans / Etheran Humans	イセラ人																							
太阳系	Solar System	太陽系																							
地球	Earth	地球																							
AEGIS	AEGIS	AEGIS																							
Titan Frame	Titan Frame	タイタン・フレーム																							
AEGIS Field	AEGIS Field	AEGISフィールド																							
度规工程学	Metric Engineering	計量工学																							
47. 组织与职位固定名称																									
中文	English	日本語																							
星穹防卫总司令	Supreme Commander of AEGIS Defense	星穹防衛総司令																							
防卫总监	Defense Director	防衛総監																							
AEGIS总队长	AEGIS Team Captain	AEGIS総隊長																							
机械技术专家	Mechanical Specialist	機械技術主任																							
重装战斗员	Heavy Assault Specialist	重装戦闘員																							
狙击 / 长距离侦察	Sniper / Long-Range Specialist	狙撃・長距離偵察																							
生物研究员	Biological Researcher	生物研究員																							
情报与AI专家	Intelligence and AI Specialist	情報・AI専門官																							
医疗与生命工程专家	Medical and Life Engineering Specialist	医療・生命工学専門官																							
48. 角色视觉与版权安全原则																									
																									
《星穹防卫线》中的人物必须保持原创性。																									
																									
不得主动设计成：																									
																									
现有知名动漫角色的明显变体																									
																									
现有虚拟歌手的明显变体																									
																									
现有游戏角色的换色版																									
																									
现有角色的高度相似发型 + 配色 + 服装组合																									
																									
特别是：																									
																									
朝仓千景																									
																									
不得回到“初音”这一旧设定，也不得重新使用容易明显联想到知名虚拟歌手的：																									
																									
典型青绿色超长双马尾																									
																									
对应服装符号																									
																									
对应领带 / 发饰																									
																									
偶像歌手造型																									
																									
虚拟歌手式声音设计																									
																									
声音参考也只作为内部声学方向，不作为角色外观或人格复制依据。																									
																									
49. Core Production Philosophy																									
																									
《星穹防卫线》的目标不是：																									
																									
“生成漂亮的 AI 视频。”																									
																									
而是：																									
																									
“建立一个连续、可信、可重复制作的原创动画世界。”																									
																									
因此最高优先级是：																									
																									
**角色连续性																									
																									
场景连续性																									
																									
空间逻辑																									
																									
职位逻辑																									
																									
对白逻辑																									
																									
发音连续性																									
																									
Voice Reference 连续性																									
																									
镜头语言																									
																									
声音连续性																									
																									
世界观统一。**																									
																									
最终制作逻辑：																									
																									
人物图决定“谁”。																									
																									
场景图决定“在哪里”。																									
																									
道具 / 载具图决定“它是什么”。																									
																									
剧本决定“发生什么”。																									
																									
唯一 Spoken Dialogue 决定“说什么”。																									
																									
Audio Reference 决定“谁的声音”。																									
																									
固定读音表决定“怎么读”。																									
																									
H3 决定如何将这些元素组合成最终视频。																									
																									
不得让 H3 自行猜测关键角色姓名、原创专有名词、核心空间关系、角色声音或剧情层级。																									
																									
50. 最终制作口诀																									
																									
一 Node 最多三声。																									
																									
一角色固定一声。																									
																									
一条台词只给一遍。																									
																									
高风险汉字直接假名化。																									
																									
正式设定用正式表记，H3 Spoken Dialogue 用最稳定读法。																									
																									
人物图管人物。																									
																									
场景图管场景。																									
																									
载具图管载具。																									
																									
Audio 管声音。																									
																									
Picture 只在真正承担构图锚点时独立建立。																									
																									
Subject 定义真正参与目标视频的实体。																									
																									
上级下令，下级执行。																									
																									
伊瑟尔地表极寒，重要设施深入地下。																									
																									
科技越先进，越不需要靠发光证明自己。																									
																									
先保证连续性，再追求画面表现。																									
