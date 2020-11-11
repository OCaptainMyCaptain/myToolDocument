### <center>摘要</center>
    本文主要记录JavaBean以及各种POJO类的异同以及各自的应用场景。
## 1. POJO类
    POJO是Plain Ordinary Java Object的缩写，通常指普通的Java类。
## 2. JavaBean
    JavaBean是特殊的Java类，使用Java语言书写，并遵守JavaBean API规范。较之普通Java类，它有如下特征：
* 提供一个默认的无参构造函数
* 需要被序列化且实现了Serializable接口
* 可能有一系列可读写属性
* 可能有一系列的getter和setter方法
## 3. Entity
    Entity是指实体类，是一种只有私有属性和对应getter和setter方法的简化的JavaBean类。
## 4. VO、POJO、PO、DTO、DO
* VO：Value Object——表现层对象。通常是Web层向模板渲染引擎层传输的对象，直白的说就是前段与后端交互的对象。
* POJO：Plain Ordinary Java Object——普通Java对象。只包含私有修饰的属性和与之对应的getter、setter方法，。没有继承、没有接口、没有注解、没有被其他Java框架入侵，有时候会直接作为与数据库表一一对应的映射类。
* PO：Persistent Object——持久化对象。一般与数据库中表结构形成一一对应的映射关系。
* DTO：Data Transfer Object——数据传输对象。用于远程调用等需要大量传输对象的地方，也可以泛指用于展示层与服务层之间的数据传输对象。
* DO：Domain Object——领域对象。从现实世界中抽象出来的有形或无形的业务实体。
## 5. BO、DAO
* BO：Business Object——业务对象。主要是吧业务逻辑封装为一个对象，这个对象可以包括一个或多个其他的对象。比如一份简历，有鉴于经历、工作经历、社会关系等。可以把教育经历对应一个PO，工作经历对应一个PO，社会关系对应一个PO，然后建立一个对应的BO来处理简历，每个BO包含这些PO，这样就可以针对BO去处理业务逻辑。
* DAO：Data Access Object——数据访问对象。此对象用于访问数据库，通常与PO结合使用，DAO中包含了各种数据库的操作方法，结合PO对数据库进行相关操作，处于业务逻辑与数据库资源中间，通过它可以把POJO持久化为PO，用PO组装VO、DTO。