# Storyboard Knowledge Router

Use this file as the first reference router after the source text is classified. It maps `文戏`, `传统武打`, `修仙打戏`, and mixed units to the correct knowledge files. The knowledge base is organized by function, not by imported source file.

## Core Routing Rule

1. Classify every source unit and every big storyboard as one of:
   - `文戏`
   - `传统武打`
   - `修仙打戏`
   - `混合转场`
2. Load only the knowledge files needed for that unit.
3. Apply action knowledge only to action rows; do not let action one-take logic override 文戏 2-3s cut rhythm.
4. If a row includes strike, collision, spell release, heavy landing, clone/summon, defense/evasion, or transformation, run the action workflow below before writing the shot row.

## Knowledge Files By Function

- `storyboard-foundation.md`: 文戏拆镜、宏观-中观-微观、对话反应链、S级输出格式、自然语速、旁白画面化、基础自检。
- `production-continuity.md`: 当前背景基线、站位基线、坐标继承、180度轴线、运镜词库、声音设计、后期配音边界、音效层。
- `fight-knowledge.md`: 15秒动作模块、打击节奏、模糊帧/拖影帧、打戏一镜到底限制、动作质量锁。
- `action-moves-audio-templates.md`: 传统武打招式名、武器招式、玄幻/仙侠招式名、特效/音效/环境震荡、强度模板、武指案例、好莱坞15秒动作范例。
- `action-playbooks.md`: 徒手肉搏三帧接触锁、法术/异能三帧锁、修仙法术表现、起式/亮架、防守/躲避/化劲/保护。
- `gesture-spell-action.md`: 剑指、结印、掐诀、掌印、挥袖、握拳收束、元素法术手势、指尖/腕部锁焦、手势→能量→轨迹→释放→反馈链。
- `xianxia-industrial-choreo.md`: 玄幻修真工业化动作、高速修仙快切、战斗距离、视线锁、元神、法天象地、破碎虚空、渐变变身、多神通层级、跨分镜状态延续、三渲二+3A物理反馈。
- `action-safety.md`: 平台安全替换、动作暴力降级、敏感画面改写、安全提示词自检。
- `nine-grid-storyboard.md`: 分镜图提示词、三层画面轨 `[前景] / [中景] / [背景]`、对应表格镜头输出。

## Route: 文戏

Read:

- `storyboard-foundation.md`
- `production-continuity.md`
- `nine-grid-storyboard.md` when image/storyboard prompts are required

Apply:

- 镜头通常 2.0-3.0 秒。
- 15秒大分镜约 5-7 镜。
- 长台词拆成 `说话方动作 -> 听者反应 -> 手部/道具/环境细节 -> 说话高点 -> 沉默反应`。
- 禁止文戏一镜到底、连续长跟拍、单脸讲到底。
- 每个镜头保留当前背景基线和站位继承，不能让角色无理由瞬移。

## Route: 传统武打 / 武器战

Read:

- `fight-knowledge.md`
- `action-moves-audio-templates.md`
- `action-playbooks.md`
- `action-safety.md` if the image prompt may trigger platform review

Action design order:

1. `动作强度`: choose the intensity level before choosing moves.
2. `动作母体`: grounded kung fu, weapon duel, Hong Kong-style group fight, close-quarters modern counter, environmental stunt, etc.
3. `武指动作设计参考`: readable bridge-work, heavy close contact, short explosive counter, group pressure, or environmental stunt.
4. `关键结果节点`: who gains space, who loses balance, what breaks, what opens, what tactical/emotional state changes.
5. `镜头 / 特效 / 声音 / 安全改写`: camera, blur-frame impact, hit-stop, target feedback, SFX, no-BGM prompt boundary, safe wording.

Every physical strike must include:

- setup / stance
- distance and attack route
- defense/evasion/contact point
- hit-stop or local motion blur when needed
- recoil and target feedback
- result / space change

## Route: 徒手肉搏

Read:

- `fight-knowledge.md`
- `action-playbooks.md`
- `action-moves-audio-templates.md` for move vocabulary and impact audio

Use the three-frame contact lock:

1. `入距帧`: footwork, shoulder/hip compression, guard opening.
2. `接触帧`: clear contact point, local blur/smear, hit-stop 0.12-0.2s.
3. `反弹帧`: target recoil, cloth/body/object feedback, stance recovery or stagger.

Do not write "punch/kick happens" without visible contact and feedback.

## Route: 修仙打戏 / 玄幻修真 / 法术 / 异能 / 元神 / 法天象地 / 破碎虚空 / 招式

Read:

- `fight-knowledge.md`
- `action-playbooks.md`
- `gesture-spell-action.md`
- `xianxia-industrial-choreo.md`
- `action-moves-audio-templates.md`
- `action-safety.md` for image prompt wording

Use supernatural action grammar:

1. `威压场`: light, dust, rain, cloth, hair, ground, architecture, or crowd reacts before release.
2. `蓄力`: spell identity, exact hand/finger seal, wrist/arm route, weapon route, active xianxia state if any (元神/法天象地/破碎虚空/变身), combat distance, qi/energy gathering, formation, talisman, clone/summon state.
3. `释放`: spell/weapon/energy path, camera speed, frame-rate or smear logic.
4. `碰撞/中断`: energy lock, shield break, deflection, recoil, route change.
5. `环境响应`: shockwave, water/rain split, debris, particle trail, light distortion, pressure ring.
6. `余波/反应`: character stance, breath, cloth settle, particles fading, tactical result.

Row continuity lock:

- Each action row must inherit the previous row's end state: weapon position, body momentum, combat distance, contact point, energy pressure, debris/rain direction, cloth/hair motion, and camera motion.
- Do not restart an earlier action stage. If a previous row ends at collision, the next row starts from that collision, recoil, pressure compression, or deflection, not from a fresh wind-up.
- Environmental destruction must show propagation: contact point -> pressure/energy route -> object crack/vibration/suspension -> collapse/reversal/aftermath.
- Professional choreography lock: each combat row must name attack line, defense line, contact frame, blur/smear frame, recoil/feedback, and exit state. Do not use vague speed phrases such as `上百次折返`, `疯狂交错`, or `无数次碰撞` as the action design.
- Post-impact separation lock: for `对冲/碰撞/对轰/反震/倒飞/分开/稳身/对峙`, define the X/Y/Z fight map, 180-degree axis, collision point C, both fighters' rebound vectors, landing frames, final coordinates, facing directions, and distance across the aftermath gap. A fighter who entered from screen left normally rebounds back to screen left unless a named technique visibly redirects them.
- Continuity goof check: no midair foot trenches before landing, no free swing while blades are still locked, no teleporting screen sides/distances, no clear face close-up when the safety lock requires no recognizable face, no heavy gravity reversal before light debris reacts.

Do not write修仙打戏 as normal punches with decorative light. The power system must visibly change space, and any casting gesture must show finger structure, wrist route, camera lock point, energy source, motion trace, active state layer, and release feedback.

## Route: 分身 / 影分身 / 召唤 / 人海战术

Read:

- `action-playbooks.md`
- `action-moves-audio-templates.md`
- `fight-knowledge.md`
- `gesture-spell-action.md`
- `action-safety.md`

15-second default structure:

1. `00:00-00:05 结印 / 召唤 / POOF`: clear hand seals or summoning gesture, exact finger structure, wrist route, close-up on fingers, classic smoke puffs, circular burst.
2. `00:05-00:10 叠浪群体突袭`: clones launch in layers; ground slide, aerial crossing kicks, thrown tools or ranged pressure, foreground/midground/background occlusion.
3. `00:10-00:15 终结汇聚`: clones converge force into the main body, vanish into smoke/energy, main body lands final impact, enemies disperse into safe smoke or stylized energy aftermath.

Rules:

- Clone bodies need layered depth, not a flat wall.
- Every clone disappearance gets a small smoke puff or energy pop.
- Group motion must have lanes: ground lane, midair lane, rear support lane.
- Final impact keeps clear hit anchor, local blur/contact, feedback, smoke/energy aftermath, final stance.

## Route: 防守 / 躲避 / 化劲 / 保护

Read:

- `action-playbooks.md`
- `fight-knowledge.md`
- `action-safety.md` when needed

Every defense row must include:

- attack line
- guard/evasion method
- route change or force redirection
- counter window
- protected target if any
- result of distance/tempo change

## Route: 抽帧 / 慢快门 / 动态模糊

Read:

- `fight-knowledge.md`
- `action-moves-audio-templates.md`
- `production-continuity.md`

Rules:

- Subject remains readable; background/crowd/lights/rain/smoke smear into streaks.
- Write dropped-frame rhythm explicitly: `低帧率顿挫`, `断续拖影`, `帧率骤降`, `帧率回正`.
- Key gaze, hit, realization, or turn should return to readable normal timing.
- Do not combine constant camera shake with unreadable blur.

## Action Quality Failure Conditions

- Move-name soup: move names appear without distance, setup, contact/collision, feedback, and result.
- Air hit: physical impact lacks contact point, overlap/occlusion, hit-stop, or target reaction.
- Effect replaces hit: particles, smoke, cracks, shockwaves, or light appear instead of contact/collision.
- All-fast rhythm: no slow setup, no hit-stop, no recovery/feedback.
- All-blur frame: blur hides the hit anchor instead of guiding speed.
