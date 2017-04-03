##### Node.js 자동 재시작

node.js로 구현되어 있는 node app이 네트웍 장애나, 코딩 실수로 인한 exception 발생으로 인하여, 죽는 현상이 발생한 경우. 해당 app을 다시 실행해야 한다.

node.js의 모듈중에 app이 죽은 경우 자동으로 다시 시작해주는 forever라는 모듈이 존재한다.

해당 모듈을 사용하면, node.js의 app을 항상 keep alive로 \(살아있는 상태로\) 유지 할 수 있다.



###### 설치

```bash
$ npm install -g forever

또는

$ sudo npm install -g forever
```



###### 기본 사용

```bash
$ forever start app.js
```



###### 명령어를 추가한 사용

일반적으로는 기본사용만으로, 항상 재시작되는 node.js의 app을 볼 수 있다. 하지만, 작성한 node.js app이 추가적인 command가 필요한 경우, 명령어를 추가하여 사용 할 수 있다.

여기에서는 forever을 사용하여, app을 항상 node debug 모드로 자동 실행 하는 방법을 예시로 보여준다.

```bash
$ forever start -c 'node --debug' app.js

또는

$ forever start -c 'node --inspect' app.js
```



-c 는 COMMAND 옵션을 의미한다. 사실 기본적값으로 'node'로 실행되고 있다. 즉

```bash
$ forever start app.js

는 아래와 동일하다

$ forever start -c 'node' app.js
```



