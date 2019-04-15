# Map 的各种实现

`Map` 接口是独立于 Collect 的独立的数据集合
其中常用的Map实现 `HashMap`

- HashMap
	使用 Hash 桶实现了数据的存储。 Hash 桶就是一个 Map.Entry 的数组，每个 Entry 是一个链表，用来存放hash值碰撞之后的数据

	loadfactory 装载因子， 当 size > threshold 的时候，开始 重新扩容, 扩容一般是扩展为上一次的一倍。
	threshold = Maxmium * loadfactory

- ListHashMap
	类中保留了几个列表字段，先使用链表保存数据，数据多的时候，超过数组限制，开始放到map中存放结果。

- LinkedHashMap
	类中使用 HashMap 来保存数据，是使用链表 head 和 tail 保存存入的顺序，这就是有序的Map就是 LinkedHashMap