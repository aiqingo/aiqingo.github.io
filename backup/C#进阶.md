# C#进阶

![C#进阶](https://raw.githubusercontent.com/aiqingo/aiqingo.github.io/refs/heads/main/image/C%23%E8%BF%9B%E9%98%B6%E5%86%85%E5%AE%B9.jpg)

数据结构是什么

```
数据结构 
//数据结构
//数据结构是计算机存储、组织数据的方式（规则）
//数据结构是指相互之间存在一种或多种特定关系的数据元素的集合
//比如自定义的一个 类 也可以称为一种数据结构 自己定义的数据组合规则
//不要把数据结构想的太复杂
//简单点理解，就是人定义的 存储数据 和 表示数据之间关系 的规则而已
//常用的数据结构（前辈总结和制定的一些经典规则）
//数组、栈、队列、链表、树、图、堆、散列表
```

```
线性表
//线性表是一种数据结构，是由n个具有相同特性的数据元素的有限序列
//比如数组、ArrayList、Stack、Queue、链表等等
```



1. ### ArrayList

   ```
   #region  ArrayList的本质
   //ArrayList是一个C#为我们封装好的类，
   //它的本质是一个object类型的数组，
   //ArrayList类帮助我们实现了很多方法，
   //比如数组的增删查改
   #endregion
   
   #region  申明
   //需要引用命名空间using System.Collections;
   ArrayList array = new ArrayList();
   #endregion
   
   #region  增删查改
   #region 增
   array.Add(1);
   array.Add("123");
   array.Add(true);
   array.Add(new object());
   array.Add(new Test());
   array.Add(1);
   array.Add(true);
   ArrayList array2 = new ArrayList();
   array2.Add(123);
   //范围增加（批量增加 把另一个list容器里面的内容加到后面）
   array.AddRange(array2);
   array.Insert(1, "12345676");
   Console.WriteLine(array[1]);
   #endregion
   
   #region 删
   //移除指定元素 从头找 找到删
   array.Remove(1);
   //移除指定位置的元素
   array.RemoveAt(2);
   //清空
   //array.Clear();
   
   #endregion
   
   #region 查
   //得到指定位置的元素
   Console.WriteLine(array[0]);
   
   //查看元素是否存在
   if( array.Contains("1234") )
   {
       Console.WriteLine("存在123");
   }
   
   //正向查找元素位置
   //找到的返回值 是位置 找不到 返回值 是-1
   int index = array.IndexOf(true);
   Console.WriteLine(index);
   
   Console.WriteLine(array.IndexOf(false));
   
   //反向查找元素位置
   //返回时从头开始的索引数
   index = array.LastIndexOf(true);
   Console.WriteLine(index);
   #endregion
   
   #region 改
   Console.WriteLine(array[0]);
   array[0] = "999";
   Console.WriteLine(array[0]);
   #endregion
   
   #endregion
   
   #region 遍历
   //长度
   Console.WriteLine(array.Count);
   //容量
   //避免产生过多的垃圾
   Console.WriteLine(array.Capacity);
   Console.WriteLine("***********************");
   for (int i = 0; i < array.Count; i++)
   {
       Console.WriteLine(array[i]);
   }
   Console.WriteLine("***********************");
   //迭代器遍历
   foreach (object item in array)
   {
       Console.WriteLine(item);
   }
   
   #endregion
   
   #region  装箱拆箱
   //ArrayList本质上是一个可以自动扩容的object数组，
   //由于用万物之父来存储数据，自然存在装箱拆箱。
   //当往其中进行值类型存储时就是在装箱，当将值类型对象取出来转换使用时，就存在拆箱。
   //所以ArrayList尽量少用，之后我们会学习更好的数据容器。
   
   int k = 1;
   array[0] = k;//装箱
   k = (int)array[0];//拆箱
   #endregion
   ```

   

2. ### Stack 栈

   ```
         #region Stack的本质
   //Stack（栈）是一个C#为我们封装好的类
   //它的本质也是object[]数组，只是封装了特殊的存储规则
   
   //Stack是栈存储容器，栈是一种先进后出的数据结构
   //先存入的数据后获取，后存入的数据先获取
   //栈是先进后出
   #endregion
   
   #region  申明
   //需要引用命名空间 System.Collections
   Stack stack = new Stack();
   #endregion
   
   #region  增取查改
   
   #region 增
   //压栈
   stack.Push(1);
   stack.Push("123");
   stack.Push(true);
   stack.Push(1.2f);
   stack.Push(new Test());
   
   #endregion
   
   #region 取
   //栈中不存在删除的概念
   //只有取的概念
   //弹栈
   object v = stack.Pop();
   Console.WriteLine(v);
   
   v = stack.Pop();
   Console.WriteLine(v);
   #endregion
   
   #region 查
   //1.栈无法查看指定位置的 元素
   //  只能查看栈顶的内容
   v = stack.Peek();
   Console.WriteLine(v);
   v = stack.Peek();
   Console.WriteLine(v);
   
   //2.查看元素是否存在于栈中
   if( stack.Contains("123") )
   {
       Console.WriteLine("存在123");
   }
   
   #endregion
   
   #region 改
   //栈无法改变其中的元素 只能压(存)和弹（取）
   //实在要改 只有清空
   stack.Clear();
   Console.WriteLine(stack.Count);
   stack.Push("1");
   stack.Push(2);
   stack.Push("哈哈哈");
   #endregion
   
   #endregion
   
   #region   遍历
   //1.长度
   Console.WriteLine(stack.Count);
   
   //2.用foreach遍历
   //  而且遍历出来的顺序 也是从栈顶到栈底
   foreach(object item in stack)
   {
       Console.WriteLine(item);
   }
   
   //3.还有一种遍历方式
   //  将栈转换为object数组
   //  遍历出来的顺序 也是从栈顶到栈底
   object[] array = stack.ToArray();
   for (int i = 0; i < array.Length; i++)
   {
       Console.WriteLine(array[i]);
   }
   
   Console.WriteLine(stack.Count);
   //4.循环弹栈
   while( stack.Count > 0 )
   {
       object o = stack.Pop();
       Console.WriteLine(o);
   }
   Console.WriteLine(stack.Count);
   #endregion
   
   #region   装箱拆箱
   //由于用万物之父来存储数据，自然存在装箱拆箱。
   //当往其中进行值类型存储时就是在装箱
   //当将值类型对象取出来转换使用时，就存在拆箱。
   #endregion
   
   
   泛型栈
   Stack<int> stack = new Stack<int>();
   ```

   

3. ### Queue 队列

   ```
     #region   申明
   //需要引用命名空间 System.Collections
   Queue queue = new Queue();
   #endregion
   
   #region   增取查改
   
   #region 增
   queue.Enqueue(1);
   queue.Enqueue("123");
   queue.Enqueue(1.4f);
   queue.Enqueue(new Test());
   #endregion
   
   #region 取
   //队列中不存在删除的概念
   //只有取的概念 取出先加入的对象
   object v = queue.Dequeue();
   Console.WriteLine(v);
   v = queue.Dequeue();
   Console.WriteLine(v);
   #endregion
   
   #region 查
   //1.查看队列头部元素但不会移除
   v = queue.Peek();
   Console.WriteLine(v);
   v = queue.Peek();
   Console.WriteLine(v);
   
   //2.查看元素是否存在于队列中
   if( queue.Contains(1.4f) )
   {
       Console.WriteLine("队列中存在1.4f");
   }
   
   #endregion
   
   #region 改
   //队列无法改变其中的元素 只能进出队列
   //实在要改 只有清
   Console.WriteLine(queue.Count);
   queue.Clear();
   queue.Enqueue(1);
   queue.Enqueue(2);
   queue.Enqueue(3);
   #endregion
   
   #endregion
   
   #region   遍历
   //1.长度
   Console.WriteLine(queue.Count);
   //2.用foreach遍历
   foreach (object item in queue)
   {
       Console.WriteLine(item);
   }
   //3.还有一种遍历方式
   //  将队列转换为object数组
   object[] array = queue.ToArray();
   for (int i = 0; i < array.Length; i++)
   {
       Console.WriteLine(array[i]);
   }
   
   //4.循环出列
   while(queue.Count>0)
   {
       object o = queue.Dequeue();
       Console.WriteLine(o);
   }
   Console.WriteLine(queue.Count);
   #endregion
   
   #region   装箱拆箱
   //由于用万物之父来存储数据，自然存在装箱拆箱。
   //当往其中进行值类型存储时就是在装箱
   //当将值类型对象取出来转换使用时，就存在拆箱。
   #endregion
   
   泛型队列
   Queue<object> queue = new Queue<object>();
   ```

   

4. ### Hashtable

   ```
     #region   Hashtalbe的本质
   //Hashtable（又称散列表） 是基于键的哈希代码组织起来的 键/值对
   //它的主要作用是提高数据查询的效率
   //使用键来访问集合中的元素
   #endregion
   
   #region   申明
   //需要引用命名空间 System.Collections
   Hashtable hashtable = new Hashtable();
   #endregion
   
   #region  增删查改
   
   #region 增
   hashtable.Add(1, "123");
   hashtable.Add("123", 2);
   hashtable.Add(true, false);
   hashtable.Add(false, false);
   //注意：不能出现相同键
   #endregion
   
   #region 删
   //1.只能通过键去删除
   hashtable.Remove(1);
   //2.删除不存在的键 没反应
   hashtable.Remove(2);
   
   //3.或者直接清空
   hashtable.Clear();
   hashtable.Add(1, "123");
   hashtable.Add(2, "1234");
   hashtable.Add(3, "123");
   hashtable.Add("123123", 12);
   #endregion
   
   #region 查
   //1.通过键查看值
   //  找不到会返回空
   Console.WriteLine(hashtable[1]);
   Console.WriteLine(hashtable[4]);//null
   Console.WriteLine(hashtable["123123"]);
   
   //2.查看是否存在
   //根据键检测
   if( hashtable.Contains(2) )
   {
       Console.WriteLine("存在键为2的键值对");
   }
   if( hashtable.ContainsKey(2) )
   {
       Console.WriteLine("存在键为2的键值对");
   }
   
   //根据值检测
   if( hashtable.ContainsValue(12) )
   {
       Console.WriteLine("存在值为12的键值对");
   }
   #endregion
   
   #region 改
   //只能改 键对应的值内容 无法修改键
   Console.WriteLine(hashtable[1]);
   hashtable[1] = 100.5f;
   Console.WriteLine(hashtable[1]);
   #endregion
   
   #endregion
   
   #region   遍历
   //得到键值对 对数
   Console.WriteLine(hashtable.Count);
   
   //1.遍历所有键
   foreach (object item in hashtable.Keys)
   {
       Console.WriteLine("键："+item);
       Console.WriteLine("值："+hashtable[item]);
   }
   
   //2.遍历所有值
   foreach (object item in hashtable.Values)
   {
       Console.WriteLine("值：" + item);
   }
   
   //3.键值对一起遍历
   foreach (DictionaryEntry item in hashtable)
   {
       Console.WriteLine("键：" + item.Key + "值：" + item.Value);
   }
   
   //4.迭代器遍历法
   IDictionaryEnumerator myEnumerator = hashtable.GetEnumerator();
   bool flag = myEnumerator.MoveNext();
   while (flag)
   {
       Console.WriteLine("键：" + myEnumerator.Key + "值：" + myEnumerator.Value);
       flag = myEnumerator.MoveNext();
   }
   #endregion
   
   #region   装箱拆箱
   //由于用万物之父来存储数据，自然存在装箱拆箱
   //当往其中进行值类型存储时就是在装箱
   //当将值类型对象取出来转换使用时，就存在拆箱
   #endregion
   ```

   

5. ### 泛型

   ```
    #region   泛型是什么
   //泛型实现了类型参数化，达到代码重用目的
   //通过类型参数化来实现同一份代码上操作多种类型
   
   //泛型相当于类型占位符
   //定义类或方法时使用替代符代表变量类型
   //当真正使用类或者方法时再具体指定类型
   #endregion
   
   #region   泛型分类
   //泛型类和泛型接口
   //基本语法：
   //class 类名<泛型占位字母>
   //interface 接口名<泛型占位字母>
   
   //泛型函数
   //基本语法：函数名<泛型占位字母>(参数列表)
   
   //注意：泛型占位字母可以有多个，用逗号分开
   #endregion
   
   #region   泛型类和接口
   
   class TestClass<T>
   {
   public T value;
   }
   
   class TestClass2<T1,T2,K,M,LL,Key,Value>
   {
   public T1 value1;
   public T2 value2;
   public K value3;
   public M value4;
   public LL value5;
   public Key value6;
   public Value value7;
   }
   
   interface TestInterface<T>
   {
   T Value
   {
   get;
   set;
   }
   }
   
   class Test : TestInterface<int>
   {
   public int Value { get => throw new NotImplementedException(); set => throw new NotImplementedException(); }
   }
   
   #endregion
   
   #region 泛型方法
   //1.普通类中的泛型方法
   
   class Test2
   {
   public void TestFun<T>( T value)
   {
   Console.WriteLine(value);
   }
   
   public void TestFun<T>()
   {
   //用泛型类型 在里面做一些逻辑处理
   T t = default(T);
   }
   
   public T TestFun<T>(string v)
   {
   return default(T);
   }
   
   public void TestFun<T,K,M>(T t, K k, M m)
   { 
   }
   }
   
   //2.泛型类中的泛型方法
   class Test2<T>
   {
   public T value;
   
   public void TestFun<K>(K k)
   {
   Console.WriteLine(k);
   }
   
   //这个不叫泛型方法 因为 T是泛型类申明的时候 就指定 在使用这个函数的时候 
   //我们不能再去动态的变化了
   public void TestFun(T t)
   {
   
   }
   }
   
   #endregion
   
   #region   泛型的作用
   //1.不同类型对象的相同逻辑处理就可以选择泛型
   //2.使用泛型可以一定程度避免装箱拆箱
   //举例：优化ArrayList
   class ArrayList<T>
   {
   private T[] array;
   
   public void Add(T value)
   {
   
   }
   
   public void Remove( T value)
   {
   
   }
   }
   #endregion
   
   #region 总结
   //1.申明泛型时 它只是一个类型的占位符
   //2.泛型真正起作用的时候 是在使用它的时候
   //3.泛型占位字母可以有n个用逗号分开
   //4.泛型占位字母一般是大写字母
   //5.不确定泛型类型时 获取默认值 可以使用default(占位字符)
   //6.看到<>包裹的字母 那肯定是泛型
   ```

   

6. ### 泛型约束

   ```
    #region   什么是泛型约束
   //让泛型的类型有一定的限制
   //关键字：where
   //泛型约束一共有6种
   //1.值类型  where 泛型字母:struct
   //2.引用类型where 泛型字母:class
   //3.存在无参公共构造函数 where 泛型字母:new()
   //4.某个类本身或者其派生类   where 泛型字母:类名
   //5.某个接口的派生类型  where 泛型字母:接口名
   //6.另一个泛型类型本身或者派生类型   where 泛型字母:另一个泛型字母
   
   // where 泛型字母:(约束的类型)
   #endregion
   
   #region   各泛型约束讲解
   
   #region 值类型约束
   class Test1<T> where T:struct
   {
   public T value;
   
   public void TestFun<K>(K v) where K:struct
   {
   
   }
   }
   #endregion
   
   #region 引用类型约束
   class Test2<T> where T:class
   {
   public T value;
   
   public void TestFun<K>(K k) where K:class
   {
   
   }
   }
   #endregion
   
   #region 公共无参构造约束
   class Test3<T> where T:new()
   {
   public T value;
   
   public void TestFun<K>(K k) where K : new()
   {
   
   }
   }
   
   class Test1
   {
   public Test1()
   {
   
   }
   }
   
   class Test2
   {
   public Test2(int a)
   {
   
   }
   }
   #endregion
   
   #region 类约束
   class Test4<T> where T : Test1
   {
   public T value;
   
   public void TestFun<K>(K k) where K : Test1
   {
   
   }
   }
   
   class Test3:Test1
   {
   
   }
   #endregion
   
   #region 接口约束
   interface IFly
   {
   
   }
   
   interface IMove:IFly
   {
   
   }
   
   class Test4:IFly
   {
   
   }
   
   class Test5<T> where T : IFly
   {
   public T value;
   
   public void TestFun<K>(K k) where K : IFly
   {
   
   }
   }
   #endregion
   
   #region 另一个泛型约束
   class Test6<T,U> where T : U
   {
   public T value;
   
   public void TestFun<K,V>(K k) where K : V
   {
   
   }
   }
   #endregion
   
   #endregion
   
   #region   约束的组合使用
   class Test7<T> where T: class,new()
   {
   
   }
   #endregion
   
   #region   多个泛型有约束
   class Test8<T,K> where T:class,new() where K:struct
   {
   
   }
   #endregion
   
   #region 总结
   //泛型约束：让类型有一定限制
   //class
   //struct
   //new()
   //类名
   //接口名
   //另一个泛型字母
   
   //注意：
   //1.可以组合使用
   //2.多个泛型约束 用where连接即可
   #endregion
   ```

   

7. ### List

   ```
    #region  List的本质
   //List是一个C#为我们封装好的类，
   //它的本质是一个可变类型的泛型数组，
   //List类帮助我们实现了很多方法，
   //比如泛型数组的增删查改
   #endregion
   
   #region   申明
   //需要引用命名空间
   //using System.Collections.Generic
   List<int> list = new List<int>();
   List<string> list2 = new List<string>();
   List<bool> list3 = new List<bool>();
   #endregion
   
   #region 增删查改
   
   #region 增
   list.Add(1);
   list.Add(2);
   list.Add(3);
   list.Add(4);
   
   list2.Add("123");
   
   List<string> listStr = new List<string>();
   listStr.Add("123");
   list2.AddRange(listStr);
   
   list.Insert(0, 999);
   Console.WriteLine(list[0]);
   #endregion
   
   #region 删
   //1.移除指定元素
   list.Remove(1);
   //2.移除指定位置的元素
   list.RemoveAt(0);
   //3.清空
   list.Clear();
   
   list.Add(1);
   list.Add(2);
   list.Add(3);
   list.Add(4);
   list.Add(1);
   #endregion
   
   #region 查
   //1.得到指定位置的元素
   Console.WriteLine(list[0]);
   //2.查看元素是否存在
   if( list.Contains(1) )
   {
       Console.WriteLine("存在元素 1");
   }
   //3.正向查找元素位置
   // 找到返回位置 找不到 返回-1
   int index = list.IndexOf(5);
   Console.WriteLine(index);
   //4.反向查找元素位置
   // 找到返回位置 找不到 返回-1
   index = list.LastIndexOf(2);
   Console.WriteLine(index);
   #endregion
   
   #region 改
   Console.WriteLine(list[0]);
   list[0] = 99;
   Console.WriteLine(list[0]);
   #endregion
   
   #endregion
   
   #region  遍历
   //长度
   Console.WriteLine(list.Count);
   //容量
   //避免产生垃圾
   Console.WriteLine(list.Capacity);
   Console.WriteLine("**********************");
   for (int i = 0; i < list.Count; i++)
   {
       Console.WriteLine(list[i]);
   }
   Console.WriteLine("**********************");
   foreach (int item in list)
   {
       Console.WriteLine(item);
   }
   
   #endregion
   ```

   

8. ### Dictionary

   ```
   #region Dictionary的本质
   //可以将Dictionary理解为 拥有泛型的Hashtable
   //它也是基于键的哈希代码组织起来的 键/值对
   //键值对类型从Hashtable的object变为了可以自己制定的泛型
   #endregion
   
   #region   申明
   //需要引用命名空间 using System.Collections.Generic
   Dictionary<int, string> dictionary = new Dictionary<int, string>();
   #endregion
   
   #region  增删查改
   
   #region 增
   //注意：不能出现相同键
   dictionary.Add(1, "123");
   dictionary.Add(2, "222");
   dictionary.Add(3, "222");
   //dictionary.Add(3, "123");
   #endregion
   
   #region 删
   //1.只能通过键去删除
   //  删除不存在键 没反应
   dictionary.Remove(1);
   dictionary.Remove(4);
   
   //2.清空
   dictionary.Clear();
   dictionary.Add(1, "123");
   dictionary.Add(2, "222");
   dictionary.Add(3, "222");
   #endregion
   
   #region 查
   //1.通过键查看值
   //  找不到直接报错
   Console.WriteLine(dictionary[2]);
   //Console.WriteLine(dictionary[4]);
   Console.WriteLine(dictionary[1]);
   
   //2.查看是否存在
   //  根据键检测
   if( dictionary.ContainsKey(4) )
   {
   Console.WriteLine("存在键为1的键值对");
   }
   //  根据值检测
   if (dictionary.ContainsValue("1234"))
   {
   Console.WriteLine("存在值为123的键值对");
   }
   
   #endregion
   
   #region 改
   Console.WriteLine(dictionary[1]);
   dictionary[1] = "555";
   Console.WriteLine(dictionary[1]);
   #endregion
   
   #endregion
   
   #region   遍历
   Console.WriteLine("**************");
   Console.WriteLine(dictionary.Count);
   //1.遍历所有键
   foreach (int item in dictionary.Keys)
   {
   Console.WriteLine(item);
   Console.WriteLine(dictionary[item]);
   }
   //2.遍历所有值
   Console.WriteLine("**************");
   foreach (string item in dictionary.Values)
   {
   Console.WriteLine(item);
   }
   //3.键值对一起遍历
   Console.WriteLine("**************");
   foreach (KeyValuePair<int,string> item in dictionary)
   {
   Console.WriteLine("键：" + item.Key + "值：" + item.Value);
   }
   #endregion
   ```

   

9. ###  顺序存储 和 链式存储

   ```
    #region 顺序存储
   //数组、Stack、Queue、List、ArrayList —— 顺序存储
   //只是 数组、Stack、Queue的 组织规则不同而已
   //顺序存储：
   //用一组地址连续的存储单元依次存储线性表的各个数据元素
   #endregion
   
   #region 链式存储
   //单向链表、双向链表、循环链表 —— 链式存储
   //链式存储(链接存储)：
   //用一组任意的存储单元存储线性表中的各个数据元素
   #endregion
   
   #region   实现一个最简单的单向链表
   /// <summary>
   /// 单向链表节点
   /// </summary>
   /// <typeparam name="T"></typeparam>
   class LinkedNode<T>
   {
   public T value;
   //这个存储下一个元素是谁 相当于钩子
   public LinkedNode<T> nextNode;
   
   public LinkedNode(T value)
   {
   this.value = value;
   }
   }
   
   /// <summary>
   /// 单向链表类 管理 节点 管理 添加等等
   /// </summary>
   /// <typeparam name="T"></typeparam>
   class LindedList<T>
   {
   public LinkedNode<T> head;
   public LinkedNode<T> last;
   
   public void Add(T value)
   {
   //添加节点 必然是new一个新的节点
   LinkedNode<T> node = new LinkedNode<T>(value);
   if( head == null )
   {
   head = node;
   last = node;
   }
   else
   {
   last.nextNode = node;
   last = node;
   }
   }
   
   public void Remove(T value)
   {
   if( head == null )
   {
   return;
   }
   if( head.value.Equals(value) )
   {
   head = head.nextNode;
   //如果头节点 被移除 发现头节点变空
   //证明只有一个节点 那尾也要清空
   if( head == null )
   {
   last = null;
   }
   return;
   }
   LinkedNode<T> node = head;
   while(node.nextNode != null)
   {
   if( node.nextNode.value.Equals(value) )
   {
   //让当前找到的这个元素的 上一个节点
   //指向 自己的下一个节点
   node.nextNode = node.nextNode.nextNode;
   break;
   }
   }
   }
   }
   #endregion
   
   #region   顺序存储和链式存储的优缺点
   //从增删查改的角度去思考
   //增：链式存储 计算上 优于顺序存储 （中间插入时链式不用像顺序一样去移动位置）
   //删：链式存储 计算上 优于顺序存储 （中间删除时链式不用像顺序一样去移动位置）
   //查：顺序存储 使用上 优于链式存储 （数组可以直接通过下标得到元素，链式需要遍历）
   //改：顺序存储 使用上 优于链式存储 （数组可以直接通过下标得到元素，链式需要遍历）
   #endregion
   ```

   

10. ###  LinkedList

    ```
      #region   LinkedList
    //LinkedList是一个C#为我们封装好的类
    //它的本质是一个可变类型的泛型双向链表
    #endregion
    
    #region   申明
    //需要引用命名空间
    //using System.Collections.Generic
    LinkedList<int> linkedList = new LinkedList<int>();
    LinkedList<string> linkedList2 = new LinkedList<string>();
    //链表对象 需要掌握两个类
    //一个是链表本身 一个是链表节点类LinkedListNode
    #endregion
    
    #region  增删查改
    
    #region 增
    //1.在链表尾部添加元素
    linkedList.AddLast(10);
    
    //2.在链表头部添加元素
    linkedList.AddFirst(20);
    
    //3.在某一个节点之后添加一个节点
    //  要指定节点 先得得到一个节点
    LinkedListNode<int> n = linkedList.Find(20);
    linkedList.AddAfter(n, 15);
    //4.在某一个节点之前添加一个节点
    //  要指定节点 先得得到一个节点
    linkedList.AddBefore(n, 11);
    #endregion
    
    #region 删
    //1.移除头节点
    linkedList.RemoveFirst();
    //2.移除尾节点
    linkedList.RemoveLast();
    //3.移除指定节点
    //  无法通过位置直接移除
    linkedList.Remove(20);
    //4.清空
    linkedList.Clear();
    
    linkedList.AddLast(1);
    linkedList.AddLast(2);
    linkedList.AddLast(3);
    linkedList.AddLast(4);
    #endregion
    
    #region 查
    //1.头节点
    LinkedListNode<int> first = linkedList.First;
    //2.尾节点
    LinkedListNode<int> last = linkedList.Last;
    //3.找到指定值的节点
    //  无法直接通过下标获取中间元素
    //  只有遍历查找指定位置元素
    LinkedListNode<int> node = linkedList.Find(3);
    Console.WriteLine(node.Value);
    node = linkedList.Find(5);
    //4.判断是否存在
    if( linkedList.Contains(1) )
    {
        Console.WriteLine("链表中存在1");
    }
    #endregion
    
    #region 改
    //要先得再改 得到节点 再改变其中的值
    Console.WriteLine(linkedList.First.Value);
    linkedList.First.Value = 10;
    Console.WriteLine(linkedList.First.Value);
    #endregion
    
    #endregion
    
    #region   遍历
    //1.foreach遍历
    foreach (int item in linkedList)
    {
        Console.WriteLine(item);
    }
    
    //2.通过节点遍历
    //  从头到尾
    Console.WriteLine("&&&&&&&&&&&&&&&&&&&&&&&&&&&");
    LinkedListNode<int> nowNode = linkedList.First;
    while (nowNode != null)
    {
        Console.WriteLine(nowNode.Value);
        nowNode = nowNode.Next;
    }
    
    //  从尾到头
    
    Console.WriteLine("&&&&&&&&&&&&&&&&&&&&&&&&&&&");
    nowNode = linkedList.Last;
    while (nowNode != null)
    {
        Console.WriteLine(nowNode.Value);
        nowNode = nowNode.Previous;
    }
    
    #endregion
    ```

    

11. ### 泛型栈 和 队列

    ```
       #region 泛型数据集合
    //using System.Collections.Generic;
    
    //List  列表  泛型列表
    //Dictionary 字典  泛型哈希表
    //LinkedList 双向链表 
    //Statck 泛型栈
    //Queue 泛型队列
    #endregion
    
    #endregion
    
    #region   泛型栈和队列
    //命名空间：using System.Collections.Generic;
    //使用上 和之前的Stack和Queue一模一样
    Stack<int> stack = new Stack<int>();
    Queue<object> queue = new Queue<object>();
    #endregion
    ```

    

12. ### 委托

    ```
    using System;
    namespace Lesson12_委托
    {
        #region   委托是什么
        //委托是 函数(方法)的容器 
        //可以理解为表示函数(方法)的变量类型
        //用来 存储、传递函数(方法)
        //委托的本质是一个类，用来定义函数(方法)的类型（返回值和参数的类型）
        //不同的 函数(方法)必须对应和各自"格式"一致的委托
        #endregion
        #region   基本语法
        //关键字 ： delegate
        //语法：访问修饰符 delegate 返回值 委托名(参数列表);
        //写在哪里？
        //可以申明在namespace和class语句块中
        //更多的写在namespace中
        //简单记忆委托语法 就是 函数申明语法前面加一个delegate关键字
        #endregion
        #region   定义自定义委托
        //访问修饰默认不写 为public 在别的命名空间中也能使用
        //private 其它命名空间就不能用了
        //一般使用public
        //申明了一个可以用来存储无参无返回值函数的容器
        //这里只是定义了规则 并没有使用
        delegate void MyFun();
        //委托规则的申明 是不能重名（同一语句块中）
        //表示用来装载或传递 返回值为int 有一个int参数的函数的 委托 容器规则
        public delegate int MyFun2(int a);
        //委托是支持 泛型的 可以让返回值和参数 可变 更方便我们的使用
        delegate T MyFun3<T, K>(T v, K k);
        #endregion
        #region   使用定义好的委托
        //委托变量是函数的容器
        //委托常用在：
        //1.作为类的成员
        //2.作为函数的参数
        class Test
        {
    public MyFun fun;
    public MyFun2 fun2;
    public Action action;
    public void TestFun( MyFun fun, MyFun2 fun2 )
    {
    //先处理一些别的逻辑 当这些逻辑处理完了 再执行传入的函数
    int i = 1;
    i *= 2;
    i += 2;
    //fun();
    //fun2(i);
    //this.fun = fun;
    //this.fun2 = fun2;
    }
    #region 增 委托变量可以存储多个函数(多播委托)
    public void AddFun(MyFun fun, MyFun2 fun2)
    {
    this.fun += fun;
    this.fun2 += fun2;
    }
    #endregion
    #region 删
    public void RemoveFun(MyFun fun, MyFun2 fun2)
    {
    //this.fun = this.fun - fun;
    this.fun -= fun;
    this.fun2 -= fun2;
    }
    #endregion
        }
        #endregion
        ------------------
    Console.WriteLine("委托");
    //专门用来装载 函数的 容器
    MyFun f = new MyFun(Fun);
    Console.WriteLine("1");
    Console.WriteLine("2");
    Console.WriteLine("3");
    Console.WriteLine("4");
    Console.WriteLine("5");
    f.Invoke();
    
    MyFun f2 = Fun;
    f2();
    MyFun2 f3 = Fun2;
    Console.WriteLine(f3(1));
    MyFun2 f4 = new MyFun2(Fun2);
    Console.WriteLine(f4.Invoke(3));
    Test t = new Test();
    t.TestFun(Fun, Fun2);
    Console.WriteLine("***************");
    //如何用委托存储多个函数
    MyFun ff = null;
    //ff = ff + Fun;
    ff += Fun;
    ff += Fun3;
    ff();
    //从容器中移除指定的函数
    ff -= Fun;
    //多减 不会报错 无非就是不处理而已
    ff -= Fun;
    ff();
    //清空容器
    ff = null;
    if( ff != null )
    {
        ff();
    }
    #region 知识点六 系统定义好的委托
    //使用系统自带委托 需要引用using System;
    //无参无返回值
    Action action = Fun;
    action += Fun3;
    action();
    //可以指定返回值类型的 泛型委托
    Func<string> funcString = Fun4;
    Func<int> funcInt = Fun5;
    //可以传n个参数的  系统提供了 1到16个参数的委托 直接用就行了
    Action<int, string> action2 = Fun6;
    //可以穿n个参数的 并且有返回值的 系统也提供了 16个委托
    Func<int, int> func2 = Fun2;
    #endregion
    }
    
    static void Fun(){}
    static void Fun3(){}
    static string Fun4(){}
    static int Fun5(){}
    static void Fun6(int i, string s){}
    		static int Fun2(int value){}
        }
    
        //总结
        //简单理解 委托 就是装载、传递函数的容器而已
        //可以用委托变量 来存储函数或者传递函数的
        //系统其实已经提供了很多委托给我们用 
        //Action:没有返回值，参数提供了 0~16个委托给我们用
        //Func:有返回值，参数提供了 0~16个委托给我们用
    }
    
    ```

    

13. ### 事件

    ```
    #region  事件是什么
        //事件是基于委托的存在
        //事件是委托的安全包裹
        //让委托的使用更具有安全性
        //事件 是一种特殊的变量类型
        #endregion
    
        #region   事件的使用
        //申明语法：
        //访问修饰符 event 委托类型 事件名;
        //事件的使用：
        //1.事件是作为 成员变量存在于类中
        //2.委托怎么用 事件就怎么用
        //事件相对于委托的区别:
        //1.不能在类外部 赋值
        //2.不能再类外部 调用
        //注意：
        //它只能作为成员存在于类和接口以及结构体中
        class Test
        {
    //委托成员变量 用于存储 函数的
    public Action myFun;
    //事件成员变量 用于存储 函数的
    public event Action myEvent;
    
    public Test()
    {
    //事件的使用和委托 一模一样 只是有些 细微的区别
    myFun = TestFun;
    myFun += TestFun;
    myFun -= TestFun;
    myFun();
    myFun.Invoke();
    myFun = null;
    
    myEvent = TestFun;
    myEvent += TestFun;
    myEvent -= TestFun;
    myEvent();
    myEvent.Invoke();
    myEvent = null;
    }
    
    public void DoEvent()
    {
    if(myEvent != null)
    {
        myEvent();
    }
    }
    
    public void TestFun()
    {
    Console.WriteLine("123");
    }
        }
        #endregion
    
        #region   为什么有事件
        //1.防止外部随意置空委托
        //2.防止外部随意调用委托
        //3.事件相当于对委托进行了一次封装 让其更加安全
        #endregion
    
        class Program
        {
    static void Main(string[] args)
    {
    Console.WriteLine("事件");
    
    Test t = new Test();
    //委托可以在外部赋值
    t.myFun = null;
    t.myFun = TestFun;
    t.myFun = t.myFun + TestFun;
    t.myFun += TestFun;
    //事件是不能再外部赋值的
    //t.myEvent = null;
    //t.myEvent = TestFun;
    //虽然不能直接赋值 但是可以 加减 去添加移除记录的函数
    t.myEvent += TestFun;
    t.myEvent -= TestFun;
    
    //委托是可以在外部调用的
    t.myFun();
    t.myFun.Invoke();
    //事件不能再外部调用
    //t.myEvent();
    //只能在类的内部去封装 调用
    t.DoEvent();
    
    Action a = TestFun;
    //事件 是不能作为临时变量在函数中使用的
    //event Action ae = TestFun;
    }
    
    static void TestFun()
    {
    
    }
        }
        //总结
        //事件和委托的区别
        //事件和委托的使用基本是一模一样的
        //事件就是特殊的委托
        //主要区别：
        //1.事件不能再外部使用赋值=符号，只能使用+ - 委托 哪里都能用
        //2.事件 不能再外部执行 委托哪里都能执行
        //3.事件 不能作为 函数中的临时变量的 委托可以
    ```

    

14. ### 匿名函数

    ```
      class Program
        {
    static void Main(string[] args)
    {
    Console.WriteLine("匿名函数"); 
    #region   什么是匿名函数
    //顾名思义，就是没有名字的函数
    //匿名函数的使用主要是配合委托和事件进行使用
    //脱离委托和事件 是不会使用匿名函数的
    #endregion
    
    #region   基本语法
    //delegate (参数列表)
    //{
    //    //函数逻辑
    //};
    //何时使用？
    //1.函数中传递委托参数时
    //2.委托或事件赋值时
    #endregion 
    #region   使用
    //1.无参无返回
    //这样申明匿名函数 只是在申明函数而已 还没有调用
    //真正调用它的时候 是这个委托容器啥时候调用 就什么时候调用这个匿名函数
    Action a = delegate ()
    {
        Console.WriteLine("匿名函数逻辑");
    }; 
    a();
    //2.有参
    Action<int, string> b = delegate (int a, string b)
    {
        Console.WriteLine(a);
        Console.WriteLine(b);
    }; 
    b(100, "123");
    //3.有返回值
    Func<string> c = delegate ()
    {
        return "123123";
    }; 
    Console.WriteLine(c()); 
    //4.一般情况会作为函数参数传递 或者 作为函数返回值
    Test t = new Test();
    Action ac = delegate ()
    {
        Console.WriteLine("随参数传入的匿名函数逻辑");
    };
    t.Dosomthing(50, ac);
    //  参数传递
    t.Dosomthing(100, delegate ()
    {
        Console.WriteLine("随参数传入的匿名函数逻辑");
    }); 
    //  返回值
    Action ac2 = t.GetFun();
    ac2();
    //一步到位 直接调用返回的 委托函数
    t.GetFun()();
    #endregion 
    #region   匿名函数的缺点
    //添加到委托或事件容器中后 不记录 无法单独移除 
    Action ac3 = delegate ()
    {
        Console.WriteLine("匿名函数一");
    }; 
    ac3 += delegate ()
    {
        Console.WriteLine("匿名函数二");
    }; 
    ac3();
    //因为匿名函数没有名字 所以没有办法指定移除某一个匿名函数
    //此匿名函数 非彼匿名函数 不能通过看逻辑是否一样 就证明是一个 
    //ac3 -= delegate ()
    //{
    //    Console.WriteLine("匿名函数一");
    //};
    ac3 = null;
    //ac3();
    #endregion
    } 
    static void TestFun() { }
        } 
        class Test
        {
    public Action action; 
    //作为参数传递时
    public void Dosomthing(int a, Action fun)
    {
    Console.WriteLine(a);
    fun();
    } 
    //作为返回值
    public Action GetFun()
    {
    return delegate() {
        Console.WriteLine("函数内部返回的一个匿名函数逻辑");
    };
    } 
    public void TestTTTT() {  }
        } 
        //总结
        //匿名函数 就是没有名字的函数
        //固定写法 
        //delegate(参数列表){}
        //主要是在 委托传递和存储时  为了方便可以直接使用倪敏该函数
        //缺点是 没有办法指定移除
    }
    
    ```

    

15. ### Lambad表达式

    ```
     #region   什么是lambad表达式
    //可以将lambad表达式 理解为匿名函数的简写
    //它除了写法不同外
    //使用上和匿名函数一模一样
    //都是和委托或者事件 配合使用的
    #endregion 
    #region   lambad表达式语法
    //匿名函数
    //delegate (参数列表)
    //{
    
    //}; 
    //lambad表达式
    //(参数列表) =>
    //{
    //    //函数体
    //};
    #endregion 
    #region 使用
    //1.无参无返回
    Action a = () =>
    {
        Console.WriteLine("无参无返回值的lambad表达式");
    };
    a();
    //2.有参
    Action<int> a2 = (int value) =>
    {
        Console.WriteLine("有参数Lambad表达式{0}", value);
    };
    a2(100); 
    //3.甚至参数类型都可以省略 参数类型和委托或事件容器一致
    Action<int> a3 = (value) =>
    {
        Console.WriteLine("省略参数类型的写法{0}", value);
    };
    a3(200);
    //4.有返回值
    Func<string, int> a4 = (value) =>
    {
        Console.WriteLine("有返回值有参数的那么大表达式{0}", value);
        return 1;
    };
    Console.WriteLine(a4("123123")); 
    //其它传参使用等和匿名函数一样
    //缺点也是和匿名函数一样的
    #endregion
      #region 知识点四 闭包
        //内层的函数可以引用包含在它外层的函数的变量
        //即使外层函数的执行已经终止
        //注意：
        //该变量提供的值并非变量创建时的值，而是在父函数范围内的最终值。
    
        class Test
        {
    public event Action action;
    
    public Test()
    {
    int value = 10;
    //这里就形成了闭包
    //因为 当构造函数执行完毕时  其中申明的临时变量value的声明周期被改变了
    action = () =>
    {
        Console.WriteLine(value);
    };
    
    for (int i = 0; i < 10; i++)
    {
        //此index 非彼index
        int index = i;
        action += () =>
        {
    Console.WriteLine(index);
        };
    }
    }
    
    public void DoSomthing()
    {
    action();
    }
        }
    
        #endregion
        
        //总结
        //匿名函数的特殊写法 就是 lambad表达式
        //固定写法 就是 (参数列表)=>{}
        //参数列表 可以直接省略参数类型
        //主要在 委托传递和存储时  为了方便可以直接使用匿名函数或者lambad表达式
    
        //缺点：无法指定移除
        
    //    单独获取某个有返回值的委托
    Func<string> funtest =()=>{return "1";};
    funtest+=()=>{return"2";};
    funtest+=()=>{return"2";};
    
    Console.WriteLine(funtest());
    //通过GetInvocationList 方法获取委托列表
    //使用迭代器单独执行每个函数获取返回值
    foreach(Func<string> del in funtest.GetInvocationList())
    {
        Console.WriteLine(dele());
    }
    //知识点：委托容器中存在方法GetInvocationList()可以返回一个委托数组
    //获取下标唯0的函数
    Func<string> d = (Func<string>)funtest.GetInvocationList()[0];
    Console.WriteLine(d());
        
    ```

    

16. ### list排序

    ```
    using System;
    using System.Collections.Generic;
    using System.Diagnostics.CodeAnalysis;
    
    namespace Lesson16_List排序
    {
        class Item : IComparable<Item> {
    public int money; 
    public Item(int money)
    {
    this.money = money;
    } 
    public int CompareTo(Item other) {
    //返回值的含义
    //小于0：
    //放在传入对象的前面
    //等于0:
    //保持当前的位置不变
    //大于0：
    //放在传入对象的后面 
    //可以简单理解 传入对象的位置 就是0
    //如果你的返回为负数 就放在它的左边 也就前面
    //如果你返回正数 就放在它的右边 也就是后面 
    if( this.money > other.money ) { return -1; }
    else { return 1; }
    }
        } 
        class ShopItem {
    public int id; 
    public ShopItem(int id) { this.id = id; }
        } 
        class Program { static void Main(string[] args) { 
    #region   List自带排序方法
    List<int> list = new List<int>();
    list.Add(3);
    list.Add(2);
    list.Add(6);
    list.Add(1);
    list.Add(4);
    list.Add(5);
    for (int i = 0; i < list.Count; i++) { Console.WriteLine(list[i]);  }
    //list提供了排序方法
    list.Sort();
    Console.WriteLine("**************");
    for (int i = 0; i < list.Count; i++) { Console.WriteLine(list[i]); }
    //ArrayList中也有Sort排序方法
    #endregion 
    #region  自定义类的排序
    List<Item> itemList = new List<Item>();
    itemList.Add(new Item(45));
    itemList.Add(new Item(10));
    itemList.Add(new Item(99));
    itemList.Add(new Item(24));
    itemList.Add(new Item(100));
    itemList.Add(new Item(12));
    //排序方法
    itemList.Sort();
    for (int i = 0; i < itemList.Count; i++) { Console.WriteLine(itemList[i].money); }
    #endregion 
    #region  通过委托函数进行排序
    List<ShopItem> shopItems = new List<ShopItem>();
    shopItems.Add(new ShopItem(2));
    shopItems.Add(new ShopItem(1));
    shopItems.Add(new ShopItem(4));
    shopItems.Add(new ShopItem(3));
    shopItems.Add(new ShopItem(6));
    shopItems.Add(new ShopItem(5)); 
    //shopItems.Sort(SortShopItem);
    //匿名函数
    //shopItems.Sort(delegate (ShopItem a, ShopItem b)
    //{ if (a.id > b.id)  return -1; 
    //    else  return 1;  });
    //lambad表达式 配合 三目运算符的 完美呈现
    shopItems.Sort((a, b) =>{ return a.id > b.id ? 1 : -1;}); 
    Console.WriteLine("*********************");
    for (int i = 0; i < shopItems.Count; i++) 
        Console.WriteLine(shopItems[i].id); 
    #endregion
    } 
    static int SortShopItem( ShopItem a, ShopItem b )  {
    //传入的两个对象 为列表中的两个对象
    //进行两两的比较  用左边的和右边的条件 比较
    //返回值规则 和之前一样 0做标准 负数在左（前） 正数在右（后）
    if (a.id > b.id)   return -1; 
    else  return 1;  }
        } 
        //总结
        //系统自带的变量(int,float,double.....) 一般都可以直接Sort
        //自定义类SOrt有两种方式
        //1.继承接口 IComparable
        //2.在Sort中传入委托函数
    
    }
    
    ```

    

17. ### 协变逆变

    ```
      namespace Lesson17_协变逆变
    {
        #region   什么是协变逆变
        //协变：
        //和谐的变化，自然的变化
        //因为 里氏替换原则 父类可以装子类
        //所以 子类变父类  
        //比如 string 变成 object 
        //感受是和谐的 
        //逆变：
        //逆常规的变化，不正常的变化
        //因为 里氏替换原则 父类可以装子类 但是子类不能装父类
        //所以 父类变子类  
        //比如 object 变成 string
        //感受是不和谐的 
        //协变和逆变是用来修饰泛型的
        //协变：out 
        //逆变：in
        //用于在泛型中 修饰 泛型字母的 
        //只有泛型接口和泛型委托能使用
        #endregion 
        #region  作用
        //1.返回值 和 参数
        //用out修饰的泛型 只能作为返回值
        delegate T TestOut<out T>();
        //用in修饰的泛型 只能作为参数
        delegate void TestIn<in T>(T t); 
        //2.结合里氏替换原则理解
        class Father { } 
        class Son:Father {  }
        #endregion
        class Program
        {
    static void Main(string[] args)
    {
    Console.WriteLine("协变逆变");
    #region  作用（结合里氏替换原则理解）
    //协变 父类总是能被子类替换
    // 看起来 就是 son ——> father
    TestOut<Son> os = () =>
    {
        return new Son();
    }; 
    TestOut<Father> of = os;
    Father f = of();//实际上 返回的 是os里面装的函数 返回的是Son 
    //逆变 父类总是能被子类替换
    //看起来像是 father——>son 明明是传父类 但是你传子类 不和谐的
    TestIn<Father> iF = (value) => {  }; 
    TestIn<Son> iS = iF;
    
    iS(new Son());//实际上 调用的是 iF
    #endregion
    }
        } 
        //总结
        //协变 out
        //逆变 in
        //用来修饰 泛型替代符的  只能修饰接口和委托中的泛型 
        //作用两点
        //1.out修饰的泛型类型 只能作为返回值类型 in修饰的泛型类型 只能作为 参数类型
        //2.遵循里氏替换原则的  用out和in修饰的 泛型委托 可以相互装载（有父子关系的泛型）
        //  协变  父类泛型委托装子类泛型委托    逆变 子类泛型委托装父类泛型委托
    }
    
    ```

    

18. ### 多线程

    ```
    using System;
    using System.Threading;
    
    namespace Lesson18_多线程
    {
        class Program
        {
    static bool isRuning = true;
    
    static object obj = new object();
    static void Main(string[] args)
    {
    Console.WriteLine("多线程");
    
    #region   了解线程前先了解进程
    //进程（Process）是计算机中的程序关于某数据集合上的一次运行活动
    //是系统进行资源分配和调度的基本单位，是操作系统结构的基础
    //说人话：打开一个应用程序就是在操作系统上开启了一个进程
    //进程之间可以相互独立运行，互不干扰
    //进程之间也可以相互访问、操作
    #endregion
    
    #region   什么是线程
    //操作系统能够进行运算调度的最小单位。
    //它被包含在进程之中，是进程中的实际运作单位
    //一条线程指的是进程中一个单一顺序的控制流，一个进程中可以并发多个线程
    //我们目前写的程序 都在主线程中
    
    //简单理解线程：
    //就是代码从上到下运行的一条“管道”
    #endregion
    
    #region   什么是多线程
    //我们可以通过代码 开启新的线程
    //可以同时运行代码的多条“管道” 就叫多线程
    #endregion
    
    #region  语法相关
    //线程类 Thread
    //需要引用命名空间 using System.Threading;
    //1.申明一个新的线程 
    //  注意 线程执行的代码 需要封装到一个函数中
    //  新线程 将要执行的代码逻辑 被封装到了一个函数语句块中
    Thread t = new Thread(NewThreadLogic);
    //2.启动线程
    t.Start();
    
    //3.设置为后台线程
    //当前台线程都结束了的时候,整个程序也就结束了,即使还有后台线程正在运行
    //后台线程不会防止应用程序的进程被终止掉
    //如果不设置为后台线程 可能导致进程无法正常关闭
    t.IsBackground = true;
    
    //4.关闭释放一个线程
    //如果开启的线程中不是死循环 是能够结束的逻辑 那么 不用刻意的去关闭它
    //如果是死循环 想要中止这个线程 有两种方式
    //4.1-死循环中bool标识
    //Console.ReadKey();
    
    //isRuning = false;
    
    //Console.ReadKey();
    
    //4.2-通过线程提供的方法(注意在.Net core版本中无法中止 会报错)
    //中止线程
    //try
    //{
    //    t.Abort();
    //    t = null;
    //}
    //catch
    //{
    
    //}
    
    //5.线程休眠
    //让线程休眠多少毫秒  1s = 1000毫秒
    //在哪个线程里执行 就休眠哪个线程
    //Thread.Sleep(1000);
    #endregion
    
    #region   线程之间共享数据
    //多个线程使用的内存是共享的，都属于该应用程序(进程)
    //所以要注意 当多线程 同时操作同一片内存区域时可能会出问题
    //可以通过加锁的形式避免问题
    
    //lock
    //当我们在多个线程当中想要访问同样的东西 进行逻辑处理时
    //为了避免不必要的逻辑顺序执行的差错
    //lock(引用类型对象)
    
    while(true)
    {
        lock(obj)
        {
    Console.SetCursorPosition(0, 0);
    Console.ForegroundColor = ConsoleColor.Red;
    Console.Write("●");
        }
    }
    #endregion
    
    #region   多线程对于我们的意义
    //可以用多线程专门处理一些复杂耗时的逻辑
    //比如 寻路、网络通信等等
    #endregion
    }
    
    static void NewThreadLogic()
    {
    //新开线程 执行的代码逻辑 在该函数语句块中
    while(isRuning)
    {
        //Thread.Sleep(1000);
        //Console.WriteLine("新开线程代码逻辑");
        lock(obj)
        {
    Console.SetCursorPosition(10, 5);
    Console.ForegroundColor = ConsoleColor.Yellow;
    Console.Write("■");
        }
    }
    }
        }
    
        //总结
        //多线程是多个可以同时执行代码逻辑的“管道”
        //可以通过代码开启多线程，用多线程处理一些复杂的可能影响主线程流畅度的逻辑
        //关键字 Thread
    }
    
    ```

    

19. ### 预处理器指令

    ```
     #region   什么是编译器
    //编译器是一种翻译程序
    //它用于将源语言程序翻译为目标语言程序
    
    //源语言程序：某种程序设计语言写成的,比如C#、C、C++、Java等语言写的程序
    //目标语言程序:二进制数表示的伪机器代码写的程序
    #endregion
    
    #region   什么是预处理器指令
    //预处理器指令 指导编译器 在实际编译开始之前对信息进行预处理
    //预处理器指令 都是以#开始
    //预处理器指令不是语句，所以它们不以分号;结束
    //目前我们经常用到的 折叠代码块 就是预处理器指令
    #endregion
    
    #region   常见的预处理器指令
    //1
    //#define
    //定义一个符号，类似一个没有值的变量
    //#undef
    //取消define定义的符号，让其失效
    //两者都是写在脚本文件最前面
    //一般配合 if指令使用 或配合特性
    
    //2
    //#if
    //#elif
    //#else
    //#endif
    //和if语句规则一样，一般配合#define定义的符号使用
    //用于告诉编译器进行编译代码的流程控制
    
    //如果发现有Unity4这个符号 那么其中包含的代码 就会被编译器翻译
    //可以通过 逻辑或 和 逻辑与 进行多种符号的组合判断
    #if Unity4
    Console.WriteLine("版本为Unity4");
    #elif Unity2017 && IOS
    Console.WriteLine("版本为Unity2017");
    //#warning 这个版本 不合法
    //#error 这个版本不准执行
    #else
    Console.WriteLine("其它版本");
    #endif
    
    //3
    //#warning
    //#error
    //告诉编译器
    //是报警告还是报错误
    //一般还是配合if使用
    #endregion
    
        //总结
        //预处理器指令
        //可以让代码还没有编译之前就可以进行一些预处理判断
        //在Unity中会用来进行一些平台或者版本的判断
        //决定不同的版本或者不同的平台使用不同的代码逻辑
    ```

    

20. ### 反射

    ```
      #region  什么是程序集
        //程序集是经由编译器编译得到的，供进一步编译执行的那个中间产物
        //在WINDOWS系统中，它一般表现为后缀为·dll（库文件）或者是·exe（可执行文件）的格式
    
        //说人话：
        //程序集就是我们写的一个代码集合，我们现在写的所有代码
        //最终都会被编译器翻译为一个程序集供别人使用
        //比如一个代码库文件（dll）或者一个可执行文件(exe)
        #endregion
    
        #region  元数据
        //元数据就是用来描述数据的数据
        //这个概念不仅仅用于程序上，在别的领域也有元数据
    
        //说人话：
        //程序中的类，类中的函数、变量等等信息就是 程序的 元数据
        //有关程序以及类型的数据被称为 元数据，它们保存在程序集中
        #endregion
    
        #region   反射的概念
        //程序正在运行时，可以查看其它程序集或者自身的元数据。
        //一个运行的程序查看本身或者其它程序的元数据的行为就叫做反射
    
        //说人话：
        //在程序运行时，通过反射可以得到其它程序集或者自己程序集代码的各种信息
        //类，函数，变量，对象等等，实例化它们，执行它们，操作它们
        #endregion
    
        #region   反射的作用
        //因为反射可以在程序编译后获得信息，所以它提高了程序的拓展性和灵活性
        //1.程序运行时得到所有元数据，包括元数据的特性
        //2.程序运行时，实例化对象，操作对象
        //3.程序运行时创建新对象，用这些对象执行任务
        #endregion
    ```

    ```
       class Test
        {
    private int i = 1;
    public int j = 0;
    public string str = "123";
    public Test()
    {
    
    }
    
    public Test(int i)
    {
    this.i = i;
    }
    
    public Test( int i, string str ):this(i)
    {
    this.str = str;
    
    }
    
    public void Speak()
    {
    Console.WriteLine(i);
    }
        }
    
        class Program
        {
    static void Main(string[] args)
    {
    Console.WriteLine("反射");
    #region  语法相关
    
    #region Type
    //Type（类的信息类）
    //它是反射功能的基础！
    //它是访问元数据的主要方式。 
    //使用 Type 的成员获取有关类型声明的信息
    //有关类型的成员（如构造函数、方法、字段、属性和类的事件）
    
    #region 获取Type
    //1.万物之父object中的 GetType()可以获取对象的Type
    int a = 42;
    Type type = a.GetType();
    Console.WriteLine(type);
    //2.通过typeof关键字 传入类名 也可以得到对象的Type
    Type type2 = typeof(int);
    Console.WriteLine(type2);
    //3.通过类的名字 也可以获取类型
    //  注意 类名必须包含命名空间 不然找不到
    Type type3 = Type.GetType("System.Int32");
    Console.WriteLine(type3);
    
    #endregion
    
    #region 得到类的程序集信息
    //可以通过Type可以得到类型所在程序集信息
    Console.WriteLine(type.Assembly);
    Console.WriteLine(type2.Assembly);
    Console.WriteLine(type3.Assembly);
    #endregion
    
    #region 获取类中的所有公共成员
    //首先得到Type
    Type t = typeof(Test);
    //然后得到所有公共成员
    //需要引用命名空间 using System.Reflection;
    MemberInfo[] infos = t.GetMembers();
    for (int i = 0; i < infos.Length; i++)
    {
        Console.WriteLine(infos[i]);
    }
    #endregion
    
    #region 获取类的公共构造函数并调用
    //1.获取所有构造函数
    ConstructorInfo[] ctors = t.GetConstructors();
    for (int i = 0; i < ctors.Length; i++)
    {
        Console.WriteLine(ctors[i]);
    }
    
    //2.获取其中一个构造函数 并执行
    //得构造函数传入 Type数组 数组中内容按顺序是参数类型
    //执行构造函数传入  object数组 表示按顺序传入的参数
    //  2-1得到无参构造
    ConstructorInfo info = t.GetConstructor(new Type[0]);
    //执行无参构造 无参构造 没有参数 传null
    Test obj = info.Invoke(null) as Test;
    Console.WriteLine(obj.j);
    
    //  2-2得到有参构造
    ConstructorInfo info2 = t.GetConstructor(new Type[] { typeof(int) });
    obj = info2.Invoke(new object[] { 2 }) as Test;
    Console.WriteLine(obj.str);
    
    ConstructorInfo info3 = t.GetConstructor(new Type[] { typeof(int), typeof(string) });
    obj = info3.Invoke(new object[] { 4, "444444" }) as Test;
    Console.WriteLine(obj.str);
    #endregion
    
    #region 获取类的公共成员变量
    //1.得到所有成员变量
    FieldInfo[] fieldInfos = t.GetFields();
    for (int i = 0; i < fieldInfos.Length; i++)
    {
        Console.WriteLine(fieldInfos[i]);
    }
    //2.得到指定名称的公共成员变量
    FieldInfo infoJ = t.GetField("j");
    Console.WriteLine(infoJ);
    
    //3.通过反射获取和设置对象的值
    Test test = new Test();
    test.j = 99;
    test.str = "2222";
    //  3-1通过反射 获取对象的某个变量的值
    Console.WriteLine(infoJ.GetValue(test));
    //  3-2通过反射 设置指定对象的某个变量的值
    infoJ.SetValue(test, 100);
    Console.WriteLine(infoJ.GetValue(test));
    #endregion
    
    #region 获取类的公共成员方法
    //通过Type类中的 GetMethod方法 得到类中的方法
    //MethodInfo 是方法的反射信息
    Type strType = typeof(string);
    MethodInfo[] methods = strType.GetMethods();
    for (int i = 0; i < methods.Length; i++)
    {
        Console.WriteLine(methods[i]);
    }
    //1.如果存在方法重载 用Type数组表示参数类型
    MethodInfo subStr = strType.GetMethod("Substring",
        new Type[] { typeof(int), typeof(int) });
    //2.调用该方法
    //注意：如果是静态方法 Invoke中的第一个参数传null即可
    string str = "Hello,World!";
    //第一个参数 相当于 是哪个对象要执行这个成员方法
    object result = subStr.Invoke(str, new object[] { 7, 5 });
    Console.WriteLine(result);
    
    #endregion
    
    #region 其它
    //Type;
    //得枚举
    //GetEnumName
    //GetEnumNames
    
    //得事件
    //GetEvent
    //GetEvents
    
    //得接口
    //GetInterface
    //GetInterfaces
    
    //得属性
    //GetProperty
    //GetPropertys
    //等等
    #endregion
    
    #endregion
    
    #region Assembly
    //程序集类
    //主要用来加载其它程序集，加载后
    //才能用Type来使用其它程序集中的信息
    //如果想要使用不是自己程序集中的内容 需要先加载程序集
    //比如 dll文件(库文件) 
    //简单的把库文件看成一种代码仓库，它提供给使用者一些可以直接拿来用的变量、函数或类
    
    //三种加载程序集的函数
    //一般用来加载在同一文件下的其它程序集
    //Assembly asembly2 = Assembly.Load("程序集名称");
    
    //一般用来加载不在同一文件下的其它程序集
    //Assembly asembly = Assembly.LoadFrom("包含程序集清单的文件的名称或路径");
    //Assembly asembly3 = Assembly.LoadFile("要加载的文件的完全限定路径");
    
    //1.先加载一个指定程序集
    Assembly asembly = Assembly.LoadFrom(@"C:\Users\MECHREVO\Desktop\CSharp进阶教学\Lesson18_练习题\bin\Debug\netcoreapp3.1\Lesson18_练习题");
    Type[] types = asembly.GetTypes();
    for (int i = 0; i < types.Length; i++)
    {
        Console.WriteLine(types[i]);
    }
    //2.再加载程序集中的一个类对象 之后才能使用反射
    Type icon = asembly.GetType("Lesson18_练习题.Icon");
    MemberInfo[] members = icon.GetMembers();
    for (int i = 0; i < members.Length; i++)
    {
        Console.WriteLine(members[i]);
    }
    //通过反射 实例化一个 icon对象
    //首先得到枚举Type 来得到可以传入的参数
    Type moveDir = asembly.GetType("Lesson18_练习题.E_MoveDir");
    FieldInfo right = moveDir.GetField("Right");
    //直接实例化对象
    object iconObj = Activator.CreateInstance(icon, 10, 5, right.GetValue(null));
    //得到对象中的方法 通过反射
    MethodInfo move = icon.GetMethod("Move");
    MethodInfo draw = icon.GetMethod("Draw");
    MethodInfo clear = icon.GetMethod("Clear");
    
    Console.Clear();
    while(true)
    {
        Thread.Sleep(1000);
        clear.Invoke(iconObj, null);
        move.Invoke(iconObj, null);
        draw.Invoke(iconObj, null);
    }
    
    //3.类库工程创建
    #endregion
    
    #region Activator
    //用于快速实例化对象的类
    //用于将Type对象快捷实例化为对象
    //先得到Type
    //然后 快速实例化一个对象
    Type testType = typeof(Test);
    //1.无参构造
    Test testObj = Activator.CreateInstance(testType) as Test;
    Console.WriteLine(testObj.str);
    //2.有参数构造
    testObj = Activator.CreateInstance(testType, 99) as Test;
    Console.WriteLine(testObj.j);
    
    testObj = Activator.CreateInstance(testType, 55, "111222") as Test;
    Console.WriteLine(testObj.j);
    #endregion
    
    #endregion
    }
        }
    
        //总结
        //反射
        //在程序运行时，通过反射可以得到其他程序集或者自己的程序集代码的各种信息
        //类、函数、变量、对象等等，实例化他们，执行他们，操作他们
    
        //关键类
        //Type
        //Assembly
        //Activator
    
        //对于我们的意义
        //在初中级阶段 基本不会使用反射
        //所以目前对于大家来说，了解反射可以做什么就行
        //很长时间内都不会用到反射相关知识点
    
        //为什么要学反射
        //为了之后学习Unity引擎的基本工作原理做铺垫
        //Unity引起的基本工作机制 就是建立在反射的基础上
    ```

    

21. ### 特性

    ```
    #region  特性是什么
        //特性是一种允许我们向程序的程序集添加元数据的语言结构
        //它是用于保存程序结构信息的某种特殊类型的类 
        //特性提供功能强大的方法以将声明信息与 C# 代码（类型、方法、属性等）相关联。
        //特性与程序实体关联后，即可在运行时使用反射查询特性信息 
        //特性的目的是告诉编译器把程序结构的某组元数据嵌入程序集中
        //它可以放置在几乎所有的声明中（类、变量、函数等等申明） 
        //说人话：
        //特性本质是个类
        //我们可以利用特性类为元数据添加额外信息
        //比如一个类、成员变量、成员方法等等为他们添加更多的额外信息
        //之后可以通过反射来获取这些额外信息
        #endregion 
        #region 自定义特性
        //继承特性基类 Attribute
        [AttributeUsage(AttributeTargets.Class | AttributeTargets.Field, AllowMultiple = true, Inherited = false)]
        class MyCustomAttribute : Attribute
        {
    //特性中的成员 一般根据需求来写
    public string info; 
    public MyCustomAttribute(string info) { this.info = info; } 
    public void TestFun() { Console.WriteLine("特性的方法"); }
        }
        #endregion 
        #region 特性的使用
        //基本语法:
        //[特性名(参数列表)]
        //本质上 就是在调用特性类的构造函数
        //写在哪里？
        //类、函数、变量上一行，表示他们具有该特性信息 
        [MyCustom("这个是我自己写的一个用于计算的类")]
        [MyCustom("这个是我自己写的一个用于计算的类")]
        class MyClass
        {
    [MyCustom("这是一个成员变量")]
    public int value; 
    //[MyCustom("这是一个用于计算加法的函数")]
    //public void TestFun( [MyCustom("函数参数")]int a ) { }
    public void TestFun(int a) { }
        }
        #endregion 
        #region  限制自定义特性的使用范围
        //通过为特性类 加特性 限制其使用范围
        [AttributeUsage(AttributeTargets.Class | AttributeTargets.Struct, AllowMultiple = true, Inherited = true)]
        //参数一：AttributeTargets —— 特性能够用在哪些地方
        //参数二：AllowMultiple —— 是否允许多个特性实例用在同一个目标上
        //参数三：Inherited —— 特性是否能被派生类和重写成员继承
        public class MyCustom2Attribute : Attribute { }
        #endregion 
        #region   系统自带特性——过时特性
        //过时特性
        //Obsolete
        //用于提示用户 使用的方法等成员已经过时 建议使用新方法
        //一般加在函数前的特性 
        class TestClass
        {
    //参数一：调用过时方法时 提示的内容
    //参数二：true-使用该方法时会报错  false-使用该方法时直接警告
    [Obsolete("OldSpeak方法已经过时了，请使用Speak方法", false)]
    public void OldSpeak(string str)
    {
    Console.WriteLine(str);
    } 
    public void Speak() { } 
    public void SpeakCaller(string str, [CallerFilePath]string fileName = "", 
    [CallerLineNumber]int line = 0, [CallerMemberName]string target = "")
    {
    Console.WriteLine(str);
    Console.WriteLine(fileName);
    Console.WriteLine(line);
    Console.WriteLine(target);
    }
        } 
        #endregion 
        #region  系统自带特性——调用者信息特性
        //哪个文件调用？
        //CallerFilePath特性
        //哪一行调用？
        //CallerLineNumber特性
        //哪个函数调用？
        //CallerMemberName特性 
        //需要引用命名空间 using System.Runtime.CompilerServices;
        //一般作为函数参数的特性
        #endregion 
        #region   系统自带特性——条件编译特性
        //条件编译特性
        //Conditional
        //它会和预处理指令 #define配合使用 
        //需要引用命名空间using System.Diagnostics;
        //主要可以用在一些调试代码上
        //有时想执行有时不想执行的代码
        #endregion 
        #region   系统自带特性——外部Dll包函数特性
        //DllImport 
        //用来标记非.Net(C#)的函数，表明该函数在一个外部的DLL中定义。
        //一般用来调用 C或者C++的Dll包写好的方法
        //需要引用命名空间 using System.Runtime.InteropServices
        #endregion
        class Program
        {
    [DllImport("Test.dll")]
    public static extern int Add(int a, int b); 
    [Conditional("Fun")]
    static void Fun()
    {
    Console.WriteLine("Fun执行");
    } 
    static void Main(string[] args)
    {
    Console.WriteLine("特性"); 
    #region 特性的使用
    MyClass mc = new MyClass();
    Type t = mc.GetType();
    //t = typeof(MyClass);
    //t = Type.GetType("Lesson21_特性.MyClass"); 
    //判断是否使用了某个特性
    //参数一：特性的类型
    //参数二：代表是否搜索继承链（属性和事件忽略此参数）
    if( t.IsDefined(typeof(MyCustomAttribute), false) )
    {
        Console.WriteLine("该类型应用了MyCustom特性");
    } 
    //获取Type元数据中的所有特性
    object[] array = t.GetCustomAttributes(true);
    for (int i = 0; i < array.Length; i++)
    {
        if( array[i] is MyCustomAttribute )
        {
    Console.WriteLine((array[i] as MyCustomAttribute).info);
    (array[i] as MyCustomAttribute).TestFun();
        }
    } 
    TestClass tc = new TestClass();
    tc.OldSpeak("123");
    tc.Speak(); 
    tc.SpeakCaller("123123123123123"); 
    Fun();
    #endregion
    }
        }
    
        //总结：
        //特性是用于 为元数据再添加更多的额外信息（变量、方法等等）
        //我们可以通过反射获取这些额外的数据 来进行一些特殊的处理
        //自定义特性——继承Attribute类
    
        // 系统自带特性：过时特性
    
        // 为什么要学习特性
        // Unity引擎中很多地方都用到了特性来进行一些特殊处理
    ```

    

22. ### 迭代器

    ```
    using System;
    using System.Collections; 
    namespace  迭代器
    {
        #region  迭代器是什么
        //迭代器（iterator）有时又称光标（cursor）
        //是程序设计的软件设计模式
        //迭代器模式提供一个方法顺序访问一个聚合对象中的各个元素
        //而又不暴露其内部的标识 
        //在表现效果上看
        //是可以在容器对象（例如链表或数组）上遍历访问的接口
        //设计人员无需关心容器对象的内存分配的实现细节
        //可以用foreach遍历的类，都是实现了迭代器的
        #endregion 
        #region 标准迭代器的实现方法
        //关键接口：IEnumerator,IEnumerable
        //命名空间：using System.Collections;
        //可以通过同时继承IEnumerable和IEnumerator实现其中的方法 
        class CustomList : IEnumerable, IEnumerator
        {
    private int[] list;
    //从-1开始的光标 用于表示 数据得到了哪个位置
    private int position = -1; 
    public CustomList()
    {
    list = new int[] { 1, 2, 3, 4, 5, 6, 7, 8 };
    } 
    #region IEnumerable
    public IEnumerator GetEnumerator()
    {
    Reset();
    return this;
    }
    #endregion 
    public object Current
    {
    get
    {
        return list[position];
    }
    }
    public bool MoveNext()
    {
    //移动光标
    ++position;
    //是否溢出 溢出就不合法
    return position < list.Length;
    } 
    //reset是重置光标位置 一般写在获取 IEnumerator对象这个函数中
    //用于第一次重置光标位置
    public void Reset()
    {
    position = -1;
    }
        }
        #endregion 
        #region  用yield return 语法糖实现迭代器
        //yield return 是C#提供给我们的语法糖
        //所谓语法糖，也称糖衣语法
        //主要作用就是将复杂逻辑简单化，可以增加程序的可读性
        //从而减少程序代码出错的机会 
        //关键接口：IEnumerable
        //命名空间：using System.Collections;
        //让想要通过foreach遍历的自定义类实现接口中的方法GetEnumerator即可 
        class CustomList2 : IEnumerable
        {
    private int[] list; 
    public CustomList2()
    {
    list = new int[] { 1, 2, 3, 4, 5, 6, 7, 8 };
    } 
    public IEnumerator GetEnumerator()
    {
    for (int i = 0; i < list.Length; i++)
    {
        //yield关键字 配合迭代器使用
        //可以理解为 暂时返回 保留当前的状态
        //一会还会在回来
        //C#的语法糖
        yield return list[i];
    }
    //yield return list[0];
    //yield return list[1];
    //yield return list[2];
    //yield return list[3];
    //yield return list[4];
    //yield return list[5];
    //yield return list[6];
    //yield return list[7];
    }
        } 
        #endregion 
        #region  用yield return 语法糖为泛型类实现迭代器
        class CustomList<T> : IEnumerable
        {
    private T[] array; 
    public CustomList(params T[] array)
    {
    this.array = array;
    } 
    public IEnumerator GetEnumerator()
    {
    for (int i = 0; i < array.Length; i++)
    {
        yield return array[i];
    }
    }
        }
        #endregion 
        class Program
        {
    static void Main(string[] args)
    {
    Console.WriteLine("迭代器"); 
    CustomList list = new CustomList(); 
    //foreach本质 
    //1.先获取in后面这个对象的 IEnumerator
    //  会调用对象其中的GetEnumerator方法 来获取
    //2.执行得到这个IEnumerator对象中的 MoveNext方法
    //3.只要MoveNext方法的返回值时true 就会去得到Current
    //  然后复制给 item
    //foreach (int item in list)
    //{
    //    Console.WriteLine(item);
    //} 
    //foreach (int item in list)
    //{
    //    Console.WriteLine(item);
    //} 
    CustomList<string> list2 = new CustomList<string>("123","321","333","555");
    foreach (string item in list2)
    {
        Console.WriteLine(item);
    }
    foreach (string item in list2)
    {
        Console.WriteLine(item);
    } 
    }
        }
    } 
    //总结：
    //迭代器就是可以让我们在外部直接通过foreach遍历对象中元素而不需要了解其结构
    //主要的两种方式
    //1.传统方式 继承两个接口 实现里面的方法
    //2.用语法糖 yield return 去返回内容 只需要继承一个接口即可
    
    ```

    

23. ### 特殊语法

    ```
     class Person
        {
    private int money;
    public bool sex; 
    public string Name
    {
    get => "xxs";
    set => sex = true;
    } 
    public int Age
    {
    get;
    set;
    } 
    public Person(int money)
    {
    this.money = money;
    } 
    public int Add(int x, int y) => x + y; 
    public void Speak(string str) => Console.WriteLine(str);
        }
    
        class Program
        {
    static void Main(string[] args)
    {
    Console.WriteLine("特殊语法"); 
    #region   var隐式类型
    //var是一种特殊的变量类型
    //它可以用来表示任意类型的变量
    //注意：
    //1.var不能作为类的成员 只能用于临时变量申明时
    //  也就是 一般写在函数语句块中
    //2.var必须初始化
    var i = 5;
    var s = "123";
    var array = new int[] { 1, 2, 3, 4 };
    var list = new List<int>();
    #endregion 
    #region   设置对象初始值
    //申明对象时 
    //可以通过直接写大括号的形式初始化公共成员变量和属性
    Person p = new Person(100) { sex = true, Age = 18, Name = "xxs" };
    Person p2 = new Person(200) { Age = 18 };
    #endregion 
    #region   设置集合初始值
    //申明集合对象时
    //也可以通过大括号 直接初始化内部属性
    int[] array2 = new int[] { 1, 2, 3, 4, 5 }; 
    List<int> listInt = new List<int>() { 1, 2, 3, 4, 5, 6 }; 
    List<Person> listPerson = new List<Person>() {
        new Person(200),
        new Person(100){Age = 10},
        new Person(1){sex = true, Name = "xxs"}
    }; 
    Dictionary<int, string> dic = new Dictionary<int, string>()
    {
        { 1, "123" },
        { 2, "222"}
    }; 
    #endregion 
    #region  匿名类型
    //var 变量可以申明为自定义的匿名类型
    var v = new { age = 10, money = 11, name = "小明" };
    Console.WriteLine(v.age);
    Console.WriteLine(v.name);
    #endregion 
    #region  可空类型
    //1.值类型是不能赋值为 空的
    //int c = null;
    //2.申明时 在值类型后面加? 可以赋值为空
    int? c = 3;
    //3.判断是否为空
    if( c.HasValue )
    {
        Console.WriteLine(c);
        Console.WriteLine(c.Value);
    }
    //4.安全获取可空类型值
    int? value = null;
    //  4-1.如果为空 默认返回值类型的默认值
    Console.WriteLine(value.GetValueOrDefault());
    //  4-2.也可以指定一个默认值
    Console.WriteLine(value.GetValueOrDefault(100)); 
    float? f = null;
    double? d = null; 
    object o = null;
    if( o != null )
    {
        Console.WriteLine(o.ToString());
    }
    //相当于是一种语法糖 能够帮助我们自动去判断o是否为空
    //如果是null就不会执行tostring也不会报错
    Console.WriteLine(o?.ToString()); 
    int[] arrryInt = null; 
    Console.WriteLine(arrryInt?[0]); 
    Action action = null;
    //if (action != null)
    //{
    //    action();
    //}
    action?.Invoke(); 
    #endregion 
    #region  空合并操作符
    // 空合并操作符 ??
    // 左边值 ?? 右边值
    // 如果左边值为null 就返回右边值 否则返回左边值
    // 只要是可以为null的类型都能用 
    int? intV = null;
    //int intI = intV == null ? 100 : intV.Value;
    int intI = intV ?? 100;
    Console.WriteLine(intI); 
    string str = null;
    str = str ?? "hahah";
    Console.WriteLine(str);
    #endregion 
    #region   内插字符串
    //关键符号：$
    //用$来构造字符串，让字符串中可以拼接变量
    string name = "xxs";
    int age = 18;
    Console.WriteLine($"好好学习,{name},年龄：{age}");
    #endregion 
    #region 单句逻辑简略写法
    //当循环或者if语句中只有 一句代码时 大括号可以省略
    if (true)
        Console.WriteLine("123123"); 
    for (int j = 0; j < 10; j++)
        Console.WriteLine(j 
    while (true)
        Console.WriteLine("123123"); 
    #endregion
    }
        }
    ```