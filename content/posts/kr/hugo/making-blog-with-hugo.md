---
title: "Hugo로 github에 블로그 만들기"
date: 2020-09-05T22:22:00+09:00
categories: ["Hugo"]
tags: ["한글", "hugo", "휴고", "GitHub", "blog"]
cover: ""
draft: false
---

윈도우즈 기준, Choco를 통한 설치를 추천  
**[Choco 설치](/posts/kr/choco/should-use-choco)**
***

## Hugo 설치
```Powershell:
choco install hugo -confirm
```
***

## Git Repository 2개 생성

* `<USERNAME>.github.io-project`  
contents(md, image, css등) **<proj_repo>**

* `<USERNAME>.github.io`  
위의 저장소를 빌드한 실제 site **<deploy_repo>**
***

## hugo site 생성

```powershell
# C:\Users\username\Hugo\Sites를 Working Dictory로 사용
cd $env:USERPROFILE
md Hugo\Sites
cd Hugo\Sites

hugo new site <deploy_repo>
# ex : hugo new site thesora.github.io
```
***

## <proj_repo>에 Hugo contents 및 themes 가져오기
```powershell
cd $env:USERPROFILE

# <proj_repo> clone
git clone <USERNAME>.github.io-project

# 방금 Hugo를 통해 만들 Site안의 내용물들 <proj_repo> 여기로 복사
Copy Hugo\Sites\<proj_repo>\* <USERNAME>.github.io-project

# clone 한 곳에서 작업
cd <USERNAME>.github.io-project

# themes 받기, 여기서는 ananke 테마 사용
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke

# theme 설정
echo 'theme = "ananke"' >> config.toml

# blog post 하나 작성
hugo new posts/my-first-post.md
```
***

## Github에 호스팅 해보기
```powershell
# 서버 띄워 보기
hugo server -D -t ananke

# http://localhost:1313/ 잘 되면 Ctrl+C로 Server 중지 후에
# public 폴더 정리
rd Public -Recurse

# <deploy_repo>를 <proj_repo>를 submodule 추가하여 관리하는 것이 좋음
git submodule add -b master https://github.com/<USERNAME>/<USERNAME>.github.io.git public

#####################################################################
# config.toml baseURL을 <USERNAME>.github.io로 직접 에디터로 업데이트
#####################################################################

# 빌드를 위해 다시 <proj_repo>로
cd ..

# 빌드
hugo -t ananke

# <deploy_repo> 변경 사항 업데이트
cd public
git add .
git commit -m "first"
git push origin master

# 마지막으로 <proj_repo>의 변경 사항도 업데이트
cd ..
git add .
git push origin master
```
***

## Git Pages 설정
https://github.com/\<USERNAME\>/\<USERNAME\>.github.io/settings로 이동하여  
[GitHub Pages]에서
* Source를 master로
* Select folder를 /(root)로 변경
***

## 테스트
웹브라우저상에서 \<USERNAME\>.github.io로 접속 시도
***

## Reference
[Hugo Official](https://gohugo.io)  
[Github-Pages Official Guide](https://docs.github.com/en/github/working-with-github-pages/getting-started-with-github-pages)
***
😊