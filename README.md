# Dockerfiles
powerful docker tools


# 配置docker 加速器 加速地址=
docker-machine ssh default
sudo sed -i "s|EXTRA_ARGS='|EXTRA_ARGS='--registry-mirror=加速地址 |g" /var/lib/boot2docker/profile
exit
docker-machine restart default

# or
# 创建一台安装有Docker环境的Linux虚拟机，指定机器名称为default，同时配置Docker加速器地址。
docker-machine create --engine-registry-mirror=加速地址 -d virtualbox default  
# 查看机器的环境配置，并配置到本地。然后通过Docker客户端访问Docker服务。
docker-machine env default eval "$(docker-machine env default)" docker info