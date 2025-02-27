C# 备忘清单
===

提供基本语法和方法的 C# 快速参考备忘单

入门
--------

### Hello.cs

```cs
class Hello {
  // main method
  static void Main(string[] args)
  {
    // 输出: Hello, world!
    Console.WriteLine("Hello, world!");
  }
}
```

编译运行（确保在项目目录下）

```shell
$ dotnet run
Hello, world!
```

### 命名空间

```cs
//使用时 using 命名名称
using Test;
//创建：
namespace Test{
  class Test_className{
    // main方法是程序的主入口
    public void Myclass() {
      console.writeline("Test")
    }
  }
}
```

### 访问修饰符
<!--rehype:wrap-class=row-span-2-->

| 声明的可访问性     | 含义     |
|-----|----------------------|
| `public`             | 访问不受限制 |
| `protected`          | 访问限于包含类或派生自包含类的类型 (该类内部和继承类中可以访问)   |
| `internal`           | 访问限于当前程序集          |
| `protected internal` | 访问限于当前程序集或派生自包含类的类型         |
| `private`            | 访问限于包含类              |
| `private protected`  | 访问限于包含类或当前程序集中派生自包含类的类型,自 C# 7.2 之后可用 |
<!--rehype:className=style-list-->

### 字符串

```cs
string first = "John";
string last = "Doe";
// 字符串连接
string name = first + " " + last;
Console.WriteLine(name); // => John Doe
```

查看: [C#字符串](#c-字符串)

### 用户输入

```cs showLineNumbers
Console.WriteLine("Enter number:");
if(int.TryParse(Console.ReadLine(),out int input))
{
  // 输入验证
  Console.WriteLine($"You entered {input}");
}
```

### 变量

```cs
int intNum = 9;
long longNum = 9999999;
float floatNum = 9.99F;
double doubleNum = 99.999;
decimal decimalNum = 99.9999M;
char letter = 'D';
bool @bool = true;
string site = "jaywcjlove.github.io";
var num = 999;
var str = "999";
var bo = false;
```

### 注释

```cs
// 单行注释

/* 
 * 多行
 * 注释 
 */

// TODO：向IDE中的任务列表添加注释（VS、Rider都支持）

/// XML 单行注释，用于文档

/**
 * XML 多行注释，
 *  用于文档 
 */
```

### 条件判断

```cs
int j = 10;
if (j == 10) {
  Console.WriteLine("I get printed");
} else if (j > 10) {
  Console.WriteLine("I don't");
} else {
  Console.WriteLine("I also don't");
}
```

### 数组

```cs
char[] chars = new char[10];
chars[0] = 'a';
chars[1] = 'b';
string[] letters = {"A", "B", "C"};
int[] mylist = {100, 200};
bool[] answers = {true, false};
```

### 循环

```cs
int[] numbers = {1, 2, 3, 4, 5};
for(int i = 0; i < numbers.Length; i++) {
  Console.WriteLine(numbers[i]);
}
```

---

```cs
foreach(int num in numbers) {
  Console.WriteLine(num);
}
```

---

```cs
while(true)
{
   Console.WriteLine("只要给定的条件为真，while 循环语句会重复执行");
}
```

---

```cs
do
{
   Console.WriteLine("与 while 类似，do...while 会确保至少执行一次循环。");
} while( true );
```

C# 数据类型
---------------------

### 原始数据类型
<!--rehype:wrap-class=col-span-2-->

| 关键字 | 名称         | System 别名 | 占用空间（Byte） | 数据范围                                 |
| ------ | ------------ | ----------- | ---------- | ---------------------------------------- |
| `bool`   | 布尔型       | `Boolean`     | 1          | true/false                               |
| `sbyte`  | 有符号字节型 | `SByte`       | 1          | -128 ~ 127                               |
| `byte`   | 字节型       | `Byte`        | 1          | 0 ~ 255                                  |
| `short`  | 短整型       | `Int16`       | 2          | -32,768 ~ 32,767                         |
| `ushort` | 无符号短整型 | `UInt16`      | 2          | 0 ~ 65,535                               |
| `int`    | 整型         | `Int32`       | 4          | -2,147,483,648 ~ 2,147,483,647           |
| `uint`   | 无符号整型   | `UInt32`      | 4          | 0 ~ 4,294,967,295                        |
| `long`   | 长整型       | `Int64`       | 8          | -2^63 ~ 2^63-1                           |
| `ulong`  | 无符号长整型 | `UInt64`      | 8          | 0 ~ 2^64-1                               |
| `char`   | 字符型       | `Char`        | 8          | UTF-16 所编码的字符                      |
| `float`  | 单精度浮点型 | `Single`      | 4          | ±1.5x10^45 ~ ±3.4x10^38                  |
| `double` | 双精度浮点型 | `Double`      | 8          | ±5.0x10^-324 ~ ±1.7x10^308               |
| `nint`   | 指针型       | `IntPtr`      | 与指针相同 | 与指针相同（受操作系统和处理器位宽影响） |
| `nuint` | 无符号指针型 | `UIntPtr`     | 与指针相同 | 与指针相同（受操作系统和处理器位宽影响） |
<!--rehype:className=show-header-->

### 基本数据类型

关键字 | 名称 | System 别名 | 说明
:------ | ------ | ------ | ------
(除指针型外的全部原始数据类型) | - | - | 原始数据类型都是值类型，基本数据类型包含部分本质上是引用的数据类型
`string` | 字符串 | `String` | 可变长度
`decimal` | 十进制浮点数 | `Decimal`     | 适合处理货币等计算，16字节长，不遵循 IEEE 754 关于浮点数的规则
<!--rehype:className=show-header-->

C# 字符串
----------------

### 字符串连接

```cs
string first = "John";
string last = "Doe";
string name = first + " " + last;
Console.WriteLine(name); // => John Doe
```

### 字符串插值

```cs
string first = "John";
string last = "Doe";
string name = $"{first} {last}";
Console.WriteLine(name); // => John Doe
```

### 字符串成员
<!--rehype:wrap-class=row-span-2-->

成员 | 说明
:- | -
`Length`    | 返回字符串长度的属性
`Compare()`   | 比较两个字符串的静态方法
`Contains()`  | 确定字符串是否包含特定的子字符串
`Equals()`    | 确定两个字符串是否具有相同的字符数据
`Format()`    | 通过 {0} 表示法和使用其他原语格式化字符串
`Trim()`      | 从尾随和前导字符中删除特定字符的所有实例。 默认删除前导和尾随空格
`Split()`     | 删除提供的字符并从两侧的剩余字符中创建一个数组
<!--rehype:className=show-header-->

### 逐字字符串

```cs showLineNumbers
string longString = @"I can type any characters in here !#@$%^&*()__+ '' \n \t except double quotes and I will be taken literally. I even work with multiple lines.";
```
<!--rehype:className=wrap-text-->

### 成员示例

```cs
// 使用 System.String 的属性
string lengthOfString = "How long?";
lengthOfString.Length           // => 9
// 使用 System.String 的方法
lengthOfString.Contains("How"); // => true
```

### 频繁字符串拼接

```cs
var sb = new StringBuilder();
for (int i = 0; i < 100; i++)
{
    sb.Append(i.ToString());
}
Console.WriteLine(sb.ToString());
// => 123456789....
```

对于频繁拼接字符串的场景（如：成百上千次循环），使用 `System.Text.StringBuilder` 提升性能

### 原始字符串文本
<!--rehype:wrap-class=col-span-2-->

```cs
// C#11 语法, 至少3个双引号(""")开头和结尾，内容可以输入任何原始字符
// 单行: 左引号，右引号，内容 三者同行
string singleLine = """Content begin "Hello World!" end.""";

// 多行：左引号，右引号各一行，内容需与右引号缩进对齐
string multiLine = """
    Content begin "Hello World!" /\n<>"" end.
    """;
Console.WriteLine(multiLine); // => Content begin "Hello World!" /\n<>"" end.
```

### 字符串操作

#### 字符串判空

```cs
string name; //空引用
string gender = ""; //空值

// 使用 string.IsNullOrEmpty(字符串) 方法，返回 bool 型
Console.WriteLine(string.IsNullOrEmpty(name)); //输出 true
Console.WriteLine(string.IsNullOrEmpty(gender)); // 输出 true
```

#### 字符串分割

```cs
string Name = "字A符A串A分A割";
string[] Names=Name.Split(new char[] { 'A' });
//会以A为媒介把字符串分成若干份
for (int i = 0; i < Names.Length; i++)
{
    Console.Write(Names[i]);
}
```

#### 字符串截取

```cs
string Str = "字符串截取";
Str = Str.Substring(2, 1);
Console.WriteLine(Str);
//输出结果“串”，意为从第二个下标开始截取一位字符
```

#### 字符串替换

```cs
string Rep = "字符1替换";
Rep = Rep.Replace("1", "串");
Console.WriteLine(Rep);
//会把字符中的 “1”替换成“串”
```

### 逻辑运算
<!--rehype:wrap-class=col-span-2-->

```cs
//或运算, 与运算, 非运算
bool A = true;
bool B = false;
bool Or = A || B; // = A | B
bool And = A && B; // = A & B
bool Not = !A;
// ||,&& 与 |,& 分别为逻辑运算和条件逻辑运算, 两者的区别在于, 
// 前者仅在必要时才会计算右侧的值, 后者始终计算右侧的值. 例如:
bool C = false;
bool D = true;
bool CalcD() {
  D = !D;
  return D;
}
bool E = C && CalcD(); // C: false, D: false, E: false
bool F = C & CalcD(); // C:false, D: true, F: false
// 两种运算方法稍有不同, 计算结果始终相同, 但第二种可能造成其他影响.
//异或运算
bool Xor = A ^ B;
```

C# 中的逻辑运算支持可空布尔类型运算. 注意条件逻辑运算不支持可空布尔类型.

x |  y | x & y | x \| y | x ^ y | ! x
:- | - | --- | --- | --- | --
true | true | true | true | false | false
true | false | false | true | true | false
true | null | null | true | null | false
false | true | false | true | true | true
false | false | false | false | false | true
false | null | false | null | null | true
null | true | null | true | null | null
null | false | false | null | null | null
null | null | null | null | null | null
<!--rehype:className=show-header-->

### 算术运算符
<!--rehype:wrap-class=col-span-1-->

C# 支持下表中的所有算术运算符。假设变量 A 的值为 10，变量 B 的值为 20，则：

| 运算符 | 描述                             | 实例              |
| :----- | -------------------------------- | ----------------- |
| +      | 把两个操作数相加                 | A + B 将得到 30   |
| -      | 从第一个操作数中减去第二个操作数 | A - B 将得到 -10  |
| \*     | 把两个操作数相乘                 | A \* B 将得到 200 |
| /      | 分子除以分母                     | B / A 将得到 2    |
| %      | 取模运算符，整除后的余数         | B % A 将得到 0    |
| ++     | 自增运算符，整数值增加 1         | A++ 将得到 11     |
| --     | 自减运算符，整数值减少 1         | A-- 将得到 9      |
<!--rehype:className=show-header-->

### 关系运算符
<!--rehype:wrap-class=col-span-2-->

C# 支持下表中的所有关系运算符。假设变量 A 的值为 1，变量 B 的值为 2，则：

| 运算符 | 描述                                                           | 实例              |
| :----- | -------------------------------------------------------------- | ----------------- |
| ==     | 检查两个操作数的值是否相等，如果相等则条件为真。               | (A == B) 不为真。 |
| !=     | 检查两个操作数的值是否相等，如果不相等则条件为真。             | (A != B) 为真。   |
| >      | 检查左操作数的值是否大于右操作数的值，如果是则条件为真。       | (A > B) 不为真。  |
| <      | 检查左操作数的值是否小于右操作数的值，如果是则条件为真。       | (A < B) 为真。    |
| >=     | 检查左操作数的值是否大于或等于右操作数的值，如果是则条件为真。 | (A >= B) 不为真。 |
| <=     | 检查左操作数的值是否小于或等于右操作数的值，如果是则条件为真。 | (A <= B) 为真。   |
<!--rehype:className=show-header-->

### 运算符优先级
<!--rehype:wrap-class=col-span-3-->

运算符的优先级确定表达式中项的组合。这会影响到一个表达式如何计算。某些运算符比其他运算符有更高的优先级，例如，乘除运算符具有比加减运算符更高的优先级。

下表将按运算符优先级从高到低列出各个运算符，具有较高优先级的运算符出现在表格的上面，具有较低优先级的运算符出现在表格的下面。在表达式中，较高优先级的运算符会优先被计算。

| 类别       | 运算符                             | 结合性   |
| :--------- | ---------------------------------- | -------- |
| 后缀       | () [] -> . ++ - -                  | 从左到右 |
| 一元       | + - ! ~ ++ - - (type)\* & sizeof   | 从右到左 |
| 乘除       | \* / %                             | 从左到右 |
| 加减       | + -                                | 从左到右 |
| 移位       | << >>                              | 从左到右 |
| 关系       | < <= > >=                          | 从左到右 |
| 相等       | == !=                              | 从左到右 |
| 位与 AND   | &                                  | 从左到右 |
| 位异或 XOR | ^                                  | 从左到右 |
| 位或 OR    | \|                                 | 从左到右 |
| 逻辑与 AND | &&                                 | 从左到右 |
| 逻辑或 OR  | \|\|                               | 从左到右 |
| 条件       | ?:                                 | 从右到左 |
| 赋值       | = += -= \*= /= %=>>= <<= &= ^= \|= | 从右到左 |
| 逗号       | ,                                  | 从左到右 |
<!--rehype:className=show-header-->

杂项
-----------

### 常用 .NET 概念
<!--rehype:wrap-class=col-span-3-->

概念 | 中文名 | 定义
:- | -|--
`Runtime` | 运行时 | 执行给定的已编译代码单元所需的服务集合
`Common Language Runtime (CLR)` | 通用语言运行库 | 主要定位、加载和托管 .NET 对象。<br/>CLR 还处理内存管理、应用程序托管、线程协调、执行安全检查和其他低级细节
`Managed code` | 托管代码 | 在 `.NET` 运行时编译和运行的代码。 C#/F#/VB 就是例子
`Unmanaged code` | 非托管代码 | 直接编译为机器代码且不能由 .NET 运行时直接托管的代码。<br/>不包含空闲内存管理、垃圾收集等。从 C/C++ 创建的 DLL 就是示例
<!--rehype:className=show-header-->
