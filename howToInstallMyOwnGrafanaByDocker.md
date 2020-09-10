## grafana docker 部署日志

1. 从源码打docker包

```bash
cd GoPorjs/src/github.com/grafana/grafana
make build-docker-full
```
其中可能会因为本机分配给docker的内存不够导致的失败，需要把docker可用的内存调整到8G

2. 从docker images保存镜像包
先docker images 查询grafana/grafana:dev的image id
```bash
docker images
```
然后保存镜像包
```bash
docker save -o grafana-0.1.2.tar imageId
```

3. 把镜像包导入服务器
首先上传刚才的tar包到服务器上，随后导入到docker中
```bash
docker load < grafana-0.1.2.tar
```
但是这样导入的镜像没有repo和tag，所以要手动设置
```bash
docker tag imageId grafana/grafana:dev
```

4. 启动docker镜像
```bash
docker run -d -p 3000:3000 --name=grafana -e "GF_AUTH_ANONYMOUS_ENABLED=true" grafana/grafana:dev
```
其中-e表示设置环境变量 GF_AUTH_ANONYMOUS_ENABLED=true 可以使查看面板免登陆