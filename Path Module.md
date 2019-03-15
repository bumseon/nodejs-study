Path Module
===========

> 실제로 가장 많이쓰는 Module이라고 한다.

<pre><code>
> const path = require('path')
> path
{ resolve: [Function: resolve],
  normalize: [Function: normalize],
  isAbsolute: [Function: isAbsolute],
  join: [Function: join],
  relative: [Function: relative],
  toNamespacedPath: [Function: toNamespacedPath],
  dirname: [Function: dirname],
  basename: [Function: basename],
  extname: [Function: extname],
  format: [Function: format],
  parse: [Function: parse],
  sep: '\\',
  delimiter: ';',
  win32: [Circular],
  posix:
   { resolve: [Function: resolve],
     normalize: [Function: normalize],
     isAbsolute: [Function: isAbsolute],
     join: [Function: join],
     relative: [Function: relative],
     toNamespacedPath: [Function: toNamespacedPath],
     dirname: [Function: dirname],
     basename: [Function: basename],
     extname: [Function: extname],
     format: [Function: format],
     parse: [Function: parse],
     sep: '/',
     delimiter: ':',
     win32: [Circular],
     posix: [Circular],
     _makeLong: [Function: toNamespacedPath] },
  _makeLong: [Function: toNamespacedPath] }
</code></pre>

## 명령어

<pre><code>
const path = require('path');console.log(path.dirname(__filename));
console.log(path.extname(__filename));
console.log(path.basename(__filename));

path.parse(__filename));

C:\algorithm
.js
var.js
{ root: 'C:\\',
  dir: 'C:\\algorithm',
  base: 'var.js',
  ext: '.js',
  name: 'var' }

-> parse : 위에 구조로 분해를 해주고

console.log(path.format({
  root: 'C:\\',
  dir: 'C:\\algorithm',
  base: 'var.js',
  ext: '.js',
  name: 'var' 
}));

-> format : 위에 구조를 합쳐줌.

# normalize

console.log(path.normalize('C:\\algorithm//var.js'));
C:\algorithm\var.js

-> 인자가 잘못된 경로를 설정해도 경로를 제대로 만들어서 출력해줌

# isAbsolute

console.log(path.isAbsolute('C:\\algorithm//var.js'));
true
-> 현재 입력된 경로가 절대 경로인지 확인할 수 있다.

# relative

console.log(path.relative('C:\\algorithm//var.js', 'C:\\'));
..\..

-> 현재 입력된 경로로부터 다음 인자값에 경로를 찾아갈 수 있는 상대 경로를 출력

# join
console.log(path.join(__dirname, '..', '..', '/node1', '.', 'geth'));
C:\node1\geth

-> 절대 경로를 무시하고 합침

console.log(path.join(__dirname, '..', '..', '..', '/node1', '.', 'geth'));
C:\node1\geth

-> 존재하지 않는 경로까지 .. 상위 디렉토리로 이동해도 루트 경로 C:\을 벗어나지 않고 값을 출력함.


# resolve
console.log(path.resolve(__dirname, '..', '..', '/node1', '.', 'geth'));
C:\node1\geth

-> 절대 경로 고려하고 합침
-> '..', '..'로 이동해도 절대경로인 C:/node1로 이동함.
-> 예를들어 '..'을 한번 이동하면 C:\algorithm 이지만 '/node1'로 값을 주면 C:\algorithm\node1이 아닌 절대 경로 C:\node1로 찾아간다.
-> join은 상대경로 인식, resolve는 절대 경로를 인식한다.
</code></pre>