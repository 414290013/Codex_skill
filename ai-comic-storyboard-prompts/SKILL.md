---
name: ai-comic-storyboard-prompts
description: Create AI comic-drama storyboard prompts from scripts, outlines, or scene text, especially for Chinese AI漫剧, 国漫, 仙侠玄幻, 打斗, 文戏, and Seedance/即梦 video generation workflows. Use when the user asks to turn a script into 分镜提示词, 逐镜头脚本, 漫剧分镜, AI视频提示词, 角色/场景参考提示词, 打斗分镜, 黄金开场, or wants to improve existing storyboard prompts with camera, continuity, action, voice, sound, and platform-safety rules.
---

# AI Comic Storyboard Prompts

## Mission

Turn source text into AI-ready comic-drama storyboard prompts with a production workflow:

1. Director analysis: extract dramatic units, emotion curve, visual symbols, character intent, and scene function.
2. Art direction: define character, costume, prop, scene, lighting, and reference-prompt anchors.
3. Storyboard prompts: write per-shot Seedance/即梦 style video prompts with camera, action, dialogue, sound, emotion, and transition logic.
4. Review: check story fidelity, continuity, generation reliability, and safety wording before delivery.

Default style unless the user says otherwise: 2D国漫赛璐璐动画, hand-drawn 2D characters, hand-drawn 2D scenes, animation-camera compositing, and hand-drawn 2D VFX.

## First Step

Ask for or identify the script before generating storyboards.

- If the user pasted script text, use it directly.
- If the user gave a file path, read that file.
- If only a vague request was given, ask for the script or scene text.
- Do not silently use example files from the workspace as the target script.

If the user asks to analyze, improve, or merge prompt systems instead of generating a storyboard, inspect the provided prompt files and extract reusable rules before editing the skill or output.

## Reference Routing

Load only the references needed for the current task.

Core references:

- `references/seedance-model-characteristics.md`: Seedance 2.0 model characteristics, hard limits, generation traps, 15-second big-storyboard rule, and inter-segment transition rules. Read this first for any Seedance/即梦 output or skill update.
- `references/director-skill.md`: director analysis, emotion units, visual keywords, character entrance formulas.
- `references/art-design-skill.md`: character, prop, costume, scene, and reference image prompt design.
- `references/seedance-storyboard-skill.md`: Seedance/即梦 prompt grammar, shot density, @ reference rules, high-risk generation traps.
- `references/output-format.md`: final line format, dialogue/sound formatting, duration calculation, segment headers.
- `references/review-script-analysis.md`, `references/review-art-direction.md`, `references/review-seedance-prompt.md`, `references/review-compliance.md`: review passes.

Scene-type router:

- For all-purpose reference, first/last-frame workflows, video extension, video editing, music beat-sync, comic page performance, or multimodal reference prompts, read `references/seedance-model-characteristics.md` first.
- For text/dialogue scenes, read `references/storyboard-foundation.md` and `references/production-continuity.md`.
- For traditional fighting or weapon action, read `references/00_storyboard_knowledge_router.md`, then the routed files it names.
- For xianxia, spell, supernatural, clone, summon, transformation, or energy battles, read `references/00_storyboard_knowledge_router.md`, `references/xianxia-industrial-choreo.md`, and `references/gesture-spell-action.md`.
- For action-heavy scenes, also read `references/action-design-master.md`, `references/fight-vfx.md`, and `references/camera-art.md`.
- For voice, acting, emotional delivery, or sound design, read `references/performance-voice.md` and `references/sound-design.md`.
- For golden opening sequences, read `references/golden-opening.md`.
- For nine-grid still storyboard images, read `references/nine-grid-storyboard.md`.

## Workflow

### 1. Classify The Source

Split the source into dramatic units, then classify each unit as:

- `文戏`
- `传统武打`
- `修仙打戏`
- `混合转场`

For each unit, identify:

- narrative function
- emotional state and percentage curve
- active characters and relationship change
- scene location and continuity baseline
- key prop or visual symbol
- dialogue that must remain verbatim
- generation risks such as unclear hands, masked faces, crowd counts, same-frame energy attacks, or unsafe wording

### 2. Build The Director Sheet

Produce a concise director sheet before detailed prompts when the task is non-trivial.

Include:

- logline of the scene
- unit-by-unit beat plan
- character intent and emotional curve
- visual symbol plan
- shot-density target
- scene continuity baseline
- action escalation plan if relevant

Use `references/director-skill.md` for the full method.

### 3. Build Reference Anchors

When the user needs character or scene prompt assets, create:

- character reference prompts with stable identity, silhouette, facial impression, costume anchor, color/light system, and forbidden variations
- scene reference prompts with location, layout, time, weather, light, texture, and recurring objects
- optional post-production voice notes outside the Seedance prompt block

Do not invent exact costume colors or styles inside storyboard rows when a reference image should control them. Use phrases like `角色名的衣服` or `角色名的衣袍`.

### 4. Write Storyboard Prompts

First read `references/seedance-model-characteristics.md`, then use the output format in `references/output-format.md`.

`references/output-format.md` is the source of truth for the final segment template, copy boundary, row format, and validation checklist. Do not maintain a second full template in this file.

Rules:

- Apply this priority order when rules compete: locked safety/user rules, Seedance hard limits, story unit clarity, shot necessity, continuity anchors, then human-facing labels.
- Each big storyboard segment must be one Seedance generation unit, 4-15 seconds. Split longer source material; merge or pad source beats that would be under 4 seconds.
- Prefer a 14-second working target when the user does not require a full 15 seconds; do not pad weak material only to fill time.
- Each big storyboard should carry one dramatic question or one clear emotional/story turn. Split by character objective change, power relationship change, information reveal, emotional defense shift, action phase, scene/time change, or prop ownership change.
- For Seedance continuity-sensitive output, define first-frame padding, tail-frame anchor, asset-reference roles, and a row-level blocking baseline for every shot that changes position, gaze, prop ownership, or scene state.
- Each big storyboard must end with a concrete next-segment hook such as action carryover, prop carryover, gaze carryover, sound bridge, occlusion transition, match transition, or a deliberate space-establishing hard cut.
- Each big storyboard must be split into two clear blocks. Put only the content that should be copied into Seedance under `【发送给即梦AI Seedance 2.0 的提示词】`: asset declaration, scene, continuity anchors, negative exclusion, and shot rows. Put source script, human review notes, segment subtotal, and other non-generation notes after `———以下为制作备注，不发送给即梦AI Seedance 2.0———`. Do not mix notes into the Seedance prompt block.
- Do not output a default character-height field. Character scale follows the provided character references and the script. Only add brief blocking/perspective notes when a shot truly needs scale clarity, such as foreground/background Z-depth, sitting/standing posture, stairs, or deliberate height contrast.
- One shot per line.
- Do not add numeric shot prefixes like `1.` or `2.`.
- Start each prompt with camera or movement instruction.
- Keep each AI visual prompt focused on one core visual idea.
- Each shot must serve one function: establish space, advance action, reveal information, show a choice, carry a reaction, insert a clue/prop, or create a transition hook. Delete shots that serve none of these.
- Use `本段允许资产` as the single asset declaration field. Do not also output `出场角色`; that repeats the same people and increases prompt noise.
- In `本段允许资产`, split references by type: `人物` / `道具` / `文字元素` / `特效元素`. Omit empty categories instead of writing `无`. This prevents Seedance from treating props or text panels as extra characters while keeping the header compact.
- Every uploaded or referenced `@素材` must have a use and ownership/scope statement in the prompt block or notes: what it controls, who owns it, and whether it is character, prop, scene, text, action, camera, or effect reference.
- For key props, always add a `道具尺寸标尺` field or an equivalent row-level size anchor. Define absolute size, relative scale, and contact point. For pills/elixirs, use a small-object anchor such as `直径约1.2cm，约拇指指甲盖大小，位于掌心中央，只占掌心宽度约四分之一`. Do not leave prop size to model inference.
- Use `@角色名` only when binding a visual character reference. Use `@道具名`, `@场景名`, or `@文字元素名` only inside the matching asset category or on first visual mention of that asset. In each shot row, each visible character should normally appear with `@` only on first visual mention; later mentions in the same row use the plain name. Do not add `@` to dialogue speakers, height notes, gaze notes, emotion notes, or ordinary repeated descriptions.
- Preserve user dialogue verbatim.
- Do not output `声音资产绑定`, `声源锁`, VoiceID, audio-reference placeholders, or any character voice-reference binding. Seedance 2.0 does not reliably lock multi-character voices; character dialogue and VO will be handled manually in post-production.
- Keep dialogue text in the storyboard as timing and performance reference only. Use `台词：角色："原文"` for spoken dialogue and `台词：角色（VO）："原文"` for inner monologue.
- For inner monologue / VO, add an explicit visual mouth lock before the dialogue: `口型锁：角色闭口不张嘴，无口型对白，内心旁白不做口型；`. Do not write open-mouth actions such as `嘴唇微张` for VO shots unless the character is also visibly speaking.
- If a shot has no spoken inner-monologue text, do not write `角色（VO）`; write `【无台词】呼吸声/心跳声/衣料声` as sound or acting state.
- 负面排除字段锁死，必须逐字输出：负面排除：无字幕，无背景音乐，仅保留环境音效和对白；如有台词、对话、旁白，使用默认字体，不透明度为0。 不得改写、拆分、删词。
- Do not put human-only `[情绪]` or `[衔接]` labels in the Seedance prompt block. Express emotion and transitions through visible action, sound, gaze, prop state, or camera movement. Put structured labels in the制作备注区 only when useful.
- Use duration estimates based on dialogue length, punctuation pauses, action buffer, and emotional silence.

### 5. Action Rules

For action design:

- Inherit the previous shot's end state: body momentum, weapon position, energy pressure, distance, facing direction, debris, clothing, hair, and camera motion.
- Split critical actions into readable stages instead of one overloaded shot. Use four stages for major attacks, two stages for medium actions, and fold small gestures into acting shots.
- Physical strike: setup, distance, attack route, contact point, hit-stop or blur, recoil, target feedback, result.
- Supernatural action: pressure field, charge, release, collision/interruption, environment response, aftermath/reaction.
- Major emotional reversal, relationship reversal, information reveal, or audience-comprehension beat must become its own reaction shot. Ordinary micro-reactions can stay inside the acting shot.
- New character entry must obey the segment standing baseline and enter from a screen edge.
- Character exit must use a fixed camera and clarify absence in the next relevant shot if needed.

### 6. Safety And Generation Reliability

Apply these checks before final output:

- Replace sensitive visual wording where needed while preserving dialogue text.
- For blades, state the blade tip direction toward the target.
- For hand close-ups, specify finger count and partial sleeve/glove occlusion.
- For masked characters, state `不见任何五官` and use body language or voice.
- Avoid vague group labels when exact character count matters; list every `@角色名`.
- Avoid abstract distant light dots for characters; keep readable human silhouettes.
- Avoid same-frame remote energy release plus victim impact when it causes generation confusion; split into release, travel/collision, feedback.
- Avoid moving-camera exit shots that make characters hang at the frame edge.

## Review Pass

Before delivering, run a concise internal review:

1. Script fidelity: dialogue unchanged, story beats preserved.
2. Continuity: positions, props, costumes, camera axis, entrances/exits, and action end states carry forward.
3. Prompt density: one visual focus per shot; no overloaded prose.
4. Generation traps: hands, masks, crowds, energy attacks, exits, distant observers, and props are controlled.
5. Safety: risky visual words rewritten without changing spoken dialogue.
6. Format: one line per shot, no shot numbers, correct segment headers, no human-only labels inside the Seedance prompt block.
7. Seedance anchors: first frame, tail frame, asset state, 9:16 depth geometry, motion vector, gaze direction, and occlusion/transition driver are explicit where needed.
8. Copy boundary: each big storyboard has a Seedance prompt block first, and non-generation notes are separated after the `———以下为制作备注，不发送给即梦AI Seedance 2.0———` delimiter.
9. Prop scale: every key prop has a visible size anchor; hand-held props state palm position, contact point, and proportion to palm/fingers.
10. Seedance prompt hygiene: no human-only metadata labels, no audio identity binding, no empty `@` references, no duplicate same-character `@` in one line.

If a review fails, revise the output before showing it.






