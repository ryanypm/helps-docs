# 前端打包启动



## 从1Panel
1. 点击菜单 `容器`
2. 点击tab `容器`
3. 点击 `创建容器`
4. 填写 `容器名称`
5. 选择 `nginx` 镜像(没有去 `容器` -> `镜像`，点击拉取镜像)
6. 填写`暴露端口`
7. 选择挂载卷
    1. `/nginx.conf` ~ `/etc/nginx/nginx.conf`
    2. `./dist` ~ `/usr/share/nginx/html`
    3. `./logs` ~ `/var/log/nginx`
8. 点击保存并启动

## 从服务器启动
1. 进入服务器 ssh root@xx.xx.xx.xx
2. 进入项目目录
3. 执行 `npm run build`
4. 确保`docker-compose.yml`在项目目录中
4. 执行 `docker-compose up -d`