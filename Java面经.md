# java面经

## **1、Java基础**

### 1、为什么重写equals还要重写hashcode

**总结来说就是两点**

**1.由于为了提高程序的执行效率才实现了hashcode方法，先进行hashcode比较，如果不同，就没有必要进行equals比较了，这样就大大的减少了equals的使用次数，从而效率得到提高**

**2.保证是同一个对象，如果重写了equals方法，而没有重写hashcode方***出现equals相等的对象，hashcode不相等的情况，重写hashcode方法就是为了避免这种情况的出现。**

### 2、说一下map的分类和常见的情况

它有四个实现类,分别是**HashMap Hashtable LinkedHashMap 和TreeMap.**

**Map**主要用于存储健值对，根据键得到值，因此不允许键重复(重复了覆盖了),但允许值重复。

**Hashmap** 是一个最常用的Map,它根据键的HashCode值存储数据,根据键可以直接获取它的值，

取得数据的顺序是完全随机的。HashMap最多只允许一条记录的键为Null;允许多条记录的值为 Null;HashMap不支持线程的同步，如果需要同步，可以用 Collections的synchronizedMap方法使HashMap具有同步的能力，或者使用ConcurrentHashMap。

**Hashtable**与 HashMap类似,它继承自Dictionary类，不同的是:它不允许记录的键或者值为空;它支持线程的同步，即任一时刻只有一个线程能写Hashtable,因此也导致了 Hashtable在写入时会比较慢。

**LinkedHashMap** 是HashMap的一个子类，保存了记录的插入顺序，在用Iterator遍历[LinkedHashMap](https://so.csdn.net/so/search?q=LinkedHashMap&spm=1001.2101.3001.7020)时，先得到的记录肯定是先插入的.也可以在构造时用带参数，按照应用次数排序。

**TreeMap**实现SortMap接口，能够把它保存的记录根据键排序,默认是按键值的升序排序，也可以指定排序的比较器，当用Iterator 遍历[TreeMap](https://so.csdn.net/so/search?q=TreeMap&spm=1001.2101.3001.7020)时，得到的记录是排过序的

### 3、Object若不重写hashCode()的话，hashCode()如何计算出来的？

如果不重写，用的是底层实现，返回的是当前对象的[内存](https://so.csdn.net/so/search?q=%E5%86%85%E5%AD%98&spm=1001.2101.3001.7020)地址。

### 4、==比较的是什么？

对于对象引用类型：“==”比较的是对象的[内存](https://so.csdn.net/so/search?q=%E5%86%85%E5%AD%98&spm=1001.2101.3001.7020)地址

```java
public class ArrayTest {

    public static void main(String[] args){

        String a = new String("aw");
        String b = new String("aw");
        System.out.println(a==b);//false
    }
}
```

显然，尽管 a 与 b 对象的值相同，但是在内存中的地址是不同的，即两个对象是不一样的。

### 5、若对一个类不重写，它的equals()方法是如何比较的？

如果没有对equals方法进行重写，则比较的是引用类型的变量所指向的对象的地址；

诸如String、Date等类对equals方法进行了重写的话，比较的是所指向的对象的内容。

### 6、java8新特性

- Lambda 表达式的本质：作为函数式接口的实例
- 函数式接口

### 7、说说Lamda表达式的优缺点。

1.  若不用并行计算，很多时候计算速度没有比传统的 for 循环快。（并行计算有时需要预热才显示出效率优势） 
2.  不容易调试。 

### 8、一个十进制的数在内存中是怎么存的？

补码的形式。

原反补码：
正数的原反补一样
负数的[反码](https://so.csdn.net/so/search?q=%E5%8F%8D%E7%A0%81&spm=1001.2101.3001.7020)是将原码除了符号位的其余位取反，补码是给反码加1.

### 9、为啥有时会出现4.0-3.6=0.40000001这种现象？

**这种舍入误差的主要原因是：**
**浮点数值采用二进制系统表示， 而在二进制系统中无法精确地表示分数 1/10。**

### 10、Java支持的数据类型有哪些？什么是自动拆装箱？

Java语言支持的8种基本数据类型是：
byte、short、int、long、float、double、boolean、char

自动拆装箱，是指基本数据类型和引用数据类型之间的自动转换

如Integer 和 int 可以自动转换； Float和float可以自动转换

### 11、什么是值传递和引用传递？

[值传递](https://so.csdn.net/so/search?q=%E5%80%BC%E4%BC%A0%E9%80%92&spm=1001.2101.3001.7020)是对基本型变量而言的,传递的是该变量的一个副本,改变副本不影响原变量.
[引用传递](https://so.csdn.net/so/search?q=%E5%BC%95%E7%94%A8%E4%BC%A0%E9%80%92&spm=1001.2101.3001.7020)一般是对于对象型变量而言的,传递的是该对象地址的一个副本, 并不是原对象本身 。

### 12、数组(Array)和列表(ArrayList)有什么区别？什么时候应该使用Array而不是ArrayList？

Array可以包含基本类型和对象类型，ArrayList只能包含对象类型。

Array大小是固定的，ArrayList的大小是动态变化的。

ArrayList提供了更多的方法和特性，比如：addAll()，removeAll()，iterator()等等。

对于基本类型数据，ArrayList 使用自动装箱来减少编码工作量；而当处理固定大小的基本数据类型的时候，这种方式相对比较慢，这时候应该使用Array。

### 13、你了解大O符号(big-O notation)么？你能给出不同数据结构的例子么？

大O符号表示一个程序运行时所需要的渐进时间复杂度上界。

### 14、String是最基本的数据类型吗?

NO

### 15、int 和 Integer 有什么区别

1.Integer是int的包装类，int则是java的一种基本的数据类型；

2.Integer变量必须实例化之后才能使用，而int变量不需要实例化；

3.Integer实际是对象的引用，当new一个Integer时，实际上生成一个指针指向对象，而int则直接存储数值

4.Integer的默认值是null，而int的默认值是0。

### 16、String 和StringBuffer的区别

StringBuffer对象的内容可以修改；而String对象一旦产生后就不可以被修改，重新赋值其实是两个对象。

### 17、我们在web应用开发过程中经常遇到输出某种编码的字符，如iso8859-1等，如何输出一个某种编码的字符串？

```java
public static String translate(String str){
        String tempStr = "";
        try{
            tempStr = new String(str.getBytes("ISO-8859-1"), "GBK");
            tempStr = tempStr.trim();
        }catch (Exception e){
            System.err.println(e.getMessage());
        }
        return tempStr;
    }
```

### 18、&和&&的区别？

&：不管前面的条件是否正确，后面都执行。

&&：前面条件正确时，才执行后面，不正确时，就不执行，就效率而言，这个更好。

### 19、简述正则表达式及其用途。

在编写处理字符串的程序时，经常会有查找符合某些复杂规则的字符串的需要。正则表达式就是用于描述这些规则的工具。换句话说，正则表达式就是记录文本规则的代码。

### 23、Java中是如何支持正则表达式操作的？

Java中的String类提供了支持正则表达式操作的方法，包括：matches()、replaceAll()、replaceFirst()、split()。此外，Java中可以用Pattern类表示正则表达式对象，它提供了丰富的API进行各种正则表达式操作，

## 2、关键字

### 1、介绍一下Syncronized锁，如果用这个关键字修饰一个静态方法，锁住了什么？如果修饰成员方法，锁住了什么？

synchronized修饰静态方法以及同步代码块的synchronized (类.class)用法锁的是类，线程想要执行对应同步代码，需要获得类锁。
synchronized修饰成员方法，线程获取的是当前调用该方法的对象实例的对象锁。

### 2、介绍一下volatile？

[volatile](https://so.csdn.net/so/search?q=volatile&spm=1001.2101.3001.7020)是Java提供的轻量级的同步机制，比sync的开销要小

被volatile定义的变量,系统每次用到它时都是直接从主存中读取,而不是各个线程的工作[内存](https://so.csdn.net/so/search?q=%E5%86%85%E5%AD%98&spm=1001.2101.3001.7020)

volatile可以像[sync](https://so.csdn.net/so/search?q=sync&spm=1001.2101.3001.7020)一样保持变量在多线程环境中是实时可见的

### 3、锁有了解嘛，说一下Synchronized和lock

Synchronized是关键字，内置语言实现，Lock是接口。

Synchronized在线程发生异常时会自动释放锁，因此不会发生异常死锁。Lock异常时不会自动释放锁，所以需要在finally中实现释放锁。

Lock是可以中断锁，Synchronized是非中断锁，必须等待线程执行完成释放锁。

Lock可以使用读锁提高多线程读效率。

### 4、讲一讲Java里面的final关键字怎么用的？

被final修饰的类不能继承。被final修饰的方法不能重写。被final修饰的变量为常量，值不能改变。

## **3、面向对象**

### 1、wait方法底层原理

1、将当前线程封装成ObjectWaiter对象node；

2、通过ObjectMonitor::AddWaiter方法将node添加到_WaitSet列表中；

### 3、String为啥不可变？

第一：在Java程序中String类型是使用最多的，这就牵扯到大量的增删改查，每次增删改差之前其实jvm需要检查一下这个String对象的安全性，就是通过hashcode，当设计成不可变对象时候，就保证了每次增删改查的hashcode的唯一性，也就可以放心的操作。

第二：网络连接地址URL,文件路径path通常情况下都是以String类型保存, 假若String不是固定不变的,将会引起各种安全隐患。就好比我们的密码不能以String的类型保存，，如果你将密码以明文的形式保存成字符串，那么它将一直留在内存中，直到垃圾收集器把它清除。而由于字符串被放在字符串缓冲池中以方便重复使用，所以它就可能在内存中被保留很长时间，而这将导致安全隐患

第三：字符串值是被保留在常量池中的，也就是说假若字符串对象允许改变,那么将会导致各种逻辑错误

### 4、类和对象的区别

1，类是一个抽象的概念，它不存在于现实中的时间/空间里，类只是为所有的对象定义了抽象的属性与行为。就好像“Person（人）”这个类，它虽然可以包含很多个体，但它本身不存在于现实世界上。

2，对象是类的一个具体。它是一个实实在在存在的东西。

3，类是一个静态的概念，类本身不携带任何数据。当没有为类创建任何对象时，类本身不存在于内存空间中。

4，对象是一个动态的概念。每一个对象都存在着有别于其它对象的属于自己的独特的属性和行为。对象的属性可以随着它自己的行为而发生改变。

### 5、请列举你所知道的Object类的方法。

Clone():创建并返回对象的副本

equals():对于基本数据类型，比较的是两个对象的值是否相等，对于引用数据类型来说，比较的是两个对象的地址值是否相等(是否指向堆中的同一个地址块) 。

finalize():当垃圾搜集器确定不再有该对象的引用时，垃圾搜集器会进行资源的回收

getClass()：返回一个运行时候的类

hashCode():返回对象的哈希码值

notify():用于唤醒在等待监视器的单个线程

notifyAll():唤醒所有在等待监视器的所有线程

wait(): 使得当前的线程进行等待

wait(long time):导致当前的线程进行等待，直到另一个线程调用notify()或notifyAll()方法来唤醒，或者是等待的时间结束

### 6、重载和重写的区别？相同参数不同返回值能重载吗？

重写是针对父类和子类的概念，重载是针对一个类中的概念；相同参数不同返回值不可以重载，因为重载必须改变参数列表（否则，虚拟机怎么知道该调用哪一个方法）

### 7、”static”关键字是什么意思？Java中是否可以覆盖(override)一个private或者是static的方法？

1、static关键字表示静态的意思，用于修饰成员变量和成员函数。表示可以在没有类的实例的情况下，用类名.变量名或者类名.函数名，进行访问

2、都不能

覆盖，也就是我们常说的重写，是子类继承父类，且子类中的方法和父类中的方法，方法名相同，参数个数和类型相同，返回值相同。

private修饰的方法，不能被继承，所以也不存在重写（覆盖）

static修饰的方法，是静态方法，在编译时就和类名就行了绑定。而重写发生在运行时，动态绑定的。何况static方法，跟类的实例都不相关，所以概念上也适用。

### 8、String能继承吗？

在Java中，只要是被定义为final的类，也可以说是被final修饰的类，就是不能被继承的。

### 9、StringBuffer和StringBuilder有什么区别，底层实现上呢？

[StringBuffer](https://so.csdn.net/so/search?q=StringBuffer&spm=1001.2101.3001.7020)线程安全，StringBuilder线程不安全，
底层实现上的话，StringBuffer其实就是比StringBuilder多了Synchronized修饰符。

### 10、类加载机制，双亲委派模型，好处是什么？

虚拟机只有在两个类的类名相同且加载该类的加载器均相同的情况下才判定这是一个类。若不采用双亲委派机制，同一个类有可能被多个类加载器加载，这样该类会被识别为两个不同的类，相互赋值时会有问题。

双亲委派机制能保证多加载器加载某个类时，最终都是由一个加载器加载，确保最终加载结果相同。

### 11、静态变量存在哪?

jdk1.8之前，静态变量存放在方法区，1.8之后取消了方法区，静态变量在堆中

### 12、讲讲什么是泛型？

```
泛型：就是一种不确定的数据类型。
比如：ArrayList<E> E就是泛型。 这种不确定的数据类型需要在使用这个类的时候才能够确定出来。
泛型可以省略，如果省略，默认泛型是Object类型。
```

### 13、解释extends 和super 泛型限定符-上界不存下界不取

上界<? extend Fruit>

下界<? super Apple>

上界的list只能get，不能add（确切地说不能add出除null之外的对象，包括Object）

下界的list只能add，不能get

### 14、是否可以在static环境中访问非static变量？

**因为静态的成员属于类，随着类的加载而加载到静态方法区内存，当类加载时，此时不一定有实例创建，没有实例，就不可以访问非静态的成员。**

### 15、谈谈如何通过反射创建对象？

方法1：通过类对象调用newInstance()方法，例如：String.class.newInstance()

方法2：通过类对象的getConstructor()或getDeclaredConstructor()方法获得构造器（Constructor）对象并调用其newInstance()方法创建对象，例如：String.class.getConstructor(String.class).newInstance(“Hello”);

### 17、接口和抽象类的区别是什么？

相同点：
1、都不能被实例化。

2、接口的实现类和抽象类的子类只有全部实现了接口或者抽象类中的方法后才可以被实例化。

不同点：
1、接口只能定义抽象方法不能实现方法，抽象类既可以定义抽象方法，也可以实现方法。

2、单继承，多实现。接口可以实现多个，只能继承一个抽象类。

3、接口强调的是功能，抽象类强调的是所属关系。

4、接口中的所有成员变量 为public static final， 静态不可修改，当然必须初始化。接口中的所有方法都是public abstract 公开抽象的。而且不能有构造方法。抽象类就比较自由了，和普通的类差不多，可以有抽象方法也可以没有，可以有正常的方法，也可以没有。

### 18、Comparable和Comparator接口是干什么的？列出它们的区别。

comparable 是在集合内部定义的方法实现的排序，Comparator 是在集合外部实现的排序，所以，如想实现排序，就需要在集合外定义 Comparator 接口的方法或在集合内实现 Comparable 接口的方法。

### 19、面向对象的特征有哪些方面

面向对象的三大特征：1.继承 2.封装 3.多态性

（1）继承：就是保留父类的属性，开扩新的东西。通过子类可以实现继承，子类继承父类的所有状态和行为，同时添加自身的状态和行为。

（2）封装：就是类的私有化。将代码及处理数据绑定在一起的一种编程机制，该机制保证程序和数据不受外部干扰。

（3）多态：是允许将父对象设置成为和一个和多个它的子对象相等的技术。包括重载和重写。重载为编译时多态，重写是运行时多态。

### 20、final, finally, finalize的区别。

**1.简单区别：**
final用于声明属性，方法和类，分别表示属性不可交变，方法不可覆盖，类不可继承。
finally是异常处理语句结构的一部分，表示总是执行。
finalize是Object类的一个方法，在垃圾收集器执行的时候会调用被回收对象的此方法，供垃圾收集时的其他资源回收，例如关闭文件等。

### 21、Overload和Override的区别。Overloaded的方法是否可以改变返回值的类型?

重载Overload表示同一个类中可以有多个名称相同的方法，但这些方法的参数列表各不相同（即参数个数或类型不同）。

重写Override表示子类中的方法可以与父类中的某个方法的名称和参数完全相同，通过子类创建的实例对象调用这个方法时，将调用子类中的定义方法，这相当于把父类中定义的那个完全相同的方法给覆盖了，这也是面向对象编程的多态性的一种表现。

这时候假设该类中有两个名称和参数列表完全相同的方法，仅仅是返回
类型不同，java 就无法确定编程者倒底是想调用哪个方法了，因为它无法通过返回结果类型
来判断。

### 22、abstract class和interface有什么区别?

1.interface中不能有字段，而abstract class可以有;

2.interface中不能有public等修饰符，而abstract class 可以有。

3.interface 可以实现多继承

### 24、当一个对象被当作参数传递到一个方法后，此方法可改变这个对象的属性，并可返回变化后的结果，那么这里到底是值传递还是引用传递?

当一个对象实例作为一个参数被传递到方法中时，参数的值就是对该对象的引用。对象的属性可以在被调用过程中被改变，但对象的引用是永远不会改变的。

### 26、JAVA语言如何进行异常处理，关键字：throws,throw,try,catch,finally分别代表什么意义？在try块中可以抛出异常吗？

try用来指定一块预防所有异常的程序；

catch子句紧跟在try块后面，用来指定你想要捕获的异常的类型；

throw语句用来明确地抛出一个异常；

[throws](https://so.csdn.net/so/search?q=throws&spm=1001.2101.3001.7020)用来声明一个方法可能抛出的各种异常（当然声明异常时允许无病呻吟）；

finally为确保一段代码不管发生什么异常状况都要被执行；

### 27、内部类可以引用他包含类的成员吗？有没有什么限制？

完全可以。如果不是静态[内部类](https://so.csdn.net/so/search?q=%E5%86%85%E9%83%A8%E7%B1%BB&spm=1001.2101.3001.7020)，那没有什么限制！

静态内部类只能访问静态成员！！！！

### 28、两个对象值相同(x.equals(y) == true)，但却可有不同的hash code说法是否正确？

**第一种情况回答：**

答：假如这个类没有[重写](https://so.csdn.net/so/search?q=%E9%87%8D%E5%86%99&spm=1001.2101.3001.7020)equals方法，如果两个对象值相同(x.equals(y) == true)，那么那么它们的hashCode值一定要相同；

**第二种情况回答：**

答：但是如果重写[equals](https://so.csdn.net/so/search?q=equals&spm=1001.2101.3001.7020)方法，没有重写HashCode的方法，就会出现不相等的情况。

29、重载（Overload）和重写（Override）的区别。重载的方法能否根据返回类型进行区分？

方法重载 (Overload)  是  编译时的多态性，而方法重写 (Override)  是  运行时的多态性。
构造器（constructor）不能被继承，因此不能被重写，但可以被重载。
重载：
发生在同一个类中，方法名相同参数列表不同（参数类型不同、个数不同、顺序不同），与 方法返回值和访问修饰符无关，即重载的方法不能根据返回类型进行区分
重写：
发生在父子类中，方法名、参数列表必须相同，抛出的异常 小于等于 父类，访问修饰符 大于或等于 父类（里氏代换原则）；如果父类方法访问修饰符为 private 则子类中 就不是重写。

### 30、如何通过反射获取和设置对象私有字段的值？

```java
package cn.liangqinghai.reflect;

public class Beans1 {
    public Beans1(){
        System.out.println("无参构造调用");
    }
    public Beans1(String name){
        System.out.println("带参数构造函数"+name);
    }
    public String getName(){
        return "getName返回值";
    }
    /**
     * 设置私有属性，并没有设置setters和getters
     */
    private String userName = "username";
    private String adminName = "adminName";
}
```

/**
* 测试反射访问属性
*/
[@Test ](/Test ) 
public void testFields() {

```java
    try {
        Class<?> clazz = Class.forName("cn.liangqinghai.reflect.Beans1");

        //
        Beans1 bean = (Beans1) clazz.newInstance();

        Field[] fs = clazz.getDeclaredFields();

        for (Field field : fs) {
            // 要设置属性可达，不然会抛出IllegalAccessException异常
            field.setAccessible(true);

            // 打印初始值
            System.out.println("设置属性之前：" + field.getName() + "===" + field.get(bean));

            // 设置属性值，set(Object obj, Object value)
            // obj - 应该修改其字段的对象
            // value - 正被修改的 obj 的字段的新值（参考api）
            field.set(bean, "Liang");
            // 打印设置属性之后的值
            System.out.println("设置属性之后：" + field.getName() + "=" + field.get(bean));
        }

    } catch (Exception e) {
        e.printStackTrace();
    }

}
```

```java
无参构造调用
设置属性之前：userName===username
设置属性之后：userName=Liang
设置属性之前：adminName===adminName
设置属性之后：adminName=Liang
```

```
通过反射机制获取和设置类的私有属性就这样，
注意点：
1、属性Field要设置.setAccessible(true)，不然会报IllegalAccessException异常
2、Field.set(obj,value)中，第一个参数是当前对象(参考代码中的bean实例引用)
```

### 32、请问Query接口的list方法和iterate方法有什么区别？

1.返回的类型不一样，list返回List，iterate返回iterator

2.查询策略不同。获取数据的方式不一样，list会直接查询数据库，iterate会先到数据库中把id取出来，然后真正要遍历某个对象的时候先到缓存中找，如果找不到，以id为条件再发一条sql到数据库，这样如果缓存中没有数据，则查询数据库的次数为n+1

### 33、Java中的方法覆盖(Overriding)和方法重载(Overloading)是什么意思？

重写和重载的区别：

1、重写只能用于子类重写父类的方法，而重载用于同一类中的所有方法

2、重写的参数列表必须相同，重载的参数列表必须不同

3、重写要求返回值类型必须一致或是其子类，重载没有要求

4、重写对方法的访问权限和抛出异常有特殊的要求，而方法的重载没有这方面的限制

5、父类的方法只能被同一子类重写一次，而一个方法可以在所有类中被重载很多次

6、重写是运行时的多态，重载是编译时的多态

### 34、Java中，什么是构造函数？什么是构造函数重载？什么是复制构造函数？

构造函数的函数名和类名一致，默认的构造函数没有参数，没有返回值，构造函数的函数体内，没有内容。 构造函数的重载是函数名与类名相同，参数类型不同，参数不同。同样的作用也是为了初始化对象的。 Java中没有拷贝构造函数的概念！

### 35、hashCode()和equals()方法有什么联系？

equals() : 判断两个对象是否相等。
一般有两种使用情况：
（1）类没有覆盖equals()方法。则通过equals()比较该类的两个对象时，等价于通过“==”比较这两个对象。
（2）类覆盖了equals()方法。我们用equals()方法来两个对象的内容相等；若它们的内容相等，则返回true(即，认为这两个对象相等)，反之为false。

## **_*4、集合*_**

### 1、Map和ConcurrentHashMap的区别？

- HashMap是线程不安全的，当出现多线程操作时，会出现安全隐患；而ConcurrentHashMap是线程安全的。
- HashMap不支持并发操作，没有同步方法，ConcurrentHashMap支持并发操作，通过继承 ReentrantLock（JDK1.7重入锁）/CAS和synchronized(JDK1.8内置锁)来进行加锁（分段锁），每次需要加锁的操作锁住的是一个 segment，这样只要保证每个 Segment 是线程安全的，也就实现了全局的线程安全。

ConcurrentHashMap采用锁分段技术，将整个Hash桶进行了分段segment，也就是将这个大的数组分成了几个小的片段segment，而且每个小的片段segment上面都有锁存在，那么在插入元素的时候就需要先找到应该插入到哪一个片段segment，然后再在这个片段上面进行插入，而且这里还需要获取segment锁。

ConcurrentHashMap让锁的粒度更精细一些，并发性能更好。

### 2、hashMap内部具体如何实现的？

HashMap是使用**hash算法**,然后基于**数组+链表+红黑树**来实现的,或许还知道HashMap内部数组的初始长度为**16**,并且还能**自动扩容**.

put(key,value)的原理
首先我们调用put方法的时候,方法内部会调用hash(key)方法,计算出key的hash值h,然后通过HashMap的主干部分(数组tab)的长度length来进行位**与运算**(length-1)&h得出一个index=(length-1)&h值,然后直接根据index的值,将**Node**对象放入对应的tab[index]=Node即可

get(key)的原理

一般情况下,首先根据key值调用方法hash(key),通过与数组长度位**与运算**来计算出index值,然后直接返回tab[index].value即可.
但是当计算出的index处的**Node**对象是**链表**结构或**红黑树**时,应该怎么办呢,因为那里所有Node的index都是相同的.

### 3、如果hashMap的key是一个自定义的类，怎么办？

**如果hashMap的key是一个自定义的类，必须重写该类的hashcode()方法和equals（）方法**

HashMap中的比较key是这样的，先求出key的hashcode(),比较其值是否相等，若相等再比较equals(),若相等则认为他们是相等 的。若equals()不相等则认为他们不相等。如果只重写hashcode()不重写equals()方法，当比较equals()时只是看他们是否为 同一对象（即进行内存地址的比较）,所以必定要两个方法一起重写。HashMap用来判断key是否相等的方法，其实是调用了HashSet判断加入元素 是否相等。

### 4、ArrayList和LinkedList的区别，如果一直在list的尾部添加元素，用哪个效率高？

ArrayList采用数组实现的，查找元素的效率比[LinkedList](https://so.csdn.net/so/search?q=LinkedList&spm=1001.2101.3001.7020)高。

LinkedList采用双线[链表](https://so.csdn.net/so/search?q=%E9%93%BE%E8%A1%A8&spm=1001.2101.3001.7020)实现，插入和删除的效率比ArrayList要高。

当插入的数据一直是小于千万级的时候，大部分是LinkedList效率高，而当数据量大于千万级时，就会出现ArrayList的效率比较高了。

LinkedList每次添加元素的时候，会new一个Node对象来存新增加的元素，所以当数据量小的时候，这个时间并不明显，而ArrayList需要扩容，所以LinkedList的效率比较高，其中，如果ArrayList出现不需要扩容的时候，那么ArrayList的效率是比LinkedList要高的，当数据量很大的时候，new对象的时间大于扩容的时间，那么ArrayList的效率高过LinkedList。

### 6、ConcurrentHashMap锁加在了哪些地方？

Java7是由Segment数组实现的，一个Segment锁住几个HashEntry元素；

Java8是由synchronized锁住transient volatile **Node**<K,V>[] table 数组的一个元素(即头结点，锁粒度比Java7低)，还通过CAS(Unsafe对象)操作数据更新、插入等。

### **7、TreeMap底层，红黑树原理？**
1.8的TreeMap是通过红黑树实现的
平衡二叉树：一棵空树或者左右子树的高度差绝对值不超过1，并且左右两个子树都一个平衡二叉树。

### 8、concurrenthashmap有啥优势，1.7，1.8区别？
HashMap效率很高，但是其是线程不安全的；
HashTable线程安全，由于加入了synchronized,所以效率要低了很多；
**一、优势：**
1、不但[线程安全](https://so.csdn.net/so/search?q=%E7%BA%BF%E7%A8%8B%E5%AE%89%E5%85%A8&spm=1001.2101.3001.7020)，而且比HashTable效率高
2、把数据分区，分成16个部分，每一个部分添加同步锁，使其其他部分的数据使用不受限制，大大提高了效率。
3、题外话：还有一种解决线程安全和应用效率的方式，效率比直接同步锁高一些，使用**ReadWriteLock**，读写锁

### 9、ArrayList是否会越界？

1. 当我们调用arraylist.add (object temp)的时候**是不会出现数组越界的问题的**，但是我们调用arraylist.add (int index, object temp)的时候，就有可能出现数组越界。

### 10、什么是TreeMap?

1. TreeMap实现了红黑树的结构，形成了一颗二叉树。
2. TreeMap 是一个有序的key-value集合，它是通过红黑树实现的。
3. TreeMap 继承于AbstractMap，所以它是一个Map，即一个key-value集合。
4. TreeMap 实现了NavigableMap接口，意味着它支持一系列的导航方法。比如返回有序的key集合。
5. TreeMap 实现了Cloneable接口，意味着它能被克隆。
6. TreeMap 实现了java.io.Serializable接口，意味着它支持序列化。

### 11、ConcurrentHashMap的原理是什么？
1.**底层数据结构**

1. JDK1.7的ConcurrentHashMap底层采用：Segments数组+HashEntry数组+链表
2. JDK1.8的ConcurrentHashMap底层采用：Node数据+链表+红黑树
3. Hashtable底层数据结构采用：数组+链表

**2.实现线程安全的方式：**

1. 在JDK1.7中ConcurrentHashMap采用分段锁实现线程安全。
2. 在JDK1.8中ConcurrentHashMap采用synchronized和CAS来实现线程安全。
3. Hashtable采用synchronized来实现线程安全。在方法上加synchronized同步锁。

### 12、Java集合类框架的基本接口有哪些？
Collection：代表一组对象，每一个对象都是它的子元素
Set：不包括重复元素的Collection
List：有顺序的Collection，并且可以包含重复元素
Map：可以把键（key）映射到值（value）的对象，键不能重复

### 13、为什么集合类没有实现Cloneable和Serializable接口？
这个问题说的不清楚，集合类框架中的接口没有实现Cloneable和Serializable接口，但是具体的实现类是实现了这些接口的，比如Arraylist

### 14、什么是迭代器？
迭代器的作用是用来访问容器（用来保存元素的数据结构）中的元素，所以使用迭代器，我们就可以访问容器中里面的元素。没错！这和访问数组这个序列的指针一样，因为数组范围内的指针就是迭代器的一种。

### 15、Iterator和ListIterator的区别是什么？

1. **Iterator**代表迭代器，是Collection框架中的一个接口；用于遍历集合元素。它允许逐个迭代集合中的每个元素，从集合中获取元素或从集合中删除元素；但无法使用Iterator修改集合中的任何元素。
2. **ListIterator**是Collection框架中的一个接口；是用于扩展Iterator接口的。使用ListIterator，可以向前和向后遍历集合的元素。还可以添加、删除或修改集合中的任何元素。简而言之，我们可以说它消除了Iterator的缺点。

### 16、快速失败(fail-fast)和安全失败(fail-safe)的区别是什么？
fail-safe允许在[遍历](https://so.csdn.net/so/search?q=%E9%81%8D%E5%8E%86&spm=1001.2101.3001.7020)的过程中对容器中的数据进行修改，而fail-fast则不允许。

### 17、HashMap和Hashtable有什么区别？

- **线程安全性不同**。HashMap线程不安全；Hashtable 中的方法是Synchronize的。
- key、value是否允许null。HashMap的key和value都是可以是null，key只允许一个null；Hashtable的key和value都不可为null。
- hash的计算方式不同。HashMap计算了hash值；Hashtable使用了key的hashCode方法。
- 默认初始大小和扩容方式不同。HashMap默认初始大小16，容量必须是2的整数次幂，扩容时将容量变为原来的2倍；**Hashtable默认初始大小11**，扩容时将容量变为原来的2倍加1。

### 18、ArrayList和LinkedList有什么区别？

- ArrayList基于**动态数组**实现的非线程安全的集合；LinkedList基于链表实现的非线程安全的集合。
- 对于随机index访问的get和set方法，一般**ArrayList**的速度要优于**LinkedList**。因为ArrayList直接通过数组下标直接找到元素；**LinkedList**要移动指针遍历每个元素直到找到为止。
- 新增和删除元素，一般LinkedList的速度要优于ArrayList。因为ArrayList在新增和删除元素时，可能扩容和复制数组；LinkedList实例化对象需要时间外，只需要修改指针即可。

### 20、Collection 和 Collections的区别。
1、**java.util.Collection 是一个集合接口**。
List，Set，Queue接口都继承Collection。
2、**java.util.Collections 是一个包装类。**
大多数方法都是用来处理线性表的。此类不能实例化，**就像一个工具类，服务于Java的Collection框架**。

### 21、你所知道的集合类都有哪些？主要方法？
集合类 ：ArrayList 、LinkedList、 HashSet、 HashMap
方法：add(),remove(),put(),addAll(),removeAll(),contains()

### 22、List、Set、Map是否继承自Collection接口？
Set 和List 都继承了Conllection；Set具有与Collection完全一样的接口
 Map没有继承于Collection接口 从Map[集合](https://so.csdn.net/so/search?q=%E9%9B%86%E5%90%88&spm=1001.2101.3001.7020)中检索元素时，只要给出键对象，就会返回对应的值对象。 

### 23、List、Map、Set三个接口存取元素时，各有什么特点？
List与Set都是单列元素的[集合](https://so.csdn.net/so/search?q=%E9%9B%86%E5%90%88&spm=1001.2101.3001.7020)，它们有一个功**共同的父接口Collection**。
List 以特定索引来存取元素，可以有重复元素。
Set 不能存放重复元素（用对象的 [equals](https://so.csdn.net/so/search?q=equals&spm=1001.2101.3001.7020)()方法来区分元素是否重复）。
Map 保存键值对（key-value pair）映射， 映射关系可以是一对一或多对一。

## 5、线程

### 1、多线程中的i++线程安全吗？为什么？
不安全。因为i++不是[原子性](https://so.csdn.net/so/search?q=%E5%8E%9F%E5%AD%90%E6%80%A7&spm=1001.2101.3001.7020)操作。i++分为读取i值，对i值加1，再赋值给i++，
执行过程中任何一步都有可能被其他线程抢占。

### 2、如何线程安全的实现一个计数器？
```java
/**

 * 编写一个线程安全的计数器

 * 5个线程一起跑，输出线程和计数到1000

 * @author yadid

 *

 */

public class MySafeThread implements Runnable {

// 设置计数初值为0

private static AtomicInteger count = new AtomicInteger(0);

 

@Override

public void run() {

while (true) {

try {

Thread.sleep(1);

} catch (InterruptedException e) {

e.printStackTrace();

}

MySafeThread.calc();

}

}

private synchronized static void calc() {

if (count.get() < 1000) {

// 自增1，返回更新后的值

int c = count.incrementAndGet();

System.out.println("线程:" + Thread.currentThread().getName()+" :" + c);

}
}

 

public static void main(String[] args) {

for (int i = 0; i < 5; i++) {

MySafeThread myThread = new MySafeThread();

Thread t = new Thread(myThread);

t.start();
}
}
}

```
### 3、多线程同步的方法

多线程同步的方法一共有五个：

1. 使用synchronized 关键字构成同步方法。
2. 使用synchronized 关键字构成同步代码块。
3. 使用ReentrantLock类构成同步代码块。
4. 使用volatile关键字修饰变量。
5. 如果使用ThreadLocal对象管理变量。

Synchronized是java中提供的一个关键字。ReentrantLock是java5.0后提供的一个类，这个类是java.util.concurrent.locks包中的，具有lock和unlock两个重要的方法。

二者在性能上的区别是：
1，Synchronized可能出现死锁现象。
2，ReentrantLock具有lockInterruptibly方法，可以中断锁等候。若线程一获得了锁，线程1执行的内容又比较多，此时若线程2不想等待，就可以中断锁，可以优化性能。而且不会出现死锁现象。在线程间通讯时ReentrantLock提供了Condition实例对象，让等待唤醒机制操作更加灵活。

### 4、介绍一下生产者消费者模式？
一个模块负责生产，一个模块负责处理消费。他们共用一个储存空间，生产者想其中存数据，消费者从其中取数据。

   - 使用wait()和nitify()可以实现。
   - 使用阻塞队列实现


### 5、线程，进程，然后线程创建有很大开销，怎么优化？
 使用线程池，线程池维护了多个线程，当我们的程序需要用到线程时，就直接从其中获取，不用的是时候放回池中。使用线程池可以减低资源的消耗。可以提高响应的速度。可以方便线程的管理。可以提高线程的使用率。

### 6、讲一下AQS吧。
AQS其实就是一个可以给我们实现锁的框架
在LOCK包中的相关锁(常用的有ReentrantLock、 ReadWriteLock)都是基于AQS来构建，一般我们叫AQS为同步器。

### 7、创建线程的方法，哪个更好，为什么？
一共有3中创建线程的方式1.继承Thread类，重写run()方法。2.实现Runnable接口。3.使用线程池。

        使用Runnable更好，因为实现了Runnable，还需要用Thread类进行包装，才能使用start方法。而对象的包装实现了资源的共享。

 一个类可以实现多个接口，避免单继承带来的局限

### 8、Java中有几种方式启动一个线程？

- 继承Thread类，重写它的run类。然后实例化调用start()方法
- 实现Runnable接口，实现run方法。使用Thread包装该类。实例化、调用start()方法
- 使用线程池，使用execute把任务添加到其中

### 9、Java中有几种线程池？
 一共有5种线程池。
newCachedThreadPool():必要是创建新线程，空闲线程会被保留60秒

newFixedThreadPoll():该池包含固定数量的线程，空线程会被一直保留

newSingleThreadExecutor():只有一个线程的“池”，该线程顺序执行每一个提交的任务

newScheduledThreadPool():用于预定执行而构建的固定线程池，代替java.util.Timer;

newSingleThreadScheduledExecutor():用于预定执行的单线程“池”。

### 10、线程池有什么好处？
线程的创建需要很大的开销，会导致系统效率缓慢。使用是线程池可以直接从池中获取，减少了创建的开销。池也可以提供定时、定期、单线程并发数的管理。

### 11、cyclicbarrier和countdownlatch的区别
Cyclicbarrier类可以使用reset()可以重用。而CountDownLatch类，释放线程过后就不会再使用了。

Cyclicbarrier类中有getNumberWaiting()正处于等待状态的线程数。getParties()使栅栏打开还需要等待多少线程。等这些方法。而CountDownLatch类有获取计数值，和递减的方法

### 12、概括的解释下线程的几种可用状态。
线程的状态：

 New（新建）： 当使用new操作符创建一个线程时，那么这个线程就处于新建状态。但是还没有开始运行。

 Runnable（可运行）：当使用了start()方法线程处于runnable状态。一个可运行状态的线程可能运行可可能还没有运行，这取决于线程调度器是否给该线程分配资源。

 Blocked（被阻塞）：当一个线程试图获取一个对象锁，而该锁被其他线程锁持有，则该线程进入阻塞状态，当其他线程释放锁，并且线程调度器运行它持有的时候，该线程将会变成一个非阻塞状态。

 Waiting（等待）：当线程等待另一个线程通知调度器一个条件是，它自己进入等待状态，调用Object.wait()或者Thread.join()方法时。

Timed waiting（计时等待）：有一个方法有一个超时参数。调用他们导致线程进入计时等待状态。比如sleep方法。

Terminated（被终止）：两个原因一个是执行完run。第二个原因是在run中没有捕获一个异常导致线程意外死亡。

### 13、同步方法和同步代码块的区别是什么？
同步方法：是有 synchronize修饰的方法，他的锁就是当前类对象
同步代码块：是有synchronize修饰的代码块，默认为当前类对象，但是也可以放其他的类对象。

### 14、在监视器(Monitor)内部，是如何做线程同步的？程序应该做哪种级别的同步？
在jvm中，每一个对象都有一把锁，一旦被synchronize修饰，那么这部分就会被监视器监视，确保一次只有一个线程执行该部分的代码。

### 15、sleep() 和 wait() 有什么区别？
**sleep():**

- 让线程处于计时等待状态，到倒计时为0时就继续执行，这个过程它将不会释放锁。

- 它会主动让出cpu，并且他可以在任何地方使用。Thread.sleep().

- 属于Thread的方法

**wait():**

- 让线程处于等待状态，直到出现notify()，或者notifyAll()就会唤醒这个线程继续执行，这个过程他将会释放锁

- 它只能在synchronize方法或代码块中使用。

- 属于Object方法

### 16、同步和异步有何异同，在什么情况下分别使用他们？举例说明。
同步：当多个线程对相同的数据进行操作的时候，使用同步。
异步： 当应用程序在对象上调用了一个需要花费很长时间来执行的方法，并且不希望让程序等待方法的返回时，就应该使用异步编程，在很多情况下采用异步途径往往更有效率。

### 17、请说出你所知道的线程同步的方法

- 同步方法
- 同步代码块
- wait()和notify()
- volatile
- Lock
- 局部变量
- blockQueue

### 18、 stop()和suspend()方法为何不推荐使用？
 stop()：**该方法会终止所有未结束的方法，包括run()方法。当线程终止，它会立即释放被它锁住的所有对象的锁。** 例如当一个账户向另一个账户转账的时候，调用了stop()方法，钱已经转出了，但是另一个账户还没有收到钱。银行对象遭到的破坏。stop之所以被弃用，是因为无法知道什么时候终止线程时安全的。

suspend()：**挂起线程。这个方法不会破坏对象。但是如果用suspend挂起一个持有一个锁的线程，那么该锁在恢复之前是不可用的。如果调用suspend()方法的线程试图获得同一个锁，那么程序就会锁死：被挂起的线程等待恢复，而将其挂起的线程等待获得锁**。   假如有A，B两个线程，A线程在获得某个锁之后被suspend阻塞，这时A不能继续执行，线程B在获得相同的锁之后才能调用resume方法将A唤醒，但是此时的锁被A占有，B不能继续执行，也就不能及时的唤醒A，此时A，B两个线程都不能继续向下执行而形成了死锁。这就是suspend被弃用的原因。


### 19、线程的sleep()方法和yield()方法有什么区别？
**sleep()：**休眠方法，该方法可以使当前线程处理阻塞状态，是Thread类中的静态方法，并且它不会释放锁。可以让其他所有线程都有机会执行，无优先级之分。有 InterruptedException异常

 **yield()：**让步方法，它也是Thread中的静态方法，使用它可以让线程处于就绪状态。yield()只是让线程暂停一下，让调度器重新分配，只有优先级和当前线程相同，或者比之高的线程并且也处于就绪状态的， 可以获得执行的机会。yield没有声明异常。


### 20、当一个线程进入一个对象的synchronized方法A之后，其它线程是否可进入此对象的synchronized方法B？

不能。因为synchronize方法使用的是当前类对象。当一个线程进入A方法时，它还没有释放锁。必须等A方法释放锁了，B在有机会执行。

### 21、请说出与线程同步以及线程调度相关的方法。
wait(): 使线程处于等待状态，并且会释放锁

sleep()：时线程处于计时等待状态。并且不会释放锁，还可能抛出异常

notify():唤醒一个处于等待状态的线程。至于唤醒哪一个由jvm决定，并且与优先级无关 

notifyAll():唤醒全部处于等待状态的线程。


### 22、举例说明同步和异步

**同步**：当多个线程对同一个内存进行读写的时候，可能数据会被覆盖，所以就需要用到同步，同步的“同”并不是同时的意思，而是协同，协助、相互配合。你说完之后，我在说。你在调用这个方法的时候，我就不能调用。     

**异步**：比如你发送一个请求，不用等待我的回应，你就可以继续给我发


### 23、说说线程的基本状态以及状态之间的关系？
线程有五个状态:new创建状态，Runnable就绪状态，Running运行状态，Dead消亡状态，Blocked阻塞状态。创建线程通过start方法进入就绪状态，获取cpu的执行权进入运行状态，失去cpu执行权会回到就绪状态，运行状态完成进入消亡状态，运行状态通过sleep方法和wait方法进入阻塞状态，休眠结束或者通过notify方法或者notifyAll方法释放锁进入就绪状态


### 24、如何保证线程安全？
使用同步机制

## 6、锁

### 1、讲一下非公平锁和公平锁在reetrantlock里的实现。
如果一个锁是公平的，那么锁的获取顺序就应该符合请求的绝对时间顺序，FIFO。对于非公平锁，只要CAS设置同步状态成功，则表示当前线程获取了锁，而公平锁还需要判断当前节点是否有前驱节点，如果有，则表示有线程比当前线程更早请求获取锁，因此需要等待前驱线程获取并释放锁之后才能继续获取锁。

### 2、讲一下synchronized，可重入怎么实现
每个锁关联一个线程持有者和一个计数器。当计数器为0时表示该锁没有被任何线程持有，那么任何线程都都可能获得该锁而调用相应方法。当一个线程请求成功后，JVM会记下持有锁的线程，并将计数器计为1。此时其他线程请求该锁，则必须等待。而该持有锁的线程如果再次请求这个锁，就可以再次拿到这个锁，同时计数器会递增。当线程退出一个synchronized方法/块时，计数器会递减，如果计数器为0则释放该锁。


### 3、锁和同步的区别。
1.synchronized是关键字,Lock是接口;
2.synchronized是隐式的加锁,lock是显式的加锁;
3.synchronized可以作用于方法上,lock只能作用于方法块;
4.synchronized底层采用的是objectMonitor,lock采用的AQS;
5.synchronized是阻塞式加锁,lock是非阻塞式加锁支持可中断式加锁,支持超时时间的加锁;
6.synchronized在进行加锁解锁时,只有一个同步队列和一个等待队列, lock有一个同步队列,可以有多个等待队列;
7.synchronized只支持非公平锁,lock支持非公平锁和公平锁;
8.synchronized使用了object类的wait和notify进行等待和唤醒, lock使用了condition接口进行等待和唤醒(await和signal);
9.lock支持个性化定制, 使用了模板方法模式,可以自行实现lock方法;

### 4、什么是死锁(deadlock)？
[死锁](https://so.csdn.net/so/search?q=%E6%AD%BB%E9%94%81&spm=1001.2101.3001.7020)就是资源无法被释放。最简单的例子是：线程 A 占有一号锁，正在请求二号锁，且线程 B 占有二号锁，正在请求一号锁，A、B 线程互相等待对方释放锁，进入了无线等待的状态。

### 5、如何确保N个线程可以访问N个资源同时又不导致死锁？
使用多线程的时候，一种非常简单的避免死锁的方式就是：指定获取锁的顺序， 并强制线程按照指定的顺序获取锁。因此，如果所有的线程都是以同样的顺序加 锁和释放锁，就不会出现死锁了。
1. 加锁顺序（线程按照一定的顺序加锁）
2. 加锁时限（线程尝试获取锁的时候加上一定的时限，超过时限则放弃对该锁的请求，
   并释放自己占有的锁）
3. 死锁检测

### 6、请你简述synchronized和java.util.concurrent.locks.Lock的异同？
1.Lock能完成几乎所有synchronized的功能，并有一些后者不具备的功能，如锁投票、定时锁等候、可中断锁等候等

2.synchronized 是Java 语言层面的，是内置的关键字；Lock 则是JDK 5中出现的一个包，在使用时，synchronized 同步的代码块可以由JVM自动释放；Lock 需要程序员在finally块中手工释放，如果不释放，可能会引起难以预料的后果（在多线程环境中）。

## **7、JDK**

### 1、Java中的LongAdder和AtomicLong的区别
LongAdder在AtomicLong的基础上将单点的更新压力分散到各个节点，在低并发的时候通过对base的直接更新可以很好的保障和AtomicLong的性能基本保持一致，而在高并发的时候通过分散提高了性能。 缺点是LongAdder在统计的时候如果有并发更新，可能导致统计的数据有误差。

### 2、JDK和JRE的区别是什么？
JDK是提供给Java开发人员使用的，其中包含了java的开发工具，也包括了JRE。所以安装了JDK，就不用在单独安装JRE了。

## **8、反射**

### 1、反射的实现与作用

- 通过 Class 对象的 newInstance() 方法
- 通过 Constructor 对象的 newInstance() 方法


**1、获取类的成员变量的信息**

```java
Field[] fields = cls.getDeclaredFields();
```
| 方法 | 用途 |
| --- | --- |
| getField(String name) | 获得某个公有的属性对象 |
| getField() | 获得所有公有的属性对象 |
| getDeclaredField(String name) | 获得某个属性对象(public和非public) |
| getDeclaredFields() | 获得所有属性对象(public和非public) |


**2、获得类方法**
```java
Method[] methods = cls.getDeclaredMethods();
```

| 方法 | 用途 |
| --- | --- |
| getMethod(String name, Class.... <?> parameterTypes) | 获得该类某个公有的方法 |
| getMethods() | 获得该类所有公有的方法 |
| getDeclaredMethod(String name, Class.... <?> parameterTypes) | 获得该类某个方法(public和非public) |
| getDeclaredMethod() | 获得该类所有方法(public和非public) |


**3、获得构造函数**

```java
Constructor[] constructors = cls.getDeclaredConstructors();
```


| 方法 | 用途 |
| --- | --- |
| getConstructor(Class... <?> parameterTypes) | 获得该类中与参数类型匹配的公有构造方法 |
| getConstructor() | 获得该类的所有公有构造方法 |
| getDeclaredConstructor(Class... <?> parameterTypes) | 获得该类中与参数类型匹配的构造方法 |
| getDeclaredConstructor | 获得该类所有构造方法 |




| 类名 | 用途 |
| --- | --- |
| Class类 | 代表类的实体，在运行的Java应用程序中表示类和接口 |
| Field类 | 代表类的成员变量 (成员变量也称为类的属性) |
| Method | 代表类的方法 |
| Constructor类 | 代表类的构造方法 |



## **9、Spring**
### 1、说一下IOC和AOP?
IOC，即**控制反转**，把对象的创建、初始化、销毁交给 Spring 来管理，而不是由开发者控制，实现控制反转。IOC 思想基于 IOC 容器完成，IOC 容器底层就是**对象工厂**（BeanFactory 接口）。IOC的原理是基于xml解析、工厂设计模式、反射实现的。使用IOC可以降低代码的耦合度。


### 2、介绍一下bean的生命周期

1. **Spring启动，查找并加载需要被Spring管理的bean，进行Bean的实例化**
2. **Bean实例化后对将Bean的引入和值注入到Bean的属性中**
3. **如果Bean实现了BeanNameAware接口的话，Spring将Bean的Id传递给setBeanName()方法**
4. **如果Bean实现了BeanFactoryAware接口的话，Spring将调用setBeanFactory()方法，将BeanFactory容器实例传入**
5. **如果Bean实现了ApplicationContextAware接口的话，Spring将调用Bean的setApplicationContext()方法，将bean所在应用上下文引用传入进来**
6. **如果Bean实现了BeanPostProcessor接口，Spring就将调用他们的postProcessBeforeInitialization()方法。**
7. **如果Bean 实现了InitializingBean接口，Spring将调用他们的afterPropertiesSet()方法。类似的，如果bean使用init-method声明了初始化方法，该方法也会被调用**
8. **如果Bean 实现了BeanPostProcessor接口，Spring就将调用他们的postProcessAfterInitialization()方法。**
9. **此时，Bean已经准备就绪，可以被应用程序使用了。他们将一直驻留在应用上下文中，直到应用上下文被销毁。**
10. **如果bean实现了DisposableBean接口，Spring将调用它的destory()接口方法，同样，如果bean使用了destory-method 声明销毁方法，该方法也会被调用。**



### 3、Spring里面注解用过没有？autowired 和resource区别？
@Autowired注解是Spring提供的，而@Resource注解是J2EE本身提供的

@Autowird注解默认通过byType方式注入，而@Resource注解默认通过byName方式注入

```xml
<bean id="userServiceImpl" class="cn.com.bochy.service.impl.UserServiceImpl" autowire="byName">
</bean>  
<bean id="userDao" class="cn.com.bochy.dao.impl.UserDaoImpl"> </bean>
```
比如说如上这段代码，byName就是通过Bean的id或者name，byType就是按Bean的Class的类型。
```
若autowire="byType"意思是通过 class="cn.com.bochy.dao.impl.UserDaoImpl"来查找UserDaoImpl下所有的对象。
```
代码autowire="byName"意思是通过id="userDao"来查找Bean中的userDao对象


@Autowired注解注入的对象需要在IOC容器中存在，否则需要加上属性required=false，表示忽略当前要注入的bean，如果有直接注入，没有跳过，不会报错


### 4、@Controller和@RestController的区别？

- @RestController加在类上面的注解，使得类里面的每个方法都将json/xml返回数据加返回到前台页面中。

- @Controller加在类上面的注解，使得类里面的每个方法都返回一个试图页面。

- @Controller和@ResponseBody（加在方法/类上面）一起使用，和@RestController的作用相同。


### 5、依赖注入的方式有几种，哪几种？

1. **属性注入（Field Injection）；**
2. **Setter 注入（Setter Injection）；**
3. **构造方法注入（Constructor Injection）。**













