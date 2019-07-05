# 遍历相关场景

1. 数据库存的数据不是完整的，需要遍历补全。比如说，图片地址只是存了图片名，没有存完整url地址。

   ```php
   //foreach使用引用
   $prefix = 'prefix';
   foreach($data as $key => &$item){
       $item['img'] = $item['img'].$prefix;
   }
   //使用array_map() 返回一个新的索引数组
   $formated_data = array_map(function($item){
       $item['img'] = $prefix . $item['img'];
       return $item;
   },$data)
   ```

2. 合并元素。数组$arr = ['08:30-10:00' , '11:00-12:00' , '12:00-14:00',' 15:00-15:30'];保存的是时间段数组，写个方法，如果时间是连续的就合并起来，最后得到['08:30-10:00' , '11:00-14:00',' 15:00-15:30']

   ```php
   public function formatArray($arr){
       $arr = [
           '08:30-10:30', '11:00-12:00', '12:00-14:00', '15:00-15:30',
       ];
      
       foreach ( $arr as $key => $datetime ) {
           
           if ( $key == 0 ) {
               $array[] = $datetime
               continue;
           }
       
           $last = explode('-',end( $array ) );
           $tmp  = explode('-',$datetime);
           if ( $tmp[0] == $last[1] ) {
               array_pop( $array );
               array_push( $array ,
                   implode('-',[ $last[0],$tmp_time[1] ])
               );
           } else {
               array_push($array, $datetime);
           }
       }
       return $array;
   }
   ```

3. 使用array_filter()过滤数组
   array_filter ( array `$array` [, [callable](https://www.php.net/manual/zh/language.types.callable.php) `$callback` [, int `$flag` = 0 ]] ) : array

   array 要被过滤的数组
   callback 回调函数
   flag 设置回调函数的参数

   ​		**ARRAY_FILTER_USE_KEY**      键名
   ​		**ARRAY_FILTER_USE_BOTH**  键名键值

   ```php
   // 1.过滤空值
   $filtered_dat = array_filter($data);
   // 2.过滤特定条件
   $data = [
   	['id'=>1,'status'=>1]
   	['id'=>1,'status'=>0]，
   ]；
   $new_data = array_filter($data,function($value,$key){
       if( $value['status'] === 0){
           return false;
       }else{
           return true;
       }
    },ARRAY_FILTER_USE_BOTH);
   
   ```

4. 组成特定的键值对 array_combine

   ```php
   $keys = $values = [];
   foreach($data as $item){
       $keys[]   =  $item['id'];
       $values[] =  $item['name'];
   }
   $new_arr = array_combine($keys,$values);
   
   $new_arr = [];
   foreach($data as $item){
   	$new_arr[ $item['id'] ] = $item['name'];
   }
   ```

5. 数组指针的相关操作
   key() 返回当前指针指向的元素的键名
   current() 返回当前指针指向的元素的键值
   prev()  指针上移
   next()  指针下移  each()返回键/值对 指针下移
   reset() 重置指针

6. count() 统计数组

   count ( [mixed](https://www.php.net/manual/zh/language.pseudo-types.php#language.types.mixed) `$array_or_countable` [, int `$mode` = COUNT_NORMAL ] ) : int

   mode = **COUNT_RECURSIVE**  将递归地对数组计数

   ```php
   $food = array('fruits' => array('orange', 'banana', 'apple'),
                 'veggie' => array('carrot', 'collard', 'pea'));
   
   // recursive count
   echo count($food, COUNT_RECURSIVE); // output 8
   
   // normal count
   echo count($food); // output 2
   ```

7. 

8. 

9. 

