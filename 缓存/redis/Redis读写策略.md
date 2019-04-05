# `Redis`读写策略
- 写
Redis所有的数据的写都是放到master节点来完成的，将新的数据写入master节点，然后通过同步机制同步到slave节点之中（两种同步机制）。
- 读
Redis的数据读取应该是放到slave节点来完成的。多个slave的情况下应该是随机选取slave节点来读取。