# Docker Compose 部署指南

## 环境准备
- 安装 Docker Engine 20.10+ 及 Docker Compose 插件（或独立版 `docker-compose` ≥1.29）。
- 准备 Supabase 项目，并获取 `VITE_SUPABASE_URL` 与 `VITE_SUPABASE_ANON_KEY`。
- 推荐在服务器上创建 `.env` 文件管理密钥，避免直接写入 `docker-compose.yml`。

## 构建与启动
```bash
docker-compose up --build -d
```
该命令会读取项目内的 `Dockerfile` 构建镜像、安装依赖，并在容器中启动前端服务。镜像构建阶段会自动执行 `npm run build-index`，生成最新的 `public/dictionary/index.json`。默认监听 `5173` 端口，可通过反向代理暴露为 `https://your-domain`。

## 环境变量配置
`docker-compose.yml` 使用环境变量注入 Supabase 凭证，部署前需正确配置：
```bash
export VITE_SUPABASE_URL=https://your-project.supabase.co
export VITE_SUPABASE_ANON_KEY=public-anon-key
docker-compose down
docker-compose up --build -d
```
或在仓库根目录创建 `.env` 文件，示例：
```env
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_ANON_KEY=public-anon-key
```

## 运维常用命令
- 查看容器状态：
  ```bash
  docker-compose ps
  ```
- 实时查看运行日志：
  ```bash
  docker-compose logs -f web
  ```
- 在容器内执行一次性命令（如对词典原始数据做增量更新后，手动刷新索引）：
  ```bash
  docker-compose exec web npm run build-index
  ```
- 停止服务并释放资源：
  ```bash
  docker-compose down
  ```

