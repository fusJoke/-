1.cookie的调用删除	
cookie文件存储方式是 `键名`、`=`、`键值`、结尾以一个分号(;)以及一个空格( ) .
所以在取得某个cookie值的时候要用（'; '）做分隔符。
防止等号、空格等特殊字符解析错误，存入cookie前进行urlencode编码
encodeURIComponent()

decodeURIComponent()

```
function getCookie(name){
        let cookies = document.cookie.split("; ");	//
        for(let i=0;i<cookies.length;i++){
            let cookie=cookies[i].split("=");   //cookie cookie名 = cookie值
            if(name==cookie[0]){
                return JSON.parse(cookie[1]);
            }
        }
        return false;
    }
```

2.js调用摄像头+canvas画图



3.判断输入设备的输入是扫码枪的扫码。



4.节点的获取，增加删除



5. json字符串转json对象 	

```
 JSON.parse(jsonStr);	//字符串转对象

JSON.stringify(json);	//
```

6.base64图片上传的细节



7.禁止表单默认提交



8.正则匹配 整数或者浮点数



9.forEach循环