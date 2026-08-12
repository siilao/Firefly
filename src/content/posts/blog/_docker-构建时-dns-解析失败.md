---
title: Docker 构建时 DNS 解析失败
published: 2026-08-12
updated: 2026-08-12
description: Docker 构建时 DNS 解析失败
image: api
tags:
  - Docker
category: 问题百出
draft: false
author: 杨了个羊
---
**症状：**
```
Temporary failure resolving 'deb.debian.org'
```
**原因：** Docker 容器内 DNS 未配置，无法解析域名。
**解决：**
```
# 给 Docker daemon 配 DNS
echo '{"dns":["8.8.8.8","1.1.1.1"]}' > /etc/docker/daemon.json
systemctl restart docker

# 重新构建
cd /home/docker/telegram/189video
docker compose build --no-cache
```
