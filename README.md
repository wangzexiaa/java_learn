# 数据类型

## 类型转换

> **八种基本数据类型**：byte(1),short(2),int(4),long(8),float(4),double(8),boolean(1),char(2)
>
> 基本数据类型默认值
>
> | 数据类型     | 默认值 |
> | ------------ | ------ |
> | byte         | 0      |
> | short        | 0      |
> | int          | 0      |
> | long         | 0L     |
> | float        | 0.0F   |
> | double       | 0.0    |
> | boolean      | false  |
> | char         | \u0000 |
> | 引用数据类型 | null   |
>
> **八种数据类型大小排序**：byte<short(32767)<int(2147483647)<long<float<double
>
> ​												 char(虽然char和short占用的字节数相同，但是char可以取到更大的正整数)
>
> ==除了**boolean**类型外其他其中都可以进行类型转换==
>
> **小容量--->大容量** ==自动类型转换==
>
> **大容量--->小容量** ==强制类型转换==  需要加入强制类型转换符，虽然编译可以通过，但是运行可能会损失精度
>
> **注：**
>
> 1. **当整数字面值没有超过byte short char的取值范围，可以直接赋值**
>
>    ```java
>    long g=10;
>    byte h=(byte)(int)g/3;//虽然表达式右边的数值没有超过byte的范围，但是编译阶段过不去，因为编译阶段只看语法不做运					 //算，如果这里直接赋值一个3是可以编译通过的
>    ```
>
>    
>
> 2. **byte short char混合运算的时候，都先转换成int之后再进行运算**
>
> 3. **多种数据类型混合运算，先转成大容量数据类型再进行计算**
>
>    ==在一个域中变量名不能重名==
>
>    ```java
>    double dd=10/3; //10和3都是int，取整得3，之后自动类型转换成double得到3.0
>    dd=10.0/3;  	//3先转换成double,之后计算得到的就是double，结果为3.33333333
>    ```
>
>    ==0的ascii是48，a是97，A是65==												

# 运算符

## 算数运算符

## 关系运算符

> < = > 关系运算符的结果都是boolean类型

## 逻辑运算符

> & 逻辑与 	! 逻辑非	|逻辑或  ^逻辑异或(==两边算子不一样就是true==)     
>
> &&短路与     ||短路或    ==逻辑运算符要求两边都是boolean类型，并且最终结果也是boolean类型==
>
> ==&&和& 的区别==：运算结果相同，只不过短路与存在短路现象
>
> ```java
> int x=10;
> int y=8;
> System.out.println(x<y & ++x<y);//x<y即是false，所以后边并没有执行的必要
> System.out.println(x);   	    //x=11，说明&后边的语句执行了
> 
> ====================================================================
> int x=10;
> int y=8;
> System.out.println(x<y && ++x<y);//x<y即是false，所以后边并没有执行的必要
> System.out.println(x);   	    //x=10，说明&&后边的语句没有执行，直接短路了
> ```
>
> ==||和| 的区别==：运算结果相同，只不过短路或存在短路现象

## 赋值类运算符

> =   +=   *=   /=   %=

## 字符串连接运算符

> +

## 三元运算符

## 位运算符==之后讲==

# 控制语句

## switch

> **switch的语法结构**
>
> ```java
> switch(int或String类型的字面值或者变量){
>     case int或String类型的字面值或者变量:
> 		java语句；
>          break;  //如果这里的break没有，就会存在case穿透现象，也就是下一个case内容一定会执行
>     case int或String类型的字面值或者变量:
> 		java语句；
>          break;
> 	...
>     default:
> 		java语句;
> 		...
> }  
> ```
>
> **注意：**byte short char可以放在==switch和case==后边，因为存在自动类型转换 ==java6之前只能用int,String都不能用，switch也支持枚举==
>
> ```java
> //case可以合并
> int i=3;
> switch(i){
>     case 1:case 2:case 3:case 10:   	
>         System.out.println("Test Code!")
> }
> //java输入
> java.util.Scanner s=new java.util.Scanner(System.in);
> int num =s.nextInt();//next()是输入字符串
> =======================
> InputStreamRead is=new InputStreamRead(System.in);
> BufferedRead br=new BufferedRead(is);
> ```
>
> **swich的简单应用(简单计算器)**
>
> ```java
> public class SimpleComputer {
>     public static void main(String[] args) {
>         java.util.Scanner scanner=new java.util.Scanner(System.in);
>         System.out.println("欢迎使用简单计算器");
>         System.out.println("请输入你的第一个数字");
>         int a=scanner.nextInt();
>         System.out.println("请输入你的运算符");
>         String fuhao=scanner.next();
>         System.out.println("请输入你的第二个数字");
>         int b=scanner.nextInt();
>         switch (fuhao){
>             case "+":
>                 System.out.println(a+"+"+b+"="+(a+b));
>                 break;
>             case "-":
>                 System.out.println(a+"-"+b+"="+(a-b));
>                 break;
>             case "*":
>                 System.out.println(a+"*"+b+"="+(a*b));
>                 break;
>             case "/":
>                 System.out.println(a+"/"+b+"="+(a/b));
>                 break;
>             case "%":
>                 System.out.println(a+"%"+b+"="+(a%b));
>                 break;
>         }
>     }
> }
> ```

# **方法**

## 方法执行内存分析

> ==JVM==   ：栈     堆     方法区
>
> 栈内存主要存储==局部变量==

## 方法重载(overload)

> 1. 什么时候考虑使用方法重载？
>
>    功能相似
>
> 2. 什么条件满足之后构成方法重载？
>
>    - 在一个类中
>    - 方法名相同
>    - 参数列表不同
>      - 数量不同
>      - 顺序不同
>      - 类型不同
>
>    ```java
>    //方法重载的print应用
>    Class Test{
>        public static void main(String[] args){
>            U.p(1);
>            U.p(flase);
>            U.p("1");
>        }
>    }
>    Class U{
>        public static void p(byte b){
>            System.out.println(b);
>        }
>        public static void p(short b){
>            System.out.println(b);
>        }
>        public static void p(int b){
>            System.out.println(b);
>        }
>        public static void p(long b){
>            System.out.println(b);
>        }
>        public static void p(float b){
>            System.out.println(b);
>        }    
>        public static void p(double b){
>            System.out.println(b);
>        }
>        public static void p(boolean b){
>            System.out.println(b);
>        }
>        public static void p(char b){
>            System.out.println(b);
>        }
>    }
>    ```

## 方法递归

> 递归很耗费内存，可以不用的时候尽量不用，
>
> 当递归一直未结束(没有结束条件)，会出现以下错误
>
> - ==java.lang.StackOverflowError==  栈内存溢出错误，这是个错误不是异常，错误的结果就是JVM停止工作
>
> ```java
> //java递归算1~N的和
> public class Test{
>     public static void main(String[] args){
>         sum(N);
>     }
>     public static int sum(int N){
>        if(N==1) return 1
>        return N+sum(N-1);
>     }
> }
> //java递归算1~N的阶乘
> public class Test{
>     public static void main(String[] args){
>         sum(N);
>     }
>     public static int mut(int N){
>        if(N==1) return 1
>        return N*mut(N-1);
>     }
> }
> ```

# 面向对象

## 对象和引用

> 对象是new出来的，存储在堆内存中
>
> 对象的地址，给的那个变量称为引用，引用可以是局部变量，也可以是成员变量，存储在栈内存中
>
> ==空引用在读取对象的时候会出现空指针异常==

## this

> this是一个关键字，是一个引用，this变量保存的内存地址是指向自身的
>
> 每个对象都有一个this
>
> ```java
> //this是一个引用
> class Customer{
>     String name;
>     public Customer(){}
>     public void shopping(){
>         sout(this.name+"正在购物！！！");
>     }
> }
> public class Test{
>     psvm(){
>         String name="张三";
>         Customer a=new Customer();
>         a.name=name;
>         a.shopping();
>     }
> }
> ```
>
> ==注意：==this不能出现在静态方法当中，因为静态方法不涉及引用，==即：实例变量只能在实例方法中使用(除非new对象)==
>
> ==带有static的方法不能直接调用**实例方法**或**实例变量**，因为实例方法和实例变量都需要对象==



> this大部分情况下都能省略，**什么时候不能省略呢？**
>
> ```java
> //构造方法或者get set方法
> public Student{
>     private num;
>     private name;
>     public Student(String name,int num){
>         num=num;   //因为有就近原则，这里的num是局部变量，和实例变量没关系，所以这里要使用this
>         name=name;
>     }
> }
> ```

> this除了可以用在实例方法中，还可以用在构造方法中 :（==this(实际参数列表)==）
>
> ==注意==：this只能出现在构造方法的第一行，并且只能写一行，如果出现在第一行，就会出现错误
>
> ```java
> //构造方法重复代码
> class Date{
>     private int year;
>     private int month;
>     private int day;
>     public Date(){
>         /* 所以以下代码可以改写成
>         this.year=1700;
>         this.month=12;
>         this.day=1;
>         */
>         this(1700,12,1);
>     }
>     public Date(int year,int month,int day){
>         this.year=year;
>         this.month=month;
>         this.day=day;
>     }
> }
> ```

## super

>  复习this
>
> - this只能出现在实例方法和构造方法中
> - this的语法是  this.   this()
> - this不能出现在静态方法中
> - this.    大部分情况下是可以省略的
> - this.    在区分局部变量和实例变量的时候不能省略
> - this()   只能出现在构造方法的第一行，通过当前构造方法去调用"本类"中的其他构造方法，目的是 代码复用
>
> super：==super不是一个引用，super也不保存内存地址，super也不指向任何对象，super只是代表当前对象内部的那一块父类型的特征==    所以单独使用this可以，但是直接使用super会出问题，super后边必须跟.或者()
>
> - super只能出现在实例方法和构造方法中
> - super的语法是  super.   super()
> - super不能出现在静态方法中
> - super.    大部分情况下是可以省略的
> - super.    子类中有和父类同名的属性，并且希望在子类中使用父类的属性，那么就是要super不能省略
> - super()   只能出现在构造方法的第一行，通过当前构造方法去调用"父类"中的其他构造方法，目的是 代码复用
> - super后边不仅可以跟属性也可以跟方法
>
> ```java
> public class Test{
>     psvm(){
>         new B();
>     }
> }
> class A{
>     public A(){
>         sout("调用A类的无参数构造方法");
>     }
> }
> class B{
>     public B(){
>         super();   //这一行是隐形的  所以子类有的构造方法，父类必须有相对应参数的构造方法与之对应，不然super()方法会报错
>         sout("调用B类的无参数构造方法");
>     }
> }
> //结果是    调用A类的无参数构造方法   调用B类的无参数构造方法
> ```
>
> super() 对应的现实中就是，要有儿子必须先要有老子
>
> ==关于this和super题目==
>
> ```java
> public class Test{
>     public static void main(String[] args){
>         new C();
>     }
> }
> class A{
>     public A(){
>         System.out.println("A的无参数构造方法");1
>     }
> }
> class B extends A{
>     public B(){
>         System.out.println("B的无参数构造方法");2
>     }
>     public B(String name){
>         System.out.println("B的有参数构造方法(String)");3
>     }
> }
> class C extends B{
>     public C(){
> 	    this(name);
>         System.out.println("C的无参数构造方法");4
>     }
>     public C(String name){
>         this(name,age);
>         System.out.println("C的有参数构造方法(String)");5
>     }  
>     public C(String name,int age){
>         super(name);
>         System.out.println("C的有参数构造方法(String ,age)");6
>     }  
> }
> //输出顺序是  13654
> ```
>
> 父类中的private属性  只能在本类中使用
>
> 比如子类的构造方法需要访问父类的private属性的时候，就需要使用super()调用父类的有参数构造方法
>
> ```java
> public class Test{
>     public static void main(String[] args){
>     	Vip a=new Vip("张三");
>     	a.shopping();   
> 		System.out.println(a.name);
>     }
> }
> class Customer{
>     public String name;
>     public Customer(){}
>     public Customer(String name){
>         super();
>         this.name=name;
>     }
> }
> class Vip extends Customer{
>     //private String name;   //如果加上这一行代码   结果this 是null super是张三 没有this 和super 默认是this
>     public Vip(){}
>     public Vip(String name){
>         super(name);
>     }
>     public void shopping(){
>         System.out.println(this.name+"正在购物");
>         System.out.println(super.name+"正在购物");
>         System.out.println(name+"正在购物");
>     }
> }
> 
> ```
>
> 



## **静态代码块**

> ```java
> static{
> 	java语句；
> 	java语句；
> 	....
> }
> ```
>
> 类加载的时候执行，并且只执行一次，作用：***给程序员一个时机--类加载时机***
>
> ==其他代码块==
>
> 基本代码块：
>
> ​	在main方法中  直接{    java语句   }使用   按照上下顺序进行运行
>
> 构造代码块：
>
> ​	在对应的class中， 直接{   java语句  }使用   按顺序运行，之后才会调用构造方法

## 继承

> 继承的缺点：耦合度太高
>
> 子类继承父类，相当于把父类的代码复制了一份，只是不在子类中显示罢了
>
> 实际开发中什么时候用extends呢？     
>
> - 猫是一个动物
> - 信用卡账户是一个银行账户
> - 白菜是一种蔬菜
>
> 以上这种  是 或者 is  都是可以进行继承的突破口

## object类

==面向对象编程：OOA(面向对象分析),OOD(面向对象设计),OOP(面向对象编程)==

==封装的作用：==

1. ==保证内部结构的安全==
2. ==屏蔽复杂，暴漏简单==

> java源码位置：==jdk/lib/src/java.base/java/==
>
> object类中的方法：
>
> - toString()
>
>   - 直接对未重写toString方法的对象执行.toString得到的结果  xxxx@yyyy   这里的yyyy对应的是该对象所在内存地址经过“哈希算法”得到的十六进制结果，xxxx是对象的类型
>
>   - 如果直接sout对应的引用，那么java会默认调用这个引用的toString方法 
>
>   - ```java
>     public String toString() {
>             return getClass().getName() + "@" + Integer.toHexString(hashCode());
>      }//源代码
>     ```
>
>     
>
> - equals()==之后再讲==
>
>   ```java
>    public boolean equals(Object obj) {
>           return (this == obj);
>       }//equals方法的源代码
>   
>   //重写equals方法
>   public boolean equals(Object obj){
>       if(obj==null) return false;
>       if(obj==this) return true;
>       if(!(obj instanceof MyTime)) return false;
>       MyTime m=(MyTime)obj;
>       if(this.year==m.year&&this.month==m.month&&this.day==m.day) return true;
>   }
>   ```
>
>   java中所有的==基本数据类型==比较是否相等使用==
>
>   java中所有的==引用数据类型==比较是否相等使用equals方法
>
> - clone()
>
> - hashcode
>
> - finalize() 
>
>   ```java
>   //Object中的源码
>   protected void finalize() throws Throwable{}
>   //这个方法不需要程序员自己来调用，JVM的垃圾回收器负责调用
>   ```
>
>   ==finalize方法的执行时机==：当一个对象即将被垃圾回收器(GC)回收的时候，垃圾回收器负责调用finalized方法
>
>   ==finalize方法的作用==：对象销毁的时机叫做垃圾销毁时机，如果希望在对象销毁时机执行一段代码，就需要讲代码写入finalize方法中
>
>   ==静态代码块是类加载时机==
>
>   ==finalize是垃圾回收时机==
>
>   当给对应的对象赋值null的时候就相当于给它回收了     
>
>   建议启动垃圾回收器    System.gc();

==注意==：在源码中，如果一个方法是以“；”结尾的，并且修饰符列表有“native”关键字，那么其底层是调用了c++写得dll(动态链接库)文件

## String

> String重写toString和equals方法
>
> 两个字符串进行比较直接使用String重写的==equals==方法即可进行比较
>
> String类的==toString==方法直接输出对应的字符串

## 方法覆盖

> **什么时候使用方法覆盖呢？**
>
> ​	子类继承父类之后，当继承过来的方法无法满足子类的业务需求的时候，需要考虑重写
>
> 方法重写=方法覆盖
>
> override、overwrite     ！=  overload(方法重载)
>
> **当子类对父类的方法进行重写的时候，父类的方法仍然在子类当中，不过继承过来的方法已经被标记了，所以JVM只认识我们程序员自己写得重写之后的方法，不会调用已经标记的继承过来的父类的方法**
>
> ==方法覆盖必须：方法名相同，参数列表相同，相同的返回值类型==
>
> **方法覆盖注意事项：**
>
> - ==继承中，对于方法的覆盖，**访问权限只能越来越高，不能越来越低**    并且   **重写之后的方法不能比之前的方法抛出更多的异常**==
> - ==方法覆盖只针对方法，和属无关==
> - ==私有方法无法覆盖==
> - ==构造方法不能继承，所以也不能覆盖==
> - ==静态方法覆盖没有意义==

## 多态

> 向上转型(子转父)和向下转型(父转子)的前提都是    ==要有继承关系==    ==编译过程不会new对象==
>
> ```java
> //多态
> Animal a=new Cat();
> a.move();
> //编译阶段：只知道a是一个Animal，并且去Animal.class中找到了move方法，所以编译通过(绑定父类方法)
> //运行阶段：a指向自己的子类对象，运行子类对象的move方法(动态绑定子类方法)
> ```
>
> **什么时候要向下转型**  *当你要访问的是子类中特有的方法的时候需要向下转型*
>
> **为什么要使用instanceof关键词**(运行阶段动态判断)  *因为向下转型有风险 比如如下代码*
>
> ```java
> Animal a=new Bird();
> Cat b=(Cat) a;
> b.catchMouse();
> //运行错误
> ```
>
> instanceof的结果是boolean类型   用法  ***引用 instanceof 对象***

> 多态在开发中的作用是：
>
> ​		**==降低程序的耦合度，提高扩展力==**
>
> 

## final

> final是java语言中的一个关键字
>
> final标志最终的不可变的
>
> final可以修饰变量、方法还有类
>
> - final修饰的方法无法被覆盖
>
> - final修饰的类无法被继承
>
> - final修饰的变量一旦赋值之后不能重新赋值(final修饰一个引用也是这个道理，因为引用中存储的是一个地址，一旦final修饰的引用指向了对应的对象，也就是地址已经写入到了该引用内存，那么地址不可再变)
>
> - final修饰的实例变量，系统不管赋值，要求程序员自己赋值   ==实例变量在new对象的时候赋值==
>
>   ```java
>   class User{
>       final double height=1.8;
>       final double weight;//这一行不可行，系统不管赋值
>       public User(){
>           weight=0.8;//这样可以，虽然无参构造，或者无构造的时候，系统会自动赋值，但是这里是在系统赋值之前进行的手动赋值，所以编译可以通过
>       }
>   }
>   ```
>
>   
>
> ==如果不想让某个类被继承，那么可以用final修饰符来修饰该类==   String就是final修饰的不可继承
>
> ==子类中特有的方法，在使用多态的时候会报错，因为编译器只会看父类引用是否有对应名称的方法，没有就会直接报错，除非强制向下转型，或者不适用多态==
>
> final不管能不能调用，final管的是方法变量和类是最终的，不变的
>
> 

## 常量

> 对于chinese这样的类，国家是一个固定值，不管加不加final，只要是实例变量，就会占用内存空间(在堆中)。
>
> 所以final一般修饰的实例变量都要加static  ----->static final+变量名，==静态变量存储在方法区==，也就是常量。
>
> ==注意==：
>
> - 常量的命名，建议全部大写， 每个单词之间使用下划线连接
> - 常量和静态变量，都是存储在方法区，并且都是在类加载的时候初始化
> - ==常量一般都是公开的，因为公开你也改不了，不用封装==

## 抽象类

> ```mermaid
> graph TD;
> 	银行账户类-->储蓄卡类;  
> 	银行账户类-->信用卡类;
> 	信用卡类-->小明的信用卡; 
> 	信用卡类-->小花的信用卡;
> 	储蓄卡类-->小明的储蓄卡;
> 	储蓄卡类-->小花的储蓄卡;
> ```
>
> 银行账户类是==抽象类==
>
> 信用卡类是==类==
>
> 下边对应的卡是==对象==
>
> 当然==抽象类仍然可以进一步抽象==
>
> 抽象类无法进行实例化，因为抽象类的具体---->类本身在生活中就是不存在的实体
>
> 抽象类属于==引用数据类型==
>
> 抽象类的语法
>
> ```java
> [修饰符列表] abstract class 类名{
> 	类体;
> }
> ```
>
> final是为了防止继承
>
> abstract是为了继承   所以final和abstract是==敌人==  所以final和abstact不能联合使用
>
> 抽象类不能实例化对象，但是有构造方法，这个构造方法是给子类创造对象使用的 

## 抽象方法

> 没有实现的方法， 没有方法体的方法就是抽象方法
>
> ```java
> public abstract void doSome();
> //特点1：没有方法体，以分号结尾
> //特点2：前边的修饰符列表有abstract关键字
> ```
>
> 抽象类不一定有抽象方法，并且抽象类中也可以有非抽象方法，抽象方法必须出现在抽象类中
>
> ==**非抽象类继承抽象类，必须将抽象类的抽象方法实现**==
>
> ==面向抽象编程==
>
> ```java
> public class Test{
>     public static void mian(String[] args){
>         Animal a=new Bird();//这就是面向抽象编程
>     }
> }
> abstract class Animal{
>     
> }
> class Bird extends Animal{
>     
> }
> ```
>
> **==OCP原则==**：开闭原则，是说一个实体应该通过扩展来实现变化，而不是通过修改已有的代码来实现变化

## 接口(行为动作  like a)

> 接口是==完全抽象的==
>
> 接口支持多继承，一个接口可以继承多个接口，**==接口中只包含两部分内容：1、常量  2、抽象方法==**
>
> - 接口中方法的修饰符列表可以省略：public abstract
> - 接口中常量的修饰符列表也可以省略：public static final 
>
> 接口中的所有元素都是公开的(public修饰的)
>
> 语法是:
>
> ```java
> [修饰符列表] interface 接口名{}
> ```
>
> 类和类之间叫做继承，类和接口之间叫做实现
>
> ==缺省的权限小于public==
>
> 一个类可以实现多个接口
>
> ==注意==：
>
> ```java
> class Test{
>     public static void main(String[] args){
>         M a=new E();
>         K b=(K)a;//接口和接口之间进行强制类型转换的时候，没有继承关系也可以强转  
>         //类转成一个没有实现的接口，可以强转成改接口
>         //运行的时候可能会出现ClassCastException 
>     }
> }
> interface K{}
> interface M{}
> class E implements M {}
> ```
>
> ==向上转型或向下转型的前提是两个类之间有继承关系，否则在编译期间就会报错，但是这个结论不适用在接口方面==
>
> 一个类同时继承类和接口的时候，先extends之后再implements

## 接口的作用

> 面向接口编程，有了接口就是可插拔，可插拔也就是  低耦合 高扩展
>
> ==has a就要以属性的形式存在==
>
> 面向接口编程，可以降低程序的耦合度，提高程序的扩展力，符合OCP原则，接口的使用离不开多态(接口+多态才能解耦合)
>
> ```java
> //去餐厅吃饭的接口例子
> public class Test{
>     public static void main(String[] args){
>         FoodMenu f=new AmericaCook();
>         Customer c=new Customer(f);
>         c.order();
>     }
> }
> interface FoodMenu{
>     void xihongshichaojidan();
>     void yuxiangrousi();
> }
> class ChineseCook implements FoodMenu{
>     public void xihongshichaojidan(){
>         System.out.println("中国厨师做西红柿超级蛋");
>     }
>     public void yuxiangrousi(){
>         System.out.println("中国厨师做鱼香肉丝");
>     }
> }
> class AmericaCook implements FoodMenu{
>     public void xihongshichaojidan(){
>         System.out.println("美国厨师做西红柿超级蛋");
>     }
>     public void yuxiangrousi(){
>         System.out.println("美国厨师做鱼香肉丝");
>     }
> }
> class Customer{
>     private FoodMenu foodmenu;
>     public Customer(FoodMenu foodmenu){
>         this.foodmenu=foodmenu;
>     }
>     public void order(){
>         foodmenu.xihongshichaojidan();
>         foodmenu.yuxiangrousi();
>     }
> }
> 
> ```
>
> 接口解耦合，解的是  ==调用者和实现者的耦合==
>
> ==**接口和接口的区别**==：
>
> - 接口是完全抽象的   抽象类是半抽象的
> - 接口没有构造方法  抽象类有构造方法
> - 接口和接口之间支持多继承  类和类之间只能单继承
> - 一个类可以同时实现多个接口  但是一个抽象类只能继承一个类

## import和包

> 包名的命名规范：  ==公司域名倒叙+项目名+模块名+功能名==
>
> package需要出现在代码的第一行 import再package下边
>
> 如果代码第一行有包名  如何编译 可以直接讲对应的包全部建好  ==javac -d . 项目名.java==这里的.是当前目录的意思
>
> java.lang包小的类都不需要导包

## 访问控制权限

> 4个访问控制权限
>
> - private    表示私有的，只能再本类中使用
> - public      公开的，在任何位置都可以访问  
> - protected       只能在本类或者同包或者子类中访问
> - 默认啥也不写     只能在本类，以及同包下访问
>
> | 访问控制符 | 本类 | 同包 | 子类 | 任意位置 |
> | ---------- | ---- | ---- | ---- | -------- |
> | public     | 可以 | 可以 | 可以 | 可以     |
> | protected  | 可以 | 可以 | 可以 | 不行     |
> | 默认       | 可以 | 可以 | 不行 | 不行     |
> | private    | 可以 | 不行 | 不行 | 不行     |
>
> 访问修饰符可以修饰什么？
>
> - 属性  4个都可以
> - 方法   4个都可以
> - 类     只能public 和默认
> - 接口   只能public和默认

## API

> Application Program Interface(应用程序编程接口)
>
> 整个JDK的类库就是javase的API

## 内部类

> 内部类的分类：
>
> - 静态内部类：相当于静态变量
>
> - 实例内部类：相当于实例变量
>
> - 局部内部类：相当于局部变量
>
>   ```java
>   class Test{
>       static class Inner1{}   //静态内部类        
>       class Inner2{}      //实例内部类
>       public void doSome(){  
>           class Inner3{}   //局部内部类
>       }
>   }
>   ```
>
>   

### 匿名内部类

> 匿名内部类是局部内部类的一种
>
> ```java
> //举例说明
> class Test{
>     public static void main(String[] args){
>         MyMath m=new MyMath();
>         m.mySum(new Computer(){
>             public int sum(int a,int b){
>                 return (a+b);
>             }
>         },10,20);
>     }
> }
> interface Computer{
>     int sum(int a,int b);
> }
> 
> 
> class MyMath{
> 	public void mySum(Computer c,int a,int b){
>         System.out.println( c.sum(a,b));
>     }    
> }
> ```
>
> 为什么不建议使用匿名内部类？
>
> ​	==因为只能用一次，没有直接用类实现接口方便==

# 数组

## 一维数组

> 数组是存放在==堆内存==的
>
> 数组一旦创建，Java中规定，长度不可再变
>
> length属性是数组自带的

> 数组的优缺点：
>
> ==**优点**==：
>
> - 每一个元素的内存地址空间存储上都是连续的
> - 每一个元素在空间中所占的内存都是一样大的
> - 知道第一个元素的位置，知道每个元素的内存大小，可以直接通过数学计算得到对应的元素位置，所以一个100大小的数组和100w大小的数组检索的效率都是一样的
>
> ==**缺点**==：
>
> - 由于地址是连续的，所以对数据进行增删的时候效率低，因为随机增删会涉及到后边元素统一前移或者后移。
> - 数组不能存储大数据量，因为在内存中很难找到一块很大的地址连续内存空间
> - ==数组的最后一个元素的增删，没有效率影响==

> 数组初始化
>
> - 静态初始化   int[] a={1,2,3};
> - 动态初始化   int[] a=new int[5];
> - sout(new int[] {1,2,3})

> ==数组扩容==  ：数组扩容效率较低，涉及到数组拷贝的问题

## 二维数组

> int[][] a=new int[2] [2]
>
> a[0] [0]的意思是第一个以为数组的第一个元素
>
> sout(new int[ ] [ ] {{1,2,3},{2,3,4},{2,3,4}});

# 异常

> 异常在java中是以类的形式存在，每一个异常类都可以创建异常对象
>
> ```mermaid
> graph TD;
> 	A(Object)--"继承"---B(Throwbale)
> 	B(Object)--"继承"---C(Error)
> 	B(Object)--"继承"---D(Exception)
> 	D(Excption)--"继承"---E(RuntimeException)
> 	D(Excption)--"Exception的直接子类"---F(ExceptionSubClass)
> 	E(RuntimeException)--"继承"---G(NullPointException)
> 	E(RuntimeException)--"继承"---H(ArithmeticException)
> 	E(RuntimeException)--"继承"---I(ClassCastException)
> ```
>
> 不管是错误还是异常都是可抛出的
>
> ==所有的Error，java程序只有一个结果就是终止程序的执行，推出JVM==
>
> ==所有的RuntimeException及其子类都属于运行时异常==
>
>  所有Exception的直接子类，都叫做==编译时异常== 
>
> ==编译时异常的意思是在编译阶段发生的异常嘛？==
>
> - 不是，编译时异常的意思是，在编译阶段程序员就要处理的异常，如果不处理编译器会报错
> - 运行时异常在编写程序阶段，==可以选择处理，也可以选择不处理==
>
> **编译时异常和运行异常，都发生在运行阶段，编译阶段异常是不会发生的，因为异常是new出来的，只有程序运行阶段才可以new对象**
>
> ==编译时异常和运行时异常的区别==
>
> 1. 编译时异常(受检异常，受控异常)发生的概率比较高
>
>    ==举例说明==：
>
>    ​		看见外边下雨，防止出门淋雨感冒(异常)，所以出门带了一把伞(**感冒异常**发生之前的处理方式)
>
>    ​		对于这种概率较高的异常，需要运行之前进行预处理
>
> 2. 运行时异常(未受检异常，非受控异常)发生的概率比较低
>
>    ==举个例子==：
>
>    ​		出门可能被飞机砸到(异常)
>
>    ​		没必要对这种低概率异常进行预处理，不然会活得很累

> java中异常处理的两种方式：
>
> - 在方法声明的地方，使用throws关键字
> - 使用try...catch语句对异常捕捉
>
> 如果一直throws给上级，直到main抛给了JVM之后，只有一个结果，就是JVM终止程序运行
>
> ```java
> class Test{
>     public static void main(String[] args){
>         dosome();//因为doSome方法有throws声明，所以在调用doSome方法的时候就要对异常进行处理，要么继续throws，也么try catch，catch的写法  catch(Exception e){e.printStackTrace();}
>     }
>     public static void doSome() throws ClassNotFoundException{
>         System.out.println("doSome");
>     }
> }
> //手动抛异常
> if(要判断的异常){
>     throw 要抛出的异常对象
> }
> ```
>
> ==代码出现异常，一个域内，出现代码之后的代码不会执行==  ==catch的后续代码会执行== catch可以写多个，这样精确到一个个的时候，有利于程序的调试
>
> catch中的异常可以通过  逻辑 |   进行统一
>
> ==如何选择throws和try catch呢？==   如果确定了调用者需要处理，就throws

## 异常的重要方法

```java
String msg=exception.getMessage();//获取异常简单的表述信息
exception.printStackTrace();//打印异常追踪的堆栈信息   print异常信息有一个单独的线程负责
```

## finally

> finally通常使用在什么情况?
>
> ```java
> try{
> 	FileInputStream f=new FileInputStream("路径");
>     
>     String s=null;
>     s.toString();//这里会出现空指针异常
>     
>     f.close();//关闭流
> }catch(Excepption e){
>     e.printStackTrace();
> }
> //以上代码如果不加finally的话，close就关闭不了，一直占用资源
> //finally中的代码一定会执行
> ```
>
> return不会对finally的运行产生影响  但是System.exit()  退出JVM语句，会影响finally的运行
>
> **==一道简单的finally的面试题==**
>
> ```java
> public static int m(){
>     int i=100;
>     try{
>         return i;
>     }finlly{
>         i++;
>     }
> }//上述代码的最终结果是100，因为只要return i出现在i的下边，就会遵循java更古不变的自上而下的规则
> //以上代码 反编译之后的结果如下
> public static int m(){
>     int i=100;
>     int j=i;
>     i++;
>     return j;
> }
> ```

## final finally 和finalize 的区别

> final
>
> - final修饰的类无法继承
> - final修饰的方法无法覆盖
> - final修饰的变量无法重新赋值
>
> finally
>
> - 和try一起使用
> - finally语句块中的代码必须执行
>
> finalize
>
> - 是一个Object类中的方法名
> - 这个方法是由垃圾回收器GC负责调用的

## 如何自定义一个异常

> ```java
> /*
> 两步：
> 1、编写一个类继承Exception或者RuntimeException
> 2、提供两个构造方法，一个无参的，一个String的
> */
> public class MyException extends Exception{ //Exception对应编译时异常  RuntimeException对应运行时异常
>     public MyException(){
>         
>     }
>     public MyException(String s){   //这里的s就是  getMessage的结果
>         super(s);
>     }
> }
> ```

# 集合

> 集合存储的都是引用数据类型
>
> 集合在java.util.*中  ArrayList 底层是数组 LinkedList 底层是链表 TreeSet 底层是二叉树 

## Collection

> 接口Interable(==Interator方法==)<-----接口Collection<----接口Interator(==hasNext()、next()、remove()方法==)  两个都是接口
>
> Collection有两个泛化(继承)接口，分别是List和Set:
>
> - **==List==**:存储的元素有序可重复，有下标，有序的意思是==存进和取出的顺序不变==，有序是因为有下标
>   
>   - **ArrayList(初始化容量是10，扩容是1.5倍)**
>   
>     - ArrayList有三种构造方法
>   
>       1. 无参的  2.传入int类型的集合初始容量  3.传入一个结合
>   
>     - 底层是Object类型的数组，非线程安全的
>   
>       - 如何变成线程安全的呢
>   
>         ```java
>         List l=new ArrayList();
>         Collections.synchronizedList(l);//集合工具类
>         ```
>   
>         
>   
> - 初始化容量是10(底层是：==先创建一个容量为0的数组，当添加第一个元素的时候，初始化结合容量为10==)，如果**add的元素如果超过了初始容量，那么集合就会扩容为之前的1.5倍**，ArrayList优化，最好还是少进行扩容，因为数组扩容效率比较低
>   
> - 初始化容量可以使用int构造方法传初始化容量进去
>   
>   - 数组优点：**检索效率比较高**  缺点：**增删改查效率低**  但是**向数组末尾添加元素效率很高**
>   
>   - **LinkedList(没有初始化容量)**
>   
>     - 底层采用了==双向链表数据结构==
>   
>     - ```java
>       //单链表的简单实现代码
>       public class Test
>       {
>       	public static void main(String[] args){
>       		Link l=new Link();
>                l.add("aaa");
>       		System.out.println(l.header.data+"?"+l.end.data+"size"+l.size);
>       	}
>       }
>       class Node
>       {
>           public Object data;
>           public Node next;
>           public Node(){}
>           public Node(Object data,Node next){
>               this.data=data;
>               this.next=next;
>           }
>       }
>       class Link
>       {
>       	int size=0;
>           Node header=null;
>           Node end=null;
>           public void add(Object obj){
>               if(header==null){
>                   header=new Node(obj,null);
>                   end=header;
>               }else{
>                   Node newNode=new Node(obj,null);
>                   end.next=newNode;
>                   end=newNode;
>               }
>       		size++;
>           }
>           public void remove(Object obj){}
>           public void modify(Object newObj){}
>           public int find(Object obj){return 1;}
>       }
>       //注意************
>       //LinkedList也有下标，List都有下标，但是ArrayList的检索效率高并不是仅仅因为有下标
>       //是因为ArrayList的底层是数组，而LinkedList的底层是有下标的链表，导致它的检索或者查找元素的效率比较低，只能从头节点开始一个一个遍历
>       链表的优缺点：
>           优点：链表不需要连续存储空间
>           	因此随机增删效率很高，所以在遇到随机增删集合中元素的业务比较多时，建议使用			LinkedList
>           缺点：不能像数组那样通过数学表达式的方式得到对应元素的内存地址，每次都需要从头节点		  进行一个一个检索，效率较低
>                       
>           ArrayList把检索发挥到了极致
>           LinkedList把随机增删发挥到了极致
>                       
>           不过平时开发都是往末尾添加元素，所以ArrayList用的是比LinkedList多的
>                   
>       ```
>   
>       
>   
>   - **Vector**(初始化容量是10，扩容是2倍)
>   
>     - 底层采用数组数据结构，相对于ArrayList，Vector是线程安全的(sychronized,虽然线程安全，但是效率较低，**因为现在线程安全有别的方案，所以Vector用的少了**)
>   
> - ==**Set**==:无序不可重复，没有下标，所以无序(不可重复是==如果重复只会存在一个结果==)
>   - **HashSet**
>     - **new HashSet实际上是new HashMap**，所以HashSet存储元素也是存到了HashMap当中了，所以其底层是哈希表数据结构
>     
>   - **TreeSet**
>     - TreeSet的父接口是SortedSet，再往上才是Set接口，**new TreeSet底层实际上是new TreeMap**，所以其底层是二叉树数据结构，放在TreeSet里的==数据可以自动按照大小排序==
>     
>     - **对于自定义的类型来说，TreeSet可以排序吗  ？   不能，因为没有指定对应的比较规则**
>     
>       - **解决方式**
>     
>         1. ==需要实现Comparable接口才可以==(Comparable是lang下的)
>     
>            ```Java
>            class WuGui implements Comparable{
>                int age;
>                public WuGui(){}
>                public WuGui(int age){this.age=age}
>                public int compareTo(WuGui o){
>                    return this.age-o.age;
>                }
>            }
>            ```
>     
>         2. 构造方法传入比较器(Comparator是util下的)
>     
>            ```java
>            class MyComparator implements Comparator<WuGui>{
>                public int compare(Wugui o1,WuGui o2){
>                    return o1.age-o2.age;
>                }
>            }
>            class Test{
>                public static void main(String[] args){
>                    MyComparator m=new MyComparator();
>                    Set<WuGui> set=new TreeSet(m);
>                }
>            }
>            ```
>     
>         3. 使用匿名内部类
>     
>            ```java
>            Set<Customer> m=new TreeSet<>(new Comparator<Customer>() {
>                            @Override
>                            public int compare(Customer o1, Customer o2) {
>                                return o1.getAge()-o2.getAge();
>                            }
>                        });
>            ```
>     
>         ==对于以上三种方式==：要选哪种方式，如果比较规则很少改变，建议使用Comparable接口
>     
>         如果比较规则有多个，并且多个比较规则之间频繁切换，建议使用Comparator接口
>     
>   - TreeSet  使用的遍历方式是：中序遍历

> ==Collection中可以存储什么东西？==集合中不能直接存储基本数据类型，也不能存java对象，只能存储java对象的内存地址
>
> ==Collection中的方法：==
>
> - boolean add(E e)
>
> - int size()  ==获取当前集合中的元素个数， 不是获取集合的容量==
>
> - void clear()
>
> - boolean contains(Object o)
>
>   - ```java
>     public class Test{
>         public static void main(String[] args){
>             Collection c=new ArrayList();
>             String s1=new String("abc");
>             c.add(s1);
>             String s1=new String("def");
>             c.add(s2);
>             String x=new String("abc");
>             sout(c.contains(x));//contains底层调用的是equals方法，对比的是String，所以结果是true
>         }
>     }
>     //重写equals方法  
>     public boolean equals(Object o){
>         if(o==null || !(o.instanceof(User))) return false;
>         if(o==this)  return true;
>         User u=(User) o;
>         return (o.name.equals(this.name));
>     }
>     
>     
>     //结论：存放在集合中的类型，一定要重写equals方法
>     ```
>
> - boolean remove(Object o)
>
>   - ```java
>     Collection c=new ArrayList();
>     String s1="abc";
>     c.add(s1);
>     String s2="abc";
>     c.remove(s2);
>     sout(c.size());// 说明remove底层调用了equals方法
>     
>     
>     
>     Collection c=new HashSet();
>     c.add("aa");
>     c.add("abb");
>     c.add("ab");//存进去什么类型，取出来还是什么类型，只不过输出的时候会调用toString方法
>     Iterator i=c.iterator();
>     while(i.hasNext()){
>         sout(i.next());
>         c.remove(i.next());//会出现异常，因为集合的内容发生了变化 所以这里可以使用迭代器的remove方法      i.remove();  即删除迭代器当前所指的对象
>     }
>     ```
>
>     
>
> - boolean isEmpty()
>
> - Object[] toArray()   将集合转换成数组
>
> - Ierator iterator()  
>
>   - ```java
>     Collection c=new HashSet();
>     c.add("aa");
>     c.add("abb");
>     c.add("ab");//存进去什么类型，取出来还是什么类型，只不过输出的时候会调用toString方法
>     Iterator i=c.iterator();
>     while(i.hasNext()){
>         sout(i.next());
>     }
>     ```
>
>   - 迭代器对象的两个方法
>
>     - boolean hasNext()
>
>     - Object next()
>
> List中的方法，在Collection的基础上：
>
> - void add(int index,E element)   这样添加效率太低 
> - E get(int index)   因为有下标，所以List集合有他自己的遍历方式
> - int indexOf()
> - int lastIndexOf()
> - E remove(int index)
> - E set(int index,E element)

## Map

> ==Key和value里都存着java对象的内存地址==，所有Map的key都是无需不可重复的，Map集合的ket和Set集合存储元素特点相同

> ==Map常用方法==
>
> - void clear()
>
> - boolean containsKey(Object key)   **contains方法底层都是equals方法**
>
> - boolean containsValue(Object value) 
>
> - V get(Object key)    通过key获取value
>
> - Set<K>  keySet()   获取所有的Key
>
> - V put(K key,V value)   添加键值对
>
> - V remove(Object key)
>
> - int size()
>
> - Collection<V> values()    获取Map集合中所有的value，返回一个Collection
>
> - Set<map.Entry<K,V>>entrySet()  将Map集合转换成Set集合
>
>   - ```java
>     key      value
>     ===============
>     1		zhangsan
>     2		lisi
>         上述Map通过entrySet之后，得到的结果如下：
>         1=zhangsan
>         2=lisi
>     ```
>
>     ```java
>     import java.util.*;
>     public class Test
>     {
>     	//遍历Map集合
>     	public static void main(String[] args){
>     		Map<Integer ,String > map=new HashMap<>();
>     		map.put(1,"zhangsan");
>     		map.put(2,"wangwu");
>     		//迭代器
>     		Set<Integer> set=map.keySet();
>     		Iterator<Integer> i=set.iterator();
>     		while(i.hasNext()){
>     			//Integer key=i.next();
>     			//String value=map.get(key);
>     			//System.out.println(key+"="+value);
>     			System.out.println(i.next()+"="+ map.get(i.next()));//注意 调用一次next就会迭代一次
>     		}
>     		//foreach
>     		for(Integer ii:set){
>     			System.out.println(ii+"="+map.get(ii));
>     		}
>     		//Set<Map.Entry<K,V>> entrySet()
>     		Set<Map.Entry<Integer,String>> set2=map.entrySet();
>     		for(Map.Entry<Integer,String> s:set2){
>     			System.out.println(s.getKey()+"="+s.getValue());
>     		}//这种foreach适合大数据量使用，因为是直接通过Node的属性值进行获取的
>     	}
>     }
>     ```
>
>     

## HashMap(初始容量是10，默认加载因子是0.75)

> Map<----HashMap(非线程安全的，类)    Map<----HashTable(线程安全的，过时了，类)<--Properties(类，存储在Properties的key和value都必须是String类型，不能是其他类型，被称为==属性类 ==)  两个底层都是哈希表

> HashMap允许key和value值都可以为null(HashTable的key和value都不能为空)
>
> HashMap扩容是2的倍数
>
> ```java
> Map map=new HashMap();
> Integer i=map.put(null,100);
> sout(map.size());//1
> ```

- HashTable的初始化容量是11，默认加载因子是0.75 它的扩容是原容量乘2再加1

## 哈希表/散列表

> ==数组==是查询遍历效率高    ==链表==是随机增删改效率高  ==哈希表==是结合两个的优点
>
> 哈希表：底层是一维数组，这个数组的每个元素是一个单向链表
>
> ==map.put(k,v)的实现原理：==
>
> 1. 先将kv封装到Node对象中
> 2. 底层会调用hashMap()得到hash
> 3. 通过哈希函数/哈希算法，将hash值转换成数组下标，下标位置如果没有任何元素，就把Node添加到或者位置，如果下标对应的位置有链表，拿着k和链表上每个节点的k进行equals，如果所有的equals方法返回都是false，那么就将新节点添加到链表的末尾，如果其中一个equals返回true，会把新的节点的value替换上
>
> ==map.get(key)的实现原理：==
>
> 先调用k的hashCode方法得到哈希值，通过哈希算法转换成数组下标，通过数组下标快速定位到某个位置，如果这个位置什么都没有，返回null。如果有一个单向链表，那么就一一equals k值，有的话返回对应的value，没有就返回null

> ==为了保证hashMap的key或hashSet的==无序不可重复==，对应的元素对象必须重写hashCode和equals方法==
>
> 假设将所有的hashCode()方法返回值固定为某个值，那么会导致底层哈希表变成一个纯单向链表，这种情况成为==散列分布不均匀==
>
> ==散列分布==需要重写hashCode的时候有一定的技巧

> ==***重点***==**：HashMap集合初始化容量必须是2的倍数，因为可以达到散列均匀，提高存取效率**
>
> ​			**如果一个类的equals方法重写了，那么hashCode方法必须重写**
>
> ​			**如果哈希表的单个链表的元素超过8个，那么单向链表会编程红黑树结构，如果数量小于6，会将红黑树改成单向链表**，为了提高检索效率

## Properties(线程安全的)

> 是一个Map集合，继承Hashtable，它的key和value都是String类型，属于==属性类对象==
>
> Properties两个方法：
>
> - setProperty
> - getProperty

## TreeMap

> Map<--SortedMap(接口)<--TreeMap(类，数据结构是二叉树)   **SortedMap**集合的key会自动按照大小顺序排序 

## 泛型

> 没用泛型的话，迭代器拿出来的就是Object类型，代码不好写
>
> ```java
> List<Animal> myList=new ArrayList<Animal>();
> ```
>
> ==自动类型推断机制(又成为钻石表达式)==
>
> ```java
> //jdk8之后   new对象的时候<>中的类型可以不写，系统会自动检测出来
> List<Animal> myList=new ArrayList<Animal>();
> ```
>
> 自定义泛型
>
> ```java
> public class Test<E(名字任意)>{}
> public E doSome(){}   //java自带的E是Element T是type
> ```

## foreach

> 缺点：没有下标
>
> ```java
> List<Integer> l=new ArrayList<>();
> l.add(1);
> for(Integer i:l){
>     sout(i);
> }
> ```
>

# IO流

> Read Input InputStream --->读  读入  输入流     ==硬盘--->内存==
>
> ==IO流分类==：
>
> - 按照流的方式分：输入 和  输出流
> - 按照读取数据的方式不同： 字节流(什么类型的文件都可以读取) 和  字符流(主要为了读取普通文本文件)

## **IO流四大家族**

> - java.io.InputStream   字节输入流
> - java.io.OutputStream  字节输出流
> - java.io.Reader   字符输入流
> - java.io.Writer   字符输出流
>
> 四大家族的首领都是抽象类，所有的流都==实现了closeable接口==，所有流都是可关闭的，所有的==输出流都实现了Flushable==，所有输出流都是可刷新的，所以***==要养成好习惯，所有的流都要关闭，所有的输出流输出之后都要刷新==***

> java.io包中需要掌握的流有16个
>
> ==文件专属==
>
> - java.io.FileInputStream   构造方法有==append参数==，为true，说明文件内容可以追加
>   - ==对应方法==
>     - int read()
>     - int read(byte[] b)
>     - int available()  返回流当中剩余没有读到的字节数量
>     - long skip(long n) 跳过几个字节不读
> - java.io.FileOutputStream
>   - ==对应方法==
>     - int write()
>     - int write(byte[] b)
>     - int write(byte[] b,int off,int len)
>     - 构造 FileOutputStream(String 文件名,boolean append)   append如果为True，那么直接在文件后边追加，不会从头开始替换
> - java.io.FileReader
> - java.io.FileWriter
>
> ==转换流(字节流转换成字符流)==
>
> - java.io.InputStreamReader
> - java.io.OutputStreamWriter
>
> ==缓冲流==
>
> - java.io.BufferedReader
> - java.io.BufferedWriter
> - java.io.BufferedInputStream
> - java.io.BufferedOutputStream
>
> ==数据流==
>
> - java.io.DataInputStream
> - java.io.DataOutputStream
>
> ==标准流==
>
> - java.io.PrintWriter
> - java.io.PrintReader
>
> ==对象流==
>
> - java.io.ObjectInputStream
> - java.io.ObjectOutputStream

## FileInputStream读取文件的代码架子

> ```java
> class Test {
>     public static void main(String[] args) {
>         FileInputStream f = null;
>         try {
>             f = new FileInputStream("Comparable/src/com/wzx/io/tempFile");
>             int readData = 0;
>             while ((readData = f.read()) != -1) {
>                 System.out.println(readData);
>             }
>         } catch (FileNotFoundException fileNotFoundException) {
>             fileNotFoundException.printStackTrace();
>         } catch (IOException ioException) {
>             ioException.printStackTrace();
>         } finally {
>             if (f != null) {
>                 try {
>                     f.close();
>                 } catch (IOException e) {
>                     e.printStackTrace();
>                 }
>             }
>         }
>     }
> }
> ```
>
> IDEA默认的当前路径是哪里？   工程Porject的根就是默认当前路径
>
> - read()    返回值是读取的数据
> - read(byte[] b)   返回值是读取的字节数
>
> ```java
> class Test {
>     public static void main(String[] args) {
>         FileInputStream f = null;
>         try {
>             f = new FileInputStream("Comparable/src/com/wzx/io/tempFile");
>             int readCount = 0;
>             byte[] b = new byte[4];
>             while ((readCount = f.read(b)) != -1) {
>                 System.out.println(new String(b, 0, readCount));
>             }
>         } catch (FileNotFoundException fileNotFoundException) {
>             fileNotFoundException.printStackTrace();
>         } catch (IOException ioException) {
>             ioException.printStackTrace();
>         } finally {
>             if (f != null) {
>                 try {
>                     f.close();
>                 } catch (IOException e) {
>                     e.printStackTrace();
>                 }
>             }
>         }
>     }
> }
> ```
>
> available()   剩余字节个数
>
> ```java
> 	try {
>             f = new FileInputStream("Comparable/src/com/wzx/io/tempFile");
>             byte[] b = new byte[f.available];
>             int readCount =f.read(b);
>             System.out.println(new String(b));
> ```
>
> skip()   跳过几个字节

## 文件拷贝

> ```java
> public class Copy {
>     public static void main(String[] args) {
>         FileInputStream fi=null;
>         FileOutputStream fo=null;
>         try {
>             fi=new FileInputStream("myfile");
>             fo=new FileOutputStream("Comparable/src/com/wzx/io/myfile");
>             byte[] b=new byte[1024*1024];
>             int readCount=0;
>             while((readCount=fi.read(b))!=-1){
>                 fo.write(b,0,readCount);
>             }
>             fo.flush();
>         } catch (FileNotFoundException e) {
>             e.printStackTrace();
>         } catch (IOException e) {
>             e.printStackTrace();
>         } finally {
>             if(fi!=null){
>                 try {
>                     fi.close();
>                 } catch (IOException e) {
>                     e.printStackTrace();
>                 }
>             }
>             if(fo!=null){
>                 try {
>                     fo.close();
>                 } catch (IOException e) {
>                     e.printStackTrace();
>                 }
>             }
>         }
>     }
> }
> ```

## FileReader  文件流

> ```java
> FileReader reader=null;
> try{
>     reader=new FileReader("tempfile");
>     char[] c=new char[4];
>     int readCount=0;
>     while((readCount=reader.read(c))!=-1){
>         sout(String(c,0,readCount));
>     }
> }catch{
> }
> //或者
> try{
>     reader=new FileReader("tempfile");
>     char[] c=new char[4];
>     reader.read(c);
>     for(char cc:c){
>         sout(cc);
>     }
> }
> ```
>
> FileWriter 的write方法，可以直接传入字符串String类型

## BufferedReader

> 带有缓冲区的字符输入流，使用该流的时候不需要自定义char数组，或者说不需要自定义byte数组，自带缓冲。 
>
> ==注意：==当一个流的构造方法中需要一个流的时候，这个被传进来的节点流称为**节点流**，外部负责包装的流称为**包装流**(处理流)，对于包装类来说，关闭包装流，节点流就会自动关闭
>
> ```java
> FileReader reader=new FileReader("文件名");
> BufferedReader br=new BufferedReader(reader);
> 
> //String firstLine=br.readLine();
> String s=null;
> while((s=br.readLine())!=null){
>     sout(s);
> }
> br.close();
> ```
>
> ```java
> FileInputStream in=new FileIputStream();
> BufferedReader br=new BufferedReader(new FileInputStreamReader(in));
> //合并
> BufferedReader br=new BufferedReader(new FileInputStreamReader(new FileInputStream));
> ```

## 数据流

> ```java
> DataOutputStream dos=new DataOutputStream(new FileOutputStream("fileName"));
> byte b=100;  //写到data文件中的不仅仅是具体的数据，还包括数据的类型都一并写入到了文件中
> short s=200;  //所以直接打开文件会出现乱码，所以这时候就需要DataInputStream来读取
> int i=300;
> long l=400L;
> float f=4.4F;
> double d=3.14;
> boolean bo=true;
> char c='a';
> 
> dos.writerByte(b);  //DataInputStream dis 的方法  dis.readByte()....
> dos.writerInt(i);
> ......
> dos.writerChar(c);
> 
> dos.flush();//刷新
> dos.close();//关闭最外层
> ```

## 标准输出流

> java.io.PrintStream 标准字节流输出 ==不需要关闭，默认输出到控制台==
>
> ```java
> PrintStream ps=System.out;
> ps.println("aaaa");
> //标准输出流不需要  flush()  和  手动close()
> ```
>
> 标准输出流怎么指向别处，==不指向控制台==
>
> ```java
> PrintStream pr=new PrintStream(new FileOutputStream("fileName"));
> System.setOut(pr);
> System.out.println("aaa");//这里的输出方向就是file文件	
> ```
>
> ```java
> //记录日志的文件
> import java.io.FileNotFoundException;
> import java.io.FileOutputStream;
> import java.io.PrintStream;
> import java.text.SimpleDateFormat;
> import java.util.Date;
> public class LoggerTest {
>     public static void main(String[] args) {
>         Logger.log("项目开始了");
>     }
> }
> class Logger{
>     public static void log(String msg){
>         try {
>             PrintStream out=new PrintStream(new FileOutputStream("log.txt",true));
>             System.setOut(out);
>             Date date=new Date();
>             SimpleDateFormat sdf=new SimpleDateFormat("yyyy-MM-dd HH:mm:ss SSS");
>             String time=sdf.format(date);
>             System.out.println(msg+time);
>         } catch (FileNotFoundException e) {
>             e.printStackTrace();
>         }
>     }
> }
> ```

## java.io.File

> File是一个文件路径的抽象表示形式 
>
> ==File和四大流没有关系==
>
> ==File的常用方法==：
>
> - 构造  File(String 路径)
> - boolean exists()  判断是否存在
> - creatNewFile()  以文件的形式创建出来
> - mkdir()   以路径的形式创建出来
> - mkdirs() 多重目录
> - String getParent()  获取父路径
> - File getParentFile()  获取父File
> - getAbsolutePath()   获取绝对路径
> - getName()  获取文件名
> - isFile()    判断是否为一个文件
> - isDirectory()  判断是否为一个路径
> - long lastModified()  获取文件最后一次修改时间  返回值是毫秒，从1970年开始
> - long length()  获取文件的大小
> - File [ ] ==listFile()==  获取当前目录下的所有子文件

## 对象的序列化和反序列化

> ==将内存的Java对象，存储到硬盘文件中---->序列化==
>
> **序列化**：ObjectOutputStream 进行拆分对象
>
> ```java
> //写一个Student类，对Student对象进行序列化
> Student stu=new Student("zhangsan");
> ObjectOutputStream oos=new ObjectOutputStream(new FileOutputStream("studentFile"));
> //序列化
> oos.writeObject(stu);
> oos.flush();
> oos.close();
> ```
>
> ==没有内容的接口是标志性接口(起到标识的作用，Java虚拟机看该类实现了该接口，就会特殊对待，JVM看到标志性接口，就会给该类自动生成一个序列化版本号)==：Serializable接口就是标志性接口
>
> ==怎么一次序列化多个对象？    将对象放在集合中，序列化集合即可==注意：放进集合中的对象都要实现Serializable接口，**如果不用集合，按顺序序列化，那么在第二个对象序列化的时候会报错**
>
> 要实现对象序列化，必须将对应的类实现Serializable接口
>
> ```java
> //如果不想序列化某个实例变量的时候
> private int a;=====>  private transient int a;   //虽然设置成游离的，但反序列化会得到对应变量的默认参数
> ```
>
> **反序列化**：ObjectInputStream 进行组装对象
>
> ```java
> ObjectInputStream ois=new ObjectInputStream(new FileInputStream("studentFile"));
> ois.readObject();
> ois.close();
> ```
>
> ==**序列化版本号**==
>
> 10年前，写了一个Student类，并对其对象进行序列化。10年后，Student类序列化版本号改变了，如果直接对硬盘中的对象进行反序列化，会报错：java.io.InvalidClassException
>
> **==java中如何区分不同的类==**
>
> 1. 首先通过类名区分，类名不同，肯定不是一个类
> 2. 如果类名一样，就要对比序列化版本号，版本号不同，不是一个类
>
> ==自动生成序列化版本号的缺陷：==
>
> - 一旦代码确定之后，不能修改，修改之后会重新编译，这样序列化版本号就变了，JVM会认为这是一个全新的类
> - 最终结论：**凡是一个类实现了Serializable接口，建议给该类手动添加一个固定不变的序列化版本号**
> - 手动：**private static final long serialVersionUID=1L**
>
> ==IDEA自动生成序列化版本号：setting-Editor-Inspections-搜索serializable class without 'serialVersionUID '==

## IO和properties

> file文件内容：
>
> username=admin
>
> password=123
>
> ```java
> //读取file文件中的内容并存储到properties对象中
> FileInputStream in=new FileInputStream("file");
> Properties pro=new Properties();
> //调用properties的load(Reader reader/InputStream in)将Map中的数据加载到Map集合当中
> pro.load(in);  //文件中=的左边是在properties的key,=右边是properties的value
> String username=pro.getProperty("username");
> in.close();
> ```
>
> IO和properties的设计理念的应用：经常需要修改的数据，可以单独写在一个文件里，需要使用的时候用程序动态调用即可。
>
> 我们把有这种机制的文件称为==配置文件==，并且如果文件中都是以key=value的形式出现的时候，我们称为属性配置文件，==属性配置文件中的注释用：#==
>
> java规范：属性配置文件命名以properties结尾，但是不是必须的

# 多线程

> 什么是进程？什么是线程？
>
> ==一个软件就是进程==，**线程是进程中的一个执行场景/执行单元**
>
> 在运行java程序的时候，目前至少有两个线程在并发，JVM是进程，进程先调用main方法线程，再调用垃圾回收线程。
>
> ==注意==  线程A和线程B，堆内存和方法区内存共享，但是栈内存独立，一个线程一个栈
>
> 多线程的目的：**为了提高程序的处理效率**

## 多线程的实现方法

> ==***方法1***==、编写一个类，直接继承java.lang.Thread，重写run方法
>
> ```java
> public class Test{
>     public static void main(String[] args){
>         MyThread thread=new MyThread();
>         thread.start();
>     }
> }
> class MyThread{
>     public void run(){
>         sout("子线程");
>     }
> }
> ```
>
> 上边代码中的start的作用是，在JVM中开辟一个新的栈空间 ，start执行完成，这个代码语句使命就结束了，启动成功的线程会自动调用run方法，并且run方法在分支栈的栈底
>
> ![image-20220124204819694](C:\Users\asus\AppData\Roaming\Typora\typora-user-images\image-20220124204819694.png)

> ***==方法2、==***编写一个类，实现java.lang.Runnable接口，实现run方法
>
> ```java
> public class Test{
>     public static void main(String[] args){
>         MyThread thread=new MyThread(new MyRunnable);
>         t.start();
>     }
> }
> class MyRunnable implements Runnable{//该类不是线程，只是一个可运行的类
>     public void run(){
>         sout("子线程");
>     }
> }
> ```
>
> **我们一般使用第二种，面向接口，因为还可以进一步继承类==以上代码还可以通过匿名内部类进行实现==**

## 线程的生命周期

> 为什么线程的运行会一会前一会后？  因为声明周期中的==就绪态==    ==运行态==
>
> 线程生命周期图
>
> ![image-20220124224440314](Z:\typora-pic\image-20220124224440314.png)

## 线程的方法

> - 设置线程的名称    **thread.setName("aaa")**
>
> - 获取线程的名称	**thread.getName()**;    如果不设置名称系统获取名称会得到 "Thread-线程的次序"
>
> - 获取当前线程对象  **static Thread currentThread()**   
>
> - 让当前线程进入休眠，进入“阻塞状态”，放弃占有的CPU时间片 **static void sleep(long millis)**，该方法可以实现一定的效果==即，间隔特定的时间，去执行一段特定的代码，每隔多久执行一次==
>
> ```java
> //关于sleep的一个面试题
> public static void main(String[] args){
>     Thread t=new Thread3();
>     t.setName("aa");
>     t.start();
>     t.sleep(1000*5);//这行代码是主线程休眠，因为sleep方法是静态的和对象无关，最终都是Thread.sleep()
> }
> class Thread3 extends Thread{
>     public void run(){
>         
>     }
> }
> ```
>
> 如果sleep时间久了，怎么叫醒一个正在睡眠的线程，终端线程的睡眠，而不是终端线程的执行
>
> - 实例方法==**t.interrupt()**  终止线程的睡眠==
>
> - **t.~~stop~~()**   已过时不建议使用   强行终止线程的执行 ==缺点==：数据丢失
>
>   - 那么怎么合理终止一个线程呢？  答：打==布尔标记==  如下代码
>
>   - ```java
>     class Test{
>         MyRunnable m=new MyRunnable();
>         Thread r=new Thread(m);
>         r.setName("a");
>         r.start();
>         r.run=false;//终止线程执行
>     }
>     class MyRunnable implements Runnanle{
>         boolean run=true;
>         public void run(){
>             if(run){
>                     
>             }else{
>                 //在return之前可以进行数据保存，从而防止stop引起的数据丢失
>                 return;
>             }
>         }
>     }
>     ```

## 线程调度

> - 抢占式调度模型
>
>   - java就是使用这种模型，谁的优先级高，谁抢到cpu时间片的概率越高
>
> - 均分式调度模型
>
> - ==线程调度方法==
>
>   - **void setPriority(int newPriority)**  设置线程的优先级
>
>   - **int getPriority()**   获取线程的优先级
>
>   - 最低的优先级是1，默认优先级是5，最高优先级是10
>
>   - **static void yield()**  让位方法，暂停当前正在执行的线程对象，并执行其他线程，yield不是阻塞方法，yield的执行，会让当前线程从**运行态**到**就绪态**
>
>   - void join()  合并线程
>
>     - ```java
>       //举例
>       class Test{
>           MyThread t=new MyThread();
>           t.join();//使得主线程进入阻塞，t线程执行，直到t线程结束，主线程才可以运行
>       }
>       class MyThread extends Thread{
>                 
>       }
>       ```
>

## 多线程的安全问题

> ==**什么时候存在多线程问题呢？**==
>
> 1. **多线程并发**
>
> 2. **有共享数据**
>
> 3. **共享数据有修改的行为**
>
>    ```java
>    public class BankTest {
>        public static void main(String[] args) throws InterruptedException {
>            Account act=new Account(10000);
>            Thread t1=new Thread(new BankRunnable(act));
>            Thread t2=new Thread(new BankRunnable(act));
>            t1.setName("t1");
>            t2.setName("t2");
>            t1.start();
>            t2.start();
>        }
>    }
>    class BankRunnable implements Runnable{
>        Account act;
>        public BankRunnable(Account act) {
>            this.act=act;
>        }
>        @Override
>        public void run() {
>            int balanceBefore=act.getBalance();
>            act.withDraw(5000);
>            System.out.println(Thread.currentThread().getName()+"run从"+balanceBefore+"取出"+5000+"元,还有余额："+(act.getBalance())+"元");
>        }
>    }
>    class Account{
>        private int balance;
>        public Account() {
>        }
>        public Account(int balance) {
>            this.balance = balance;
>        }
>        public int getBalance() {
>            return balance;
>        }
>        public void setBalance(int balance) {
>            this.balance = balance;
>        }
>        public void withDraw(int num){
>            int balanceBefore=this.getBalance();
>            try {
>                Thread.sleep(1000);
>            } catch (InterruptedException e) {
>                e.printStackTrace();
>            }
>            this.setBalance(getBalance()-num);
>        }
>    }
>    /*
>    t2从10000取出5000元,还有余额：5000元
>    t1从10000取出5000元,还有余额：5000元
>    */
>    ```
>
> ==**怎么解决线程安全问题呢？**==
>
> 1. 线程排队执行(不能并发)，这种机制称为==线程同步机制==，**同步机制会降低效率** 
>
>    通过同步机制来解决以上代码的安全问题：
>
>    ```java
>    //只需要修改会出现错误的操作代码，因为取钱的动作不能异步，所以要对取钱这个动作采用同步机制
>    
>     public void withDraw(int num){
>         synchronized{//synchronized括号中的数据必须是多线程共享的数据，这里的代码共享对象是账户对象也就是this
>         	int balanceBefore=this.getBalance();
>            try {
>                Thread.sleep(1000);
>            } catch (InterruptedException e) {
>                e.printStackTrace();
>            }
>            this.setBalance(getBalance()-num);   
>         }
>        }
>    /*
>    t1run从10000取出5000元,还有余额：5000元
>    t2run从5000取出5000元,还有余额：0元
>    */
>    synchronized(){}称为同步代码块
>    ```
>
>    怎么解释synchronized呢？
>
>    ​		java语言中，每个对象都有一把==锁==，是一个标志。**假设t1先执行，遇到了synchronized，就会锁定共享对象的锁，之后执行同步代码块中的代码，直到同步代码块中的代码执行完毕。如果在t1锁定对象锁之后，t2也遇到了synchronized，不要怕，锁已经被占有了，要等t1执行完同步代码块的代码再释放锁之后，t2才会执行。**     ==()中放的共享对象一定要是多个需要排队的线程的共享对象==
>
>    ![image-20220125160137394](../typora-pic/image-20220125160137394.png)
>
>    对象是共享的，那么对象的实例对象也是共享的，只要是==对象==，就可以占有
>
>    如果是synchronized("abc")  那么所有线程都会同步
>
> java**中的三大变量**：局部(栈中) 静态(方法区) 实例(堆 )   ==局部变量永远都不存在线程安全问题==，因为局部变量在栈内，一个线程一个栈，而方法区和堆只有一个，都是多线程共享的，所以可能存在线程安全问题

> ==编程模型==
>
> - 异步编程模型
>   - 多线程并发，谁也不等谁
> - 同步编程模型
>   - 排队执行

## 扩大同步范围的缺点

> 不仅可以直接在取钱方法体内使用同步机制，也可以直接在调用取钱方法的时候使用同步机制，如：sychronized(act){act.withDraw(5000)}   ==这样扩大了同步范围，但是代码执行效率降低了==

## 实例方法上使用Synchronized(缺点 和优点)

> synchronized修饰实例变量，public synchronized void withDraw 是将==this锁住了==
>
> 缺点:
>
> - 这种方式不灵活  一直锁住this
> - 这种方式会无缘无故扩大同步范围，从而降低代码执行效率
>
> 优点：
>
> - 代码少了，所以共享对象是this，并且需要同步的代码块是整个方法体，那么建议实例方法使用synchronized

## StringBuilder 和 StringBuffer的线程安全问题

> 如果不存在线程安全问题，局部变量使用StringBuilder，因为StringBuilder不需要做同步处理，效率较高

## synchronized的三种用法

> 1. 同步代码块
> 2. 实例方法使用synchronized
> 3. 在静态方法上使用synchronized，表示找==类锁==，类锁只有一把，和对象的个数没有关系(第三种是为了保证==静态变量的安全==)
>
> **synchronized面试题**
>
> ```java
> public class Test
> {
> 	public static void main (String[] args) throws Exception{
> 		Myclass m=new Myclass();
> 		MyThread t1=new MyThread(m);
> 		MyThread t2=new MyThread(m);
> 		t1.setName("t1");
> 		t2.setName("t2");
> 		t1.start();
> 		try{Thread.sleep(1000);	}
> 		catch (Exception e){}
> 		t2.start();
> 	}
> }
> class MyThread extends Thread{
> 	Myclass m=new Myclass();
> 	public MyThread(Myclass m){
> 		this.m=m;
> 	}
> 	public void run() {
> 		if(Thread.currentThread().getName().equals("t1")){
> 			m.doSome();
> 		}
> 		if(Thread.currentThread().getName().equals("t2")){
> 			m.doOther();
> 		}
> 	}
> }
> class Myclass
> {
> 	public synchronized void doSome() {
> 		System.out.println("doSome开始");
> 		try{Thread.sleep(1000*10);}
> 		catch (Exception e){}
> 		System.out.println("doSome结束");
> 	}
> 	public void doOther(){
> 		System.out.println("doOther开始");
> 		System.out.println("doOther结束");
> 	}
> }
> //t1执行doSome并不影响t2执行doOther，因为doOther方法并不涉及到线程安全问题
> //那么如果在doOther方法上加synchronized，那么就需要等待t1线程调用完doSome
> //如果创建两个Myclass对象分别给t1和t2，那么两者之间也需要等待
> ```
>
> ==类锁面试题，根据上边代码修改得到==
>
> ```java
> public class Test
> {
> 	public static void main (String[] args) throws Exception{
> 		Myclass m=new Myclass();
> 		MyThread t1=new MyThread(m);
> 		MyThread t2=new MyThread(m);
> 		t1.setName("t1");
> 		t2.setName("t2");
> 		t1.start();
> 		try{Thread.sleep(1000);	}
> 		catch (Exception e){}
> 		t2.start();
> 	}
> }
> class MyThread extends Thread{
> 	Myclass m=new Myclass();
> 	public MyThread(Myclass m){
> 		this.m=m;
> 	}
> 	public void run() {
> 		if(Thread.currentThread().getName().equals("t1")){
> 			m.doSome();
> 		}
> 		if(Thread.currentThread().getName().equals("t2")){
> 			m.doOther();
> 		}
> 	}
> }
> class Myclass
> {
> 	public synchronized static void doSome() {
> 		System.out.println("doSome开始");
> 		try{Thread.sleep(1000*10);}
> 		catch (Exception e){}
> 		System.out.println("doSome结束");
> 	}
> 	public synchronized static void doOther(){
> 		System.out.println("doOther开始");
> 		System.out.println("doOther结束");
> 	}
> }
> //synchronized放在静态方法上，是锁类锁的，所以线程t1直接锁住了Myclass类，t2需要等t1的doSome方法结束之后才可以占用Myclass锁
> ```
>
> **==目前所学的“对象锁”和“类锁”都是排他锁，之后还会有互斥锁==**

## 死锁

> 死锁代码要求会写，面试有时会让你写一个死锁
>
> ```java
> //死锁
> public class Test{
> 	public static void main(String[] args){
>         Object o1=new Object();
>         Object o2=new Object();
>         Thread t1=new MyThread1(o1,o2);
>         Thread t2=new MyThread2(o1,o2);       
>         t1.start();
>         t2.start(); 
>     }    
> }
> class MyThread1 extends Thread{
>     Object o1;
>     Object o2;
>     public MyThread1(Object o1,Object o2){
>         this.o1=o1;
>         this.o2=o2;
>     }
>     public void run(){
>         synchronized(o1){
> 			try{Thread.sleep(1000);}catch (Exception e){}
>             synchronized(o2){ }
>         }
>     }
> }
> class MyThread2 extends Thread{
>     Object o1;
>     Object o2;
>     public MyThread2(Object o1,Object o2){
>         this.o1=o1;
>         this.o2=o2;
>     }
>     public void run(){
>         synchronized(o2){
> 			try{Thread.sleep(1000);}
> 			catch (Exception e){}
>             synchronized(o1){
>             }
>         }
>     }
> }
> ```
>
> 所以在开发过程中，synchronized最好不要嵌套使用

## 开发中怎么解决线程安全问题(考虑synchronized的低效率)

> 1. 尽量使用局部变量代替“实例变量”和“静态变量”
> 2. 如果必须使用实例变量，那么可以考虑创建多个对象，这样实例变量的内存就不共享了
> 3. 如果不能使用局部变量，对象也不能创建多个，那么只能选择synchronized线程同步机制

## 守护线程

> 除了守护线程(如gc垃圾回收线程)，其他都是==用户线程==，当所有的用户线程结束的时候，守护线程也就结束了
>
> ```java
> //守护线程的实现
> class Test{
>     Thread t=new BakcThread();
>     t.setDaemon();//设置成守护线程，主线程(用户线程)结束，守护线程也就结束
>     t.start();
> }
> class BackThread extends Thread{
>     public void run(){
>         int i=0;
>         while(true){
>             System.out.println(Thread.currentThread().getName()+"--->"+(++i));
>             try{
>                 Thread.sleep(1000);
>             }catch(InterruptedException e){
>                 e.printStackTrace();
>             }
>         }
>     }
> }
> ```
>
> 

## 定时器

> 定时器的作用：间隔特定的时间，执行特定的程序
>
> 首先可以想到sleep()，不过这种方法是最原始的，现在都是java.util.Timer，不过在实际的开发过程中，目前使用最多的是==Spring框架中提供的SpringTask框架==(其底层原理就是Timer)，简单配置即可完成定时器的任务
>
> ```java
> import java.util.*;
> import java.text.*;
> public class Test{
>     public static void main(String[] args) throws Exception{
>         Timer timer=new Timer();
>         SimpleDateFormat sdf=new SimpleDateFormat("yyyy-MM-dd HH:mm:ss SSS");
>         //Date firstTime=sdf.parse("2022-01-25 21:42:22 222");
> 		Date firstTime=new Date();
>         timer.schedule(new TimerTask(){int i=0;
>         						public void run(){++i;
>                                     System.out.println("定时器第"+i+"次执行，执行时间										是"+sdf.format(new Date()));}
>         },firstTime,1000*10);
>     }
> }
> ```
>
> TimerTask是一个接口，任务接口，该接口实现了Runnable接口，也是一个线程
>
> 定时器的方法：==schedule(TimerTask task,Date date,long time)==

## 线程实现的第三种方法

> 实现Callable接口(jdk8新特性)，这种方式==可以获取线程的返回值==，之前的实现Runnable和继承Thread的run方法的返回值都是void，如果希望完成任务的线程结束之后可以返回东西，就需要这种实现了Callable接口的线程实现方式。
>
> 实现过程见以下代码：
>
> ```java
> import java.util.concurrent.Callable;
> import java.util.concurrent.ExecutionException;
> import java.util.concurrent.FutureTask;
> public class ThreadThird {
>     public static void main(String[] args) {
>         FutureTask task=new FutureTask(new Callable() {
>             @Override
>             public Object call() throws Exception {//call方法相当于是run方法，只不过有返回值
>                 System.out.println("call method begin");
>                 Thread.sleep(1000*3);
>                 System.out.println("call method end");
>                 return 100+200;
>             }
>         });
>         Thread t=new Thread(task);
>         t.start();
>         //那么如何获得线程的返回值呢？
>         try {
>             Object o=task.get();
>             System.out.println(o);
>         } catch (InterruptedException e) {
>             e.printStackTrace();
>         } catch (ExecutionException e) {
>             e.printStackTrace();
>         }
>         System.out.println("aaa");//这里的代码需要等t线程结束才可以运行，所以get()方法会导致当前线程阻塞
>     }
> }
> 
> ```
>
> **线程实现的第三种方法的优缺点：**
>
> - 优点：可以获取线程的执行结果
> - 缺点：效率比较低，get()方法会让当前线程阻塞，效率较低

## wait和notify(生产者和消费者模式)

> wait方法和notify方法，不是线程的方法，是java中任何对象的方法，因为是Object的方法
>
> wait()的作用：
>
> ```java
> Object o=new Object();
> o.wait();//让正在o对象上活动的线程进入等待状态，无期限等待，直到唤醒为止
> ```
>
> notify()的作用：o.notify() 唤醒o对象上等待的线程
>
> notifyAll()的作用：唤醒o对象上所有等待的线程
>
> ==生产者和消费者模式==
>
> 注意：o.wait()  让o对象上活动的线程t进入等待状态，并释放掉t线程之前占有的o对象的锁
>
> ​			o.notify() 让o对象上等待的锁唤醒，但是不释放之前占有o对象的锁
>
> ```java
> //KuCun  对象是共享对象，对于生产者产品为偶数，或满100个就停止生产，对于消费者为奇数或为0时停止消费
> public class ShengChanZheXiaoFeiZhe {
>     public static void main(String[] args) {
>         KuCun c=new KuCun(50);
>         Thread  ts=new ThreadShengChan(c);
>         Thread tx=new ThreadXiaoFei(c);
>         ts.setName("生产者线程");
>         tx.setName("消费者线程");
>         ts.start();
>         tx.start();
>     }
> }
> class ThreadShengChan extends Thread{
>     KuCun c;
>     public ThreadShengChan(KuCun c ) {
>         this.c = c;
>     }
>     @Override
>     public void run() {
>         while(true){
>             synchronized (c){
>                 if(c.getC()%2==0||(c.getC()==100)){
>                     try {
>                         c.wait();
>                     } catch (InterruptedException e) {
>                         e.printStackTrace();
>                     }
>                 }
>                 c.setC(c.getC()+1);;
>                 try {
>                     Thread.sleep(1000*2);
>                 } catch (InterruptedException e) {
>                     e.printStackTrace();
>                 }
>                 System.out.println(Thread.currentThread().getName()+"当前库存---->"+c.getC());
>                 c.notifyAll();
>             }
>         }
>     }
> }
> class ThreadXiaoFei extends Thread{
>     KuCun c;
> 
>     public ThreadXiaoFei(KuCun c) {
>         this.c = c;
>     }
>     @Override
>     public void run() {
>         while (true){
>             synchronized (c){
>                 if (c.getC()==0||(c.getC()%3==0)){
>                     try {
>                         c.wait();
>                     } catch (InterruptedException e) {
>                         e.printStackTrace();
>                     }
>                 }
>                 c.setC(c.getC()-2);
>                 try {
>                     Thread.sleep(1000*2);
>                 } catch (InterruptedException e) {
>                     e.printStackTrace();
>                 }
>                 System.out.println(Thread.currentThread().getName()+"当前库存---->"+c.getC());
>                 c.notifyAll();
>             }
> 
>         }
>     }
> }
> class KuCun{
>     private Integer c;
>     public KuCun(Integer c){
>         this.c=c;
>     }
>     public Integer getC() {
>         return c;
>     }
>     public void setC(Integer c) {
>         this.c = c;
>     }
> }
> ```

# 反射

## 反射机制相关的类

> java.lang.reflect.*;
>
> java.lang.Class   代表字节码文件  代表一个类型
>
> java.lang.reflect.Method   代表字节码中的方法字节码
>
> java.lang.reflect.Constructor    代表字节码中的构造方法字节码
>
> java.lang.reflect.Field    代表字节码中的属性字节码

## 获取Class的三种方式

> ```java
> /*方式1
> Class.forName()
> 1、静态方法
> 2、方法的参数是一个字符串，并且字符串是一个完整的类名
> 3、完整类名必须带有包名，不可省略
> */
> class Test{
>     public static void main(String[] args){
>         Class c1=Class.forName("java.lang.String");//c1代表的就是java/lang/String.class
>         Class c2=Class.forName("java.util.Date");
>         Class c3=Class.forName("java.lang.System");
>     }
> }
> /*方式2
> java中任何一个对象都有一个方法：getClass()
> */
> String s="abc";
> Class c=s.getClass();//Class 内存储的内存地址是加载到方法区的String字节码文件
> /*方式3
>  java语言中任何一种类型，包括基本数据类型，他都有.class属性 如String.class
> */
> ```

## 通过反射实例化对象

> ```java
> Class c=Class.forName("java.lang.String");
> String s=c.newInstance("aaa");//newInstance会调用User这个类的无参数构造方法，不会调用有参构造
> //newInstance已经过时了 从jdk9开始
> ```
>
> 反射机制更加灵活，灵活在哪里呢？
>
> ```
> 配合属性配置文件和流进行实现
> ```
>
> Spring SpringMVC MyBatis
>
> Spring Structs Hibernate

## Class.forName()

> 这个方法会导致类加载，从而会执行静态代码块的内容，**所以以后只要希望一个类的静态代码块执行，其他代码一律不执行，可以使用Class.forName()**

## 路径问题

> 以Module为根得到的相对路径==移植性==太差
>
> 这里说一种即使代码换了位置，路径也是通用的方式，前提是：这个文件必须在类路径下【==凡是在src下的路径都是类路径==】
>
> ```java
> String path=Thread.currentThread().getContextClassLoader().getResource("").getPath();
> InputStream in=new FileInputStream(path);
> Properties pro=new Properties();
> pro.load(in);
> in.close();
> String className=pro.getProperty("className");
> 
> InputStream reader=Thread.currenThread().getContextClassLoader().getResourceAsStream("");
> /*
> getContextClassLoader() 是线程对象的方法，可以获取到当前线程的类加载器对象
> getResource()是类加载器对象的方法，当前线程的类加载器默认从类的根路径加载资源
> */
> ```

## 资源绑定器

> java.util包下提供了一个资源绑定器，便于获取属性配置文件的内容
>
> 同样的，这里的属性配置文件也要放在类路径下，资源绑定器只能绑定==.properties文件==
>
> ```java
> ResourceBundle bundle=ResourceBundle.getBundle("filename")  //文件名不加后缀properties
> String className=bundle.getString("文件中的Key")
> ```

## 类加载器

> 类加载器就是**专门负责加载类的命令/工具(ClassLoader)**
>
> JDK中自带的3中类加载器
>
> - 启动类加载器
>
>   ​		代码再开始执行之前，会将所有需要的类加载到JVM中，首先通过”启动类加载器“加载，加载的是==jre\lib\rt.jar==内的类。
>
> - 扩展类加载器
>
>   ​		 如果**启动类加载器**加载不到的时候，就是用**扩展类加载器**，加载的是==jre\lib\ext==目录下的包
>
> - 应用类加载器
>
>    		如果启动类加载器和扩展类加载器都加载不出来，就会启动应用类加载器，也就是在classpath下找对应的包资源

> ==***双亲委派机制***==
>
> 启动类加载器  String
>
> 扩展类加载器
>
> 应用类加载器	String(你自己写了一个String类，但是JVM加载不到)
>
> ==java中为了保证类加载的安全，使用了双亲委派机制，“父”是启动类加载器，“母”是扩展类加载器==，如果都加载不到，就去应用类加载器中加载，直到加载到为止

## 获取Field

> ```java
> //********************获取属性
> //先获取整个类
> Class class=Class.forName("类名");
> class.getName();//获取完整类名
> class.getSimpleName();//获取简类名
> //获取类中所有的Field
> Field[] fields=class.getFields();//获取的是所有public的属性
> Field f=fields[0];
> String fieldName=f.getName();
> 
> Field[] fields=class.getDeclaredFields();//获取所有属性
> //*********************获取属性的类型   Field对象是包括修饰符列表的  如：pirvate String name;
>  Class fieldType=f.getType();
>  String fieldName=fieldType.getName();
> //*********************获取属性的修饰符列表
> String modifiersName=Modifier.toString（f.getModifiers()）;//getModifiers的返回值是int,实际是每个修饰符的代号，怎么将代号转换成字符串呢？使用到Modifier类中的静态方法------toString(int mod)即可
> ```
>
> 获取单个属性
>
> ```java
> //通过反射机制调用参数
> Class c=Class.forName("className");
> Object obj=c.newInstance();
> Field noFiedl=c.getDeclaredField("no");
> noField.set(obj,222);
> noField.get(obj);//获取对应属性的值 如果属性的值是private修饰的 那么只能打破封装
> //打破封装代码
> noField.setAccessible(true);
> ```

## Method(超级重点)

> ==可变长参数==：以一个静态方法为例
>
> ```java
> public static void main(String[] args){m(1);m(1,2);m(12,3,2);}
> public static void m(int... args){System.out.println("m方法执行了！")}
> //可变长参数只能出现在参数列表的最后一个，并且可变长参数一个参数列表里只能有一个
> //可以把可变长参数看成  一个数组 它也有Length属性
> public static void m1(String... args){
>     for(int i=0;i<args.length;i++){
>         System.out.println(args[i]);
>     }
> }
> ```

> ==如何反射Method==
>
> ```java
> Method[] method=Class.forName("").getDeclaredMethods();
> Method m=method[0];
> m.getReturnType().getSimpleName();//返回值类型
> m.getName();//返回方法名
> m.getParameterTypes();//获取方法的修饰符列表
> ```
>
> ```java
> //通过反射调用方法
> Class c=Class.forName("");
> Object obj=c.newInstance();
> Method login=c.getDeclaredMethod("方法名",Class<?>... agrs)//这里传入的是参数的类型	
> Object retValue=login.invoke(obj,"admin","123");
> //反射方法四要素
> //1、login方法
> //2、obj对象
> //3、admin 123 实参
> //4、retValue 返回值
> ```

## 反射constructor

> ```java
> //通过反射机制创建对象  使用构造方法   newInstance()的调用有参构造
> Class c=Class.forName("");
> Constuctor con=c.getDelcaredConstructor(对应的形参类型);
> Object obj=con.newInstance(对应的实参);
> 
> //newInstance()调用无参构造的正确方式
> Object newObj=con.newInstance();
> ```

## 反射继承的父类和实现的父接口

> ```java
> Class stringClass=Class.forName("java.lang.String");
> Class supoerClass=stringClass.getSuperclass();  //getSuperclass
> //获取所有的接口
> Class[] interfaces=stringClass.getInterfaces();
> ```

## 反射的缺点

> noFiedl.setAccessible(true);容易打破封装，给不法分子留下机会

# 注解(annotation)

## 注解基本概念

> ```java
> /*
> 1、注解是一种引用数据类型，编译之后也生成xxx.class文件
> 2、定义注释的语法格式：
> 		[修饰符列表] @interface 注解类型名{}
> 3、注解怎么使用？  @注解类姓名
> 	注解可以出现在类上、属性上、方法上、变量上，还可以出现在注解上
> */
> public @interface MyAnnocation{
>     
> }
> @MyAnnocation
> class Dosome{
>     @MyAnnocation
>     int a;
>     @MyAnnocation
>     public static void dosome(){}
>     @MyAnnocation
>     public void doOther(){@MyAnnocation int a;}
> }
> @MyAnnocation
> interface Myinterface{}
> @MyAnnocation
> enum Season{}
> @MyAnnocation
> @interface OtherAnnocation{}
> ```

## JDK自带的几个注解

> java.lang报下的注解
>
> 1. Deprceated 已过时
>
>    ```java
>    @Documented
>    @Retention(RetentionPolicy.RUNTIME)
>    @Target(value={CONSTRUCTOR, FIELD, LOCAL_VARIABLE, METHOD, PACKAGE, MODULE, PARAMETER, TYPE})
>    public @interface Deprecated {
>        String since() default "";
>        boolean forRemoval() default false;
>    }
>    
>    ```
>
>    
>
> 2. Override 方法覆盖
>
>    ​	override这个注解是给编译器看的，和运行阶段无关，凡是带有这个注解的方法，编译阶段都要检查是否重写了父类的方法，如果没有编译器就会报错。
>
>    ```java
>    //Override注解的源代码
>    @Target(ElementType.METHOD)//这两个标注“注解类型”的“注解”称为元注解
>    @Retention(RetentionPolicy.SOURCE)
>    public @interface Override{}
>    //Target注解 用来标注“被标注注解”可以出现在哪些位置上
>    
>    //Retention注解 用来标注“被标注注解”最终保存到哪
>    @Retention(RetentionPolicy.SOURCE)//表示该注解被保留在java源文件中
>    @Retention(RetentionPolicy.CLASS)//表示该注解被保留在class文件中
>    @Retention(RetentionPolicy.RUNTIME)//表示该注解被保留在class文件中，并且可以通过反射机制进行读取
>    ```

## 注解中怎么定义属性

> ```java
> @interface MyAnnotation{
>     String name() default "ss";//如果这里的属性名是value，并且只有一个属性，那么使用该注解的时候，赋值可以省略属性名
>     String[] ss();
>     Sesson[] season();
> }
> public class Test{
>     @MyAnnotation(name="sss",ss="ssss")//数组只有一个元素{}可以省略
>     public void doSome(){}
> }
> ```
>
> 注解的属性类型可以是：byte short int lang float double boolean char ==String Class 枚举类型==，以及这些类型的数组形式

## 反射注解

> ```java
> import java.lang.annotation.*;
> public class ReflectAnnotation{
>     public static void main(String[] args) throws Exception{
>         Class c= Class.forName("com.wzx.reflect.MyAnnotation");
>         System.out.println(c.isAnnotationPresent(MyAnnotation.class));//看看这个类上是否有注解
>     }
> }
> @MyAnnotation
> @Target({ElementType.TYPE,ElementType.METHOD})
> @Retention(RetentionPolicy.RUNTIME)
> @interface MyAnnotation{}
> 
> 
> //反射得到注解对象
> Class c= Class.forName("com.wzx.reflect.MyAnnotation");
> System.out.println(c.isAnnotationPresent(MyAnnotation.class));
> if (c.isAnnotationPresent(MyAnnotation.class)){
>     MyAnnotation myAnnotation= (MyAnnotation) c.getAnnotation(MyAnnotation.class);
>     System.out.println(myAnnotation);
> }
> //注解的属性可以直接    引用点  
> 
> 
> 
> //通过反射获取注解对象属性的值
> public class Test{
>     @MyAnnotation(username="admin",password="123")
>     public void doSome(){}
>     public static void main(String args){
>        	//获取Test的doSome方法上的注解信息
>         Class c=Class.forName("Test");
>         Method method=c.getDeclaredMethod("doSome");
>         if(method.isAnnotationPresent(MyAnnotation.class)){
>             System.out.println(method.Annotation.username+method().Annotation.password());
>         }
>     }
> }
> ```

## 注解在开发中的作用(举例说明)

> 需求：假设有一个叫id的注解，要求这个注解只能出现在类上，并且类有这个注解的时候必须有一个int类习惯的id，如果没有就报错，如果有则正常执行！
>
> ```java
> import java.lang.annotation.ElementType;
> import java.lang.annotation.Retention;
> import java.lang.annotation.RetentionPolicy;
> import java.lang.annotation.Target;
> import java.lang.reflect.Field;
> public class AnnotationTest {
>     public static void main(String[] args) throws Exception{
>         try {
>             panDuan("com.wzx.reflect.User1");
>         }catch (MyException me){
>             System.out.println(me.getMessage());
>         }
>     }
>     public static void panDuan(String add) throws ClassNotFoundException, MyException {
>         Class userClass=Class.forName(add);
>         if (userClass.isAnnotationPresent(ID.class)){
>             //当一个类有@ID注解的时候  要判断这个类里是否有int id
>             Field[] fields=userClass.getDeclaredFields();
>             for (Field field:fields){
>                 if ("id".equals(field.getName())&&("int".equals(field.getType().getSimpleName()))){
>                     System.out.println("语法正确");
>                     return;
>                 }
>             }
>             throw new MyException("语法错误");
>         }
>     }
> }
> class MyException extends Exception{
>     public MyException() {
>     }
>     public MyException(String message) {
>         super(message);
>     }
> }
> @Target(ElementType.TYPE)
> @Retention(RetentionPolicy.RUNTIME)
> @interface ID
> }
> @ID
> class User1{
>     int id;
>     String name;
>     String password;
> }
> ```
>
> 注解在开发中到底有什么用？
>
> 

# 常见运行时异常

> 类型转换异常   ***java.lang.ClassCastException***
>
> 空指针异常   ***java.lang.NullPointException***
>
> 数组越界异常  ***java.lang.ArrayIndexOutOfBoundsException***
>
> 数字格式化异常    ***java.lang.NumberFormatException***
>
> 分母为零异常  ***java.lang.ArithmeticException***
>
> 集合内容发生变化，没有重新获取iterator时  ***java.util.ConcurrentModificationException***   ==因为迭代器类似一个照相机，看到的都是集合获取迭代器时候的集合内容==



==和equals的区别

> ==是对内存地址进行对比
>
> equals是对对象的内容进行对比

# 常用的方法

> 数组拷贝：***==System.arrayCopy==***(==源目标==，==源开始下标==，==目标==，==目标开始下表==，==拷贝长度==)
>
> 获取当前毫秒数(自1970年0000 至今)：***==System.currentTimeMillis()==***;
>
> 建议启动垃圾回收：***==System.gc()==***
>
> 推出JVM：***==System.exit(0)==***
>
> ==Arrays:==
>
> - 排序：Arrays.sort(int[] a);
>
> - 二分查找：Arrays.binarySearch(int[] a，对应元素);    如果返回结果是-1说明不存在改元素
>
> ==String:==
>
> - char charAt(int index )     "中国人".charAt(1)    ---->  "国"
> - int compareTo(String anotherString)    两个字符串相等即为0  其他看大小  差值
> - boolean contains(CharSequence s)
> - boolean endWith(String suffix)
> - startsWith
> - boolean equalsIgnoreCase(String anotherString)   判断两个字符串是否相等，并且不区分大小写
> - String toLowerCase()    转换到小写
> - toUpperCase()
> - String trim()   去除字符串前后空白
> -  byte[ ]   getByte(String s)    将字符串转成byte数组
> - char[ ]    toCharArray()   将字符串转成char数组
> - int indexOf(String s)   判断s子字符串在某个串中第一次出现处的索引
> - lastIndexOf
> - boolean isEmpty()   判断字符串是否为空
> - int leagth()    判断数组长度是length属性，判断字符串长度是length()方法
> - String replace(charSquence target,charSquence replacement)
> - String[ ] split(String regex)     "1998-02-16".split("-");
> - String subString(int beginIndex)   截取字符串
> - String subString(int beginIndex,int endIndex)   截取字符串   包括beginIndex  不包括endIndex
> - ==静态方法==   String.valueOf(非字符串)   将非字符串转换成字符串   
>
> ==Integer==
>
> - static int parseInt(String s)    字符串转换成int   所以也有parseDouble
>
> ==引用.valueOf()== 将括号内的类型转换成 对应的包装类   

# 常用类

## String

> 字符串从出生到死亡都是不能变的
>
> ==在JDK中双引号括起来的字符串都是放在方法区的字符串常量池的==为了提高执行效率
>
> ```java
> String s=new String("xy");
> //双引号的字符串都是在方法区的字符串常量池中，这里是在堆中创建对象，并且指向字符串常量池中的"xy"
> ```
>
> **==垃圾回收器是不会释放常量的==**
>
> String类重写了equals方法，所以对于字符串对象的相同比较直接使用equals方法即可
>
> ```java
> //以下程序创建了几个对象
> public class Test{
>     public static void main(String[] args){
>         String a=new String("aaa");
>         String b=new String("aaa");
>     }
> }
> //以上程序一共创建了3个对象  分别是一个字符串常量池对象和两个堆String对象
> ```
>
> String的构造方法可以使用==byte[],char[]==

## StringBuffer

> 思考：在实际开发中，如果需要频繁对字符串进行拼接，有什么问题？
>
> ​	==在对字符串进行 拼接得时候，每一次拼接都会产生新字符串，从而方法区占用内存，造成空间浪费==
>
> 如果需要频繁进行字符串拼接，要使用java自带得类：java.lang.StringBuffer和java.lang.StringBuilder
>
> - ==StringBuffer(线程安全的)==
>
>   - 初始化容量是16(字符串缓冲对象)
>
>   - StringBuffer的底层是byte数组   ==String的底层也是byte数组，不过是被final修饰了的byte数组==
>
>   - StringBuffer中有一个方法，可以追加字符串  即==append==   这个append方法已经被==重载==可以传入很多参数类型
>
>   - **==如何优化Stringbuffer的性能==**
>
>     ​       在创建StringBuffer的时候尽可能给定一个初始化容量，最好减少底层数组的扩容次数
>
> - ==Stringbuilder==
>
>   - 初始容量也是16

## 基础类型对应的8个包装类

> | 基本数据类型 | 包装类型            |
> | ------------ | ------------------- |
> | byte         | java.lang.Byte      |
> | short        | java.lang.Short     |
> | int          | java.lang.Integer   |
> | long         | java.lang.Long      |
> | float        | java.lang.Float     |
> | double       | java.lang.Double    |
> | boolean      | java.lang.Boolean   |
> | char         | java.lang.Character |
>
> 八种包装类型中，Boolean和Character的父类是java.lang.Object，其他的都是java.lang.Number
>
> Number类有多个方法，Number类是一个抽象类，不可以实例化对象
>
> - intValue floatValue doubleValue byteValue   longValue  shortValue  ==这几个方法都是负责拆箱的==
>
> ==基本数据类型  --->   引用数据类型(装箱)==
>
> ==引用数据类型  --->   基本数据类型(拆箱)==

> ==**Integer**==
>
> Integer的构造方法可以装箱String    public Integer(String s)
>
> Integer的最大值和最小值   Integer.MAX_VALUE  最小值Integer.MIN_VALUE
>
> ==自动装箱==    Integer i=10;    ==自动拆箱==   int a=i;
>
> 有了自动拆箱之后  Number类中的方法就用不着了
>
> ==Integer类型的i   +1   会自动将Integer转换成int类型，  自动拆箱机制==   运算才会拆箱 ==不会拆箱
>
> ==Java为了提高执行效率，将-128----127之间的包装对象提前创建好，挡在了"整数型常量池"中==这个整数型常量池在Integer类加载的时候就会实现
>
> ==缓存==   优点：效率高   缺点：耗费内存    大型项目的重要优化手段就是cache缓存机制
>
> ```java
> //String int 和Integer之间的转换
> class Test
> {
> 	public static void main(String[] agrs){
> 		//String  ---->  int
> 		String s1="100";
> 		int i1=Integer.parseInt(s1);
> 		//int ----->String
> 		String s2=String.valueOf(i1);
> 		String s3=i1+" ";
> 		//int -->Integer
> 		Integer ie=i1;
> 		//Integer-->int
> 		int i2=ie;
> 		//String--->Integer
> 		Integer ie1=Integer.valueOf(s1);
> 		//Integer--->String
> 		String s4=String.valueOf(ie1);
> 	}
> }
> ```
>
> 

## 日期相关类

> java.util.Date   
>
> SimpleDateFormat  专门用于日期格式化的类  java.text包下的
>
> ```java
> import java.util.Date;
> import java.text.SimpleDateFormat;
> class Test
> {
> 	public static void main(String[] args){
> 		Date nowTime=new Date();
> 		SimpleDateFormat sdf=new SimpleDateFormat("yyyy-MM-dd HH:mm:ss SSS");
> 		System.out.println(sdf.format(nowTime));
> 	}
> }  //Date--->String
> ```
>
>  以上是将日期对象转换成了字符串
>
> 如何将字符串转化成对应的Date对象  使用==SimpleDateFormat.parse==方法
>
> ```java
> String time="2009-12-30 08:08:08 888";
> SimpleDateFormate sdf=new SimpleDateFormate("yyyy-MM-dd hh:MM:ss SSS");
> Date d=sdf.parse(time);
> //String ---> Date
> ```
>
> 获取自1970年1月1日  00：00：00 000到当前系统时间的总毫秒数
>
> ```java
> System.currentTimeMillis();
> ```
>
> ```java
> Date d=new Date(System.currentTimeMillis());
> //  毫秒  --->  Date
> ```

## 数字相关类

> 数字格式化
>
> java.text.DecimalFormat专门负责数字格式化
>
> - #代表任何数字   ，代表千分位    . 代表小数点   0代表不够的时候补0
>
> 数字格式化和日期格式化
>
> ```java
> DecimalFormat df=new DecimalFormat("###，###.0000")
>     df.format();
> ```

> ==BigDecimal==属于大数据，精度极高，用在财务软件当中
>
> ```java
> BigDecimal v1=new BigDecimal(100);
> BigDecimal v2=new BigDecimal(200);
> System.out.println(v1.add(v2));
> //BigDecimal的toString重写了    subtract乘法   divide除法
> ```

## Random

> ```java
> Random random=new Random();//创建随机数对象
> int num=random.nextInt();//随机产生一个int类型取值范围内的数字  还有重载的nextInt()形参输入对应的int边界，范围不包含形参中
> System.out.println(num);
> ```

## Enum

> 为什么要用枚举，因为boolean类型无法再满足需求，可能性在两个之上
>
> ==如果要判断的结果有多种可能性，那么建议使用枚举==
>
> - ==枚举，一枚一枚可以列举出来的，才建议使用枚举类型==
> - ==枚举编译之后生成的也是class文件==
> - ==枚举是一种引用数据类型==
> - ==枚举中的每个值都可以看作是常量==
>
> ```java
> class Test{
>     public static Result divide(int a,int b){
>         try{
>             int c=a/b;
>             return Result.SUCCESS;
>         }catch(Exception e){
>             return Result.FAIL;
>         }
>     } 
> }
> enum Result{
>     SUCCESS,FAIL
> }
> ```
>
> 