# frontend

## 目的
提供内置管理面板 UI（账号管理、系统设置、监控与日志等）。

## 模块概述
- **职责:** 管理端 UI、与后端管理 API 通信、提供公开监控页面路由
- **状态:** ✅稳定
- **最后更新:** 2026-01-15

## 规范
### 需求: 构建产物由后端托管
**模块:** frontend
前端通过 Vite 构建后输出到仓库根目录 `static/`，由后端 FastAPI 挂载并提供 `/` 入口访问。

#### 场景: Docker 多阶段构建
- 条件：执行 `docker build` 或 `docker compose up --build`
- 预期结果：构建阶段生成 `static/` 产物，运行阶段容器内 `/app/static` 可用于对外提供页面

### 需求: 账户配置 JSON 可编辑（首次添加）
**模块:** frontend
当系统无任何账户配置时，账户配置（JSON）面板应默认允许编辑，以便首次添加账号；当已有配置时，默认以脱敏只读展示，并提示用户点击“显示原文”后编辑。

#### 场景: 首次添加账号
- 条件：`/admin/accounts-config` 返回空数组
- 预期结果：点击「账户配置（JSON）」后可直接输入 JSON；保存按钮可用

#### 场景: 已存在账号配置
- 条件：`/admin/accounts-config` 返回非空数组
- 预期结果：默认脱敏只读并显示提示；点击“显示原文”后可编辑并保存

## 依赖
- Vue 3 / Vite

## 变更历史
- [202601142359_local_docker_deploy](../../history/2026-01/202601142359_local_docker_deploy/) - 修复容器化构建的前端产物复制路径
- [202601150043_fix_accounts_config_editor](../../history/2026-01/202601150043_fix_accounts_config_editor/) - 修复账户配置 JSON 在空配置时不可编辑的问题
