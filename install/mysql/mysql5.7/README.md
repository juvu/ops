mysql5.7 安装指南

注意事项：
1. 使用docker-compose安装时, 请将 `mysqld.cnf` 文件copy至 `/docker/mysql5.7/conf/` 目录下
2. 如果docker logs mysql 出现Permission denied， 请执行`chown -R 999 /docker/mysql5.7/` 即可。 该问题产生的原因是：宿主机目录拥有者与容器对应目录组拥有者不同导致。可输入`docker run -ti --rm --entrypoint="/bin/bash" mysql:5.7 -c "ls -la /var/lib/mysql"`
