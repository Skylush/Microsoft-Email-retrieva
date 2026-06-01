# 📬 Microsoft Email Retrieva

> 一个极简专业的 Microsoft 1Acc 邮箱获取与管理工具

[![Node.js](https://img.shields.io/badge/Node.js-18+-339933?style=flat-square&logo=node.js&logoColor=white)](https://nodejs.org/)
[![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20Docker-lightgrey?style=flat-square)]()

---

## ✨ 功能特点

- **令牌自动刷新** — 使用 `refresh_token` 自动换取 `access_token`，无需手动干预
- **邮件管理** — 支持查看收件箱与垃圾邮件，单选或批量删除
- **响应式布局** — 完美适配桌面端与移动端
- **隐私安全** — 令牌仅在内存中使用，不持久化任何敏感信息
- **极简设计** — 清爽 UI，流畅操作体验

---

## 🚀 快速开始

### 方式一：本地运行

**环境要求**：Node.js 16+

```bash
# 克隆项目
git clone https://github.com/AlexVera0/Microsoft-Email-retrieva.git
cd Microsoft-Email-retrieva

# 安装依赖
npm install

# 启动服务
node api.js
```

访问 `http://localhost:3001`

---

### 方式二：Docker 部署（推荐）

**1. 在项目根目录创建 `Dockerfile`**

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install --production
COPY . .
EXPOSE 3001
CMD ["node", "api.js"]
```

**2. 构建并运行**

```bash
docker build -t ms-email .

docker run -d \
  --name ms-email \
  --restart unless-stopped \
  -p 33001:3001 \
  ms-email
```

访问 `http://服务器IP:33001`

---

### 方式三：Docker Compose

创建 `docker-compose.yml`：

```yaml
services:
  ms-email:
    build: .
    container_name: ms-email
    restart: unless-stopped
    ports:
      - "33001:3001"
```

```bash
docker compose up -d
```

---

### 方式四：PM2 守护进程（Linux 服务器）

```bash
# 安装 PM2
npm install -g pm2

# 启动服务
pm2 start api.js --name "ms-email"

# 开机自启
pm2 save && pm2 startup
```

---

## 📖 使用说明

1. **粘贴邮箱信息** — 在顶部输入框中按以下格式填入：
   ```
   邮箱----密码----ClientID----RefreshToken
   ```

2. **收取邮件** — 点击「点击收件」按钮开始同步

3. **切换文件夹** — 左侧边栏可在「收件箱」与「垃圾邮件」之间切换

4. **删除邮件** — 勾选邮件后点击「删除」，支持批量操作

---

## 🛠 技术栈

| 层级 | 技术 |
|------|------|
| 前端 | HTML5, CSS3, Vanilla JavaScript (ES6+) |
| 后端 | Node.js, Express, Axios |
| API  | Microsoft Graph API |
| 部署 | Docker / PM2 |

---

## 🔧 防火墙配置

确保服务器安全组已放行对应端口：

| 参数 | 值 |
|------|----|
| 协议 | TCP |
| 端口 | `3001`（本地）或自定义外部端口 |
| 来源 | `0.0.0.0/0` 或指定 IP |

---

## ⚠️ 免责声明

本工具仅用于学习与研究目的，请确保使用过程中遵守 [Microsoft 服务协议](https://www.microsoft.com/servicesagreement)。邮箱信息安全由使用者自行负责。

---

## 👤 作者

**AlexVera** · [GitHub](https://github.com/AlexVera0)

---

<p align="center">MIT License · © 2025 AlexVera</p>
