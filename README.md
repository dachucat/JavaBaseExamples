# 小课堂JAVA说明
## 02-01 git 基础应用
### git 仓库基本原理
### modify by milk
#### modify by Derrick
### modify by flh
### 远程仓库， 本地仓库（多个仓库），代码拉去，修改，添加，提交，推送，冲突解决 
# 优秀的资源：
    1 运维视频课程： https://www.cnblogs.com/JayYang/p/16436646.html
    2 计算机基础原理： https://github.com/xiaolincoder/CS-Base
    3 计算机基础算法： https://github.com/chefyuan/algorithm-base
    4 Java Web应用开发技术与案例教程例题与习题代码: https://github.com/Hackergeek/JavaWebBase
    5: 各种学习资源: https://www.kancloud.cn/apachecn/howtodoinjava-zh/1953371
    6: 运维工具： https://github.com/guohongze/adminset
    7: spring cloud 代码: https://github.com/search?q=spring+cloud+kit
    8: spring clod alibaba: https://blog.csdn.net/zhangzhanpu/article/details/120314551
# 账号：
    milk: 2917462604@qq.com
    deriick: 812062797@qq.com
# jira nginx:
    | ec2 1 跳板机 openjump/vpn (管理), nginx 反向代理(web, 漏洞、加速、负载均衡 )
    | ec2 2 172.31.4.0/24
    | ec2 3 172.31.4.0/24
    |
    Remote -> |  jira:8888
    Pycharm: python 工具，日常文档管理
    Certbot: htpps 免费证书
    ansible: 自动化安装
# project lists:
  https://github.com/dachucat/java-common-spring-boot-starter
  https://github.com/dachucat/java-common-db-spring-boot-starter
  https://github.com/dachucat/java-common-core
  https://github.com/dachucat/java-commons
  https://github.com/dachucat/java-wallet
  https://github.com/dachucat/java-members
  https://github.com/dachucat/java-business
  https://github.com/dachucat/java-framework  

# java dao
  mysql -> spring(model mapper(dao) = interface(数据库操作接口)  )
  mybatisplus:
  SysRoleMenuMapper -> class SysRoleMenuMapperImpl imp SysRoleMenuMapper {}
  model | mapper(dao) | service | controller
  model: 表记录
  mapper: 表操作, 增删改查
  service: 实现业务, interface -> impl,  inerface 声明接口， impl 真正的实现, mapper(dao)实现
  controller: 业务的接口  用input 参数 调用 service 获取输出参数 输出， 缝合, 实现api接口，使用postman测试
  mvc： 模型, 后台开发主要模型
  postman: api 调用\测试工具
  
  Spring: 当类声明是：@Service @Component @RestController： 当用 @Resource @Autowired 引用一个interface 的时候，
  预先实现业务，然后完善
# 安装:
  mysql, postman
# 数据库概念:
  增，删，改，查
  create table:
  drop table;
  insert:
  delete:
  update:
  select:
  index:
  join:
  foreign key:
    1 - 1:  
    1 - *:   user -> book
    * - *    author * author_book * book
  逻辑 -》 join -》 index

  SELECT b.name as book_name, u.name as user_name  from book b join `user` u on b.user_id  = u.id WHERE  b.id = 1;

  SELECT * from book_author ba join book b on b.id  = ba.book_id JOIN author a on a.id  = ba.author_id where ba.book_id  = 3;

  CREATE TABLE `user` (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键',
  `name` varchar(100) NOT NULL,
  PRIMARY KEY (`id`)
  ) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

  CREATE TABLE `author` (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键',
  `name` varchar(100) NOT NULL,
  PRIMARY KEY (`id`)
  ) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

  CREATE TABLE `book` (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键',
  `name` varchar(100) NOT NULL,
  `user_id` bigint NOT NULL,
  PRIMARY KEY (`id`),
  KEY `book_user_id_IDX` (`user_id`) USING BTREE,
  CONSTRAINT `book_FK` FOREIGN KEY (`user_id`) REFERENCES `user` (`id`)
  ) ENGINE=InnoDB AUTO_INCREMENT=5 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

  CREATE TABLE `book_author` (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键',
  `book_id` bigint NOT NULL,
  `author_id` bigint NOT NULL,
  PRIMARY KEY (`id`)
  ) ENGINE=InnoDB AUTO_INCREMENT=5 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;


  CREATE TABLE `user_auth` (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键',
  `type` varchar(32) NOT NULL,
  `user_id` bigint NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `user_auth_user_id_IDX` (`user_id`) USING BTREE
  ) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

# 常用工具:
  jira:   大型，项目管理工具 
  confluence:   wiki 记录工具
  禅道：   国产，中型的项目管理工具
  
  ...

# creage .ssh
  cd ~/
  rm -rf .ssh
  ssh-keygen
  cat ~/.ssh/id_rsa.pub

# members mysql 数据库配置:
  1。 建立一个数据库 user-center
  2. 创建表：
     CREATE TABLE `sys_role_menu` (
     `role_id` int(11) NOT NULL,
     `menu_id` int(11) NOT NULL,
     PRIMARY KEY (`role_id`,`menu_id`)
     ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 ROW_FORMAT=DYNAMIC;

     INSERT INTO sys_role_menu
     (role_id, menu_id)
     VALUES(1, 2);

  3. 配置application.properties e2cef.datasource.* 字段

  4。 自己建立 user, book, author, book_author 表
      先user 建立 account, password, name 字段
      建立 UserController, 在UserController 建立 login api, 并且用account, password 验证登陆
      
# git branch 分支, git tag: tag
  dev, test, release_a release_b, main(release_a + release_b)
  dev, milk, dericck, fly
  test,
  release,

  本地服务器，开发服务器，测试服务， 体验环境, 生产环境
  milk/xxx,  dev,     test,             release_a/rlease_b 
  java + mysql, reis

# job 分配，
  milk：book 管理
  fly： user 管理
  deriick：ahutor 管理

# java 概念:
  java bean: property -> method
  
  
  