# 全国大学生职业规划大赛指导 Skill

[![MIT License](https://img.shields.io/github/license/tansir6/career-planning-competition-2027)](LICENSE)

![全国大学生职业规划大赛指导 Skill](assets/banner.png)

一个面向全国大学生职业规划大赛的开源 Agent Skill，支持成长赛道和就业赛道备赛，并内置**覆盖八大工科专业的定制包**。它会按官方评分标准帮助参赛者梳理真实经历、建立证据链，并完成或审核生涯发展报告、求职简历、展示 PPT、陈述稿、证明材料和答辩内容。

> 本仓库基于 [6laoliu6/career-planning-competition-cn-skill](https://github.com/6laoliu6/career-planning-competition-cn-skill)（MIT）fork，已将默认基线升级到第四届（2026—2027），并把定制范围从单一电气方向扩展为全工科体系（工科通用框架 + 8 个专业定制包）。

**适用关键词：** 全国大学生职业规划大赛、职规赛、成长赛道、就业赛道、生涯发展报告、求职简历、展示 PPT、答辩训练、Codex Skill、职业规划。

## 主要能力

- 判断赛道、组别、比赛层级和适用规则
- 建立"评分项—主张—证据—材料位置—缺口"矩阵
- 按评分项诊断材料、保守估分并给出具体修改动作
- 指导成长赛道的目标形成、学习实践、成果验证与动态调整
- 指导就业赛道的岗位调研、胜任力证明、求职适配与发展潜力展示
- 生成或修改报告、简历、PPT 大纲、陈述稿、证明材料目录
- 模拟评委提问，开展答辩训练和终稿一致性审查
- 区分已证实成果、待核实信息和计划目标，避免虚构经历与数据

## 评分基线（第四届，已核验）

本仓库默认采用**第四届全国大学生职业规划大赛（2026—2027）**国家方案作为基线（2026.10—2027.4，重庆主办）：

- 成长赛道：职业目标 25 分，学习实践行动 50 分，优化改进 25 分；国赛环节为主题陈述7分钟、评委提问5分钟、天降实习offer 2分钟
- 就业赛道：职业目标 10 分，综合素质 40 分，专业能力 40 分，发展潜力 10 分；国赛环节为主题陈述6分钟、综合面试6分钟、天降offer 2分钟

校赛、省赛或后续届次的通知与评分表优先于默认基线。涉及资格、材料要求、比赛流程或权重时，应以当届主办方正式文件为准。第三届（2025—2026）权重仅作历史对照。

### 第四届基线核验清单（2026-10-23 核验）

| 项目 | 官方文件 | 核验状态 |
|---|---|---|
| 赛事主办与时间 | 教育部《关于举办第四届全国大学生职业规划大赛的通知》（教学函〔2026〕2号，2026-10-10） | 已核验与教育部官网一致 |
| 成长赛道权重 | 第四届成长赛道方案（职业目标25 / 学习实践50 / 优化改进25） | 已核验与官方方案一致 |
| 报名平台与截止 | 全国大学生职业规划大赛平台（zgs.chsi.com.cn），报名不晚于 2027-01-31 | 已核验 |
| 省赛/国赛时间 | 省赛 2027-03-15 前完成；总决赛 2027 年 4 月 | 已核验 |
| 工科政策锚点 | 电气：《新型电力系统建设"十五五"规划》（发改能源〔2026〕942号）；机械：《"十四五"智能制造发展规划》《人形机器人创新发展指导意见》；信息：《关于深入实施"人工智能+"行动的意见》（国发〔2025〕11号）；能源：《氢能产业发展中长期规划（2021—2035年）》；三航：《通用航空装备创新应用实施方案（2024—2030年）》等 | 已核验，原文链接见各定制包"已核验来源" |

官方参考：

- [教育部关于举办第四届全国大学生职业规划大赛的通知（教学函〔2026〕2号）](https://hudong.moe.gov.cn/srcsite/A15/s7063/202610/t20261010_1453481.html)
- [全国大学生职业规划大赛平台](https://zgs.chsi.com.cn/)

## 安装

兼容 Codex、Claude Code、DSH（DeepSeek Harness）等支持标准 Agent Skills（SKILL.md + references 目录）的客户端。把整个仓库放到任一被扫描的 skills 目录即可：

```bash
# Codex
git clone https://github.com/tansir6/career-planning-competition-2027.git "$HOME/.codex/skills/career-planning-competition"
# Claude Code
git clone https://github.com/tansir6/career-planning-competition-2027.git "$HOME/.claude/skills/career-planning-competition"
# DSH：放入 ~/.dsh/skills 或在「设置 → Agent Skills」导入整个目录/zip
```

也可以下载仓库后手动复制，确保最终路径含 `SKILL.md`：

```text
<skills目录>/career-planning-competition/SKILL.md
```

安装后重新打开会话，或在新的对话中使用。

## 使用示例

可以直接描述任务，例如：

```text
请用 career-planning-competition 帮我按成长赛道评分标准审核这份生涯发展报告。
```

```text
我要参加职业规划大赛就业赛道，目标岗位是数据分析师。请先帮我建立评分项和证据矩阵，再设计 7 分钟展示 PPT。
```

```text
我是机械工程专业（智能制造方向），参加成长赛道。请读取机械定制包，帮我建立证据链并模拟评委追问。
```

```text
请模拟国赛评委，对我的陈述稿进行追问，并指出哪些成果缺少证明材料。
```

## 文件结构

```text
全国大学生职业规划大赛指导-Skill/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── assets/
│   └── banner.png                    # README 横幅图
├── examples/
│   └── diagnostic-demo.md            # 示例：材料诊断输入与输出（虚构数据）
└── references/
    ├── engineering-framework.md      # 工科通用定制框架（总入口 + 定制包索引）
    ├── official-baseline.md          # 官方基线（第四届，已核验）
    ├── growth-track.md               # 成长赛道指导
    ├── employment-track.md           # 就业赛道指导
    ├── deliverables.md               # 材料与展示制作
    ├── defense-and-audit.md          # 答辩与终审
    └── packs/                        # 八大工科专业定制包（按专业读取）
        ├── electrical-growth-track.md
        ├── mechanical-growth-track.md
        ├── information-growth-track.md
        ├── automation-instrument-growth-track.md
        ├── civil-transport-growth-track.md
        ├── chemical-materials-environment-growth-track.md
        ├── energy-power-growth-track.md
        └── aerospace-ocean-growth-track.md
```

## 工科定制包清单

| 专业大类 | 定制包 | 覆盖专业示例 |
|---|---|---|
| 电气工程 | [电气工程](references/packs/electrical-growth-track.md) | 电气工程及其自动化、智能电网 |
| 机械工程 | [机械工程](references/packs/mechanical-growth-track.md) | 机械设计制造、智能制造、机器人、车辆 |
| 信息类 | [信息类](references/packs/information-growth-track.md) | 计算机、软件、电子信息、人工智能、通信 |
| 自动化与仪器 | [自动化与仪器](references/packs/automation-instrument-growth-track.md) | 自动化、测控技术与仪器 |
| 土木与交通 | [土木与交通](references/packs/civil-transport-growth-track.md) | 土木、道桥、交通、地下空间 |
| 化工·材料·环境 | [化工·材料·环境](references/packs/chemical-materials-environment-growth-track.md) | 化工、材料、环境、生工（工科） |
| 能源与动力 | [能源与动力](references/packs/energy-power-growth-track.md) | 能源与动力、储能、氢能、核工程 |
| 航空航天·海洋 | [航空航天·海洋](references/packs/aerospace-ocean-growth-track.md) | 飞行器设计、航空航天、船舶海洋 |

每个定制包包含：政策锚点（带官方来源）、岗位锚点、能力模型、证据清单、优化方向、专业答辩追问与核验日期。非工科专业使用通用成长赛道指导即可。未覆盖的专业（矿业、水利、纺织、食品等）先使用工科通用框架，欢迎提交新定制包（见参与改进）。

## 使用原则

- 参赛者提供的当届通知、评分表和学校要求优先。
- 所有奖项、排名、数据、访谈结论和岗位信息都应有真实依据。
- 评分时区分官方权重与内部诊断，不把自定义细分分值说成官方标准。
- 先修复报告、简历、PPT、陈述稿之间的事实冲突，再优化表达和视觉呈现。
- 政策锚点以官方文件为准，引用时注明文号或链接并标注核验日期。

## 维护与更新

大赛规则按届次更新，本仓库按年度维护基线：

- 每个规则性文件头部标注 `核验日期`；届次更新后重新核验并同步修改。
- 欢迎通过 Issue 提交：当届通知/评分表变化、政策锚点更新、专业定制包新增。
- 已核验的政策锚点见各定制包文末"已核验来源"；标注"可在 gov.cn 检索核验"的条目为方向性锚点，引用前请按文件名检索原文。

## 参与改进

欢迎通过 [Issue](https://github.com/tansir6/career-planning-competition-2027/issues) 提交规则更新、材料问题和改进建议；新增专业定制包请参考任一现有定制包的结构并附政策来源。如果这个项目对你有帮助，可以点一个 Star，让更多参赛同学看到它。

## 许可证

本项目采用 [MIT License](LICENSE)。本仓库 fork 自 MIT 项目，保留上游版权声明并追加本仓库维护者署名。
