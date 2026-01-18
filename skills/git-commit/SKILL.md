---
name: git-commit
description: 处理git提交操作。当用户要求"提交commit"、"git提交"、"提交代码"或类似请求时触发。适用于所有git提交场景，包括使用MCP工具、命令行或其他git客户端。
allowed-tools: git, bash, git mcp, github mcp
---
# Git Commit Skill

## 快速要点
- **工具选择**：根据可用工具选择最合适的提交方式。优先使用 git 相关 MCP 工具（如 `git.*` 命令），如果没有则使用 git 原生命令行
- **提交信息**：确保提交信息准确、清晰地反映变更内容，遵循约定式提交规范
- **原子提交**：每次提交应包含一个逻辑上完整的变更，避免混合多个不相关的修改
- **变更检查**：提交前使用 `git status` 和 `git diff` 检查变更内容
- **工作流程**：适应不同的 git 工作流程（如 Git Flow、GitHub Flow 等）

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
- 在无法满足用户需求（无变更、冲突、工具报错等）时，提供下一步指引（例如"请先解决冲突再通知我继续提交"）
- 明确告知用户当前状态和需要采取的行动
- 提供具体的解决建议或替代方案
