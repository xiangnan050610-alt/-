# GitHub优秀AI视频Prompt资源总库

## 用途
本文件集中记录本轮筛选出的优秀 GitHub AI 视频提示词/Skill 资源，并把可迁移的方法映射到本知识库。只保存摘要、方法论、适用范围与来源，不复制原仓库长文。

## A级核心来源

### 1. CyberJ0605/cinematic-video-prompt-engineer-skill
来源：https://github.com/CyberJ0605/cinematic-video-prompt-engineer-skill
核心价值：
- 先判断“什么能在短视频中被看见”，再把抽象剧情翻译为可执行的动作、表演、摄影、光线、声音与时间。
- 运镜按戏剧功能选择，而不是先堆炫技镜头。
- 镜头运动应描述起点、路径/变化、方向、速度、信息增量、终点。
- 情绪应落到可观察表演信号；复杂情绪只选少量关键肌肉/身体信号。
- 续写与多镜头任务优先维护人物、场景、道具和镜头几何连续性。
- 生成结果修复应锁定成功元素，只修改失败控制项。
- 普通日常场景不应强行套商业电影质感；视觉风格必须服从场景事实。

### 2. geekjourneyx/awesome-ai-video-prompts
来源：https://github.com/geekjourneyx/awesome-ai-video-prompts
核心价值：
- 建立 Prompt Engineering、镜头类型、运镜、构图、视觉元素、音画同步、质量检查、工作流等分类。
- 适合作为“知识库目录与案例入口”，不应直接把其全部模板塞入主Skill。

### 3. dexhunter/seedance2-skill
来源：https://github.com/dexhunter/seedance2-skill
核心价值：
- 参考素材必须明确用途：首帧、尾帧、人物、场景、运镜、动作、特效、节奏、声音等。
- 长于8秒时适合时间轴分段。
- 延长、编辑、融合、一镜到底、对白、音画卡点等场景需要不同的控制方式。
- 禁止模糊引用；必须说明参考的是哪一个视觉变量。

### 4. imooooc/video-to-prompt
来源：https://github.com/imooooc/video-to-prompt
核心价值：
- 建立“视频→采样→时间码→动作/镜头/对白/视觉风格→Prompt”的逆向分析链。
- 时间码应覆盖主要可见事件，快速插入镜头合并进相邻节拍。
- 逆向分析时把观察事实与推断分层，避免把猜测写成事实。

### 5. Reviral-ai/ai-video-prompt-checklist
来源：https://github.com/Reviral-ai/ai-video-prompt-checklist
核心价值：
- 用检查表在生成前发现主体、动作、时长、声音、视觉证据和约束缺失。
- 检查“一个主要动作是否清楚”“时长是否容得下动作”“指令是否互相冲突”。

## B级专项来源
- Veo Prompting Guide：https://github.com/snubroot/Veo-3-Prompting-Guide
- Kling 4.0 Prompts：https://github.com/aivideoweb/awesome-kling-4-0-prompts
- Awesome Seedance 2 Prompts：https://github.com/YouMind-OpenLab/awesome-seedance-2-prompts
- video-prompt-skill：https://github.com/lostinheaven-knt/video-prompt-skill
- inference-sh/video-prompting-guide：https://github.com/inference-sh/skills/blob/main/guides/prompting/video-prompting-guide/SKILL.md

## 方法迁移原则
1. 只迁移可泛化的工作方法，不照搬平台专属限制。
2. 模型特定能力进入17-生成模型能力与平台Prompt适配库。
3. 视频逆向分析进入14-参考视频逆向分析库。
4. Prompt结构与时间轴进入13-AI视频提示词结构与时间轴库。
5. 运镜进入05，画面/光线进入04，皮肤进入03，约束进入07，Visual DNA进入18。
6. 主Skill只增加“什么时候查、怎么查、怎么把知识应用到原模板”的流程规则，不复制知识条目。
