# PHP 版设计模式

> 🌹 一个使用 **PHP** 语言实现的设计模式实例。

[![Build Status](https://travis-ci.org/imajinyun/php-design-patterns.svg?branch=master)](https://travis-ci.org/imajinyun/php-design-patterns)
[![Build status](https://ci.appveyor.com/api/projects/status/lbf61giw9iavhtt5/branch/master?svg=true)](https://ci.appveyor.com/project/imajinyun/php-design-pattern/branch/master)
[![codecov](https://codecov.io/gh/imajinyun/php-design-patterns/branch/master/graph/badge.svg)](https://codecov.io/gh/imajinyun/php-design-patterns)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/imajinyun/php-design-patterns/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/imajinyun/php-design-patterns/?branch=master)
[![Code Coverage](https://scrutinizer-ci.com/g/imajinyun/php-design-patterns/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/imajinyun/php-design-patterns/?branch=master)
[![Build Status](https://scrutinizer-ci.com/g/imajinyun/php-design-patterns/badges/build.png?b=master)](https://scrutinizer-ci.com/g/imajinyun/php-design-patterns/build-status/master)
[![Code Intelligence Status](https://scrutinizer-ci.com/g/imajinyun/php-design-patterns/badges/code-intelligence.svg?b=master)](https://scrutinizer-ci.com/code-intelligence)
[![StyleCI](https://styleci.io/repos/112085360/shield?branch=master)](https://styleci.io/repos/112085360)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/368998e20fe64b2da7f8ef1f42444527)](https://www.codacy.com/app/imajinyun/php-design-pattern?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=imajinyun/php-design-patterns&amp;utm_campaign=Badge_Grade)
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fimajinyun%2Fphp-design-pattern.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Fimajinyun%2Fphp-design-pattern?ref=badge_shield)
[![PHP from Packagist](https://img.shields.io/packagist/php-v/imajinyun/php-design-pattern.svg)](http://php.net/releases/)

## 安装 PHPUnit 测试扩展包

> [PHPUnit](https://phpunit.de/getting-started.html)

```bash
wget https://phar.phpunit.de/phpunit.phar
chmod +x phpunit.phar
sudo mv phpunit.phar /usr/local/bin/phpunit
phpunit --version
```

## 代码测试

```bash
git clone https://github.com/imajinyun/php-design-pattern.git
cd ./php-design-pattern
phpunit -v
```

## 结构型模式 - `Structural Pattern`

### [组合 - `Composite`](src/Structural/Composite)

#### 定义

把多个对象组成树状结构来表示局部与整体, 这样用户可以一样的对待单个对象和对象的组合

#### 场景

- 需要表示一个对象整体或部分层次, 在具有整体和部分的层次结构中, 希望通过一种方式忽略整体与部分的差异, 可以一致地对待它们
- 让客户能够忽略不同对象层次的变化, 客户端可以针对抽象构件编程, 无须关心对象层次结构的细节

#### 特性

##### 优点

- 可以清楚地定义分层次的复杂对象, 表示对象的全部或部分层次, 使得增加新构件也更容易
- 客户端调用简单, 客户端可以一致的使用组合结构或其中单个对象
- 定义了包含叶子对象和容器对象的类层次结构, 叶子对象可以被组合成更复杂的容器对象, 而这个容器对象又可以被组合, 这样不断递归下去, 可以形成复杂的树形结构
- 更容易在组合体内加入对象构件, 客户端不必因为加入了新的对象构件而更改原有代码

##### 缺点

使设计变得更加抽象, 对象的业务规则如果很复杂, 则实现组合模式具有很大挑战性, 而且不是所有的方法都与叶子对象子类都有关联

### [数据映射器 - `DataMapper`](src/Structural/DataMapper)

#### 定义

数据映射器是一个数据访问层, 用于将数据在持久性数据存储(通常是一个关系数据库)和内存中的数据表示(领域层)之间进行相互转换. 简单的说, 数据映射器就是一个负责将数据映射到对象的类数据

#### 场景

- 数据映射器可以很好地解决对象和关系数据库之间的被称做对象关系阻抗不匹配或阻抗不匹配的分歧, 由它来负责对象和关系数据库两者数据的转换, 从而有效地在领域模型中隐藏数据库操作并管理数据库转换中不可以避免的冲突
- 使用数据库映射器的主要是数据库方案和对象模型需要彼此独立演变的时候. 最常见的是和领域模式一起使用

#### 特性

##### 优点

- 在对象和数据库之间移动数据, 同时保持它们彼此独立, 并且映射器本身
- 消除了领域层和数据库操作之间的耦合
- 数据模型遵循单一职责原则
- 更适合于 `ORM`

##### 缺点

数据映射器的实现比较复杂

### [装饰器 - `Decorator`](src/Structural/Decorator)

#### 定义

动态地给一个对象增加一些额外的职责(`Responsibility`), 就增加对象功能来说, 装饰模式比生成子类实现更为灵活. 其别名也可以称为包装器(`Wrapper`), 与适配器模式的别名相同, 但它们适用于不同的场合

#### 场景

- 在不影响其他对象的情况下, 以动态/透明的方式给单个对象添加职责
- 需要动态地给一个对象增加功能, 这些功能也可以动态地被撤销
- 当不能采用继承的方式对系统进行扩充或者采用继承不利于系统扩展和维护时. 不能采用继承的情况主要有两类: 第一类是系统中存在大量独立的扩展, 为支持每一种组合将产生大量的子类, 使得子类数目呈爆炸性增长; 第二类是因为类定义不能继承(如: `final` 类)
- 装饰者可以在被装饰者的行为前面或者后面加上自己的行为, 甚至可以将被装饰者的行为整个取代掉, 从而达到特定的目的

#### 特性

##### 优点

- 装饰模式与继承关系的目的都是要扩展对象的功能, 但是装饰模式可以提供比继承更多的灵活性
- 可以通过一种动态的方式来扩展一个对象的功能, 通过配置文件可以在运行时选择不同的装饰器, 从而实现不同的行为
- 通过使用不同的具体装饰类以及这些装饰类的排列组合, 可以创造出很多不同行为的组合. 可以使用多个具体装饰类来装饰同一对象, 得到功能更为强大的对象
- 具体构件类与具体装饰类可以独立变化, 用户可以根据需要增加新的具体构件类和具体装饰类, 在使用时再对其进行组合, 原有代码无须改变, 符合开闭原则

##### 缺点

- 使用装饰模式进行系统设计时将产生很多小对象, 这些对象的区别在于它们之间相互连接的方式有所不同, 而不是它们的类或者属性值有所不同, 同时还将产生很多具体装饰类. 这些装饰类和小对象的产生将增加系统的复杂度, 加大学习与理解的难度
- 比继承更加灵活机动的特性, 也同时意味着装饰模式比继承更加易于出错, 排错也很困难, 对于多次装饰的对象, 调试时寻找错误可能需要逐级排查, 较为烦琐

### [依赖注入 - `DependencyInjection`](src/Structural/DependencyInjection)

#### 定义

一个将行为从依赖中分离的技术, 简单地说, 它允许开发者定义一个方法函数依赖于外部其他各种交互, 而不需要编码如何获得这些外部交互的实例. 这样就在各种组件之间解耦, 从而获得干净的代码, 相比依赖的硬编码, 一个组件只有在运行时才调用其所需要的其他组件, 因此在代码运行时, 通过特定的框架或容器, 将其所需要的其他依赖组件进行注入, 主动推入. 依赖注入可以看成是控制反转(`Inversion of Control`)的一个特例. 依赖注入说白一点, 就是容器将某个类依赖的其他类注入到这个类中

#### 场景

- 高层次的模块不应该依赖于低层次的模块, 他们都应该依赖于抽象
- 抽象不应该依赖于具体实现, 具体实现应该依赖于抽象

#### 特性

##### 优点

- 代码解耦, 便于单元测试及 `Mock`
- 提供一种调控系统, 实现依赖解析的自动注入

##### 缺点

- `DI` 强制构建的分离还会使调试变得麻烦
- 并不能解决复用性问题, 反而引入了模块查找和构造的额外代价
- `DI` 要求集中管理依赖的所有实现, 那么 `Client` 引入你的工具库中任何一部分都必须首先构造整个 `IOC` 容器

### [外观 - `Facade`](src/Structural/Facade)

#### 定义

为子系统中的一组接口提供一个一致的界面, 外观模式定义了一个高层接口, 这个接口使得这一子系统更加容易使用

#### 场景

- 当要为一个复杂子系统提供一个简单接口时可以使用外观模式. 该接口可以满足大多数用户的需求, 而且用户也可以越过外观类直接访问子系统
- 客户程序与多个子系统之间存在很大的依赖性. 引入外观类将子系统与客户以及其他子系统解耦, 可以提高子系统的独立性和可移植性
- 在层次化结构中, 可以使用外观模式定义系统中每一层的入口, 层与层之间不直接产生联系, 而通过外观类建立联系, 降低层之间的耦合度

#### 特性

##### 优点

- 对客户屏蔽子系统组件, 减少了客户处理的对象数目并使得子系统使用起来更加容易. 通过引入外观模式, 客户代码将变得很简单, 与之关联的对象也很少
- 实现了子系统与客户之间的松耦合关系, 这使得子系统的组件变化不会影响到调用它的客户类, 只需要调整外观类即可
- 降低了大型软件系统中的编译依赖性, 并简化了系统在不同平台之间的移植过程, 因为编译一个子系统一般不需要编译所有其他的子系统. 一个子系统的修改对其他子系统没有任何影响, 而且子系统内部变化也不会影响到外观对象
- 只是提供了一个访问子系统的统一入口, 并不影响用户直接使用子系统类

##### 缺点

- 不能很好地限制客户使用子系统类, 如果对客户访问子系统类做太多的限制则减少了可变性和灵活性
- 在不引入抽象外观类的情况下, 增加新的子系统可能需要修改外观类或客户端的源代码, 违背了开闭原则

### [连贯接口 - `FluentInterface`](src/Structural/FluentInterface)

#### 定义

又称流接口或方法链, 实现一种面向对象的, 能提高代码可读性的 `API` 的方法

#### 场景

查询构建器

#### 特性

##### 优点

可以编写具有自然语言一样可读性的代码

##### 缺点

### [享元 - `Flyweight`](src/Structural/Flyweight)

#### 定义

使用共享物件, 以便有效的支持大量小颗粒对象, 用来尽可能减少内存使用量以及分享资讯给尽可能多的相似物件

#### 场景

- 一个系统有大量相同或者相似的对象, 由于这类对象的大量使用, 造成内存的大量耗费
- 对象的大部分状态都可以外部化, 可以将这些外部状态传入对象中
- 使用享元模式需要维护一个存储享元对象的享元池, 而这需要耗费资源, 因此, 应当在多次重复使用享元对象时才值得使用享元模式

#### 特性

##### 优点

- 享元模式的优点在于它可以极大减少内存中对象的数量, 使得相同对象或相似对象在内存中只保存一份
- 享元模式的外部状态相对独立, 而且不会影响其内部状态, 从而使得享元对象可以在不同的环境中被共享

##### 缺点

- 享元模式使得系统更加复杂, 需要分离出内部状态和外部状态, 这使得程序的逻辑复杂化
- 为了使对象可以共享, 享元模式需要将享元对象的状态外部化, 而读取外部状态使得运行时间变长

### [代理 - `Proxy`](src/Structural/Proxy)

#### 定义

为其他对象提供一个代理以控制对这个对象的访问

#### 场景

- 远程(`Remote`)代理: 为一个位于不同的地址空间的对象提供一个本地的代理对象, 这个不同的地址空间可以是在同一台主机中, 也可是在另一台主机中, 远程代理又叫做大使(`Ambassador`)
- 虚拟(`Virtual`)代理: 如果需要创建一个资源消耗较大的对象, 先创建一个消耗相对较小的对象来表示, 真实对象只在需要时才会被真正创建
- `Copy-on-Write` 代理: 它是虚拟代理的一种, 把复制(克隆)操作延迟到只有在客户端真正需要时才执行. 一般来说, 对象的深克隆是一个开销较大的操作, `Copy-on-Write` 代理可以让这个操作延迟, 只有对象被用到的时候才被克隆
- 保护(`Protect or Access`)代理: 控制对一个对象的访问, 可以给不同的用户提供不同级别的使用权限
- 缓冲(`Cache`)代理: 为某一个目标操作的结果提供临时的存储空间, 以便多个客户端可以共享这些结果
- 防火墙(`Firewall`)代理: 保护目标不让恶意用户接近
- 同步化(`Synchronization`)代理: 使几个用户能够同时使用一个对象而没有冲突
- 智能引用(`Smart Reference`)代理: 当一个对象被引用时, 提供一些额外的操作, 如将此对象被调用的次数记录下来等

#### 特性

##### 优点

- 代理模式能够协调调用者和被调用者, 在一定程度上降低了系统的耦合度
- 远程代理使得客户端可以访问在远程机器上的对象, 远程机器可能具有更好的计算性能与处理速度, 可以快速响应并处理客户端请求
- 虚拟代理通过使用一个小对象来代表一个大对象, 可以减少系统资源的消耗, 对系统进行优化并提高运行速度
- 保护代理可以控制对真实对象的使用权限

##### 缺点

- 由于在客户端和真实主题之间增加了代理对象, 因此 有些类型的代理模式可能会造成请求的处理速度变慢
- 实现代理模式需要额外的工作, 有些代理模式的实现非常复杂

## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fimajinyun%2Fphp-design-pattern.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Fimajinyun%2Fphp-design-pattern?ref=badge_large)
