# deployment

## 目的
统一记录本项目在本地系统使用 Docker / docker compose 的部署方式与注意事项。

## 模块概述
- **职责:** 构建镜像、启动容器、端口与数据卷配置、常见排障
- **状态:** ✅稳定
- **最后更新:** 2026-01-14

## 规范
### 需求: 一条命令启动
**模块:** deployment
在仓库根目录执行 `docker compose up -d --build` 可完成构建与启动。

#### 场景: 首次启动
- 条件：创建 `.env` 并设置 `ADMIN_KEY`
- 预期结果：容器 `Up`，本地 `http://localhost:7860/` 可访问

## 关键文件
- `Dockerfile`：前后端多阶段构建
- `docker-compose.yml`：端口映射、环境变量文件、数据卷挂载
- `.dockerignore`：构建上下文裁剪

## 常见问题
- 容器启动即退出：检查 `ADMIN_KEY` 是否配置（未配置会直接退出）。
- 构建失败提示找不到前端产物：检查 Dockerfile 是否从前端构建阶段复制正确目录（Vite 默认输出到 `static/`）。

## 变更历史
- [202601142359_local_docker_deploy](../../history/2026-01/202601142359_local_docker_deploy/) - 本地 Docker 部署完善与验证

