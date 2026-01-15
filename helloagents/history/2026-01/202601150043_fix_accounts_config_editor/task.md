# 任务清单: 修复“账户配置 JSON 无法输入新增账号”

目录: `helloagents/plan/202601150043_fix_accounts_config_editor/`

> 轻量迭代：仅包含 task.md；完成后需迁移至 `helloagents/history/2026-01/`。

---

## 1. 前端交互修复
- [√] 1.1 修复 `frontend/src/views/Accounts.vue`：当账户配置为空时，账户配置 JSON 面板默认允许编辑（不进入脱敏只读）
- [√] 1.2 修复 `frontend/src/views/Accounts.vue`：在脱敏只读模式下增加提示文案，降低误解成本

## 2. Docker 回归验证
- [√] 2.1 执行 `docker compose up -d --build` 重新构建并启动
- [?] 2.2 登录管理面板后进入「账号管理」→「账户配置」，确认可输入 JSON 并保存成功（会触发 `PUT /admin/accounts-config`）
- [?] 2.3 刷新页面确认配置仍存在（验证写入 `data/accounts.json` 生效）

## 3. 知识库同步
- [√] 3.1 更新 `helloagents/wiki/modules/frontend.md` 记录账户配置编辑模式规则与提示
- [√] 3.2 更新 `helloagents/CHANGELOG.md` 记录本次修复
