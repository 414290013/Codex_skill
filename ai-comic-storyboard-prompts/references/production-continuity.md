# Production Continuity, Camera, and Voice Reference

## Knowledge Categories

- `背景基线`: 固定空间结构、光线方向、天气/质感、色彩比例、道具地图、技术参数。
- `站位基线`: 人物坐标、层次、朝向、180度轴线、走位继承、同场景连续性。
- `运镜词库`: 跟拍、环绕、推拉、变焦、慢变速、组合运镜和景别匹配。
- `声音设计`: VoiceID、语气状态、原文台词保留、SFX/BGM、语速与停顿。


# Background, Blocking, and Technical Continuity Knowledge Base

Use this reference whenever a storyboard shot block needs scene continuity, character positioning, movement coordinates, row-level blocking notes, or technical camera/image parameters.

## Required Baselines

Every big storyboard must define these two baselines before `关联剧本 (Related Script)`:

- `背景基线`: exact location, fixed spatial structures, light source direction, weather/atmosphere, ground/floor plane, key prop map, color ratio, texture, distortion control, and reusable scene ID when available.
- `站位基线`: each visible character's screen-left/screen-right relation, foreground/midground/background layer, 180-degree axis, initial coordinate when useful, and any triggered position change inside the unit.

Use concise production wording. Do not turn baselines into decorative prose.

Example:

```text
背景基线：@场景2破旧出租屋｜窄门在画左后方，单人床画右中景，窗户画右后方冷光入射，地面灰白瓷砖，主色冷蓝60%+脏白25%+暗灰15%，胶片颗粒15%，畸变控制≤1%。
站位基线：@许燃画左前景(2.5,0.6)，@林夏画右中景(4.1,1.2)，两人轴线沿床沿到门口，镜头不得无动机越轴。
```

## Character Positioning

- Character coordinates use scene-left-bottom as `(0,0)` unless the user provides another coordinate system.
- Use `@人物` tags in `视觉+运镜` and `声音` cells.
- Position inheritance is mandatory: the next shot inherits the prior shot's location, layer, screen direction, and body state unless a visible action changes it.
- If a character changes layer or screen side, write the motivated movement in `视觉+运镜`: `@A从画左前景侧退至画左中景`, `@B由门口(1.0,2.8)走到桌边(3.2,1.4)`.
- Never let a character jump from background to extreme foreground without an intermediate movement, motivated camera path, or deliberate disorientation note.

## Character Height Ratio Lock

- Treat height as a continuity baseline, not a decorative character note.
- If the user provides a numeric height for one character and no height for another adult main character, keep the unspecified adult in the same adult height class unless the script explicitly says otherwise.
- Convert height notes into visible screen constraints: `头顶高度基本齐平`, `肩线接近`, `同为成人体型`, `禁止一高一矮`, `禁止儿童化`, `禁止缩小体型`.
- In two-character standing shots, put the height lock in the segment baseline and repeat it in the first same-frame shot or any shot where scale drift appeared before.
- If characters stand at different Z-depths, name the perspective effect so the model does not interpret it as body height: `A在前景显大是透视关系，真实身高仍与B接近`.
- Sitting, kneeling, bowing, stairs, slopes, platforms, carrying, or crouching must explicitly state posture-caused height change; otherwise keep adult head-top and shoulder-line alignment stable.

## Movement Marker Format

When adjacent shots or adjacent scene numbers stay in the same location, write a `走位标记` inside `视觉+运镜` or the asset-flow field. It must preserve the prior coordinate and name the physical change.

Required format:

`走位标记：延续场号X走位，复用坐标@人物（x,y），[身体/头部/手部/视线/重心变化]。`

Canonical example to preserve:

```text
走位标记：延续场号2走位，复用坐标许燃（2.5,0.6），低头后头部垂直下沉1.5cm。
```

Rules:

- Keep coordinates stable when only posture, gaze, breath, hand position, or head angle changes.
- Use centimeter-level body changes when the shot depends on micro-performance: `头部垂直下沉1.5cm`, `右手指节收紧0.8cm`, `肩线向画右倾斜3度`.
- For walking/fighting, include trajectory: `@A从(2,3)快速侧移至(4,3)，抬手格挡`.
- For same-location adjacent scene numbers, begin with `延续场号X走位，复用坐标...`.
- For changed blocking, name the trigger: `因@B伸手拉开门，@A从(2.5,0.6)后撤到(2.1,0.9)`.

## Background Continuity

- `背景基线` must prevent location drift. Do not replace a poor bedroom, corridor, courtyard, gate, vehicle, street, or battlefield with a richer location unless the source says so.
- Reuse fixed structures across shots: doors, windows, bed, table, altar, gate, car seat, weapon rack, rubble line, light source, and prop positions.
- Lighting may intensify with emotion, but the base light direction, color ratio, and season/time anchor must remain stable unless a plot event changes them.
- If the scene state changes, write the trigger: broken lamp, opened door, rain starts, power release, crowd enters, weapon falls, smoke fills the room.

## Technical Parameters

Technical parameters must be retained when the workflow asks for them or when visual consistency depends on them.

Include them in `视觉+运镜`, `声画节奏校验`, `技术参数`, or asset-flow notes as appropriate:

- Lens/focal length: emotion close-up `85mm-135mm`, dialogue OTS `50mm-85mm`, fight wide `24mm-35mm`.
- Aperture: emotion close-up `f/1.8-f/2.8`, dialogue `f/2.8-f/4.0`, fight wide `f/4.0-f/5.6`.
- Light/color: color temperature, main color ratio, light direction, shadow/highlight behavior.
- Image texture: film grain percentage, dust/smoke density, fabric/metal/skin texture, surface wear.
- Distortion and stability: keep distortion `≤1%` for asset consistency unless stylized disorientation is explicitly required.
- Continuity locks: scene ID, character ID, prop ID, coordinates, and triggered state changes.

Example row note:

```text
技术参数：85mm，f/2.2，冷蓝60%+脏白25%+暗灰15%，窗右侧逆光5500K，胶片颗粒15%，畸变控制≤1%。
```

## Self-Audit

Before delivery, verify:

- Every big storyboard has both `背景基线` and `站位基线`.
- Coordinates and screen direction are inherited unless visibly changed.
- Same-location adjacent scene numbers use `延续场号X走位，复用坐标...`.
- Micro-movements preserve useful centimeter/degree details.
- Technical parameters are not dropped when the workflow asks for them.
- Background, character, and prop IDs do not drift across repeated locations.


# Camera Movement Knowledge Base

Use this reference to choose precise Hollywood/S-level camera movement instead of generic "push/pull/pan".

## Core Camera Vocabulary

- `贴身跟拍`: close immersive follow; use for walking, running, pursuit, body details, panic, combat.
- `环绕运镜`: orbit around the subject; use for heroic reveal, emotional pivot, object reveal, ritual moments.
- `频繁变焦`: rapid focal compression/expansion; use for shock, suspicion, emotional rupture, multi-subject contrast.
- `超广角高空俯拍`: large-scale god-view; use for cities, battlefields, crowds, worldview, fate.
- `极速俯冲跟焦`: high-speed dive while keeping focus; use for falling, landing, aerial-to-ground impact, sudden threat.
- `慢变速`: gradual speed ramp; use for emotional rise, impact peak, reveal, or poetic transition.
- `稳定超广角`: stable wide lens; use for immersive environment, group blocking, spatial clarity.

## Dynamic Follow Variants

- `贴身贴地跟拍`: feet, hem, wheels, dust, speed, chase, low-body action.
- `贴身仰角跟拍`: low-angle close follow for aura, dominance, heroic or villain entry.
- `贴身穿障跟拍`: pass through doors, curtains, crowds, trees, debris; use for depth and danger.
- `贴身侧移跟拍`: stable side follow for parallel walking, carriage, riding, two-person movement.

## Orbit Variants

- `低角度环绕跟拍`: power-centered orbit for high-status characters, weapons, magic buildup.
- `高空环绕俯拍`: large space plus subject focus; use for battlefield or ritual layout.
- `极速环绕跟焦`: high-tension orbit for fight climax, emotional explosion, target lock.
- `半环绕推进`: move from side to front; use for a character changing decision or exposing emotion.

## Zoom and Speed-Ramp Variants

- `变焦推拉环绕`: orbit plus zoom for suspicion, stage spectacle, emotional fracture.
- `跟拍高频变焦`: follow with quick focal changes for street chaos, chase, fast multi-subject handoff.
- `俯冲变焦跟焦`: dive plus zoom; use from huge environment into decisive detail.
- `定点变焦摇镜`: fixed pan with zoom; use for scanning groups, rooms, or suspicious details.
- `急快缓慢变速跟拍`: fast push then slow stop; use for jump, impact, emotional snap, freeze highlight.
- `环绕渐变变速`: slow-fast-slow orbit; use for complete emotional arc.
- `变焦联动慢变速`: zoom and motion speed rise together; use for deep emotional pressure.

## High-Impact Combinations

- `稳定超广角 + 高空平飞扫拍 + 轻俯`: high-end opening, world scale, battlefield scan.
- `贴身跟拍 + 低角度环绕 + 慢变速`: character aura reveal, villain entry, hero awakening.
- `超广角高空俯拍 + 极速俯冲跟焦 + 频繁变焦`: world scale to threat detail, blockbuster opening.
- `稳定超广角 + 贴地横移 + 跟拍升降`: immersive group movement or street action.
- `极速俯冲跟焦 + 俯冲接贴地跟拍 + 慢变速`: landing, chase continuation, fast-to-ground continuity.
- `贴身穿障跟拍 + 频繁变焦 + 急快缓慢变速`: alley chase, room panic, crowd escape.
- `极速环绕跟焦 + 频繁变焦 + 慢变速`: fight climax, emotional explosion, reveal of true power.

## Shot Writing Rules

Each `运镜提示` cell should include:

`运镜名称 + 起始帧 -> 关键帧 -> 结束帧 + 镜头情绪目的`

Example:

`贴身穿障跟拍；起始帧从破门缝贴近油灯，关键帧穿过悬挂衣物掠到主角手背，结束帧停在刀柄；目的：把空间压迫和求生动作连成一条线。`

## Selection Rules

- Use high-angle wide views for world, fate, layout, and strategic pressure.
- Use low-angle close movement for power, threat, dominance, or heroic ignition.
- Use handheld breathing only when the character is unstable, injured, chased, or afraid.
- Use stable wide movement when the audience must understand space.
- Use fast orbit or zoom only at genuine emotional or action peaks.
- Do not repeat the same camera movement for three shots in a row.


# Voice and Sound Design Knowledge Base

Use this reference whenever a storyboard contains narration, inner monologue, dialogue, screams, breaths, combat sounds, ambience, or music.

## VoiceID Lock

Before writing the table, assign every speaking voice a stable `VoiceID`.

VoiceID definition must include:

- Gender / age stage / pitch tendency.
- Timbre keywords: clear, warm, hoarse, metallic, youthful, airy, cold, etc.
- Diction and rhythm: heavy word starts, clipped endings, fast or slow baseline.
- Breath and resonance: chest, nasal, airy, stable, broken, breathy.
- Accent or register: ancient, modern, regional, official, street, noble, rough.
- Character identity feeling.

Once defined, the same character must keep the same VoiceID. Only state and delivery may change.

## Per-Shot Voice Instruction

Every storyboard row must include sound design. If the shot contains speech, the `声音设计` cell must include the exact line and this structure:

`【台词】角色：“原文台词一字不差。” 【配音指令】角色｜VoiceID｜状态（身体/情绪/目标）｜语气特点（音量/语速/气息/尾音/情绪色彩） 【音效/BGM】...`

If the shot has no speech:

`【无台词】环境声 / 动作音效 / 呼吸 / BGM / 静默设计...`

## Exact Dialogue Rules

- Do not rewrite, polish, shorten, merge, or paraphrase any dialogue, narration, or inner monologue.
- If a line is too long for one shot, split it across multiple shots at punctuation or breath points, but preserve every character in order.
- If the source contains narration or inner monologue, treat it as voiceover unless the user says no narration.
- Track all spoken text before finalizing. Nothing may be missing.
- Never write "同上", "同前", "继续上一句", or any placeholder.

## Delivery State

For each speaking shot, adjust only:

- Body: injured, drunk, panting, whispering, standing still, running, restrained.
- Emotion: calm, angry, scared, guilty, proud, collapsing, pretending, cold.
- Goal: intimidate, plead, hide, delay, comfort, provoke, test, survive.
- Volume: low / medium / high, or 1-5.
- Speed: slow / medium / fast, or 1-5.
- Breath: steady, tight, laughing, panting, trembling, suppressed.
- Ending: clipped, dragged, pressed down, rising.
- Color: sarcasm, grief, false calm, cold laugh, rage under control.

## Sound Layering

Sound design should include:

- Dialogue or voiceover when present.
- Ambience: wind, room tone, rain, crowd, insects, city, battlefield.
- Foley: cloth, footsteps, weapon draw, hand on wood, breath, saliva, door hinge.
- Impact: thud, crack, metal clash, dust blast, energy pulse, body hit.
- Music: low drone, rising strings, percussion hit, silence drop, climax swell.
- Sound bridges: a sound may begin before the next visual, but do not output a separate transition column.

## Dialogue Density

- A 10-second group should usually carry no more than 4 dialogue lines unless it is fast argument.
- For dense prose, distribute narration over several shots and let visuals carry information.
- For emotional lines, give the listener or object a reaction shot while the voice continues.

## Self-Check

Before delivery:

1. List all dialogue, narration, and inner monologue from the source.
2. Confirm each exact text appears once in `声音设计` or `关联剧本`.
3. Confirm no line has been paraphrased.
4. Confirm every speaking row has a VoiceID and delivery state.
5. Confirm silent rows still have ambience, Foley, BGM, or intentional silence.

## 最新分镜 Skill 融合连续性规则

本节用于吸收用户提供的“最新skill出分镜”资料。规则只补强 Seedance 2.0 分镜稳定性，不覆盖现有时长、格式和安全规则。

### 大分镜连续性契约

- 每个大分镜仍按一个独立 Seedance 生成单元处理。
- 15 秒是硬上限；可行时优先写 14 秒生产目标。
- 每段都要有首帧垫图锚点和尾帧生成锚点。
- 首帧锚点说明继承主体、位置、视线、道具归属、光线、场景几何和残留动作。
- 尾帧锚点说明最终姿态、道具位置、运动向量、遮挡、环境反馈和声音余波。
- 下一段首帧必须显式继承上一段尾帧，或用空间/时间建立镜头解释硬切。

### 逐镜站位基线

当镜头改变位置、朝向、视线、层级、道具归属或场景状态时，使用逐镜站位基线：

```text
本镜站位基线：继承上一镜A在画左前景、B在画右中景，A面向B，B视线看向A手中道具；
```

规则：

- 段首站位基线定义整段空间；逐镜站位基线定义本镜的继承和变化。
- 被裁出画面不等于消失。人物或道具仍在场时，必须保留画外方向和返回路径。
- 新角色必须从画面四边之一入画，并落到明确位置。
- 角色出画优先使用固定镜头；下一次相关镜头要说明该角色是离场、画外，还是仍在空间内。

### 人脸、视线和群像锁

- 可见角色在影响剧情理解时，必须写明脸部朝向和视线目标。
- 蒙面、兜帽、背影、遮挡角色要写清隐藏内容，用身体角度、头部角度、声音、呼吸或手部动作表达情绪。
- 反应镜必须说明“谁看见了什么、视线朝向画面哪边”。
- 多角色场景中，重点人物要用体型、年龄段、发型轮廓、服装轮廓、道具、姿态、层级或脸部可见度区分。
- 非重点群众降级为背景轮廓，避免模型复制同脸同姿势。

### 资产状态锁

相邻镜头和相邻大分镜必须追踪：

- 角色：姿态、伤痕/印记、情绪伪装、衣物运动、手部位置、视线方向。
- 道具：持有者、位置、朝向、是否藏起、是否破损、画面中是否明确不存在。
- 场景：门窗开合、家具移动/破损、烟尘雨雪光线变化、能量残留。
- 特殊状态：变身、法术光效、伪装、附身、分身、召唤、临时能力效果。

如果道具破损、服装改变、角色变身或场景状态已经明显偏离参考资产，应提示“参考资产需更新”。

### 尾首帧四件套

交付前逐段检查：

1. 资产状态：可见对象和角色状态延续，除非镜头内发生可见改变。
2. 9:16 空间几何：左右、前中后景、Z轴距离、遮挡和180度轴线可读。
3. 运动向量：人物、镜头、衣物、烟尘、光线、粒子、飞行物延续或有原因停止。
4. 转场驱动：动作、道具、视线、声音、遮挡、形状匹配、光源匹配或空间建立硬切明确。

### 动态尾帧门

段尾最后一镜不得成为静态海报，至少保留一种活性线索：

- 呼吸、眨眼、手指微动、衣袖摆动。
- 尘烟、蒸汽、雨线、烛火、光线变化。
- 脚步未落、道具滑动、遮挡物掠过。
- 台词尾音、房间底噪、远处呼喊、J-Cut 或 L-Cut 声音桥。

### 运镜路径完整性

非固定运镜必须包含：

```text
起始帧 -> 路径 -> 速度变化 -> 关键帧/焦点 -> 结束帧 -> 运镜动机
```

拒绝无动机运镜。运镜必须用于建立空间、跟随动作、加强压迫、隐藏/揭示信息、制造遮挡或准备下一段转场。

### 动作镜头防软化检查

动作、法术、追逐、碰撞、变身或高压对峙镜头，至少写入 4 个导演可见锚点：

- 接触点
- 运动路线
- 屏幕方向或视线
- 前景/视差
- 环境反馈
- 速度、气压、粒子、衣物或发丝反应
- 声音峰值
- 物理支撑点或受力点
- 色彩/光线变化
- 道具状态
