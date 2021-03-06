# mysql的事务隔离级别
*注*
此时的隔离级别是<font color="red">事务与事务</font> `之间` 的隔离关系，实验的时候，尽量开两个`cmd`窗口进入，分别开启事务，比较容易得出结论。
##### Read Uncommitted (读取未提交的内容)
  在该隔离级别，所有事务能够看到其他未提交事务的结果。本隔离级别很少用于实际应用，因为它的性能不比其他级别好多少，读取未提交的内容，也称之为脏读(Dirty Read)
##### Read Committed (读取提交的内容)
  这是大多数数据库系统的默认隔离级别(但不是MySql默认的)。它满足了隔离的简单定义：一个事务只能看见已经提交事务所做的改变。这种隔离级别也支持所谓的不可重复读(Nonrepeatable Read). 这种事务隔离级别会出现"幻影"现象。
*例*
现在假设有两个事务(事务A和事务B)，一张没有数据的空表。通过事务B先查询该表，查询语句后面没有事务提交的 `commit;`语句。事务B的查询结果是空表。此时使用事务A向空表中插入一条数据，先不提交事务，此时通过事务B来查询表，发现还是没有结果，此时说明事务隔离级别确实是读取提交的内容。然后提交事务A，通过事务B来查询数据表(从开始到现在事务B还是原来起始的事务，还没有提交过)，发现事务B已经看见了事务A增加的那一条数据。注意，现在由于事务B在一个事务中，第一次看不见数据，到第二次看见数据，说明此时在事务B中出现了"幻影"。
##### Repeatable Read (可重复读)
这是MYSQL默认的事务隔离级别，它确保同一个事务对同一个数据的多次查询时能够得到同样的数据行，尽管另一个事务可能会对该条数据进行了修改，但是仍然能够得到事务执行之前的数据。这样可以解决了 `Read Committed`出现的'幻影'现象。(如果事务A已经对id=1的数据进行了修改，但是事务B仍然无法查询得到该数据的修改也算作"幻影"的情况的话，那么可重复性读也是会存在幻影的情况的。)
##### Serializable (可串行化)
这是最高的事务隔离级别，它强制事务排序，使之不可能互相冲突，当然了，同样也解决了"幻影"问题。简言之就是在每个读的数据行上边加了共享锁，在这个级别，可能导致大量的超时现象和锁竞争。可串行化可以理解为对于表中的某条数据而言，多个事务对于它的操作是可串行化的。也就是，一个事务A对该数据进行了修改，在事务A提交之前，如果事务B对该条数据进行了查询，那么在事务隔离级别之下，事务B会等到事务A提交了之后才会进行查询操作，也就保证了数据的一致性。同样也很容易看出来这中隔离级别的执行效率比较低。
*注*
[参考博文](http://xm-king.iteye.com/blog/770721)