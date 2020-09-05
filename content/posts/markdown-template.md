---
title: "Markdown Template"
date: 2020-09-04T22:52:30+09:00
draft: false
---


   <pre><code class="lang-Powershell">Set-VMFirmware -VMName &quot;VMname&quot; -EnableSecureBoot Off</code></pre> 


<!--다른 페이지로 링크 걸기-->
<!--See [gRPC Concepts](/../test/test)-->

<!--아이콘 링크-->
[![Join the chat at https://gitter.im/grpc/grpc](https://badges.gitter.im/grpc/grpc.svg)](https://gitter.im/grpc/grpc?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

<!--표 만들기-->
| Language                | Source                              |
|-------------------------|-------------------------------------|
| Shared C [core library] | [src/core](src/core)                |
| C++                     | [src/cpp](src/cpp)                  |
| Ruby                    | [src/ruby](src/ruby)                |
| Python                  | [src/python](src/python)            |
| PHP                     | [src/php](src/php)                  |
| C# (core library based) | [src/csharp](src/csharp)            |
| Objective-C             | [src/objective-c](src/objective-c)  |


<!--아래 둘다 H1-->
# Unreal Engine
Unreal Engine
=============

<!--일반 텍스트-->
Welcome to the Unreal Engine source code! 

<!--리스트-->
* [Unreal Engine Programming Guide](https://docs.unrealengine.com/latest/INT/Programming/index.html)
* [Unreal Engine API Reference](https://docs.unrealengine.com/latest/INT/API/index.html)

[Youtube](https://www.youtube.com/?hl=ko&gl=KR "이것은 하이퍼링크의 설명을 작성할 수 있습니다.")

<!--아래 둘다 H2-->
## Branches
Branches
--------

We publish source for the engine in several branches:

<!--볼드체하면서 링크-->
The **[release branch](https://github.com/EpicGames/UnrealEngine/tree/release)** is extensively tested by our QA team and makes a great starting point for learning the engine or
making your own games. We work hard to make releases stable and reliable, and aim to publish new releases every few months.

<!--단순 볼드체-->
Individual teams have their own **development branches** for day to day work

<!--H3-->
### Windows

<!--넘버링 리스트-->
1. Install **[GitHub for Windows](https://windows.github.com/)** then **[fork and clone our repository](https://guides.github.com/activities/forking/)**. 
   
1. Install **Visual Studio 2017**. 
   All desktop editions of Visual Studio 2017 can build UE4, including [Visual Studio Community 2017](http://www.visualstudio.com/products/visual-studio-community-vs)
  
1. Open your source folder in Explorer and run **Setup.bat**.    
   
`Mark인용코드1`

<code>Tag인용 코드1</code>

<pre>Tag인용 코드2</pre>

<pre><code>Tag인용 코드3</code></pre>

```
// Fenced **with** highlighting
function doIt() {
    for (var i = 1; i <= slen ; i^^) {
        setTimeout("document.z.textdisplay.value = newMake()", i*300);
        setTimeout("window.status = newMake()", i*300);
    }
}
```

```html:hello.html
<div>
 <p>Hello, LYNMP!</p>
</div>
```
<!DOCTYPE html>
<html>
<head>
<title>Page Title</title>
</head>
<body>
```

#### **`hello_world.css`**
```css
int main()
{
  cout << "Hello World!" << endl;
}
```

```cpp:cpp
int main()
{
  cout << "Hello World!" << endl;
}
```

```bash
cd test
```

```cs
public void int main () {
   return 0;
}
```
```go
func main() {
	// Instantiate default collector
	c := colly.NewCollector(
}
```

```ini
DEFAULT_WAIT_TIME = 10
```

```lang-Powershell
# onPowerShell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

```python:hello.py
for i in range(height,0,-1):
    print(i* ' ' + (height+1-i) * '*')
```

> 인용구

<Blockquote>
인용구 내용
</Blockquote>

| <center>제목1</center> | 제목2 | 제목3 | <center>제목1</center> |
| :- | - | :-: | -: |
| 내용1입니다 | 내용2입니다 | 내용3입니다 | 내용4입니다 |
| 내용1 | 내용2 | 내용3 | 내용4 |

| 제목1 | 제목2 | 제목3 | 제목4 |
| :---- | ------ | :----------: | --------------------: |
| 내용1입니다 | 내용2입니다 | 내용3입니다 | 내용4입니다 |
| 내용1 | 내용2 | 내용3 | 내용4 |

---
***
* * * * * * * * * * * * * * * * * * * * * * * * * * * 

윈도우키 + .

윈도우키 + ;

😊❤😒
😁❤😒😊❤💕

![ImageExample](https://github.com/WonHeeSoo/GitBook_StudyBook/blob/master/image/Image%20Example.PNG?raw=true)

[![BTS DNA Youtube](https://img.youtube.com/vi/MBdVXkSdhwU/0.jpg)](https://www.youtube.com/watch?v=MBdVXkSdhwU)

[![Young Marco](https://i.vimeocdn.com/video/625196300_560x290.jpg)](https://vimeo.com/209607366)

[TOC], [toc]

Velog[^1]는 Velog입니다.
[^1]:Velig는 블로그 프레임워크입니다.

Typing an @ symbol, followed by a username, will
notify that person to come and view the comment.
This is called an “@mention”, because you’re
mentioning the individual. You can also @mention
teams within an organization.