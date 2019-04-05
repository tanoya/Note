# Memcached简介
这里先不赘述Memcached的原理和机制，宏观上看应该是和redis类似，我们这里比较一下Memcached和redis的不同点，这对选择应用场景还有启发的作用
- Memcached的数据结构单一，只有key-value，而redis支持了list/set/hash
- Redis支持的数据类型单一，只能是string。而Memcached支持了图片，视频等文件
- Memcache不支持持久化，Redis支持RDB和AOF数据持久化策略