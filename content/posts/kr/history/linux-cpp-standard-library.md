---
title: "리눅스의 C++ standard library 정리 그리고 Unreal project와의 이슈"
date: 2020-09-08T10:40:21+09:00
categories: ["linux"]
tags: ["linux", "standard libs", "history", "unreal"]
cover: ""
draft: false
---

## 개요
* C++ standard library 구현체에 관한 내용
* 관련해서 Unreal project와 third-party libraries 통합 이슈
***

## 간단 C Standard Library 정리

최초의 libc, 이것이 원래의 고대 표준 라이브러리 구현체입니다.
나중에 이것이 GNU의 C 라이브러리로 대체되는데 이것이 바로 glibc입니다.
현재의 주류 리눅스 운영체제는 glibc를 사용합니다.(데비안 계열 우분투도 2015년 이후로 glibc 사용)

glibc는 리눅스 시스템에서 가장 저수준의 API이며 거의 모든 runtime library가 glibc에 의존합니다. 예를 들면 c코드에서 fopen 함수를 사용하면 시스템에서 sys_open이 트리거 되고 중간 처리를 해주는 것이 glibc입니다.

glibc 자체는 시스템 호출을 캡슐화하는 것 말고도 문자열, malloc, linuxthread, locale, signal등과 같은 상위 레벨 응용 프로그램에 필요한 기능을 제공합니다.
***

## C++ Standard Library

C++ 코드를 작성하는 경우 libc++ / libstdc++라는 두 가지 다른 라이브러리가 있습니다. 이것이 언리얼에서 서드파티 모듈을 참조할 때 문제가 생기는 원인이죠.

libstdc++는 GCC(GNU Compiler Collection)와 연관된 라이브리입니다. 이것이 리눅스 환경에서의 디폴트 C++ Library이죠.
libc++는 clang 컴파일러를 위해 재작성된 C++ Standard Library입니다.
gcc와 libstdc++의 관계는 clang 및 libc++ 관계와 비슷합니다.

libstdc++와 gcc는 함께 번들로 제공되므로 gcc가 설치될 때 libstdc++가 설치됩니다.

참고로 glibc와 gcc가 함께 묶이지 않은 이유는 무엇일까요?
glibc와 비교하여 libstdc++는 표준 C++ 프로그램 라이브러리를 제공하지만 커널을 처리하지는 않습니다. 즉 추상화 수준이 다르죠. 시스템 수준 이벤트의 경우 libstdc++는 먼저 커널과 통신하기 전에 glibc와 상호 작용을 합니다. 아무튼 glibc와 비교할 때 libstdc++는 좀 더 상위 레벨이 라이브러리죠.
***

## 언리얼 프로젝트와 third-party libraries 통합 이슈
언리얼에서 쓰는 것은 libc++입니다.
라이선스 문제 때문에 libc++를 쓰는 것으로 압니다.
안드로이드 역시 libc++만 지원할 예정이죠.

리눅스는 libstdc++이 기본입니다.
libstdc++과 libc++ 이 둘은 Application Binary Interfaces가 호환되지 않습니다.
그 결과 서로 간의 컴파일된 바이너리가 상호 통신이 불가능하죠.

이것이 언리얼 프로젝트에 서드파티 라이브러리 플러그인들을 통합할 때 문제가 되는 이유입니다.
***

## 대처 방법
third-party libraries를 libc++로 컴파일해야 합니다.(가급적 엔진에 번들된 버전으로)
차후에 이것에 도움이 되는 괜찮은 Open Source 프로젝트를 소개해 드릴까 합니다.
***
😊