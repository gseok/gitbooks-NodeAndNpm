##### package.json에 node module 관련 dependency 자동 추가



npm을 이용하여, node module을 추가하는 것은 아래와 같이 매우 간단하다.

```bash
$ npm install <node_module_name>

e.g)
$ npm install lodash
```

하지만, node module을 추가한 이후 package.json을 설정해야 한다.

npm에서는 npm을 이용하여 node moudle을 추가할때, 추가와 동시에 **package.json에 dependency을 자동으로 추가**하는 옵션을 제공하고 있다.



###### denpendency 추가

```bash
$ npm install --save <node_module_name>

e.g)
$ npm install --save bluebird
```



###### devDependency 추가

```bash
$ npm install --save-dev <node_module_name>

e.g)
$ npm install --save-dev tslint
```



package.json을 열어보면 자동으로 node\_module에 대한 dependency가 추가되었음을 살펴 볼 수 있다.

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



dependency와 devDependency의 구분은 일반적으로, 다음과 같다.

dependency는 deploy시에 실제 해당 프로그램에서 필요로 하는 module이다.

devDependency는 deploy시에는 필요하지 않지만, 개발 도중에는 필요로 하는 module이다.

\(e.g. tslint같은 linter나 unit test의 module이 될 수 있겠다.\)



