##### node.js nodemon을 통한 개발중 app 자동 재시작

개발이 종료되어 서비스 되고 있는 `node app`의 경우 `forever`을 사용해서 자동 재시작 하는 방법을 이전 포스트에서 소개한 적이 있다.

\(참고: [node.js forever을 통한 app 자동 재시작](http://gseok.tistory.com/entry/Node-nodejs-forever을-통한-app-자동-재시작)\)

`forever`의 경우는, `node` 서버가 죽지 않고, 항상 살아있게 \(`keep alive`\) 하는 동작을 담당하는 형태이다. 이와 다르게 `node app` 개발중에, 빈번하게 수정되는 수정코드의 실제 구동 상황을, 별도의 `node` 재시작 없이 자동으로 재시작 하고 싶은 경우가 존재한다.

즉 node app 개발 중, 소스코드 수정하고 나면, 자동으로 서버를 재시작해서, 변경된 소스가 반영된 형태의 node app이 바로 구동되게 해주는 `nodemon` 이라는 모듈이 존재한다.



###### 설치

```bash
$ npm install -g nodemon

or

$ npm install nodemon --save-dev
```



###### 기본 사용

```bash
$ nodemon app.js
```



###### app.js에 arguments을 넘기는 사용

```
$ nodemon app.js localhost 8080
```



###### node을 debug모드로 구동되게 사용

```
$ nodemon --debug app.js 80
```



이외, --wath 옵션을 사용해서 multiple한 file의 수정을 감지해서, 자동으로 node을 재시작 하는 것도 가능.

또한,  --delay 옵션을 사용해서, 코드 수정수 서버 재시작시, 바로 재시작 하지 않고, 일정 시간의 delay 이후 재시작 하도록 하는 것도 가능.

위와 같은 고급 사용들은 [nodemon의 공식 document](https://github.com/remy/nodemon#nodemon)을 참고



