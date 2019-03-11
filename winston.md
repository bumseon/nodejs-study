winston
========

> ���� ���� � �� console.log�� console.error�� ��ü�ϱ� ���� ��� 
> console.log�� console.error�� ����ϸ� ���� �߿��� ���ϰ� ������ ��Ȳ�� �ľ��� �� ������ 
> ���� ���� �ÿ��� console ��ü�� �޼������ ���� ȣ��Ǿ����� �ľ��ϱ� ���� �Ӹ� �ƴ϶� ������ ����Ǵ� ���� �α׵鵵 ����� ������ �������� ����

�α׸� �����̳� �ٸ� �����ͺ��̽��� �����ؾ� �� �� winston�� ����Ѵ�.
------------------------------------------------------------------

<pre><code>
$ npm i winston
</code></pre>


### winston�� ��ġ�� ��, logger.js�� �ۼ��Ѵ�.

<pre><code>
const { createLogger, format, transports } = require('winston');

const logger = createLogger({
  level: 'info',
  format: format.json(),
  transports: [
    new transports.File({ filename: 'combined.log' }),
    new transports.File({ filename: 'error.log', level: 'error' }),
  ],
});

if (process.env.NODE_ENV !== 'production') {
  logger.add(new transports.Console({ format: format.simple() }));
 }
 
 module.exports = logger;
 </code></pre>
 
### winston ��Ű���� createLogger �޼���� logger�� ����� ���ڷ� logger�� ���� ������ �־��� �� ������, �������δ� level, format, transports ���� �ִ�.

* level�� �α��� �ɰ����� �ǹ��ϸ�, error, warn, info, verbose, debug, silly�� �ִ� ( �ɰ��������� error�� ���� �ɰ� )
* format�� �α��� ������ �ǹ��ϸ�, json, label, timestamp, printf, simple, combine ���� �پ��� ������ �ִ�.
* transports�� �α� ���� ����� �ǹ��ϸ�, new transports.File�� ���Ϸ� �����Ѵٴ� ���̰�, new transports.Console�� �ֿܼ� ����Ѵٴ� ���̴�.

## winston-daily-rotate-file ��Ű���� �ִ�. (�α׸� ��¥���� ������ �� �ְ� ���ִ� ��Ű�� )