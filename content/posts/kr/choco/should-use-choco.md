---
title: "Choco 사용하기(Windows Package Manager)"
date: 2020-09-04T22:54:49+09:00
categories: []
tags: ["windows", "choco", "choco command"]
cover: ""
draft: false
---

## choco 설치


```powershell
# PowerShell 관리자 권한에서 진행
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```
***

## choco 명령어들

```powershell
# 지정한 패키지의 존재유무, 버전, Approved 날짜 확인
choco search vscode

# -e : 정확히 패키지명이 일치하는것만 검색
# -detail : Package parameters등 추가 정보 얻기
choco search vscode -exact --detail

# 패키지 설치
choco install vscode

# 설치 중 script 실행 여부 물어보는 것 yes 처리
choco install vscode --confirm

# 패키지 업그레이드
choco upgrade vscode

# 패키지 삭제
choco uninstall vscode
```
***

## Reference
[Chocolatey Official](https://chocolatey.org)
***
😊