# 变更提案: 本地 Docker 部署（可直接启动）

## 需求背景
当前项目已提供 Dockerfile 与 docker-compose，但在本地执行 `docker compose up --build` 时会因前端构建产物目录不一致导致构建失败，影响本地部署体验。

## 变更内容
1. 修复 Dockerfile 前端构建产物复制路径，使多阶段构建可成功完成。
2. 增加 `.dockerignore`，避免将本地密钥与运行数据打进镜像，并缩小构建上下文。
3. 补充文档，提供 `docker compose` 的推荐启动方式。

## 影响范围
- **模块:** deployment / frontend / backend
- **文件:** `Dockerfile`, `.dockerignore`, `README.md`, `docs/README_EN.md`
- **API:** 无（仅部署与文档改动）
- **数据:** 无（仍使用 `./data:/app/data` 作为持久化）

## 核心场景

### 需求: 本地 Docker 一键启动
**模块:** deployment
使项目在本地 Docker Desktop 环境下可直接构建并运行，且提供可验证的访问入口。

#### 场景: 使用 docker compose 构建并启动
在仓库根目录执行：
- `docker compose up -d --build`

预期结果：
- 构建成功且容器处于 `Up` 状态
- 访问 `http://localhost:7860/` 返回管理面板页面
- 访问 `http://localhost:7860/public/uptime` 返回 JSON

## 风险评估
- **风险:** `.env` 中包含 `ADMIN_KEY` 等敏感信息，误提交可能造成泄露
- **缓解:** `.env` 已在 `.gitignore` 中忽略；Docker 构建通过 `.dockerignore` 排除 `.env`

