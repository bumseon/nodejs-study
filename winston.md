winston
========

> 실제 서버 운영 시 console.log와 console.error를 대체하기 위한 모듈 
> console.log와 console.error를 사용하면 개발 중에는 편리하게 서버의 상황을 파악할 수 있지만 
> 실제 배포 시에는 console 객체의 메서드들이 언제 호출되었는지 파악하기 힘들 뿐만 아니라 서버가 종료되는 순간 로그들도 사라져 버리는 문제점이 있음

로그를 파일이나 다른 데이터베이스에 저장해야 할 때 winston을 사용한다.
------------------------------------------------------------------

<pre><code>
$ npm i winston
</code></pre>


### winston을 설치한 뒤, logger.js를 작성한다.

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
 
### winston 패키지의 createLogger 메서드로 logger를 만들면 인자로 logger에 대한 설정을 넣어줄 수 있으며, 설정으로는 level, format, transports 등이 있다.

* level은 로그의 심각도를 의미하며, error, warn, info, verbose, debug, silly가 있다 ( 심각도순으로 error가 가장 심각 )
* format은 로그의 형식을 의미하며, json, label, timestamp, printf, simple, combine 등의 다양한 형식이 있다.
* transports는 로그 저장 방식을 의미하며, new transports.File은 파일로 저장한다는 뜻이고, new transports.Console은 콘솔에 출력한다는 뜻이다.

## winston-daily-rotate-file 패키지도 있다. (로그를 날짜별로 관리할 수 있게 해주는 패키지 )