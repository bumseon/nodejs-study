URL Module
===========

## URL Module
![urlmoduleImage](./img/urlmodule.png "URL Module")

> ������ ���� ����� �ּ� ü�� (url.parse)
> �Ʒ��� WHATWG ����� �ּ� ü�� (url.URL)
> ���� �Ѵ� ������ �ϸ�, url.parse�� ȣ��Ʈ�� ���� ���� �� �� �ְ�, WHATWG ���(url.URL)�� search ó���� ���ϴ�.

<pre><code>
audgn@HONG-PC MINGW64 /c/algorithm (master)
$ node var
new URL(): URL {
  href:
   'https://guide.luniverse.io/docs/wallet-bridge-%EC%9D%B4%EC%9A%A9%ED%95%98%EA%B8%B0',
  origin: 'https://guide.luniverse.io',
  protocol: 'https:',
  username: '',
  password: '',
  host: 'guide.luniverse.io',
  hostname: 'guide.luniverse.io',
  port: '',
  pathname: '/docs/wallet-bridge-%EC%9D%B4%EC%9A%A9%ED%95%98%EA%B8%B0',
  search: '',
  searchParams: URLSearchParams {},
  hash: '' }
url.format(): https://guide.luniverse.io/docs/wallet-bridge-%EC%9D%B4%EC%9A%A9%ED%95%98%EA%B8%B0
</code></pre>

> ��� searchParams�� �޼���� FormData�� URLSearchParams ��ü���� ����ϰ� ���δ�.

```javascript
example )

const url = require('url');

const URL = url.URL;
const myURL = new URL('https://search.naver.com/search.naver?where=nexearch&query=%ED%8A%B8%EC%99%80%EC%9D%B4%EC%8A%A4&ie=utf8&sm=tab_lve');

console.log('searchParams:', myURL.searchParams);

searchParams: URLSearchParams {
  'where' => 'nexearch',
  'query' => 'Ʈ���̽�',
  'ie' => 'utf8',
  'sm' => 'tab_lve' }

console.log('searchParams.getAll():', myURL.searchParams.getAll('category'));

searchParams.getAll(): []
-> getAll�� �ϸ�, category value�� ���ļ� ��µ�.

console.log('searchParams.get():', myURL.searchParams.get('limit'));

searchParams.get(): null

console.log('searchParams.has():', myURL.searchParams.has('page'));

searchParams.has(): false

console.log('searchParams.keys():', myURL.searchParams.keys());

searchParams.keys(): URLSearchParams Iterator { 'where', 'query', 'ie', 'sm' }

console.log('searchParams.values():', myURL.searchParams.values());

searchParams.values(): URLSearchParams Iterator { 'nexearch', 'Ʈ���̽�', 'utf8', 'tab_lve' }

myURL.searchParams.append('filter', 'es3');  //  &filter=es3
myURL.searchParams.append('filter', 'es5');  //  &filter=es3&filter=es5
console.log(myURL.searchParams.getAll('filter'));

[ 'es3', 'es5' ]

myURL.searchParams.set('filter', 'es6');    //  ������ �ִ� ���� ����� set -> &filter=es6
console.log(myURL.searchParams.getAll('filter'));

[ 'es6' ]


console.log('searchParams.toString():', myURL.searchParams.toString());
myURL.search = myURL.searchParams.toString();

searchParams.toString(): where=nexearch&query=%ED%8A%B8%EC%99%80%EC%9D%B4%EC%8A%A4&ie=utf8&sm=tab_lve&filter=es6

-> filter�� �߰��� URL�� ��µ�.

myURL.searchParams.delete('filter');
console.log(myURL.searchParams.getAll('filter'));

[ ] 

console.log('searchParams.toString():', myURL.searchParams.toString());
myURL.search = myURL.searchParams.toString();

searchParams.toString(): where=nexearch&query=%ED%8A%B8%EC%99%80%EC%9D%B4%EC%8A%A4&ie=utf8&sm=tab_lve

-> filter�� ������ URL�� ��µ�.
```

## TIPS

<pre><code>
https://search.naver.com/search.naver?where=nexearch&query=%ED%8A%B8%EC%99%80%EC%9D%B4%EC%8A%A4&ie=utf8&sm=tab_lve

���� URL ����� (URL.parse)  ������ �������� ���� ���

/search.naver?where=nexearch&query=%ED%8A%B8%EC%99%80%EC%9D%B4%EC%8A%A4&ie=utf8&sm=tab_lve

��ó�� ������ URL�� ǥ�õ� �� ����.
�̷� ��쿡�� url.URL (WHATWG) ����� ����� �� ���� ������
�ΰ��� ��� ���ǰ� ����.
</code></pre>

