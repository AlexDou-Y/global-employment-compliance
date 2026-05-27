[English](README.md) | [中文](README.zh-CN.md)

# Global Employment Compliance

[![Version](https://img.shields.io/badge/version-16.0-blue.svg)]()
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-orange.svg)](https://docs.claude.com/en/docs/claude-code)
[![Language](https://img.shields.io/badge/lang-简体中文-red.svg)](README.md)

> 全球人力合规与运营专家 — 一个面向 Claude Code 的 Skill，用于生成各国/地区的用工合规手册、查询当地劳动法细节、解答海外 HR 实务问题。

适用对象：跨国公司 HR、外派项目经理、全球用工服务商、劳动法咨询从业者。

---

## 核心特性

- **14 章标准结构**：覆盖员工全生命周期 — 序言、国家概况、招聘、薪酬、个税、社保、合同、合同解除、假期、工会、数据合规、劳动争议、外汇、风险提醒、资料汇总
- **三层内容模型**：规则层（法律规定）+ 实务层（企业如何执行）+ 风险层（常见问题与预防）
- **三阶段研究流程**：官方法规 → 权威解读 → 定向补全，自动化分阶段调研
- **27 点质量清单**：输出前强制校验，确保覆盖完整、内容准确、格式规范
- **持久化研究**：研究内容实时落地磁盘，规避 auto-compact 上下文丢失风险
- **增量更新支持**：可针对特定章节单独更新，不必重新生成整本手册

---

## 安装

### 前置要求

- 已安装 [Claude Code](https://docs.claude.com/en/docs/claude-code)
- 系统：Windows / macOS / Linux

### 方式 1：克隆到 skills 目录

```bash
# Linux / macOS
git clone https://github.com/<your-username>/global-employment-compliance.git \
  ~/.claude/skills/global-employment-compliance

# Windows (Git Bash / PowerShell)
git clone https://github.com/<your-username>/global-employment-compliance.git \
  "$HOME/.claude/skills/global-employment-compliance"
```

### 方式 2：手动下载

1. 下载本仓库 ZIP 包并解压
2. 将 `global-employment-compliance/` 整个目录复制到：
   - Linux / macOS: `~/.claude/skills/`
   - Windows: `%USERPROFILE%\.claude\skills\`

### 验证安装

启动 Claude Code，输入 `/skills` 查看可用 skill 列表，应能看到 `global-employment-compliance`。

---

## 使用

### 场景 1：生成完整合规手册

直接在 Claude Code 中描述需求即可触发：

```
帮我生成一份新加坡的用工合规手册
```

或显式调用：

```
/global-employment-compliance 生成韩国用工合规手册
```

**输出**：
- 文件：`新加坡用工合规手册_YYYYMMDD_V1.0.md`
- 位置：`~/.claude/skills/global-employment-compliance/`
- 格式：Markdown（兼容飞书、Notion、Confluence），含表格、图例、法律链接

### 场景 2：快速查询劳动法

```
韩国的最低工资是多少？
阿联酋 DIFC 的试用期规定是什么？
美国加州的加班费如何计算？
```

### 场景 3：合规实务咨询

```
我们要在德国解雇一名员工，需要注意什么？
外籍员工在日本工作需要办理哪些手续？
如何在法国合规地进行大规模裁员？
```

### 场景 4：增量更新已有手册

```
更新韩国手册的最低工资部分到 2026 最新数据
基于当前的法规变化，给迪拜手册补充一节远程办公政策
```

---

## 输出示例

生成的手册采用统一结构：

```
第1章 序言（适用范围、版本说明）
第2章 国家/地区概况
第3章 招聘与入职
第4章 薪酬与福利
第5章 个人所得税
第6章 社会保险与公积金
第7章 劳动合同
第8章 合同解除与赔偿
第9章 假期与休假
第10章 工会与员工代表
第11章 数据保护与合规
第12章 劳动争议与诉讼
第13章 外汇与跨境支付
第14章 风险提醒与资料汇总
```

每个条款均按"规则 → 实务 → 风险"三层展开，附法律条文出处链接。

---

## 目录结构

```
global-employment-compliance/
├── skill.md                    # 主入口（Claude 加载的入口文件）
├── README.md                   # 本文档
├── ARCHITECTURE.md             # 架构说明
├── CHANGELOG.md                # 版本变更日志
├── LICENSE                     # MIT 许可证
├── 1_core/                     # 核心规则（合规专家定位、原则）
├── 2_tools/                    # 工具配置（Web Search 策略等）
├── 3_workflow/                 # 工作流（研究流程、质量校验、增量更新）
├── 4_output/                   # 输出规范（格式模板、术语标准、章节尺度）
├── 5_spec/                     # 章节规格（14 章详细要求）
└── 6_meta/                     # 元信息
```

---

## 适用国家/地区

理论上支持任意国家/地区，已实测验证：

- **东亚**：日本、韩国、中国香港
- **东南亚**：新加坡、马来西亚、印尼、越南、泰国
- **中东**：阿联酋（含 DIFC）、沙特阿拉伯
- **欧美**：美国（联邦及加州）、英国、德国、法国

> 注：法规更新较快的地区（如欧盟），建议生成手册后人工复核最新立法动态。

---

## 工作原理

```
用户请求
   ↓
[Scope 确认] → 创建草稿文件
   ↓
[阶段 1] 官方法规收集 → 实时写入草稿
   ↓
[阶段 2] 权威解读补全 → 实时写入草稿
   ↓
[阶段 3] 信息分发 → 按章节分配
   ↓
[质量校验] 27 点检查清单
   ↓
[最终写入] 分批 Edit 写入正式文件
   ↓
[HRBP 视角审查] 完整性 + 实务可执行性
```

详见 [ARCHITECTURE.md](ARCHITECTURE.md)。

---

## 免责声明

本 skill 生成的合规手册仅供参考，**不构成法律意见**。各国劳动法规复杂多变，正式应用前请：

1. 由当地持牌律师或专业咨询机构复核
2. 关注法规更新（手册中标注的有效期）
3. 结合企业实际情况调整执行细节

作者及贡献者不对使用本工具产生的任何法律或商业后果承担责任。

---

## 路线图

- [ ] 英文版 README（International Edition）
- [ ] 多语言手册输出支持（English / 日本語 / 한국어）
- [ ] 集成 Claude Code Plugin Marketplace
- [ ] 章节模板可视化预览

---

## 贡献

欢迎提交 Issue 和 Pull Request：

- **报告问题**：法规错误、模板缺陷、流程改进建议
- **新增国家**：欢迎贡献已实测的国家手册作为参考样本
- **改进 Prompt**：优化研究阶段的搜索策略、质量校验清单

提交 PR 前请阅读 [CHANGELOG.md](CHANGELOG.md) 了解版本演进。

---

## 许可证

[MIT](LICENSE) © 2026

---

## 相关资源

- [Claude Code 官方文档](https://docs.claude.com/en/docs/claude-code)
- [Anthropic Skills 仓库](https://github.com/anthropics/skills)
- [Skill 编写指南](https://docs.claude.com/en/docs/claude-code/skills)
