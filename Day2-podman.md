# Podman Usage

## 1. Podman pull images && run container
1. `podman pull quay.io/fedora/mysql-80`
2. `podman run -d --name mysql_podman -e MYSQL_ROOT_PASSWORD=root -p 3306:3306 <imageId>`