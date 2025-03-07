# 教程
https://github.com/tech-shrimp/docker_image_pusher

# 从阿里云docker pull镜像报错
[root@localhost ~]# docker pull crpi-g05smmlotxjkdb8e.cn-hangzhou.personal.cr.aliyuncs.com/xwupiaomiao/alpine
Using default tag: latest
Error: remote trust data does not exist for crpi-g05smmlotxjkdb8e.cn-hangzhou.personal.cr.aliyuncs.com/xwupiaomiao/alpine: crpi-g05smmlotxjkdb8e.cn-hangzhou.personal.cr.aliyuncs.com does not have trust data for crpi-g05smmlotxjkdb8e.cn-hangzhou.personal.cr.aliyuncs.com/xwupiaomiao/alpine
# 解决方法，设置环境变量来禁用内容信任，这样运行的Docker pull命令将不会进行内容信任验证
[root@localhost ~]# export DOCKER_CONTENT_TRUST=false  
[root@localhost ~]# docker pull docker pull crpi-g05smmlotxjkdb8e.cn-hangzhou.personal.cr.aliyuncs.com/xwupiaomiao/alpine
