# Skill 总目录导航

本目录将两套用途不同的 Skill 明确分开管理。**导演 Skill 与提示词生成 Skill 不合并、不互相覆盖，各自保留独立入口、职责和参考资料。**

## 1. 提示词生成 Skill

目录：[`提示词生成Skill/`](./提示词生成Skill/)

用途：将已经明确的剧情/场景需求转化为可供 AI 视频模型使用的详细生成提示词。

- 当前主版本：[`Reality_Cinematic_Engine_Master_SKILL_V10.21_GitHubKB_最高铁律锁定版.md`](./提示词生成Skill/Reality_Cinematic_Engine_Master_SKILL_V10.21_GitHubKB_最高铁律锁定版.md)
- 历史版本：[`提示词生成Skill/历史版本/`](./提示词生成Skill/历史版本/)
- 知识库：仓库根目录的 [`提示词知识库/`](../提示词知识库/)

职责边界：提示词 Skill 负责既有工作流、提示词模板、描述规范、知识库检索路由、输出顺序和自检；复杂的视觉、材质、摄影参数与案例放在「提示词知识库」。不得擅自删改原有模板、输出框架或用户锁定内容。

## 2. 导演 Skill

目录：[`外部导演Skill/DirectorSKILL/`](./外部导演Skill/DirectorSKILL/)

用途：从编剧/导演角度处理故事开发、人物目标与冲突、场景调度、镜头设计、分镜、表演、视听表达、制作交接与诊断。

- 主入口：[`外部导演Skill/DirectorSKILL/SKILL.md`](./外部导演Skill/DirectorSKILL/SKILL.md)
- 故事开发与短剧结构补充模块：[`外部导演Skill/DirectorSKILL/references/story-development-and-short-drama.md`](./外部导演Skill/DirectorSKILL/references/story-development-and-short-drama.md)
- 导演/编剧 Skill 精选参考库：[`GitHub编剧导演Skill精选收藏/`](./GitHub编剧导演Skill精选收藏/)

职责边界：导演 Skill 负责创作判断和制作决策；它可以向提示词 Skill 交付已确定的剧情、人物、场景、表演和镜头意图，但不替换提示词 Skill 的固定输出模板。

## 3. 两套 Skill 的协作顺序

1. **需要开发或诊断故事、人物、戏剧冲突、场景、镜头方案时：先使用导演 Skill。**
2. **需要将确定的方案写成模型可执行的详细提示词时：再使用提示词生成 Skill。**
3. 如果用户只要求直接生成提示词，不强制启动完整编剧流程；按提示词 Skill 的原流程处理。
4. 两套 Skill 可以互相交接信息，但不合并主文件、不复制重复模块、不更改彼此的固定模板。
5. 知识库与 Skill 流程分层管理：导演参考资料留在导演 Skill 的 references/精选收藏中；AI 视频画面质感、光影、皮肤、服装、摄影参数等提示词知识仍归「提示词知识库」。

## 4. 维护规则

- 原有文件优先保留；只有为清晰归类而移动文件时，才调整路径，不改文件正文。
- 已有能力不重复添加；缺失能力才补充。
- 主版本与历史版本明确标记，避免误把旧版当作当前入口。
- 任何未来更新先检查本导航，再更新对应 Skill，不跨目录混写。

## 3. MiniMax 提示词 Skill 外部研究区

- [外部参考 Skill 精选与对比](./提示词生成Skill/外部参考Skill/README.md)
- [社区 Skill 快照](./提示词生成Skill/外部参考Skill/社区Skill快照/README.md)

该区域只属于提示词生成 Skill 的外部研究资料，不属于导演 Skill。当前主 Skill 模板保持独立，外部项目按许可与来源规则存档。
