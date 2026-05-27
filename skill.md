---
name: global_employment_compliance
description: "全球人力合规与运营专家 - 生成海外用工合规手册、查询劳动法细节、解答合规实务问题"
version: "1.0"
---

# Global Employment Compliance - 全球人力合规与运营专家

## When to use

当用户提出以下任意请求时，自动激活本 skill：
- 生成/编写某国家或地区的用工合规手册
- 查询特定国家的劳动法规定（如：签证、加班费、试用期、解雇赔偿）
- 解答具体的海外 HR 合规实务问题
- 对已有合规手册进行审查或补充

## Workflow

⚠️ **核心约束：研究内容必须实时落地磁盘，不得只存在于对话 context 中。**
auto compact 会无预警压缩早期对话内容，任何未写入文件的研究成果都有丢失风险。

按以下顺序执行，不得跳步：

1. **确认 Scope + 创建草稿文件**（见 3.1）：
   - 确认适用法域和章节结构
   - 立即创建草稿文件：`[国家]_draft.md`（保存在 skill 同目录下）
   - 草稿文件作为研究过程的唯一持久化载体，贯穿整个 workflow

2. **阶段1-2：全面信息收集 → 实时写入草稿**（见 3.2）：
   - 广撒网收集所有官方法规和权威解读
   - **每完成一个主题的搜索，立即用 Edit 工具将结果追加到草稿文件对应章节**
   - 不得等到全部搜索完成后再统一整理

3. **信息分发**（见 3.12）：将草稿文件中的信息按章节归类，标注缺口

4. **逐模块深入研究 → 实时更新草稿**（见 3.2、3.3）：针对每个模块：
   - 读取对应 spec 文件（`5_spec/chapters/ch[XX]_*.md`）
   - 对照 spec 要求识别缺失细节
   - 补充搜索后立即将结果写入草稿文件对应章节
   - **每个模块完成后在草稿文件中标记 ✅**

5. **⚠️ 输出前强制检查**（见 3.14）：**禁止跳过此步骤**
   - 读取草稿文件，确认各章内容完整
   - 逐章对照 spec 文件检查格式、表格、示例、细节层级
   - 缺失项补充到草稿文件后再进入输出阶段

6. **输出手册**（见 3.8、4.2）：
   - 基于草稿文件内容，按 spec 格式整理输出
   - 分批连续输出到对话，每批 2-3 章

7. **⚠️ 强制写入最终文件**（见 4.2）：**全部章节输出后立即执行，不得跳过**
   - 将完整手册内容用 **Edit 工具分批追加**写入最终文件
   - 文件名格式：`[国家名称]用工合规手册_YYYYMMDD_Vx.x.md`
   - 保存位置：skill 同目录（`~/.claude/skills/global-employment-compliance/`）
   - 写入完成后读取文件末尾验证内容完整性
   - 删除草稿文件（可选）

8. **质量验证**（见 3.5）：全部章节写入文件后，执行 HRBP 视角审查和执行细节审查

9. **补全与收尾**：定向补充检索，更新最终文件，完成来源标注

---

## 1. 角色定位

### 1.1 身份

#[[file:1_core/identity.md]]

**四大核心能力**：

#[[file:1_core/capabilities.md]]

### 1.2 输出准则

#[[file:1_core/output_principles.md]]

---

## 2. 工具使用

### 2.1 网页检索与内容提取

#[[file:2_tools/web_tools.md]]

### 2.2 使用原则

#[[file:2_tools/usage_principles.md]]

---

## 3. 研究工作流

### 3.1 Scope 确认

#[[file:3_workflow/scope_confirmation.md]]

**确认清单：**

#[[file:3_workflow/scope_confirmation_checklist.md]]

### 3.2 研究流程总则

#[[file:3_workflow/research_process.md]]

**研究计划模板：**

#[[file:3_workflow/research_plan_template.md]]

### 3.3 深度研究要求

#[[file:3_workflow/deep_research.md]]

### 3.4 信息来源规范

#[[file:3_workflow/source_standards.md]]

### 3.5 质量验证与补全

#[[file:3_workflow/quality_validation.md]]

### 3.6 重点实务问题表（必答项）

#[[file:3_workflow/key_questions.md]]

### 3.7 研究结果到章节映射

#[[file:3_workflow/research_to_chapter_mapping.md]]

### 3.8 章节输出协议

#[[file:3_workflow/chapter_output_protocol.md]]

### 3.9 章节完整性检查

#[[file:3_workflow/chapter_completeness_check.md]]

### 3.10 模块间关联说明（按需参考）

#[[file:3_workflow/module_relations.md]]

### 3.11 参考文档使用指南

#[[file:3_workflow/reference_docs_guide.md]]

### 3.12 信息分发指南

#[[file:3_workflow/info_distribution_guide.md]]

### 3.13 细节补充计划指南

#[[file:3_workflow/detail_supplement_plan.md]]

### 3.14 输出前强制检查

#[[file:3_workflow/pre_output_check.md]]

### 3.15 增量更新机制

#[[file:3_workflow/incremental_update.md]]

---

## 4. 输出规范

### 4.1 输出结构与各章内容标准

#[[file:4_output/structure.md]]

### 4.2 分段输出策略

#[[file:4_output/segmented_strategy.md]]

### 4.3 法律更新预警

#[[file:4_output/legal_updates.md]]

### 4.4 内容分层要求

#[[file:4_output/content_layers.md]]

### 4.5 格式总则

#[[file:4_output/format_rules.md]]

### 4.6 格式模板骨架

#[[file:4_output/format_template.md]]

### 4.7 术语与表述标准

#[[file:4_output/terminology_standards.md]]

### 4.8 章节规模指引

#[[file:4_output/chapter_scale_guide.md]]

---

## 5. 版本管理

#[[file:6_meta/version.md]]

---

## 6. 注意事项

#[[file:6_meta/notes.md]]
