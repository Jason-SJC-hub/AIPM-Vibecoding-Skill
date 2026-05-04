# AIPM-Vibecoding-Skill

> vibecoding 专用 Skill 库，沉淀面向 AI 编程助手的产品、需求、执行与交付方法。

这个仓库用于开源和维护一组 AIPM / vibe coding 场景下可直接安装使用的 Skill。它的目标不是写给人看的传统方法论文档，而是把实际项目中反复验证过的工作流、提问方式、验收标准和交付护栏，整理成 AI 编程助手可以稳定调用的操作说明。

当前版本首先开源的是 `vibe-coding-prd`：一个专门帮助用户生成“AI 可直接执行”的 vibe coding PRD 的 Skill。

## 这个仓库解决什么问题

vibe coding 的核心风险不是“AI 不会写代码”，而是“需求没有被写成 AI 可以稳定执行的形式”。传统 PRD 往往允许模糊表达，例如“界面更现代”“支持 @ 提及”“体验顺滑一点”。这些描述给人看可以开会补齐，给 AI 执行时却很容易产生自由发挥。

这个仓库希望把产品思路转成更适合 AI 执行的材料：

- 明确上下文、目标用户、业务边界和成功标准
- 明确必须做、不能做、暂缓做的范围
- 明确视觉、行为、数据、技术约束
- 明确可观测的验收标准
- 明确 AI 不应该越界发挥的护栏
- 用可复用 Skill 把这些流程固化下来

## 当前包含的 Skill

### `vibe-coding-prd`

`vibe-coding-prd` 用于生成给 Claude Code、Cursor 等 AI 编程助手直接执行的 PRD。它不是传统团队评审 PRD，而是面向 AI 落地的执行说明。

核心流程：

1. 前置信息确认：确认产品目标、用户、平台、功能范围和约束
2. 产品架构确认：先形成一屏产品结构草图，避免直接进入细节
3. PRD 分模块撰写：逐个确认 Context、Scope、Specification、Acceptance、Guardrails
4. 自查与二次确认：用检查清单找出模糊点、缺口和 AI 可能误解的位置

适用场景：

- 你有一个产品想法，希望交给 Claude Code 或 Cursor 实现
- 你不是工程师，但希望把需求写到 AI 能执行的粒度
- 你已经有 BRD、MRD、idea、notes，希望整理成开发 PRD
- 你希望减少“AI 做偏了”“越做越复杂”“返工很多”的情况

不适用场景：

- 纯 debug 现有代码
- 修改已有 PRD 的局部文字
- 市场分析或商业判断
- 只问某个技术问题，例如部署、框架选择、报错排查

## 安装方式

把本仓库 clone 到你的 Codex / Claude Code skills 目录下即可。

Codex 示例：

```bash
git clone https://github.com/sjchahalife-cmd/AIPM-Vibecoding-Skill.git ~/.codex/skills/vibe-coding-prd
```

Windows PowerShell 示例：

```powershell
git clone https://github.com/sjchahalife-cmd/AIPM-Vibecoding-Skill.git "$env:USERPROFILE\.codex\skills\vibe-coding-prd"
```

安装后目录中应直接包含：

```text
SKILL.md
README.md
VERSION
CHANGELOG.md
examples/
templates/
```

## 使用方式

安装后，在支持 Skill 的 AI 编程环境中输入：

```text
/vibe-coding-prd
```

或：

```text
/vcprd
```

也可以直接说：

```text
帮我写一份给 Claude Code 用的 vibe coding PRD
```

Skill 会通过分步对话引导你补齐信息，并在关键节点等待确认。

## 文件结构

```text
AIPM-Vibecoding-Skill/
├── SKILL.md
├── README.md
├── VERSION
├── CHANGELOG.md
├── agents/
│   └── openai.yaml
├── examples/
│   ├── web-tool.md
│   ├── ios-app.md
│   └── miniprogram.md
└── templates/
    └── prd-template.md
```

## 维护约定

每次更新这个仓库时，都必须同步检查并更新以下文件：

- `README.md`：说明新增、删除或变更了什么，让第一次打开仓库的人能理解当前状态
- `CHANGELOG.md`：记录版本变化和重要调整
- `VERSION`：按语义化版本更新版本号
- `SKILL.md`：如果触发逻辑、流程、约束或输出标准发生变化，必须同步更新
- `examples/` 和 `templates/`：如果 Skill 的使用方式变化，示例和模板也要同步

推荐提交前检查：

```bash
python ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py .
```

在 Windows 上如果遇到中文编码问题，可以使用：

```powershell
$env:PYTHONUTF8='1'
python "$env:USERPROFILE\.codex\skills\.system\skill-creator\scripts\quick_validate.py" .
```

## 开源说明

本仓库完全开源，供 AIPM、独立开发者、产品经理和 vibe coding 用户自由学习、安装、修改和复用。

本仓库使用 [MIT License](./LICENSE)。

## 版本

当前版本见 [VERSION](./VERSION)。

变更历史见 [CHANGELOG.md](./CHANGELOG.md)。

## 作者与定位

这个仓库来自 AIPM / vibe coding 实践沉淀，面向希望用 AI 编程助手更稳定交付产品的人。

它会持续演进为一个 vibecoding 专用 Skill 库，而不只是单个 PRD Skill。
