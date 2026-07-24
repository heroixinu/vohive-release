# VoHive Release

VoHive 4G/5G 模组管理平台 — 二进制发布与安装脚本仓库。

## 一键安装（裸机）

```bash
wget -O - https://raw.githubusercontent.com/heroixinu/vohive-release/master/install.sh | sh
```

或：

```bash
curl -fsSL https://raw.githubusercontent.com/heroixinu/vohive-release/master/install.sh | bash
```

安装完成后访问 `http://服务器IP:7575`，默认账号 `admin / admin`。

## 一键启动（Docker）

```bash
mkdir -p vohive && cd vohive

# 下载 docker-compose.yml
curl -fsSL -o docker-compose.yml \
  https://raw.githubusercontent.com/heroixinu/vohive-release/master/docker-compose.yml

# 创建配置文件
mkdir -p config data logs
cat > config/config.yaml << 'EOF'
server:
  port: 7575
  debug: false

web:
  username: admin
  password: admin123

devices: []

vowifi:
  enabled: false

webhook:
  enabled: false
EOF

# 登录 GHCR（镜像为私有）
echo "YOUR_GITHUB_TOKEN" | docker login ghcr.io -u heroixinu --password-stdin

# 启动
docker compose up -d
```

访问 `http://服务器IP:7575`，默认账号 `admin / admin123`。

## Docker 镜像

| 镜像 | 说明 |
|------|------|
| `ghcr.io/heroixinu/vohive:v1.6.0` | 指定版本 |
| `ghcr.io/heroixinu/vohive:latest` | 最新版本 |

```bash
docker pull ghcr.io/heroixinu/vohive:v1.6.0
```

## 卸载

```bash
wget -O - https://raw.githubusercontent.com/heroixinu/vohive-release/master/uninstall.sh | sh
```

## 默认安装目录

| 路径 | 说明 |
|------|------|
| `/opt/vohive/bin/vohive` | 二进制文件 |
| `/opt/vohive/config/config.yaml` | 配置文件 |
| `/opt/vohive/data` | 数据目录 |
| `/opt/vohive/logs` | 日志目录 |

## 源码仓库

https://github.com/heroixinu/vohive2
