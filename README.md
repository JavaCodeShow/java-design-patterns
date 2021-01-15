## <<大话设计模式>> java语言版本

### 设计模式几大原则

1. **单一职责原则**:  就一个类而言，应该仅有一个引起它变化的原因

   > 通俗的讲就是我们不要让一个承担过多的职责，如果一个类承担的职责过多，就等于把这些职责耦合在一起，一个职责的变化可能会削弱或者抑制这个类完成其他职责的能力。 这种耦合会导致脆弱的设计，当变化发生时，设计会遭受到破坏。

2. **开放封闭原则：** 类，模块，函数等应该是可以扩展的，但是不可以修改

   > 开放封闭有两个含义：一个是对于扩展是开放，另一个是对于修改是封闭的。
   >
   > 对于开发者莱索，需求肯定是变化的，但是有新需求，我们就要把类重新改一遍，这显然是令人头痛的，所以我们设计程序时，面对需求的改变要尽可能得保证相对稳定，尽量通过扩展的方式来实现变化，而不是通过修改原有的代码来实现。

3. **里氏替换原则：** 所有引用基类(父类)的地方必须能透明的使用其子类的对象

   > 在软件中将一个基类对象替换成其子类对象，程序将不会产生任何错误和异常，反过来则不成立，如果一个软件实体使用的是一个子类对象的话，那么它不一定能够使用子类对象。里式替换原则是实现开放封闭原则的重要方式之一。由于使用基类对象的地方都可以使用子类对象， 因此在程序中尽量使用基类类型来对对象进行定义，而在运行时在确定其子类类型，用子类对象来替换父类对象。在使用里式替换原则是需要注意以下几个问题：
   >
   > 子类的所有方法必须在父类中声明，或子类必须实现父类中声明的所有方法。根据里式替换原则，为了保证系统的扩展性，在程序中通常使用父类来定义。如果一个方法只存于子类中，在父类中不提供相应的声明，则无法在以父类定义的对象中使用该方法。
   >
   > 我们运用里式替换原则时，尽量把父类设计为抽象类或接口，让子类继承父类或实现父接口，并实现在父类中声明的方法、运行时，子类实例替换父类实例，我们可以很方便的扩展系统功能，同时无序修改原有子类的代码；增加新的功能可以通过增加一个新的子类来实现。里式替换原则是开放封闭原则的具体实现手段之一。
   >
   > 在java语言中，在编译阶段，java编译器会检查一个程序是否符合里式替换原则。这是一个与实现无关，纯语法意义上的检查，但Java编译器的检查是有局限性的

4. **依赖倒置原则：** 高层模块(调用端)不应该依赖底层模块，两者都应该依赖于抽象。抽象不应该依赖于细节(实现类),细节应该依赖于抽象。

   > 在Java中，抽象指接口或者抽象类，两者都是不能直接被实例化；细节就是实现类，实现接口或者继承抽象类而产生的就是细节，也就是可以加上一个关键字 new 产生的对象。高层模块就是调用端，低层模块就是具体实现类。 依赖倒置原则在 java 中的表现就是，模块间的依赖通过抽象发生，实现类之间不发生直接依赖关系，其依赖关系就是通过接口或者抽象类产生的。如果类与类直接依赖细节，那么就会直接耦合。如此一来，就会同时修改依赖者代码，这样限制了可扩展性。

5. **迪米特原则：** 一个软件实体应当少的与其他实体发生相互作用。

   > 这也被称最好知识原则。如果一个系统符合迪米特原则，那么当其中某一个模块发生修改时，就会尽量少的影响其他模块。迪米特原则要求我们在设计系统是，应该尽量减少对象之间的交互。如果两个对象之间不必彼此直接通向，那么这两个对象就不应当发生任何直接的相互作用。如果其中的一个对象需要调用另一个对象的某一个方法，则可以通过第三者转发这个调用。简言之，就是通过引入一个合理的第三者来降低现有对象之间的耦合度。在将迪米特原则运用到系统设计中时，要注意以下几点：
   >
   > - 在类的划分上，应当尽量创建松耦合的类。类之间的耦合越低，就越有利于复用。一个处在松耦合中的类一旦被修改，则不会对关联的类造成太大波及。
   > - 在类的结构上，每一个类都应当尽量降低其成员变量和成员函数的访问权限。
   > - 在对其他类的引用上，一个对象对其他对象的引用应当降到最低。

6. **接口隔离原则：** 一个类对另一个类的依赖应该建立在最小的接口上

   > 建立单一接口，不要建立庞大臃肿的接口：尽量细化接口，接口中的方法尽量少。也就是说，我们要为各个类建立专用的接口，而不要试图建立一个一个很庞大的接口供所有依赖他的类调用。采取接口隔离原则对接口进行约束时，要注意以下几点：
   >
   > 接口尽量小，但是要有限度。对接口进行细化可以提高程序设计的灵活性；但是如果过小，则会造成接口数量过多，使设计复杂化。所以，一定要适度。
   >
   > - 为依赖接口的类定制服务，只暴露给调用的类他需要的方法，他不需要的方法则隐藏起来，只有专注的为一个模块提供定制服务，才能建立最小的依赖关系。
   >
   > - 为提高内聚，减少对外交互。接口方法尽量少用public 修饰。接口是对外的承诺，承诺越少对系统的开发越有利，变更的风险也越少。

### 设计模式分类

- **创建型模式**：<u>*专注生产对象，不直接使用new*</u>
    - [简单工厂模式](https://github.com/1546844168/java-design-patterns/tree/master/simple-factory)
    - [工厂方法模式](https://github.com/1546844168/java-design-patterns/tree/master/factory-method)
    - [抽象工厂模式](https://github.com/1546844168/java-design-patterns/tree/master/abstract-factory)
    - [原型模式](https://github.com/1546844168/java-design-patterns/tree/master/prototype)
    - [建造者模式](https://github.com/1546844168/java-design-patterns/tree/master/builder)
    - [单例模式](https://github.com/1546844168/java-design-patterns/tree/master/singleton)
- **结构型模式**：*<u>关注类和对象的组合</u>*
    - [适配器模式](https://github.com/1546844168/java-design-patterns/tree/master/adapter)
    - [桥接模式](https://github.com/1546844168/java-design-patterns/tree/master/bridge)
    - [组合模式](https://github.com/1546844168/java-design-patterns/tree/master/composite)
    - [装饰器模式](https://github.com/1546844168/java-design-patterns/tree/master/decorator)
    - [外观模式](https://github.com/1546844168/java-design-patterns/tree/master/facade)
    - [享元模式](https://github.com/1546844168/java-design-patterns/tree/master/flyweight)
    - [代理模式](https://github.com/1546844168/java-design-patterns/tree/master/proxy)
- **行为模式（类行为型模式）**：*<u>关注对象之间的通信</u>*
    - [解释器模式](https://github.com/1546844168/java-design-patterns/tree/master/interpreter)
    - [模板方法模式](https://github.com/1546844168/java-design-patterns/tree/master/template)
- **行为模式（对象行为型模式）**：*<u>关注对象之间的通信</u>*
    - [策略模式](https://github.com/1546844168/java-design-patterns/tree/master/strategy)
    - [观察者模式](https://github.com/1546844168/java-design-patterns/tree/master/observer)
    - [状态模式](https://github.com/1546844168/java-design-patterns/tree/master/state)
    - [备忘录模式](https://github.com/1546844168/java-design-patterns/tree/master/memento)
    - [迭代器模式](https://github.com/1546844168/java-design-patterns/tree/master/iteractor)
    - [命令模式](https://github.com/1546844168/java-design-patterns/tree/master/command)
    - [责任链模式](https://github.com/1546844168/java-design-patterns/tree/master/responsibility-chain)
    - [中介者模式](https://github.com/1546844168/java-design-patterns/tree/master/mediator)
    - [访问者模式](https://github.com/1546844168/java-design-patterns/tree/master/visitor)

### 设计模式定义

1. **简单工厂模式**：到底要实例化哪一个对象，将来会不会增加实例化的对下个，这是很容易变化的地方，通过一个单独的类来做这个实例化的过程，这就是工厂。
   简单工厂模式的最大有点在于工厂类中包含了简单的逻辑判断，根据客户端的选择条件动态的实例化相关的类，对于客户端来说，去除了与具体产品的依赖。


2. **策略模式**：它定义了算法家族，分别封装起来，让他们之间可以相互转换，此模式让算法的变法，不会影响到使用算法的客户

3. **装饰模式**：动态的给一个对象添加一些额外的职责，就增加功能来说，装饰模式比生成子类更为灵活

4. 代理模式：为其他对象提供了一种代理，以控制对这个对象的访问。代理类与被代理类实现了相同的接口。

5. **工厂方法模式**：定义一个用于创建对象的接口，让子类决定实例化哪一个类。工厂方法是的让一个类的实例延迟到了子类。（工厂方法模式相对于简单工厂符合开放-封闭原则的精神）

6. **原型模式**：用原型实例指定创建对象的种类，并且通过拷贝这些原型创建新的对象。原型模式其实就是从一个对象在创建另一个可以定制的对象，而且不需要知道任何创建的细节。（实际上就是浅拷贝与深拷贝）

7. **模板方法模式**：定义一个操作中算法的骨架，而将一些步骤延迟到子类中。模板方法模式使得子类可以不改变一个算法的结构，即可重新定义算法的某些特定步骤。
   模板方法模式给出了逻辑的骨架，而逻辑的组成是一些相应的抽象操作，也有可能是具体的方法，他们都推迟到子类去实现。通过把不变的行为搬移到超类，去除子类中的重复代码。提供了一个很好的代码复用平台。

8. **外观模式：** 为子系统中共的一组接口提供一个人一致的界面，此模式定义了一个高层接口，这个接口使得这一子系统更加容易使用。（MVC便是外观模式的体现）   
