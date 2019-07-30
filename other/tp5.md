项目结构
tp5
--application
--config
--extend
--public
   --index.php 入口文件
​	
--route
--runtime
--thinkphp
   --library 类库
​      --think
​      
   --base.php  基础文件
​      引入自动加载类
  --convention 惯例配置文件
  --helper.php 助手函数

一、生命周期
​	1./public/index.php
​	入口文件。
​	2./thinkphp/base.php
​		载入loader类
​		
​	
二、几个概念
​	1.容器是什么的，	

​		container类 管理所有类的实例化，调度，依赖注入
​		app类继承container类，管理各种类,初始化各种配置文件

​	2.facede概念	
​		可以用调用静态方法的方式去调用类。具体实现的方式，魔术方法**__callStatic** 会在一个不存在的类方法被调用时被触发，__callStatic()的返回值就是 通过container类调用某个类的某个结果

```php
	class Facade{	
	....
	//魔术方法 调用一个不存在的静态的方法时候触发
	public static function __callStatic($method, $params)
    {
        return call_user_func_array([static::createFacade(), $method], $params);
    }
	...
	protected static function createFacade($class = '', $args = [], $newInstance = false)
    {
        ...
        return Container::getInstance()->make($class, $args, $newInstance);//从容器返回类的实例
    }
        
    }
```

​	3.依赖注入概念
​		一个类的某个方法实现需要调用另一个类的某个方法。
​		依赖注入的类统一由容器进行管理，大多数情况下是在自动绑定并且实例化的

三、路由

1. 

四、控制器
​	前置操作 



​	空操作和空控制器

​	分层控制器
​		只允许在控制器内部、模型类被调用
​	资源控制器
​		
​		
五、数据库类
​	1.链式操作
​		类的每个方法都是 设置属性值，然后返回它本身，在select()、find()、update组装好sql，然后清空对象的成员属性的值。	
​	2.\thinkphp\think\db.php
​		数据库功能被抽象成具体几个类(connect类, query类, where类, Express类, Builder类 )。而db类用来调度这些数据库功能类。
​		

```php

```

六、验证器	
​	
​	
​	
​	
​	
六、问题
​	1.tp5业务逻辑放在model还是controller层。涉及到多个model的逻辑要怎么写
​		controller层{
​			1.接收请求
​			2.对参数做处理
​			3.响应
​		}
​		model层对数据进行操作
​			把实际的表抽象成对象。
​			
​	2.如何把业务逻辑封装成model方法。如何定返回值。
​	
​	




​	
​	