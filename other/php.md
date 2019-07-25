1.   6位随机整数

```php
substr(mt_rand()/mt_getrandmax() ,2,6);
```

  2.in_array() 使用的是===比较还是==比较

```
in_array ( mixed $needle , array $haystack [, bool $strict = FALSE ] ) : bool
```

​	1.needle如果是字符串是区分大小写的，比较区分大小写
​	2.第三个参数是否严格比较，默认false，开启后还会检查数据类型是否相同

  3.is_numberic() 变量是否是数字或数字字符串.是返回true，不是false

​	浮点数 1.22 ==>true，
​	   负数 ( -1 ) ( -1.22 )  ==>true

4.判断数据属性类型  

```
gettype ( mixed $var ) : string
```

- boolean
- integer
- double
- string
- array
- object



5.foreach 和array_map的区别
​	array_map($callback，array $array 1,[,array 	$...]):array
​	array_map同时遍历N个数组，取相同指针位置的数组元素，通过callback处理，生成一个新的索引数组。

​		1.$callback的返回值作为新数组的元素
​		2.$callback的参数顺序对应加入array_map数组的顺序。
​		3.返回新数组的长度=最长的数组
​		4.如果只传入一个数组 则键值会被保存	不能控制键值

​	foreach()是语法结构

6.empty()

​	用于判断变量是否为空

​	“”(空字符串)
​	0(整数0)
​	0.0(浮点数零)
​	"0"(字符串0)
​	NULL
​	FALSE
​	array()（空数组）
​        $var；（声明了未赋值）
​	以上为空。

7.unset()
​	删除对象属性 

8.array_filter()

array_filter ( array `$array` [, [callable](https://www.php.net/manual/zh/language.types.callable.php) `$callback` [, int `$flag` = 0 ]] ) : array

$array每个元素都使用回调函数$callback()过滤，如果$callback()返回false，则在$array删除该元素。

- 如果没有提供 `callback` 函数， 将删除 `array` 中所有等值为 **FALSE** 的条目

- 使用类方法作为回调函数。

  - ```
    $where = array_filter($where,[$this,'whereMap'],ARRAY_FILTER_USE_BOTH );
    //第一个参数是要进行过滤的数组 
    //第二个参数传入数组,数组第一个元素是对象的引用，第二是对象的方法名
    //第三个参数是回调函数传参设置
    	ARRAY_FILTER_USE_BOTH 回调函数接受键值和健名作为参数，参数顺序为(键值，键名)
    	ARRAY_FILTER_USE_KEY  仅接受键值作为参数
    public function whereMap($value,$key){
        ...
    }
    
    ```

  9.执行||等逻辑运算符 数据类型会进行自动的转换。

  ​	代码会执行完，然后将值进行自动转换boolaen



10.闭包函数、匿名函数以及Closure 类



11.我如何分析



12.postman使用xdebu断点调试
​	请求参数带上![1557971557059](C:\Users\aumak\AppData\Roaming\Typora\typora-user-images\1557971557059.png)

​	XDEBUG_SESSION_START=PHPSTORM

13.array_push()优缺点
​	

```
array_push ( array &$array , mixed $value1 [, mixed $... ] ) : int

array_push($stack, "apple", "raspberry");
/*
 * 可以一次性压入多个值 不能控制键值
 * 不如用$var[]=来的实际
 */
 
```

13.使用exit返回字符串的时候注意设置响应体的格式

```php
//exit会直接中断代码的执行，如果没有设置编码格式返回的就是text文档而不是json
header('Content-Type:application/json;charset=utf-8')
```



14.一个业务过程如果涉及多个表的修改，删除，必须使用事务，并且加上try catch 捕获错误。



16.yield应用场景
​	生成器(Generatir) ：实现迭代器的方式。函数通过
​	





接口开发和模板混合开发的区别

![1560938090319](C:\Users\aumak\AppData\Roaming\Typora\typora-user-images\1560938090319.png)

![1560938133034](C:\Users\aumak\AppData\Roaming\Typora\typora-user-images\1560938133034.png)





17.反射类的应用





18.sprintf()使用



19.  self::class 和static:class 的区别

    	self::class 指向的当前父类的名字
    	static::class 当前类的名字


20. call_user_func_array 的用法

    ```php
    
    ```

21. list批量设置变量
     list($val1,$val2,$val3,$val4) = explode($delimiter,$str);