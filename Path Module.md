Path Module
===========

> ������ ���� ���̾��� Module�̶�� �Ѵ�.

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

## ��ɾ�

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

-> parse : ���� ������ ���ظ� ���ְ�

console.log(path.format({
  root: 'C:\\',
  dir: 'C:\\algorithm',
  base: 'var.js',
  ext: '.js',
  name: 'var' 
}));

-> format : ���� ������ ������.

# normalize

console.log(path.normalize('C:\\algorithm//var.js'));
C:\algorithm\var.js

-> ���ڰ� �߸��� ��θ� �����ص� ��θ� ����� ���� �������

# isAbsolute

console.log(path.isAbsolute('C:\\algorithm//var.js'));
true
-> ���� �Էµ� ��ΰ� ���� ������� Ȯ���� �� �ִ�.

# relative

console.log(path.relative('C:\\algorithm//var.js', 'C:\\'));
..\..

-> ���� �Էµ� ��ηκ��� ���� ���ڰ��� ��θ� ã�ư� �� �ִ� ��� ��θ� ���

# join
console.log(path.join(__dirname, '..', '..', '/node1', '.', 'geth'));
C:\node1\geth

-> ���� ��θ� �����ϰ� ��ħ

console.log(path.join(__dirname, '..', '..', '..', '/node1', '.', 'geth'));
C:\node1\geth

-> �������� �ʴ� ��α��� .. ���� ���丮�� �̵��ص� ��Ʈ ��� C:\�� ����� �ʰ� ���� �����.


# resolve
console.log(path.resolve(__dirname, '..', '..', '/node1', '.', 'geth'));
C:\node1\geth

-> ���� ��� ����ϰ� ��ħ
-> '..', '..'�� �̵��ص� �������� C:/node1�� �̵���.
-> ������� '..'�� �ѹ� �̵��ϸ� C:\algorithm ������ '/node1'�� ���� �ָ� C:\algorithm\node1�� �ƴ� ���� ��� C:\node1�� ã�ư���.
-> join�� ����� �ν�, resolve�� ���� ��θ� �ν��Ѵ�.
</code></pre>