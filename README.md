# docker


# 创建自定义镜像

```bash
# 1. 创建空目录，并创建Dockerfile
mkdir test
cd test
touch Dockerfile
touch .dockerignore

# 2. 构建
docker build -t btpka3/my-img:1.0 .

# 3. 检查本地的images
docker images

# 4. 运行
docker run -d btpka3/my-img:1.0
```