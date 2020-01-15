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

## 行为型模式 - `Behavioral Pattern`

### [中介者 - `Mediator`](src/Behavioral/Mediator)

### 定义

包装了一系列对象相互作用的方式, 使得这些对象不必相互明显作用, 从而使它们可以松散偶合. 当某些对象之间的作用发生改变时, 不会立即影响其他的一些对象之间的作用, 保证这些作用可以彼此独立的变化

#### 场景

- 系统中对象之间存在比较复杂的引用关系, 导致他们之间的依赖关系结构混乱而且难以复用该对象
- 想通过一个中间类来封装多个类中的行为, 而又不想生成太多的子类

#### 特性

##### 优点

- 适当地使用中介者模式可以避免同事类之间的过度耦合, 使得各同事类之间可以相对独立地使用
- 使用中介者模式可以将对象间一对多的关联转变为一对一的关联, 使对象间的关系易于理解和维护
- 使用中介者模式可以将对象的行为和协作进行抽象, 能够比较灵活的处理对象间的相互作用

##### 缺点

由于中介者对象封装了系统中对象之间的相互关系, 导致其变得非常复杂, 使得系统维护比较困难

### [备忘录 - `Memento`](src/Behavioral/Memento)

#### 定义

备忘录对象是一个用来存储另外一个对象内部状态的快照的对象. 备忘录模式的用意是在不破坏封装的条件下, 将一个对象的状态捉住, 并外部化, 存储起来, 从而可以在将来合适的时候把这个对象还原到存储起来的状态

#### 场景

- 保存一个对象在某一个时刻的全部状态或部分状态, 这样以后需要时它能够恢复到先前的状态, 实现撤销操作
- 防止外界对象破坏一个对象历史状态的封装性, 避免将对象历史状态的实现细节暴露给外界对象

#### 特性

##### 优点

- 提供了一种状态恢复的实现机制, 使得用户可以方便地回到一个特定的历史步骤, 当新的状态无效或者存在问题时, 可以使用暂时存储起来的备忘录将状态复原
- 备忘录实现了对信息的封装, 一个备忘录对象是一种原发器对象状态的表示, 不会被其他代码所改动. 备忘录保存了原发器的状态, 采用列表或堆栈等集合来存储备忘录对象可以实现多次撤销操作. 即实现了信息的封装, 使得用户不需要关心状态的保存细节

##### 缺点

资源消耗过大, 如果需要保存的原发器类的成员变量太多, 就不可避免需要占用大量的存储空间, 每保存一次对象的状态都需要消耗一定的系统资源

### [空对象 - `NullObject`](src/Behavioral/NullObject)

#### 定义

通过提供默认对象来避免空引用

#### 场景

- 一个对象需要一个协作对象, 但并无具体的协作对象
- 协作对象不需要做任何事情

#### 特性

##### 优点

- 减少了对对象是否为 `Null` 的判断
- 提供默认无任何具体行为的协作对象
- 加强系统的稳固性, 能有有效地防止空指针报错对整个系统的影响, 使系统更加稳定

##### 缺点

### [观察者 - `Observer`](src/Behavioral/Observer)

#### 定义

在对象间定义一个一对多的联系性, 由此当一个对象改变了状态, 所有其他相关的对象会被通知并且自动刷新

#### 场景

- 一个抽象模型有两个方面, 其中一个方面依赖于另一个方面. 将这些方面封装在独立的对象中使它们可以各自独立地改变和复用
- 一个对象的改变将导致其他一个或多个对象也发生改变, 而不知道具体有多少对象将发生改变, 可以降低对象之间的耦合度
- 一个对象必须通知其他对象, 而并不知道这些对象是谁
- 需要在系统中创建一个触发链, `A` 对象的行为将影响 `B` 对象, `B` 对象的行为将影响 `C` 对象, 可以使用观察者模式创建一种链式触发机制

#### 特性

##### 优点

- 观察者模式可以实现表示层和数据逻辑层的分离, 并定义了稳定的消息更新传递机制, 抽象了更新接口, 使得可以有各种各样不同的表示层作为具体观察者角色
- 观察者模式在观察目标和观察者之间建立一个抽象的耦合
- 观察者模式支持广播通信
- 观察者模式符合开闭原则的要求

##### 缺点

- 如果一个观察目标对象有很多直接和间接的观察者的话, 将所有的观察者都通知到会花费很多时间
- 如果在观察者和观察目标之间有循环依赖的话, 观察目标会触发它们之间进行循环调用, 可能导致系统崩溃
- 观察者模式没有相应的机制让观察者知道所观察的目标对象是怎么发生变化的, 而仅仅只是知道观察目标发生了变化

### [规格(或约) - `Specification`](src/Behavioral/Specification)

#### 定义

以布尔形式表示的可重绑定的业务逻辑

#### 场景

- 一个业务规则可以和另外的业务规则聚合, 业务规则可以使用布尔逻辑组成规则进而重新组合
- 在框架性开发中使用较多

#### 特性

##### 优点

- 在初始化之后, 规格可以和其它规格进行逻辑组合, 使新的规格很容易维护, 实现高度自定义的业务逻辑
- 实现高度自定义的业务逻辑

##### 缺点

- 缺乏通用性
- 实际项目较少用到

### [状态 - `State`](src/Behavioral/State)

#### 定义

让一个对象在其内部状态改变的时候, 其行为也随之改变. 状态模式需要对每一个系统可能获取的状态创立一个状态类的子类. 当系统的状态变化时, 系统便改变所选的子类

#### 场景

- 对象的行为依赖于它的状态(属性)并且可以根据它的状态改变而改变它的相关行为
- 代码中包含大量与对象状态有关的条件语句, 这些条件语句的出现, 会导致代码的可维护性和灵活性变差, 不能方便地增加和删除状态, 使客户类与类库之间的耦合增强. 在这些条件语句中包含了对象的行为, 而且这些条件对应于对象的各种状态

#### 特性

##### 优点

- 封装了转换规则
- 枚举可能的状态, 在枚举状态之前需要确定状态种类
- 将所有与某个状态有关的行为放到一个类中, 并且可以方便地增加新的状态, 只需要改变对象状态即可改变对象的行为
- 允许状态转换逻辑与状态对象合成一体, 而不是某一个巨大的条件语句块
- 可以让多个环境对象共享一个状态对象, 从而减少系统中对象的个数

##### 缺点

- 状态模式的使用必然会增加系统类和对象的个数
- 状态模式的结构与实现都较为复杂, 如果使用不当将导致程序结构和代码的混乱
- 状态模式对开闭原则的支持并不太好, 对于可以切换状态的状态模式, 增加新的状态类需要修改那些负责状态转换的源代码, 否则无法切换到新增状态; 而且修改某个状态类的行为也需修改对应类的源代码

### [策略 - `Strategy`](src/Behavioral/Strategy)

#### 定义

定义一个算法的系列, 将其各个分装, 并且使他们有交互性. 策略模式使得算法在用户使用的时候能独立的改变

#### 场景

- 如果在一个系统里面有许多类, 它们之间的区别仅在于它们的行为, 那么使用策略模式可以动态地让一个对象在许多行为中选择一种行为
- 一个系统需要动态地在几种算法中选择一种
- 如果一个对象有很多的行为, 如果不用恰当的模式, 这些行为就只好使用多重的条件选择语句来实现
- 不希望客户端知道复杂的, 与算法相关的数据结构, 在具体策略类中封装算法和相关的数据结构, 提高算法的保密性与安全性

#### 特性

##### 优点

- 策略模式提供了对开闭原则的完美支持, 用户可以在不修改原有系统的基础上选择算法或行为, 也可以灵活地增加新的算法或行为
- 策略模式提供了管理相关的算法族的办法
- 策略模式提供了可以替换继承关系的办法
- 使用策略模式可以避免使用多重条件转移语

##### 缺点

- 客户端必须知道所有的策略类, 并自行决定使用哪一个策略类
- 策略模式将造成产生很多策略类, 可以通过使用享元模式在一定程度上减少对象的数量

### [模板方法 - `TemplateMethod`](src/Behavioral/TemplateMethod)

#### 定义

模板方法模式准备一个抽象类, 将部分逻辑以具体方法及具体构造子类的形式实现, 然后声明一些抽象方法来迫使子类实现剩余的逻辑. 不同的子类可以以不同的方式实现这些抽象方法, 从而对剩余的逻辑有不同的实现. 先构建一个顶级逻辑框架, 而将逻辑的细节留给具体的子类去实现

#### 场景

- 一次性实现一个算法的不变的部分, 并将可变的行为留给子类来实现
- 各子类中公共的行为应被提取出来并集中到一个公共父类中以避免代码重复
- 控制子类的扩展

#### 特性

##### 优点

- 模板方法模式在定义了一组算法, 将具体的实现交由子类负责
- 模板方法模式是一种代码复用的基本技术
- 模板方法模式导致一种反向的控制结构, 通过一个父类调用其子类的操作, 通过对子类的扩展增加新的行为, 符合开闭原则

##### 缺点

每一个不同的实现都需要一个子类来实现, 导致类的个数增加, 使得系统更加庞大臃肿

### [访问者 - `Visitor`](src/Behavioral/Visitor)

#### 定义

封装一些施加于某种数据结构元素之上的操作. 一旦这些操作需要修改, 接受这个操作的数据结构可以保持不变. 访问者模式适用于数据结构相对稳定的系统, 它把数据结构和作用于结构上的操作之间的耦合解脱开, 使得操作集合可以相对自由的演化

#### 场景

- 一个对象结构包含很多类操作, 它们有不同的接口, 而你想对这些对象实施一些依赖于其具体类的操作
- 一个对象中存在着一些与本对象不相干(或者关系较弱)的操作, 为了避免这些操作污染这个对象, 则可以使用访问者模式来把这些操作封装到访问者中去
- 定义对象结构的类很少改变, 但经常需要在此结构上定义新的操作

#### 特性

##### 优点

- 将数据结构和作用于结构上的操作解耦, 使得操作集合可以独立变化
- 添加新的操作或者说访问者会非常容易
- 将对各个元素的一组操作集中在一个访问者类当中
- 使得类层次结构不改变的情况下, 可以针对各个层次做出不同的操作, 而不影响类层次结构的完整性
- 可以跨越类层次结构, 访问不同层次的元素类, 做出相应的操作

##### 缺点

- 增加新的元素会非常困难
- 实现起来比较复杂, 会增加系统的复杂性
- 破坏封装, 如果将访问行为放在各个元素中, 则可以不暴露元素的内部结构和状态, 但使用访问者模式的时候, 为了让访问者能获取到所关心的信息, 元素类不得不暴露出一些内部的状态和结构, 就像收入和支出类必须提供访问金额和单子的项目的方法一样

## 创建型模式 - `Creational Pattern`

### [抽象工厂 - `AbstractFactory`](src/Creational/AbstractFactory)

#### 定义

为一个产品族提供了统一的创建接口. 当需要这个产品族的某一系列的时候, 可以从抽象工厂中选出相应的系列创建一个具体的工厂类

#### 场景

- 一个系统不应当依赖于产品类实例如何被创建, 组合和表达的细节, 这对于所有类型的工厂模式都是重要的
- 系统中有多于一个的产品族, 而每次只使用其中某一产品族
- 属于同一个产品族的产品将在一起使用, 这一约束必须在系统的设计中体现出来
- 系统提供一个产品类的库, 所有的产品以同样的接口出现, 从而使客户端不依赖于具体实现

#### 特性

##### 优点

- 抽象工厂模式隔离了具体类的生成, 使得客户并不需要知道什么被创建. 由于这种隔离, 更换一个具体工厂就变得相对容易. 所有的具体工厂都实现了抽象工厂中定义的那些公共接口, 因此只需改变具体工厂的实例, 就可以在某种程度上改变整个软件系统的行为. 另外, 应用抽象工厂模式可以实现高内聚低耦合的设计目的, 因此抽象工厂模式得到了广泛的应用
- 当一个产品族中的多个对象被设计成一起工作时, 它能够保证客户端始终只使用同一个产品族中的对象. 这对一些需要根据当前环境来决定其行为的软件系统来说, 是一种非常实用的设计模式
- 增加新的具体工厂和产品族很方便, 无须修改已有系统, 符合开闭原则

##### 缺点

- 在添加新的产品对象时, 难以扩展抽象工厂来生产新种类的产品, 这是因为在抽象工厂角色中规定了所有可能被创建的产品集合, 要支持新种类的产品就意味着要对该接口进行扩展, 而这将涉及到对抽象工厂角色及其所有子类的修改, 显然会带来较大的不便
- 开闭原则的倾斜性(增加新的工厂和产品族容易, 增加新的产品等级结构麻烦)

### [创建(建造)者或生成器 - `Builder`](src/Creational/Builder)

#### 定义

将一个复杂对象的构建与它的表示分离, 使得同样的构建过程可以创建不同的表示

#### 场景

- 需要生成的产品对象有复杂的内部结构, 这些产品对象通常包含多个成员属性
- 需要生成的产品对象的属性相互依赖, 需要指定其生成顺序
- 对象的创建过程独立于创建该对象的类. 在建造者模式中引入了指挥者类, 将创建过程封装在指挥者类中, 而不在建造者类中
- 隔离复杂对象的创建和使用, 并使得相同的创建过程可以创建不同的产品

#### 特性

##### 优点

- 在建造者模式中, 客户端不必知道产品内部组成的细节, 将产品本身与产品的创建过程解耦, 使得相同的创建过程可以创建不同的产品对象
- 每一个具体建造者都相对独立, 而与其他的具体建造者无关, 因此可以很方便地替换具体建造者或增加新的具体建造者, 用户使用不同的具体建造者即可得到不同的产品对象
- 可以更加精细地控制产品的创建过程. 将复杂产品的创建步骤分解在不同的方法中, 使得创建过程更加清晰, 也更方便使用程序来控制创建过程
- 增加新的具体建造者无须修改原有类库的代码, 指挥者类针对抽象建造者类编程, 系统扩展方便, 符合开闭原则

##### 缺点

- 建造者模式所创建的产品一般具有较多的共同点, 其组成部分相似, 如果产品之间的差异性很大, 则不适合使用建造者模式, 因此其使用范围受到一定的限制
- 如果产品的内部变化复杂, 可能会导致需要定义很多具体建造者类来实现这种变化, 导致系统变得很庞大

### [工厂方法 - `FactoryMethod`](src/Creational/FactoryMethod)

#### 定义

定义一个接口用于创建对象, 但是让子类决定初始化哪个类. 工厂方法把一个类的初始化下放到子类

#### 场景

- 一个类不知道它所需要的对象的类: 在工厂方法模式中, 客户端不需要知道具体产品类的类名, 只需要知道所对应的工厂即可, 具体的产品对象由具体工厂类创建; 客户端需要知道创建具体产品的工厂类
- 一个类通过其子类来指定创建哪个对象: 在工厂方法模式中, 对于抽象工厂类只需要提供一个创建产品的接口, 而由其子类来确定具体要创建的对象, 利用面向对象的多态性和里氏代换原则, 在程序运行时, 子类对象将覆盖父类对象, 从而使得系统更容易扩展
- 将创建对象的任务委托给多个工厂子类中的某一个, 客户端在使用时可以无须关心是哪一个工厂子类创建产品子类, 需要时再动态指定, 可将具体工厂类的类名存储在配置文件或数据库中

#### 特性

##### 优点

- 在工厂方法模式中, 工厂方法用来创建客户所需要的产品, 同时还向客户隐藏了哪种具体产品类将被实例化这一细节, 用户只需要关心所需产品对应的工厂, 无须关心创建细节, 甚至无须知道具体产品类的类名
- 基于工厂角色和产品角色的多态性设计是工厂方法模式的关键. 它能够使工厂可以自主确定创建何种产品对象, 而如何创建这个对象的细节则完全封装在具体工厂内部. 工厂方法模式之所以又被称为多态工厂模式, 是因为所有的具体工厂类都具有同一抽象父类
- 使用工厂方法模式的另一个优点是在系统中加入新产品时, 无须修改抽象工厂和抽象产品提供的接口, 无须修改客户端, 也无须修改其他的具体工厂和具体产品, 而只要添加一个具体工厂和具体产品就可以了. 这样, 系统的可扩展性也就变得非常好, 完全符合开闭原则

##### 缺点

- 在添加新产品时, 需要编写新的具体产品类, 而且还要提供与之对应的具体工厂类, 系统中类的个数将成对增加, 在一定程度上增加了系统的复杂度, 有更多的类需要编译和运行, 会给系统带来一些额外的开销
- 由于考虑到系统的可扩展性, 需要引入抽象层, 在客户端代码中均使用抽象层进行定义, 增加了系统的抽象性和理解难度, 且在实现时可能需要用到`DOM`, 反射等技术, 增加了系统的实现难度

### [多例 - `Multiton`](src/Creational/Multiton)

#### 定义

确保一个类只有命名的实例, 并提供对这些实例的全局访问

#### 场景

多并发请求环境下, 系统需要为每个客户端的独立请求提供单独服务的资源, 但是系统总的开销是有限的, 系统在并发量很大时也不可能为所有的并发请求同时提供相应的资源, 否则不但系统资源消耗量大而且非常耗时. 这时就可以考虑使用池的概念, 也即是一种多例模式的实现, 如: 数据库连接池

#### 特性

##### 优点

- 有上限的多例类: 一个实例数目有上限的多例类已经把实例的上线当做逻辑的一部分, 并创造到了多例类的内部
- 无上限多例模式: 多例类的实例数目并不需要有上限, 由于事先不知道要创建多少个实例, 因此必然使用聚集管理所有的实例

##### 缺点

### [对象池 - `Pool`](src/Creational/Pool)

#### 定义

通过回收利用对象避免获取和释放资源所需的昂贵成本

#### 场景

- 需要频繁创建和销毁对象
- 类的实例化过程开销较大
- 类的实例化的频率较高
- 类参与交互的时间周期有限
- 类的实例可重用于交互, 每个对象都封装了像数据库或者网络连接这样很昂贵又可以重用的资源
- 对象大小相仿
- 在堆上进行对象内存分配十分缓慢或者会导致内存碎片

#### 特性

##### 优点

- 节省了创建类的实例的开销
- 节省了创建类的实例的时间

##### 缺点

- 池的大小设置, 池可能在不需要的对象上浪费内存
- 同步
- 脏对象导致内存泄漏, 影响程序处理数据
- 生命周期
- 异常处理

### [原型 - `Prototype`](src/Creational/Prototype)

#### 定义

用原型实例指定创建对象的种类, 并且通过拷贝这些原型创建新的对象

#### 场景

- 创建新对象成本较大(如: 初始化需要占用较长的时间, 占用太多的 `CPU` 资源或网络资源), 新的对象可以通过原型模式对已有对象进行复制来获得, 如果是相似对象, 则可以对其成员变量稍作修改
- 如果系统要保存对象的状态, 而对象的状态变化很小, 或者对象本身占用内存较少时, 可以使用原型模式配合备忘录模式来实现
- 需要避免使用分层次的工厂类来创建分层次的对象, 并且类的实例对象只有一个或很少的几个组合状态, 通过复制原型对象得到新实例可能比使用构造函数创建一个新实例更加方便

#### 特性

##### 优点

- 当创建新的对象实例较为复杂时, 使用原型模式可以简化对象的创建过程, 通过复制一个已有实例可以提高新实例的创建效率
- 扩展性较好, 由于在原型模式中提供了抽象原型类, 在客户端可以针对抽象原型类进行编程, 而将具体原型类写在配置文件中, 增加或减少产品类对原有系统都没有任何影响
- 原型模式提供了简化的创建结构, 工厂方法模式常常需要有一个与产品类等级结构相同的工厂等级结构, 而原型模式就不需要这样, 原型模式中产品的复制是通过封装在原型类中的克隆方法实现的, 无须专门的工厂类来创建产品
- 可以使用深克隆的方式保存对象的状态, 使用原型模式将对象复制一份并将其状态保存起来, 以便在需要的时候使用(如: 恢复到某一历史状态), 可辅助实现撤销操作

##### 缺点

- 需要为每一个类配备一个克隆方法, 而且该克隆方法位于一个类的内部, 当对已有的类进行改造时, 需要修改源代码, 违背了开闭原则
- 在实现深克隆时需要编写较为复杂的代码, 而且当对象之间存在多重的嵌套引用时, 为了实现深克隆, 每一层对象对应的类都必须支持深克隆, 实现起来可能会比较麻烦

### [简单工厂 - `SimpleFactory`](src/Creational/SimpleFactory)

#### 定义

又称为静态工厂方法(`Static Factory Method`)模式, 它属于类创建型模式. 在简单工厂模式中, 可以根据参数的不同返回不同类的实例. 简单工厂模式专门定义一个类来负责创建其他类的实例, 被创建的实例通常都具有共同的父类

#### 场景

- 工厂类负责创建的对象比较少; 由于创建的对象较少, 不会造成工厂方法中的业务逻辑太过复杂
- 客户端只知道传入工厂类的参数, 对于如何创建对象不关心; 客户端既不需要关心创建细节, 甚至连类名都不需要记住, 只需要知道类型所对应的参数

#### 特性

##### 优点

- 工厂类含有必要的判断逻辑, 可以决定在什么时候创建哪一个产品类的实例, 客户端可以免除直接创建产品对象的责任, 而仅仅消费产品; 简单工厂模式通过这种做法实现了对责任的分割, 它提供了专门的工厂类用于创建对象
- 客户端无须知道所创建的具体产品类的类名, 只需要知道具体产品类所对应的参数即可, 对于一些复杂的类名, 通过简单工厂模式可以减少使用者的记忆量
- 通过引入配置文件, 可以在不修改任何客户端代码的情况下更换和增加新的具体产品类, 在一定程度上提高了系统的灵活性

##### 缺点

- 由于工厂类集中了所有产品创建逻辑, 一旦不能正常工作, 整个系统都要受到影响
- 使用简单工厂模式将会增加系统中类的个数, 在一定程序上增加了系统的复杂度和理解难度
- 系统扩展困难, 一旦添加新产品就不得不修改工厂逻辑, 在产品类型较多时, 有可能造成工厂逻辑过于复杂, 不利于系统的扩展和维护
- 简单工厂模式由于使用了静态工厂方法, 造成工厂角色无法形成基于继承的等级结构

### [单例 - `Singleton`](src/Creational/Singleton)

#### 定义

单例模式确保某一个类只有一个实例, 而且自行实例化并向整个系统提供这个实例, 这个类称为单例类, 它提供全局访问的方法

#### 场景

- 系统只需要一个实例对象, 如系统要求提供一个唯一的序列号生成器, 或者需要考虑资源消耗太大而只允许创建一个对象
- 客户调用类的单个实例只允许使用一个公共访问点, 除了该公共访问点, 不能通过其他途径访问该实例
- 在一个系统中要求一个类只有一个实例时才应当使用单例模式. 反过来, 如果一个类可以有几个实例共存, 就需要对单例模式进行改进, 使之成为多例模式

#### 特性

##### 优点

- 提供了对唯一实例的受控访问. 因为单例类封装了它的唯一实例, 所以它可以严格控制客户怎样以及何时访问它, 并为设计及开发团队提供了共享的概念
- 由于在系统内存中只存在一个对象, 因此可以节约系统资源, 对于一些需要频繁创建和销毁的对象, 单例模式无疑可以提高系统的性能
- 允许可变数目的实例. 我们可以基于单例模式进行扩展, 使用与单例控制相似的方法来获得指定个数的对象实例

##### 缺点

- 由于单例模式中没有抽象层, 因此单例类的扩展有很大的困难
- 单例类的职责过重, 在一定程度上违背了单一职责原则. 因为单例类既充当了工厂角色, 提供了工厂方法, 同时又充当了产品角色, 包含一些业务方法, 将产品的创建和产品的本身的功能融合到一起
- 滥用单例将带来一些负面问题, 如为了节省资源将数据库连接池对象设计为单例类, 可能会导致共享连接池对象的程序过多而出现连接池溢出

### [静态工厂 - `StaticFactory`](src/Creational/StaticFactory)

#### 定义

类的创建模式, 又叫做简单工厂模式, 静态工厂模式是一个工厂对象决定创建出哪一种产品类的实例. 类似于抽象工厂模式, 这种模式是用于创建一系列相关或依赖对象. 这与抽象工厂模式的区别在于静态工厂模式只使用一个静态方法来创建它所能创建的所有类型的对象

#### 场景

- 工厂类负责创建的对象比较少; 由于创建的对象较少, 不会造成工厂方法中的业务逻辑太过复杂
- 客户端只知道传入工厂类的参数, 对于如何创建对象不关心; 客户端既不需要关心创建细节, 甚至连类名都不需要记住, 只需要知道类型所对应的参数

#### 特性

##### 优点

- 工厂类含有必要的判断逻辑, 可以决定在什么时候创建哪一个产品类的实例, 客户端可以免除直接创建产品对象的责任, 而仅仅消费产品; 静态工厂模式通过这种做法实现了对责任的分割, 它提供了专门的工厂类用于创建对象
- 客户端无须知道所创建的具体产品类的类名, 只需要知道具体产品类所对应的参数即可, 对于一些复杂的类名, 通过静态工厂模式可以减少使用者的记忆量
- 通过引入配置文件, 可以在不修改任何客户端代码的情况下更换和增加新的具体产品类, 在一定程度上提高了系统的灵活性

##### 缺点

- 由于工厂类集中了所有产品创建逻辑, 一旦不能正常工作, 整个系统都要受到影响
- 使用静态工厂模式将会增加系统中类的个数, 在一定程序上增加了系统的复杂度和理解难度
- 系统扩展困难, 一旦添加新产品就不得不修改工厂逻辑, 在产品类型较多时, 有可能造成工厂逻辑过于复杂, 不利于系统的扩展和维护
- 静态工厂模式由于使用了静态工厂方法, 造成工厂角色无法形成基于继承的等级结构

## 结构型模式 - `Structural Pattern`

### [适配器 - `Adapter`](src/Structural/Adapter)

#### 定义

将某个类的接口转换成客户端期望的另一个接口表示. 适配器模式可以消除由于接口不匹配所造成的类兼容性问题

#### 场景

- 系统需要使用现有的类, 而这些类的接口不符合系统的需要
- 想要建立一个可以重复使用的类, 用于与一些彼此之间没有太大关联的一些类, 包括一些可能在将来引进的类一起工作

#### 特性

##### 优点

- 将目标类和适配者类解耦, 通过引入一个适配器类来重用现有的适配者类, 而无须修改原有代码
- 增加了类的透明性和复用性, 将具体的实现封装在适配者类中, 对于客户端类来说是透明的, 而且提高了适配者的复用性
- 灵活性和扩展性都非常好, 通过使用配置文件, 可以很方便地更换适配器, 也可以在不修改原有代码的基础上增加新的适配器类, 完全符合开闭原则
- 类适配器模式: 由于适配器类是适配者类的子类, 因此可以在适配器类中置换一些适配者的方法, 使得适配器的灵活性更强
- 对象适配模式: 一个对象适配器可以把多个不同的适配者适配到同一个目标, 也就是说, 同一个适配器可以把适配者类和它的子类都适配到目标接口

##### 缺点

- 过多地使用适配器, 会让系统非常零乱, 不易整体进行把握
- 类适配器模式: 对于 `Java`, `C#` 等不支持多重继承的语言, 一次最多只能适配一个适配者类, 而且目标抽象类只能为抽象类, 不能为具体类, 其使用有一定的局限性, 不能将一个适配者类和它的子类都适配到目标接口
- 对象适配器模式: 与类适配器模式相比, 要想置换适配者类的方法就不容易. 如果一定要置换掉适配者类的一个或多个方法, 就只好先做一个适配者类的子类, 将适配者类的方法置换掉, 然后再把适配者类的子类当做真正的适配者进行适配, 实现过程较为复杂

### [桥接 - `Bridge`](src/Structural/Bridge)

#### 定义

将一个抽象与实现解耦, 以便两者可以独立的变化. 它是一种对象结构型模式, 又称为柄体(`Handle and Body`)模式或接口(`Interface`)模式

#### 场景

- 如果一个系统需要在构件的抽象化角色和具体化角色之间增加更多的灵活性, 避免在两个层次之间建立静态的继承联系, 通过桥接模式可以使它们在抽象层建立一个关联关系
- 象化角色和实现化角色可以以继承的方式独立扩展而互不影响, 在程序运行时可以动态将一个抽象化子类的对象和一个实现化子类的对象进行组合, 即系统需要对抽象化角色和实现化角色进行动态耦合
- 一个类存在两个独立变化的维度, 且这两个维度都需要进行扩展
- 虽然在系统中使用继承是没有问题的, 但是由于抽象化角色和具体化角色需要独立变化, 设计要求需要独立管理这两者
- 对于那些不希望使用继承或因为多层次继承导致系统类的个数急剧增加的系统, 桥接模式尤为适用

#### 特性

##### 优点

- 分离抽象接口及其实现部分
- 桥接模式有时类似于多继承方案, 但是多继承方案违背了类的单一职责原则(即一个类只有一个变化的原因), 复用性比较差, 而且多继承结构中类的个数非常庞大, 桥接模式是比多继承方案更好的解决方法
- 桥接模式提高了系统的可扩充性, 在两个变化维度中任意扩展一个维度, 都不需要修改原有系统
- 实现细节对客户透明, 可以对用户隐藏实现细节

##### 缺点

- 桥接模式的引入会增加系统的理解与设计难度, 由于聚合关联关系建立在抽象层, 要求开发者针对抽象进行设计与编程
- 桥接模式要求正确识别出系统中两个独立变化的维度, 因此其使用范围具有一定的局限性

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

### [注册 - `Registry`](src/Structural/Registry)

#### 定义

也叫注册模式, 注册器模式. 注册树模式通过将对象实例注册到一棵全局的对象树上, 需要的时候从对象树上采摘的模式设计方法, 注册树上的实例却可以无数次获取

#### 场景

全局共享和交换对象

#### 特性

##### 优点

对于实例, 能够更好地统筹管理安排, 就像使用全局变量一样的方便实用

##### 缺点

## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fimajinyun%2Fphp-design-pattern.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Fimajinyun%2Fphp-design-pattern?ref=badge_large)
