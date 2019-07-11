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
​	
​	2.facede概念
​	

```

```

​	3.依赖注入概念
​		一个类的某个方法实现需要调用另一个类的某个方法。
​		依赖注入的类统一由容器进行管理，大多数情况下是在自动绑定并且实例化的

三、路由

四、控制器
​	前置操作 
​	空操作和空控制器
​	分层控制器
​		只允许在控制器内部、模型类被调用
​	资源控制器
​		
​		
五、模型
​	模型关联
​		
​	
​六、验证器	
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
​	