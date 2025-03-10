# 教程
https://github.com/tech-shrimp/docker_image_pusher

# 从阿里云docker pull镜像报错
[root@localhost ~]# docker pull crpi-g05smmlotxjkdb8e.cn-hangzhou.personal.cr.aliyuncs.com/xxxxxx/alpine
Using default tag: latest
Error: remote trust data does not exist for crpi-g05smmlotxjkdb8e.cn-hangzhou.personal.cr.aliyuncs.com/xxxxxx/alpine: crpi-g05smmlotxjkdb8e.cn-hangzhou.personal.cr.aliyuncs.com does not have trust data for crpi-g05smmlotxjkdb8e.cn-hangzhou.personal.cr.aliyuncs.com/xxxxxx/alpine
# 解决方法，设置环境变量来禁用内容信任，这样运行的Docker pull命令将不会进行内容信任验证
# 临时允许未签名的镜像
[root@localhost ~]# export DOCKER_CONTENT_TRUST=false
# 永久设置
[root@localhost ~]# echo "export DOCKER_CONTENT_TRUST=false" >>.bashrc
[root@localhost ~]# source ~/.bashrc
# 允许使用未签名的镜像源
[root@localhost ~]# echo '{"insecure-registries": ["your-registry-address:port"]}' >/etc/docker/daemon.json
# 启动Docker守护进程时添加--insecure-registry
[root@localhost ~]# vim /usr/lib/systemd/system/docker.service
ExecStart=/usr/bin/dockerd --insecure-registry your-registry-address:port
