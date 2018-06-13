###MongoDB

####MongoDB

 * 无数据结构限制
  
  * 没有表结构的概念,每条记录可以有完全不同的结构
  * 业务开发方便快捷
  * sql数据库需要事先定义表结构再使用
   
   ```js
    {name:'小明',sex:'男'}
    {name:'小红',address:'上海'}
    {name:'小兰',home:[{'山东'},{江西}]}

   ```
 * 完全的索引支持
 
  * redis的key-value
  * hbase的单索引,二级索引需要自己实现
  ```js
  
  单键索引,多键索引：{x:1,y:1}
  数组索引:["apple","lemon"]
  全文索引:"i am a little bird."(中文)
  
  
  ```