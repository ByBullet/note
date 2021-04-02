> 查看doker匿名挂载的位置
>  1. docker ps：查看运行的容器
>  2. docker inspect 容器名 / 容器id
>  3. 在Mounts中的Destination是虚拟机的挂载点
>  4. Source是实体机挂载点
****
> 配置docker远程访问
> 1. 编辑`vim /usr/lib/systemd/system/docker.service`文件
> 2. 修改`ExecStart=/usr/bin/dockerd -H tcp://0.0.0.0:2375 -H unix:///var/run/docker.sock"`
> 3. 重新加载配置文件
`systemctl daemon-reload` 
> 4. 重启docker `systemctl start docker`
> 5. 查看端口2375是否开启`netstat -nptl`
****
> 修改docker镜像源
> 1. 修改或添加`/etc/docker/daemon.json`
> 2. 内容为 ```{
"registry-mirrors": ["http://hub-mirror.c.163.com"]}```
> 3. 执行 `systemctl restart docker.service` 