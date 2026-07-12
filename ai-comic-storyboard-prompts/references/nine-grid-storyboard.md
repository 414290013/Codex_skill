# Director Storyboard Design Board Prompt Reference (导演分镜设计板提示词参考)

Use this reference to create the `分镜图提示词（对应表格镜头）` block for each big storyboard shot block.

## Purpose

The output is a single Chinese image-generation prompt for a professional film-director storyboard design board. It must be written inside one fenced code block. It is not a Markdown table, not JSON, not bullets, and not a seven-column board table.

Every time segment inside the prompt must correspond to the Chinese storyboard shot-block rows in exact order. If the Chinese shot block has 6 rows, write 6 time-segment clauses. If it has 9 rows, write 9 time-segment clauses. No deletion, no merging, no reordering.

## Required Output Format

Output this block directly under the English shot block:

````markdown
### 分镜一｜分镜图提示词（对应表格镜头）

```text
写一份用于生成专业影视导演示意图的描述，是一张完整的电影导演分镜设计板。镜头主题包含[N]张镜号，[镜头主题]，[类型/风格]，人物保持一致性[时间1]	画面轨：[前景]：[前景画面1]；[中景]：[中景画面1]；[背景]：[背景画面1]	[台词/旁白1]	[音效/情绪标签1][时间2]	画面轨：[前景]：[前景画面2]；[中景]：[中景画面2]；[背景]：[背景画面2]	[台词/旁白2]	[音效/情绪标签2]...[时间N]	画面轨：[前景]：[前景画面N]；[中景]：[中景画面N]；[背景]：[背景画面N]	[台词/旁白N]	[音效/情绪标签N]，写实，电影感、4K、超清
```
````

Important: keep the exact ` ```text ` fenced-code-block style. Do not output this as a table.

## Fixed Opening Sentence

The prompt must start with this sentence pattern:

`写一份用于生成专业影视导演示意图的描述，是一张完整的电影导演分镜设计板。镜头主题包含[N]张镜号，[镜头主题]，[类型/风格]，人物保持一致性`

Rules:

- `[N]` = the number of shot rows in the Chinese storyboard shot block.
- `[镜头主题]` = a concise phrase from the scene/shot block, e.g. `图1图2两人的对手戏`, `室内压迫对峙`, `街头追逐`, `产品展示与品牌收束`.
- `[类型/风格]` = the user's style if provided, e.g. `短剧风格`, `商业广告风格`, `古风玄幻风格`. If absent, infer from the script conservatively.
- Always include `人物保持一致性`.

## Time Segment Rules

After the fixed opening sentence, append one segment per Chinese shot-block row:

`[时间]	画面轨：[前景]：...；[中景]：...；[背景]：...	[台词/旁白]	[音效/情绪标签]`

Use tab-like spacing or clear spaces between the four parts, but keep it as running text inside the same code block.

- `[时间]`: copy the exact `时间` cell from the corresponding Chinese shot-block row. Do not invent fixed `0-5s / 5-10s / 10-15s` windows unless those are the actual row times.
- `画面轨`: derive from that row's `景别/构图` + `视觉+运镜`, then expand the prompt into `[前景] / [中景] / [背景]`. Do not copy the short CSV cell. Each layer must add cinematic detail: lens height, camera movement, foreground texture, character blocking, micro-action, light/weather/VFX, spatial continuity, and immediate feedback.
- Length density: default to **1200-1800 Chinese characters per 15-second big storyboard**, around **1500 Chinese characters**. For a normal 5-row storyboard, write about **220-320 Chinese characters per time segment**. If there are fewer rows, make each row richer; if there are more rows, preserve all segments while keeping the whole block near the target range.
- `[前景]`: closest visible layer: hands, feet, weapons, props, rain/mud/water droplets, impact contact, micro-expression, lens-adjacent occlusion, local blur/smear detail.
- `[中景]`: main character blocking and action: body route, opponent/partner reaction, stance, dialogue performance, chase/fight choreography, camera movement around the subject.
- `[背景]`: environment and continuity layer: fixed structures, crowd, sky/light/weather, depth, debris, energy aftermath, inherited background baseline, spatial pressure.
- Every time segment must include all three labels exactly: `[前景]`, `[中景]`, `[背景]`. Do not collapse them into one `[画面]` sentence.
- Use dense picture-track prose when the user asks for cinematic prompts: `[前景]` should lock the closest physical/VFX detail, `[中景]` should carry the subject action and camera route, `[背景]` should carry weather, light, spatial pressure, continuity, and aftermath.
- `[台词/旁白]`: extract exact spoken dialogue, narration, or inner monologue from that row's `声音` cell. Preserve original wording. If multiple speakers speak in one row, keep `人物：台词` order.
- `[音效/情绪标签]`: extract SFX/BGM/environment/breath/silence from the `声音` cell. If there is no clear SFX, write a short emotional or plot label from the row, e.g. `谁啊这么吵`, `离谱送件`, `空快递？`, `压迫沉默`, `转折逼近`.

## Ending Style Lock

The prompt must end with:

`写实，电影感、4K、超清`

If the user provides additional style words, append them after this phrase. Do not remove this ending.

## Hard Locks

- Do not output Markdown tables in `分镜图提示词（对应表格镜头）`.
- Do not output JSON.
- Do not use `Grid1`, `Grid2`, `镜头1`, or bullet lists.
- Do not group by fixed time windows unless those time windows come from the Chinese shot-block rows.
- Do not use the big storyboard title as content. Derive segments from the Chinese shot-block rows only.
- Do not omit dialogue, narration, SFX, or emotional tag.
- Do not write `同上`.
- Do not change the user's original dialogue in `[台词/旁白]`.
- Every prompt time segment must use the three-layer picture track form: `画面轨：[前景]：...；[中景]：...；[背景]：...`.
- Every prompt block must be detailed enough for direct image/video generation, around 1500 Chinese characters per 15-second big storyboard. A short summary-style prompt is a failure.
- Do not write `省略`, `后续同理`, `待续`, `继续生成`, `篇幅有限`, or any shortcut instead of a full prompt segment.
- Every Chinese shot-block row must become a fully written prompt segment. No batching, collapsing, or generic "same style for remaining shots".
- Keep this block Chinese, except fixed technical style words like `4K`.

## Example

```text
写一份用于生成专业影视导演示意图的描述，是一张完整的电影导演分镜设计板。镜头主题包含9张镜号，图1图2两人的对手戏，短剧风格，人物保持一致性0-5s	画面轨：[前景]：门把手被猛地拧开，近处快递袋边缘晃入镜头；[中景]：女生开门后压着不耐烦情绪怼向男生，男生举袋解释；[背景]：楼道冷白灯和门牌保持清晰，空间狭窄形成压迫	女生：敲半天了！干嘛啊？我没买快递！男生：没错就是你的，专门给你送的！	谁啊这么吵5-10s	画面轨：[前景]：空快递袋褶皱占据镜头下缘；[中景]：男生把袋子递近，女生身体后撤半步保持怀疑；[背景]：门口墙面与走廊纵深稳定，冷光延续	女生：我最近啥都没剁手，你绝对送错了！男生：地址门牌号全对上，错不了！	离谱送件10-15s	画面轨：[前景]：女生指尖撑开快递袋口，袋内空荡细节清晰；[中景]：女生抬眼质问，男生压低语气提示袋里是话；[背景]：楼道尽头光线微暗，环境安静放大转折	女生：空的？耍我玩呢？信不信我投诉你！男生：别着急，袋子里是带话，不是物件！	空快递？写实，电影感、4K、超清
```

## Safety Handling

For sensitive content, preserve exact dialogue in `[台词/旁白]` unless the user explicitly asks for a platform-safe rewrite. Sanitize only the visual `画面轨` wording across `[前景] / [中景] / [背景]` when needed. If a platform blocks the full prompt because of sensitive visible text, output an additional `纯视觉安全版分镜图提示词` with dialogue replaced by口型/情绪提示, but keep the main prompt unchanged.
