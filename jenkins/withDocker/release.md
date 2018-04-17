發佈專案使用 docker
-------------------

建置 image
----------

複製 task/[release](../task/release)

```
docker build --no-cache -t localhost:5000/sailssample .
docker push localhost:5000/sailssample:latest

docker rm -f sample
docker run -d -p 3333:1337 --link mysql --name sample localhost:5000/sailssample
```
