# C#核心

![C#核心内容.jpg (294×723)](https://raw.githubusercontent.com/aiqingo/aiqingo.github.io/refs/heads/main/image/C%23核心内容.jpg)

![七大原则](https://raw.githubusercontent.com/aiqingo/aiqingo.github.io/refs/heads/main/image/%E4%B8%83%E5%A4%A7%E5%8E%9F%E5%88%99.jpg)

![封装继承多态.jpg (1171×310)](https://raw.githubusercontent.com/aiqingo/aiqingo.github.io/refs/heads/main/image/封装继承多态.jpg)

### 封装

```
封装
**封装**：将属性和方法组合到类中，并限制对这些数据的直接访问。封装的目的是隐藏类的内部实现细节，只通过公共接口暴露必要的操作，这样可以保护数据，减少外部干扰，提高代码的安全性和可维护性
``` 

### 继承

```
 继承
将一堆类中的一些共有的“成员”单独抽取出来，作为一个父类，然后这一堆类继承这个父类，共享父类的资源，优化代码结构， 让类与类之间产生关系，提高代码的复用性， 便于阅读，为“ 多态” 提供前提
```

### 多态

```
有多态之前必须要有继承，只有多个类同时继承了同一个类，才有多态这样说法。在继承关系的前提下，实例化出不同的对象，这些对象调用相同的方法，但是却表现出不同的行为，这就叫做多态。

在 C#语言中体现多态有三种方式：虚方法，抽象类， 接口。
```



1. ### 类和对象

   ```
   类申明实例
       //这个类是用来形容人类的
       //命名：用帕斯卡命名法 
       //注意：同一个语句块中的不同类 不能重名
       /*class Person
       {
           //特征——成员变量
           //行为——成员方法
           //保护特征——成员属性
   
           //构造函数和析构函数
           //索引器
           //运算符重载
           //静态成员
       }*/
   ```

2. ### 访问修饰符

   ```
    //public - 公共 内外部访问
       //private - 私有 内部访问
       //protected - 保护 内部和子类访问
       //internal - 内部的 只有在同一个程序集的文件中，内部类型或者是成员才可以访问
   ```

   

3. ### 成员变量

   ```
   成员变量
       //基本规则
       //1.申明在类语句块中
       //2.用来描述对象的特征
       //3.可以是任意变量类型
       //4.数量不做限制
       //5.是否赋值根据需求来定
       
       //性别枚举
       enum E_SexType
       {
           Man,
           Woman,
       }
       //位置结构体
       struct Position
       {
   
       }
       //宠物类
       class Pet
       {
   
       }
       class Person
       {
           //特征——成员变量
           //姓名
           public string name = "唐老狮";
           //年龄
           public int age;
           //性别
           public E_SexType sex;
           //女朋友
           //如果要在类中申明一个和自己相同类型的成员变量时
           //不能对它进行实例化
           public Person gridFriend;
           //朋友
           public Person[] boyFriend;
           //位置
           public Position pos;
           //宠物
           private Pet pet = new Pet();
       }
       查看默认值
       default(变量类型) 就能得到默认值
               Console.WriteLine(default(Person));
   ```

   

4. ### 成员函数

   ```
    //基本概念
       //成员方法(函数) 用来表现对象行为
       // 1.申明在类语句块中
       // 2.是用来描述对象的行为的
       // 3.规则和函数申明规则相同
       // 4.受到访问修饰符规则影响
       // 5.返回值参数不做限制
       // 6.方法数量不做限制
   
       //注意：
       //1.成员方法不要加static关键字
       //2.成员方法 必须实例化出对象 再通过对象来使用 相当于该对象执行了某个行为
       //3.成员方法 受到访问修饰符影响
   
    class Person
       {
           /// <summary>
           /// 判断是否成年
           /// </summary>
           /// <returns></returns>
           public bool IsAdult()
           {
               return age >= 18;
           }
   
           /// <summary>
           /// 说话的行为
           /// </summary>
           /// <param name="str">说话的内容</param>
           public void Speak(string str)
           {
               Console.WriteLine("{0}说{1}", name, str);
           }
   
           /// <summary>
           /// 添加朋友的方法
           /// </summary>
           /// <param name="p">传入新朋友</param>
           public void AddFriend(Person p)
           {
               if(friends == null)
               {
                   friends = new Person[] { p };
               }
               else
               {
                   //新建一个 房子数组
                   Person[] newFriends = new Person[friends.Length + 1];
                   //搬家
                   for (int i = 0; i < friends.Length; i++)
                   {
                       newFriends[i] = friends[i];
                   }
                   //把新加的朋友放到最后一个
                   newFriends[newFriends.Length - 1] = p;
                   //地址重定向
                   friends = newFriends;
               }
           }
   
           public string name;
           public int age;
           //朋友们
           public Person[] friends;
       }
   ```

   

5. ### 构造析构函数

   ```
   构造函数
       //基本概念
       //在实例化对象时 会调用的用于初始化的函数
       //如果不写 默认存在一个无参构造函数
   
       //构造函数的写法
       //1.没有返回值
       //2.函数名和类名必须相同
       //3.没有特殊需求时 一般都是public的
       class Person
       {
           public string name;
           public int age;
   
           //类中是允许自己申明无参构造函数的
           //结构体是不允许
           public Person()
           {
               name = "唐老狮";
               age = 18;
           }
   
           public Person(int age)
           {
               //this代表当前调用该函数的对象自己 
               this.age = age;
           }
   
           public Person(string name)
           {
               this.name = name;
           }
   
           //可以通过this 重用构造函数代码
           //访问修饰符 构造函数名(参数列表):this(参数1,参数2....)
           public Person(int age, string name):this(age + 10)
           {
               Console.WriteLine("Person两个参数构造函数调用");
           }
   
           //当引用类型的堆内存被回收时，会调用该函数
           //对于需要手动管理内存的语言（比如C++），需要在析构函数中做一些内存回收处理
           //但是C#中存在自动垃圾回收机制GC
           //所以我们几乎不会怎么使用析构函数。除非你想在某一个对象被垃圾回收时，做一些特殊处理
           //注意：
           //在Unity开发中析构函数几乎不会使用，所以该知识点只做了解即可
   
           //基本语法
           // ~类名()
           // {
           // }
           //当引用类型的堆内存被回收时
           //析构函数 是当垃圾 真正被回收的时候 才会调用的函数
           ~Person()
           {
   
           }
       }
   
       //4.构造函数可以被重载
       //5.this代表当前调用该函数的对象自己
   
       //注意：
       // 如果不自己实现无参构造函数而实现了有参构造函数
       // 会失去默认的无参构造
   ```

   

6. ### 垃圾回收

   ```
   垃圾回收机制
       //垃圾回收，英文简写GC（Garbage Collector）
       //垃圾回收的过程是在遍历堆(Heap)上动态分配的所有对象
       //通过识别它们是否被引用来确定哪些对象是垃圾，哪些对象仍要被使用
       //所谓的垃圾就是没有被任何变量，对象引用的内容
       //垃圾就需要被回收释放
   
       //垃圾回收有很多种算法，比如
       //引用计数(Reference Counting)
       //标记清除(Mark Sweep)
       //标记整理(Mark Compact)
       //复制集合(Copy Collection)
   
       //注意：
       //GC只负责堆(Heap)内存的垃圾回收
       //引用类型都是存在堆(Heap)中的，所以它的分配和释放都通过垃圾回收机制来管理
   
       //栈(Stack)上的内存是由系统自动管理的
       //值类型在栈(Stack)中分配内存的，他们有自己的生命周期，不用对他们进行管理，会自动分配和释放
   
       //C#中内存回收机制的大概原理
       //0代内存     1代内存     2代内存
       //代的概念：
       //代是垃圾回收机制使用的一种算法（分代算法）
       //新分配的对象都会被配置在第0代内存中
       //每次分配都可能会进行垃圾回收以释放内存(0代内存满时) 
   
       //在一次内存回收过程开始时，垃圾回收器会认为堆中全是垃圾，会进行以下两步
       //1.标记对象 从根（静态字段、方法参数）开始检查引用对象，标记后为可达对象，未标记为不可达对象
       //  不可达对象就认为是垃圾
       //2.搬迁对象压缩堆  （挂起执行托管代码线程） 释放未标记的对象 搬迁可达对象 修改引用地址
   
       //大对象总被认为是第二代内存  目的是减少性能损耗，提高性能
       //不会对大对象进行搬迁压缩  85000字节（83kb）以上的对象为大对象
       
        //手动触发垃圾回收的方法 
               //一般情况下 我们不会频繁调用
               //都是在 Loading过场景时 才调用
               GC.Collect();
   ```

7. ### 成员属性

   ```
   成员属性的基本语法
       // 访问修饰符 属性类型 属性名
       // {
       //     get{}
       //     set{}
       // }
       class Person
       {
           private string name;
           private int age;
           private int money;
           private bool sex;
   
           //属性的命名一般使用 帕斯卡命名法
           public string Name
           {
               get
               {
                   //可以在返回之前添加一些逻辑规则 
                   //意味着 这个属性可以获取的内容
                   return name;
               }
               set
               {
                   //可以在设置之前添加一些逻辑规则 
                   // value 关键字 用于表示 外部传入的值
                   name = value;
               }
           }
           #region   成员属性中 get和set前可以加访问修饰符
           // 注意
           // 1.默认不加 会使用属性申明时的访问权限
           // 2.加的访问修饰符要低于属性的访问权限
           // 3.不能让get和set的访问权限都低于属性的权限
           #endregion
           public int Money
           {
               get
               {
                   //解密处理
                   return money - 5;
               }
               set
               {
                   //加密处理
                   money = value + 5;
               }
           }
   
           #region  get和set可以只有一个
           //注意：
           //只有一个时  没必要在前面加访问修饰符
           //一般情况下 只会出现 只有 get的情况 基本不会出现只有set
           public bool Sex
           {
               get
               {
                   return sex;
               }
               //set
               //{
               //    sex = value;
               //}
           }
           #endregion
   
           #region   自动属性
           //作用：外部能得不能改的特征
           //如果类中有一个特征是只希望外部能得不能改的 又没什么特殊处理
           //那么可以直接使用自动属性
           public float Height
           {
               //没有再get和set中写逻辑的需求或者想法
               get;
               private set;
           }
           #endregion
   
       }
         //总结
       //1.成员属性概念：一般是用来保护成员变量的
       //2.成员属性的使用和变量一样 外部用对象点出
       //3.get中需要return内容 ； set中用value表示传入的内容
       //4.get和set语句块中可以加逻辑处理
       //5.get和set可以加访问修饰符，但是要按照一定的规则进行添加
       //6.get和set可以只有一个
       //7.自动属性是属性语句块中只有get和set，一般用于 外部能得不能改这种情况
   ```

8. ### 索引器

   ```
   索引器语法
       //访问修饰符 返回值 this[参数类型 参数名, 参数类型 参数名.....]
       //{
       //      内部的写法和规则和索引器相同
       //      get{}
       //      set{}
       //}
       class Person
       {
           private string name;
           private int age;
           private Person[] friends;
   
           private int[,] array;
   
           #region   索引器可以重载
           //重载的概念是——函数名相同 参数类型、数量、顺序不同
           public int this[int i, int j]
           {
               get
               {
                   return array[i, j];
               }
               set
               {
                   array[i, j] = value;
               }
           }
   
           public string this[string str]
           {
               get
               {
                   switch (str)
                   {
                       case "name":
                           return this.name;
                       case "age":
                           return age.ToString();
                   }
                   return "";
               }
           }
           #endregion
   
           public Person this[int index]
           {
               
               get
               {
                   //可以写逻辑的 根据需求来处理这里面的内容
                   #region   索引器中可以写逻辑
                   if( friends == null ||
                       friends.Length - 1 < index)
                   {
                       return null;
                   }
                   #endregion
                   return friends[index];
               }
               set
               {
                   //value代表传入的值
                   //可以写逻辑的 根据需求来处理这里面的内容
                   if( friends == null )
                   {
                       friends = new Person[] { value };
                   }
                   else if(index > friends.Length - 1)
                   {
                       //自己定了一个规则 如果索引越界 就默认把最后一个朋友顶掉
                       friends[friends.Length - 1] = value;
                   }
                   friends[index] = value;
               }
           }
   
       }
   ```

9. ### 静态成员

   ```
   静态成员基本概念
       //静态关键字 static
       //用static修饰的 成员变量、方法、属性等
       //称为静态成员
   
     class Test
       {
           public const float G = 9.8f;
   
           //静态成员变量
           static public float PI = 3.1415926f;
           //成员变量
           public int testInt = 100;
   
           //静态成员方法
           public static float CalcCircle(float r)
           {
               #region 静态函数中不能使用非静态成员
               //成员变量只能将对象实例化出来后 才能点出来使用 不能无中生有
               //不能直接使用 非静态成员 否则会报错
               //Console.WriteLine(testInt);
               Test t = new Test();
               Console.WriteLine(t.testInt);
               #endregion
               //πr²
               return PI * r * r;
           }
           //成员方法
           public void TestFun()
           {
               Console.WriteLine("123");
               #region 非静态函数可以使用静态成员
               Console.WriteLine(PI);
               Console.WriteLine(CalcCircle(2));
               #endregion
           }
       }
       为什么可以直接点出来使用
       //记住！
       //程序中是不能无中生有的
       //我们要使用的对象，变量，函数都是要在内存中分配内存空间的
       //之所以要实例化对象，目的就是分配内存空间，在程序中产生一个抽象的对象
   
       //静态成员的特点
       //程序开始运行时 就会分配内存空间。所以我们就能直接使用。
       //静态成员和程序同生共死
       //只要使用了它，直到程序结束时内存空间才会被释放
       //所以一个静态成员就会有自己唯一的一个“内存小房间”
       //这让静态成员就有了唯一性
       //在任何地方使用都是用的小房间里的内容，改变了它也是改变小房间里的内容。
       静态成员对于我们的作用
       //静态变量：
       //1.常用唯一变量的申明 
       //2.方便别人获取的对象申明
       //静态方法：
       //常用的唯一的方法申明 比如 相同规则的数学计算相关函数
       
        常量和静态变量
       //const（常量）可以理解为特殊的static（静态）
       //相同点
       //他们都可以通过类名点出使用
       //不同点
       //1.const必须初始化，不能修改 static没有这个规则
       //2.const只能修饰变量、static可以修饰很多
       //3.const一定是写在访问修饰符后面的 ，static没有这个要求
   ```

   

10. 静态类和静态构造函数

    #### 静态类

    ```
    静态类
        //概念
        //用static修饰的类
    
        //特点
        //只能包含静态成员
        //不能被实例化
    
        //作用
        //1.将常用的静态成员写在静态类中 方便使用
        //2.静态类不能被实例化，更能体现工具类的 唯一性
        //比如 Console就是一个静态类
    
        static class Tools
        {
            //静态成员变量
            public static int testIndex = 0;
    
            public static void TestFun()
            {
    
            }
    
            public static int TestIndex
            {
                get;
                set;
            }
        }
       //静态类
      //用static 修饰的类
      //特点
      //只能包含静态成员
      //不能实例化
      //作用
      //工具类
      //拓展方法
    ```

    #### 静态构造函数

    ```
    静态构造函数
        //概念
        // 在构造函数加上 static 修饰
    
        //特点
        //1.静态类和普通类都可以有
        //2.不能使用访问修饰符
        //3.不能有参数  
        //4.只会自动调用一次  
    
        //作用
        //在静态构造函数中初始化 静态变量
    
        //使用
        //1.静态类中的静态构造函数
        static class StaticClass
        {
            public static int testInt = 100;
            public static int testInt2 = 100;
    
            static StaticClass()
            {
                Console.WriteLine("静态构造函数");
                testInt = 200;
                testInt2 = 300;
            }
        }
    
        //2.普通类中的静态构造函数
        class Test
        {
            public static int testInt = 200;
            static Test()
            {
                Console.WriteLine("静态构造");
            }
    
            public Test()
            {
                Console.WriteLine("普通构造");
            }
        }
        
      //静态构造函数
      //用static修饰的构造函数
      //特点
      //静态类和普通类都可以有静态构造函数
      //不能使用访问修饰符
      //不能有参数
      //只会自动调用一次
      //作用
      //初始化静态成员
    ```

11. ### 扩展方法

    ```
    拓展方法基本概念
        //概念 
        //为现有非静态 变量类型 添加 新方法
        //作用
        //1.提升程序拓展性
        //2.不需要再对象中重新写方法
        //3.不需要继承来添加方法
        //4.为别人封装的类型写额外的方法
        //特点
        //1.一定是写在静态类中
        //2.一定是个静态函数
        //3.第一个参数为拓展目标
        //4.第一个参数用this修饰
        
         #region  基本语法
        //访问修饰符 static 返回值 函数名(this 拓展类名 参数名, 参数类型 参数名,参数类型 参数名....)
        #endregion
    
        #region  实例
        static class Tools
        {
            //为int拓展了一个成员方法
            //成员方法 是需要 实例化对象后 才 能使用的
            //value 代表 使用该方法的 实例化对象
            public static void SpeakValue(this int value)
            {
                //拓展的方法 的逻辑
                Console.WriteLine("唐老狮为int拓展的方法" + value);
            }
    
            public static void SpeakStringInfo(this string str, string str2, string str3)
            {
                Console.WriteLine("唐老狮为string拓展的方法");
                Console.WriteLine("调用方法的对象" + str);
                Console.WriteLine("传的参数" + str2 + str3);
            }
    
            public static void Fun3(this Test t)
            {
                Console.WriteLine("为test拓展的方法");
            }
    
        }
        
                int i = 10;
                i.SpeakValue();
                
                
     //总结：
        //概念：为现有的非静态 变量类型 添加 方法
        //作用：
        // 提升程序拓展性
        // 不需要再在对象中重新写方法
        // 不需要继承来添加方法
        // 为别人封装的类型写额外的方法
    
        //特点：
        //静态类中的静态方法
        //第一个参数 代表拓展的目标
        //第一个参数前面一定要加 this
    
        //注意：
        //可以有返回值 和 n个参数
        //根据需求而定
    ```

    

12. ### 运算符重载

    ```
     #region  基本概念
        //概念
        //让自定义类和结构体
        //能够使用运算符
    
        //使用关键字 
        //operator
    
        //特点
        //1.一定是一个公共的静态方法
        //2.返回值写在operator前
        //3.逻辑处理自定义
    
        //作用
        //让自定义类和结构体对象可以进行运算
        //注意
        //1.条件运算符需要成对实现
        //2.一个符号可以多个重载
        //3.不能使用ref和out
        #endregion
    
        #region  基本语法
        //public static 返回类型 operator 运算符(参数列表)
        #endregion
    
        #region 实例
        class Point
        {
            public int x;
            public int y;
    
            public static Point operator +(Point p1, Point p2)
            {
                Point p = new Point();
                p.x = p1.x + p2.x;
                p.y = p1.y + p2.y;
                return p;
            }
    
            public static Point operator +(Point p1, int value)
            {
                Point p = new Point();
                p.x = p1.x + value;
                p.y = p1.y + value;
                return p;
            }
    
            public static Point operator +(int value, Point p1)
            {
                Point p = new Point();
                p.x = p1.x + value;
                p.y = p1.y + value;
                return p;
            }
    
            #region 可重载的运算符
    
            #region 算数运算符
            //注意 符号需要两个参数还是一个参数
            public static Point operator -(Point p1, Point P2)
            {
                return null;
            }
            public static Point operator *(Point p1, Point P2)
            {
                return null;
            }
            public static Point operator /(Point p1, Point P2)
            {
                return null;
            }
            public static Point operator %(Point p1, Point P2)
            {
                return null;
            }
    
            public static Point operator ++(Point p1)
            {
                return null;
            }
            public static Point operator --(Point p1)
            {
                return null;
            }
            #endregion
    
            #region 逻辑运算符
            //注意 符号需要两个参数还是一个参数
            public static bool operator !(Point p1)
            {
                return false;
            }
            #endregion
    
            #region 位运算符
            //注意 符号需要两个参数还是一个参数
            public static Point operator |(Point p1, Point p2)
            {
                return null;
            }
            public static Point operator &(Point p1, Point p2)
            {
                return null;
            }
            public static Point operator ^(Point p1, Point p2)
            {
                return null;
            }
            public static Point operator ~(Point p1)
            {
                return null;
            }
            public static Point operator <<(Point p1, int num)
            {
                return null;
            }
            public static Point operator >>(Point p1, int num)
            {
                return null;
            }
            #endregion
    
            #region 条件运算符
            //1.返回值一般是bool值 也可以是其它的
            //2.相关符号必须配对实现
            public static bool operator >(Point p1, Point p2)
            {
                return false;
            }
            public static bool operator <(Point p1, Point p2)
            {
                return false;
            }
            public static bool operator >=(Point p1, Point p2)
            {
                return false;
            }
            public static bool operator <=(Point p1, Point p2)
            {
                return false;
            }
            public static bool operator ==(Point p1, Point p2)
            {
                return false;
            }
            public static bool operator !=(Point p1, Point p2)
            {
                return false;
            }
            public static bool operator true(Point p1)
            {
                return false;
            }
            public static bool operator false(Point p1)
            {
                return false;
            }
            #endregion
            #endregion
    
            #region 不可重载的运算符
            //逻辑与(&&) 逻辑或(||)
            //索引符 []
            //强转运算符 ()
            //特殊运算符 
            //点.   三目运算符? :  赋值符号=
    
            #endregion
        }
        #endregion
    ```

    

13. ### 内部类和分部类

    ### 内部类

    ```
     #region  内部类
        //概念
        //在一个类中再申明一个类
    
        //特点
        //使用时要用包裹者点出自己
    
        //作用
        //亲密关系的变现
    
        //注意
        //访问修饰符作用很大
    
        class Person
        {
            public int age;
            public string name;
            public Body body;
            public class Body
            {
                Arm leftArm;
                Arm rightArm;
                class Arm
                {
    
                }
            }
        }
        #endregion
    ```

    

    ### 分部类

    ```
     #region  分部类
        //概念
        //把一个类分成几部分申明
    
        //关键字
        //partial
    
        //作用
        //分部描述一个类
        //增加程序的拓展性
    
        //注意
        //分部类可以写在多个脚本文件中
        //分部类的访问修饰符要一致
        //分部类中不能有重复成员
    
        partial class Student
        {
            public bool sex;
            public string name;
    
            partial void Speak();
        }
    
        partial class Student
        {
            public int number;
    
            partial void Speak()
            {
                //实现逻辑
            }
    
            public void Speak(string str)
            {
    
            }
        }
    
        #endregion
    ```

    

14. ### 继承

    ```
    基本语法
        //class 类名 : 被继承的类名
        //{
    
        //}
    ```

15. ### 里氏替换原则

    ```
       #region  基本概念
        // 里氏替换原则是面向对象七大原则中最重要的原则
        // 概念：
        // 任何父类出现的地方，子类都可以替代
        // 重点：
        // 语法表现——父类容器装子类对象,因为子类对象包含了父类的所有内容
        // 作用：
        // 方便进行对象存储和管理
        #endregion
    
        #region   基本实现
        class GameObject
        {
    
        }
    
        class Player:GameObject
        {
            public void PlayerAtk()
            {
                Console.WriteLine("玩家攻击");
            }
        }
    
        class Monster:GameObject
        {
            public void MonsterAtk()
            {
                Console.WriteLine("怪物攻击");
            }
        }
    
        class Boss:GameObject
        {
            public void BossAtk()
            {
                Console.WriteLine("Boss攻击");
            }
        }
        #endregion
    
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("里氏替换原则");
    
                //里氏替换原则 用父类容器 装载子类对象
                GameObject player = new Player();
                GameObject monster = new Monster();
                GameObject boss = new Boss();
    
                GameObject[] objects = new GameObject[] { new Player(), new Monster(), new Boss() };
    
                #region  is和as
                //基本概念 
                // is：判断一个对象是否是指定类对象
                // 返回值：bool  是为真 不是为假
    
                // as：将一个对象转换为指定类对象
                // 返回值：指定类型对象
                // 成功返回指定类型对象，失败返回null
    
                //基本语法
                // 类对象 is 类名   该语句块 会有一个bool返回值 true和false
                // 类对象 as 类名   该语句块 会有一个对象返回值 对象和null
    
                if( player is Player )
                {
                    //Player p = player as Player;
                    //p.PlayerAtk();
                    (player as Player).PlayerAtk();
                }
    
                for (int i = 0; i < objects.Length; i++)
                {
                    if( objects[i] is Player )
                    {
                        (objects[i] as Player).PlayerAtk();
                    }
                    else if( objects[i] is Monster )
                    {
                        (objects[i] as Monster).MonsterAtk();
                    }
                    else if (objects[i] is Boss)
                    {
                        (objects[i] as Boss).BossAtk();
                    }
                }
    
                #endregion
            }
        }
        //总结
        //概念：父类容器装子类对象
        //作用：方便进行对象的存储和管理
        //使用：is和as
        // is 用于判断
        // as 用于转换
        // 注意：不能用子类容器装父类对象
    ```

    

16. ### 继承中的构造函数

    ```
    继承中的构造函数 基本概念
        //特点
        //当申明一个子类对象时
        //先执行父类的构造函数
        //再执行子类的构造函数
    
        //注意：
        //1.父类的无参构造 很重要
        //2.子类可以通过base关键字 代表父类 调用父类构造
        #endregion
    
        #region  继承中构造函数的执行顺序
        // 父类的父类的构造——>。。。父类构造——>。。。——>子类构造
        class GameObject
        {
            public GameObject()
            {
                Console.WriteLine("GameObject的构造函数");
            }
        }
        class Player:GameObject
        {
            public Player()
            {
                Console.WriteLine("Player的构造函数");
            }
        }
        class MainPlayer : Player
        {
            public MainPlayer()
            {
                Console.WriteLine("MainPlayer的构造函数");
            }
        }
        #endregion
    
        #region 父类的无参构造函重要
        //子类实例化时 默认自动调用的 是父类的无参构造 所以如果父类无参构造被顶掉 会报错
        class Father
        {
            //public Father()
            //{
    
            //}
    
            public Father(int i)
            {
                Console.WriteLine("Father构造");
            }
        }
    
    
        class Son:Father
        {
            #region 通过base调用指定父类构造
            public Son(int i) : base(i)
            {
                Console.WriteLine("Son的一个参数的构造");
            }
    
            public Son(int i, string str):this(i)
            {
                Console.WriteLine("Son的两个参数的构造");
            }
            #endregion
        }
    ```

    

17. ### 万物之父Object

    ```
    万物之父
        //万物之父
        //关键字：object
        //概念：
        //object是所有类型的基类，它是一个类（引用类型）
        //作用：
        //1.可以利用里氏替换原则，用object容器装所有对象
        //2.可以用来表示不确定类型，作为函数参数类型
         #region 万物之父的使用
                Father f = new Son();
                if( f is Son )
                {
                    (f as Son).Speak();
                }
    
                //引用类型 
                object o = new Son();
                //用is as 来判断和转换即可
                if( o is Son )
                {
                    (o as Son).Speak();
                }
                //值类型 
                object o2 = 1f;
                //用强转
                float fl = (float)o2;
    
                //特殊的string类型
                object str = "123123";
                string str2 = str as string;
    
                object arr = new int[10];
                int[] ar = arr as int[];
                #endregion
    
                #region  装箱拆箱
                //发生条件
                //用object存值类型（装箱）
                //再把object转为值类型（拆箱）
    
                //装箱
                //把值类型用引用类型存储
                //栈内存会迁移到堆内存中
    
                //拆箱
                //把引用类型存储的值类型取出来
                //堆内存会迁移到栈内存中
    
                //好处：不确定类型时可以方便参数的存储和传递
                //坏处：存在内存迁移，增加性能消耗
    
                //装箱
                object v = 3;
                //拆箱
                int intValue = (int)v;
    
                TestFun(1, 2, 3, 4f, 34.5, "123123", new Son());
                #endregion
    ```

    

18. ### 密封类

    ```
    #region   基本概念
        //密封类 是使用 sealed密封关键字修饰的类
        //作用：让类无法再被继承
        #endregion
    
        #region  实例
        class Father
        {
    
        }
    
        sealed class Son:Father
        {
    
        }
        #endregion
    
        #region  作用
        //在面向对象程序的设计中，密封类的主要作用就是不允许最底层子类被继承
        //可以保证程序的规范性、安全性
        //目前对于大家来说 可能用处不大
        //随着大家的成长，以后制作复杂系统或者程序框架时 便能慢慢体会到密封的作用
        #endregion
    
        //总结
        // 关键字：sealed
        // 作用：让类无法再被继承
        // 意义： 加强面向对象程序设计的 规范性、结构性、安全性
    ```

    

19. ### 多态

    ```
    多态的概念
        // 多态按字面的意思就是“多种状态”
        // 让继承同一父类的子类们 在执行相同方法时有不同的表现（状态）
        // 主要目的
        // 同一父类的对象 执行相同行为（方法）有不同的表现
        // 解决的问题
        // 让同一个对象有唯一行为的特征
    ```

    ```
    多态的实现
        //我们目前已经学过的多态
        //编译时多态——函数重载，开始就写好的
    
        //我们将学习的：
        //运行时多态( vob、抽象函数、接口 )
        //我们今天学习 vob
        //v: virtual(虚函数)
        //o: override(重写)
        //b: base(父类)
    
        class GameObject
        {
            public string name;
            public GameObject(string name)
            {
                this.name = name;
            }
    
            //虚函数 可以被子类重写
            public virtual void Atk()
            {
                Console.WriteLine("游戏对象进行攻击");
            }
        }
    
        class Player:GameObject
        {
            public Player(string name):base(name)
            {
    
            }
    
            //重写虚函数
            public override void Atk()
            {
                //base的作用
                //代表父类 可以通过base来保留父类的行为
                base.Atk();
                Console.WriteLine("玩家对象进行攻击");
            }
        }
    
        class Monster:GameObject
        {
            public Monster(string name):base(name)
            {
    
            }
    
            public override void Atk()
            {
                Console.WriteLine("怪物对象进行攻击");
            }
        }
    ```

    

20. ### 抽象类和抽象方法

    ```
      #region  抽象类
        //概念
        //被抽象关键字abstract修饰的类
        //特点：
        //1.不能被实例化的类
        //2.可以包含抽象方法
        //3.继承抽象类必须重写其抽象方法
    
        abstract class Thing
        {
            //抽象类中 封装的所有知识点都可以在其中书写
            public string name;
    
            //可以在抽象类中写抽象函数
        }
    
        class Water:Thing
        {
    
        }
        #endregion
    
        #region  抽象函数
        //又叫 纯虚方法
        //用 abstract关键字修饰的方法
        //特点：
        //1.只能在抽象类中申明
        //2.没有方法体
        //3.不能是私有的
        //4.继承后必须实现 用override重写
    
        abstract class Fruits
        {
            public string name;
    
            //抽象方法 是一定不能有函数体的
            public abstract void Bad();
    
            public virtual void Test()
            {
                //可以选择是否写逻辑
            }
        }
    
        class Apple : Fruits
        {
            public override void Bad()
            {
                
            }
            //虚方法是可以由我们子类选择性来实现的
            //抽象方法必须要实现
        }
    
        class SuperApple:Apple
        {
    
            //虚方法和抽象方法 都可以被子类无限的 去重写
            public override void Bad()
            {
                base.Bad();
            }
    
            public override void Test()
            {
                base.Test();
            }
        }
    ```

    

21. ### 接口

    ```
    using System;
    
    namespace Lesson19_多态_接口
    {
        #region  接口的概念
        //接口是行为的抽象规范
        //它也是一种自定义类型
        //关键字 ：interface
    
        //接口申明的规范
        //1.不包含成员变量
        //2.只包含方法、属性、索引器、事件
        //3.成员不能被实现
        //4.成员可以不用写访问修饰符，不能是私有的
        //5.接口不能继承类，但是可以继承另一个接口
    
        //接口的使用规范
        //1.类可以继承多个接口
        //2.类继承接口后，必须实现接口中所有成员
    
        //特点：
        //1.它和类的申明类似
        //2.接口是用来继承的
        //3.接口不能被实例化，但是可以作为容器存储对象
        #endregion
    
        #region 接口的申明
        //接口关键字：interface
        //语法：
        // interface 接口名
        // {
        // }
        //一句话记忆：接口是抽象行为的“基类”
        //接口命名规范 帕斯卡前面加个I
    
        interface IFly
        {
            void Fly();
    
            string Name
            {
                get;
                set;
            }
    
            int this[int index]
            {
                get;
                set;
            }
    
            event Action doSomthing;
        }
        #endregion
    
        #region 接口的使用
        //接口用来继承
        class Animal
        {
    
        }
    
        //1.类可以继承1个类，n个接口
        //2.继承了接口后 必须实现其中的内容 并且必须是public的
        class Person : Animal, IFly
        {
            //3.实现的接口函数，可以加v再在子类重写
            public virtual void Fly()
            {
    
            }
    
            public string Name
            {
                get;
                set;
            }
    
            public int this[int index]
            {
                get
                {
                    return 0;
                }
                set
                {
    
                }
            }
    
            public event Action doSomthing;
        }
    
    
        #endregion
    
        #region  接口可以继承接口
        //接口继承接口时  不需要实现
        //待类继承接口后  类自己去实现所有内容
        interface IWalk
        {
            void Walk();
        }
    
        interface IMove : IFly, IWalk
        { 
        }
    
        class Test : IMove
        {
            public int this[int index] { get => throw new NotImplementedException(); set => throw new NotImplementedException(); }
    
            public string Name { get => throw new NotImplementedException(); set => throw new NotImplementedException(); }
    
            public event Action doSomthing;
    
            public void Fly()
            {
                throw new NotImplementedException();
            }
    
            public void Walk()
            {
                throw new NotImplementedException();
            }
        }
        #endregion
    
        #region  显示实现接口
        //当一个类继承两个接口
        //但是接口中存在着同名方法时
        //注意：显示实现接口时 不能写访问修饰符
    
        interface IAtk
        {
            void Atk();
        }
    
        interface ISuperAtk
        {
            void Atk();
        }
    
        class Player : IAtk, ISuperAtk
        {
            //显示实现接口 就是用 接口名.行为名 去实现
            void IAtk.Atk()
            {
                
            }
    
            void ISuperAtk.Atk()
            {
                
            }
    
            public void Atk()
            {
    
            }
        }
    
    
        #endregion
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("接口");
                //4.接口也遵循里氏替换原则
                IFly f = new Person();
    
                IMove im = new Test();
                IFly ifly = new Test();
                IWalk iw = new Test();
    
                IAtk ia = new Player();
                ISuperAtk isa = new Player();
                ia.Atk();
                isa.Atk();
    
                Player p = new Player();
                (p as IAtk).Atk();
                (p as ISuperAtk).Atk();
                p.Atk();
            }
        }
    
        //总结：
        //继承类：是对象间的继承，包括特征行为等等
        //继承接口：是行为间的继承，继承接口的行为规范，按照规范去实现内容
        //由于接口也是遵循里氏替换原则，所以可以用接口容器装对象
        //那么久可以实现 装载各种毫无关系但是却有相同行为的对象
    
        //注意：
        //1.接口值包含 成员方法、属性、索引器、事件，并且都不实现，都没有访问修饰符
        //2.可以继承多个接口，但是只能继承一个类
        //3.接口可以继承接口，相当于在进行行为合并，待子类继承时再去实现具体的行为
        //4.接口可以被显示实现 主要用于实现不同接口中的同名函数的不同表现
        //5.实现的接口方法 可以加 virtual关键字 之后子类 再重写
    }
    
    ```

    

22. ### 密封方法

    ```
     #region  密封方法基本概念
        //用密封关键字sealed 修饰的重写函数
        //作用：让虚方法或者抽象方法之后不能再被重写
        //特点：和override一起出现
        #endregion
    
        #region  实例
        abstract class Animal
        {
            public string name;
            public abstract void Eat();
    
            public virtual void Speak()
            {
                Console.WriteLine("叫");
            }
        }
    
        class Person:Animal
        {
            public override void Eat()
            {
                
            }
    
            public override void Speak()
            {
                
            }
        }
    
        class WhitePerson:Person
        {
            public sealed override void Eat()
            {
                base.Eat();
            }
    
            public sealed override void Speak()
            {
                base.Speak();
            }
        }
    ```

    

23. ### 命名空间

    ```
    命名空间的使用
    //基本语法
    //namespace 命名空间名
    //{
    //  类
    //  类
    //}
    namespace MyGame
    {
        class GameObject
        {
    
        }
    }
    
    关于修饰类的访问修饰符
    //public   —— 命名空间中的类 internal
    //internal —— 只能在该程序集中使用
    //abstract —— 抽象类
    //sealed   —— 密封类
    //partial  —— 分部类
    
    //总结
    //1.命名空间是个工具包 用来管理类的
    //2.不同命名空间中 可以有同名类
    //3.不同命名空间中相互使用 需要using引用命名空间 或者 指明出处
    //4.命名空间可以包裹命名空间
    ```

    

24. ### Object的方法

    ```
    object中的静态方法
                //静态方法 Equals 判断两个对象是否相等
                //最终的判断权，交给左侧对象的Equals方法，
                //不管值类型引用类型都会按照左侧对象Equals方法的规则来进行比较
                Console.WriteLine(Object.Equals(1, 1));
                //Test t = new Test();
                //Test t2 = new Test();
                //Console.WriteLine(Object.Equals(t, t2));
                //静态方法ReferenceEquals
                //比较两个对象是否是相同的引用，主要是用来比较引用类型的对象。
                //值类型对象返回值始终是false。
                //Console.WriteLine(Object.ReferenceEquals(t, t2));
    ```

    ```
    object中的成员方法
                //普通方法GetType
                //该方法在反射相关知识点中是非常重要的方法，之后我们会具体的讲解这里返回的Type类型。
                //该方法的主要作用就是获取对象运行时的类型Type，
                //通过Type结合反射相关知识点可以做很多关于对象的操作。
                Test t = new Test();
                Type type = t.GetType();
                //普通方法MemberwiseClone
                //该方法用于获取对象的浅拷贝对象，口语化的意思就是会返回一个新的对象，
                //但是新对象中的引用变量会和老对象中一致。
                Test t2 = t.Clone();
                Console.WriteLine("克隆对象后");
                Console.WriteLine("t.i = " + t.i);
                Console.WriteLine("t.t2.i = " + t.t2.i);
                Console.WriteLine("t2.i = " + t2.i);
                Console.WriteLine("t2.t2.i = " + t2.t2.i);
    
                t2.i = 20;
                t2.t2.i = 21;
                Console.WriteLine("改变克隆体信息后");
                Console.WriteLine("t.i = " + t.i);
                Console.WriteLine("t.t2.i = " + t.t2.i);
                Console.WriteLine("t2.i = " + t2.i);
                Console.WriteLine("t2.t2.i = " + t2.t2.i);
                #endregion
    ```

    ```
    object中的虚方法
                //虚方法Equals
                //默认实现还是比较两者是否为同一个引用，即相当于ReferenceEquals。
                //但是微软在所有值类型的基类System.ValueType中重写了该方法，用来比较值相等。
                //我们也可以重写该方法，定义自己的比较相等的规则
    
                //虚方法GetHashCode
                //该方法是获取对象的哈希码
                //（一种通过算法算出的，表示对象的唯一编码，不同对象哈希码有可能一样，具体值根据哈希算法决定），
                //我们可以通过重写该函数来自己定义对象的哈希码算法，正常情况下，我们使用的极少，基本不用。
    
                //虚方法ToString
                //该方法用于返回当前对象代表的字符串，我们可以重写它定义我们自己的对象转字符串规则，
                //该方法非常常用。当我们调用打印方法时，默认使用的就是对象的ToString方法后打印出来的内容。
                
    ```

25. ### string相关

    #### 字符串指定位置获取

    ```
    #region  字符串指定位置获取
                //字符串本质是char数组
                string str = "小学生";
                Console.WriteLine(str[0]);
                //转为char数组
                char[] chars = str.ToCharArray();
                Console.WriteLine(chars[1]);
    
                for (int i = 0; i < str.Length; i++)
                {
                    Console.WriteLine(str[i]);
                }
                #endregion
    ```

    #### 字符串拼接

    ```
        #region  字符串拼接
                str = string.Format("{0}{1}", 1, 3333);
                Console.WriteLine(str);
                #endregion
    ```

    #### 正向查找字符位置

    ```
     #region  正向查找字符位置
                str = "正向查找字符位置！";
                int index = str.IndexOf("找");
                Console.WriteLine(index);
    
                index = str.IndexOf("吊");
                Console.WriteLine(index);
                #endregion
    ```

    #### 反向查找指定字符串位置

    ```
      #region 反向查找指定字符串位置
                str = "反向查找指定字符串位置位置";
    
                index = str.LastIndexOf("位置");
                Console.WriteLine(index);
    
                index = str.LastIndexOf("位置");
                Console.WriteLine(index);
                #endregion
    ```

    #### 移除指定位置后的字符

    ```
    #region  移除指定位置后的字符
                str = "移除指定位置后的字符";
                str.Remove(4);
                Console.WriteLine(str);
                str = str.Remove(4);
                Console.WriteLine(str);
    
                //执行两个参数进行移除
                //参数1 开始位置
                //参数2 字符个数
                str = str.Remove(1, 1);
                Console.WriteLine(str);
                #endregion
    ```

    ####  替换指定字符串

    ```
       #region  替换指定字符串
                str = "替换指定字符串";
                str.Replace("替换", "老炮儿");
                Console.WriteLine(str);
                str = str.Replace("替换", "老炮儿");
                Console.WriteLine(str);
                #endregion
    ```

    #### 大小写转换

    ```
        #region   大小写转换
                str = "ksdfasdfasfasdfsasdfasdf";
                str.ToUpper();
                Console.WriteLine(str);
                str = str.ToUpper();
                Console.WriteLine(str);
    
                str.ToLower();
                Console.WriteLine(str);
                str = str.ToLower();
                Console.WriteLine(str);
                #endregion
    ```

    #### 字符串截取

    ```
      #region 字符串截取
                str = "字符串截取字符串截取";
                //截取从指定位置开始之后的字符串
                str.Substring(2);
                Console.WriteLine(str);
                str = str.Substring(2);
                Console.WriteLine(str);
    
                //参数一 开始位置
                //参数二 指定个数
                //不会自动的帮助你判断是否越界 你需要自己去判断
                str = str.Substring(2, 2);
                Console.WriteLine(str);
                #endregion
    ```

    #### 字符串切割

    ```
      #region 字符串切割
                str = "1_1|2_2|3_3|5_1|6_1|7_2|8_3";
                string[] strs = str.Split('|');
                for (int i = 0; i < strs.Length; i++)
                {
                    Console.WriteLine(strs[i]);
                }
                #endregion
    ```

    

26. ### StringBuilder相关

    ```
      #region  StringBuilder
                //C#提供的一个用于处理字符串的公共类 
                //主要解决的问题是：
                //修改字符串而不创建新的对象,需要频繁修改和拼接的字符串可以使用它，可以提升性能
                //使用前 需要引用命名空间
    
                #region 初始化 直接指明内容
                StringBuilder str = new StringBuilder("123123123");
                Console.WriteLine(str);
                #endregion
    
                #region 容量
                //StringBuilder存在一个容量的问题，每次往里面增加时 会自动扩容
                //获得容量
                Console.WriteLine(str.Capacity);
                //获得字符长度
                Console.WriteLine(str.Length);
                #endregion
    
                #region 增删查改替换
                //增
                str.Append("4444");
                Console.WriteLine(str);
                Console.WriteLine(str.Length);
                Console.WriteLine(str.Capacity);
    
                str.AppendFormat("{0}{1}", 100, 999);
                Console.WriteLine(str);
                Console.WriteLine(str.Length);
                Console.WriteLine(str.Capacity);
                //插入
                str.Insert(0, "小学生");
                Console.WriteLine(str);
                //删
                str.Remove(0, 10);
                Console.WriteLine(str);
                //清空
                //str.Clear();
                //Console.WriteLine(str);
                //查
                Console.WriteLine(str[1]);
                //改
                str[0] = 'A';
                Console.WriteLine(str);
                //替换
                str.Replace("1", "小");
                Console.WriteLine(str);
    
                //重新赋值 StringBuilder
                str.Clear();
                str.Append("123123");
                Console.WriteLine(str);
                //判断StringBuilder是否和某一个字符串相等
                if( str.Equals("12312") )
                {
                    Console.WriteLine("相等");
                }
                #endregion
    
       
    ```

    

27. ### 结构体和类的区别

    ```
     #region 区别概述
                //结构体和类最大的区别是在存储空间上的，因为结构体是值，类是引用，
                //因此他们的存储位置一个在栈上，一个在堆上，
                //通过之前知识点的学习，我相信你能够从此处看出他们在使用的区别——值和引用对象在赋值时的区别。
    
                //结构体和类在使用上很类似，结构体甚至可以用面向对象的思想来形容一类对象。
                //结构体具备着面向对象思想中封装的特性，但是它不具备继承和多态的特性，因此大大减少了它的使用频率。
                //由于结构体不具备继承的特性，所以它不能够使用protected保护访问修饰符。
                #endregion
    
                #region 细节区别
                //1.结构体是值类型，类是引用类型
                //2.结构体存在栈中，类存在堆中
                //3.结构体成员不能使用protected访问修饰符，而类可以
                //4.结构体成员变量申明不能指定初始值，而类可以
                //5.结构体不能申明无参的构造函数，而类可以
                //6.结构体申明有参构造函数后，无参构造不会被顶掉
                //7.结构体不能申明析构函数，而类可以
                //8.结构体不能被继承，而类可以
                //9.结构体需要在构造函数中初始化所有成员变量，而类随意
                //10.结构体不能被静态static修饰（不存在静态结构体），而类可以
                //11.结构体不能在自己内部申明和自已一样的结构体变量，而类可以
                #endregion
    
                #region 结构体的特别之处
                //结构体可以继承 接口 因为接口是行为的抽象
                #endregion
    
                #region 如何选择结构体和类
                //1.想要用继承和多态时，直接淘汰结构体，比如玩家、怪物等等
                //2.对象是数据集合时，优先考虑结构体，比如位置、坐标等等
                //3.从值类型和引用类型赋值时的区别上去考虑，比如经常被赋值传递的对象，并且
                //改变赋值对象，原对象不想跟着变化时，就用结构体。比如坐标、向量、旋转等等
                #endregion
            }
    ```

28. ### 抽象类和接口

    ```
    #region 知识回顾
                //抽象类和抽象方法
                //abstract修饰的类和方法
                //抽象类 不能实例化
                //抽象方法只能在抽象类中申明 是个纯虚方法 必须在子类中实现
    
                //接口
                //interface 自定义类型
                //是行为的抽象
                //不包含成员变量
                //仅包含方法、属性、索引器、事件，成员都不能实现，建议不写访问修饰符，默认public
                #endregion
    
                #region 知识点一 相同点
                //1.都可以被继承
                //2.都不能直接实例化
                //3.都可以包含方法申明
                //4.子类必须实现未实现的方法
                //5.都遵循里氏替换原则
                #endregion
    
                #region 知识点二 区别
                //1.抽象类中可以有构造函数；接口中不能
                //2.抽象类只能被单一继承；接口可以被继承多个
                //3.抽象类中可以有成员变量；接口中不能
                //4.抽象类中可以申明成员方法，虚方法，抽象方法，静态方法；接口中只能申明没有实现的抽象方法
                //5.抽象类方法可以使用访问修饰符；接口中建议不写，默认public
                #endregion
    
                #region 如何选择抽象类和接口
                //表示对象的用抽象类，表示行为拓展的用接口
                //不同对象拥有的共同行为，我们往往可以使用接口来实现
                //举个例子：
                //动物是一类对象，我们自然会选择抽象类；而飞翔是一个行为，我们自然会选择接口。
                #endregion
            }
    ```

