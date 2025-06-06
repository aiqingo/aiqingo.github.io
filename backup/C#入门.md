# C#入门  

![C](https://raw.githubusercontent.com/aiqingo/aiqingo.github.io/refs/heads/main/image/C%23%E5%85%A5%E9%97%A8%E5%86%85%E5%AE%B9.jpg)
1. ##  变量类型 

   #### 有符号的整形变量 是能存储 一定范围 正负数包括0的变量类型

   #### // sbyte -128~127

   ```c#
   sbyte sb = 1;
   ```

   #### // int  -21亿~21亿多

   ```
   int i = 2;
   ```

   #### // short -32768~32767之间的数

   ```
   short s = 3;
   ```

   #### // long -9百万兆~9百万兆之间的数

   ```
   long l = 4;
   ```

   #### 无符号的整形变量 是能存储 一定范围 0和正数的变量类型

   #### // byte 0~255

   ```
   byte b = 1;
   ```

   #### // uint 0~42亿多的一个范围

   ```
   uint ui = 2;
   ```

   #### // ushort 0~65535之间的一个数

   ```
   ushort us = 3;
   ```

   #### // ulong 0~18百万兆之间的数

   ```
   ulong ul = 4;
   ```

2. ### 浮点数(小数)

   #### //float 存储7/8位有效数字 根据编译器不同 有效数字也可能不一样 四舍五入

   #### //有效数字 是从左到右从非0数开始算有效数字的

   #### //之所以要在后面加f 是因为c#中 申明的小数 默认是double的类型 加f 是告诉系统 它是float类型

   ```
   float f = 1.01234567890f;
   ```

   #### //double 存储15~17位有效数字 抛弃的数字 会四舍五入

   ```
   double d = 0.12345678901234567890123456789;
   ```

   #### //decimal 存储27~28位的有效数字 不建议使用

   ```
   decimal de = 0.123456789012345678901234567890m;
   ```

3. ### 特殊类型

   #### //bool true false 表示真假的数据类型  真假类型

   ```
   bool bo = true;
   bool bo2 = false; 
   ```

   #### //char 是用来存储单个字符的变量类型 字符类型

   ```
   char c = '王';
   ```

   ### //string 是字符串类型 用来存储多个字符的 没有上限

   ```
   string str = "的骄傲了肯定就发生123123sdafjkasdkfjaskldjfAKKSAJD"; 
   ```

4. ###  常量 //关键字 const

   ​      //固定写法：

   ​      //const 变量类型 变量名 = 初始值;

   ```
   const int i2 = 20;
   ```

5. ### 转义字符

   ####   // 换行 \n

   ```
   str = "1231231\n23123123123";
   Console.WriteLine(str);
   ```

   ####       // 斜杠 \\  计算机文件路径 是要用到\符号的

   ```
   str = "哈\\哈哈";
   Console.WriteLine(str);
   ```

   ####       //不常用转义字符（了解）

   ####       // 制表符（空一个tab键）  \t

   ```
   str = "哈\t哈哈";
   Console.WriteLine(str);
   ```

   ####       // 光标退格  \b

   ```
   str = "123\b123";
   Console.WriteLine(str);
   ```

   ####       // 空字符 \0

   ```
    str = "1234\0123";
    Console.WriteLine(str);
   ```

   ####       // 警报音  \a

   ```
   str = "\a";
   Console.WriteLine(str);
   ```

   ####       //取消转义字符 @

   ```
   string str2 = @"哈哈\哈哈";
   Console.WriteLine(str2);
   Console.WriteLine(@"\n\\");
   ```

6. ###  // 什么是类型转换

   ​      // 类型转换 就是不同变量类型之间的相互转换

   ​      // 隐式转换的基本规则——>不同类型之间自动转换

   ​      // 大范围装小范围.

7. ### 显示转换

   #### 括号强转

   ​      // 作用 一般情况下 将高精度的类型强制转换为低精度

   ​      // 语法： 变量类型 变量名 = (变量类型)变量;

   ​      // 注意： 精度问题 范围问题

   #### Parse法

   ​      //作用  把字符串类型转换为对应的类型

   ​      //语法： 变量类型.Parse("字符串")

   ​      //注意： 字符串必须能够转换成对应类型 否则报错

   #### Convert法

   ​      //作用  更准确的将 各个类型之间进行相互转换 

   ​      //语法： Convert.To目标类型(变量或常量)

   ​      //注意： 填写的变量或常量必须正确 否则出错

8. ### 异常捕获

   //必备部分 

   ```
   try 
   {
   //希望进行异常捕获的代码块
   //放到try中 
   //如果try中的代码 报错了 不会让程序卡死
   }
   catch
   {
   //如果出错了 会执行 catch中的代码 来捕获异常
   //catch(Exception e) 具体报错跟踪 通过e得到 具体的错误信息
   }
   //可选部分
   finally
   {
   //最后执行的代码 不管有没有出错 都会执行其中的代码
   //目前 大家可以不用写
   }
   ```

   ​      //注意：异常捕获代码基本结构中 不需要加; 在里面去写代码逻辑时  每一句代码才加;

9. ### 运算符 

   ##### //优先级 是指 在混合运算时的运算顺序 

   ##### //乘除取余 优先级高于 加减 先算乘除取余 后算加减

   ##### //括号可以改变优先级 优先计算括号内内容

   #####  //多组括号 先算最里层括号 依次往外算

   #### // =

   ​      // 关键知识点 : 

   ​      // 先看右侧 再看左侧 把右侧的值赋值给左侧的变量

   ```
   string myName = "小学生";
   ```

   #### //加 +

   ​      // 用自己计算 先算右侧结果 再赋值给左侧变量

   ```
   int i = 1;
   // 3
   i = i + 2;
   ```

   #### 减 -

   ​      // 用自己计算 先算右侧结果 再赋值给左侧变量

   ```
   int j = 1;
   j = j - 1;
   ```

   #### 乘 *

   ​      // 用自己计算 先算右侧结果 再赋值给左侧变量

   ```
   int c = 1;
   c = c * 10;
   ```

   #### 除 / 

   ​      // 用自己计算 先算右侧结果 再赋值给左侧变量

   ```
   int chu = 1;
   chu = 10 / chu;
   ```

   #### 取余 %

   ​      // 用自己计算 先算右侧结果 再赋值给左侧变量

   ```
   int y = 4;
   // 4 / 3 得到余数 1
   y = y % 3;
   ```

   #### 算数运算符的 复合运算符

   ​      // 固定写法 运算符=

   ​      // += -= *= /= %=

   ​      //复合运算符 是用于 自己=自己进行运算

   ####  //自增运算符  让自己+-1 

   ```
   a2 = 1;
   a2++;//先用再加
   Console.WriteLine(a2);
   ++a2;//先加再用
   Console.WriteLine(a2);
   ```

   

10. ### 字符串拼接方式 

    ####       //string.Format("待拼接的内容", 内容1, 内容2,......);

    ​      //拼接内容中的固定规则

    ​      //想要被拼接的内容用占位符替代 {数字} 数字:0~n 依次往后 

    ```
    string str2 = string.Format("我是{0}, 我今年{1}岁, 我想要{2}", "小王", 18, "天天学习，好好向上");
    ```

    

11. ### 条件运算符

    ​      // 用于比较两个变量或常量

    ​      // 是否大于 >

    ​      // 是否小于 <

    ​      // 是否等于 == 

    ​      // 是否不等于 !=

    ​      // 是否大于等于 >=

    ​      // 是否小于等于 <=

12. ### 逻辑运算符

    #### 逻辑与

    ​      //符号 &&  并且

    ​      //规则 对两个bool值进行逻辑运算 有假则假 同真为真

    ```
    bool result = true && false;
    ```

    #### 逻辑或

    ​      //符号 || 或者

    ​      //规则 对两个bool值进行逻辑运算 有真则真 同假为假

    ```
    result = true || false;
    ```

    #### 逻辑非

    ​      //符号 !

    ​      //规则 对一个bool值进行取反  真变假  假变真

    ```
    result = !true;
    ```

    #### 混合使用优先级问题

    ​      // 规则  !(逻辑非)优先级最高  **&&(逻辑与)优先级高于||(逻辑或)**

    ​      // 逻辑运算符优先级 低于 算数运算符 条件运算符（逻辑非除外）

    #### 逻辑运算符短路规则

    ```
     int i3 = 1;
    // || 有真则真
    // 只要 逻辑与或者逻辑或 左边满足了条件 
    // i3 > 0 true 
    // 只要 满足条件 右边的内容 对于我们来说 已经不重要
    //逻辑或 有真则真 那左边只要为真了 右边就不重要
    result = i3 > 0 || ++i3 >= 1;
    // false && i3 ++ > 1;抛弃后面不去计算
    //逻辑与 有假则假 那左边只要为假了 右边就不重要
    result = i3 < 0 && i3++ > 1; 
    ```

13. ### 位运算符

    **位与 &**

    ```
    // 规则 连接两个数值进行位计算 将数值转为2进制 
    // 对位运算 有0则0
    int a = 1;// 001
    int b = 5;// 101
    //  001
    //& 101
    //  001  =  1
    int c = a & b;
    ```

    **位或 |**

    ```
    // 规则 连接两个数值进行位计算 将数值转为2进制 
    // 对位运算 有1则1
    a = 1;//001
    b = 3;//011
    c = a | b;
    //  001
    //| 011
    //  011
    Console.WriteLine(c);
    ```

    **异或 ^**

    ```
    // 规则 连接两个数值进行位计算 将数值转为2进制 
    // 对位运算 相同为0 不同为1
    a = 1; //001
    b = 5; //101
    // 001
    //^101
    // 100
    c = a ^ b;
    Console.WriteLine(c);
    ```

    **位取反 ~**

    ```
    // 规则 写在数值前面 将数值转为2进制 
    // 对位运算 0变1 1变0
    a = 5; 
    // 0000 0000 0000 0000 0000 0000 0000 0101
    // 1111 1111 1111 1111 1111 1111 1111 1010
    // 反码补码知识  
    c = ~a;
    Console.WriteLine(c);
    ```

    **左移<< 和 右移>>**

    ```
    // 规则 让一个数的2进制数进行左移和右移
    // 左移几位 右侧加几个0
    a = 5; // 101
    c = a << 5;
    // 1位 1010
    // 2位 10100
    // 3位 101000
    // 4位 1010000
    // 5位 10100000 = 32 + 128 = 160
    Console.WriteLine(c);
    // 右移几位 右侧去掉几个数
    a = 5; // 101
    c = a >> 2;
    // 1位 10
    // 2位 1
    Console.WriteLine(c);
    ```

14. ### 三目运算符 

    ```
    基本语法
    //套路： 3个空位 2个符号！！！
    //固定语法：空位   ? 空位         : 空位;
    //关键信息：bool类型 ? bool类型为真返回内容 : bool类型为假返回内容;
    //三目运算符 会有返回值，这个返回值类型必须一致，并且必须使用！
    string str = false ? "条件为真" : "条件为假";
    ```

    

15. ### if语句

    ```
    //作用： 满足条件时 多执行一些代码
    //语法：
    // if( bool类型值 )  // bool类型相关：bool变量 条件运算符表达式 逻辑运算符表达式
    // {
    //   满足条件要执行的代码 写在if代码块中;
    // }
    //else
    //{
    //}
    // 注意：
    // 1.if语句的语法部分， 不需要写分号
    // 2.if语句可以嵌套使用
    
    ```

16. ### switch

    ```
    //switch(变量)
    //{
    //   // 变量 == 常量 执行 case和 break之间的代码
    //   case 常量:
    //     满足条件执行的代码逻辑;
    //     break;
    //   case 常量:
    //     满足条件执行的代码逻辑;
    //     break;
    //   case 可以有无数个
    //   default:
    //     如果上面case的条件都不满足 就会执行 default中的代码
    //     break;
    //}
    // 注意： 常量！！ 只能写一个值 不能去写一个范围 不能写条件运算符啊 逻辑运算符啊
    // switch 只判断变量是否等于某一个固定值！！！！
    ```

17. #### 流程控制关键词

    ​      //作用 ： 控制循环逻辑的关键词

    ​      // break：跳出循环

    ​      // continue：回到循环开始 继续执行

18. ### while

    ```
    // bool类型变量  条件运算符 逻辑运算符 
    //while(bool类型的值)
    //{
    //   //当满足条件时 就会执行while语句块中的内容
    //   //......
    //   //......
    //   //......
    //   //......
    //   //当代码逻辑执行完 会回到while循环开头
    //   //再次进行条件判断
    //}
    ```

19. ### do..while

    ```
    // while循环 是先判断条件再执行
    // do while循环 是先斩后奏 先至少执行一次循环语句块中的逻辑 再判断是否继续
    //do
    //{
    //    //do while 循环语句块;
    //} while (bool类型的值);
    // 注意 do while 语句 存在一个重要的分号
    ```

20. ### for

    ```
    //for( /*初始表达式*/; /*条件表达式*/; /*增量表达式*/ )
                //{
                //    //循环代码逻辑;
                //}
                // 第一个空（初始表达式）： 一般声明一个临时变量，用来计数用
                // 第二个空（条件表达式）： 表明进入循环的条件 一个bool类型的结果（bool变量 条件运算符 逻辑运算符 算术运算符）
                // 第三个空（增量表达式）： 用第一个空中的变量 进行 自增减运算
                
                // 第一次进入循环时 才会调用 第一个空中的代码
                // 每次进入循环之前 都会判断第二个空中的条件 满足才会进入循环逻辑
    ```

#### 















