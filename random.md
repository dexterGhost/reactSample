**Solving authentication issues with Automation testing [Bypassing oAuth (google auth) for unit tests (Jest)]**

Google auth using passport gives us two response header “set-cookie”, namely **session** and **session.sig**
Using the Buffer node library we can decode the **session** value

```
const session = ‘session value returned from oauth’
const Buffer = require(‘safe-buffer’).Buffer;

Buffer.from(session, ‘base64’).toString(‘utf8’) == gives us ==> {“passport”: {“user”: “some value”}}
```

session.sig is used to validate whether someone tampered with the session value..

We can use Keygrip (another node module) to generate the signed session (verified)
```
const session = ‘session value returned from oauth’
const Keygrip = require(‘keygrip’)
const keygrip = new Keygrip([‘our private cookie key’])

keygrip.sign(‘session=‘ + session) ==> gives us **session.sig**

Keygrip.verify(‘session=‘ + session, <value from keygrip.sign>)
```


