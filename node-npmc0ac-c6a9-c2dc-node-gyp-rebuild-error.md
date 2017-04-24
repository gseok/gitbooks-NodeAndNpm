##### \[Node\] npm사용시 node-gyp rebuild error

npm으로 node 모듈 설치시 node-gyp rebuild error가 간혹 발생하는 경우가 있다.

node-gyp는 사실 Node.js로 작성된 크로스 플랫폼 커맨드 라인 툴이다. 이 툴은 어떤 node 모듈이,  native 소스 코드와의 dependency가 존재하는 경우, 해당 모듈을 사용자의 환경에 맞게 모듈 인스톨 시점에 다시 빌드하여 설치하는 역할을 한다.

즉, 설치하려는 node 모듈이 사용하고 있는 라이브러리 프로그램을, 사용자의 플렛폼 환경에 맞게 다시 빌드하여, 정상 구동 되도록 하는 것이다. node-gyp rebuild error는 따라서, 사용자의 플렛폼 환경에 맞게 소스 빌드중 빌드 에러가 발생한 것이다.

node-gyp 자체는 플렛폼 별로 조금씩 다른 dependency를 가지고 있다. 하지만 공통적으로 python에 대한 dependency가 있다.

따라서 대다수의 node-gyp rebuild error의 경우, python에 대한 dependency을 맞추어 주는 것으로 해결 가능하다.

사실 node-gyp 공식 문서에 node-gyp에 대한 required를 잘 설명해 두었다.

참고: [node-gyp 공식 문서](https://www.npmjs.com/package/node-gyp)

**공통적으로 주의해야 할점**

* 반드시 python 2.7.x 버전을 설치해야 한다.
  * python의 경우, 2.x 버전과 3.x 버전의 api의 상호 호환이 어느 순간 깨졌다.
  * 따라서 python 2.x버전과 3.x버전은 사실 서로 다른 프로그램으로 개념을 잡아도 무방하다.
  * 참고: [python 2.7 & 3.x](http://blog-ko.python.org/2011/05/27-3x.html)

###### 해결 방법

**Linux \(ubuntu\)**

```bash
// python을 설치한다.
$ apt-get install python-2.7.0

// npm에 설치한 python을 config 세팅 해준다. 
$ npm config set python /etc/bin/python2.7
```

* ubuntu의 경우 make, gcc 는 기본적으로 존재한다.
* 만약 없다면 해당 make 와 gcc도 설치한다.

**Window**

```
// python을 설치한다.
Window의 경우 python을 다운받아서 설치 할 수 있는 프로그램 형태로 제공 된다.

1. 아래 사이트에서 2.7.x (여기서는 2.7.13)을 다운 받아서 설치한다.
https://www.python.org/downloads/release/python-2713/

2. window의 환경변수에 python을 추가한다.
정상적으로 추가해서, cmd(명령 프롬프트)에서 pyhton 명령어 수행시 정상적으로 프로그램이 동작해야 한다.

3. window의 경우, Visual C++ 에 대한 의존성이 있다.
- 이유는 linux에서의 make, gcc를 window에서는 visual c++로 사용되고 있기 때문이다.
- 따라서 window에서 make, gcc 컴파일러를 설치하면 된다.
- 공식 문서에는 두가지 옵션을 설명하고 있다.
  - a. Visual C++ Build Tools 을 설치한다.
  - b. Visual Studio 2015을 설치한다.
  - 추가로 window vita나 window 7의 경우 .NET Framework 4.5.1의 설치를 가이드 하고 있다.
  -- .NET은 Visual Studio진영에 또 의존성이 있다.
     (사실 윈도우 사용시 수많은 프로그램들이 .NET에 의존성이 있어서 이미 설치되어 있을 수도 있다.)
     
4. npm에 설치한 python을 config 세팅 해준다. (본인이 설치한 디렉토리로)
npm config set python c:\python\python2.7

5. npm에 설치한 visual studio을 config 세팅 해준다. 
npm config set msvs_version 2015
```

보통, 설치 이후 npm install 을 다시 시도해 보면, node-gyp rebuild가 정상적으로 수행 될 것이다.



참고: [node-gyp 공식 문서](https://www.npmjs.com/package/node-gyp)

참고: [python 2.7 & 3.x](http://blog-ko.python.org/2011/05/27-3x.html)



