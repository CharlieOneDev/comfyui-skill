《星穹防卫线》MiniMax H3 视频制作 Skill																									
项目最终版																									
																									
用于原创科幻动画《星穹防卫线 / AEGIS FRONTIER》的分镜设计、15秒 Node 拆分、MiniMax H3 Full-Reference 视频 Prompt 编写、角色固定 Voice Reference 管理、日语对白、镜头、声音及世界观连续性控制。																									
																									
0. 规则层级																									
																									
本项目同时遵循两套规则：																									
																									
A. MiniMax H3 通用 Prompt 规则																									
																									
来源：																									
																									
https://github.com/CharlieOneDev/comfyui-skill/blob/main/多模态优化提示词元指令_通用版.md																									
																									
每次正式编写 H3 Prompt 时，优先读取该文档的最新版本。																									
																									
B. 《星穹防卫线》项目规则																									
																									
本 Skill 负责补充：																									
																									
世界观																									
																									
角色																									
																									
角色姓名与固定读音																									
																									
9名核心女性角色 Voice Reference																									
																									
Audio 输入限制																									
																									
图片输入逻辑																									
																									
空间逻辑																									
																									
职位体系																									
																									
对白逻辑																									
																									
连续性																									
																									
两者必须同时遵守。																									
																									
1. 生产单位																									
																									
默认 1 Node = 15秒 H3 生成单元。																									
																									
每个 Node 可包含 1–3 个 Shot。																									
																									
优先在 Node 边界形成自然硬切。																									
																									
不为了凑满15秒而拖长镜头。																									
																									
场景自然结束于9秒、10秒、12秒等时，应直接结束。																									
																									
只有连续镜头真正超过15秒时，才标记：																									
⚠️【长镜头警告】																									
2. H3 图片输入																									
																									
H3 Full-Reference 最多使用8个图片输入。																									
																									
Picture 编号没有固定含义。																									
																									
每个 Node 必须重新分配：																									
																									
Picture 1																									
																									
Picture 2																									
																									
Picture 3																									
																									
…																									
																									
下一个 Node 可以完全重新排列。																									
																									
因此正式 Prompt 前必须提供：																									
																									
【图片输入分配】																									
图片	输入内容	用途																							
图1	XXX	XXX																							
图2	XXX	XXX																							
图3	XXX	XXX																							
图4	XXX	XXX																							
图5–8	不使用	—																							
																									
用户必须可以按照该表直接连接 ComfyUI H3 输入。																									
																									
3. H3 音频输入【重要】																									
																									
H3 最多只能接入：																									
																									
3个 Audio 输入。																									
																									
但必须正确理解：																									
																									
不是一个 Node 最多只能出现3个有声音的人。																									
																									
而是：																									
																									
一个 Node 最多只能接入3个独立 Audio Reference。																									
3.1 9名核心女性角色																									
																									
以下9名角色拥有长期固定的独立 Voice Reference：																									
																									
角色	English	日本語	是否使用固定 Audio																						
神崎紫苑	Kanzaki Shion	神崎紫苑	是																						
神代玲奈	Kamishiro Reina	神代玲奈	是																						
白神凛	Shiragami Rin	白神凛	是																						
九条绫	Kujou Aya	九条綾	是																						
米娅	Mia	ミア	是																						
雪乃	Yukino	雪乃	是																						
神代澪	Kamishiro Mio	神代澪	是																						
朝仓千景	Asakura Chikage	朝倉千景	是																						
艾琳	Eileen	アイリーン	是																						
																									
这些角色在需要说话时，应优先使用自己的固定 Voice Reference。																									
																									
3.2 其他人物默认不使用 Audio Reference																									
																									
以下角色默认不需要独立 Audio Reference：																									
																									
男主																									
																									
电视台纪录片式女性旁白																									
																									
普通 NPC																									
																									
医生																									
																									
研究人员																									
																									
监测员																									
																									
士兵																									
																									
路人																									
																									
背景人物																									
																									
临时出现角色																									
																									
这些角色即使需要对白：																									
																									
允许直接由 MiniMax H3 根据文字、场景和角色描述生成普通人声。																									
																									
不要为了他们额外占用 Audio 输入。																									
																									
3.3 男主声音																									
																									
男主没有固定 Voice Reference。																									
																									
默认：																									
																									
使用 MiniMax H3 的普通成年男性声音能力。																									
																									
根据剧情在 Prompt 中描述：																									
																									
年龄感																									
																									
情绪																									
																									
语速																									
																									
声压																									
																									
状态																									
																									
但不需要 Audio Reference。																									
																									
3.4 电视台纪录片旁白																									
																									
电视台纪录片式女性旁白默认不使用固定 Audio Reference。																									
																									
通过 Prompt 描述：																									
																									
professional Japanese television-documentary female narrator																									
mature adult female																									
magnetic medium-low register																									
extremely clear diction																									
calm professional delivery																									
moderate speaking speed																									
precise Japanese pronunciation																									
																									
由 H3 直接生成。																									
																									
除非用户以后明确制作并指定了固定旁白 Audio。																									
																									
4. 【音频输入分配】																									
																									
只要 Node 使用固定 Voice Reference，必须输出：																									
																									
【音频输入分配】																									
音频	输入内容	对应角色																							
音频1	神崎紫苑 Voice Reference	神崎紫苑																							
音频2	神代玲奈 Voice Reference	神代玲奈																							
音频3	白神凛 Voice Reference	白神凛																							
																									
如果一个 Node 中只有一个核心女性角色：																									
																									
音频	输入内容	对应角色																							
音频1	朝仓千景 Voice Reference	朝仓千景																							
音频2–3	不使用	—																							
																									
如果 Node 完全没有9名核心女性角色：																									
																									
音频	输入内容	对应角色																							
音频1–3	不使用	—																							
5. Audio 与角色的绑定																									
																									
如果角色有固定 Voice Reference：																									
																									
<Subject 1> is Shiragami Rin, whose appearance comes from <Picture 1>. Her voice reference is provided by <Audio 1>.																									
																									
在对白部分：																									
																									
<Picture 1>, Shiragami Rin, speaks using <Audio 1>.																									
																									
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
6. Subject / Picture / Video / Audio																									
Subject																									
																									
Subject 是真正参与目标视频的实体。																									
																									
可以是：																									
																									
人物																									
																									
车辆																									
																									
道具																									
																									
动物																									
																									
场景																									
																									
服装																									
																									
动作																									
																									
特效																									
																									
一个 Subject 可以由多个素材共同定义。																									
																									
Picture																									
																									
Picture 用于：																									
																									
视觉 Reference																									
																									
首帧																									
																									
关键帧																									
																									
尾帧																									
																									
构图锚点																									
																									
如果只是作为人物/场景/载具 Reference 来源，不要为了形式重复定义。																									
																									
Video																									
																									
Video 用于：																									
																									
视频续写																									
																									
动作参考																									
																									
时间结构																									
																									
镜头运动																									
																									
剪辑节奏																									
Audio																									
																									
Audio 用于：																									
																									
固定角色 Voice Reference																									
																									
音色参考																									
																									
实际声音复制																									
																									
音乐																									
																									
音效																									
																									
其他需要明确声音参考的内容																									
7. Reference 使用原则																									
人物图负责																									
																									
facial identity																									
																									
facial proportions																									
																									
hairstyle																									
																									
hair color																									
																									
eyes																									
																									
body proportions																									
																									
costume																									
																									
accessories																									
																									
character identity																									
场景图负责																									
																									
architecture																									
																									
spatial proportions																									
																									
layout																									
																									
materials																									
																									
lighting																									
																									
environment																									
																									
spatial continuity																									
载具 / 道具 / 装置图负责																									
																									
structure																									
																									
shape																									
																									
proportions																									
																									
materials																									
																									
mechanical design																									
																									
visual behavior																									
																									
必须避免 Reference Leakage。																									
																									
8. 人物引用																									
																									
采用简洁写法：																									
																									
<Subject 1> is Asakura Chikage, whose appearance comes from <Picture 1>.																									
																									
如果有固定 Audio：																									
																									
<Subject 1> is Asakura Chikage, whose appearance comes from <Picture 1>. Her voice reference is provided by <Audio 1>.																									
																									
避免大量重复：																									
																									
<Picture 1> controls only...																									
Whenever...																									
<Picture 1> is the sole...																									
																									
人物出现时必须明确对应：																									
																									
Cut to <Picture 1>, Asakura Chikage.																									
																									
不要只写：																									
																									
Cut to Chikage.																									
9. 六段 Prompt 结构																									
																									
正式 H3 Prompt 必须严格使用：																									
																									
subject_definitions																									
summary																									
retention_analysis																									
detailed_description																									
overall_soundscape																									
non_diegetic_music																									
																									
顺序不得改变。																									
																									
10. subject_definitions																									
																									
简洁说明：																									
																									
Subject																									
																									
Picture																									
																									
Video																									
																									
Audio																									
																									
以及它们之间的关系。																									
																									
只定义真正使用的素材。																									
																									
不要定义后文没有使用的标签。																									
																									
11. summary																									
																									
必须明确任务类型，例如：																									
																									
[reference generation]																									
																									
或：																									
																									
[reference generation + audio reference]																									
																									
或：																									
																									
[video continuation]																									
																									
summary 负责：																									
																									
剧情目的																									
																									
视觉目的																									
																									
主要 Subject																									
																									
情绪																									
																									
空间关系																									
																									
Reference 用途																									
12. retention_analysis																									
																									
用于保证：																									
																									
人物连续																									
																									
场景连续																									
																									
载具连续																									
																									
道具连续																									
																									
声音连续																									
																									
Voice Reference 连续																									
																									
Reference 不泄漏																									
																									
只能使用官方允许的关系：																									
																									
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
																									
不得使用 (S1)、(S2) 等说话人 ID。																									
																									
13. detailed_description																									
																									
必须按照实际播放顺序设计。																									
																									
开头简要定义：																									
																									
视觉风格																									
																									
摄影风格																									
																									
光线																									
																									
色彩																									
																									
整体氛围																									
																									
随后按照：																									
																									
[Shot 1]																									
[Shot 2] At 00:03.000, ...																									
[Shot 3] At 00:08.000, ...																									
																									
描述。																									
																									
14. Shot 时间规则																									
																									
Shot 1 不写时间戳。																									
																									
Shot 2 开始写时间戳。																									
																									
所有时间必须递增。																									
																									
所有时间必须小于 Node 总时长。																									
																									
使用自然切镜：																									
																									
the camera cuts to																									
																									
the shot cuts to																									
																									
the shot transitions to																									
																									
the shot switches to																									
																									
尽量避免无必要的：																									
																									
cross-dissolve																									
																									
fade																									
																									
wipe																									
15. 对白规则																									
																									
每句对白必须明确：																									
																									
说话角色																									
																									
Picture																									
																									
Audio（如果使用固定 Voice Reference）																									
																									
时间																									
																									
表情																									
																									
语气																									
																									
嘴型																									
																									
停顿																									
																									
例如：																									
																									
<Picture 1>, Shiragami Rin, speaks using <Audio 1>:																									
「しらがみ りん、行きます。」																									
Her delivery is calm and decisive, with natural restrained mouth movement.																									
16. 日语对白规则																									
																									
所有人物对白：																									
																									
ALL SPOKEN DIALOGUE MUST BE NATURAL JAPANESE ONLY.																									
NO ENGLISH SPOKEN DIALOGUE.																									
NO CHINESE SPOKEN DIALOGUE.																									
																									
必须直接写真实日语台词。																									
																									
不得：																									
																									
according to the original script																									
																									
she says something appropriate																									
																									
the character speaks naturally																									
																									
没有对白：																									
																									
No dialogue.																									
17. 日语发音安全【核心规则】																									
																									
MiniMax H3 会直接根据 Prompt 理解并生成对白语音。																									
																									
因此：																									
																									
一条 Spoken Dialogue 只能出现一次。																									
																									
禁止：																									
																									
「白神凛、出撃します。」																									
Pronunciation:																									
「しらがみ りん、しゅつげきします。」																									
																									
禁止：																									
																									
「白神凛、出撃します。」																									
「しらがみ りん、出撃します。」																									
																									
这样可能导致 H3：																									
																									
重复朗读																									
																									
错误理解																									
																									
口型错位																									
																									
第二次朗读																									
18. 正式表记与 Spoken Dialogue 分离																									
																									
世界观、角色表、正式字幕：																									
																									
可以写：																									
																									
白神凛																									
神代玲奈																									
神崎紫苑																									
朝倉千景																									
																									
真正由 H3 发声的对白：																									
																									
遇到高风险读音时，直接局部假名化。																									
																									
例如：																									
																									
「しらがみ りん、出撃します。」																									
																									
而不是：																									
																									
「白神凛（しらがみ りん）、出撃します。」																									
19. 假名化规则																									
																									
处理顺序：																									
																									
自然改写 ＞ 局部假名化 ＞ 整句假名化																									
																									
例如：																									
																									
未確認飛行物																									
																									
如果不稳定：																									
																									
未確認の飛行体																									
																									
如果仍然误读：																									
																									
みかくにんの飛行体																									
																									
只修改高风险部分。																									
																									
默认使用平假名。																									
																									
不要无意义地把正常日语变成全片假名。																									
																									
20. 固定角色日语读音																									
中文	日本語正式表记	固定读音																							
神崎紫苑	神崎紫苑	かんざき しおん																							
神代玲奈	神代玲奈	かみしろ れいな																							
白神凛	白神凛	しらがみ りん																							
九条绫	九条綾	くじょう あや																							
米娅	ミア	ミア																							
雪乃	雪乃	ゆきの																							
神代澪	神代澪	かみしろ みお																							
朝仓千景	朝倉千景	あさくら ちかげ																							
艾琳	アイリーン	アイリーン																							
21. 核心专有名词读音																									
正式表记	H3 Spoken Dialogue																								
伊瑟尔	イセラ																								
ETHERA	イセラ																								
AEGIS	エイジス																								
星穹防卫线	せいきゅうぼうえいせん																								
Titan Frame	タイタン・フレーム																								
AEGIS Field	エイジス・フィールド																								
度规工程学	計量工学																								
																									
如果实测 H3 在某个新专有名词上误读：																									
																									
优先采用自然改写或局部假名化，并将新读法加入项目固定表。																									
																									
22. 多人对白																									
																									
一个 Node 最多3名固定 Voice Reference 角色。																									
																									
但可以存在超过3个普通声音角色，只要他们不需要独立 Audio Reference。																									
																									
多人对白优先：																									
																									
A完整说完																									
→																									
停顿																									
→																									
B																									
→																									
动作 / 反应																									
→																									
C																									
																									
避免：																									
																									
A																									
B																									
A																									
B																									
A																									
B																									
23. 职位层级																									
																									
固定：																									
																									
星穹防卫总司令 ＞ 防卫总监 ＞ AEGIS战队队长 ＞ 战队队员																									
																									
神崎紫苑																									
																									
最终战略判断、关键提问、最高级命令。																									
																									
神代玲奈																									
																									
情报整理、分析、汇报、执行协调。																									
																									
白神凛																									
																									
前线判断、战术建议、接受命令、执行。																									
																									
其他队员																									
																									
专业报告、执行任务。																									
																									
基本模式：																									
																									
上级提问 / 判断 / 下令 → 下级汇报 / 回答 / 执行。																									
																									
24. 人物表演																									
																									
保持自然成人表演。																									
																									
对白镜头：																									
																									
natural mouth movement																									
																									
restrained mouth opening																									
																									
realistic facial motion																									
																									
no exaggerated mouth opening																									
																									
no excessive anime shouting																									
																									
通过：																									
																									
语速																									
																									
停顿																									
																									
音量																									
																									
眼神																									
																									
微表情																									
																									
姿态																									
																									
表现情绪。																									
																									
25. UI 与屏幕文字																									
																									
能用图形表达，就尽量不用文字。																									
																									
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
																									
大段文字																									
																									
大型英文 UI																									
																									
大型中文 UI																									
																									
大型日文 UI																									
																									
密集可读文字																									
																									
巨型 holographic screens																									
26. 世界观与空间逻辑																									
																									
伊瑟尔：																									
																									
Isara / ETHERA / イセラ																									
																									
必须保持：																									
																									
外太阳系极寒环境																									
																									
地表是冰原																									
																									
主要文明位于深层地下																									
																									
大型人员设施位于地下																									
																									
大型机械设施位于地下																									
																									
车辆日常停放、维修位于地下																									
																									
地下与地表有巨型入口、运输井、隧道和升降系统																									
																									
避免：																									
																									
露天大型军用机库																									
																									
露天大型维修厂																									
																									
大量人员长期暴露在冰原																									
																									
地表常规城市基础设施																									
27. 地下文明纵深																									
																									
地下设施不能表现成：																									
																									
冰层几米 → 一个房间。																									
																									
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
																									
不同区域可以有不同功能性建筑语言，但必须属于同一文明体系。																									
																									
28. 地下设施视觉风格																									
																									
总体：																									
																									
advanced civilization																									
																									
refined Japanese architecture																									
																									
Scandinavian minimalism																									
																									
luxury research institution																									
																									
civic architecture																									
																									
understated technology																									
																									
主材：																									
																									
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
																									
军事兵工厂等功能区可以更加工业化，但仍属于同一文明体系。																									
																									
29. 角色版权与原创性																									
																									
所有核心角色保持原创视觉身份。																									
																									
不得主动设计成：																									
																									
现有动漫角色换色版																									
																									
现有游戏角色换装版																									
																									
知名虚拟歌手明显变体																									
																									
现有角色高度相似发型＋服装＋配色																									
																									
尤其：																									
																									
朝仓千景																									
																									
不得重新使用与“初音”相关的旧名称或明显视觉符号。																									
																									
包括：																									
																									
标志性青绿色超长双马尾																									
																									
类似虚拟歌手服装																									
																									
对应领带																									
																									
对应发饰																									
																									
偶像歌手视觉体系																									
																									
虚拟歌手式声音																									
30. 角色数量																									
																									
尽量使用已有角色。																									
																									
不要无理由新增核心角色。																									
																									
如果需要新增具有剧情作用的新角色：																									
																									
必须提前告诉用户。																									
																									
背景路人可以存在，但不得突然拥有核心对白或重要剧情职责。																									
																									
31. 镜头语言																									
																									
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
																									
信息揭示																									
																									
情绪推进																									
																									
人物关系																									
																									
空间建立																									
																									
动作连续性																									
																									
优先一个主运镜。																									
																									
32. 灯光规则																									
																									
重要场景明确：																									
																									
Key Light																									
																									
来源																									
																									
方向																									
																									
色温																									
																									
强度																									
																									
软硬																									
Fill Light																									
																									
控制反差。																									
																									
Rim / Backlight																									
																									
必须有合理光源。																									
																									
Ambient Light																									
																									
符合空间环境。																									
																									
Practical Light																									
																									
真实照亮周围材质。																									
																									
Volumetric Light																									
																									
必须有雾、烟、尘等介质支持。																									
																									
33. 材质规则																									
																									
皮肤：																									
																									
natural pores																									
																									
fine facial hair																									
																									
subtle subsurface scattering																									
																									
金属：																									
																									
realistic environment reflection																									
																									
physically plausible highlights																									
																									
玻璃：																									
																									
transmission																									
																									
refraction																									
																									
Fresnel																									
																									
edge highlights																									
																									
白色服装：																									
																									
保留织物纹理																									
																									
避免过曝																									
34. 摄影与画质																									
																									
适合时使用：																									
																									
Live-action cinematic realism with a Hasselblad X2D 100C medium-format aesthetic, natural tonal separation, realistic skin tones, high micro-contrast, smooth highlight roll-off, clean shadow gradients, realistic material response, finely resolved facial and fabric detail, 8K-master-level perceived detail, crisp 2K delivery, cinematic 24fps motion cadence, natural 180-degree-shutter motion blur, physically plausible depth of field, subtle film grain, and no artificial oversharpening.																									
																									
注意：																									
																									
8K仅代表母版级感知细节。																									
																									
不声称 H3 原生8K。																									
																									
不声称真的由 Hasselblad 拍摄。																									
35. 焦段建议																									
																									
24–28mm：																									
																									
大空间、城市、动作。																									
																									
35mm：																									
																									
环境人物。																									
																									
50–65mm：																									
																									
人物中近景。																									
																									
80–100mm：																									
																									
肖像和细节。																									
																									
近距离拍脸避免无理由使用超广角。																									
																									
36. overall_soundscape																									
																									
描述：																									
																									
环境																									
																									
机械																									
																									
脚步																									
																									
风																									
																									
车辆																									
																									
空间混响																									
																									
非语言人声																									
																									
必须与画面动作、距离和空间一致。																									
																									
不要在这里重复完整对白。																									
																									
37. non_diegetic_music																									
																									
只写：																									
																									
观众听到的配乐。																									
																									
包括：																									
																									
乐器																									
																									
节拍																									
																									
速度																									
																									
动态																									
																									
情绪推进																									
																									
不要把：																									
																									
警报																									
																									
脚步																									
																									
机器																									
																									
对白																									
																									
写进这里。																									
																									
没有配乐：																									
																									
N/A																									
38. 连续性优先级																									
																									
所有 Node：																									
																									
人物连续性																									
＞ 场景连续性																									
＞ 道具 / 载具连续性																									
＞ 空间逻辑																									
＞ 对白逻辑																									
＞ 发音连续性																									
＞ Voice Reference 连续性																									
＞ 镜头语言																									
＞ 特效																									
																									
尤其：																									
																									
同一角色姓名读音必须一致。																									
																									
同一角色 Voice Reference 必须一致。																									
																									
同一专有名词读音必须一致。																									
																									
同一载具结构必须一致。																									
																									
同一地点空间关系必须一致。																									
																									
每个 Node 重新定义 Picture 和 Audio 分配。																									
																									
39. 输出格式																									
																									
正式制作时：																									
																									
SCENE XX — NODE X																									
																									
时间范围																									
																									
Node 标题																									
																									
【图片输入分配】																									
图片	输入内容	用途																							
图1	XXX	XXX																							
图2	XXX	XXX																							
【音频输入分配】																									
音频	输入内容	对应角色																							
音频1	XXX Voice Reference	XXX																							
音频2	XXX Voice Reference	XXX																							
音频3	XXX Voice Reference	XXX																							
【角色】																									
																									
列出本 Node 实际出现的主要角色。																									
																									
【镜头目标】																									
																									
说明这一 Node 的剧情和视觉任务。																									
																									
之后输出：																									
																									
subject_definitions																									
summary																									
retention_analysis																									
detailed_description																									
overall_soundscape																									
non_diegetic_music																									
40. 最终检查																									
																									
正式输出前检查：																									
																									
输入																									
																									
Picture ≤ 8																									
																									
Audio ≤ 3																									
																									
Picture / Audio 分配是否清晰																									
Reference																									
																									
Subject 是否真实参与视频																									
																									
Picture / Subject 是否职责明确																									
																									
是否 Reference Leakage																									
声音																									
																									
哪些角色使用固定 Audio？																									
																									
Audio 是否正确绑定？																									
																									
普通 NPC 是否误占 Audio？																									
																									
是否超过3个固定 Voice Reference？																									
对白																									
																									
是否全部为自然日语？																									
																									
每句台词是否只出现一次？																									
																									
是否有高风险汉字？																									
																									
是否需要局部假名化？																									
																									
是否符合角色身份与职位？																									
时间																									
																									
Shot 1 是否无时间戳？																									
																									
后续时间是否递增？																									
																									
是否适合15秒 Node？																									
表演																									
																									
嘴型是否自然？																									
																									
是否过度张嘴？																									
																									
是否夸张喊叫？																									
																									
眼神、呼吸、微表情是否连贯？																									
连续性																									
																									
人物																									
																									
发型																									
																									
服装																									
																									
场景																									
																									
车辆																									
																									
空间																									
																									
光线																									
																									
声线																									
																									
专有名词读音																									
长度																									
																									
Prompt 是否 ≤ 7000字符？																									
																									
是否存在大量重复规则？																									
																									
是否为了压缩而删掉关键对白或动作？																									
41. 最终制作哲学																									
																									
《星穹防卫线》的目标不是单纯生成漂亮的 AI 视频，而是建立一个：																									
																									
连续、可信、可重复制作的原创动画世界。																									
																									
制作逻辑固定为：																									
																									
人物图决定“谁”。																									
																									
场景图决定“在哪里”。																									
																									
载具 / 道具图决定“它是什么”。																									
																									
剧本决定“发生什么、说什么”。																									
																									
唯一 Spoken Dialogue 决定 H3 实际说什么。																									
																									
固定 Audio Reference 决定9名核心女性角色“用什么声音说”。																									
																									
普通 NPC、旁白和男主默认由 H3 自行生成普通声音，不占用固定 Audio 输入。																									
																									
固定读音表决定高风险专有名词的安全读法。																									
																									
每个 Node 最多3个独立 Audio Reference。																									
																									
一个 Node 最多3名固定 Voice Reference 角色，但不限普通自动生成声音角色数量。																									
																									
最终优先级：																									
																									
连续性 ＞ 准确性 ＞ 可发音性 ＞ 可生成性 ＞ 可剪辑性 ＞ 画面表现。																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
																									
