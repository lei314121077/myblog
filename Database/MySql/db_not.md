# mysql 相关

## mysql 锁
当计算机协程或进程并发对数据库资源进行高并发的读写的时候，为了保证数据的一致性和有效性，mysql数据库设计了锁机制。mysql的锁分3个等级，表级锁、行级锁、页级锁。很难去评判哪种锁更好，只能相对于所处的业务场景来选择更加适合的锁机制。如果仅从锁的角度来看，表级锁更适合以查询为主的应用场景，而行级锁则更适合于大量按索引条件并发更新少量数据的应用场景。

* 表级锁：开销小，加锁快；不会出现死锁；锁定粒度大，发生锁冲突的概率最高，并发度最低。
* 行级锁：开销大，加锁慢；会出现死锁；锁定粒度最小，发生锁冲突的概率最低，并发度也最高。
* 页面锁：开销和加锁时间界于表锁和行锁之间；会出现死锁；锁定粒度界于表锁和行锁之间，并发度一般 

### MySQL表级锁

* 如何设置锁

   MyISAM在执行查询语句[SELECT]前，会自动给涉及的所有表加读锁，在执行更新操作（[UPDATE]、[DELETE]、[INSERT]等）前，会自动给涉及的表加写锁，这个过程并不需要用户干预，因此用户一般不需要直接用LOCK TABLE命令给MyISAM表显式加锁。给MyISAM表显示加锁，一般是为了一定程度模拟事务操作，实现对某一时间点多个表的一致性读取。

   例如，有一个订单表orders，其中记录有订单的总金额total，同时还有一个订单明细表order_detail，其中记录有订单每一产品的金额小计subtotal，假设我们需要检查这两个表的金额合计是否相等，可能就需要执行如下两条SQL：

   ```mysql
   SELECT SUM(total) FROM orders;
   SELECT SUM(subtotal) FROM order_detail;
   ```

   这时，如果不先给这两个表加锁，就可能产生错误的结果，因为第一条语句执行过程中，order_detail表可能已经发生了改变。因此，正确的方法应该是：
   ```
   LOCK tables orders read local,order_detail read local;
   SELECT SUM(total) FROM orders;
   SELECT SUM(subtotal) FROM order_detail;
   Unlock tables;
   ```
   * 要特别说明以下两点内容。

      上面的例子在LOCK TABLES时加了‘local’选项，其作用就是在满足MyISAM表并发插入条件的情况下，允许其他用户在表尾插入记录
      在用LOCKTABLES给表显式加表锁是时，必须同时取得所有涉及表的锁，并且MySQL支持锁升级。也就是说，在执行LOCK TABLES后，只能访问显式加锁的这些表，不能访问未加锁的表；同时，如果加的是读锁，那么只能执行查询操作，而不能执行更新操作。其实，在自动加锁的情况下也基本如此，MySQL问题一次获得SQL语句所需要的全部锁。这也正是MyISAM表不会出现死锁（Deadlock Free）的原因,一个session使用LOCK TABLE 命令给表film_text加了读锁，这个session可以查询锁定表中的记录，但更新或访问其他表都会提示错误；同时，另外一个session可以查询表中的记录，但更新就会出现锁等待。
      当使用LOCK TABLE时，不仅需要一次锁定用到的所有表，而且，同一个表在SQL语句中出现多少次，就要通过与SQL语句中相同的别名锁多少次，否则也会出错！


* MySQL表级锁的锁模式（MyISAM)
   
   * 并发锁
   
      MyISAM也支持查询和操作的并发进行。MyISAM存储引擎有一个系统变量concurrent_insert，专门用以控制其并发插入的行为，其值分别可以为0、1或2。
      
      * 当concurrent_insert设置为0时，不允许并发插入。
      * 当concurrent_insert设置为1时，如果MyISAM允许在一个读表的同时，另一个进程从表尾插入记录。这也是MySQL的默认设置。
      * 当concurrent_insert设置为2时，无论MyISAM表中有没有空洞，都允许在表尾插入记录，都允许在表尾并发插入记录。
   
   可以利用MyISAM存储引擎的并发插入特性，来解决应用中对同一表查询和插入锁争用。例如，将concurrent_insert系统变量为2，总是允许并发插入；同时，通过定期在系统空闲时段执行OPTIONMIZE TABLE语句来整理空间碎片，收到因删除记录而产生的中间空洞。
   
   * 共享锁

## mysql oneproxy

* 读写分离

* 分表分库







