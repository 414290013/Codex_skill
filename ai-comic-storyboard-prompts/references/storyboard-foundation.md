# Storyboard Foundation Reference

## Knowledge Categories

- `文戏拆镜`: 2-3秒镜头、对话反应链、J-Cut/L-Cut、沉默与环境细节。
- `基础分镜结构`: 宏观 -> 中观 -> 微观、角色入场、动作关键点、同框交接。
- `输出格式`: S级分镜块、关联剧本、时长推算、旁白语速与画面化。
- `自检`: 是否漏台词、是否一镜到底、是否缺反应镜头、是否压缩时长。


# Manual Storyboard Method Knowledge Base

Use this reference to convert prose into dense, hand-built storyboard logic instead of loose AI expansion.

## Core Method

1. Build every scene unit as `入场 -> 发展 -> 结尾`.
2. Start with `宏观 -> 中观 -> 微观`: world or city scale, then street or room scale, then object or body detail.
3. Use a recurring visual or sound anchor to connect scale changes. Good anchors: light, smoke, window, tree, vehicle, weapon, hand, eye, footprint, wind, bells, door sound.
4. A unit ending should naturally introduce the next unit. Prefer same-frame handoff, shared object, shared gaze, sound bridge, or a character entering the frame.
5. Do not rely on external transition effects. The storyboard itself must create continuity through camera, action, object, gaze, sound, or staging.
6. Key shots are more important than continuous in-between frames. Show the decisive start point and the decisive result point; let the viewer mentally fill the motion.
7. Add missing shots when two major story beats would otherwise feel like a flat jump.
8. Use hard cuts when the visual cause and effect are already clear; avoid decorative transitions.

## Establishing Unit

For the beginning of an episode or a new place:

- Use the first 3 seconds to establish world, tone, location, and hook.
- Avoid one flat wide shot. Use 1-3 linked shots that compress world information.
- Use `宏观 -> 中观 -> 微观` if time allows.
- If time is tight, choose one high-information macro image plus one object or character detail.
- End the establishing unit by placing the main character, key object, or next action inside the same visual logic.

## Character Entry Unit

For character entry:

- Give the character a clear entrance action, not just a face reveal.
- Build the entrance with `环境带出角色 -> 身体局部/动作点 -> 眼神/表情 -> 同框关系`.
- A character entry should include the character's emotional state, social position, and relation to the previous unit.
- When the next character enters, use a shared frame, POV, rear-seat view, doorway view, reflection, or gaze bridge to hand off.

## Action Breakdown

For any action, split into key points:

1. Intention: hand reaches, foot plants, shoulder loads, eyes lock, breath stops.
2. Start point: fist starts, door handle turns, blade leaves sheath, body leans.
3. Result point: hit lands, door opens, blade clears, body arrives.
4. Reaction: target responds, environment reacts, sound lands, emotion changes.

Do not waste shots on meaningless continuous motion unless the action itself is the spectacle.

## Dialogue and Reaction

- Dialogue does not mean the camera must stay on the speaker.
- Split dialogue by breath, punctuation, reaction, and subtext.
- Important words may stay on the listener, object, hand, or silence.
- Use reaction chains for all visible characters: micro-expression, posture shift, breath, hand tension, eye movement.

## Timing

- For short-video storyboard shot blocks, a big storyboard unit should normally be 15 seconds.
- A 15-second big unit may contain 5-12 micro-shots depending on action density.
- Dialogue-heavy units need fewer, longer shots, but every line must remain intact.
- Action-heavy units need short shots and clear keyframes.
- Establishing units can be 0.5-2 seconds per shot if they are visually linked.

## Quality Bar

A manual-grade storyboard should feel like it was built by a human director:

- The viewer always knows where they are.
- Every next shot has a visible or audible reason to exist.
- No unit is just a flat illustration of a sentence.
- The scene breathes through objects, eyes, hands, sound, and spatial handoffs.
- Missing shots are filled by purposeful增补镜头, not random decoration.


# S-Level Integrated Storyboard Prompt Method

Use this reference when the user asks to build S级分镜提示词 from the local knowledge files such as `Gemini影视级分镜.docx`, horizontal/vertical manual segmentation prompts, A(1).pdf, or fight prompt libraries.

## Core S-Level Locks

- Storyboard from emotion beats, not broad scenes.
- Use dense but motivated shots: every row must add new story, emotion, space, action, or reaction information.
- Opening must not be flat: first 15 seconds need world hook, environment-led character entry, and dramatic tension seed.
- Use macro -> mid -> micro construction when entering a world/location/emotional unit.
- Build character establishment through action, posture, gaze, reaction, and relationship blocking.
- Every visual must remain traceable to the novel/script/audio line.

## Output Format

- Before outputting any storyboard, resolve the global-style gate. If the source text is provided without a global style answer, ask only `请提供本次分镜的全局画风。` and do not generate the storyboard yet. If the user answers `无`, `没有`, `没有画风`, `无画风`, `不需要画风`, `不指定画风`, `不用画风`, or equivalent, continue without any global-style section.
- Each big storyboard is a section: `## 分镜一：00:00-00:15｜标题`.
- Under the heading, write current-moment background and blocking baselines before `关联剧本 (Related Script)`.
- Use `production-continuity.md` for background baseline, character positioning, coordinate reuse, movement markers, and retained technical parameters.
- Chinese output uses a fenced `text` shot block, not a Markdown pipe table. Inside the block, write global requirement lines; if an actual style exists, include `【全局画风】` and put the raw style text directly on the next line with no label prefix; if the user answered no style, omit those lines entirely. Then write the CSV header `时间,景别/构图,视觉+运镜,声音,衔接逻辑`.
- No `关联剧本` column inside the shot block.
- No `镜头 / 镜头编号 / Shot No.` table column and no `001 / 002` shot-number column.
- Keep shot-block wording compact, but do not obey old table-length limits when they would remove exact speech, breath, reaction shots, movement markers, or technical parameters. If exact speech is too long, split the big storyboard rather than compressing speech.
- Storyboard image prompts correspond one-to-one with Chinese shot-block rows unless the user explicitly asks for 9宫格.
- Do not use shortcuts such as `省略`, `后续同理`, `待续`, `继续生成`, `篇幅有限`, or `分镜二同上`. Write every shot block and every image-prompt segment completely.

## Natural Speech Timing

Timecodes must be calculated from realistic speech duration before visual timing:

- Calm narration: max 5 Chinese chars/sec.
- Emotional narration / inner monologue: max 4 Chinese chars/sec.
- Normal dialogue: max 3.5-4 chars/sec.
- Crying, begging, pain, fear, threat, whisper, breathless speech: max 2.5-3.2 chars/sec.
- Add punctuation pauses: comma 0.15-0.25s, period/semicolon 0.25-0.45s, question/exclamation 0.30-0.60s, ellipsis/long hesitation 0.60-1.00s.
- Short breath/interjection/silence usually needs 0.8-1.5s.
- If 15 seconds is not enough, split the source into another big storyboard. Never make dialogue unnaturally fast.

## Audio + Novel Alignment

- `声音` must include exact narration/dialogue/inner monologue for the row.
- `视觉+运镜` must depict the same source span: action, reaction, prop, environment, gaze, or body state.
- Do not place later/earlier visual beats under the wrong audio line.
- Do not use generic filler like `按原文动作与情绪执行`.

## Background and Blocking

- Use `production-continuity.md` as the source of truth.
- Every scene needs `背景基线`: exact location, fixed structures, light source, weather/atmosphere, ground, and key prop map.
- No background drift: do not replace a poor bedroom/courtyard/gate with palace, street, tavern, forest, battlefield, or abstract fantasy unless source says so.
- Every scene needs `站位基线`: screen-left/right, foreground/midground/background, and 180-degree axis.
- Characters and props inherit position across rows unless motivated movement changes them.
- Same-location adjacent scene numbers must use `走位标记：延续场号X走位，复用坐标...`; keep micro-movement details such as `低头后头部垂直下沉1.5cm`.
- Technical parameters must be retained when requested: lens, aperture, color temperature, color ratio, texture, distortion control, lighting accessory, IDs, coordinates, and triggered state changes.

## Horizontal vs Vertical

- 16:9 horizontal: medium + close shots dominate; use wide/small-wide for spatial relationships, OTS medium for dialogue, close-up for emotional/key-line emphasis.
- 9:16 vertical: close-up + extreme close-up dominate; medium/wide only as functional support; subject must stay centered and readable.
- Camera movement must serve narrative/emotion, with clear start frame, movement path, and end frame. No random handheld shake, unjustified 360 spin, axis jump, or subject loss.

## Fight Prompt Modules

Use fight modules only when source has fight/threat/weapons/monsters/power release:

- Pre-fight skill release: `0-3 对峙起势`, `3-7 能量汇聚`, `7-12 技能展开`, `12-15 威压定格`.
- 1V1 fight: `0-2 瞬发入战`, `2-5 近身缠斗`, `5-9 全屏对轰`, `9-12 破防反杀`, `12-15 绝杀定格`.
- 1V-many fight: `0-2 合围破局`, `2-5 近身清场`, `5-9 全屏对轰`, `9-12 逐个击溃`, `12-15 全屏清场`.
- Use exact action words: `直刺`, `竖劈`, `横斩`, `撩刀`, `格刀`, `旋斩`, `截击`, `横扫`, `反撩`, `沉肩重砍`, `格后反劈`.
- Use physical VFX: blade trail, weapon sparks, body-impact shockwave, wall collapse, cracked ground, flying gravel, dust ring, debris, cloth snap.

## Self-Audit

Before finalizing, verify:

- Exact source text appears in `关联剧本` and exact spoken text appears in `声音`.
- User-specified global style appears in every Chinese shot block.
- Timing supports human speech.
- Visual matches the same audio/novel line.
- Background and blocking do not drift.
- No shot-number column.
- Movement markers and technical parameters were not dropped.
- Image prompts correspond to Chinese shot-block rows and timecodes.
- Opening achieves S-level hook.

