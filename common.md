[TOC]

[1 前言](#user-content-1-前言)

[2 代码风格](#user-content-2-代码风格)

　　[2.1 结构](#user-content-21-结构)

　　　　[2.1.1 缩进](#user-content-211-缩进)

　　　　[2.1.2 空格](#user-content-212-空格)

　　　　[2.1.3 空行](#user-content-213-空行)

　　　　[2.1.4 换行](#user-content-214-换行)

　　[2.2 命名](#user-content-22-命名)

　　[2.3 注释](#user-content-23-注释)

[3 语言特性](#user-content-3-语言特性)

　　[3.1 变量](#user-content-31-变量)

　　[3.2 语句](#user-content-32-语句)

　　[3.3 函数](#user-content-33-函数)

[4 附录](#user-content-4-附录)

# 通用编码规范

## 1 前言

### 1.1 说明

有些编程规范是大部分编程语言通用的，特把它独立出来。

示例中我采用 Java 语言。有时也混杂其他语言。

本编码规范完全适用于 Java 和 Javascript 的编程规范，对其他语言也有借鉴作用。

### 1.2 好的编码规范

什么样的规范才算是好的编程规范？

“大家好，才是真的好”。不是你觉得好就是好，而是绝大部分人都觉得这个编程规范好，才是一份好的规范。当然，如果你的编程风格与主流的不符合，我的建议是：强迫自己改正。

本编程规范主要参考 Google Java 编程规范，并且**绝大部分规范符合谷歌编程规范**，除了以下几点与其不同：

1. 代码缩进。谷歌建议缩进 2 个空白符；本规范建议缩进 4 个空白符。
2. 好像没了？想到再补充。

此外，本规范还参考了百度等互联网大公司的编程规范，主要是对谷歌编程规范的补充（谷歌编程规范不够详细，所涉及的规范主要是编程风格的）

当然，也有一些个人的见解。

### 1.3 基本准则

##### [建议] 坚持一致原则

维护别人写的代码，应当遵守一致原则。即修改后的代码的编程风格应该与之前的代码一致。

### 使用必读

不同的要求严格程度不同，参照 RFC2119 分成三个等级：

1. `[强制]` 表示必须（MUST）或者不允许（MUST NOT）这样做。

2. `[建议]` 表示一般情况下应该（SHOULD）或者不应该（SHOULD NOT）这样做，但是在某些特定情况下可以忽视这个要求。

3. `[可选]` 表示这个要求完全是可选的，你可以（MAY）这样做，也可以不这样做，视个人喜好而定。


## 2 代码风格

### 2.1 结构

#### 2.1.1 缩进

##### [强制] 采用 4 个空格缩进而不是 2 个空格或 tab 字符

虽然谷歌推荐 2 个空格的缩进，但 4 个空格缩进的代码可读性明显更强。现在很多代码编辑器支持输入时自动把 tab 字符转化为 4 个空格符。

每当开始一个新的块，缩进增加2个空格，当块结束时，缩进返回先前的缩进级别。缩进级别适用于代码和注释。

```
// good
void foo() {
    int a = 0;
}

// bad
  int a = 0;
}
```

##### [强制] 所有的块状结构都要缩进

```
void foo() {
    if (condition) {
        // statement        
    }
}
```

##### [强制] switch 语句缩进要合理

```
switch (foo) { 
    case 1: 
        // code
        break; 
    case 1: 
        // code 
        break; 
    default: 
        break; 
}
```

#### 2.1.2 空格

##### [强制] 注释时，注释符两边的空白符必不可少

* 双斜杠后面的空格必不可少。
* 如果在一条语句后做注释，则双斜杠两边都要一个空格。
* 可以允许多个空格，但没有必要。

```
// good
int foo = 0; // 这是一个注释示例
/* 这是一个注释示例 */
/** 这是一个注释示例 */

// bad
int foo = 0; //这是一个注释示例
int foo = 0;// 这是一个注释示例
/*这是一个注释示例*/
/**这是一个注释示例*/
```

##### [强制] 任何保留字（如if, while for等等）与紧随其后的左括号之间要有一个空格

```
// good
if (foo == 0) {

}

// bad
if(foo == 0) {

}
```

##### [强制] 任何保留字(如else、catch等)与其前面的右大括号之间要有一个空格

```
// good
if (foo == 0) {

} else {

}

// bad
if(foo == 0) {

}else {

}
```

##### [强制] 任何左大括号 `{` 前必须加一个空格

两个例外：
* @SomeAnnotation({a, b})(不使用空格)。
* String[][] x = foo;(大括号间没有空格)。

##### [强制] 在任何二元或三元运算符的两侧必须有空格

这也适用于以下“类运算符”符号：
类型界限中的&(<T extends Foo & Bar>)。
catch块中的管道符号(catch (FooException | BarException e)。
foreach语句中的分号。

```
// good
int i = 1 + 2;

// bad
int i = 1+2;
```

##### [强制] 一元运算符与操作对象之间不允许有空格

```
// good
if (!isOk) {
}

i++;

// bad
if (! isOk) {
}

i ++;
```

##### [强制] 在 `,`、`:`、`;` 及右括号 `)` 后必须空格

```
for (int i = 0; i < 100; i++) {

}

int i = (int) 3.5f;
```

##### [建议] 数组初始化中，大括号内的空格是可选的

```
new int[] {5, 6};

new int[] { 5, 6 };
```
##### [强制] 行尾不得有多余的空格

##### [强制] 本规范没有要求的空格不要随便乱加

几个经典的错误例子：

```
// good
void foo(int i) {}

// bad
void foo (int i) {}

// bad
void foo( int i) {}

// bad
void foo(int i ) {}
```

##### [建议] 水平对齐，没这个必要，也不建议这么做

虽然增加了代码的可读性，但给维护带来问题。很多时候为了保持对齐，做了一些无用功。所以即使对于已经使用水平对齐的代码，我们也不需要去保持这种风格。


```
// good
int foo = 1;
String s = "foo";

// bad
int        foo = 1;
String    s = "foo";
```

#### 2.1.3 空行

##### [强制] 类内连续成员之间，必须有 1 个空行

类内连续的成员（字段，构造函数，方法，嵌套类，静态初始化块，实例初始化块等）之间，必须有一个空行

例外：两个连续字段之间的空行是可选的，用于字段的空行主要用来对字段进行逻辑分组。

##### [建议] 类内的第一个成员前或最后一个成员后的空行是可选的

既不鼓励也不反对这样做，视个人喜好而定。


##### [建议] 多个连续的空行是允许的，但没必要这样做，也不推荐这样做

##### [建议] 在函数体内，语句的逻辑分组间使用空行

这样做可增强代码的可读性

##### [建议] 没意义的空行不要乱加

#### 2.1.4 换行 

##### [强制] 列限制：80、100，还是 120？

一个项目可以选择一行80个字符或100个字符的列限制。

我推荐 100 个字符。

任何一行如果超过这个字符数限制，必须换行。

例外：

不可能满足列限制的行(例如，Javadoc中的一个长URL，或是一个长的JSNI方法参考)。
package和import语句(见3.2节和3.3节)。
注释中那些可能被剪切并粘贴到shell中的命令行。

##### [建议] 自动换行的基本准则是：更倾向于在更高的语法级别处断开


##### [强制] 如果在非赋值运算符处断开，那么在该符号前断开

这条规则也适用于以下“类运算符”符号：点分隔符(.)，类型界限中的&（<T extends Foo & Bar>)，catch块中的管道符号(catch (FooException | BarException e)

```
// good
int i = 1 + 2 + 3 + ... + 1000000
    + 1000001；

// bad
int i = 1 + 2 + 3 + ... + 1000000 + 
    1000001；
```

##### [强制] 如果在赋值运算符处断开，通常的做法是在该符号后断开

这条规则也适用于foreach语句中的分号
```
// good，虽然在这里没必要换行
int i = 
    100000000;

// bad
int i
    = 100000000;
```

##### [强制] 自动换行时函数名与左括号留在同一行

##### [强制] 自动换行时逗号(,)与其前面的内容留在同一行

##### [强制] 自动换行时第一行后的每一行至少比第一行多缩进 4 个空格

##### [强制] 非空块得换行遵守 K & R 风格


对于非空块，大括号遵循Kernighan和Ritchie风格 (Egyptian brackets):

* 左大括号前不换行
* 左大括号后换行
* 右大括号前换行
* 如果右大括号是一个语句、函数体或类的终止，则右大括号后换行; 否则不换行。例如，如果右大括号后面是else或逗号，则不换行。

Java的enum类有一些例外，在 Java 编程规范讲解。

```
// good
class Foo {
    public void foo() {
        if (condition) {
            something();
        } else {
            other();
        }
    }
}

// bad
class 
{    
}

// bad
if (condition)
{
    something();
}
else
{
    other();
}
```

##### [可选] 空块可以用简洁版本，不换行

一个空的块状结构里什么也不包含，大括号可以简洁地写成{}，不需要换行。

例外：如果它是一个多块语句的一部分(if/else 或 try/catch/finally) ，即使大括号内没内容，右大括号也要换行。

```
void doNothing() {} 
```

#### 括号

##### [强制] 函数的返回值不可以用括号包住

不然会降低可读性。

```
// good
return count + 100;

// bad
return (count + 100); 
```

##### [强制] 任何标识符的命名都不能采用拼音

```
// good
class Student {}

// bad
class Xuesheng {}
```

### 2.2 命名

#### 2.2.1 通用命名

##### [建议] 良好的命名应该是自解释的

良好的命名应该能够顾名思义，不需要注释

```
// good
int studentCount;

// bad
int count; // 学生数量
```

##### [建议] 谨慎使用缩略词

不常见的缩略词会降低代码的可读性。尽量避免缩写，除非该缩写是众所周知的，如HTML、URL等等。

```

```

##### [建议] 命名应该是简短且有意义的

```

```

#### 2.2.2 编程语言中的命名

##### [强制] 类名、接口名以 UpperCamelCase 风格编写

```
// good
class Foo {...}

// bad
class foo {...}
```

##### [强制] 类名使用名词或名词短语

##### [建议] 接口使用形容词或形容词短语


接口命名多以able或ible结尾

```
interface Runable {...}

interface Accessible {...}
```


##### [强制] 测试类的命名以它要测试的类的名称开始，以 Test 结束

```
class HashTest {
}

HashIntegrationTest {
}
```

##### [强制] 方法名以 lowerCamelCase 风格编写

##### [建议] 方法名使用动宾短语

也可以使用动词。

下划线可能出现在JUnit测试方法名称中用以分隔名称的逻辑组件。一个典型的模式是：test<MethodUnderTest>_<state>，例如testPop_emptyStack。 并不存在唯一正确的方式来命名测试方法。

```
// good
void initView() {}

void updateData() {}

// not good
void init() {}

void update() {}
```

##### [强制] 常量名以 CONSTANT_CASE 风格编写

全部字母大写，用下划线分隔单词。

那，到底什么算是一个常量？

每个常量都是一个静态final字段，但不是所有静态final字段都是常量。在决定一个字段是否是一个常量时， 考虑它是否真的感觉像是一个常量。例如，如果任何一个该实例的观测状态是可变的，则它几乎肯定不会是一个常量。 只是永远不打算改变对象一般是不够的，它要真的一直不变才能将它示为常量。

```
// Constants
static final int NUMBER = 5;
static final ImmutableList<String> NAMES = ImmutableList.of("Ed", "Ann");
static final Joiner COMMA_JOINER = Joiner.on(',');  // because Joiner is immutable
static final SomeMutableType[] EMPTY_ARRAY = {};
enum SomeEnum { ENUM_CONSTANT }

// Not constants
static String nonFinal = "non-final";
final String nonStatic = "non-static";
static final Set<String> mutableCollection = new HashSet<String>();
static final ImmutableSet<SomeMutableType> mutableElements = ImmutableSet.of(mutable);
static final Logger logger = Logger.getLogger(MyClass.getName());
static final String[] nonEmptyArray = {"these", "can", "change"};
```

这些名字通常是名词或名词短语。

##### [建议] 减少代码中的硬编码

代码中不允许出现直接硬编码的字面常量， 尤其是 **重复出现** 的硬编码。

你需要做的是把硬编码定义成常量。

如果常量只在一个类中用到，则在类中定义。否则可以在公共类中定义常量。

##### [强制] 常量必须用常量修饰符修饰

```
// good
final int MAX_COUNT = 99;

// bad
int int MAX_COUNT = 99;
```

##### [强制] 非常量字段名以 lowerCamelCase 风格编写

这些名字通常是名词或名词短语。

##### [强制] 参数名以 lowerCamelCase 风格编写。

参数应该避免用单个字符命名。

##### [强制] 局部变量名以 lowerCamelCase 风格编写

比起其它类型的名称，局部变量名可以有更为宽松的缩写。

虽然缩写更宽松，但还是要避免用单字符进行命名，除了临时变量和循环变量。

即使局部变量是final和不可改变的，也不应该把它示为常量，自然也不能用常量的规则去命名它。

允许在循环中使用单个字符的变量

避免在多重循环中同时使用 i 和 j 这种容易混淆的变量名


##### [建议] 类型变量可用以下两种风格之一进行命名

* 单个的大写字母，后面可以跟一个数字(如：E, T, X, T2)。
* 以类命名方式(5.2.2节)，后面加个大写的T(如：RequestT, FooBarT)。

##### [建议] boolean 类型的变量命名以 is 或 has 开头

```
// good
boolean isReady = false;

// bad
boolean ready = false;
```

##### [建议] 集合、数组类型的变量，常用名词复数

```
// good
Student student;
Student[] students;
List<Student> students;

// not good
List<Student> someStudent;

// bad
List<Student> list;
```


### 2.3 注释

这里的注释不包括文档注释

##### [强制] 单行注释用 `//` 而不是 `/* */`

##### [强制] 块注释与其周围的代码在同一缩进级别

```
// good
if (condition) {
    // 这是一段注释
    something();
}

// bad
if (condition) {
// 这是一段注释
    something();
}
```

##### [强制] 多行注释可以是/* ... */风格，也可以是// ...风格。对于多行的/* ... */注释，后续行必须从*开始， 并且与前一行的*对齐

```
/* 这是一段很长很长很长...................很长
 * 很长很长的注释。
 */

// 这也是一段很长很长很长...................很长
// 很长很长的注释。

/* 我不会告诉你这三种写法都是
 * 可以的 */
```

##### [强制] 注释不要封闭在由星号或其它字符绘制的框架里。

这样做很可能给维护带来不必要的麻烦

```
// bad
/****************************************
 * 这是一个
 *         很漂亮但是没什么卵用注释
 ***************************************/

```

##### [建议] 禁止没意义的注释

```
// bad
int foo; // 定义一个变量

// 创建一个Foo类
class Foo {

}
```

为什么这里是建议，而不是强制？因为很多时候，判断一句注释是不是废话还跟开发者水平有关。

举个不是很恰当的例子：

```
// bad
// 创建一个线程并执行
new Thread(new Runnable() {
    public void run() {
        something();
    }
}).start();
```

稍微懂点 Java 的都知道这句注释是句废话，但对于一个刚入门，没接触过多线程的就不这么认为了，后面这条建议是对本条建议的补充说明：

##### [建议] 注释一般不包含语言本身的语法、语言内置的API的说明、第三方类库（如 Spring 等）某个函数的用法的说明

不懂的去看相应的开发文档。

##### [建议] 对整段代码进行注释说明，而不是逐行注释

##### [建议] 只进行必要的注释，注释不是越多越好

## 3 语言特性

### 3.1 变量

##### [强制] 每次只声明一个变量

```
// good
int foo;
int foo2;

// bad
int foo, foo2;

// bar
var foo = 1,
    foo2 = 2,
    foo3 = 3;
```

##### [强制] 需要时才声明，并尽快进行初始化

不要在一个代码块的开头把局部变量一次性都声明了，而是在第一次需要使用它时才声明。 局部变量在声明时最好就进行初始化，或者声明后尽快进行初始化。

变量声明与使用的距离越远，代码的阅读与维护成本就越高。

从优化方面讲，这样做也是有好处的。

##### [建议] 尽量使用局部变量

Java：
> 尽量使用局部变量，调用方法时传递的参数以及在调用中创建的临时变量都保存在栈（Stack）中，速度较快。其他变量，如静态变量、实例变量等，都在堆（Heap）中创建，速度较慢。另外，依赖于具体的编译器/JVM，局部变量还可能得到进一步优化

##### [建议] 变量在真正需要的时候才开始创建

```
// good
if (i == 1) {
    String str = "abc";
    list.add(str);
}

// bad
String str = "abc";
if (i == 1) {
    list.add(str);
}
```

### 3.2 语句

##### [强制] 一行最多一个语句

```
// good
int foo;
int foo2;

// bad
int foo; int foo2;
```

##### [强制] 禁止连续赋值

连续赋值不仅影响可读性，而且很多时候容易出错。

```
// good
a = 1;
b = 1;
c = 1;

a = b = c = 1;
```

##### [建议] 避免深层嵌套

多级嵌套降低了代码的可读性。

##### [强制] 使用大括号，即使大括号是可选的

大括号与if, else, for, do, while语句一起使用，即使只有一条语句(或是空)，也应该把大括号写上。

```
// good
if (i > 0) {
    i++;
}

// bad
if (i > 0)
    i++;
```

### 条件

##### [可选] 对于相同变量或表达式的多值条件，用 switch 代替 if

```
// good
switch (i) {
    case 1:
        // ......
        break;
    case 2:
    case 3:
    case 4:
        // ......
        break;
}

// bad
if (i == 1) {
    // ......
} else if (i == 1 || i == 2 || i == 3) {
    // ......
}
```

##### [可选] 如果函数或全局中的 else 块后没有任何语句，可以删除 else

```
// good
function getName() {
    if (name) {
        return name;
    }

    return 'unnamed';
}

// bad
function getName() {
    if (name) {
        return name;
    } else {
        return 'unnamed';
    }
}
```

### 循环

##### [建议] 避免在循环中重复获取长度

```java
// bad
for (int i = 0; i < list.size(); i++) {
}

// good
for (int i = 0, int size = list.size(); i < size; i++) {
}

// good
int size = list.size();
for (int i = 0, ; i < size; i++) {
}
```

##### [建议] 嵌套循环将小循环写在外层

```
// good
for (int i = 0; i < 5; i++) {
    for (int k = 0; k < 5000; k++) {
    }
}

// bad
for (int k = 0; k < 5000; k++) {
    for (int i = 0; i < 5; i++) {
    }
}
```

##### [建议] 避免在循环中做耗时的工作

* 循环中不要使用try-catch()语句
* 不要在循环中调用synchronized(同步)方法
* 循环中不要频繁声明对象，对象可以在循环外创建
* 循环中尽量避免数据库查询操作等耗时的操作
* ......



### 3.3 函数

##### [建议] 函数的长度控制在 50 行以内

太长的函数难以维护。

关于一个函数的规范行数没有统一标准，40行、60行也可以。

##### [建议] 函数的参数控制在 6 个以内

### 面向对象

##### [强制] 除非必要，否则不允许使用 public 修饰类的属性


## 4 附录

### 4.1 驼峰式命名法（CamelCase）

驼峰式命名法分大驼峰式命名法(UpperCamelCase)和小驼峰式命名法(lowerCamelCase)。 有时，我们有不只一种合理的方式将一个英语词组转换成驼峰形式，如缩略语或不寻常的结构(例如"IPv6"或"iOS")。Google指定了以下的转换方案。

名字从散文形式(prose form)开始:

把短语转换为纯ASCII码，并且移除任何单引号。例如："Müller’s algorithm"将变成"Muellers algorithm"。
把这个结果切分成单词，在空格或其它标点符号(通常是连字符)处分割开。
推荐：如果某个单词已经有了常用的驼峰表示形式，按它的组成将它分割开(如"AdWords"将分割成"ad words")。 需要注意的是"iOS"并不是一个真正的驼峰表示形式，因此该推荐对它并不适用。
现在将所有字母都小写(包括缩写)，然后将单词的第一个字母大写：最后将所有的单词连接起来得到一个标识符。
每个单词的第一个字母都大写，来得到大驼峰式命名。
除了第一个单词，每个单词的第一个字母都大写，来得到小驼峰式命名。
示例：

：

```
// good
XmlHttpRequest // XML HTTP request
newCustomerId // new customer ID
innerStopwatch // inner stopwatch
supportsIpv6OnIos // supports IPv6 on iOS
YouTubeImporter // YouTube importer
YoutubeImporter // 不推荐

// bad
XMLHTTPRequest
newCustomerID
innerStopWatch
supportsIPv6OnIOS
```


Note：在英语中，某些带有连字符的单词形式不唯一。例如："nonempty"和"non-empty"都是正确的，因此方法名checkNonempty和checkNonEmpty也都是正确的。