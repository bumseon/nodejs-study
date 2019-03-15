OS Module
===========

> 자주 사용하는 OS Module을 연습

<pre><code>
> os.arch()
'x64'

> os.platform()
'win32'

> os.type()
'Windows_NT'

> os.uptime()
270569
-> process.uptime()과 다른점은 현재 운영체제가 켜지고 얼마나 시간이 지났는지 확인할 수 있음.

> os.hostname()
'HONG-PC'

> os.release()
'10.0.17134'

> os.homedir()
'C:\\Users\\audgn'

> os.tmpdir()
'C:\\Users\\audgn\\AppData\\Local\\Temp'

> os.freemem()
9552912384

> os.totalmem()
17005105152

> os.cpus()
[ { model: 'Intel(R) Core(TM) i7-8550U CPU @ 1.80GHz',
    speed: 1992,
    times:
     { user: 3661656,
       nice: 0,
       sys: 3135031,
       idle: 33292875,
       irq: 591078 } },
  { model: 'Intel(R) Core(TM) i7-8550U CPU @ 1.80GHz',
.....
</code></pre>

> process 명령어와 유사한 것이 많은 것 같다.