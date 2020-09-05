---
title: "Choco를 사용하기"
date: 2020-09-04T22:54:49+09:00
categories: []
tags: []
cover: ""
draft: false
---

See [MarkdownTest](/posts/markdown-template)

## 개요

Chocolatey는 The Package Manager for Windows 입니다. Linux의 APT와 동일한 기능을 하는 Windows의 패키지 매니저 입니다.

일반적으로 dockerize나 기타 Automation 과정에서 패키지의 command-line 명령을 통한 패키지 관리는 필수인데 Windows에서는 Chocolatey(이하 choco)를 사용하면 됩니다.

쓰다보면 편해서 일반적으로 사용하는 윈도 어플도 저는 choco를 사용해서 설치하고 있습니다.

## choco 설치

```powershell
# On PowerShell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```
## choco로 패키지 제어하기
```powershell
# 관리자 권한 필요
# 패키지(VSCode) 설치
choco install vscode

# 패키지 설치 중에 y 누르기 귀찮다 &amp;&amp; 믿을 만한 곳에서 배포한다면
choco install vscode -y

# 패키지 업그레이드
choco upgrade vscode

# 패키지 삭제
choco uninstall vscode</pre>
```
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>간단합니다.<br>관리자 권한이 필요함에 유의하세요.</p>
<!-- /wp:paragraph -->

<!-- wp:separator -->
<hr class="wp-block-separator"/>
<!-- /wp:separator -->

<!-- wp:heading -->
<h2>패키지 검색</h2>
<!-- /wp:heading -->

<!-- wp:syntaxhighlighter/code {"language":"powershell","lineNumbers":false,"makeURLsClickable":false} -->
<pre class="wp-block-syntaxhighlighter-code"># 패키지 명과 버전, Approved 날짜 확인 가능
choco search vscode</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>설치하고자 하는 패키지들은 한번 쯤 <br><a href="https://chocolatey.org/">https://chocolatey.org/</a> 오피셜 사이트에서 확인해 보는 것도 좋습니다.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>패키지가 테스트를 통과했는지, 어떤 파라메터를 추가해서 설치할 수 있는지 등등을 확인해 볼 수 있습니다.</p>
<!-- /wp:paragraph -->

<!-- wp:separator -->
<hr class="wp-block-separator"/>
<!-- /wp:separator -->

<!-- wp:heading -->
<h2>잡설</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>제 경우 최근에 컴퓨터 포맷할 일이 생겼을 때<br>포맷 전 다시 설치해야 할 윈도우 어플리케이션들을<br>미리 리스팅 해서 배치 파일로 작성해 두었습니다.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>윈도우 재설치 후 배치 파일을 실행하여<br>어플리케이션들을 신속히 설치할 수 있었습니다.</p>
<!-- /wp:paragraph -->

<!-- wp:syntaxhighlighter/code {"language":"bash","lineNumbers":false,"makeURLsClickable":false} -->
<pre class="wp-block-syntaxhighlighter-code"># EssentialAppInstall.bat

choco install notepadplusplus -y
choco install dngrep -y
choco install geforce-game-ready-driver -y
choco install 7zip -y
choco install golang -y
choco install microsoft-windows-terminal -y
choco install googlechrome -y
...</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:separator -->
<hr class="wp-block-separator"/>
<!-- /wp:separator -->

<!-- wp:heading {"level":4} -->
<h4>Reference</h4>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p id="block-60bd0242-6459-4ea3-932b-65d1ee88df63"><a href="https://chocolatey.org/">https://chocolatey.org/</a></p>
<!-- /wp:paragraph -->

