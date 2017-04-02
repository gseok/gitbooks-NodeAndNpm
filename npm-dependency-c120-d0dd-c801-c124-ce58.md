##### node module dependency 선택적 설치

package.json에 명시된, dependency node module을 선택적으로 설치 할 수 있다.

```js
{
  ...
  "dependencies": {
    "bluebird": "^3.5.0",
    "locally": "^0.2.1"
  },
  "devDependencies": {
    "tslint": "^5.0.0"
  },
  ...
}
```



###### 전체 dependency 설치

```
$ npm install
```



###### dependency만 설치\(deploy시 필요한 dependency\)

```bash
$ npm install --only prod

또는

$ npm install --only production
```



###### devDependency만 설치

```
$ npm install --only dev

또는

$ npm install --only development
```



