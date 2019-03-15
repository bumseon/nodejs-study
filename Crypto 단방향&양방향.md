Crypto 단방향 암호화(해시)
======================

```javascript
const crypto = require('crypto');

console.log(crypto.createHash('sha512').update('qjatjs12!').digest('base64'));

s8qZFY9xNwLTBRLPiQdBytl3expbQ7HhDSv6ZRbFtjfDOGJxsR0VXUVVJN85bsFp6IgNNWXFIpkOjUAy1MtpiQ==
```

> 기본으로 제공하는 crypto module을 사용
> .update 부분에 비밀번호를 입력
> .digest 표시하고자 하는 방식을 입력하면 되는데 보통 base64를 사용한다.
> Hash값은 입력받은 값이 작을수록 충돌날 확률이 높아짐.

```javascript
example)

1234 = s8qZFY9xNwLTBRLPiQdB
5678 = s8qZFY9xNwLTBRLPiQdB
```

## pdkdf2 Algorithm

```javascript
const crypto = require('crypto');

crypto.randomBytes(64, (err, buf) => {
    const salt = buf.toString('base64');
    console.log('salt', salt);
});

salt /vfB/XkR866eIpfHxhMJCvo/KJIxCMVyQGNy2shxXlU6vQjbXbBE+kj1BKDVPmvkrb39qxHgef/Wo87vC69rmw==

-> random한 문자열 byte를 만듬.
-> 예제는 64byte 길이에 base64 기반으로 만듬.

crypto.randomBytes(64, (err, buf) => {
    const salt = buf.toString('base64');
    console.log('salt', salt);
    crypto.pbkdf2('qjatjs12!', salt, 100000, 64, 'sha512', (err, key) => {
    console.log('password', key.toString('base64'));
    });
});
```

> 해시 충돌 공격을 어렵게 하기 위해 salt(소금)이라는 문자열을 원래 비밀번호에 추가하고 iteration 횟수를 높인다.
> salt는 암호화된 비밀번호와 같이 저장하고, iteration은 1초 정도가 걸릴때까지 올려주면 좋다.
>현업에서는 bcrypt, scrypt를 많이 사용한다고 함. (시간이 되면 정리해보자 !)


Crypto 양방향
=============

```javascript
const crypto = require('crypto');

const cipher = crypto.createCipher('aes-256-cbc', '열쇠');
let result = cipher.update('qjatjs12!', 'utf8', 'base64');
result += cipher.final('base64');
console.log('암호', result);

const decipher = crypto.createDecipher('aes-256-cbc', '열쇠');
let result2 = decipher.update(result, 'base64', 'utf8');
result2 += decipher.final('utf8');
console.log('복호화', result2);
```

> '열쇠' key 값을 다른 곳에 유출하지 않으면, 다른 사용자가 이 암호를 해킹할 수 없다.
> 그래서 관리가 굉장히 중요함.
> 참고사이트 : https://nodejs.org/dist/latest-v10.x/docs/api/crypto.html