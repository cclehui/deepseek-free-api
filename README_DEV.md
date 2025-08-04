
## 原生部署

请先安装好Node.js环境并且配置好环境变量，确认node命令可用。

安装依赖

```shell
npm i

```

安装PM2进行进程守护

```shell
npm i -g pm2
```

编译构建，看到dist目录就是构建完成

```shell
# build
npm run build

# start app
npm run start

# build and start
npm run build && npm run start
```

启动服务

```bash
# dev start (easy start)
node dist/index.js

```

```bash
# manage by pm2
pm2 start dist/index.js --name "deepseek-free-api"

pm2 list

# see logs
pm2 logs deepseek-free-api

pm2 reload deepseek-free-api
pm2 stop deepseek-free-api
pm2 delete  deepseek-free-api
```

### 请求测试
```bash
curl http://127.0.0.1:8000/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer 4HYJXb56Y2A3McWOnFgqF+o3wz2urG6vgAQ87+aa6H+dYio0pFn1gaEnBtp7Wfay" \
  -d '{
    "model": "deepseek",
    "messages": [
      {"role": "user", "content": "Explain quantum computing in simple terms."}
    ],
    "stream": false
  }'
```