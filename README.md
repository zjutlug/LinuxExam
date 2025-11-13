一键部署多台容器
可根据需要选择是否挂载 **/etc/container_id** 到宿主机
```bash
for i in {01..40}; do
    docker run -d \
      --add-host=host.docker.internal:host-gateway \
      --name linux-exam-node-${i} \
      --cpus=0.5 \
      --memory=512m \
      -p 200${i}:22 \
      -e API_BASE_URL=http://host.docker.internal:8888 \
      linux-exam-node:latest
done
```