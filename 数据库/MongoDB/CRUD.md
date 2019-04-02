# MongoDB 常用到的　`CRUD`　语句
MongoDB 设计原理和Mysql类似，查询语句使用的js语法，相对来说容易理解

#### 数组查询相关
- 查询数据为空
```
db.newsdoc.find({ "provider.name": "Stocker", "state": 1, $where: "this.images.length == 0" }, { "docid": 1 })

```

- 匹配对象数组当中的一个值

```
db.newsdoc.find({ "provider.name": "Stocker", "images": { $elemMatch: { "url": { $regex: "www.baidu.com", $options: 'i' } } } }).count();

```
