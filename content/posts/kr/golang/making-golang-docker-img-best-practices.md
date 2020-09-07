---
title: "경량의 Golang-Docker Image 만들기"
date: 2020-09-07T17:22:00+09:00
categories: ["Golang"]
tags: ["한글", "Docker", "Golang", "Dockerfile", "best-practices", "go module"]
cover: ""
draft: false
---

Ping-Pong Webserver 구현

>Working Directory : go-docker  
사용 웹프레임워크 : gin-gonic

## main.go

```go
package main

import (
	"github.com/gin-gonic/gin"
)

func main() {
	//gin.SetMode(gin.ReleaseMode) 릴리즈 모드 활성화 하고 싶으면 주석 해제
	r := gin.Default()
	r.GET("/ping", func(c *gin.Context) {
		c.JSON(200, gin.H{
			"message": "pong",
		})
	})	
	r.Run(":3000") // port
}
```
***

## Go module 생성

```bash
go mod init go-docker
```
***

## Dockerfile 
> Working directory에 Dockerfile 생성

```dockerfile
FROM golang:alpine AS builder

ENV GO111MODULE=on \
    CGO_ENABLED=0 \
    GOOS=linux \
    GOARCH=amd64

WORKDIR /build

COPY go.mod go.sum main.go ./

RUN go mod download

RUN go build -o main .

WORKDIR /dist

RUN cp /build/main .

FROM scratch

COPY --from=builder /dist/main .

ENTRYPOINT ["/main"]
```
***

## 이미지 빌드 및 실행

```bash
docker build . -t go-dock
docker run -p 3000:3000 go-dock
```
***

## 테스트

```bash
curl http://localhost:3000/ping
```
***

## Reference
[Using Go Module](https://blog.golang.org/using-go-modules)  
[docker.com/blog](https://www.docker.com/blog/intro-guide-to-dockerfile-best-practices/)
***
😊