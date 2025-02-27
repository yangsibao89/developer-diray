# Podman Usage

## 1. Podman install
1. `podman machine set --rootful=true` 设置 root权限
2. `podman machine set --user-mode-networking=true` 将会生成一个新的wsl实例
3. `wsl -l -v` 查看实例

## 2. 直接使用 terminal 进入podman-net-usermode 便是使用system proxy的模式

## 3. Podman set registries
1. `sudo yum update ca-certificates` 更新linux ssl证书
1. 注意代理模式，不能是黑名单模式
1. podman login docker.io username password

## 4. Podman install mysql
1. `podman search --filter is-official=true mysql`
1. `podman pull docker.io/library/mysql:latest`
```
podman run -d \
  --name podman-mysql \
  -e MYSQL_ROOT_PASSWORD=root \              # 设置 root 密码（替换为实际值）
  -p 3306:3306 \                              # 映射宿主机 3306 端口到容器
  -v D:\workspace\Data\podman-mysql:/var/lib/mysql \              # 持久化数据卷
  mysql:latest \
  --character-set-server=utf8mb4 \            # 可选：设置字符集
  --collation-server=utf8mb4_unicode_ci
```
# Day2 appending:
1. 查看wsl实例位置
   1. win+r regedit `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Lxss`

2. wsl实例如果移动过位置，需要修改权限
   1. ext4.vhdx文件修改权限，properties -> security -> edit -> Authenticated User and Full Control

3. wsl -l -v 查看状态
4. wsl -d podman-machine-default or podman machien start