# MiniMax 视频提示词 Skill 外部参考精选

> 研究日期：2026-10-09
> 目标：筛选可用于 MiniMax / Hailuo 视频生成提示词编写的 Skill，优先考虑官方适配、时间线、镜头连续性、音画控制、参考素材模式和可验证的社区信号。
> 重要：这是外部参考与研究区，不是当前主 Skill。不得将这里的格式直接覆盖到 Reality Cinematic Engine V10.21 的固定输出模板。

## 先说结论

**最值得优先研究的顺序（按适配价值，不等同于纯星标排名）：**

1. **MiniMax 官方 H3 Prompt Writing Skill** — 官方模型适配基线。覆盖 T2VA、I2VA、FL2VA、L2VA、Ref2VA 五种模式，规定结构化提示词和参考素材标签。官方仓库页面约 9.7k stars / 727 forks（仓库整体数据，不是该 Skill 单独的星标）。[官方仓库](https://github.com/MiniMax-AI/MiniMax-H3) · [官方 Skill 目录](https://github.com/MiniMax-AI/MiniMax-H3/tree/main/skills)
2. **babicat4242-svg/minimax-h3-prompting** — 生产校验取向。页面显示 12 stars / 1 fork；强调格式校验、时长、镜头时间线、说话人绑定、参考素材角色和可重复修订。适合研究“提示词输出后如何检查”。[原项目](https://github.com/babicat4242-svg/minimax-h3-prompting) · [本地参考快照](./社区Skill快照/Babicat-H3-Prompting/)
3. **r600a-code/minimax-h3-prompt-skill** — 中文提示词模板与案例库取向。页面显示 7 stars / 1 fork；包含 T2V/I2V/R2V 模板、镜头运动/灯光词汇与案例。其 README 声明提示词和模板开放使用，但仓库没有找到独立 LICENSE 文件；因此此处只保留源链接，不整份复制。[原项目](https://github.com/r600a-code/minimax-h3-prompt-skill)
4. **matheusbgodoi/minimax-h3-prompting** — 便携、轻量、结构清楚，MIT 许可；覆盖模式选择、镜头/动作、对白、环境声、音乐、参考模式和常见错误检查。页面当时显示 0 stars / 0 forks，但技术内容与当前任务相关，故作为技术参考而非人气榜。[原项目](https://github.com/matheusbgodoi/minimax-h3-prompting) · [本地参考快照](./社区Skill快照/Matheus-H3-Prompting/)
5. **unknowlei/minimax-h3-opencode-skills / minimax-h3-text-video-prompt** — 专注纯文生视频，使用官方三字段格式，强调动作顺序、时间预算、镜头切换理由、声音层次与对白保真；仓库页面可见 4 forks，星标数无法从本次页面稳定确认。MIT 许可，已收录该专项 Skill 与许可证。[原项目](https://github.com/unknowlei/minimax-h3-opencode-skills) · [本地参考快照](./社区Skill快照/Unknowlei-H3-Text-to-Video/)

## 中文优先的候选补充

- **Cicaba/minimax-h3-prompts** — 中文优先，强调“增加细节不等于增加事件”、动作预算、角色/场景/运镜参考分工、音画同步和防止提示词格式混用。页面显示 0 stars / 0 forks，项目较新且没有独立 LICENSE 文件；作为阅读研究对象保留源链接，不复制原文。[原项目](https://github.com/Cicaba/minimax-h3-prompts)

## 官方 H3 的八种风格专项 Skill

官方 H3 仓库还提供以下专项方向：极简产品广告、3D 动画短片、纸艺定格动画、品牌宣传片、音乐视频字幕、双人合作游戏开场、拼贴知识讲解、手绘与实拍融合视频。它们更适合作为专项工作流参考，不应整体塞入通用提示词 Skill。部分 Skill 面向 MiniMax Hub 画布节点工作流，不能直接当作通用 Markdown Skill 使用。详见[官方 Skill 清单](https://github.com/MiniMax-AI/MiniMax-H3/tree/main/skills)。

## 针对当前 Reality Cinematic Engine 的吸收建议

### 建议吸收的能力（只增补，不替换原模板）

- 模式识别：先判断是纯文本、首帧、首尾帧还是多模态参考任务；仅当实际使用 H3 对应模式时才套用 H3 专属字段。
- 时间线：把动作拆成可观察的初始状态、动作启动、连续发展、结果/反应、结尾状态；时间总量必须符合用户指定时长。
- 动作预算：限制短时长内的独立事件数量；动作复杂度优先于无效堆词，尤其是打斗、舞蹈、多人互动。
- 参考素材映射：明确哪张图锁定身份、哪张图锁定场景、哪段视频只参考运镜、哪段音频只参考声音，避免引用职责混乱。
- 音频分层：对白/说话人、现场环境声、动作音效、配乐分开；不自动添加用户未要求的台词或音乐。
- 输出自检：检查格式、时长、动作连续性、人物/道具状态、说话人绑定、参考标签、音画冲突和结尾状态。
- 风格落地：把“电影感、真实、细腻”等抽象词转化为可观察的光线、材质、镜头、色彩、运动与环境反应，避免只堆形容词。

### 不应直接照搬的内容

- H3 的专属字段名、时长/帧率/素材数量上限，不能误用到 Hailuo 2.3 或 MiniMax 其他视频模型。
- 英文专属输出、固定三字段/六段式输出，不得覆盖用户原本的中文提示词格式和 V10.21 固定模板。
- 面向 Codex、Claude、OpenCode、ComfyUI 的安装配置与脚本，不是提示词本身；只在用户实际运行对应环境时参考。
- 社区技巧应标记为经验性建议，不得包装成官方保证。

## 口碑与排名说明

星标/收藏量只能作为一个信号，不代表生成质量已经被独立验证。此处将**官方权威性、内容完整度、可执行性、更新情况、可复核的社区指标**分开判断；没有足够证据的项目不会被称作“全网第一”或“收藏前几名”。星标数量会变化，本文数据为 2026-10-09 查阅时的页面值。

## 参考快照目录

- [Babicat H3 Prompting（MIT）](./社区Skill快照/Babicat-H3-Prompting/)
- [Matheus H3 Prompting（MIT）](./社区Skill快照/Matheus-H3-Prompting/)
- [Unknowlei H3 Text-to-Video（MIT）](./社区Skill快照/Unknowlei-H3-Text-to-Video/)

原项目作者与许可证信息保留在各自快照目录中。外部快照用于本地对比研究，不自动并入主 Skill。
