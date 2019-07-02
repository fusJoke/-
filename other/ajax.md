1.为什么php返回json数据。ajax的success接收到返回值的是字符串而不是对象？？？

响应体的编码格式设置成json。

![1557022944175](C:\Users\aumak\AppData\Roaming\Typora\typora-user-images\1557022944175.png)

```php
header("Content-type:application/json;chartset=uft-8");
```

