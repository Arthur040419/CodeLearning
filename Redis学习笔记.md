# Redis学习笔记

参考资料：[基础篇-01.Redis入门课程介绍_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1cr4y1671t?spm_id_from=333.788.videopod.episodes&vd_source=f3cb3ea986b26c6910b4df6d37acd60d&p=2)



## 认识Redis

Redis是Remote Dictionary Server的缩写，因为远程词典服务器，是一个基于内存的键值型NoSQL数据库

它具有以下特征

![image-20250331091159249](./pictures/image-20250331091159249.png)

Redis属于非关系型数据库(NoSQL)，非关系型数据库与关系型数据库的区别如下

![image-20250331090440760](./pictures/image-20250331090440760.png)

其中事务特性，SQL是满足ACID原则，NoSQL是满足BASE原则

扩展性，SQL垂直指的是SQL在存储数据时只能将数据存储到本地数据库中，不能像NoSQL一样可以将数据拆分进行分布式存储。





## Redis安装说明

大多数企业都是基于Linux服务器来部署项目，而且Redis官方也没有提供Windows版本的安装包。因此课程中我们会基于Linux系统来安装Redis.

此处选择的Linux版本为CentOS 7.

Redis的官方网站地址：https://redis.io/





1.单机安装Redis

### 1.1.安装Redis依赖

Redis是基于C语言编写的，因此首先需要安装Redis所需要的gcc依赖：

```sh
yum install -y gcc tcl
```



### 1.2.上传安装包并解压

然后将课前资料提供的Redis安装包上传到虚拟机的任意目录：

![image-20211211071712536](./pictures/image-20211211071712536.png)

例如，我放到了/usr/local/src 目录：

![image-20211211080151539](./pictures/image-20211211080151539.png)

解压缩：

```sh
tar -xzf redis-6.2.6.tar.gz
```

解压后：

![image-20211211080339076](./pictures/image-20211211080339076.png)

进入redis目录：

```sh
cd redis-6.2.6
```



运行编译命令：

```sh
make && make install
```

如果没有出错，应该就安装成功了。



默认的安装路径是在 `/usr/local/bin`目录下：

![image-20211211080603710](./pictures/image-20211211080603710.png)

该目录以及默认配置到环境变量，因此可以在任意目录下运行这些命令。其中：

- redis-cli：是redis提供的命令行客户端
- redis-server：是redis的服务端启动脚本
- redis-sentinel：是redis的哨兵启动脚本



### 1.3.启动

redis的启动方式有很多种，例如：

- 默认启动
- 指定配置启动
- 开机自启



### 1.3.1.默认启动

安装完成后，在任意目录输入redis-server命令即可启动Redis：

```
redis-server
```

如图：

![image-20211211081716167](./pictures/image-20211211081716167.png)



这种启动属于`前台启动`，会阻塞整个会话窗口，窗口关闭或者按下`CTRL + C`则Redis停止。不推荐使用。



### 1.3.2.指定配置启动

如果要让Redis以`后台`方式启动，则必须修改Redis配置文件，就在我们之前解压的redis安装包下（`/usr/local/src/redis-6.2.6`），名字叫redis.conf：

![image-20211211082225509](./pictures/image-20211211082225509.png)

我们先将这个配置文件备份一份：

```
cp redis.conf redis.conf.bck
```



然后修改redis.conf文件中的一些配置：

```
vi  redis.conf
```

```properties
# 允许访问的地址，默认是127.0.0.1，会导致只能在本地访问。修改为0.0.0.0则可以在任意IP访问，生产环境不要设置为0.0.0.0
bind 0.0.0.0
# 守护进程，修改为yes后即可后台运行
daemonize yes 
# 密码，设置后访问Redis必须输入密码
requirepass 123321
```



Redis的其它常见配置：

```properties
# 监听的端口
port 6379
# 工作目录，默认是当前目录，也就是运行redis-server时的命令，日志、持久化等文件会保存在这个目录
dir .
# 数据库数量，设置为1，代表只使用1个库，默认有16个库，编号0~15
databases 1
# 设置redis能够使用的最大内存
maxmemory 512mb
# 日志文件，默认为空，不记录日志，可以指定日志文件名
logfile "redis.log"
```



启动Redis：

```sh
# 进入redis安装目录 
cd /usr/local/src/redis-6.2.6
# 启动
redis-server redis.conf
```



停止服务：

```sh
# 利用redis-cli来执行 shutdown 命令，即可停止 Redis 服务，
# 因为之前配置了密码，因此需要通过 -u 来指定密码
redis-cli -u 123321 shutdown
```



### 1.3.3.开机自启

我们也可以通过配置来实现开机自启。

首先，新建一个系统服务文件：

```sh
vi /etc/systemd/system/redis.service
```

内容如下：

```conf
[Unit]
Description=redis-server
After=network.target

[Service]
Type=forking
ExecStart=/usr/local/bin/redis-server /usr/local/src/redis-6.2.6/redis.conf
PrivateTmp=true

[Install]
WantedBy=multi-user.target
```



然后重载系统服务：

```sh
systemctl daemon-reload
```



现在，我们可以用下面这组命令来操作redis了：

```sh
# 启动
systemctl start redis
# 停止
systemctl stop redis
# 重启
systemctl restart redis
# 查看状态
systemctl status redis
输入冒号  : 然后加q退出查看状态
```



执行下面的命令，可以让redis开机自启：

```sh
systemctl enable redis
```



## Redis命令行客户端

Redis在安装时自带了一个命令行客户端

```sh
redis-cli -h Redis数据库的地址 -p 端口号 [-a 密码]

redis-cli -h localhost -p 6379 -a 123456

redis-cli -h localhost -p 6379
#如果连接时不指定密码可以在连接后再验证密码
#连接后使用以下命名来验证密码
AUTH 密码
#使用ping命令来验证Redis是否连接成功
ping
```

![image-20250331095702873](./pictures/image-20250331095702873.png)



## Redis命令

#### Redis常用数据类型

 Redis中key是String类型的，value有五种常用的数据类型

1.String，字符串。普通字符串，Redis中最简单的数据类型

2.hash，哈希。也叫做散列，hash内部也是类似于一个键值对形式的存储形式，实际上就是一个字符串类型的field和value的映射表，因此哈希适合存储对象类型数据。

3.list，列表。按照插入顺序排序，可以有重复数据，类似Java中的LinkedList

4.set，集合。无序且不能重复，类似Java中的HashSet

5.sorted set/zset，有序集合。集合中每个元素关联一个分数（score），根据分数升序排序，没有重复元素。

这五种数据类型如下图所示

![image-20250326191126554](./pictures/image-20250326191126554.png)

 

#### Redis字符串（String）操作命令

字符串类型下面又分有三种类型：1.string普通字符串、2.int整数类型，可做自增自减操作、3.float浮点类型，可做自增自减操作。

不管那种格式，顶层都是以字节数组形式存储。字符串类型数据最大不能超过512M

操作字符串的命令常用的有如下几个：

设置key的值为value

```
SET key value 
```

批量添加修改key

```
MSET key1 value1 [key2 value2] [....]
```



获取key的值

```
GET key
```

批量获取key的值

```
MGET key1 [key2] [...] 
```



设置key的值为value，并指定key的过期时间为seconds秒

```
SETEX key seconds value

等效于
SET key value ex seconds
```



只有当key不存在时，才设置key的值为value

```
SETNX key value

等效于
SET key value nx
```



整形数据的自增自减

```
INCR key 		让整形key自增1
INCRBY key num		让key增加num
INCRBY key -1		让key自减1

```



浮点类型的增减

```
INCRBYFLOAT key num			让浮点类型的key增加num  
```









#### Redis哈希（Hash）操作命令

实际上哈希类型的数据就是一个哈希表

![image-20250326193028201](./pictures/image-20250326193028201.png)



将key所指的哈希表中field对应的值设置为value

```
HSET key field value
```

批量添加哈希表的字段

```
HMSET key field1 value1 field2 value2 [field3 value3] [....]
```

当哈希表中某个field不存在才添加相应的field并设置为value

```
HSETNX key field value
```





取出key哈希表中field对应的值

```
HGET key field
```

批量取出key哈希表中field对应的值

```
HMGET key field1 field2 [field3] [....]
```



取出key哈希表中的所有field和value

```
HGETALL key
```



删除key哈希表中field对应的值

```
HDEL key field
```



获取key哈希表中的所有field

```
HKEYS key
```



获取key哈希表中的所有value

```
HVALS key 
```



让key哈希表中field的值自增指定大小increment

```
HINCRBY key field increment
```



 

#### Redis列表（List）操作命令

列表List是一个简单的字符串列表，依照插入顺序排列

![image-20250326194341510](./pictures/image-20250326194341510.png)

将一个或多个数据插入列表头部（左边）

```
LPUSH key value1 [value2]
```

将一个或多个数据插入列表尾部（右边）

```
RPUSH key value1 [value2]
```



从列表中取出指定范围内的元素

其中 0 表示列表的第一个元素， 1 表示列表的第二个元素，以此类推。 你也可以使用负数下标，以 -1 表示列表的最后一个元素， -2 表示列表的倒数第二个元素，以此类推。

```
LRANGE key start stop
```



移出并获取列表的第一个元素（左边）

```
LPOP key
```

移出并获取列表的最后一个元素（右边）

```
RPOP key
```

BLPOP和BRPOP和LPOP、RPOP类似，只不过会在list没有元素时等待指定时间time，而不是返回nullkey 

```
BLPOP key time
```





获取列表长度

```
LLEN key
```







#### Redis集合（Set）操作命令

Set是字符串类型的无序集合

![image-20250326200135701](./pictures/image-20250326200135701.png)



向key集合添加一个或多个成员

```
SADD key member1 [member2]
```



返回key集合的所有成员

```
SMEMBERS key
```



判断key集合中是否存在member元素

```
SISMEMBER key member
```



获取key集合的成员数

```
SCARD key
```



返回指定所有集合的交集

```
SINTER key1 [key2]
```



返回指定所有集合的并集

```
SUNION key1 [key2]
```



返回指定所有集合的差集

```
SDIFF key1 [key2]
```



删除key集合中的一个或多个成员

```
SREM key memeber1 [member2]
```







#### Redis有序集合（zset）操作命令

有序集合是一个字符串类型的集合，不能重复，根据每个成员的score来排序

![image-20250326201441681](./pictures/image-20250326201441681.png)



zset有很多命令

![image-20250401100317207](./pictures/image-20250401100317207.png)



向key有序集合中添加一个或多个成员

```
ZADD key score1 rember1 [score2 rember2]
```



返回有序集合中指定范围的成员，带上WITHSCORES代表返回成员时会带上成员的score

```
ZRANGE key start stop [WITHSCORES]
```



为key有序集合中的member成员的score值增加increment

```
ZINCRBY key increment member
```



删除key有序集合中一个或多个成员

```
ZREM key member1 [member2]
```

 



#### 通用命令

通用命令不区分类型，所有类型都可以使用



查找所有符合指定模式（pattern）的key

```
KEYS pattern
keys *     返回所有key
keys set*  返回所有以set开头的key
keys *s*   返回包含字母s的key

```

由于Redis是单线程的，因此在模糊查询key时，会阻塞线程，因此在实际开发中不建议使用该命令



判断某个key是否存在

```
EXISTS key
```



返回key所存储的类型

```
TYPE key
```



删除存在的key

```
DEL key
```

批量删除

```
DEL key1 key2 key3 ...
```



为key设置有效期

```
EXPIRE key seconds
EXPIRE age 20			设置age这个key的有效期为20秒
```

查询key的剩余有效期

```
TTL key
TTL age					查询age这个key的剩余有效期
```

有效期为-2表示key已经过期

有效期为-1表示key是永久的

![image-20250401083455982](./pictures/image-20250401083455982.png)





#### Redis中key的分级存储

如果现在需要存储两种信息：一个用户信息，一个商品信息，它们中都有一个共同属性id，但redis中不允许存在重复的key，那要怎么同时存储这两个id呢？可以使用分级存储，分级存储就像是文件夹一样，既然同一个文件夹下不能存在同名，那就将这些同名的文件放在不同文件夹下呗。分级存储也是这个道理。

比如要同时存储用户的id和商品的id，可以这样设置key键

用户id

```
set info:usr:usr1 '{"id":1,"name":"sky"}'
```

商品id

```
set info:product:pro1 '{"id":3,"name":"pro1"}'
```

此时我们就可以通过图像化界面来看到存储数据的层级结构

![image-20250401090551250](./pictures/image-20250401090551250.png)

## Redis客户端

Redis客户端有以下几种，其中Spring Data Redis集成了Jedis和lettuce

![image-20250401105511860](./pictures/image-20250401105511860.png)



### Jedis快速入门

1.引入Jedis的依赖

```xml
    <dependency>
      <groupId>redis.clients</groupId>
      <artifactId>jedis</artifactId>
      <version>5.2.0</version>
    </dependency>
```



2.建立Redis连接

3.使用Jedis进行操作，命令与Redis原命令一致

4.释放资源

上面三步的整体代码如下

```java
import org.junit.jupiter.api.AfterEach;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import redis.clients.jedis.Jedis;

import java.util.HashMap;
import java.util.Map;

public class test {

    private Jedis jedis;

    //@BeforeEach注解表示该方法在测试方法每次执行前执行一次
    @BeforeEach
    public void init(){
        //建立连接
        jedis = new Jedis("120.26.90.87",6379);
        //输入密码
        jedis.auth("123456");
        //选择库
        jedis.select(0);
    }

    @Test
    public void testJedis(){
        //添加字符串数据
        jedis.set("Jedis","666");
        //获取字符串数据
        String data = jedis.get("Jedis");
        System.out.println("Jedis："+data);
    }
    @Test
    public void testHash(){
        //测试哈希类型的数据
        jedis.hset("user1","name","sky");
        jedis.hset("user1","age","21");

        //批量添加
        Map<String,String> user = new HashMap<>();
        user.put("name","arthur");
        user.put("age","22");
        jedis.hmset("user2",user);

        //获取哈希数据
        Map<String, String> user1 = jedis.hgetAll("user1");
        Map<String, String> user2 = jedis.hgetAll("user2");
        System.out.println("user1:"+user1);
        System.out.println("user2:"+user2);
    }

    //@AfterEach注解表示每次执行完测试方法后执行一次该方法
    @AfterEach
    public void tearDown(){
        //释放连接
        if(jedis!=null){
            jedis.close();
        }
    }


}
```

 



### Jedis连接池

Jedis本身是线程不安全的，并且频繁创建销毁连接会损耗性能，因此使用连接池会是一个更好的选择

首先创建一个连接工厂，用来获取连接，连接工厂使用的就是连接池

```java
import redis.clients.jedis.Jedis;
import redis.clients.jedis.JedisPool;
import redis.clients.jedis.JedisPoolConfig;

public class JedisConnectionFactory {
    private static final JedisPool jedisPool;

    static {
        //首先创建一个连接池的配置对象
        JedisPoolConfig jedisPoolConfig = new JedisPoolConfig();
        //配置Jedis连接池
        //设置最大连接
        jedisPoolConfig.setMaxTotal(8);
        //设置最大空闲连接
        jedisPoolConfig.setMaxIdle(8);
        //设置最小空闲连接
        jedisPoolConfig.setMinIdle(0);
        //设置最长等待时间 ms -1表示无限等待
        jedisPoolConfig.setMaxWaitMillis(200);

        //使用jedis配置对象创建jedisPool连接池对象
        jedisPool=new JedisPool(jedisPoolConfig,"120.26.90.87",6379,1000,"123456");

    }


    public static Jedis getJedis(){
        return jedisPool.getResource();
    }


}
```

此时获取连接对象就变成通过连接池来获取

![image-20250401113932148](./pictures/image-20250401113932148.png)





### Spring Data Redis

#### 1.导入Spring Data Redis的依赖

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-redis</artifactId>
</dependency>
```

如果要使用连接池还需要使用连接池依赖

```xml
<!--commons pool-->
<dependency>
    <groupId>org.apache.commons</groupId>
    <artifactId>commons-pool2</artifactId>
</dependency>
```

不管是Jedis还是lettuce，底层使用的连接池都是基于commons-pool



#### 2.配置Redis

```xml
spring:
  profiles:
    active: dev
  main:
    allow-circular-references: true
  redis:
    host: localhost
    port: 6379
    password: 123456
    database: 10			#指定使用哪一个数据库，Redis默认生成16个数据库，0~15，数据库之间是隔离的

```

如果要使用连接池，还需配置连接池的参数

```yaml
spring:
  data:
    redis:
      host:
      port:
      password:
      #配置连接池，如果使用的是Jedis，配置就要变成Jedis的
      lettuce:
        pool:
          max-active: 8     #最大连接
          max-idle: 8       #最大空闲连接
          min-idle: 0       #最小空闲连接
          max-wait: 200     #连接等待时间
```



![image-20250326210153572](./pictures/image-20250326210153572.png)



#### 3.编写配置类，创建RedisTemplate对象

```java
@Configuration
@Slf4j
public class RedisConfiguration {

    @Bean
    //RedisConnectionFactory导入的依赖已经自动创建并交给IOC容器管理了，因此这里我们可以直接通过依赖注入来获得
    public RedisTemplate redisTemplate(RedisConnectionFactory redisConnectionFactory){
        //创建一个RedisTemplate
        RedisTemplate redisTemplate = new RedisTemplate<>();
        //设置Redis的连接工厂对象
        redisTemplate.setConnectionFactory(redisConnectionFactory);
        //设置Redis的key的序列化器
        redisTemplate.setKeySerializer(new StringRedisSerializer());
        //哈希类型的key和value的序列化器需要单独设置，设置哈希类型数据的key（也就是field）的序列化器
        //redisTemplate.setHashKeySerializer(new StringRedisSerializer());
        //设置Redis的value的序列化器
        //redisTemplate.setValueSerializer(new GenericJackson2JsonRedisSerializer());
        //redisTemplate.setHashValueSerializer(new GenericJackson2JsonRedisSerializer());
        
        return redisTemplate;
    }
}
```

如果不设置Redis的序列化器，那么不管是key还是value，在存入Redis数据库时都要被默认序列化器序列化后再存入，但是默认序列化器的序列化后的可读性较差，并且对于key，没法存入原始的key，如：假如key为name，但经过序列化后会变成一连串的编码直接存入，就会导致实际上存入的key不是name。因此我们一般会设置KeySerializer为StringRedisSerializer，设置ValueSerializer为json序列化器：GenericJackson2JsonRedisSerializer()。

但是使用json序列化器会导致一个问题，如下图

![image-20250402093521160](./pictures/image-20250402093521160.png)

在将对象序列化时，同时添加了改对象的类的字节码，这是为了在反序列化时能够知道该对象到底是一个什么类的对象。但是添加的字节码的大小比我们真正内容的大小还要大，这就造成了空间的浪费。

因此在实际开发中，建议key和value的序列化器都使用StringRedisSerializer，然后手动对对象进行序列化和反序列化。

Spring默认提供了一个StringRedisTemplate类，它的key和value的序列化器使用的就是StringRedisSerializer，因此我们可以通过依赖注入来直接使用这个类，省去了我们自己配置这个类的代码。



#### 4.使用RedisTemplate对象操作Redis

前面讲的所有命令在Java中的使用示例如下

```java
@SpringBootTest
public class SpringDataRedisTest {

    @Autowired
    RedisTemplate redisTemplate;

    @Test
    public void testRedisTemplate(){
        //使用RedisTemplate来创建操作Redis每种数据类型的对象
        System.out.println(redisTemplate);
        //创建操作Redis字符串类型数据的对象
        ValueOperations valueOperations = redisTemplate.opsForValue();
        //创建操作Redis哈希类型数据的对象
        HashOperations hashOperations = redisTemplate.opsForHash();
        //创建操作Redis列表类型数据的对象
        ListOperations listOperations = redisTemplate.opsForList();
        //创建操作Redis集合类型数据的对象
        SetOperations setOperations = redisTemplate.opsForSet();
        //创建操作Redis有序集合类型数据的对象
        ZSetOperations zSetOperations = redisTemplate.opsForZSet();
    }

    /**
     * 通过RedisTemplate对象来操作Redis的字符串类型数据
     */
    @Test
    public void testStringOperation(){
        ValueOperations valueOperations = redisTemplate.opsForValue();
        //Redis中的set命令，value的参数可以是任意类型的对象，最终都会被转换成字符串类型存入Redis数据库
        valueOperations.set("name","Arthur");
        //Redis中的get命令
        String name = (String) valueOperations.get("name");
        System.out.println(name);

        //Redis中的setex命令
        valueOperations.set("age",21,1, TimeUnit.MINUTES);
        //Redis中的setnx命令
        valueOperations.setIfAbsent("hobby","java");
        System.out.println(valueOperations.get("hobby"));   //java
        valueOperations.setIfAbsent("hobby","C++");
        System.out.println(valueOperations.get("hobby"));   //还是java

    }

    /**
     * 通过RedisTemplate对象来操作Redis的哈希类型数据
     */
    @Test
    public void testHashOperation(){
        HashOperations hashOperations = redisTemplate.opsForHash();

        //Redis中的hset命令
        hashOperations.put("people","name","张三");
        hashOperations.put("people","age",21);

        //Redis中的hget命令
        System.out.println(hashOperations.get("people", "name"));       //张三
        System.out.println(hashOperations.get("people", "age"));        //21

        //Redis中的hkeys命令
        Set keys = hashOperations.keys("people");
        System.out.println(keys);

        //Redis中的hvals命令
        List values = hashOperations.values("people");
        System.out.println(values);

        //Redis中的hdel命令
        hashOperations.delete("people","age");

    }

    /**
     * 通过RedisTemplate对象来操作Redis的列表类型数据
     */
    @Test
    public void testListOperation(){
        ListOperations listOperations = redisTemplate.opsForList();
        //Redis中的lpush命令
        listOperations.leftPushAll("list","a","b","c");
        listOperations.leftPush("list","d");

        //Redis中的lrange命令
        List list = listOperations.range("list", 0, -1);
        System.out.println(list);

        //Redis中的rpop命令
        System.out.println(listOperations.rightPop("list"));        //a

        //Redis中的llen命令
        System.out.println(listOperations.size("list"));            //3
    }


    /**
     * 通过RedisTemplate对象来操作Redis的集合类型数据
     */
    @Test
    public void testSetOperation(){
        SetOperations setOperations = redisTemplate.opsForSet();
        //Redis中的sadd命令
        setOperations.add("set1","a","b","c","d");
        setOperations.add("set2","a","b","x","y");

        //Redis中的smembers命令
        Set set1 = setOperations.members("set1");
        System.out.println(set1);

        //Redis中的scard命令
        System.out.println(setOperations.size("set1"));       //4

        //Redis中的sinter
        Set intersect = setOperations.intersect("set1", "set2");
        System.out.println(intersect);

        //Redis中的sunion命令
        Set union = setOperations.union("set1", "set2");
        System.out.println(union);

        //Redis中的srem命令
        setOperations.remove("set1","a","b");

    }

    /**
     * 通过RedisTemplate对象来操作Redis的有序集合类型数据
     */
    @Test
    public void testZSetOperation(){
        ZSetOperations zSetOperations = redisTemplate.opsForZSet();

        //Redis中的zadd命令
        zSetOperations.add("zset","a",10.2);
        zSetOperations.add("zset","b",10);
        zSetOperations.add("zset","c",11);

        //Redis中的zrange命令
        Set zset = zSetOperations.range("zset", 0, -1);
        System.out.println(zset);

        //Redis中的zincrby
        zSetOperations.incrementScore("zset","a",5.0);
        zset = zSetOperations.range("zset", 0, -1);
        System.out.println(zset);

        //Redis中的zrem命令
        zSetOperations.remove("zset","a");

    }


    /**
     * 通用命令
     */
    @Test
    public void testCommonOperation(){
        //Redis中的keys命令
        Set keys = redisTemplate.keys("*");
        System.out.println(keys);

        //Redis中的exists 命令
        System.out.println(redisTemplate.hasKey("list"));       //true
        System.out.println(redisTemplate.hasKey("abc"));        //false

        //Redis中的type命令
        for (Object key : keys) {
            System.out.println(redisTemplate.type(key));
        }

        //Redis中的del命令
        redisTemplate.delete("people");

    }
}
```



## 黑马点评实战

### 项目导入问题

我在导入项目时遇到了两个问题

1.Redis死循环

启动项目后控制台一直报这样一个错误：NOGROUP No such key 'stream.orders' or consumer group 'g1' in XREADGROUP with GROUP option

解决方法：

在Redis中输入命令

```
XGROUP CREATE stream.orders g1 0 MKSTREAM
XGROUP CREATE 队列名称  组名称  起始id  MKSTREAM不存在则自动创建
```



2.MySQL一直报错：Public Key Retrieval is not allowed

这是MySQL8.0及以上版本会出现的问题，默认情况下禁用了通过公钥检索用户密码的功能。

在旧版本的 MySQL 中，客户端连接到服务器时，可以使用公钥来检索用户密码。这种机制称为 “public key retrieval”，它允许客户端使用公钥来解密在服务器端加密的密码。然而，为了提高安全性，MySQL 开发团队在较新的版本中禁用了这个功能。禁用公钥检索可以防止恶意用户通过获取公钥来获取用户密码。

解决这个问题可以在配置MySQL连接路径是添加如下配置

```
allowPublicKeyRetrieval=true
```

即：

![image-20250403112027137](./pictures/image-20250403112027137.png)



### 短信登录功能

#### 基于Session

实现短信登录功能可以基于Session来实现，即生成验证码后将验证码code存到Session中，当用户输入验证码进行登录时就可以根据用户请求的SessionID来从对应的Session中取出验证码code，接着进行比对即可完成登录校验。

但是这种方式存在Session共享问题：多台Tomcat服务器间的Session不共享，实际生产环境中，服务端通常部署在多台服务器上，由nginx来负载均衡，因此用户多次请求时访问的服务器很可能不是同一台，此时由于Session不共享，原本用户的Session信息就会丢失。



#### 基于Redis

基于Redis来实现本功能时，我们可以将生成的验证码code放在Redis数据库中，而多台Tomcat可以使用同一个Redis服务器，因此就可以解决Session共享问题。

实现思路如下：

用户发送验证码请求，生成验证码，以用户的手机号作为key，将验证码存入Redis中。

当用户使用验证码进行登录时，根据用户提供的手机号去Redis中查询验证码并进行校验，如果校验通过就再从mysql数据库中查询该用户以判断该用户是否为新用户，如果为新用户就创建新用户保存到数据库中，并将用户信息保存到Redis中，保存用户信息的key使用UUID生成的token（不使用手机号是为了避免用户手机号信息泄露），然后将token返回给客户端，客户端下次发起请求时就会带上这个token。

![image-20250406225615691](./pictures/image-20250406225615691.png)





##### 1.定义拦截器

```java
public class LoginInteceptor implements HandlerInterceptor {
    
    //要先准备好操作Redis的类
    private StringRedisTemplate stringRedisTemplate;

    public LoginInteceptor(StringRedisTemplate stringRedisTemplate) {
        this.stringRedisTemplate = stringRedisTemplate;
    }

    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
        //获取token，不再获取Session
        //HttpSession session = request.getSession();
        Object token = request.getHeader("authorization");
        
        //从Redis中获取用户信息
        //Object user = session.getAttribute("user");
        String key = RedisConstants.LOGIN_USER_KEY+token;

        Map<Object, Object> userMap = stringRedisTemplate.opsForHash().entries(key);
        //判断用户是否存在，这里不用判断空指针，因为entries做了处理，如果没有对应的键，返回的是一个空的集合。
        if (userMap.isEmpty()) {
            //不存在则拦截请求
            response.setStatus(401);
            return false;
        }
        //将获取到的map转换成用户信息对象
        UserDTO user = BeanUtil.fillBeanWithMap(userMap, new UserDTO(), false);

        //存在则将用户信息存入LocalThread中，然后放行
        UserHolder.saveUser(user);
        /*刷新token的过期时间，只有当用户超过30分钟未访问才进行清除用户登录状态
        反之如果用户有持续访问，就要在每次访问呢时刷新过期时间。*/
        stringRedisTemplate.expire(key,RedisConstants.LOGIN_USER_TTL, TimeUnit.SECONDS);
        //放行
        return true;

    }


    @Override
    public void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex) throws Exception {
        UserHolder.removeUser();
    }
}
```



##### 2.注册拦截器

```java
@Configuration
public class MVCConfig implements WebMvcConfigurer {

    @Autowired
    StringRedisTemplate stringRedisTemplate;

    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(new LoginInteceptor(stringRedisTemplate)).excludePathPatterns(
                "/user/login",
                "/user/code",
                "/shop/**",
                "/voucher/**",
                "/shop-type/**",
                "upload/**",
                "blog/hot"
        );
    }
}
```

##### 3.Controller层

```java
/**
 * 发送手机验证码
 */
@PostMapping("code")
public Result sendCode(@RequestParam("phone") String phone, HttpSession session) {
    return userInfoService.sendCode(phone,session);

}

/**
 * 登录功能
 * @param loginForm 登录参数，包含手机号、验证码；或者手机号、密码
 */
@PostMapping("/login")
public Result login(@RequestBody LoginFormDTO loginForm, HttpSession session){
    // 实现登录功能
    //return Result.fail("功能待完成");
    return userService.login(loginForm,session);
}
```



##### 4.Service层

userInfoService

```java
@Service
@Slf4j
public class UserInfoServiceImpl extends ServiceImpl<UserInfoMapper, UserInfo> implements IUserInfoService {

    //直接使用Spring提供的StringRedisTemplate
    @Autowired
    StringRedisTemplate stringRedisTemplate;

    /**
     * 发送手机验证码
     *
     * @param phone
     * @param session
     * @return
     */
    @Override
    public Result sendCode(String phone, HttpSession session) {
        //1.校验手机号是否合法
        if (phone == null || !phone.matches(RegexPatterns.PHONE_REGEX)) {
            //2.如果不合法直接返回错误
            return Result.fail("请输入正确的手机号");

        }
        //3.如果合法就生成一个随机验证码
        String code = RandomUtil.randomNumbers(6);

        //4.将验证码存入Redis
        //session.setAttribute("code",code);
        stringRedisTemplate.opsForValue().set(RedisConstants.LOGIN_CODE_KEY+phone,code,RedisConstants.LOGIN_CODE_TTL, TimeUnit.MINUTES);



        //5.为用户发送验证码，暂时不实现发送验证码的功能
        log.debug("发送验证码：{}",code);

        return Result.ok();
    }
}
```



userService

```java
@Service
public class UserServiceImpl extends ServiceImpl<UserMapper, User> implements IUserService {

    @Autowired
    StringRedisTemplate stringRedisTemplate;

    /**
     * 用户登录
     * @param loginForm
     * @param session
     * @return
     */
    @Override
    public Result login(LoginFormDTO loginForm, HttpSession session) {
        //1.验证手机号
        String phone = loginForm.getPhone();
        if(phone==null|| RegexUtils.isPhoneInvalid(phone)){
            //手机号不合法
            return Result.fail("手机号错误");
        }
        //2.校验验证码
        String cacheCode = stringRedisTemplate.opsForValue().get(RedisConstants.LOGIN_CODE_KEY+phone);
        String code = loginForm.getCode();
        if(code==null||!code.equals(cacheCode)){
            //验证码校验失败
            return Result.fail("验证码错误");
        }
        //3.如果验证码通过，就在数据库中查询用户
        User user = query().eq("phone", phone).one();

        //4.如果数据库中不存在用户，则将该新用户存入数据库
        if(user==null){
            user = createUserWithPhone(phone);
        }

        //5.将用户信息存入Redis
        UserDTO userDTO = new UserDTO();
        BeanUtils.copyProperties(user,userDTO);
        //生成token作为键值
        String token = UUID.randomUUID().toString(true);
        //由于使用的是StringRedisTemplate来操作Redis，StringRedisTemplate要求key和value都要为String类型，所以这里要对对象中的数据处理一下
        Map<String, Object> userMap = BeanUtil.beanToMap(user,new HashMap<>(),CopyOptions.create()
                .setIgnoreNullValue(true)
                .setFieldValueEditor((fileName,fileValue)->fileValue.toString()));
        //将用户信息存入Redis
        stringRedisTemplate.opsForHash().putAll(RedisConstants.LOGIN_USER_KEY+token,userMap);
        //设置token过期时间
        stringRedisTemplate.expire(RedisConstants.LOGIN_USER_KEY+phone,RedisConstants.LOGIN_USER_TTL, TimeUnit.SECONDS);

        //不使用Session
        //session.setAttribute("user",userDTO);

        //返回token
        return Result.ok(token);
    }

    private User createUserWithPhone(String phone) {
        User user = new User();
        user.setPhone(phone);
        user.setNickName(SystemConstants.USER_NICK_NAME_PREFIX+phone);
        save(user);
        return user;
    }
}
```





#### 登录状态刷新问题

上面实现了短信登录的功能，但是仍然存在一个问题，我们刷新用户登录状态的操作是在拦截器中进行的，但是如果用户访问的是不需要拦截的路径，我们就无法刷新用户的登录状态了。

要解决这个问题我们可以在原来的基础上再加一层拦截器，这层拦截器拦截所有请求路径，拦截到请求后就在Redis中查询用户信息，如果查到用户信息，就刷新过期时间。

![image-20250407084458622](./pictures/image-20250407084458622.png)



新增RefreshInterceptor，用于刷新登录状态

```java
public class RefreshInteceptor implements HandlerInterceptor {

    //要先准备好操作Redis的类
    private StringRedisTemplate stringRedisTemplate;

    public RefreshInteceptor(StringRedisTemplate stringRedisTemplate) {
        this.stringRedisTemplate = stringRedisTemplate;
    }

    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
        //获取token，不再获取Session
        //HttpSession session = request.getSession();
        Object token = request.getHeader("authorization");
        
        //从Redis中获取用户信息
        //Object user = session.getAttribute("user");
        String key = RedisConstants.LOGIN_USER_KEY+token;

        Map<Object, Object> userMap = stringRedisTemplate.opsForHash().entries(key);
        //判断用户是否存在，这里不用判断空指针，因为entries做了处理，如果没有对应的键，返回的是一个空的集合。
        if (userMap.isEmpty()) {
            //不存在直接放行
            return true;
        }
        //将获取到的map转换成用户信息对象
        UserDTO user = BeanUtil.fillBeanWithMap(userMap, new UserDTO(), false);

        //存在则将用户信息存入LocalThread中，然后放行
        UserHolder.saveUser(user);
        /*刷新token的过期时间，只有当用户超过30分钟未访问才进行清除用户登录状态
        反之如果用户有持续访问，就要在每次访问呢时刷新过期时间。*/
        stringRedisTemplate.expire(key,RedisConstants.LOGIN_USER_TTL, TimeUnit.SECONDS);
        //放行
        return true;

    }


    @Override
    public void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex) throws Exception {
        UserHolder.removeUser();
    }
}
```

修改原来的拦截器

```java
public class LoginInteceptor implements HandlerInterceptor {
    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) {
        //从ThreadLocal中获取用户信息
        UserDTO user = UserHolder.getUser();
        if(user==null){
            //如果用户不存在，就拦截请求
            response.setStatus(401);
            return false;
        }
        //用户存在则放行
        return true;

    }
}
```

注册拦截器

指定拦截器的order，来保证拦截器的执行顺序

```java
@Configuration
public class MVCConfig implements WebMvcConfigurer {

    @Autowired
    StringRedisTemplate stringRedisTemplate;

    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(new LoginInteceptor()).excludePathPatterns(
                "/user/login",
                "/user/code",
                "/shop/**",
                "/voucher/**",
                "/shop-type/**",
                "/upload/**",
                "/blog/hot"
        ).order(1);
        registry.addInterceptor(new RefreshInteceptor(stringRedisTemplate)).addPathPatterns("/**").order(0);
    }
}
```





### 商户查询缓存

#### 缓存的优缺点

优点：

1.降低后端负载

2.提高读写效率，降低响应时间

缺点：

1.会导致数据一致性问题

2.代码维护成本较高（使用缓存，要在代码中添加保证数据一致性的代码等）

3.运维成本提高（需要额外维护用于缓存的数据库集群）。





#### 实现缓存商户

实现流程思路如下

![image-20250407093329233](./pictures/image-20250407093329233.png)



```java
@Service
public class ShopServiceImpl extends ServiceImpl<ShopMapper, Shop> implements IShopService {

    @Resource
    StringRedisTemplate stringRedisTemplate;

    /**
     * 根据id查询商户
     * @param id
     * @return
     */
    @Override
    public Result queryById(Long id) {
        String key = RedisConstants.CACHE_SHOP_KEY+id;
        //1.查询缓存
        String shopJson = stringRedisTemplate.opsForValue().get(key);
        //2.缓存中存在商户信息，直接返回
        if(StrUtil.isNotBlank(shopJson)){
            Shop shop = JSONUtil.toBean(shopJson,Shop.class);
            return Result.ok(shop);
        }

        //3.不存在商户信息，查询数据库
        Shop shop = getById(id);
        //4.数据库不存在商户信息，返回404
        if(shop==null){
            return Result.fail("店铺不存在");
        }
        //5.存在商户信息，将信息存入缓存
        stringRedisTemplate.opsForValue().set(key,JSONUtil.toJsonStr(shop));
        //6.返回商户信息
        return Result.ok(shop);
    }
}
```







### 缓存更新策略

为了保证Redis与数据库中的数据保持一致，我们需要对Redis中的数据进行更新。

#### 三种缓存更新策略

下面有三种缓存更新策略

1.内存淘汰。当内存空间不足时，会自动删除一些缓存，Redis默认使用内存淘汰策略

2.超时剔除。给缓存设定过期时间，过期后自动删除缓存

3.主动更新。自己编写代码，每当数据发生变化就更新缓存

对于低一致性需求的业务，比如店铺类型数据，这些不经常变化的数据可以采用内存淘汰策略。

对于高一致性需求的业务，则采用主动更新策略，还可以用超时剔除策略来辅助（保底，就算没能主动更新成功，过期了也会自动删除缓存）。



#### 主动更新策略的实现方式

实现主动更新策略的方式也有多种

1.自己写代码来实现，在改动数据的同时更新缓存

2.将缓存与数据库整合为一个服务，由这个服务来保证缓存与数据库的一致性。无需开发者操心。

3.开发者只操作缓存，有其他线程异步地将缓存数据持久化到数据库中，保证数据的最终一致性。





#### 主动更新策略实现

这里我们采用第一种实现方式。

通过代码来实现改动数据的同时更新缓存。

要实现这个功能首先要考虑下面三个问题：

1.删除缓存还是更新缓存

一般选择直接删除缓存。因为如果选择更新缓存，那么每次更新数据库时都要更新缓存，但是可能在更新数据库那段时间并没有那么多访问请求，也就是说就算更新了缓存也没人访问，无效写操作较多。



2.如何保证对数据库和缓存的操作同时成功或失败

对于单体系统，我们可以将对缓存和数据库的操作放在同一个事务中。但是这种方式不能用于分布式系统

对于分布式系统，利用TCC等分布式事务方案（还没学过，想学的话去学微服务）



3.先操作缓存还是先操作数据库（线程安全问题）

先操作缓存会导致线程不安全的发生概率较高，因此先操作数据库。

因为操作缓存的速度比操作数据库的操作快很多，如果先操作缓存，在操作数据库的时候，可能数据库数据还没更新成功，其他线程就又会查询数据库将旧数据又放回缓存中。但是先操作数据库就会让这种可能大大降低，因为先操作完数据库后，操作缓存的速度非常快，很快就执行完了，执行时其他线程突然插进来执行的概率会变低。



#### 优化缓存商户功能（缓存更新）

当商户更新时我们需要同步更新缓存，以此保证数据的一致性。这里更新缓存采用的方式是直接删除原来的缓存。

下面是更新商户信息的功能代码

```java
/**
 * 更新商铺信息
 * @param shop
 * @return
 */
@Override
//开启事务
@Transactional
public Result update(Shop shop) {
    if(shop.getId()==null){
        return Result.fail("店铺id不能为空");
    }
    //更新数据库（先操作数据库，再操作缓存）
    updateById(shop);
    //删除缓存
    stringRedisTemplate.delete(RedisConstants.CACHE_SHOP_KEY+shop.getId());
    return Result.ok();
}
```







### 缓存穿透

#### 什么是缓存穿透

缓存穿透指的是客户端请求的数据在缓存和数据库中都不存在，这样缓存就永远不会生效，这些请求会全部打到数据库上，容易导致数据库服务崩溃。



#### 缓存穿透的解决方法

##### 1.缓存空值

如果一个请求查询数据库发现没有对应的数据，那么就将空值缓存到缓存中，这样这个请求下次来就不会造成缓存穿透了。

这种方式实现起来相对简单，但是有如下缺点：

1）会造成额外的内存消耗

2）会导致短期的数据不一致性。

如果将空值缓存到缓存中的这期间，在该缓存过期之前，如果正好该请求对应的数据就存储到数据库中了，就会导致数据不一致性，因为此时缓存的还是空值，但数据库里有刚存进来的值，只有当空值缓存过期后才能重新恢复一致性。



##### 2.布隆过滤

布隆过滤是在请求到达Redis之前再加一层布隆过滤器，布隆过滤器的作用是判断该请求对应的数据是否存在，如果存在则放行，如果不存在则直接拒绝请求。

布隆过滤器可以看成是一个byte数组，存储二进制位，数据库中存储的数据会基于某个哈希算法计算出其哈希值，再将哈希转转换为二级制位保存到布隆过滤器中，当我们判断请求的数据是否存在时，其实就是判断这个数据对应的位置是0还是1，以此判断数据是否存在。这种判断结果并不完全准确，它是一种基于概率上的结果，如果判断为不存在那就一定不存在，如果判断为存在就不一定存在。



布隆过滤虽然内存消耗小，没有存储多余的key，但是它有如下缺点：

1）实现复杂

2）存在误判可能



##### 3.减少会导致缓存穿透的请求

上面两种解决缓存穿透的方法是属于被动解决方法，就是别人已经发出了会导致缓存穿透的请求，我们来处理这个请求。那我们其实还可以采取一些措施主动地去减少会导致缓存穿透的请求。

下面是一些减少会导致缓存穿透的请求的数量的方法

1.增强请求路径的复杂度，比如对于请求路径携带的id值，我们可以刻意去设计id的格式，让别人难以猜测id的规律，这样我们在收到请求时只需要判断id是否合法就能够过滤掉很多会导致缓存穿透的请求了。

2.可以加强用户的权限校验，避免用户发出超出权限的请求。

3.可以对热点参数进行限流。让用户短时间内无法频繁发出请求。



#### 解决缓存穿透（缓存空值）

这里解决缓存穿透采用的方式是缓存空值。

```java
/**
 * 根据id查询商户
 * @param id
 * @return
 */
@Override
public Result queryById(Long id) {
    String key = RedisConstants.CACHE_SHOP_KEY+id;
    //1.查询缓存
    String shopJson = stringRedisTemplate.opsForValue().get(key);
    //2.缓存中存在商户信息，直接返回
    if(StrUtil.isNotBlank(shopJson)){
        Shop shop = JSONUtil.toBean(shopJson,Shop.class);
        return Result.ok(shop);
    }

    //解决缓存穿透，如果缓存为空值，说明信息不存在
    if(shopJson!=null){
        return Result.fail("店铺不存在");
    }

    //3.不存在商户信息，查询数据库
    Shop shop = getById(id);
    //4.数据库不存在商户信息，返回404
    if(shop==null){
        //并向缓存存入空值
        stringRedisTemplate.opsForValue().set(key,"",RedisConstants.CACHE_NULL_TTL,TimeUnit.MINUTES);
        return Result.fail("店铺不存在");
    }
    //5.存在商户信息，将信息存入缓存
    stringRedisTemplate.opsForValue().set(key,JSONUtil.toJsonStr(shop),RedisConstants.CACHE_SHOP_TTL, TimeUnit.MINUTES);
    //6.返回商户信息
    return Result.ok(shop);
}
```







### 缓存雪崩

#### 什么是缓存雪崩

缓存雪崩指的是在某一时刻，缓存中大量的key在同一时间失效，或者缓存服务直接宕机，导致大量请求一瞬间同时到达数据库，造成数据库服务的巨大压力甚至崩溃。



#### 如何解决缓存雪崩

##### 1.给不同的key的TTL设置为随机值

比如在缓存预热的时候存入TTL为随机值的缓存数据，这样就不会出现在同一时刻大量key失效的情况。



##### 2.利用Redis集群提高服务的可用性

微服务里面学



##### 3.给缓存业务添加降级限流策略

微服务里面学



##### 4.给业务添加多级缓存

微服务和Redis高级都有学





### 缓存击穿

#### 什么是缓存击穿

缓存击穿问题也叫热点key问题，指的是在一个被高并发访问（热点）并且缓存重构业务复杂（如：查询涉及多个表）的key突然失效了，大量的请求会瞬间给数据库带来巨大的压力。





#### 如何解决缓存击穿

##### 1.互斥锁

当key失效需要重新构建缓存时，需要先获取锁，然后才能执行缓存重构的业务，这样的话就只会有一个线程来访问数据库，减轻了数据库的压力。

其他未获得锁的线程会等待一段时间，然后重新查询缓存，如果缓存命中就可以直接返回，如果缓存没有命中就再尝试获取锁以执行缓存重构业务，如果又没有获取到锁，就再等待一段时间，重复上述流程。

![image-20250407212414061](./pictures/image-20250407212414061.png)



##### 2.逻辑过期

逻辑过期指的是在缓存数据时多缓存一个expire数据，expire数据就表示过期时间，但是这个expire是放在缓存数据里的，实际的缓存是没有设置过期时间的，这样无论如何请求都能够命中缓存，只不过需要根据获取到的缓存数据中的expire来判断该缓存是否过期，如果过期就执行缓存重构业务，执行缓存重构业务之前同样需要获取互斥锁，但与上面讲的方式不同，这里获取到互斥锁后会再创建一个新的线程来单独执行缓存重构业务，而原本的线程则会直接返回旧的数据。其他没有获取到互斥锁的线程，也不会等待，而是直接返回旧数据。

![image-20250407212943064](./pictures/image-20250407212943064.png)





#### 缓存击穿解决方法的比较

![image-20250407213423497](./pictures/image-20250407213423497.png)

互斥锁的死锁风险：

如果一个缓存重构业务涉及到多个缓存，就可能需要获取多个锁，此时如果有多个线程，一个线程获取了一个锁还需要获取另一个锁，但另一个锁又被其他线程获取了，这个时候这两个线程都在等待获取剩下的锁，这就导致了死锁



逻辑过期的额外内存消耗指的是需要额外存储expire信息。







#### 解决缓存击穿（互斥锁）

##### 1.如何实现互斥锁

互斥锁实现是通过Redis的setnx来实现的，setnx有一个特点就是只有当key不存在时才能赋值成功，因此利用这个特性，我们可以在获取锁时尝试使用setnx来给key赋值，如果赋值成功说明获取到锁，如果获取失败说明锁被占用，如下图所示，第一次给key为lock的键赋值，成功，代表获取锁，第二次赋值失败，代表锁已经被占用。

![image-20250408132325997](./pictures/image-20250408132325997.png)



##### 2.解决缓存击穿

有了如何实现互斥锁的知识，我们才能解决缓存击穿问题。在原来实现商铺缓存的逻辑上进行修改，当缓存未命中时不再直接访问数据库，而是先尝试获取锁，如果获取锁成功才会访问数据库，如果获取锁失败，则等待一段时间后再次尝试获取缓存，如果这时候缓存获取成功则直接返回，如果失败就继续尝试获取锁，就这样一直循环。

![image-20250408133210289](./pictures/image-20250408133210289.png)

```java
/**
 * 根据id查询商户
 *
 * @param id
 * @return
 */
@Override
public Result queryById(Long id) {
    String key = RedisConstants.CACHE_SHOP_KEY + id;
    //.查询缓存
    Shop shop = getCache(id);
    if (shop != null) {
        return Result.ok(shop);
    }
    String s = stringRedisTemplate.opsForValue().get(key);
    if (s != null && StrUtil.isBlank(s)) {
        return Result.fail("店铺不存在");
    }

    //下面解决缓存击穿
    //.如果缓存中不存在商户信息，尝试获取锁
    try {
        Boolean flag = tryLock(RedisConstants.LOCK_SHOP_KEY + id);
        while (!flag) {
            //如果没有获取到锁，等待一段时间后再次查询缓存，存在则返回，不存在就再次尝试获取锁
            Thread.sleep(10);
            //再次查询缓存
            shop = getCache(id);
            if (shop != null) {
                //缓存存在则直接返回
                return Result.ok(shop);
            }
            s = stringRedisTemplate.opsForValue().get(key);
            if (s != null && StrUtil.isBlank(s)) {
                return Result.fail("店铺不存在");
            }else{
                //缓存不存在则再次尝试获取锁
                flag = tryLock(RedisConstants.LOCK_SHOP_KEY + id);
            }
        }

        //如果获取到锁，查询数据库
        //模拟一下高并发
        Thread.sleep(200);
        shop = getById(id);
        //4.数据库不存在商户信息，返回404
        if (shop == null) {
            //并向缓存存入空值
            stringRedisTemplate.opsForValue().set(key, "", RedisConstants.CACHE_NULL_TTL, TimeUnit.MINUTES);
            return Result.fail("店铺不存在");
        }
        //5.存在商户信息，将信息存入缓存
        stringRedisTemplate.opsForValue().set(key, JSONUtil.toJsonStr(shop), RedisConstants.CACHE_SHOP_TTL, TimeUnit.MINUTES);
        //6.返回商户信息
        return Result.ok(shop);
    } catch (InterruptedException e) {
        throw new RuntimeException(e);
    } finally {
        //最后别忘了释放锁
        unLock(RedisConstants.LOCK_SHOP_KEY + id);
    }

}
/**
 * 获取操作缓存的锁
 *
 * @param key
 * @return
 */
private Boolean tryLock(String key) {
    //尝试获取锁
    Boolean flag = stringRedisTemplate.opsForValue().setIfAbsent(key, "1", RedisConstants.LOCK_SHOP_TTL, TimeUnit.SECONDS);
    //返回获取结果
    return flag;
}

/**
 * 释放锁
 *
 * @param key
 */
private void unLock(String key) {
    stringRedisTemplate.delete(key);
}

/**
 * 尝试获取缓存
 * @param id
 * @return
 */
private Shop getCache(Long id) {
    String key = RedisConstants.CACHE_SHOP_KEY + id;
    //1.查询缓存
    String shopJson = stringRedisTemplate.opsForValue().get(key);
    //2.缓存中存在商户信息，直接返回
    if (StrUtil.isNotBlank(shopJson)) {
        Shop shop = JSONUtil.toBean(shopJson, Shop.class);
        return shop;
    }

    //解决缓存穿透，如果缓存为空值，说明信息不存在
    return null;
}
```



#### 解决缓存击穿（逻辑过期）

采用逻辑过期方式，需要提前预热缓存，即将热点数据提前存入缓存中，并且该缓存永不过期（但是会逻辑过期），也就是说一定能够在缓存中查到该数据，只不过需要判断该数据是否过期。如果没有查询到该数据，说明查询目标不存在。

数据过期后，需要获取锁，如果获取成功，则新建一个线程来重构缓存，然后返回过期数据；如果获取失败则直接返回过期数据。

![image-20250408192218125](./pictures/image-20250408192218125.png)

需要有一个实体类来封装数据和逻辑过期时间

```java
/**
 * 逻辑缓存用的Redis数据实体类
 */
@Data
@AllArgsConstructor
@NoArgsConstructor
public class RedisData {
    private LocalDateTime expire;
    private Object data;

}
```

```java
//使用线程池来进行缓存重构,简单创建线程数为10的线程池
private static final ExecutorService CACHE_REBUILD_EXECUTOR = Executors.newFixedThreadPool(10);

/**
 * 根据id查询商户
 *
 * @param id
 * @return
 */
@Override
public Result queryById(Long id) {
    String key = RedisConstants.CACHE_SHOP_KEY + id;
    //查询缓存
    RedisData redisData = getCacheWithLogicExpire(key);
    //如果缓存不存在直接返回
    if(redisData==null){
        return Result.fail("店铺不存在");
    }
    //将查询结果反序列化
    Shop shop = JSONUtil.toBean((JSONObject) redisData.getData(), Shop.class);
    LocalDateTime expire = redisData.getExpire();
    //接下来解决缓存击穿问题，采用逻辑锁的方式
    //检查缓存是否过期
    if (expire.isAfter(LocalDateTime.now())) {
        //未过期，直接返回缓存信息
        return Result.ok(shop);

    }
    //已过期，需要进行缓存重建
    //先尝试获取锁
    Boolean flag = tryLock(RedisConstants.LOCK_SHOP_KEY+id);
    if (flag) {
        //锁获取成功，开启新线程进行缓存重建，然后直接返回旧数据
        //锁获取成功后再次尝试获取缓存，做二次校验
        redisData = getCacheWithLogicExpire(key);
        //如果二次校验结果仍然是过期时间就新建线程进行缓存重构
        if(redisData.getExpire().isBefore(LocalDateTime.now())){
            // TODO 新建线程重构缓存
            CACHE_REBUILD_EXECUTOR.submit(()->{
                try{
                    // TODO 过期时间暂时设定为30s，为了方便测试
                    saveShop2Redis(id,30L);
                } catch (InterruptedException e) {
                    throw new RuntimeException(e);
                } finally {
                    //最后别忘了释放锁
                    unLock(RedisConstants.LOCK_SHOP_KEY+id);
                }
            });
        }else{
            unLock(RedisConstants.LOCK_SHOP_KEY+id);
        }
    }
    //锁获取失败或者成功创建新线程后，直接返回数据
    shop = JSONUtil.toBean((JSONObject) redisData.getData(), Shop.class);
    return Result.ok(shop);
}


/**
 * 构建缓存（逻辑过期）
 *
 * @param id
 */
@Override
public void saveShop2Redis(Long id, Long expireSeconds) throws InterruptedException {
    String key = RedisConstants.CACHE_SHOP_KEY + id;
    //查询数据库
    //模拟高并发
    Thread.sleep(200);
    Shop shop = getById(id);
    //封装数据，封装expire逻辑过期时间
    RedisData redisData = new RedisData(LocalDateTime.now().plusSeconds(expireSeconds), shop);
    //将封装后的数据存入Redis
    stringRedisTemplate.opsForValue().set(key, JSONUtil.toJsonStr(redisData));

}

/**
 * 获取缓存（逻辑过期）
 * @return
 */
private RedisData getCacheWithLogicExpire(String key){
    //查询缓存
    String shopJson = stringRedisTemplate.opsForValue().get(key);
    //如果查询为空，直接返回，因为使用逻辑过期时一般会提前预热缓存，也就是说如果店铺存在，在缓存中就一定有，不会查出空值
    if (StrUtil.isBlank(shopJson)) {
        return null;
    }
    //将查询结果反序列化
    RedisData redisData = JSONUtil.toBean(shopJson, RedisData.class);
    return redisData;
}


/**
 * 获取操作缓存的锁
 *
 * @param key
 * @return
 */
private Boolean tryLock(String key) {
    //尝试获取锁
    Boolean flag = stringRedisTemplate.opsForValue().setIfAbsent(key, "1", RedisConstants.LOCK_SHOP_TTL, TimeUnit.SECONDS);
    //返回获取结果
    return flag;
}

/**
 * 释放锁
 *
 * @param key
 */
private void unLock(String key) {
    stringRedisTemplate.delete(key);
}
```





### 封装Redis工具类

在解决缓存问题（缓存击穿、缓存穿透等）的时候，通常涉及到很多复杂的业务，因此我们可以将这些业务封装到一个工具类中。

这里封装下面四个方法

![image-20250408193743072](./pictures/image-20250408193743072.png)

这里封装工具类还是比较难的，这是第一次尝试自己用泛型来封装工具类，要学会使用泛型。还涉及到一个Function<K,T>，这个代表参数类型为K，返回结果为T的函数。

工具类封装如下

```java
/**
 * 缓存工具类
 */
@Component
public class CacheClient {

    @Autowired
    StringRedisTemplate stringRedisTemplate;

    //使用线程池来进行缓存重构,简单创建线程数为10的线程池
    private static final ExecutorService CACHE_REBUILD_EXECUTOR = Executors.newFixedThreadPool(10);


    /**
     * 将任意Java对象序列化为json并存入缓存
     *
     * @param key
     * @param object
     * @param time
     * @param unit
     */
    public void set(String key, Object object, Long time, TimeUnit unit) {
        stringRedisTemplate.opsForValue().set(key, JSONUtil.toJsonStr(object), time, unit);
    }


    /**
     * 将任意Java对象序列化并存入缓存，需要解决缓存基础
     *
     * @param key
     * @param object
     * @param time
     * @param unit
     */
    public void setWithLogicExpire(String key, Object object, Long time, TimeUnit unit) {
        //封装逻辑过期并序列化对象
        RedisData redisData = new RedisData();
        redisData.setData(object);
        redisData.setExpire(LocalDateTime.now().plusSeconds(unit.toSeconds(time)));
        String jsonData = JSONUtil.toJsonStr(redisData);
        //存入缓存
        stringRedisTemplate.opsForValue().set(key, jsonData);
    }

    /**
     * 查询缓存，解决了缓存穿透
     * @param keyPrefix
     * @param id
     * @param type
     * @param dbFallback
     * @param time
     * @param unit
     * @return
     * @param <T>
     * @param <ID>
     */
    public <T, ID> T queryWithPassThrough(
            String keyPrefix, ID id, Class<T> type, Function<ID,T> dbFallback,
            Long time,TimeUnit unit) {
        String key = keyPrefix + id;
        //1.查询缓存
        String jsonData = stringRedisTemplate.opsForValue().get(key);
        //2.缓存中存在，直接返回
        if (StrUtil.isNotBlank(jsonData)) {
            //将查询结果序列化为指定的对象
            return JSONUtil.toBean(jsonData,type);
        }

        //解决缓存穿透，如果缓存为空值，说明信息不存在
        if (jsonData != null) {
            return null;
        }

        //3.不存在商户信息，查询数据库
        //查询数据库对应的逻辑需要调用者提供
        T data = dbFallback.apply(id);
        //4.数据库不存在商户信息，返回null
        if (data == null) {
            //并向缓存存入空值，直接调用上面写的方法来存入缓存
            set(key,"",time,unit);
            return null;
        }
        //5.查询结果存在，将信息存入缓存
        set(key,data,time,unit);
        //6.返回查询结果
        return data;


    }

    /**
     * 查询缓存，解决了缓存击穿
     * @param keyPrefix
     * @param id
     * @param type
     * @param dbFallback
     * @param time
     * @param unit
     * @return
     * @param <T>
     * @param <ID>
     */
    public <T,ID> T queryWithLogicExpire(
            String keyPrefix,ID id,Class<T> type,Function<ID,T> dbFallback,
            Long time,TimeUnit unit){
        String key = keyPrefix + id;
        String lockKey = RedisConstants.LOCK_SHOP_KEY+id;
        //查询缓存
        String json = stringRedisTemplate.opsForValue().get(key);
        //如果缓存不存在直接返回
        if(StrUtil.isBlank(json)){
            return null;
        }
        //将查询结果反序列化
        RedisData redisData = JSONUtil.toBean(json, RedisData.class);
        T t = JSONUtil.toBean((JSONObject) redisData.getData(), type);
        LocalDateTime expire = redisData.getExpire();
        //接下来解决缓存击穿问题，采用逻辑过期的方式
        //检查缓存是否过期
        if (expire.isAfter(LocalDateTime.now())) {
            //未过期，直接返回缓存信息
            return t;

        }
        //已过期，需要进行缓存重建
        //先尝试获取锁
        Boolean flag = tryLock(lockKey);
        if (flag) {
            //锁获取成功，开启新线程进行缓存重建，然后直接返回旧数据
            //锁获取成功后再次尝试获取缓存，做二次校验
            redisData = JSONUtil.toBean(stringRedisTemplate.opsForValue().get(key), RedisData.class);
            //如果二次校验结果仍然是过期时间就新建线程进行缓存重构
            if(redisData.getExpire().isBefore(LocalDateTime.now())){
                // 新建线程重构缓存
                CACHE_REBUILD_EXECUTOR.submit(()->{
                    try{
                        //查询数据库
                        T t1 = dbFallback.apply(id);
                        // TODO 过期时间暂时设定为30s，为了方便测试
                        setWithLogicExpire(key,t1,30L,TimeUnit.SECONDS);
                    }finally {
                        //最后别忘了释放锁
                        unLock(lockKey);
                    }
                });
            }else{
                unLock(lockKey);
            }
        }
        //锁获取失败或者成功创建新线程后，直接返回数据
        t = JSONUtil.toBean((JSONObject) redisData.getData(), type);
        return t;
    }

    /**
     * 获取操作缓存的锁
     *
     * @param key
     * @return
     */
    private Boolean tryLock(String key) {
        //尝试获取锁
        Boolean flag = stringRedisTemplate.opsForValue().setIfAbsent(key, "1", RedisConstants.LOCK_SHOP_TTL, TimeUnit.SECONDS);
        //返回获取结果
        return flag;
    }

    /**
     * 释放锁
     *
     * @param key
     */
    private void unLock(String key) {
        stringRedisTemplate.delete(key);
    }


}
```

有了这个工具类，我们就可以来修改原来的业务逻辑代码，只需要调用工具类里面的方法即可。

```java
@Autowired
CacheClient cacheClient;

/**
 * 根据id查询商户
 *
 * @param id
 * @return
 */
@Override
public Result queryById(Long id) {
    //直接使用封装的缓存工具类来查询缓存（缓存穿透）
    //Shop shop = cacheClient.queryWithPassThrough(RedisConstants.CACHE_SHOP_KEY, id, Shop.class, this::getById, RedisConstants.CACHE_SHOP_TTL, TimeUnit.MINUTES);

    //查询缓存（缓存击穿）
    Shop shop = cacheClient.queryWithLogicExpire(RedisConstants.CACHE_SHOP_KEY, id, Shop.class, this::getById, RedisConstants.CACHE_SHOP_TTL, TimeUnit.SECONDS);

    if(shop==null){
        //如果查询结果为空，说明不存在
        return Result.fail("查询店铺不存在");
    }
    //存在则返回
    return Result.ok(shop);
}
```







### 全局唯一ID

#### 1.主键自增ID的缺点

以前我们数据库表的主键ID用的都是自增ID，从1开始。这种ID会带来一些问题：

1）id规律太明显。

id规律太明显，容易泄露出一些信息，也会带来缓存穿透的风险，因为用户可以很容易猜出id的规律，以此来发送无用的请求。

2）无法保证全局唯一性

在实际业务中，不会将所有数据存储到一个表中，而是使用分布式存储系统，将数据拆分成多个表来存储，此时如果仍然采用主键自增ID，就会导致ID的不唯一，因为每个表中的主键自增ID是单独计算的，因此会出现多个ID一样的记录。



#### 2.全局ID生成器

使用全局ID生成器生成的ID就能够保证在分布式系统中ID也唯一，并且该ID也比较复杂，没那么容易猜出规律。

全局ID生成器的特性：

1）唯一性

生成的ID必须全局唯一

2）高可用

全局ID生成器必须保证高可用，因为如果全局ID生成器宕机，会导致其他业务无法进行

3）高性能

全局ID生成器需要保证能够快速生成ID，如果ID生成慢会拖慢所有业务。

4）递增性

递增性指的后生成的ID值是大于前面生成的ID，这样有利于在数据库中建立索引，提高查询效率

5）安全性

生成的ID不能太简单，避免用户直接猜出ID规律。



基于以上特性，Redis就特别适合来实现全局ID生成器

全局ID结构大概如下：

![image-20250408232208102](./pictures/image-20250408232208102.png)

1）符号位。永远为0

2）时间戳。基于某个时间点开始，所经过的时间，以秒为单位

3）序列号。秒内计数器，每秒可生成2的32次方个不同的ID。





#### 3.使用Redis实现全局ID生成器

实现时要注意两个点

1.Redis自增key如何设置

2.时间戳和序列号如何拼接

这两个点在代码注释有讲，注意看。

```java
/**
 * 全局ID生成器
 */
@Component
public class RedisIdWorker {

    //指定时间戳开始的时间，这里指定为2022年1月1日 00:00:00
    private static final long BEGIN_TIMESTAMP = 1640995200;
    @Autowired
    StringRedisTemplate stringRedisTemplate;


    /**
     * 生成全局id
     * @param prefix 代表业务的前缀
     * @return
     */
    public long nextId(String prefix){
        //生成时间戳
        LocalDateTime now = LocalDateTime.now();
        long nowTimestamp = now.toEpochSecond(ZoneOffset.UTC);
        long timestamp = nowTimestamp-BEGIN_TIMESTAMP;

        //生成序列号
        //序列号的生成使用Redis的自增
        /*获取当天的日期，精确到天，将日期添加到key中，这样可以防止key的值一直增长，防止Redis的值溢出
            因为Redis的值最长为64位，如果不带上日期，那么同一个业务的key就一直不变，其对应的值就会一直增长
            不让值一直增长的不仅仅是因为Redis的值会溢出，更是因为序列号只有32位，所以不允许生成的值超过32位
            而加上当天日期，即使是同一个业务，每天的自增长都是单独计算的，这样不仅可以防止值溢出，还可以很方便地统计每天，每月，每年的业务数量
         */
        String date = now.format(DateTimeFormatter.ofPattern("yyyy:MM:dd"));
        //这里类型不用Long包装类，是因为Redis的自增即使不存在key，也会创建该key，然后自增，因此不会出现null值
        //而且后面要进行计算，使用long避免了自动拆箱
        long count = stringRedisTemplate.opsForValue().increment("icr:" + prefix + ":" + date);
        //拼接并返回
        /*拼接时间戳和序列号的实现需要好好学，是以前没有用过的方法。
        * 这里拼接不使用转字符串啥的，转来转去太麻烦了。
        * 这里直接采用位运算（重点来了），可将时间戳的向左移动32位，32位指的是序列号的位数，如果序列号的位数为其他，就左移对应的位数
        * 左移完成后，再采用或运算（|）,或运算就是全为0，则为0，否则为1。
        * 通过使用或运算，就能对末尾的32位进行运算
        * 由于左移位后的时间戳的末尾32位全为0，因此此时时间戳与序列号进行或运算的后32位的结果就是序列号的值，序列号是啥，后32位就是啥
        * 这样就成功将时间戳与序列号拼接
        * */
        return timestamp<<32|count;
    }


}
```



测试代码

```java
private ExecutorService es = Executors.newFixedThreadPool(500);

@Test
public void testIdWorker() throws InterruptedException {
    CountDownLatch latch = new CountDownLatch(300);
    Runnable task = ()-> {
        long id=0L;
        for (int i = 0 ;i<100;i++){
            id = redisIdWorker.nextId("order");
        }
        System.out.println("id："+id);
        latch.countDown();
    };

    long begin = System.currentTimeMillis();
    for(int i = 0;i<300;i++){
        es.submit(task);
    }
    latch.await();
    long end = System.currentTimeMillis();
    System.out.println("time:"+(end-begin)/1000);
}
```

运行结果

![image-20250409084752869](./pictures/image-20250409084752869.png)

此时我们查看Redis，就可以看到这一天生成的ID数，也就相当于是当天的业务数量，可以方便统计数据。

这里我执行了两次上面的测试代码，因此生成了60000个ID

![image-20250409084841297](./pictures/image-20250409084841297.png)





### 秒杀下单功能

#### 秒杀下单功能（简单实现）

实现秒杀下单功能，但是有很多问题还没解决，只是基础实现。

![image-20250409094119845](./pictures/image-20250409094119845.png)

Controller层

```java
    @PostMapping("seckill/{id}")
    public Result seckillVoucher(@PathVariable("id") Long voucherId) {
        return voucherOrderService.seckillVoucher(voucherId);
    }
```

Service层

```java
   @Autowired
    private ISeckillVoucherService seckillVoucherService;
    @Autowired
    private RedisIdWorker redisIdWorker;

    /**
     * 秒杀优惠券
     *
     * @return
     */
    @Override
    //涉及到两个表，使用事务
    @Transactional
    public Result seckillVoucher(Long voucherId) {
        //1.查询优惠券
        SeckillVoucher voucher = seckillVoucherService.getById(voucherId);

        //2.判断秒杀时间
        if (voucher.getBeginTime().isAfter(LocalDateTime.now())) {
            //秒杀还未开始
            return Result.fail("秒杀还未开始");
        }
        if (voucher.getEndTime().isBefore(LocalDateTime.now())) {
            //秒杀结束
            return Result.fail("秒杀已结束");
        }

        //3.判断库存
        if (voucher.getStock() < 1) {
            return Result.fail("库存不足");
        }

        //4.减少库存
        boolean success = seckillVoucherService.update()
                .setSql("stock=stock-1")
                .eq("voucher_id", voucherId).update();
        if(!success){
            return Result.fail("库存不足");
        }
        //5.生成订单
        //生成订单id
        long orderId = redisIdWorker.nextId("order");
        VoucherOrder voucherOrder = new VoucherOrder();
        //订单id
        voucherOrder.setId(orderId);
        //优惠券id
        voucherOrder.setVoucherId(voucherId);
        //用户id
        voucherOrder.setUserId(UserHolder.getUser().getId());
        save(voucherOrder);

        return Result.ok(orderId);
    }
```





#### 库存超卖问题分析

以上代码实现在有大量并发请求时会出现线程安全问题

现在我有一个秒杀优惠券，库存为100

![image-20250409191200360](./pictures/image-20250409191200360.png)

如果有大量请求来尝试购买这个优惠券，正常来说是只会创建100个订单，但是结果却如下，这里测试发出了200次请求，可以发现库存剩余-9，这明显是错误的。

![image-20250409191416301](./pictures/image-20250409191416301.png)

正常来讲只会建立100个订单，但是现在却建立了109个订单（右下角有显示记录数）

![image-20250409191535128](./pictures/image-20250409191535128.png)

产生这个问题的原因如下图所示

![image-20250409191653524](./pictures/image-20250409191653524.png)



假如此时库存剩余量为1，此时线程1进来查询发现还有剩余量，于是准备创建订单，但是在创建订单之前，线程2进来查询了库存，发现也为1，因此线程2也准备创建订单，这就出现问题了，因为库存容量为1，现在却有两个线程能够创建订单了。并且实际中还会有更多的线程，因此才会出现上面的多出9个订单的结果。



#### 解决库存超卖问题

要解决库存超卖问题有两种方法：

##### 1.悲观锁

认为线程安全问题一定会发生，因此每一个线程在操作数据之前要先获取锁，这种方式确保了线程的串行执行。



##### 2.乐观锁

悲观锁很显然会有性能上的问题。因此我们一般采用乐观锁的方式来解决这个问题

乐观锁是假设线程安全问题不一定发生，因此不对数据进行加锁，只是在要修改数据时去判断一下数据是否已经被其他线程修改过。

如果被其他线程修改过，就重试或直接返回异常。

如果没有被其他线程修改过，就可以直接修改数据。





#### 乐观锁解决库存超卖问题

基于乐观锁解决库存超卖问题有两种方案:

##### 1.版本号法

在原来数据的基础上再添加一个版本号数据，数据每次被修改，版本号就加1。当一个线程查询数据时，也会查询出版本号，接着在进行修改前会对比版本号，如果版本号与原来查询的不一致，说明数据被其他线程修改过了，可以重试或直接返回异常。如果版本号一致说明数据没被修改过，可以直接修改数据。

![image-20250409193447702](./pictures/image-20250409193447702.png)

上图中线程1完成修改后版本号就会变为2，因此线程2无法完成修改。



##### 2.CAS

CAS是Compare And Set 的缩写，意为比较并交换。它其实和版本号法大差不差，只不过版本号需要单独用一个版本信息来判断数据是否被修改过。而CAS直接利用数据本身作为版本号，一个线程要进行修改操作时先查询数据，然后在修改之前再次查询数据，然后对比两次查询的结果是否发生变化，如果没发生变化，说明数据没有被其他线程修改，可以直接执行修改操作。如果两次查询结果不一致，说明数据被其他线程修改过，所以要么重试要么返回异常。

![image-20250409193904681](./pictures/image-20250409193904681.png)

上图中，线程1执行完后stock就会变为0，因此线程2第二次查询结果就为0，与第一次的查询结果不一致，因此线程2执行失败。





##### 代码实现

只需在修改数据前判断库存量是否大于0

![image-20250409194709261](./pictures/image-20250409194709261.png)

接着还是在1秒内发送200个请求，结果如下，并没有出现库存超卖问题

![image-20250409194755045](./pictures/image-20250409194755045.png)

查看200个请求的报告也可以发现成功率为50%，也就说只有100条请求购买成功。

![image-20250409194906672](./pictures/image-20250409194906672.png)





#### 实现一人一单功能

一人一单功能，即：同一个用户对同一张优惠券只能买一张。这个功能实现起来优点复杂，慢慢来。

首先来讲基本思路，要保证一个用户只能购买一张同类型的优惠券，只需要在建立订单之前去数据库查询一下当前用户是否存在购买当前优惠券的订单，即根据user_id和voucher_id来查询订单。

![image-20250409201908516](./pictures/image-20250409201908516.png)

假如当前用户id为1010，购买的优惠券的id为10，那就去查user_id=1010，voucher_id=10的订单信息。

如果找到就不创建订单，反之则创建订单。

基于上面的思路我们来改进原本的代码，在减少库存创建订单之前查询用户是否已经购买过该优惠券

![image-20250409202641135](./pictures/image-20250409202641135.png)



接下来我们进行测试，发送200个请求，所有请求的用户都是同一个用户，测试结果如下

![image-20250409202909110](./pictures/image-20250409202909110.png)

可以发现，以上代码没有成功实现一人一单功能，因为同一个用户的200个请求按理来说也只会生成1个订单，但这里生成了10个。

那是什么原因造成的呢？

原因其实也很好分析，假设有一个线程1和一个线程2，线程1先进行查询，发现数据库不存在该用户的订单，说明该用户可以购买优惠券，于是线程1准备修改库存并创建订单记录，但是在线程1创建号订单记录之前，线程2进来了，线程2也去查询数据库，发现此时也不存在用户的订单，于是线程2也准备修改库存并创建订单记录，这就出现问题了，因为此时一个用户就已经购买了2张优惠券了。



那要如何解决这个问题呢？

要解决这个问题就必须采用悲观锁了，因为这里无法像乐观锁那样，存在某个数据让我们判断是否存在线程安全。

采用悲观锁，也就是要对数据库的操作进行加锁。

这里我们需要对从查询数据库判断用户是否已经购买过到创建新的订单记录的所有操作加锁。

我们可以将这一段逻辑封装到一个方法中，并对这一个方法加锁

```java
//涉及到两个表，使用事务
@Transactional
public synchronized Result createVoucherOrder(Long voucherId) {
    /**
     * 查询订单，判断用户是否已经购买过当前优惠券。
     */
    Long userId = UserHolder.getUser().getId();
    Integer count = query().eq("user_id", userId).eq("voucher_id", voucherId).count();
    if(count>0){
        //如果查询结果大于0，说明用户已经购买过了。
        return Result.fail("每人限购一张");
    }
    //如果查询结果为0，就继续后面的业务。

    //4.减少库存
    boolean success = seckillVoucherService.update()
            .setSql("stock=stock-1")
            .eq("voucher_id", voucherId)
            .gt("stock",0)      //用乐观锁解决线程安全问题，只需要在修改前判断库存量是否大于0，如果大于0则允许修改，否则不允许修改
            .update();
    if(!success){
        return Result.fail("库存不足");
    }
    //5.生成订单
    //生成订单id
    long orderId = redisIdWorker.nextId("order");
    VoucherOrder voucherOrder = new VoucherOrder();
    //订单id
    voucherOrder.setId(orderId);
    //优惠券id
    voucherOrder.setVoucherId(voucherId);
    //用户id
    voucherOrder.setUserId(UserHolder.getUser().getId());
    save(voucherOrder);

    return Result.ok(orderId);
}
```

然后在原本方法中调用这个方法

![image-20250409204452939](./pictures/image-20250409204452939.png)

再次发起200个请求来测试，可以发现确实实现了一人一单功能

![image-20250409204923799](./pictures/image-20250409204923799.png)



但是这种方法，默认是对this加锁，也就是说不管哪个用户，进来争夺的都是同一把锁，显然锁的范围太大了，性能可能非常差，所以还要进行优化。

要缩小锁的范围，可以将锁范围锁到同一个用户上，也就说如果多个线程是同一个用户，那这些线程抢这一把锁，如果是另一个用户，那就去抢另一把锁，不同用户之间互不干扰，这样性能就会好很多。



那如何将锁范围锁到同一个用户上呢？

可以使用用户的ID，将用户的ID转换为字符串，锁对象就为这个字符串对象，而不同用户的ID不同，因此生成的字符串对象肯定不同，因此每个用户也就会有自己的锁。

这里需要注意的是，toString方法会创建新的对象，因此即使是同一用户ID，使用toString也会创建多个地址不同的对象，这就会导致同一个用户的每次的请求争夺的锁并不是同一把了。为了解决这个问题，可以使用intern方法

String.intern()是一个Native方法,它的作用是:如果字符常量池中已经包含一个等于此String对象的字符串,则返回常量池中字符串的引用,否则,将新的字符串放入常量池,并返回新字符串的引用

因此使用intern方法能够保证同一ID生成的字符串对象是同一个，同一个用户的请求争夺的锁才会是同一把

```java
//涉及到两个表，使用事务
@Transactional
public Result createVoucherOrder(Long voucherId) {
    /**
     * 查询订单，判断用户是否已经购买过当前优惠券。
     */
    Long userId = UserHolder.getUser().getId();
    
    //使用用户ID转换为字符串对象来作为锁
    synchronized (userId.toString().intern()) {
        Integer count = query().eq("user_id", userId).eq("voucher_id", voucherId).count();
        if (count > 0) {
            //如果查询结果大于0，说明用户已经购买过了。
            return Result.fail("每人限购一张");
        }
        //如果查询结果为0，就继续后面的业务。

        //4.减少库存
        boolean success = seckillVoucherService.update()
                .setSql("stock=stock-1")
                .eq("voucher_id", voucherId)
                .gt("stock", 0)      //用乐观锁解决线程安全问题，只需要在修改前判断库存量是否大于0，如果大于0则允许修改，否则不允许修改
                .update();
        if (!success) {
            return Result.fail("库存不足");
        }
        //5.生成订单
        //生成订单id
        long orderId = redisIdWorker.nextId("order");
        VoucherOrder voucherOrder = new VoucherOrder();
        //订单id
        voucherOrder.setId(orderId);
        //优惠券id
        voucherOrder.setVoucherId(voucherId);
        //用户id
        voucherOrder.setUserId(UserHolder.getUser().getId());
        save(voucherOrder);

        return Result.ok(orderId);
    }
}
```



但是这样又会有一个问题，由于该方法使用了事务，如果我们在方法内部加锁，那么方法内部的被加锁的代码块执行完毕后就会自动释放锁，但是Spring事务的提交是在方法执行完毕后才会提交事务，这就会导致一个问题，如果在锁释放后，事务还没有提交的时候又进来了一个线程又获取了锁，查询订单发现该用户没有购买过该优惠券（实际上已经购买过了，但是由于事务还没提交，数据库内还不存在相应的记录），就又会产生一个新的订单，也就导致同一个用户购买了多张优惠券。



要解决这个问题，我们不能在方法内部加锁，而是要在调用方法外边进行加锁，只有获取到锁才能执行该方法，这样事务就会先提交，然后才会释放锁。如下图所示

![image-20250409211804399](./pictures/image-20250409211804399.png)



但是这里又有一个问题，因为createVoucherOrder方法被@Transactional修饰了，而seckillVoucher方法没有开启事务。我们知道事务是由代理对象来实现了，但这里调用方法时其实是通过`this.createVoucherOrder`来调用的，因此实际执行createVoucherOrder方法的是VoucherOrderServiceImpl这个类本身的对象，并没有开启代理对象，这就会导致方法的事务失效。

要解决这个问题我们可以手动生成一个VoucherOrderServiceImpl类的代理对象，用这个代理对象去调用方法，这样就能保证事务有效。

手动创建代理对象需要先导入依赖

```xml
<dependency>
    <groupId>org.aspectj</groupId>
    <artifactId>aspectjweaver</artifactId>
</dependency>
```

还需要在启动类上添加`@EnableAspectJAutoProxy`以暴露代理对象，加上了该注解我们手动创建的代理对象才会生效

![image-20250409213447042](./pictures/image-20250409213447042.png)

接下来就是在调用方法前创建代理对象，然后用代理对象去调用方法

![image-20250409213635206](./pictures/image-20250409213635206.png)

最终的完整代码如下

```java
@Service
public class VoucherOrderServiceImpl extends ServiceImpl<VoucherOrderMapper, VoucherOrder> implements IVoucherOrderService {
    @Autowired
    private ISeckillVoucherService seckillVoucherService;
    @Autowired
    private RedisIdWorker redisIdWorker;

    /**
     * 秒杀优惠券
     *
     * @return
     */
    @Override
    public Result seckillVoucher(Long voucherId) {
        //1.查询优惠券
        SeckillVoucher voucher = seckillVoucherService.getById(voucherId);

        //2.判断秒杀时间
        if (voucher.getBeginTime().isAfter(LocalDateTime.now())) {
            //秒杀还未开始
            return Result.fail("秒杀还未开始");
        }
        if (voucher.getEndTime().isBefore(LocalDateTime.now())) {
            //秒杀结束
            return Result.fail("秒杀已结束");
        }

        //3.判断库存
        if (voucher.getStock() < 1) {
            return Result.fail("库存不足");
        }

        //调用创建订单的方法
        //在调用方法外部加锁
        Long userId = UserHolder.getUser().getId();
        synchronized (userId.toString().intern()) {
            //创建代理对象
            IVoucherOrderService proxy = (IVoucherOrderService) AopContext.currentProxy();
            //用代理对象去创建方法
            return proxy.createVoucherOrder(voucherId);
        }
    }

    //涉及到两个表，使用事务
    @Transactional
    public Result createVoucherOrder(Long voucherId) {
        /**
         * 查询订单，判断用户是否已经购买过当前优惠券。
         */
        Long userId = UserHolder.getUser().getId();
        Integer count = query().eq("user_id", userId).eq("voucher_id", voucherId).count();
        if (count > 0) {
            //如果查询结果大于0，说明用户已经购买过了。
            return Result.fail("每人限购一张");
        }
        //如果查询结果为0，就继续后面的业务。

        //4.减少库存
        boolean success = seckillVoucherService.update()
                .setSql("stock=stock-1")
                .eq("voucher_id", voucherId)
                .gt("stock", 0)      //用乐观锁解决线程安全问题，只需要在修改前判断库存量是否大于0，如果大于0则允许修改，否则不允许修改
                .update();
        if (!success) {
            return Result.fail("库存不足");
        }
        //5.生成订单
        //生成订单id
        long orderId = redisIdWorker.nextId("order");
        VoucherOrder voucherOrder = new VoucherOrder();
        //订单id
        voucherOrder.setId(orderId);
        //优惠券id
        voucherOrder.setVoucherId(voucherId);
        //用户id
        voucherOrder.setUserId(UserHolder.getUser().getId());
        save(voucherOrder);

        return Result.ok(orderId);

    }
}
```



这下才总算完成了一人一单功能。



#### 集群下的线程并发安全问题

上面完成一人一单功能只能在单机服务下保证线程安全，如果业务是部署在集群上的，上面的代码还是会出现线程安全问题。

下面我们先来模拟将业务部署在集群上

进入idea，在下面选择services，选中原本的服务，按ctrl+d，可以再创建一个一模一样的服务。

![image-20250409232927202](./pictures/image-20250409232927202.png)

但是我们要先配置第二个服务的端口号，不然会产生端口冲突。

添加`VM option`配置，输入-Dserver.port=8082配置端口号

![image-20250409233112576](./pictures/image-20250409233112576.png)



然后就可以同时启动两个项目来模拟集群环境了。

此外还需要修改一下nginx的配置，添加最下面两行配置，让nginx轮询访问集群中的两个服务

![image-20250409235215141](./pictures/image-20250409235215141.png)

然后重启nginx服务器

![image-20250409233702431](./pictures/image-20250409233702431.png)



接下来使用postman发送两个购买优惠券的请求，请求都是同一个用户，请求结果发现该用户买了两张优惠券，说明出现了线程安全问题

![image-20250410000723697](./pictures/image-20250410000723697.png)

产生这个问题的原因是，在集群中，每一个服务都有一个单独的jvm，而每一个jvm的锁监视器都是独立的，因此即使是同一个用户，在两台不同的jvm上运行，也无法共享同一个锁

![image-20250410000946735](./pictures/image-20250410000946735.png)

