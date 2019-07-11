http://www.thinkphp.cn/topic/59357.html

1.控制器的方法参数和请求的参数如何分辨



2.逻辑分层

​	1.对请求的参数取值范围的判定放在路由，包括正则。
​	2.控制器层负责调度，以及组装数据返回。
​	3.模型层负责对数据查找，删除，增加。
​		

3.查询表达式错误:'order_id'：
​	5.1的数组查询方式有所调整，为二维索引数组，是为了尽量避免数组方式的条件查询注入。

```
//官方代码示例：二维数组
$map[]=['name','like','thinke'];
//
$orderModel = Db::name('order');
$order = $orderModel->where([['order_id','=',$id]])->select()
//二维索引数组必须是连续的索引 
也就是说像这种数组是会报错的
$data = [
    2 => ['field','option','condition]
]；
必须是从零开始且连续的索引数组。
一般是不会遇上这种问题

```

![1559807431031](C:\Users\aumak\AppData\Roaming\Typora\typora-user-images\1559807431031.png)



![1559807558017](C:\Users\aumak\AppData\Roaming\Typora\typora-user-images\1559807558017.png)

![1559807960888](C:\Users\aumak\AppData\Roaming\Typora\typora-user-images\1559807960888.png)

![1559808769042](C:\Users\aumak\AppData\Roaming\Typora\typora-user-images\1559808769042.png)

4.如果是用restful path paramter这种传参方式
​	例：http://www.url.com/pos/order/:order_no

​	控制器中方法直接用用参数接收

5.接申通接口 通过Bearer Token 验证



6. 模型的saveAll()的返回值

7. 什么时候需要用toArray

8. 各种查询的返回值

   1. find()
      成功返回一维数组， 失败返回null
      findOrFail()查询失败`think\db\exception\DataNotFoundException`异常。

   2. select()
      成功返回二维数组， 失败返回空数组
      selectOrFail()查询失败返回的是DataNotFoundException异常

   3. column
      一维索引数组

      ```
      /**
       * 一维索引数组
       */
      public function testSelColumn(){
          $sku = Db::name('order_product')
              ->where('order_no','=','20190521163441237162')
              ->column('sku');
          var_dump($sku);
      }
      ```

      ![1561099753769](C:\Users\aumak\AppData\Roaming\Typora\typora-user-images\1561099753769.png)

9. Session::get('name'); 如果name的值不存在 返回null

