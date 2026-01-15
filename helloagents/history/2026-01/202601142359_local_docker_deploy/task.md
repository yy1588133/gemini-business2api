# 任务清单: 本地 Docker 部署（可直接启动）

目录: `helloagents/plan/202601142359_local_docker_deploy/`

---

## 1. deployment
- [√] 1.1 修复 `Dockerfile` 中前端构建产物复制路径，保证 `docker compose up --build` 可成功构建
- [√] 1.2 新增 `.dockerignore`，排除 `.env`、`data/`、`logs/` 等本地内容进入镜像

## 2. docs
- [√] 2.1 更新 `README.md` 补充 `docker compose` 启动方式
- [√] 2.2 更新 `docs/README_EN.md` 补充 `docker compose` 启动方式
- [√] 2.3 更新 `.env.example`，移除与代码不一致的哈希示例说明

## 3. 验证
- [√] 3.1 执行 `docker compose up -d --build` 并确认容器启动成功
- [√] 3.2 验证 `GET /` 与 `GET /public/uptime` 可访问

## 4. 知识库
- [√] 4.1 初始化 `helloagents/` 知识库并记录本次变更

