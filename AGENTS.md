# Java Server Architecture Review Skill

Java 服务端架构审查工具。通过**可执行脚本确定性扫描 + AI 深度分析**的混合模式，从 19 个核心维度审查 Java/Spring Boot 项目。

## Trigger Keywords

以下关键词应触发此 skill：
- 架构审查、设计审查、Java 后端审查、服务端架构
- 后端 CR、工程规范检查、检查工程质量
- server arch review、architecture review、code quality check
- "帮我看看这个 Java 项目"、"review 一下后端代码"

## 执行流程

当用户要求审查 Java 项目时，执行以下流程：

### Step 1: 运行扫描脚本

```bash
bash {SKILL_DIR}/scripts/arch-review.sh --project {PROJECT_PATH} --mode <MODE>
```

根据用户意图选择模式：
- `full` — 19 项全量扫描（用户说"全量"、"完整审查"）
- `pr` — 仅扫描 git 变更文件（默认模式）
- `focus --dimensions "sql-injection,security"` — 指定维度（用户说"只看安全"等）
- `quick` — 仅 BLOCKER 级别（用户说"快速检查"）

### Step 2: 解析 JSON 结果

脚本输出 JSON，包含：
- `findings[].type = "confirmed"` — 确定性问题，直接采信
- `findings[].type = "needs_ai_review"` — 可疑点，需要读代码判断
- `uncoveredDimensions` — 脚本未覆盖的维度，需要自主审查

### Step 3: AI 深度分析

- 对 `needs_ai_review` 项：读取相关源代码做判断
- 对 `uncoveredDimensions`：读取 `{SKILL_DIR}/references/*.md` 按规则审查
- 综合分析架构合理性

### Step 4: 生成报告

- 合并脚本结果 + AI 分析结果
- 健康度评分：100 - (BLOCKER × 5) - (MAJOR × 2) - (MINOR × 1)
- **默认输出摘要报告**（评分 + BLOCKER/MAJOR 列表 + 建议），不打印原始 JSON，不逐项叙述分析过程
- 用户说"详细"时才输出完整报告

## 参考文档

- [SKILL.md](./SKILL.md) — 审查维度定义、违规等级、脚本覆盖矩阵
- [references/](./references/) — 详细审查规则文件
- [references/checklist-index.md](./references/checklist-index.md) — 60+ 检查项索引
