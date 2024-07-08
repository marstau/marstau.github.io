---
layout: post
title: golang在docker中运行
category: 编程开发
tags: php
keywords: 
description: 
---

```
// user-service/main.go
package main

import (
    "fmt"
    "net/http"
)

func main() {
    http.HandleFunc("/user", func(w http.ResponseWriter, r *http.Request) {
        fmt.Fprint(w, "Hello from User Service!")
    })

    http.ListenAndServe(":8081", nil)
}
```

```
// order-service/main.go
package main

import (
    "fmt"
    "net/http"
)

func main() {
    http.HandleFunc("/order", func(w http.ResponseWriter, r *http.Request) {
        fmt.Fprint(w, "Hello from Order Service!")
    })

    http.ListenAndServe(":8082", nil)
}
```

```
# user-service/Dockerfile
FROM golang:latest

WORKDIR /app

COPY . .

RUN go build -o user-service main.go

EXPOSE 8081

CMD ["./user-service"]
```

```
# order-service/Dockerfile
FROM golang:latest

WORKDIR /app

COPY . .

RUN go build -o order-service main.go

EXPOSE 8082

CMD ["./order-service"]
```

在每个微服务的目录中执行以下命令构建Docker镜像：

```
docker build -t user-service ./user-service
docker build -t order-service ./order-service
```

创建一个名为docker-compose.yml的文件，定义整个微服务架构。

```
# docker-compose.yml
version: '3'

services:
  user-service:
    image: user-service
    ports:
      - "8081:8081"

  order-service:
    image: order-service
    ports:
      - "8082:8082"
```

启动微服务：
```
docker-compose up
```

现在，用户服务将在`http://localhost:8081/user`上提供服务，订单服务将在`http://localhost:8082/order`上提供服务。


## Reference

* [Go和Docker部署微服务架构的详细教程](https://cloud.tencent.com/developer/article/2371379)

