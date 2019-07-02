RESTful API

rest围绕`资源`展开

## RESTful API设计

1.url中不能有动词
​	get:获取；post:创建；put:更新；delete:删除；











https://www.colabug.com/228298.html



2.postman中form-data、x-www-form-urlencoded、raw、binary

- ​	form-data方式：表示http请求中multipart/form-data方式，会将表单的数据处理为一条消息

```
--l_Sh3DQ0_nc-zPblBpi8L3Oq63BWUDLqDqbRpyd
Content-Disposition: form-data; name="name"
Content-Type: text/plain;charset=UTF-8
Content-Length: 12

wangjianfeng
--l_Sh3DQ0_nc-zPblBpi8L3Oq63BWUDLqDqbRpyd
Content-Disposition: form-data; name="age"
Content-Type: text/plain;charset=UTF-8
Content-Length: 2

20
--l_Sh3DQ0_nc-zPblBpi8L3Oq63BWUDLqDqbRpyd--
```

- x-www-form-urlencoded：讲表单的数据转换成键值对

  ```
  name=wangjianfeng&age=12
  ```

-  binary：相当于Content-Type:application/octet-stream,只可以上传二进制数据，通常用来上传文件，但是一次只能上传一个文件。
- raw：可以上传任意格式的文本，文本不做任何修饰传到服务端。比如传一些xml，或者json数据，或者text文本数据