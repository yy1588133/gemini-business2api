# backend

## 目的
提供 OpenAI 兼容 API 与管理面板后端能力（FastAPI）。

## 模块概述
- **职责:** 请求鉴权、账号池调度、OpenAI 兼容响应封装、公开监控与管理端点
- **状态:** ✅稳定
- **最后更新:** 2026-01-14

## 规范
### 需求: 本地 Docker 部署可直接启动
**模块:** backend
在容器环境下默认监听 `0.0.0.0:${PORT:-7860}`，并能正确托管前端静态资源。

#### 场景: 使用 docker compose 启动
- 条件：设置 `ADMIN_KEY` 且映射端口 `7860:7860`
- 预期结果：容器启动后访问 `/` 返回管理面板页面，访问 `/public/uptime` 返回 JSON

## API接口
详见 `helloagents/wiki/api.md`。

## 数据模型
详见 `helloagents/wiki/data.md`。

## 依赖
- `core/*`：账号池/鉴权/配置等
- `util/*`：工具函数

## 变更历史
- [202601142359_local_docker_deploy](../../history/2026-01/202601142359_local_docker_deploy/) - 修复 Dockerfile 前端产物复制路径并完善 Docker 部署

