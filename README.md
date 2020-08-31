# Simple script to get your discord token
## Using NodeJS

To start the script simply type 
```node gettoken.js```
Then insert your credentials and your token will show up!

# Source code:
```javascript 
var rp = require("request-promise")
var rs = require("readline-sync");
var colors = require('colors/safe');
var email = rs.question("email: ");
var password = rs.question("password: ");

var options = {
body: JSON.stringify({"email": email,"password": password,"undelete":false,"captcha_key":null,"login_source":null,"gift_code_sku_id":null}),
headers: {
"Content-Type": "application/json",
"x-fingerprint": "715952977180885042.yskHI7mK4iZWhTX7iXlXIcDovRc",
"x-super-properties" :Buffer.from(JSON.stringify({"os":"Windows","browser":"Chrome","device":"","browser_user_agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.61 Safari/537.36","browser_version":"83.0.4103.61","os_version":"10","referring_domain":"discord.com","referrer_current":"","referring_domain_current":"","release_channel":"stable","client_build_number":60856,"client_event_source":null}), "utf-8").toString("base64"),
cookie: '__cfduid=d638ccef388c4ca5a94c97c547c7f0d9e1598555308; __cfruid=4d17c1a957fba3c0a08c74ea83114af675f7ef19-1598796039;'
 },
method: "POST",
uri: "https://discord.com/api/v8/auth/login"
}

rp(options).then(function (body) {

var tmtc = JSON.parse(body)
console.log( colors.green(tmtc.token) )

});
```
