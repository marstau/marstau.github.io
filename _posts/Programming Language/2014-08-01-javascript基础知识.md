---
layout: post
title: javascript基础知识
category: 编程开发
tags: javascript
keywords: 
description: 
---

## 基础语法


```
JSON.stringify(result); // object转为string
JSON.parse(str); // string转为json
```


#### `=>`

```
(x) => x + 6

相当于

function(x){
    return x + 6;
};
```

#### json使用

```
{
  "networks": {
    "5777": {
      "events": {},
      "links": {},
      "address": "0x49f62f21510b8ec6d812979b723e8f59dfa4b6de",
      "transactionHash": "0xc541427f63e958db2a04d6f64ff8371d7fb8fe13f131b9732b8b66ddce4bea70"
    }
  }
}
```

```
var MyJson = require('./x.json')
var str = JSON.stringify(MyJson["networks"]);
var jsonStr = JSON.parse(str);
console.log("jsonStr=", jsonStr[5777].address);
console.log("jsonStr2=", MyJson["networks"]["5777"]["address"]);
```


#### `...`[More](https://blog.csdn.net/qq_30100043/article/details/53391308)

#### 页面加载效果fakeLoader[More](http://www.jq22.com/jquery-info2082)

扩展运算符

将一个数组转为用逗号分隔的参数序列。

#### 复制内容到剪切板[More](https://blog.csdn.net/github_36091081/article/details/77508710)

因为exeCommand()可以操作系统剪切板，有可能被恶意利用。所以你不能用JS“直接”调用execCommand('copy')，而需要放到某一个有用户出发的事件响应函数内.[More](https://segmentfault.com/q/1010000005783830)

```
<script type="text/javascript">
function copyUrl2()
    {
        var Url2=document.getElementById("biao1").innerText;
        var oInput = document.createElement('input');
        oInput.value = Url2;
        document.body.appendChild(oInput);
        oInput.select(); // 选择对象
        document.execCommand("Copy"); // 执行浏览器复制命令
        oInput.className = 'oInput';
        oInput.style.display='none';
        alert('复制成功');
    }
</script>
<div cols="20" id="biao1">12345678</div>
<input type="button" onClick="copyUrl2()" value="点击复制代码" />
```

但不支持safari浏览器。

所以使用[clipboard.js](https://github.com/zenorocha/clipboard.js)


```javascript
<div class="buttonClass" data-clipboard-text="
line1
line2
"  data-clipboard-action="copy" id="bs">确定</div>
<script>
$('#bs').click(function () {
  var roomid = 1;
  var site = 'baidu.com';
  var recommenCode = 'sdkc';

  var clipboard = new ClipboardJS("#bs");
  clipboard.on("success",function (e) {
    console.info('Action:', e.action);
    console.info('Text:', e.text);
    console.info('Trigger:', e.trigger);
  });
  clipboard.on("error",function (e) {
    console.error('Action:', e.action);
    console.error('Trigger:', e.trigger);
    console.info(e);
  });
});
</script>
```

If you want to dynamically set a text, you'll return a String.[More](https://clipboardjs.com/)

```
<script>
new ClipboardJS('.btn', {
    text: function(trigger) {
        return trigger.getAttribute('aria-label');
    }
});
</script>
```

## 还原min.js为js文件, unminify js[More1](https://beautifier.io/)[More2](https://github.com/beautify-web/js-beautify)

```
npm -g install js-beautify
js-beautify -f file.min.js -o file.js
```

#### post

```
var formData = new FormData();
formData.append('p1', param1);
formData.append('p2', param1);
fetch('https://url.com/index.php/', {
  method: 'POST',
  headers: {
    'Accept': 'application/json',
    'Content-Type': 'application/x-www-form-urlencoded',
  },
  body: formData
})
```

```
fetch('https://mywebsite.com/endpoint/', {
  method: 'POST',
  headers: {
    'Accept': 'application/json',
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    p1: 'yourValue',
    p2: 'yourOtherValue',
  })
})
```

#### get

```
fetch("https://mywebsite.com/endpoint", {
  method: 'GET',
  headers: {
    'Accept': 'application/json',
  }
  })
  .then((response) => {
      return response.json();
  }).then((response) => {
      console.log("response=" + JSON.stringify(response))
  }
);
```

#### AES加密[More](http://www.fairyland.live/wordpress/2017/03/16/php%E4%B8%8Ejavascript%E5%85%BC%E5%AE%B9%E7%9A%84aes%E5%8A%A0%E8%A7%A3%E5%AF%86/)

```
var CryptoJS = require("crypto-js")
var key = CryptoJS.enc.Utf8.parse("amOWLGDgZCyrG4ARTDf64Qn3FEigIQhw");
var iv =  CryptoJS.enc.Utf8.parse("PPwFSQW0i7d3Unpa4ZmmILPcznV51AAa");
var encrypted = CryptoJS.AES.encrypt("message", key, {iv:iv,mode: CryptoJS.mode.CBC, padding: CryptoJS.pad.Pkcs7})
console.log("encrypted=" + encrypted.toString())
```

#### 位运算代替求余运算提高效率

```
a % b = a - (a / b)*b
a % b = a & (b-1) // 当b为2^n的时候
```

#### 字符串为空

```
if(str.trim()!==""){
  console.log("非空");
}else{
  console.log("空");
}
```

#### 字符串全部替换

```
str.replace(new RegExp(" ",'g'), "")
```

#### 同步读取mysql[More](https://blog.csdn.net/tinfengyee/article/details/94434659)

```
const mysql = require('mysql')
const pool = mysql.createPool({
  host     :  '127.0.0.1',
  user     :  'root',
  password :  '123456',
  database :  'my_database'
})

let query = function( sql, values ) {
  return new Promise(( resolve, reject ) => {
    pool.getConnection(function(err, connection) {
      if (err) {
        reject( err )
      } else {
        connection.query(sql, values, ( err, rows) => {

          if ( err ) {
            reject( err )
          } else {
            resolve( rows )
          }
          // 结束会话
          connection.release()
        })
      }
    })
  })
}
```

### minify js or [Minify JS](https://javascript-minifier.com/)

```
npm install minify
```

#### Load node.js module from string in memory[More](https://stackoverflow.com/questions/17581830/load-node-js-module-from-string-in-memory)

```
function requireFromString(src, filename) {
  var m = new module.constructor();
  m.paths = module.paths;
  m._compile(src, filename);
  return m.exports;
}

var codeString = fs.readFileSync("./text.js", "utf-8");
var Js = requireFromString(codeString, '')
```

## Error




## Reference

* [best-javascript-mysql-libraries](https://openbase.com/categories/js/best-javascript-mysql-libraries)