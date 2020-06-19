
## Docker Compose 常用命令与配置

### 常见命令

- ps：列出所有运行容器

`docker-compose ps`

- logs：查看服务日志输出

`docker-compose logs`

- port：打印绑定的公共端口，下面命令可以输出 eureka 服务 8761 端口所绑定的公共端口

`docker-compose port eureka 8761`

build：构建或者重新构建服务
docker-compose build
start：启动指定服务已存在的容器
docker-compose start eureka
stop：停止已运行的服务的容器
docker-compose stop eureka
rm：删除指定服务的容器
docker-compose rm eureka
up：构建、启动容器
docker-compose up
kill：通过发送 SIGKILL 信号来停止指定服务的容器
docker-compose kill eureka
pull：下载服务镜像
scale：设置指定服务运气容器的个数，以 service=num 形式指定
docker-compose scale user=3 movie=3
run：在一个服务上执行一个命令
docker-compose run web bash

docker-compose.yml 属性
version：指定 docker-compose.yml 文件的写法格式
services：多个容器集合
build：配置构建时，Compose 会利用它自动构建镜像，该值可以是一个路径，也可以是一个对象，用于指定 Dockerfile 参数
build: ./dir
---------------
build:
    context: ./dir
    dockerfile: Dockerfile
    args:
        buildno: 1
command：覆盖容器启动后默认执行的命令
command: bundle exec thin -p 3000
----------------------------------
command: [bundle,exec,thin,-p,3000]
dns：配置 dns 服务器，可以是一个值或列表
dns: 8.8.8.8
------------
dns:
    - 8.8.8.8
    - 9.9.9.9
dns_search：配置 DNS 搜索域，可以是一个值或列表
dns_search: example.com
------------------------
dns_search:
    - dc1.example.com
    - dc2.example.com
environment：环境变量配置，可以用数组或字典两种方式
environment:
    RACK_ENV: development
    SHOW: 'ture'
-------------------------
environment:
    - RACK_ENV=development
    - SHOW=ture
env_file：从文件中获取环境变量，可以指定一个文件路径或路径列表，其优先级低于 environment 指定的环境变量
env_file: .env
---------------
env_file:
    - ./common.env
expose：暴露端口，只将端口暴露给连接的服务，而不暴露给主机
expose:
    - "3000"
    - "8000"
image：指定服务所使用的镜像
image: java
network_mode：设置网络模式
network_mode: "bridge"
network_mode: "host"
network_mode: "none"
network_mode: "service:[service name]"
network_mode: "container:[container name/id]"
ports：对外暴露的端口定义，和 expose 对应
ports:   # 暴露端口信息  - "宿主机端口:容器暴露端口"
- "8763:8763"
- "8763:8763"
links：将指定容器连接到当前连接，可以设置别名，避免ip方式导致的容器重启动态改变的无法连接情况
links:    # 指定服务名称:别名 
    - docker-compose-eureka-server:compose-eureka
volumes：卷挂载路径
volumes:
  - /lib
  - /var
logs：日志输出信息
--no-color          单色输出，不显示其他颜.
-f, --follow        跟踪日志输出，就是可以实时查看日志
-t, --timestamps    显示时间戳
--tail              从日志的结尾显示，--tail=200