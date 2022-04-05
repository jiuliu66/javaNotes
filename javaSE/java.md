## 第一阶段(P001 - P373)

### 第03章 变量(P035 - P062)

#### 3.1字符型细节

字符串常量只能是单引号，双引号为字符串。

如果你确实希望你的字符串是可变的，则可以使用 toCharArray 将其转换为字符数组。
如果你经常必须连接字符串，最好使用一些其他的数据结构，如 StringBuilder 。

### 第06章 数组、排序和查找(P156 - P191)

```
//动态初始化，默认初始化为0
int[] a = new int[5];
//静态初始化
int[] a = {1,3,5};
```

数组是引用传递，传的是地址，赋值方式为引用赋值。

![](https://raw.githubusercontent.com/jiuliu66/javaNotes/main/javaSE/image/202204051547671.jpg?token=AJ46KCATVQWJ3R6J6SHCZ4DCJP2FM)

![](https://raw.githubusercontent.com/jiuliu66/javaNotes/main/javaSE/image/202204051549756.jpg?token=AJ46KCAALAVWJ53RXI2O5GTCJP2JW)



### 第07章 面向对象编程（基础部分）(P192 - P263) 3.14

#### 7.1对象存在形式

![](https://raw.githubusercontent.com/jiuliu66/javaNotes/main/javaSE/image/202204051549152.jpg?token=AJ46KCBAHLW2532BFMNGIATCJP2LK)

#### 7.2类与对象分配机制

![](https://raw.githubusercontent.com/jiuliu66/javaNotes/main/javaSE/image/202204051549121.jpg?token=AJ46KCATYLFCH3NKJV3OKXLCJP2MC)

#### 7.3对象创建过程

**类和对象的内存分配机制**

* Java内存的结构分析
  1. 堆:存放对象(Cat cat,数组等)
  2. 栈:一般存放基本数据类型(局部变量)
  3. 方法区:常量池(常量,比如字符串),类加载信息
  4. 示意图[Cat (name, age, price)]

* Java创建对象的流程简单分析

```java
Person p = new Person);
p.name = "jack” ;
p.age = 10
```

1. 先加载Person类信息(属性和方法信息,只会加载一次)
2. 在堆中分配空间,进行默认初始化(看规则)
3. 把地址赋给p,p就指向对象
4. 进行指定初始化,比如`p.name =" jack",p.age = 10`

#### 7.4方法调用机制

![](https://raw.githubusercontent.com/jiuliu66/javaNotes/main/javaSE/image/202204051550167.jpg?token=AJ46KCCS65UQANSJTCIPN7TCJP2OO)

#### 7.5引用数据类型传参机制

![](https://raw.githubusercontent.com/jiuliu66/javaNotes/main/javaSE/image/202204051550358.jpg?token=AJ46KCBBKD6UPFT2J3RWAZDCJP2PK)

#### 7.6递归

##### 方法的递归调用：

![](https://raw.githubusercontent.com/jiuliu66/javaNotes/main/javaSE/image/202204051550342.jpg?token=AJ46KCCCOQZGERCRJ2P74JTCJP2Q4)

如果加个else，只输出n=2。那里调用的就返回给哪里。

```java
public void test(int n){
	if(n>2){
        test(n-1);
    }else {
        System.out.println("n="+n);
    }
}
```

##### 递归规则：

* 递归重要规则
  1. 执行一个方法时，就创建一个新的受保护的独立空间(栈空间)
  2. 方法的局部变量是独立的，不会相互影响,比如n变量
  3. 如果方法中使用的是引用类型变量(比如数组，对象)，就会共享该引用类型的数据.
  4. 递归必须向退出递归的条件逼近，否则就是无限递归,出现`StackOverflowError`，死龟了:)
  5. 当一个方法执行完毕，或者遇到`return`，就会返回，遵守谁调用，就将结果返回给谁，同时当方法执行完毕或者返回时，该方法也就执行完毕。

#### 7.7可变参数

```java
public int sum(int... nums){
	return 0;
}
public int sum(String s,int... nums){
	return 0;
}
```

##### 使用细节

1. 可变参数的实参可以为0个或任意多个
2.  可变参数的实参可以为数组
3. 可变参数的本质就是数组
4. 可变参数可以和普通类型的参数一起放在形参列表，但必须保证可变参数在最后
5. 一个形参列表中只能出现一个可变参数

#### 7.8作用域

* 基本使用
  面向对象中，变量作用域是非常重要知识点，相对来说不是特别好理解，请大家注意听，认真思考,要求深刻掌握变量作用域。

  1. 在`java`编程中，主要的变量就是属性(成员变量)和局部变量。

  2. 我们说的局部变量1般是指在成员方法中定义的变量。【举例Cat类:cry)
  3. `java`中作用域的分类
     全局变量:也就是属性，作用域为整个类体Cat类:cry eat等方法 使用属性
     局部变量:也就是除了属性之外的其他变量,作用域为定义它的代码块中!
  4. ==全局变量==可以不赋值，直接使用，因为有默认值，局部变量必须赋值后，才能使用,因为没有默认值。

#### 7.9构造器

* 注意事项和使用细节

  1. 一个类可以定义多个不同的构造器，即构造器重载
     比如:我们可以再给Person类定义一个构造器,用来创建对象的时候,只指定人名不需要指定年龄

  2. 构造器名和类名要相同

  3. 构造器没有返回值

  4. 构造器是完成对象的初始化.并不是创建对象

  5. 在创建对象时,系统自动的调用该类的构造方法

#### 7.10 this的理解

![](https://raw.githubusercontent.com/jiuliu66/javaNotes/main/javaSE/image/202204051553275.jpg?token=AJ46KCG26SW4YDLHFDBRIYDCJP2YU)

**哪个对象调用，this就指向那个对象。**可以是用Object.hashcode()看看地址情况。

* this的注意事项和使用细节
  1. this关键字可以用来访问本类的属性、方法、构造器
  2. this用于区分当前类的属性和局部变量
  3. 访问成员方法的语法:this.方法名(参数列表);
  4. 访问构造器语法:this(参数列表);注意只能在构造器中使用
  5. this不能在类定义的外部使用，只能在类定义的方法中使用.

**访问构造器语法：**this（参数列表）必须放在第一条语句。

### 第08章 面向对象编程（中级部分）(P264 - P361)3.15

#### 8.1IDEA快捷键

1. 生成构造方法等alt + inser[提高开发效率]

2. 查看一个类的层级关系ctrl+H[学习继承后，非常有用]

3. 将光标放在一个方法上，输入ctrl +B，可以选择定位到哪个类的方法[学继承后，非常有用]

4. 自动的分配变量名，通过在后面.var

5. 还有很多其它的快捷键.

   老师要求:练习老师讲过的这些快捷键，这是作为一个专业Java程序员必备技能.

#### 8.2封装

##### **封装步骤**

1. 将属性进行私有化private【不能直接修改属性】

2. 提供一个公共的(public)set方法，用于对属性判断并赋值

   ```java
   public void setXxx(类型参数名){//Xxx表示某个属性
       //加入数据险证的业务逻辑
       属性=参数名;
   }
   ```

3. 提供一个公共的(public)get方法，用于获取属性的值

   ```java
   public 数据类型getXxxO{//权限判断,Xxx某个属性
   	return xx;
   }
   ```

## 第二阶段(P374 - P661)

### 第10章 面向对象编程（高级部分）(P374 - P424)

#### 10.1继承 3.16

##### **继承使用细节**

ctrl+H看到类的继承关系，先加载父类，后加载子类。

1. 子类继承了所有的属性和方法，==非私有的属性和方法可以在子类直接访问==,但是私有属性和方法不能在子类直接访问，要通过父类提供公共的方法去访问

2. 子类必须调用父类的构造器,完成父类的初始化
3. 当创建子类对象时，不管使用子类的哪个构造器，默认情况下总会去调用父类的无参构造器，如果父类没有提供无参构造器，则必须在子类的构造器中用 super去指定使用父类的哪个构造器完成对父类的初始化工作，否则，编译不会通过
4. 如果希望指定去调用父类的某个构造器，则显式的调用一下: super(参数列表)
5. super在使用时，必须放在构造器第一行
6. super()和this()都只能放在构造器第一行，因此这两个方法不能共存在一个构造器

7. java所有类都是Object类的子类, Object是所有类的基类.
8. 父类构造器的调用不限于直接父类!将一直往上追溯直到Object类(顶级父类)
9. 子类最多只能继承一个父类(指直接继承)，即java中是单继承机制。
10. 不能滥用继承，子类和父类之间必须满足`is-a`的逻辑关系

**继承的本质分析**

（1）查看子类是否有该属性

（2）如果子类有这个属性，并且可以访问，则返回信息

（3）如果子类没有这个属性，就看父类有没有这个属性（如果父类有该属性，并且可以访问，就返回信息）

![](https://raw.githubusercontent.com/jiuliu66/javaNotes/main/javaSE/image/202204051554931.png?token=AJ46KCCTTS6NOHYZAABJU2LCJP24O)

#### 10.2 super

**基本介绍**
super代表父类的引用，用于访问父类的属性、方法、构造器

* 基本语法

1. 访问父类的属性，但不能访问父类的private属性[案例]
   ``super.属性名;``

2. 访问父类的方法，不能访问父类的private方法
   ``super.方法名(参数列表);``

3. 访问父类的构造器(这点前面用过):
   super(参数列表);只能放在构造器的第一句，只能出现一句!

```java
//找cal方法时，顺序是，
//(1)先找本类，如果有，则调用
//（2)如果没有，则找父类(如果有，并可以调用，则调用)
//(3)如果父类没有，则继续找父类的父类,整个规则，就是一样的,直到0bject类1/提示:如果查找方法的过程中，找到了，但是不能访问，则报错
```



![递归机制](https://raw.githubusercontent.com/jiuliu66/javaNotes/main/java/image/202204051412387.jpg?token=AJ46KCBFH773SOIXWBOYFSDCJPO7Q)

**super给编程带来的便利/细节/**

1. 调用父类的构造器的好处(分工明确,父类属性由父类初始化，子类的属性由子类初始化)
2. 当子类中有和父类中的成员（属性和方法)重名时，为了访问父类的成员，必须通过super。如果没有重名，使用super、this、直接访问是一样的效果!
3. super的访问不限于直接父类，如果爷爷类和本类中有同名的成员，也可以使用super去访问爷爷类的成员;如果多个基类(上级类)中都有同名的成员，使用super访问遵循就近原则。A->B->C

**super和this的比较**

![](https://raw.githubusercontent.com/jiuliu66/javaNotes/main/javaSE/image/202204051555621.jpg?token=AJ46KCDDDONKXZJA7TZXIRLCJP3D2)

#### 10.3重写

* 注意事项和使用细节
  方法重写也叫方法覆盖，需要满足下面的条件

  1. 子类的方法的参数,方法名称,要和父类方法的参数,方法名称完全一样。

  2. 子类方法的返回类型和父类方法返回类型一样，或者是父类返回类型的子类比如父类返回类型是Object,子类方法返回类型是String

     ```java
     public object getInfo(){
     public String getInfo(){}
     ```

3.  子类方法不能缩小父类方法的访问权限

**重载与重写比较**

![](https://raw.githubusercontent.com/jiuliu66/javaNotes/main/javaSE/image/202204051558165.jpg?token=AJ46KCG5SSCAYEMFP5SC4YDCJP3OG)

#### 10.4多态    3.18

**属性看编译类型，方法看运行类型**

* 多态的具体体现
  2.对象的多态(核心，困难,重点)
  (1)一个对象的编译类型和运行类型可以不一致
  (2)编译类型在定义对象时,就确定了，不能改变
  3)运行类型是可以变化的.
  (4)编译类型看定义时=号的左边,运行类型看=号的右边

  ```java
  Animal animal = new Dog0;//animal编译类型是Animal,运行类型Dog
   animal = new Cat();//animal的运行类型变成了Cat,编译类型仍然是 Animal
  ```

* 多态注意事项和细节讨论
  多态的前提是:两个对象(类)存在继承关系
  多态的向上转型
* 1)本质:父类的引用指向了子类的对象
* 2)语法:父类类型引用名=new子类类型();
* 3)特点:编译类型看左边，运行类型看右边。
  可以调用父类中的所有成员(需遵守访问权限)，不能调用子类中特有成员;
  最终运行效果看子类的具体实现!

**多态的向上转型**

![](https://raw.githubusercontent.com/jiuliu66/javaNotes/main/javaSE/image/202204051603128.jpg?token=AJ46KCAFFEP4TQ27OYHVDN3CJP4AA)

****

**向上转型调用方法的规则如下:**

1. 可以调用父类中的所有成员(需遵守访问权限)
2. 但是不能调用子类的特有的成员
3. 因为在编译阶段，能调用哪些成员,是由编译类型来决定的/ / animal.catchMouse();错误
4. 最终运行效果看子类(运行类型)的具体实现，即调用方法时，按照从子类(运行类型)开始查找方法//，然后调用，规则我前面我们讲的方法调用规则一致。

1.成员变量，编译看左，运行看左。

2.成员方法，编译看左，运行看右。

##### **向下转型**

1. 语法:子类类型引用名=(子类类型) ==父类引用==;
2. 只能强转父类的引用，不能强转父类的对象
3. 要求父类的引用必须指向的是当前目标类型的对象
4. 当向下转型后，可以调用子类类型中所有的成员

##### **动态绑定**

![递归机制](https://raw.githubusercontent.com/jiuliu66/javaNotes/main/java/image/202204051413015.jpg?token=AJ46KCBMXOXNBDUIXQMU4WDCJPPB6)



#### 10.5`Object`类3.19

##### **==和equals运算符**

1. ==:既可以判断基本类型，又可以判断引用类型
2. ==:如果判断基本类型，判断的是值是否相等。示例: int i=10; double d=10.0;
3. ==: 如果判断引用类型，判断的是地址是否相等，即判定是不是同一个对象

4. equals: 是Object类中的方法，只能判断引用类型，如何看Jdk源码,看老师演示:
5. 默认判断的是地址是否相等，子类中往往重写该方法，用于判断内容是否相等。比如lnteger,String【看看String和 Integer的equals源代码】

##### **hashcode方法**

1)提高具有哈希结构的容器的效率!

2)两个引用，如果指向的是同一个对象，则哈希值肯定是一样的!

3)两个引用，如果指向的是不同对象，则哈希值是不一样的

4)哈希值主要根据地址号来的!，不能完全将哈希值等价于地址。

5)后面在集合，中hashCode 如果需要的话，也会重写

##### **toString方法**

* 基本介绍
  默认返回:全类名+@+哈希值的十六进制，【查看Object 的 toString方法】子类往往重写toString方法，用于返回对象的属性信息

  ```java
  public String tostring(
  	return getclass().getName() + "@”+ Integer.toHexString(hashCode());
  }
  ```

* 重写toString方法，打印对象或拼接对象时，都会自动调用该对象的toString形式.
* 当直接输出一个对象时，toString方法会被默认的调用

##### **finalize方法**

1. 当对象被回收时，系统自动调用该对象的`finalize`方法。子类可以重写该方法,做一些释放资源的操作【演示】
2. 什么时候被回收:当某个对象没有任何引用时，则`jvm`就认为这个对象是一个垃圾对象，就会使用垃圾回收机制来销毁该对象，在销毁该对象前,会先调用`finalize`方法。
3. 垃圾回收机制的调用，是由系统来决定,也可以通过`System.gc()`主动触发垃圾
   回收机制，测试:Car [name]

##### **断点调试**

* 一个实际需求

  1. 在开发中，新手程序员在查找错误时,这时老程序员就会温馨提示，可以用断点调试,一步一步的看源码执行的过程，从而发现错误所在。
  2. 重要提示:在断点调试过程中，是运行状态，是以对象的运行类型来执行的.

  ```java
  A extends B; B b = new A(); b.xx();
  ```

* 断点调试介绍
  1. 断点调试是指在程序的某一行设置一个断点，调试时，程序运行到这一行就会停住，
     然后你可以一步一步往下调试，调试过程中可以看各个变量当前的值，出错的话，调试到出错的代码行即显示错误，停下。进行分析从而找到这个Bug
  2. 断点调试是程序员必须掌握的技能。
  3. 断点调试也能帮助我们查看`java`底层源代码的执行过程，提高程序员的Java水平。

##### 快捷键

![](https://raw.githubusercontent.com/jiuliu66/javaNotes/main/javaSE/image/202204051609796.jpg?token=AJ46KCABSMBI5NCKN5P266TCJP4WS)

#### 10.6类变量和类方法

##### **类变量**

https://blog.csdn.net/x iya/article/details/81260154/
https://www.zhihu.com/question/59174759/answer/163207831

有些书说在方法区... jdk版本有关系,记住一点: static变量是对象共享
不管static变量在哪里，共识(1) static变量是同一个类所有对象共享(2) static类变量，在类加载的时候就生成了.

**类变量使用注意事项和细节讨论 **

1. 什么时候需要用类变量
   当我们需要让某个类的所有对象都共享一个变量时，就可以考虑使用类变量(静态变量):比如:定义学生类，统计所有学生共交多少钱。`Student (name, staticfee)`

2. 类变量与实例变量(普通属性)区别

   类变量是该类的所有对象共享的，而实例变量是每个对象独享的。

3. 加上static称为类变量或静态变量,否则称为实例变量/普通变量/非静态变量

4. 类变量可以通过类名.类变量名或者对象名.类变量名来访问，但java设计者推荐
   我们使用类名.类变量名方式访问。【前提是满足访问修饰符的访问权限和范围】

5. 实例变量不能通过类名.类变量名方式访问。
6. 类变量是在类加载时就初始化了，也就是说，即使你没有创建对象，只要类加载了,就可以使用类变量了。[案例演示]
7. 类变量的生命周期是随类的加载开始,随着茭消亡而销毁。[举例,，Monster.name][案例演示]

##### **类方法**

类方法经典的使用场景
>当方法中不涉及到任何和对象相关的成员，则可以将方法设计成静态方法,提高开发效率。
>
>比如:工具类中的方法utils
>Math类、Arrays类、Collections集合类看下源码:
>小结
>在程序员实际开发，往往会将一些通用的方法，设计成静态方法，这样我们不需要创建对象就可以使用了，比如打印一维数组，冒泡排序,完成某个计算任务等..[举例说明...]

##### 注意事项

> 1)类方法和普通方法都是随着类的加载而加载，将结构信息存储在方法区;
> 	类方法中无this的参数
> 	普通方法中隐含着this的参数
> 2)类方法可以通过类名调用，也可以通过对象名调用。[举例]
>
> 3)普通方法和对象有关，需要通过对象名调用，比如对象名.方法名(参数)，不能通过类名调用。【举例]
>
> 4)类方法中不允许使用和对象有关的关键字，比如this和super。普通方法(成员方法)可以。【举例]
>
> 5)类方法(静态方法)中只能访问静态变量或静态方法。【如何理解】
>
> 6)普通成员方法，既可以访问普通变量(方法)，也可以访问静态变量(方法)。
>
> ==小结:==静态方法，只能访问静态的成员，非静态的方法，可以访问静态成员和非静态成员(必须遵守访问权限)

##### **main方法**

* 深入理解main方法
  解释main方法的形式:public static void main(String[] args)
  1. java虚拟机需要调用类的main()方法，所以该方法的访问权限必须是public
  2.  java虚拟机在执行main()方法时不必创建对象，所以该方法必须是static
  3. 该方法接收String类型的数组参数，该数组中保存执行java命令时传递给所运行的类的参数
  4. java 执行的程序参数1参数2参数3

>特别提示:
>1)在main()方法中，我们可以直接调用main方法所在类的静态方法或静态属性。
>
>2)但是，不能直接访问该类中的非静态成员，必须创建该类的一个实例对象后，才能通过这个对象去访问类中的非静态成员

#### 10.7代码块

* 代码块的好处:

  > 1)相当于另外一种形式的构造器(对构造器的补充机制)，可以做初始化的操作
  > 2)场景:如果多个构造器中都有重复的语句，可以抽取到初始化块中，提高代码的重用性

**3个构造器重载**

> (1）下面的三个构造器都有相同的语句
>
> (2)这样代码看起来比较冗余
>
> (3)这时我们可以把相同的语句，放入到一个代码块中，即可
>
> (4)这样当我们不管调用哪个构造器，创建对象，都会先调用代码块的内容 
>
> (5)代码块调用的顺序优先于构造器。

##### **代码块使用细节**


1) static代码块也叫静态代码块，作用就是对类进行初始化，而且它随着类的加载而执行，并且只会行一次。如果是普通代码块，每创建一个对象，就执行。
2) ==类什么时候被加载==
  * 创建对象实例时(new)
  * 创建子类对象实例,父类也会被加载
  * 使用类的静态成员时(静态属性,静态方法)案例演示:A类extends B类的静态块

3. .普通的代码块，在创建对象实例时，会被隐式的调用。
   被创建一次，就会调用一次。
   如果只是使用类的静态成员时，普通代码块并不会执行。
   小结:1. static代码块是==类加载==时，执行,只会执行一次2.普通代码块是在创建对象时调用的，创建一次，调用一次

   3.类加载的3种情况,需要记住.

4. 创建一个对象时，在一个类调用顺序是:(==重点，难点==)∶
   1调用静态代码块和静态属性初始化(注意:静态代码块和静态属性初始化调用的优先级一样，如果有多个静态代码块和多个静态变量初始化，则按他们定义的顺序调用)[举例说明]
   ②调用普通代码块和普通属性的初始化(注意:普通代码块和普通属性初始化调用的优先级一样,如果有多个普通代码块和多个普通属性初始化，则按定义顺序调用)
   ③调用构造方法。

5. 构造器的最前面其实隐含了super()和调用普通代码块，新写一个类演示【截图+说明],静态相关的代码块，属性初始化，在类加载时，就执行完毕
   ，因此是优先于构造器和普通代码块执行的CodeBlockDetail03.java

   ```java
   class A {
   	public AO {V/构造器
           M/这里有隐藏的执行要求
           11(1) super)://这个知识点,在前面讲解继承的时候,老师说(2)调用普通代码块的
           System.out.println("ok");}
   }
   ```

6. 我们看一下创建一个子类对象时(继承关系)，他们的静态代码块，静态属性初
   始化，普通代码块，普通属性初始化，构造方法的调用顺序如下:

> 1.父类的静态代码块和静态属性(优先级一样,按定义顺序执行)
>
> 2.子类的静态代码块和静态属性(优先级一样，按定义顺序执行)
>
> 3.父类的普通代码块和普通属性初始化(优先级一样，按定义顺序执行)
>
> 4.父类的构造方法
>
> 5.子类的普通代码块和普通属性初始化(优先级一样，按定义顺序执行)
>
> 6.子类的构造方法面试题
> AAAA extends BBBB类演示[10Min ]55 CodeBlockDetail04.java

7. 静态代码块只能直接调用静态成员(静态属性和静态方法)，普通代码块可以调
   用任意成员。

#### 10.8设计模式

##### **饿汉式单例设计模式**

1)构造器私有化=》防止直接new

2)类的内部创建对象

3)向外暴露一个静态的公共方法。getlnstance

4)代码实现

```java
//饿汉式设计模式
class Girlfriend{

    private String name;

    private Girlfriend(String name) {
        this.name = name;
    }

    private static Girlfriend gf = new Girlfriend("小红");

    public static Girlfriend getInstance(){
        return gf;
    }

    @Override
    public String toString() {
        return "Girlfriend{" +
                "name='" + name + '\'' +
                '}';
    }
}
```

##### **懒汉式单例设计模式**

```java
public class SingleTon02 {
    public static void main(String[] args) {
        //new Cat("大黄");
//        System.out.println(Cat.n1);
        Cat instance = Cat.getInstance();
        System.out.println(instance);

    }
}

//饿汉式设计模式
class Cat {
    private String name;
    private static Cat cat;
    public static int n1;
//    1.构造器私有化
//    2.定义一个static静态属性对象
//    3.提供一个public的static方法，可以返回一个对象
    private Cat(String name) {
        System.out.println("构造器被调用");
        this.name = name;
    }

    public static Cat getInstance(){
        if (cat == null ){
            cat = new Cat("小可啊");
        }
        return cat;
    }

    @Override
    public String toString() {
        return "Girlfriend{" +
                "name='" + name + '\'' +
                '}';
    }
}
```

##### **区别**

* 饿汉式VS懒汉式
  1. 二者最主要的区别在于创建对象的时机不同:饿汉式是在类加载就创建了对象实例,而懒汉式是在使用时才创建
  2. 饿汉式不存在线程安全问题，懒汉式存在线程安全问题。(后面学习线程后，会完善一把)
  3. 饿汉式存在浪费资源的可能。因为如果程序员一个对象实例都没有使用，那么饿汉式创建的对象就浪费了，懒汉式是使用时才创建，就不存在这个问题。
  4. 在我们`javaSE`标准类中，`java.lang.Runtime`就是经典的单例模式。

##### **小结**

1. 单例模式的两种实现方式(1)饿汉式(2)懒汉式
2. 饿汉式的问题:在类加载时候就创建，可能存在资源浪费问题
3. 懒汉式的问题:线程安全问题，后面我们学了线程后，在进行完善

#### 10.9final关键字 3.20

* 基本介绍
  final中文意思:最后的，最终的.
  final可以修饰类、属性、方法和局部变量.
  在某些情况下,程序员可能有以下需求，就会使用到final:

  > 1)当不希望类被继承时,可以用final修饰.
  > 2)当不希望父类的某个方法被子类覆盖/重写(override)时,可以用final关键字修饰。
  > 3)当不希望类的的某个属性的值被修改,可以用final修饰.
  > 4)当不希望某个局部变量被修改，可以使用final修饰

* final使用注意事项和细节讨论

  > 1) final修饰的属性又叫常量,一般用XX XX_ XX来命名
  > 2) final修饰的属性在定义时,必须赋初值并且以后不能再修改,赋值可以在如下位置之一【选择一个位置赋初值即可】:
  > ①定义时:如public final double TAX_RATE=0.08;
  >
  > ②在构造器中
  >
  > ③在代码块中。
  >
  > 3)如果final修饰的属性是静态的，则初始化的位置只能是①定义时②在静态代码块不能在构造器中赋值。
  > 4) final类不能继承,但是可以实例化对象。
  > 5)如果类不是final类，但是含有final方法，则该方法虽然不能重写，但是可以被继承。
  >
  > 5)一般来说，如果一个类已经是final类了，就没有必要再将方法修饰成final方法。
  >
  > 6) final不能修饰构造方法(即构造器)
  > 7) final和static往往搭配使用，效率更高，不会导致类加载.底层编译器做了优化处理。
  >
  > 8)包装类(Integer,Double,Float,Boolean.都是final),String也是final类。

#### 10.10抽象类

* 抽象类的介绍

  1. 用abstract关键字来修饰一个类时,这个类就叫抽象类

     ```java
     访问修饰符 abstract 类名{
     }
     ```

     

  2. 用abstract关键字来修饰一个方法时,这个方法就是抽象方法

     ```java
     访问修饰符 abstract 返回类型方法名(参数列表);//没有方法体
     ```

  3. 抽象类的价值更多作用是在于设计,是设计者设计好后，让子类继承并实现

     ```java
     抽象类()
     ```

  4. 抽象类,是考官比较爱问的知识点,在框架和设计模式使用较多

**细节**

1. 抽象类不能被实例化
2. 抽象类不一定要包含abstract方法。也就是说,抽象类可以没有abstract方法[举例]
3. 一旦类包含了abstract方法,则这个类必须声明为abstract[说明]
4. abstract只能修饰类和方法,不能修饰属性和其它的。[说明]
5. 抽象类可以有任意成员【抽象类本质还是类】，比如:非抽象方法、构造器、静态属性等等[举例]
6. 抽象方法不能有主体,即不能实现
7. 如果一个类继承了抽象类，则它必须实现抽象类的所有抽象方法，除非它自己也声明为abstract类。
8. 抽象方法不能使用private、final 和 static来修饰，因为这些关键字都是和重写相违背的。

**练习**

>1)题1，思考: abstract final class A能编译通过吗, why?错误, final是不能继承
>
>2)题2，思考: abstract public static void test2();能编译通过吗, why?错误，static关键健字和方法重写无关.
>
>3)题3，思考: abstract private void test3();能编译通过吗, why?错误，private的方法不能重写

#### 10.11接口

* 基本介绍
  接口就是给出一些没有实现的方法,封装到一起,到某个类要使用的时候,在根据具体情况把这些方法写出来。语法:

  ```java
  interface接口名{
      //属性
      //方法(1.抽象方法2默认实现方法3.静态方法)
  }
  class类名 implements 接口{
  	自己属性;
  	自己方法;
  	必须实现的接口的抽象方法
  }
  ```

  

==小结:==

1. 在Jdk7.0前接口里的所有方法都没有方法体，即都是抽象方法。

2. Jdk8.0后接口可以有静态方法，默认方法，也就是说接口中可以有方法的具体实现

  **注意事项**

1. 接口不能被实例化
2. 接口中所有的方法是public方法,接口中抽象方法，可以不用abstract修饰 图示:
3. 一个普通类实现接口,就必须将该接口的所有方法都实现。
4. 抽象类实现接口，可以不用实现接口的方法。
5. 一个类同时可以实现多个接口[举例]
6. 接口中的属性,只能是final的，而且是 public static final修饰符。比如:`int a=1;实际上是 public static final int a=1;`(必须初始化)
7. 接口中属性的访问形式:接口名.属性名
8. 一个接口不能继承其它的类,但是可以继承多个别的接口[举例]
   `interface A extends B,C{}`
9. 接口的修饰符只能是public 和默认，这点和类的修饰符是一样的。

**接口和继承类区别**

继承直接使用，接口实现学习。

**实现接口vs继承类**

* 接口和继承解决的问题不同
  继承的价值主要在于:解决代码的==复用性和可维护性==。
  接口的价值主要在于:设计，设计好各种规范(方法)，让其它类去实现这些方法。即更加的灵活.

* 接口比继承更加灵活
  接口比继承更加灵活,继承是满足is- a的关系，而接口只需满足 like - a的关系

* 接口在一定程度上实现代码解耦[即:接口规范性+动态绑定]
* 小结:当子类继承了父类,就自动的拥有父类的功能
  如果子类需要扩展功能，可以通过实现接口的方式扩展。可以理解实现接口是 对java单继承机制的一种补充.

**接口的多态性**

接口类型的变量可以指向，实现了该接口的类的对象实例。

1. 多态参数(前面案例体现)

   在前面的Usb接口案例，Usb usb，既可以接收手机对象，又可以接收相机对象，就体现了接口多态(接口引用可以指向实现了接口的类的对象)

2. 多态数组 

3. 接口存在多态传递现象.

**总结**

![](E:\刷题\java\image\10-59.jpg)

#### 10.12内部类

**基本介绍**

一个类的内部又完整的嵌套了另一个类结构。被嵌套的类称为内部类(inner class),嵌套其他类的类称为外部类(outer class)。是我们类的第五大成员【思考:类的五大成员是哪些?[属性、方法、构造器、代码块、内部类]】，内部类最大的特点就是可以直接访问私有属性,并且可以体现类与类之间的包含关系
,●基本语法

```java
class Outer{1/外部类
	class Inner{ 1/内部类
    }
}
class Other{M/外部其他类
}
```

**分类**

>定义在外部类局部位置上(比如方法内):
>
>​	1)局部内部类（有类名)
>
>​	2)匿名内部类(没有类名，重点!!!!!!!!)
>
>定义在外部类的成员位置上:
>
>​	1)成员内部类（没用static修饰)
>
>​	2)静态内部类(使用static修饰)



##### **局部内部类的使用**

**说明:局部内部类是定义在外部类的局部位置，比如方法中，并且有类名。**

1. 可以直接访问外部类的所有成员，包含私有的
2. 不能添加访问修饰符,因为它的地位就是一个局部变量。局部变量是不能使用修饰符的。但是可以使用final修饰，因为局部变量也可以使用final
3. 作用域:仅仅在定义它的方法或代码块中。
4. 局部内部类---访问---->外部类的成员[访问方式:直接访问]
5. 外部类---访问---->局部内部类的成员
   访问方式:创建对象，再访问(注意:必须在作用域内)

**记住：**

1. 局部内部类是定义在方法中/代码块中
2. 作用域在方法体或者代码块中
3. 本质仍然是一个类
4. 外部其他类---不能访问----->局部内部类（因为局部内部类地位是一个局部变量)
5. 如果外部类和局部内部类的成员重名时，默认遵循就近原则,如果想访问外部类的成员，则可以使用(外部类名.this.成员)去访问
   `System.out.println("外部类的n2="+外部类名.this.n2)`;

**解释：**`外部类名.this`本质是外部类的对象

##### 匿名内部类的使用

(1)本质是类(2)内部类(3)该类没有名字(4)同时还是一个对象
说明:匿名内部类是定义在外部类的局部位置,比如方法中,并且没有类名

1. 匿名内部类的基本语法

```java
new类或接口(参数列表){
	类体
};
```



  ```java
类名.getClass() 查看运行类型的类名
  ```

**基于接口的匿名内部类**

1. 需求:想使用IA接口，并创建对象
2. 传统方式，是写一个类，实现该接口，并创建对象
3. 老韩需求是 Tiger/Dog类只是使用一次，后面再不使用
4. 可以使用匿名内部类来简化开发
5.  tiger的编译类型? IA
6. tiger的运行类型?就是匿名内部类`Outer04$1`
7. `jdk`底层在创建匿名内部类Outer04\$1,立即马上就创建了`Outer04$1`实例，并且把地址l返回给tiger
8. 匿名内部类使用一次，就不能再使用

```java
/*
我们看底层会分配类名Outer04$1
class outer04$1 implements IA{
    @Override
    public void cry() {
    	System.out.printLn("老虎叫唤...");
	}
}*/
```

##### **基于类的匿名内部类**

2. 匿名内部类的语法比较奇特，请大家注意，因为匿名内部类既是一个类的定义
   同时它本身也是一个对象，因此从语法上看，它既有定义类的特征，也有创建对象的特征，对前面代码分析可以看出这个特点,因此可以调用匿名内部类方法。

```java
new A(){
    @Override
    public void cry() {
    	System.out.print1n("he1lo~");
    }
}.cry();

A a = new A();
    @override
    public void cry( {
    	System.out.print1n("he1lo~");
    }
};
a.cry();
```

3. 可以直接访问外部类的所有成员，包含私有的
4. 不能添加访问修饰符,因为它的地位就是一个局部变量。
5. 作用域:仅仅在定义它的方法或代码块中。
6. 匿名内部类---访问---->外部类成员[访问方式:直接访问]
7. 外部其他类---不能访问----->匿名内部类（因为匿名内部类地位是一个局部变量)
8. 如果外部类和匿名内部类的成员重名时，匿名内部类访问的话，默认遵循就近原则,如果想访问外部类的成员，则可以使用(外部类名.this.成员)去访问

##### **成员内部类**

说明:成员内部类是定义在外部类的成员位置，并且没有static修饰。

1. 可以直接访问外部类的所有成员，包含私有的

```java
class Outer01{//外部类
private int n1 = 10;
public String name =“张三";
class lnntero1{
public void say(){
    System.out.printIn("Outer01的n1= "+ n1 + " outer01的name = " + name );
}
```

2. 可以添加任意访问修饰符(public、protected、默认、private),因为它的地位就是一个成员。

3. 作用域MemberlnnerClass01.java和外部类的其他成员一样，为整个类体比如前面案例，在外部类的成员方法中创建成员内部类对象,再调用方法.
4. 成员内部类---访问---->外部类(比如:属性)[访问方式:直接访问]
5. 外部类---访问------>内部类(说明)访问方式:创建对象,再访问
6. 外部其他类---访问---->成员内部类
7. 如果外部类和内部类的成员重名时，内部类访问的话，默认遵循就近原则，如果想访问外部类的成员,则可以使用(外部类名.this.成员)去访问

##### 静态内部类

说明:静态内部类是定义在外部类的成员位置，并且有static修饰

1. 可以直接访问外部类的所有静态成员，包含私有的，但不能直接访问非静态成员
2. 可以添加任意访问修饰符(public.protected、默认、private),因为它的地位就是一个成员。
3. 作用域:同其他的成员，为整个类体
4. 静态内部类---访问---->外部类(比如:静态属性)[访问方式:直接访问所有静态成员]
5. 外部类---访问------>静态内部类访问方式:创建对象，再访问
6. 外部其他类---访问----->静态内部类
7. 如果外部类和静态内部类的成员重名时，静态内部类访问的时，默认遵循就近原则，如果想访问外部类的成员，则可以使用（外部类名.成员)去访问

**这里:小结**

1. 内部类有四种==局部内部类,匿名内部类，成员内部类,静态内部类==

2. 重点还是掌握匿名内部类使用 

   ```java
   new 类/接口(参数列表){
   	//.….
   };
   ```

3. 成员内部类,静态内部类是放在外部类的成员位置，本质就是一个成员.

4. 其他细节看笔记...

### 第11章 枚举和注解(P425 - P443)   3.21

#### 11.1枚举

##### 注意事项

1. 当我们使用enum 关键字开发一个枚举类时，默认会继承Enum类,而且是一个final类[如何证明],老师使用javap工具来演示
2. 传统的`public static final Season2 SPRING = new Season2("春天","温暖“")`;简化成 SPRING("春天","温暖")，这里必须知道，它调用的是哪个构造器.
3. 如果使用无参构造器创建枚举对象，则实参列表和小括号都可以省略
4. 当有多个枚举对象时，使用,间隔，最后有一个分号结尾
5. 枚举对象必须放在枚举类的行首.

##### 常用方法

1. `toString:Enum`类已经重写过了，返回的是当前对象名,子类可以重写该方法,用于返回对象的属性信息
2. name:返回当前对象名(常量名),子类中不能重写
3. ordinal:返回当前对象的位置号，默认从O开始

4. values:返回当前枚举类中所有的常量
5. valueOf:将字符串转换成枚举对象,，要求字符串必须为已有的常量名，否则报异常!
6. `compareTo`: 比较两个枚举常量,比较的就是编号!

##### 实现接口

1. 使用enum关键字后，就不能再继承其它类了，因为enum会隐式继承Enum,而Java是单继承机制。
2. 枚举类和普通类一样,可以实现接口，如下形式。
   enum类名implements接口1，接口2{}



#### 11.2注解

##### 理解

1. 注解(Annotation)也被称为元数据(Metadata),用于修饰解释包、类、方法、属性、构造器、局部变量等数据信息.。
2. 和注释一样,注解不影响程序逻辑,但注解可以被编译或运行，相当于嵌入在代码中的补充信息。
3. `在JavaSE`中,注解的使用目的比较简单，例如标记过时的功能，忽略警告等。在`JavaEE`中注解占据了更重要的角色,例如用来配置应用程序的任何切面,代替`java EE`旧版中所遗留的繁冗代码和XML配置等。

**Override使用说明**

1. @Override表示指定重写父类的方法(从编译层面验证)，如果父类没有fly方法，则会报错
2. 如果不写@Override注解,而父类仍有`public void fly(){}`，仍然构成重写
3. @Override只能修饰方法,不能修饰其它类,包,属性等等
4. 查看@Override注解源码为@Target(ElementType.METHOD),说明只能修饰方法
5. @Target是修饰注解的注解，称为元注解

`@SuppressWarnings({unused})`抑制警告

**SuppressWarnings注解的案例>说明各种值**

1. unchecked是忽略没有检查的警告
2. rawtypes是忽略没有指定泛型的警告(传参时没有指定泛型的警告错误)
3. unused是忽略没有使用某个变量的警告错误
4. @SuppressWarnings可以修饰的程序元素为,查看@Target生成@SupperssWarnings时，不用背，直接点击左侧的黄色提示，就可以选择(注意可以指定生成的位置)

##### 源注解

**JDK的元Annotation 用于修饰其他Annotation**
元注解:本身作用不大，讲这个原因希望同学们，看源码时，可以知道他是干什么.

* 元注解的种类(使用不多，了解,不用深入研究)
  1. Retention//指定注解的作用范围,三种SOURCE,CLASS,RUNTIME
  2. Target//指定注解可以在哪些地方使用
  3. Documented//指定该注解是否会在javadoc体现
  4.  Inherited //子类会继承父类注解

### 第12章 异常(P444 - P459)

将该代码块->选中->快捷键`ctrl+alt+t`->选择`try-catch`。

#### 12.1基本概念

Java语言中，将程序执行中发生的不正常情况称为“异常”。(开发过程中的语法错误和逻辑错误不是异常)

* 执行过程中所发生的异常事件可分为两大类
  1. Error(错误):Java虚拟机无法解决的严重问题。如:JVM系统内部错误、资源耗尽等严重情况。比如: StackOverflowError[栈溢出]和OOM(out of memory) Error是严重错误,程序会崩溃。
  2. Exception:其它因编程错误或偶然的外在因素导致的一般性问题，可以使用针对性的代码进行处理。例如空指针访问，试图读取不存在的文件，网络连接中断等等， Exception 分为两大类:==运行时异常==[程序运行时，发生的异常]和==编译时异常==[编程时，编译器检查出的异常]。

**异常体系图小结**

1. 异常分为两大类，运行时异常和编译时异常.
2. 运行时异常，编译器不要求强制处置的异常。一般是指编程时的逻辑错误，是程序员应该避免其出现的异常。java.lang.RuntimeException类及它的子类都是运行时异常
3. 对于运行时异常，可以不作处理,因为这类异常很普遍，若全处理可能会对程序的可读性和运行效率产生影响
4. 编译时异常，是编译器要求必须处置的异常。

#### 12.2异常处理

异常处理就是当异常发生时，对异常处理的方式。

* 异常处理的方式
  1. try-catch-finally
     程序员在代码中捕获发生的异常,自行处理
  2. throws
     将发生的异常抛出,交给调用者(方法)来处理,最顶级的处理者就是`JVM`

**throws处理机制图**

1. try-catch-finally和throws二选一
2. 如果程序员没有显示处理异常，默认throws

![](E:\刷题\java\image\11-11.jpg)

**注意事项**

1. 如果异常发生了，则异常发生后面的代码不会执行，直接进入到catch块.
2. 如果异常没有发生，则顺序执行try的代码块，不会进入到catch.
3. 如果希望不管是否发生异常，都执行某段代码(比如关闭连接，释放资源等)则使用如下代码- finally {}
4. 可以有多个catch语句,捕获不同的异常(进行不同的业务处理)，要求父类异
   常在后，子类异常在前，比如(Exception在后，NullPointerException在前)，如果发生异常,只会匹配一个catch。
5. 可以进行try-finally 配合使用,这种用法==相当于没有捕获异常==，因此程序会直接崩掉/退出。应用场景，就是执行一段代码,不管是否发生异常，都必须执行某个业务逻辑

**小结**

1. 如果没有出现异常，则执行try块中所有语句，不执行catch块中语句，如果有finally，最后还需要执行finally里面的语句
2. 如果出现异常，则try块中异常发生后，try块剩下的语句不再执行。将执行catch块中的语句,如果有finally，最后还需要执行finally里面的语句!

#### 12.3throws异常处理

**基本介绍**

1. 如果一个方法(中的语句执行时)可能生成某种异常，但是并不能确定如何处理这种异常，则此方法应显示地声明抛出异常，表明该方法将不对这些异常进行处理,而由该方法的调用者负责处理。
2. 在方法声明中用throws语句可以声明抛出异常的列表,throws后面的异常类型可以是方法中产生的异常类型，也可以是它的父类。

**细节**

1. 对于编译异常，程序中必须处理,比如try-catch或者throws
2. 对于运行时异常，程序中如果没有处理，默认就是throws的方式处理
3. 子类重写父类的方法时，对抛出异常的规定:子类重写的方法，所抛出的异常类型要么和父类抛出的异常一致，要么为父类抛出的异常的类型的子类型
4. 在throws过程中，如果有方法 try-catch,就相当于处理异常，就可以不必throws

#### 12.4自定义异常

1. 定义类:自定义异常类名(程序员自己写)继承Exception或RuntimeException 
2. 如果继承Exception，属于编译异常
3. 如果继承RuntimeException，属于运行异常(一般来说，继承RuntimeException)

#### 12.5 throw和throws的区别

![](E:\刷题\java\image\12-4.jpg)

#### 12.6异常体系图

![](E:\刷题\java\image\12-5.jpg)

### 第13章 常用类(P460 - P498)

#### 13.1包装类

* 自动装箱底层调用的是`valueOf`方法，比如`Integer.valueOf()`
* 自动拆箱是`intValue()`;  三元运算符是一个整体

**Integer转为String：**`i.toString,String.valueOf(i)`

**String 转为Integer：**`Integer.parseInt(str),new Integer(str)`

**只要是基本数据类型"=="判断的就是值是否相等**

**`str.intern()`返回结果指向常量池的值**

#### 13.2 String类

![](E:\刷题\java\image\12-6.jpg)

![](E:\刷题\java\image\12-7.jpg)

* `String`是final类，不能被其他类继承
* `String`有属性`private final char value[]`;用于存放字符串内容
* 注意：`value`是一个`final`类型，不可以修改（**指向的地址不可以修改**）即`value`不能指向新的地址，但是单个字符内容可以变化。

```java
final[] char value = {'a','b','c'};
char v2 = {'b','c','d'};
value[0] = 'H';//正确
value = v2;//不可以修改value的地址
```

两种创建String对象的区别

方式一：直接复制 `String s = "hss"`;

方式二：调用构造器 `String s = new String("hsp")` ;

1. 方式一:先从常量池查看是否有"hsp”数据空间，如果有，直接指向;如果没有则重新创建,然后指向。s最终指向的是常量池的空间地址
2. 方式二:先在堆中创建空间，里面维护了value属性，指向常量池的hsp空间。如果常量池没有"hsp",重新创建，如果有，直接通过value指向。最终指向的是堆中的空间地址。
3. 画出两种方式的内存分布图

![](E:\刷题\java\image\13-2.jpg)



##### 13.2.1字符串特性

![](E:\刷题\java\image\13-3.jpg)

#### 13.3 StringBuffer类

##### **13.3.1基本介绍**

1. `java.lang.StringBuffer`代表可变的字符序列，可以对字符串内容进行增删。

2. 很多方法与String相同，但`StringBuffer`是可变长度的。

3. StringBuffer是一个容器。

   >1. StringBuffer的直接父类是AbstractStringBuilder
   >2. StringBuffer实现了 Serializable，即StringBuffer的对象可以串行化
   >3. 在父类中`AbstractStringBuilder`有属性 char[] value,不是`final`该value 数组存放字符串内容，引出存放在堆中的
   >4. `StringBuffer`是一个 final类，不能被继承

##### 13.2.2 String 对比 StringBuffer

![](E:\刷题\java\image\13-6.jpg)

```bash
//5.因为StringBuffer字符内容是存在char[] value，所有在变化(增加/删除）
// 不用每次都更换地址(即不是每次创建新对象)，所以效率高于 String
```

#### 13.4 StringBuilder类

1. 一个可变的字符序列。此类提供一个与StringBuffer兼容的API，但不保证同步(StringBuilder 不是线程安全)。该类被设计用作 StringBuffer的一个简易替换，用在字符串缓冲区被单个线程使用的时候。如果可能，建议优先采用该类，因为在大多数实现中，它比 StringBuffer 要快[后面测】。
2. 在 StringBuilder上的主要操作是append和 insert方法，可重载这些方法，以接受任意类型的数据。

#### 13.5三者比较

```bash
1) StringBuilder 和 StringBuffer非常类似,均代表可变的字符序列，而且方法
也一样
2) String:不可变字符序列,效率低,但是复用率高。
3) StringBuffer:可变字符序列、效率较高(增删)、线程安全,看源码
4)StringBuilder:可变字符序列、效率最高、线程不安全
5) String使用注意说明:
    string s="a";//创建了一个字符串
    S += "b";//实际上原来的"a"字符串对象已经丢弃了，现在又产生了一个字符串s+"b"(也就是"ab")。如果多次执行这  	  些改变串内容的操作,会导致大量副本字符串对象存留在内存中，降低效率。如果这样的操作放到循环中，会极大影响程序     的性能=>结论:如果我们对String 做大量修改，不要使用String
效率：StringBuilder>StringBuffer>String
```

**使用原则**

```bash
使用的原则,结论:
1．如果字符串存在大量的修改操作,一般使用StringBuffer或StringBuilder
2.如果字符串存在大量的修改操作,并在单线程的情况,使用 StringBuilder
3．如果字符串存在大量的修改操作，并在多线程的情况,使用 StringBuffer
4、如果我们字符串很少修改，被多个对象引用,使用String,比如配置信息等
StringBuilder的方法使用和StringBuffer一样,不再说.
```

#### 13.6 Arrays类

Arrays里面包含了一系列静态方法，用于管理或操作数组(比如排序和搜索).

1. `toString`返回数组的字符串形式`Arrays.toString(arr)`

2. sort 排序(自然排序和定制排序) `Integer arr[] ={1,-1,7,0,89];`
3. `binarySearch` 通过二分搜索法进行查找,要求必须排好序`int index = Arrays.binarySearch(arr,3);`

#### 13.7 System类

1. exit 退出当前程序

2. `arraycopy` :复制数组元素,比较适合底层调用，一般使用`Arrays.copyOf`完成复制数组.

   ```
   int[] src={1,2,33;
   int[] dest = new int[3];
   System.arraycopy(src, 0, dest, 0,3);
   ```

3.  `currentTimeMillens`:返回当前时间距离1970-1-1的毫秒数
4. ` gc`:运行垃圾回收机制`System.gc()`;

#### 13.8大数据机制

* Biglnteger和BigDecimal常见方法Biglnteger_.java BigDecimal_.java
  *  add加
  * subtract减3) multiply乘
  * divide除

* 应用场景:
  *  `Biglnteger`适合保存比较大的整型
  * `BigDecima`适合保存精度更高的浮点型(小数)

#### 13.9 Date

  **第三代日期类**

```
>前面两代日期类的不足分析
JDK 1.0中包含了一个java.util.Date类，但是它的大多数方法已经在JDK 1.1引入Calendar类之后被弃用了。而Calendar也存在问题是:
1)可变性:像日期和时间这样的类应该是不可变的。
2)偏移性:Date中的年份是从1900开始的,而月份都从0开始。
3)格式化:格式化只对Date有用, Calendar则不行。
4)此外，它们也不是线程安全的;不能处理闰秒等(每隔2天,多出1s)。
```

**第三代日期常见方法**

1. LocalDate(日期/年月日)、LocalTime(时间/时分秒)、LocalDateTime(日期时间/年月日时分秒)JDK8加入

* LocalDate只包含日期，可以获取日期字段

* LocalTime只包含时间，可以获取时间字段
  LocalDateTime包含日期+时间，可以获取日期和时间字段

  ```java
  //LocalDate.now()://LocalTime.nowSystem.out.println(ldt);
  LocalDateTime ldt = LocalDateTime.now();
  ldt.getYearO;ldt.getMonthValue();
  ldt.getMonth();
  ldt.getDayOfMonth();
  ldt.getHour();
  ldt.getMinute();
  ldt.getSecond();
  ```

  

2. DateTimeFormatter格式日期类
   类似于SimpleDateFormat

   ```java
   DateTimeFormat dtf = DateTimeFormatter.ofPattern(格式);
   String str = dtf.format(日期对象);
   
   LocalDateTime ldt = LocalDateTime.now();
   //关于DateTimeFormatter的各个格式参数，需要看jdk8的文档.
   DateTimeFormatter dtf = DateTimeFormatter.ofPattern("yyy年MM月dd日HH时mm分钟ss秒");
   String strDate = dtf.format(ldt);
   ```

### 第14章 集合(P499 - P553)

#### 14.1单列集合

![](E:\刷题\java\image\14-1.jpg)

#### 14.2双列集合

![](E:\刷题\java\image\14-2.jpg)

#### 14.3 Collection接口和常用方法

##### 14.3.1 Collection接口实现类的特点

`public interface Collection<E> extends Iterable<E>`

1. collection实现子类可以存放多个元素，每个元素可以是Object
2. 有些Collection的实现类,可以存放重复的元素，有些不可以
3. 有些Collection的实现类，有些是有序的(List)，有些不是有序(Set)
4. Collection接口没有直接的实现子类，是通过它的子接口Set 和 List来实现的



##### 14.3.2 Collection接口遍历元素方式1-使用Iterator（迭代器）

1. Iterator对象称为迭代器,主要用于遍历Collection集合中的元素。
2. 所有实现了Collection接口的集合类都有一个iterator()方法，用以返回一个实现了lterator接口的对象,即可以返回一个迭代器。
3. lterator的结构.
4.  Iterator仅用于遍历集合,Iterator本身并不存放对象。

##### 14.3.3 Iterator接口的方法

![](E:\刷题\java\image\14-5.jpg)

**执行原理**

![](E:\刷题\java\image\14-6.jpg)

#### 14.4 list接口

**List接口是Collection接口的子接口List .java**

1. List集合类中元素有序(即添加顺序和取出顺序一致)、且可重复[案例]
2.  List集合中的每个元素都有其对应的顺序索引，即支持索引。[案例]
3. List容器中的元素都对应一个整数型的序号记载其在容器中的位置,可以根据序号存取容器中的元素。
4. JDK API中List接口的实现类有:
   常用的有:ArrayList、LinkedList和Vector。

**ArrayList底层源码分析**

* ArrayList的底层操作机制源码分析(重点，难点.)ArrayListSource.java ，先说结论，在分析源码(示意图)
  1. ArrayList中维护了一个0bject类型的数组elementData. [debug看源码]
     transient Object[] elementData; ==//transient表示瞬间,短暂的,表示该属性不会被序列号==
  2. 当创建ArrayList对象时，如果使用的是无参构造器，则初始elementData容量为0，第1次添加，则扩容elementData为10，如需要再次扩容，则扩容elementData为1.5倍。
  3. 如果使用的是指定大小的构造器，则初始elementData容量为指定大小，如果需要扩容,
     则直接扩容elementData为1.5倍。

**Vector底层源码**

![](E:\刷题\java\image\14-9.jpg)

**Vector底层结构和ArrayList的比较**

![](E:\刷题\java\image\14-10.jpg)

**LinkedList底层结构**

1. LinkedList底层实现了双向==链表==和双端==队列==特点
2. 可以添加任意元素(元素可以重复)，包括null
3. 线程不安全，没有实现同步

* LinkedList的底层操作机制
  1. LinkedList底层维护了一个双向链表.
  2. LinkedList中维护了两个属性first和last分别指向首节点和尾节点
  3. 每个节点(Node对象)，里面又维护了prev、next、item三个属性，其中通过prev指向前一个，通过next指向后一个节点。最终实现双向链表.
  4. 所以LinkedList的元素的==添加和删除==，不是通过数组完成的，相对来说效率较高。
  5. 模拟一个简单的双向链表
     

![](E:\刷题\java\image\14-12.jpg)

**源码分析**

`remove`源码默认删除第一个节点

![](E:\刷题\java\image\14-13.jpg)

**ArrayList与LinkedList比较**

![](E:\刷题\java\image\14-14.jpg)

```bash
如何选择ArrayList和LinkedList:
1)如果我们改查的操作多，选择ArrayList
2)如果我们增删的操作多，选择LinkedList
3)一般来说，在程序中，80%-90%都是查询，因此大部分情况下会选择ArrayList4)在一个项目中，根据业务灵活选择，也可能这样，一个模块使用的是ArrayList,另外一个模块是LinkedList.
```

#### 14.5 set接口

##### 14.5.1基本介绍

```bash
1)无序(添加和取出的顺序不一致)，没有索引
2)不允许重复元素，所以最多包含一个null
3) JDK API中Set接口的实现类有:TreeSet、HashSet
```

##### 14.5.2遍历方式

同Collection的遍历方式一样,因为Set接口是Collection接口的子接口。

1. 可以使用迭代器
2. 增强for
3. 不能使用索引的方式来快取.

`hashSet`

1. HashSet实现了Set接口

2.  HashSet实际上是HashMap，看下源码.(图)

   ```java
   public Hashset( ) {
   map = new HashMap<>();
   ```

3. 可以存放null值，但是只能有一个null

4.  HashSet不保证元素是有序的,取决于hash后，再确定索引的结果.(即，不保证存放元素的顺序和取出顺序一致)

5. 不能有重复元素/对象.在前面Set接口使用已经讲过

==1。在执行add方法后，会返回一个boolean值==

==2。如果添加成功，返回true，否则返回false==

==3．可以通过remove 指定删除哪个对象==

#####  15.5.3 HashSet底层机制说明

```bash
1.HashSet底层是HashMap
2.添加一个元素时,先得到hash值-会转成->索引值
3.找到存储数据表table,看这个索引位置是否已经存放的有元素
4.如果没有，直接加入
5.如果有，调用equals 比较，如果相同，就放弃添加,如果不相同，则添加到最后
6.在Java8中,如果一条链表的元素个数超过TREEIFY_THRESHOLD(默认是8)，并且table的大小> = MIN TREEIFY CAPACITY(默认64),就会进行树化(红黑树)
```

![](E:\刷题\java\image\14-17.jpg)

##### 14.5.4 LinkedHashSet

1. LinkedHashSet是HashSet的子类
2.  LinkedHashSet底层是一个 LinkedHashMap，底层维护了一个数组+双向链表
3. LinkedHashSet根据元素的hashCode值来决定元素的存储位置,同时使用链表维护元素的次序(图)，这使得元素看起来是以插入顺序保存的。
4. LinkedHashSet 不允许添重复元素

**说明**

```bash
1)在LinkedHastSet中维护了一个hash表和双向链表(LinkedHashSet有head和tail )
2)每一个节点有pre 和next属性,这样可以形成双向链表
3)在添加一个元素时，先求hash值，在求索引,确定该元素在hashtable的位置,然后将添加的元素加入到双向链表(如果已经存在，不添加[原则和hashset一样])
tail.next = newElement//简单指定
newElement.pre = tail
tail = newEelment;
4)这样的话，我们遍历LinkedHashSet 也能确保插入顺序和遍历顺序一致
```

**底层机制示意图**

![](E:\刷题\java\image\14-19.jpg)

#### 14.6 Map接口

**特点**

```bash
注意:这里讲的是JDK8的Map接口特点 Map_java
1)Map与Collection并列存在。用于保存具有映射关系的数据:Key-Value
2) Map 中的key和 value 可以是任何引用类型的数据,会封装到HashMap$Node对象中
3) Map 中的key不允许重复，原因和HashSet一样,前面分析过源码.
4) Map 中的value可以重复
5) Map 的key可以为null, value 也可以为null,注意key 为null, 只能有一个,value为null ,可以多个.
6)常用String类作为Map的key
7) key和 value之间存在单向一对一关系，即通过指定的key 总能找到对应的value
8) Map存放数据的key-value示意图,一对k-v是放在一个HashMap$Node中的，有因为Node实现了 Entry 接口，有些书上也说一对k-v就是一个Entry(如图)

```

![](E:\刷题\java\image\14-20.jpg)

**遍历的四种方法**

```bash
1)containsKey:查找键是否存在
2) keySet:获取所有的键
3) entrySet:获取所有关系k-v
4) values:获取所有的值
```

##### 14.6.1 HashTable的基本介绍

```bash
1)存放的元素是键值对:即K-V
2) hashtable的键和值都不能为null
3) hashTable使用方法基本上和HashMap一样
4) hashTable是线程安全的，hashMap是线程不安全的
5)简单看下底层结构
```

##### 14.6.2 Properties类

```
1. Properties类继承自Hashtable类并且实现了Map接口，也是使用-种键值对的形式来保存数据。
2.他的使用特点和Hashtable类似
3. Properties 还可以用于从xox.properties文件中，加载数据到Properties类对象,并进行读取和修改
4.说明:工作后xxx.properties文件通常作为配置文件，这个知识点在IO流举例,有兴趣可先看文章
```

##### 14.6.3总结

```bash
1)先判断存储的类型(一组对象[单列]或一组键值对[双列])
2)一组对象[单列]: Collection接口
    允许重复:List
        增删多:LinkedList [底层维护了一个双向链表]
        改查多:ArrayList [底层维护Object类型的可变数组]
    不允许重复:Set
        无序: HashSet [底层是HashMap，维护了一个哈希表即(数组+链表+红黑树)]
        排序:TreeSet
        插入和取出顺序一致:LinkedHashSet,维护数组+双向链表
3)一组键值对:Map
    键无序: HashMap [底层是:哈希表 jdk7: 数组+链表,jdk8:数组+链表+红黑树]
    键排序:TreeMap
    键插入和取出顺序一致:LinkedHashMap
    读取文件Properties
```



##### 14.6.4 treeSet

##### 14.6.5 Collections工具类

```bash
1) reverse(List):反转 List中元素的顺序
2) shuffle(List):对List集合元素进行随机排序
3) sort(List):根据元素的自然顺序对指定List集合元素按升序排序
4) sort(List, Comparator):根据指定的Comparator产生的顺序对List集合元素进行排序
5) swap(List, int,int):将指定 list集合中的i处元素和j处元素进行交换
```

```java
Collections.sort(list, new Comparator()
@override
public int compare(Object o1,0bject o2){
    //可以加入校验代码
    return ((String) o2).length() - ((String) o1).length()
	}
});
```

**查找和替换**

```bash
1) Object max(Collection):根据元素的自然顺序，返回给定集合中的最大元素
2) Object max(Collection,Comparator):根据Comparator 指定的顺序,返回给定集合中的最大元素
3) Object min(Collection)
4) Object min(Collection,Comparator)
5) int frequency(Collection,Object):返回指定集合中指定元素的出现次数
6) void copy(List dest,List src):将src中的内容复制到dest中,deat大小需要先设定
7) boolean replaceAll(List list, Object oldVal, Object newVal)。使用用新值替换List 对象的所有旧值
8)应用案例演示

```



### 第15章 泛型(P554 - P568)

#### 15.1介绍

```bash
1)泛型又称参数化类型，是Jdk5.0出现的新特性,解决数据类型的安全性问题
2)在类声明或实例化时只要指定好需要的具体的类型即可。
3) Java泛型可以保证如果程序在编译时没有发出警告，运行时就不会产生ClassCastException异常。同时，代码更加简洁、健壮
4)泛型的作用是:可以在类声明时通过一个标识表示类中某个属性的类型,或者是某个方法的返回值的类型，或者是参数类型。

```

#### 15.2细节

```
1. interface List<T>0, public class HashSet<E>l..等等说明:TE只能是引用类型

2.在指定泛型具体类型后,可以传入该类型或者其子类类型

3.泛型使用形式
    List<lnteger> list1 = new ArrayList<lnteger>();
    List<lnteger> list2 = new ArrayList<>();

4.如果我们这样写List list3 = new ArrayList();默认给它的泛型是[<E>E就是Object ]即:Object

```

#### 15.3自定义泛型类

```bash
>基本语法
class类名<T, R..> {//表示可以有多个泛型
	成员
}
>注意细节
1)普通成员可以使用泛型(属性、方法)
2)使用泛型的数组，不能初始化（因为数组不能确定类型，不能再内存开辟空间）
3)静态方法中不能使用类的泛型（因为静态是和类相关的,在类加载加载时,对象还没有创建）
4)泛型类的类型，是在创建对象时确定的(因为创建对象时,需要指定确定类型)
5)如果在创建对象时,没有指定类型,默认为Object

```

#### 15.4接口泛型

```
>基本语法
	interface接口名<T,R.….>{}
>注意细节
    1)接口中，静态成员也不能使用泛型(这个和泛型类规定一样)
    2)泛型接口的类型,在继承接口或者实现接口时确定
    3)没有指定类型,默认为Object

```

#### 15.5自定义泛型方法

```
> 基本语法
   修饰符<T,R..>返回类型方法名(参数列表){}
> 注意细节
    1.泛型方法,可以定义在普通类中，也可以定义在泛型类中
    2.当泛型方法被调用时,类型会确定
    3. public void eat(Ee) 0,修饰符后没有<T,R..> eat
       方法不是泛型方法,而是使用了泛型
```

#### 15.6泛型的继承和通配符说明

```
1)泛型不具备继承性
List<Object> list = new ArrayList<String>0);//对吗?
2)<?>:支持任意泛型类型
3) <? extends A>:支持A类以及A类的子类,规定了泛型的上限
4)<? super A>:支持A类以及A类的父类,不限于直接父类，规定了泛型的下限
```



### 第17章 线程基础(P580 - P599)

#### 17.1线程介绍

```bash
1、线程是由进程创建的，是进程的一个实体。

3.并发:同一个时刻，多个任务交替执行，造成一种“貌似同时”的错觉，简单的说,，单核cpu实现的多任务就是并发。
4.并行:同一个时刻，多个任4同时执行。多核cpu可以实现并行。
```

#### 17.2线程使用

##### 17.1 继承Thread类

##### 17.2实现Rnnable接口

```bash
1. java是单继承的，在某些情况下一个类可能已经继承了某个父类,这时在用继承Thread类方法来创建线程显然不可能了。
2. java设计者们提供了另外一个方式创建线程,就是通过实现Runnable接口来创建线程。
```

**区别**

```bash
1. 从java的设计来看,通过继承Thread或者实现Runnable接口来创建线程本质上没有区别,从jdk帮助文档我们可以看到Thread类本身就实现了Runnable接口
2。实现Runnable接口方式更加适合多个线程共享一个资源的情况,并且避免了单继承的限制
```

```java
T3 t3 = new T3( "he1lo ");
Thread threado1 = new Thread(t3);
Thread thread02 = new Thread(t3);
threado1.start();
thread02.start();
system.out.print1n("主线程完毕");
```

#### 17.3线程方法

**常用方法第一组**

```bash
1. setName//设置线程名称，使之与参数name相同
2. getName //返回该线程的名称
3. start//使该线程开始执行;Java虚拟机底层调用该线程的start0方法
4. run//调用线程对象 run方法;
5. setPriority //更改线程的优先级
6. getPriority//获取线程的优先级
7. sleep1/在指定的毫秒数内让当前正在执行的线程休眠（暂停执行)
8. interrupt /中断线程
```

**注意事项**

```bash
1. start底层会创建新的线程，调用run, run 就是一个简单的方法调用，不会启动新线程
2. 线程优先级的范围
3. interrupt，中断线程，但并没有真正的结束线程。所以一般用于中断正在休眠线程
4. sleep:线程的静态方法,使当前线程休眠
```

**常用方法第二组**

![](E:\刷题\java\image\17-1.jpg)

**用户线程和守护线程**

1. 用户线程:也叫工作线程，当线程的任务执行完或通知方式结束

2. 守护线程:一般是为工作线程服务的，当所有的用户线程结束，守护线程自动结束
3. 常见的守护线程:**垃圾回收机制**


#### 17.4线程生命周期

![](E:\刷题\java\image\17-2.jpg)

![](E:\刷题\java\image\17-3.jpg)

#### 17.5 Synchronized

**线程同步机制**

1. 在多线程编程，一些敏感数据不允许被多个线程同时访问，此时就使用同步访问技术，保证数据在任何时刻，最多有一个线程访问，以保证数据的完整性。
2. 也可以这里理解:线程同步，**即当有一个线程在对内存进行操作时,其他线程都不可以对这个内存地址进行操作,**直到该线程完成操作，其他线程才能对该内存地址进行操作。

**同步具体方法-Synchronized**

1. 同步代码块

   ```java
   synchronized(对象){/得到对象的锁,才能操作同步代码
   	//需要被同步代码;
   }
   ```

2. synchronized还可以放在方法声明中，表示整个方法-为同步方法

   ```java
   public synchronized void m (String name){
   	//需要被同步的代码
   }
   ```

#### 17.6互斥锁

●基本介绍

1. Java在Java语言中，引入了对象互斥锁的概念，来保证共享数据操作的完整性。

2. 每个对象都对应于一个可称为“互斥锁”的标记，这个标记用米保证在任一时刻，只能有一个线程访问该对象。

3. 关键字synchronized来与对象的互斥锁联系。当某个对象用synchronized修饰时表明该对象在任一时刻只能由一个线程访问

4. 同步的局限性:导致程序的执行效率要降低

5. 同步方法（(非静态的）的锁可以是this,也可以是其他对象(要求是同一个对象)
6. 同步方法（静态的)的锁为当前类本身。

![](E:\刷题\java\image\17-4.jpg)

●注意事项和细节

1. 同步方法如果没有使用static修饰:默认锁对象为this

2. 如果方法使用static修饰,默认锁对象:当前类.class3.

3. 实现的落地步骤:

   * 需要先分析上锁的代码
   * 选择同步代码块或同步方法

   * 要求多个线程的锁对象为同一个即可!

#### 17.7死锁

**基本介绍**

* 多个线程都占用了对方的锁资源，但不肯相让，导致了死锁,在编程是一定要避免死锁的发生.

**下面操作会释放锁**

1. 当前线程的同步方法、同步代码块执行结束
   案例:上厕所，完事出来

2. 当前线程在同步代码块、同步方法中遇到break、return。
   案例:没有正常的完事，经理叫他修改bug,不得已出来

3. 当前线程在同步代码块、同步方法中出现了未处理的Error或Exception,导致异常结束
   案例:没有正常的完事,发现忘带纸，不得已出来

4. 当前线程在同步代码块、同步方法中执行了线程对象的wait()方法，当前线程暂停，并释
   放锁。
   案例:没有正常完事，觉得需要酝酿下，所以出来等会再进去

**下面操作不会释放锁**

1. 线程执行同步代码块或同步方法时，程序调用Thread.sleep()、Thread.yield()方
   法暂停当前线程的执行,不会释放锁
   案例:上厕所，太困了，在坑位上眯了一会

2. 线程执行同步代码块时，其他线程调用了该线程的suspend()方法将该线程挂起,
   该线程不会释放锁。
   提示:应尽量避免使用suspend()和resume()来控制线程，方法不再推荐使用

### 第19章 IO流(P611 - P644)

#### 19.1文件流

文件在程序中是以流的形式来操作的
![](E:\刷题\java\image\19-2.jpg)

流:数据在数据源(文件)和程序(内存)之间经历的路径

输入流:数据从数据源(文件)到程序(内存)的路径

输出流:数据从程序(内存)到数据源(文件)的路径

**常用的文件操作**

* 创建文件对象相关构造器和方法
  相关方法

```java
new File(String pathname)//根据路径构建一个File对象
new File(File parent,String child)//根据父目录文件+子路径构建
new File(String parent,String child)//根据父目录+子路径构建
```

* 获取文件的相关信息

  ```java
  #方法getName、getAbsolutePath、getParent、length、exists、isFile、isDirectory
  //先创建文件对象
  File file = new File( "e:l [news1.txt");
  /调用相应的方法，得到对应信息
  System.out.println("文件名字=" + file.getName();         
  ```

* 目录的操作和文件删除
  `mkdir`创建一级目录、`mkdirs`创建多级目录、`delete`删除空目录或文件

#### 19.2 IO流原理及流的分类

* Java IO流原理
  1. I/O是1nput/Output的缩写，I/O技术是非常实用的技术，用于处理数据传输.
     如读/写文件，网络通讯等。
  2. Java程序中，对于数据的输入/输出操作以”流(stream)”的方式进行。
  3. `java.io`包下提供了各种“流”类和接口，用以获取不同种类的数据，并通过方
     法输入或输出数据
  4. 输入input:读取外部数据(磁盘、光盘等存储设备的数据)到程序(内存)中。
  5. 输出output:将程序(内存)数据输出到磁盘、光盘等存储设备中

* 流的分类
  * 按操作数据单位不同分为:字节流(8 bit)二进制文件，字符流(按字符)文本文件
  * 按数据流的流向不同分为:输入流，输出流
  * 按流的角色的不同分为:节点流，处理流/包装流

![](E:\刷题\java\image\19-3.jpg)

* IO流体系图-常用的类

1. IO流体系图
2. 文件 VS 流

![](E:\刷题\java\image\19-1.png)

P615

#### 19.3Properties类

* 基本介绍
  1)专门用于读写配置文件的集合类
  	配置文件的格式:
  	键=值
  	键=值 
  2)注意:键值对不需要有空格，值不需要用引号一起来。默认类型是String

  3) Properties的常见方法

  * load:加载配置文件的键值对到Properties对象. 
  * list:将数 据显示到指定设备
  * getProperty(key):根据键获取值
  * setProperty(key,value):设置键值对到Properties对象
  *  store:将Properties中的键值对存储到配置文件,在idea中，保存信息到配置文件，如果含有中文，会存储为unicode码

  http://tool.chinaz.com/tools/unicode.aspx unicode码查询工具



![](E:\刷题\java\image\14-.jpg)

![](E:\刷题\java\image\14-.jpg)

## 第三阶段(P662 - P910)

### 第21章 网络编程(P662 - P684)

### 第22章 多用户即时通信系统(P685 - P710)

### 第23章 反射(P711 - P730)

#### 23.1反射机制

**Java Reflection**

1. 反射机制允许程序在执行期借助于`Reflection AP`取得任何类的内部信息(比如成员变量,构造器,成员方法等等),并能操作对象的属性及方法。反射在设计模式和框架底层都会用到

2. 加载完类之后，在堆中就产生了一个Class类型的对象（一个类只有一个Class对象)，这个对象包含了类的完整结构信息。通过这个对象得到类的结构。这个对象就像一面镜子，透过这个镜子看到类的结构，所以,形象的称之为:反射

![](E:\刷题\java\image\19-4.jpg)



**Java反射机制可以完成**

1. 在运行时判断任意一个对象所属的类

2. 在运行时构造任意一个类的对象

3. 在运行时得到任意一个类所具有的成员变量和方法

4. 在运行时调用任意一个对象的成员变量和方法

5. 生成动态代理

**反射相关的主要类:**

1. java.lang.Class:代表一个类,Class对象表示某个类加载后在堆中的对象

2. `java.lang.reflect.Method`:代表类的方法,Method对象表示某个类的方法

3. `java.lang.reflect.Fieid`:代表类的成员变量，Filed对象表示某个类的成员变量

4. `java.lang.reflect.Constructor`:代表类的构造方法，COnstructor对象表示

   这些类在`java.lang.reflection`

**反射优点和缺点**

1. 优点:可以动态的创建和使用对象(也是框架底层核心)，使用灵活，没有反射机制，框架技术就失去底层支撑。

2. 缺点:使用反射基本是解释执行,对执行速度有影响.

**反射调用优化-关闭访问检查**

1. Method和Field、Constructor对象都有setAccessible()方法
2. `setAccessible`作用是启动和禁用访问安全检查的开关
3. 参数值为`true`表示反射的对象在使用时取消访问检查，提高反射的效率。参数值为`false`则表示反射的对象执行访问检查

#### 23.2 Class类

**基本介绍**

1. Class也是类,因此也继承Object类[类图]

2. Class类对象不是new出来的，而是系统创建的[演示]
3. 对于某个类的Class类对象,在内存中只有一份，因为类只加载一次
4. 每个类的实例都会记得自己是由哪个Class 实例所生成
5. 通过Class可以完整地得到一个类的完整结构，通过一系列`API`
6. Class对象是存放在堆的
7. 类的字节码二进制数据，是放在方法区的，有的地方称为类的元数据(包括方法代码，变量名，方法名，访问权限等等)https://www.zhihu.com/question/38496907【示意图】

![](E:\刷题\java\image\19-5.jpg)

**常用方法**

![](E:\刷题\java\image\19-6.jpg)

**获取Class类对象方式**

`GetClass_.java`

1. 前提:已知一个类的全类名，且该类在类路径下，可通过Class类的静态方法`forName()`获取，可能抛出`ClassNotFoundException`， 实例: `Class cls1 =Class.forName( "java.lang.Cat”)`;

   ==应用场景:==多用于配置文件,读取类全路径，加载类.

2. 前提:若已知具体的类，通过类的class获取，该方式最为安全可靠,程序性能最高 实例: `Class cls2 = Cat.class`;
   ==应用场景:==多用于参数传递，比如通过反射得到对应构造器对象.

3. 前提:已知某个类的实例，调用该实例的`getClass()`方法获取`Class`对象，实例:
   `Class clazz =对象.getClass()`;//运行类型
   ==应用场景:==通过创建好的对象,获取`Class`对象

4. 其他方式
   `ClassLoader cl =对象.getClass().getClassLoader()`;

   `Class clazz4 = cl.loadClass(“类的全类名”)`;

5. 基本数据(int, char,boolean,float,double,byte,long,short)按如下方式得到Class类对象
        `Class cls =基本数据类型.class`
6. 基本数据类型对应的包装类,可以通过.type得到Class类对象
   `Class cls =包装类.TYPE`

**哪些类型有Class对象**
**如下类型有Class对象**

1. 外部类，成员内部类,静态内部类,局部内部类,匿名内部类

2. interface:接口
3. 数组
4. enum:枚举

5. annotation:注解
6. 基本数据类型
7. void

```java
Class<String> cls1 = String.class;//外部类
Class<Serializable> cls2 = Serializable.class;//接口
Class<Integer[]> cls3 = Integer[].class;//数组
class<float[][]> cls4 = float[][].class;//二维数组
class<Deprecated> cls5 = Deprecated.class;//注解//枚举
Class<Thread.State> cls6 = Thread.State.class;
Class<Long> cls7 = long.class;//
Class<Void> cls8 = void.class;
Class<class> cls9 = Class.class;

```

#### 23.3类加载

**基本说明**
`ClassLoad java com.hspedu.classload`
反射机制是java实现动态语言的关键，也就是通过反射实现类动态加载。

1. 静态加载:编译时加载相关的类，如果没有则报错，依赖性太强
2. 动态加载:运行时加载需要的类，如果运行时不用该类，则不报错，降低了依赖性
3. 举例说明

**类加载时机**

1. 当创建对象时(new)//静态加载

2. 当子类被加载时，父类也加载//静态加载

3. 调用类中的静态成员时//静态加载

4. 通过反射//动态加载

**类加载过程图**

![](E:\刷题\java\image\19-7.jpg)

**类加载各个阶段完成的任务**

![](E:\刷题\java\image\19-8.jpg)

**1.加载阶段**

JVM在该阶段的主要目的是将字节码从不同的数据源（可能是class文件、也可能是jar包，甚至网络)转化为二进制字节流加载到内存中，并生成一个代表该类的java.lang.Class对象

**2.1链接阶段-验证**

1. 目的是为了确保Class文件的字节流中包含的信息符合当前虚拟机的要求，并且不会危害虚拟机自身的安全

2. 包括:文件格式验证(是否以魔数`oxcafebabe`开头)、元数据验证、字节码验证和符号引用验证

3. 可以考虑使用`-Xverify:none`参数来关闭大部分的类验证措施，缩短虚拟机类加载的时间。

**2.2连接阶段-准备**

1. `JVM` 会在该阶段对静态变量,分配内存并默认初始化(对应数据类型的默认初始值，如0、OL、null、false 等)。这些变量所使用的内存都将在方法区中进行分配

**2.3连接阶段-解析**

1. 虚拟机将常量池内的符号引用替换为直接引用的过程。

**3. Initialization(初始化)**

1. 到初始化阶段，才真正开始执行类中定义的 Java程序代码，此阶段是执行<clinit>()方法的过程。

2. <clinit>()方法是由编译器按语句在源又件中现的顺序，依次自动收集静态变量的赋值动作和静态代码块中的语句,并进行合并。

3. 虚拟机会保证一个类的<clinit>()方法在多线程环境中被正确地加锁、同步，如果多个线程同时去初始化一个类，那么只会有一个线程去执行这个类的<clinit>()方法，其他线程都需要阻塞等待，直到活动线程执行<clinit>()方法完毕

**通过反射获取类的结构信息**
第一组: `java.lang.Class`类
`com.hspedu.reflection ReflectionUtils.java`

```bash
getName:获取全类名
getSimpleName:获取简单类名
getFields:获取所有public修饰的属性，包含本类以及父类的
getDeclaredFields:获取本类中所有属性
getMethods:获取所有public修饰的方法，包含本类以及父类的
getDeclaredMethods:获取本类中所有方法(包括私有的)
getConstructors: 获取所有public修饰的构造器，包含本类及父类的
getDeclaredConstructors:获取本类中所有构造器
getPackage:以Package形式返回包信息
getSuperClass:以Class形式返回父类信息
getlnterfaces:以Class[]形式返回接口信息
getAnnotations:以Annotation[]形式返回注解信息
```

第二组:` java.lang.reflect.Field `类

1. `getModifiers:` 以int形式返回修饰符
[说明:默认修饰符是0，public是1,private是2，protected是4,static是8，final是16]， public(1) + static (8) =9

2. `getType:`以Class形式返回类型
3. `getName:`返回属性名

第三组:` java.lang.reflect.Method`类

1. `getModifiers:`以int形式返回修饰符

   [说明:默认修饰符是0，public是1，private是2, protected是4,static是8, final是16]

2. `getReturnTyPe:`以class形式获取返回类型

3. ` getName:`返回方法名

4. `getParameterTypes`以Class[]返回参数类型数组

**通过反射创建对象**

1. 方式一:调用类中的public修饰的无参构造器

2. 方式二:调用类中的指定构造器

3. Class类相关方法

```java
newInstance:调用类中的无参构造器,获取对应类的对象
getConstructor(Class...clazz):根据参数列表，获取对应的public构造器对象
getDecalaredConstructor(Class..clazz):根据参数列表，获取对应的构造器对象
```

4. Constructor类相关方法

    ```java
    setAccessible:暴破
    newlnstance(Object...obj):调用构造器
    ```

**通过反射访问类中的成员**

* 访问属性 `ReflecAccessProperty.java`

1. 根据属性名获取Field对象

```java
Field f = clazz对象.getDeclaredField(属性名);
```

2. 暴破:`f.setAccessible(true);`//f 是Field属性

3. 访问

```java
f.set(o,值);//o表示对象
syso(f.get(o))://o表示对象
//静态
f.set(null,值)
f.get(null)
```

4. 注意:如果是静态属性(使用`getDeclareFiled`进行获取)，对属性进行爆破，可以操作私有属性，或者set和get中的参数o，可以写成null，因为是static属性。

**通过反射访问类中的成员**

* 访问方法

1. 根据方法名和参数列表获取Method方法对象:`Method m=clazz.getDeclaredMethod`(==方法名==，==XX.class==);

2. 获取对象:`Object o=clazz.newlnstance()`;

3. 暴破:`m.setAccessible(true)`;    

4. 访问:`Object returnValue = m.invoke(o,实参列表)`;

5. 注意:如果是静态方法，则`invoke`的参数o，可以写成null。

**homework01**

```java
 public static void main(String[] args) throws Exception {
        //1.得到 PrivateTestClass对象
        Class<PrivateTest> privateTestClass = PrivateTest.class;
        //创建对象实例
        PrivateTest privateTestObj = privateTestClass.newInstance();
        //3.得到name属性
        Field name = privateTestClass.getDeclaredField("name");//name私有的
        //4.爆破
        name.setAccessible(true);
        name.set(privateTestObj,"天龙八部");
        //5.得到getName对象
        Method getName = privateTestClass.getMethod("getName");
        //6.调用getName
        Object invoke = getName.invoke(privateTestObj);
        System.out.println("name属性值="+invoke);

    }
}

class PrivateTest{
    private String name = "helloKitty";

    public String getName(){
        return name;
    }
```

**02**

```java
public static void main(String[] args) throws Exception {
        //1.得到 File类的对象
        Class<?> fileClass = Class.forName("java.io.File");
        //得到构造器
        Constructor<?>[] constructors = fileClass.getConstructors();
        //输出
        for (Constructor<?> constructor : constructors) {
            System.out.println(constructor);
        }

        //3.单独的得到
        Constructor<?> declaredConstructor = fileClass.getDeclaredConstructor(String.class);
        String filePath = "e:\\test.txt";
        Object file = declaredConstructor.newInstance(filePath);//创建file对象

        //4.得到createNewFile的方法对象
        Method createNewFile = fileClass.getMethod("createNewFile");
        createNewFile.invoke(file);

        //file的运行类型就是file
        System.out.println(file.getClass());
    }
```

### 第24章 零基础学MySQL(P731 - P820)

### 第25章 JDBC和数据库连接池(P821 - P857)

#### 25.1` jdbc`原理

![](E:\刷题\java\image\25-1.jpg)

**JDBC程序编写步骤**

1. 注册驱动-加载Driver 类

2. 获取连接-得到Connection
3. 执行增删改查-发送SQL给mysql执行

4. 释放资源-关闭相关连接

**ResultSet [结果集]**

●基本介绍

1. 表示数据库结果集的数据表，通常通过执行查询数据库的语句生成

2. ResultSet对象保持一个光标指向其当前的数据行。最初，光标位于第一行之前
3. next方法将光标移动到下一行，并且由于在ResultSet对象中没有更多行时返回false,因此可以在while循环中使用循环来遍历结果集

**Statement**

* 基本介绍

1. Statement对象用于执行静态SQL语句并返回其生成的结果的对象

2. 在连接建立后，需要对数据库进行访问，执行命名或是SQL语句，可以通过·

     Statement[存在SQL注入]

     ==PreparedStatement==[预处理]

     CallableStatement[存储过程]

3. Statement对象执行SQL语句,存在SQL注入风险
4. SQL注入是利用某些系统没有对用户输入的数据进行充分的检查，而在用户输入数据中注入非法的SQL语句段或命令,恶意攻击数据库。
5. 要防范SQL 注入，只要用PreparedStatement(从Statement扩展而来)取代Statement就可以了

**PreparedStatement**

1. PreparedStatement 执行的SQL语句中的参数用问号(?)来表示，调用
   PreparedStatement对象的setXxx()方法来设置这些参数. setXxx()方法有两个参数，第一个参数是要设置的SQL语句中的参数的索引(从1开始)，第二个是设置的SQL语句中的参数的值
2. 调用`executeQuery()`，返回ResultSet 对象
3. 调用`executeUpdate()`:执行更新,包括增、删、修改

预处理好处

1. 不再使用+拼接sql语句，减少语法错误
2. 有效的解决了sql注入问题!
3. 大大减少了编译次数,效率较高

**小结**

#### 25.2 事务

* 基本介绍

1. JDBC程序中当一个Connection对象创建时，默认情况下是自动提交事务:每次执行一个SQL语句时，如果执行成功，就会向数据库自动提交，而不能回滚

2. JDBC程序中为了让多个SQL语句作为一个整体执行，需要==使用事务==
3. 调用Connection 的 setAutoCommit(false)可以取消自动提交事务
4. 在所有的SQL语句都成功执行后，调用Connection的commit();方法提交事务
5. 在其中某个操作失败或出现异常时，调用rollback();方法回滚事务

#### 25.3批处理

* 基本介绍
  1. 当需要成批插入或者更新记录时。可以采用Java的批量更新机制，这一机制允许多条语句一次性提交给数据库批量处理。通常情况下比单独提交处理更有效率。
  2. JDBC的批量处理语句包括下面方法:
     addBatch():添加需要批量处理的SQL语句或参数executeBatch():执行批量处理语句;clearBatch():清空批处理包的语句
  3. JDBC连接MySQL时，如果要使用批处理功能,请再url中加参数?rewriteBatchedStatements=true
  4. 批处理往往和PreparedStatement一起搭配使用，可以既减少编译次数,又减少运行次数,效率大大提高

1. 注意:需要修改配置
   `文件 jdbc.propertiesurl=jdbc:mysql://localhost:3306/数据库?rewriteBatchedStatements=true`

#### 25.4数据库连接池

* 传统获取Connection问题分析
  1. 传统的JDBC数据库连接使用DriverManager 来获取，每次向数据库建立连接的时候都要将Connection 加载到内存中，再验证IP地址，用户名和密码(0.05s ~1s时间)。需要数据库连接的时候，就向数据库要求一个，频繁的进行数据库连接操作将占用很多的系统资源，容易造成服务器崩溃。
  2. 每一次数据库连接，使用完后都得断开，如果程序出现异常而未能关闭，将导致数据库内存泄漏，最终将导致重启数据库。
  3. 传统获取连接的方式，不能控制创建的连接数量，如连接过多，也可能导致==内存泄漏==，MySQL崩溃。
  4. 解决传统开发中的数据库连接问题,可以采用数据库连接池技术(connection pool)。

* 数据库连接池基本介绍
  1. 预先在缓冲池中放入一定数量的连接,当需要建立数据库连接时，只需从“缓冲池”中取出一个，使用完毕之后再放回去。
  2. 安据库连接池负责分配、管理和释放数据库连接,它允许应用程序==重复使用==一个现有的数据库连接，而不是重新建立一个。
  3. 当应用程序向连接池请求的连接数超过最大连接数量时，这些请求将被加入到等待队列中

* 连接池示意图

![](E:\刷题\java\image\25-2.jpg)

* 数据库连接池种类

1. JDBC的数据库连接池使用javax.sql.DataSource 来表示,DataSource只是一个接口，该接口通常由第三方提供实现

2. ==C3PO==数据库连接池，速度相对较慢，稳定性不错(hibernate, spring)
3. DBCP数据库连接池，速度相对c3p0较快,但不稳定
4. Proxool数据库连接池，有监控连接池状态的功能，稳定性较c3p0差一点
5.  BoneCP数据库连接池,速度快
6. Druid(德鲁伊)是阿里提供的数据库连接池,集DBCP、C3PO、Proxool优点于一身的数据库连接池

```java
//配置文件必须放在src下
public void testC3P0() throws SQLException {
        ComboPooledDataSource jdbc = new ComboPooledDataSource("mysql");
        Connection connection = jdbc.getConnection();
        System.out.println("链接ok");
        connection.close();
    } 
public void testDruid() throws Exception {
        //1加入Druid jar包
        //2加入配置文件druid.properties ，将该文件拷贝项目的src目录
        //3创建Properties对象，读取配置文件
        Properties properties = new Properties();
        properties.load(new FileInputStream("src\\druid.properties"));
        DataSource dataSource = DruidDataSourceFactory.createDataSource(properties);
        Connection connection = dataSource.getConnection();
        System.out.println("链接成功");
        connection.close();
    }
```

#### 25.4 Apache-DButils

* 基本介绍

   1 .commons-dbutils 是Apache组织提供的一个开源 JDBC工具类库，它是对JDBC的封装,使用dbutils能极大简化jdbc编码的工作量[真的]。

DbUtils类

1. QueryRunner类:该类封装了SQL的执行，是线程安全的。可以实现增、删、改、查、批处理

2. 使用QueryRunner类实现查询

3. ResultSetHandler接口:该接口用于处理java.sql.ResultSet,将数据按要求转换为另一种形式

   ```java
    ArrayHandler:把结果集中的第一行数据转成对象数组。
    ArrayListHandler:把结果集中的每一行数据都转成一个数组，再存放到List中。
    BeanHandler:将结果集中的第一行数据封装到一个对应的JavaBean实例中。
    BeanListHandler: 将结果集中的每一行数据都封装到一个对应的JavaBean实例中，存放到List里。ColumnListHandler:将结果集中某一列的数据存放到List中。
    KeyedHandler(name):将结果集中的每行数据都封装到Map里，再把这些map再存到一个map里，其key为指定的key,MapHandler:将结果集中的第一行数据封装到一个Map里，key是列名，value就是对应的值。
    MapListHandler:将结果集中的每一行数据都封装到一个Map里，然后再存放到List
   ```

  

#### 25.5BasicDao

1. DAO :data access object数据访问对象
2这样的通用类，称为 BasicDao，是专门和数据库交互的，即完成对数据库(表)的crud操作。
3在BaiscDao 的基础上，实现一张表对应一个Da0，更好时完网功能，比1 CuStomer衣-
Customer.java类(javabean)-CustomerDao.java 

### 第27章 正则表达式(P878 - P904)

