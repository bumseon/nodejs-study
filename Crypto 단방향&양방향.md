Crypto �ܹ��� ��ȣȭ(�ؽ�)
======================

```javascript
const crypto = require('crypto');

console.log(crypto.createHash('sha512').update('qjatjs12!').digest('base64'));

s8qZFY9xNwLTBRLPiQdBytl3expbQ7HhDSv6ZRbFtjfDOGJxsR0VXUVVJN85bsFp6IgNNWXFIpkOjUAy1MtpiQ==
```

> �⺻���� �����ϴ� crypto module�� ���
> .update �κп� ��й�ȣ�� �Է�
> .digest ǥ���ϰ��� �ϴ� ����� �Է��ϸ� �Ǵµ� ���� base64�� ����Ѵ�.
> Hash���� �Է¹��� ���� �������� �浹�� Ȯ���� ������.

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

-> random�� ���ڿ� byte�� ����.
-> ������ 64byte ���̿� base64 ������� ����.

crypto.randomBytes(64, (err, buf) => {
    const salt = buf.toString('base64');
    console.log('salt', salt);
    crypto.pbkdf2('qjatjs12!', salt, 100000, 64, 'sha512', (err, key) => {
    console.log('password', key.toString('base64'));
    });
});
```

> �ؽ� �浹 ������ ��ư� �ϱ� ���� salt(�ұ�)�̶�� ���ڿ��� ���� ��й�ȣ�� �߰��ϰ� iteration Ƚ���� ���δ�.
> salt�� ��ȣȭ�� ��й�ȣ�� ���� �����ϰ�, iteration�� 1�� ������ �ɸ������� �÷��ָ� ����.
>���������� bcrypt, scrypt�� ���� ����Ѵٰ� ��. (�ð��� �Ǹ� �����غ��� !)


Crypto �����
=============

```javascript
const crypto = require('crypto');

const cipher = crypto.createCipher('aes-256-cbc', '����');
let result = cipher.update('qjatjs12!', 'utf8', 'base64');
result += cipher.final('base64');
console.log('��ȣ', result);

const decipher = crypto.createDecipher('aes-256-cbc', '����');
let result2 = decipher.update(result, 'base64', 'utf8');
result2 += decipher.final('utf8');
console.log('��ȣȭ', result2);
```

> '����' key ���� �ٸ� ���� �������� ������, �ٸ� ����ڰ� �� ��ȣ�� ��ŷ�� �� ����.
> �׷��� ������ ������ �߿���.
> �������Ʈ : https://nodejs.org/dist/latest-v10.x/docs/api/crypto.html