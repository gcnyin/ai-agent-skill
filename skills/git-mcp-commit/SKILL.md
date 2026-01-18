---
name: git-mcp-commit
description: 使用git提交commit。当用户要求"提交 commit"、"git 提交"、"提交代码"时触发。
allowed-tools: git mcp, github mcp, bash
---
# MCP Git Commit Skill

## 快速要点
- 优先通过 MCP 的 `git.*` 命令处理版本控制，如果没有 git 相关 MCP，就使用 git 原生命令行进行操作。

## 提交信息（Commit Message）

### 用户未提供提交信息时
当用户未提供 commit message 时，**必须由 AI 自动分析变更内容并生成简洁合适的提交信息**。

### 生成提交信息的步骤
1. **分析变更类型**：通过 `git diff` 或 `git status` 了解变更内容，判断类型：
   - `feat`: 新功能
   - `fix`: bug 修复
   - `refactor`: 代码重构
   - `docs`: 文档更新
   - `style`: 代码格式调整（不影响功能）
   - `test`: 测试相关
   - `chore`: 构建/工具链变更

2. **遵循约定式提交格式**（可选但推荐）：
   ```
   type(scope): description

   [可选的详细说明]
   ```

3. **撰写原则**：
   - 使用祈使句（如 "Add user login" 而非 "Added user login"）
   - 一句话概括核心变更
   - 默认使用英文，用户明确要求时使用中文
   - 简洁明了，避免冗余

### 示例
- `feat(auth): add user login functionality`
- `fix(api): resolve timeout issue in data fetch`
- `refactor(user): simplify validation logic`
- 添加用户登录功能（用户要求中文时）

## 沟通建议
- 在无法满足用户需求（无变更、冲突、MCP 报错）时，提供下一步指引（例如"请先解决冲突再通知我继续提交"）。
