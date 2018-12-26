# 总则

---

- 编码以易读，易理解，美观为要。  
- 修改现有代码，坚持最小修改原则，重构代码除外。
- 对于二次开发，比如Android的bugfix 和 feature 开发，注意保持和原始代码的风格一致。  
- 一个文件中只定义一个类\(或接口\)，根据需要的内部类和接口除外。

易读就意味着：
- 逻辑相关的代码在一起
- 作用域尽量小
- 方法尽量短小

# 文件

---

### 1. 文件名

文件名就是类名\(或接口\),.java 为文件后缀。

### 2. 文件编码

1.UTF-8  
2.换行为UNIX风格

# 排版

---

### 1. 文件结构
一个源文件包含\(按顺序且每个部分之间用一个空行隔开,类注释和类之间无空行\)：
* 许可证或版权信息\(可选\)
* package语句
* import语句
* 类注释\(可选\)
* 类

#### 1.1.许可证或版本

放在源文件最前面，格式如下

```
/*
 * Copyright (C) 2017, CK TELECOM
 * 
 * Description Line 1
 * Description Line 2
 */
```

第一行，只有**/\***;  
第二行起，**\***和第一行的对齐，也就是说要行前有一个空格;  
最后一行只有** \*/**;

#### 1.2.package声明

package语句不换行，如果太长请考虑重新命名。  
包名统一使用小写，点分隔符之间有且仅有一个自然语义的英语单词。  
包名统一使用单数形式，但是类名如果有复数含义，类名可以使用复数形式。  
示例：

```
com.ckt.xxx
com.sioeye.xxx
```

#### 1.3.import声明

import语句不换行；  
不能使用通配符，不管是否是静态导入，即，不要出现类似这样的import语句：import java.util.\*;

import语句可分为以下几组，按照这个顺序，每组由一个空行分隔：
* 第三方的包。每个顶级包为一组，字典序。例如：android, com, junit, org, sun
* java imports
* javax imports
* 所有的静态导入为一组 

  **组内不空行，按ASCII码排序。**

如果是修改源文件，和原始风格保持一致，比如有些Android源码的静态导入包的位置可能在最前面。

#### 1.4.顶级类/接口

成员应该按照某种逻辑顺序排列;  
重载方法应该放在一起;

### 2. 格式
#### 2.1.文件中的空白字符只能是空格和换行符  
字符串，文本段等需要其它特殊空白字符情况除外，这里主要强调格式。
#### 2.2.代码块的缩进是4个空白字符  
#### 2.3.行长度为100字符  
#### 2.4.断行(Line-wrapping)的原则就是易读,缩进8个字符
1.一般在非赋值语句前断行，例
```
Slog.d(TAG, "updateSettingsLocked: mScreenBrightnessModeSetting="
                    + mScreenBrightnessModeSetting);
```
2.一般在赋值语句后面断开，例
```
mWakeLockSuspendBlocker = 
                    createSuspendBlockerLocked("PowerManagerService.WakeLocks");
```
3.在调用函数或者构造函数需要断行时，与函数名相连的左括号要在一行。也就是在左括号之后断行。
4.逗号断行时，在逗号之后断行。
5.lambda的箭头前后一般不断行  
```
// 一般
MyLambda<String, Long, Object> lambda =
    (String label, Long value, Object obj) -> {
        ...
    };

// 特例
Predicate<String> predicate = str ->
    longExpressionInvolving(str);

```

#### 2.5.一条语句一行
不要有如下代码,一条语句就一行。
```
int a, b;
a = b + 3; b++;
```
#### 2.6.大括号格式
大括号不能省略，即使只有一行代码或者空代码块
- 左大括号前面不换行，在后面换行
- 右大括号之前换行
- 如果右括号结束一个语句块或者函数体、构造函数体或者有命名的类体，则需要换行，否则不换行，如，当右括号后面接else或者逗号时，不应该换行
- 一个空的语句块，可以在左花括号之后直接接右花括号，中间不需要空格或换行

**  Enum请特殊对待。**  

#### 2.7.空行使用
单行空行在以下情况使用：
1.类成员间需要空行隔开：例如成员变量、构造函数、成员函数、内部类、静态初始化语句块（static initializers）、实例初始化语句块（instance initializers）。注意：成员变量之间的空白行不是必需的。一般多个成员变量中间的空行，是为了对成员变量做逻辑上的分组。
2.在函数内部，根据代码逻辑分组的需要，设置空白行作为间隔。
3.类的第一个成员之前，或者最后一个成员结束之后，不用空行间隔。 
4.本文档中其他部分介绍的需要空行的情况。

#### 2.8.空格使用
除了语法、其他规则、词语分隔、注释和javadoc外，水平的ASCII空格只在以下情况出现：
 
1.所有保留的关键字与紧接它之后的位于同一行的左括号之间需要用空格隔开。（例如if、for、catch）
2.所有保留的关键字与在它之前的右大括号之间需要空格隔开。（例如else、catch）
3.在左大括号之前都需要空格隔开。只有两种例外：
```@SomeAnnotation({a, b})```
```String[][] x = {{"foo"}};```
4.所有的二元运算符和三元运算符的两边，都需要空格隔开。包括下面类似运算符的情况
(&): ```<T extends Foo & Bar>```
(|): ```catch (FooException | BarException e)```
(:): ```for (String ac : accountTypesWithManagementDisabled)```
(->): ```(String str) -> str.length()```
5.逗号、冒号、分号和右括号之后，需要空格隔开。
6.// 双斜线开始一行注释时。双斜线两边都应该用一个空格隔开。
7.变量声明时，变量类型和变量名之间需要用空格隔开。
8.初始化一个数组时，如果只要一行请用如下格式
```new int[] {5, 6}```
 
注意：这一原则不影响一行开始或者结束时的空格。只针对行内部字符之间的隔开。

#### 2.9.不要水平对齐
水平对齐，是指通过添加多个空格，使本行的某一符号与上一行的某一符号上下对齐。

以下是没有水平对齐和水平对齐的例子

```
// 请这样
private int x;    
private Color color;    
```
``` 
// 禁止水平对齐
private int      x;          
private Color color;     
```
#### 2.10.分组括号建议多用
分组括号可以使用，也可以不用。请以清晰和美观为前提。
比如，运算符优先级不是所有人都清楚，但是常见的也没必要添加
任何reviewer对需要分组的地方有疑惑，作者就有义务重新修改代码，添加分组。


#### 2.11.特殊格式
**1. 数组**
数组的初始化建议用采用多行形式，即使目前只有一个元素。
```
// 多行，断行缩进
int[] array = new int[] {
        1,
        2,
        3,
        4
};

// 单行
int[] array = new int[] {1, 2, 3, 4};
```

**2.枚举类**
按照数组的方式处理即可，又因为可以有方法，是一个类，故类的格式要求也适用于枚举。
```
private enum Answer {
        YES {
                @Override public String toString() {
                   return "yes";
                }
            },

        NO,
        MAYBE
}
```
**3.switch 语句**
- 按照块缩进，即4个空格  
- 每个标签对应的代码执行完后，都应该通过语句结束（例如：break、continue、return 或抛出异常），否则应该通过注释说明，代码需要继续向下执行下一个标签的代码。注释说明文字只要能说明代码需要继续往下执行都可以（通常是 //fall through）。
- 每个switch语句中，都需要显式声明default标签。即使没有任何代码也需要显示声明。
```
switch (input) {
    case 1:
    case 2:
        prepareOneOrTwo();
        // fall through
    case 3:
        handleOneTwoOrThree();
        break;
    default:
        handleLargeNumber(input);
}
```

**4.注解(Annotations)格式**
Annotations应用到类、函数或者构造函数时，应紧接javadoc之后。每一行只有一个Annotations。
Annotations所在行不受行长度限制，也不需要增加缩进。例如：
``` 
@Override
@Nullable
public String getNameIfPresent() { ... }
```
例外情况：
如果Annotations只有一个，并且不带参数。则它可以和类或方法名放在同一行。例如：
```
@Override public int hashCode() { ... }
```
 
Annotations应用到成员变量时，也是紧接javadoc之后。不同的是，多个annotations可以放在同一行。例如：
```
@Partial @Mock DataLoader loader;
```
 
对于参数或者局部变量使用Annotations的情况，没有特定的规范。

**5.修饰符顺序**
多个类和成员变量的修饰符，按Java Lauguage Specification中介绍的先后顺序排序。具体是：
```
public protected private abstract default static final transient volatile synchronized native strictfp
```


# 注释
- 注释遵照Javadoc格式。
- 注释的缩进和要说明的代码保持一致。

关于[Javadoc](http://www.oracle.com/technetwork/java/javase/documentation/index-137868.html)的内容请每一位Javaer自行学习。在目前的工作中，几乎没有使用。  
但是要成为一个专业的Javaer这部分内容是应该掌握的。



1.行注释

```
// 样式一
/** Names of any split APKs, ordered by parsed splitName */

// 样式二
// The notion of required permissions is deprecated but for compatibility.

// 样式三  mWindowAdded限定符是package 故如此注释，比较和谐
/*package*/ boolean mWindowAdded = false;

// 样式四  参数说明
mFragments.doLoaderStop(mChangingConfigurations /*retain*/);
```



2.块注释

第一行，只有/**;
第二行起，*和第一行的对齐，也就是说要行前有一个空格;
最后一行只有 */;
```
/**
 * Timeout (in milliseconds) after which the watchdog should declare that
 * our handler thread is wedged.  The usual default for such things is one
 * minute but we sometimes do very lengthy I/O operations on this thread,
 * such as installing multi-gigabyte applications, so ours needs to be longer.
 */
```

# 命名
---
见名知意，请使用有意义的命名。

### 0. 驼峰命名定义技巧
1. 将字符全部转换为ASCII字符，并且去掉 ' 等符号。例如，"Müller's algorithm" 被转换为 "Muellers algorithm" 。
2. 将上一步转换的结果拆分成一个一个的词语。从空格处和从其他剩下的标点符号处划分。  
3. 经过上面两部后，先将所有的字母转换为小写，再把每个词语的第一个字母转换为大写。
4. 最后，将所有词语连在一起，形成一个标示符。
 
注意1：一些已经是Camel case的词语，也应该在这个时候被拆分。（例如 AdWords 被拆分为 ad words）。但是例如iOS之类的词语，它其实不是一个Camel case的词语，而是人们惯例使用的一个词语，因此不用做拆分。
注意2：词语原来的大小写规则，应该被完全忽略。

以下是一些例子：

|Prose form|Correct| Incorrect|
| :--: | :--:| :--: |
| "XML HTTP request"| XmlHttpRequest |  XMLHTTPRequest   |
|"new customer ID"|	newCustomerId|	newCustomerID|
|"inner stopwatch"|	innerStopwatch|	innerStopWatch|
|"supports IPv6 on iOS?"|	supportsIpv6OnIos|	supportsIPv6OnIOS|

### 1. 包名

- 包名统一使用小写
- 无下划线
- 点分隔符之间有且仅有一个自然语义的英语单词。  
包名统一使用单数形式，但是类名如果有复数含义，类名可以使用复数形式。

### 2. 类名
- 大驼峰命名
- class命名一般使用名词或名词短语
- interface的命名有时也可以使用形容词或形容词短语 
- 测试类的命名，应该以它所测试的类的名字为开头，并在最后加上Test结尾。如：HashTest

### 3. 方法名
- 小驼峰命名
- 方法命名一般使用动词或者动词短语
- 在JUnit的测试方法中，可以使用下划线，用来区分测试逻辑的名字，经常使用如下的结构：test<MethodUnderTest>_<state> 。例如：testPop_emptyStack 。
### 4. 常量名
- 全部使用大写字符，词与词之间用下划线隔开
- 一般是名词或名词短语
### 5. 类成员属性名
- 小驼峰
- static属性s为前缀，如```private static MyClass sSingleton;```
- 非public,非static的属性m为前缀，如```Activity mParent;```

### 6. 参数名
- 小驼峰
- 避免使用一个字符作为参数的命名方式。
 
 
### 7. 局部变量名
- 局部变量采用小驼峰。它相对于其他类型的命名，可以采用更简短宽松的方式。
- 避免采用单个字母进行命名的情况，除了在循环体内使用的临时变量。

 
### 8. 类型名
 
类型名有两种命名方式：
- 单独一个大写字母，有时后面再跟一个数字。（例如，E、T、X、T2）。
- 同类命名，再在最后接一个大写字母。（例如，RequestT、FooBarT）。


# 编码
---
### 1. @override 总是被使用
只有当父方法是@Deprecated，@override 可以省略。简单来说就是不要省略。

### 2. 异常捕获 不应该被忽略
**当reviewer看到捕获异常没有处理，请果断打回去。**
一般情况下，catch住的异常不应该被忽略，而是都需要做适当的处理。例如将错误日志打印出来，或者如果认为这种异常不会发生，则应该作为断言异常重新抛出。
 
如果这个catch住的异常确实不需要任何处理，也应该通过注释做出说明。例如：
```
void setServerPort(String value) {
    try {
        serverPort = Integer.parseInt(value);
    } catch (NumberFormatException e) {
        // Method is documented to just ignore invalid user input.
        // serverPort will just be unchanged.
    }
}
```

例外：在测试类里，有时会针对方法是否会抛出指定的异常，这样的异常是可以被忽略的。但是这个异常通常需要命名为： expected。例如：
```
try {
  emptyStack.pop();
  fail();
} catch (NoSuchElementException expected) {
}
```
### 2. 精确地捕获异常
请不要做下面两件事：
- 多个异常一个处理方式
- 捕捉的异常范围太大

下面是个不好的例子：
```
try {
    someComplicatedIOFunction();        // may throw IOException
    someComplicatedParsingFunction();   // may throw ParsingException
    someComplicatedSecurityFunction();  // may throw SecurityException
    // phew, made it all the way
} catch (Exception e) {                 // I'll just catch all exceptions
    handleError();                      // with one generic handler!
}
```


### 3. 静态成员的访问：应该通过类，而不是对象

```
Foo aFoo = ...;
Foo.aStaticMethod(); // good
aFoo.aStaticMethod(); // bad
```
### 4. 不使用finalize 方法
目前Android中还是有些代码使用了该方法。


### 5. equals比较，常量在前
```
 if (ZoneGetter.KEY_DISPLAYNAME.equals(mSortingKey)) {
```
### 6. 使类和成员的可访问性最小
一个属性，方法，甚至是类应该有明确使用限定符(public protected private)



# REF
https://source.android.com/source/code-style
https://google.github.io/styleguide/javaguide.html




