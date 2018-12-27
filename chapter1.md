# 源文件

---

1. 一个文件中只定义一个类，内部类除外。
2. 文件名就是类名.java
3. 文件编码为UTF-8
4. 换行符为UNIX格式
5. 文件中的空白字符只能是空格和换行符
6. 一个源文件包含\(按顺序且每个部分之间用一个空行隔开,类注释和类之间无空行\)：
   * 许可证或版权信息\(可选\)
   * package语句
   * import语句
   * 类注释\(可选\)
   * 类  

![](/assets/Screenshot from 2018-11-13 14-33-41.png)

# 通用格式

---

行尾只能有一个换行符，不能有其它空白符  
每行长度最多为100个字符

# 格式

---

## 1.许可证或版本

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

## 2.package语句

package语句不换行，如果太长请考虑重新命名。  
包名统一使用小写，点分隔符之间有且仅有一个自然语义的英语单词。  
包名统一使用单数形式，但是类名如果有复数含义，类名可以使用复数形式。  
示例：

```
com.ckt.xxx
com.sioeye.xxx
```

## 3.import语句

import语句不换行；  
不能使用通配符，即，不要出现类似这样的import语句：import java.util.\*;

import语句可分为以下几组，按照这个顺序，每组由一个空行分隔：

* 第三方的包。每个顶级包为一组，字典序。例如：android, com, junit, org, sun
* java imports
* javax imports
* 所有的静态导入为一组
  **组内不空行，按字典序排列。**

## 4.类

类中的成员应该按照某种逻辑顺序排列；  
重载方法应该放在一起

## 5.缩进为4个空格

## 6.命名

1. 类名用能描述类意义的英文且用UpperCamelCase风格编写
2. 方法名以lowerCamelCase风格编写
3. 常量用全大写的英文单词描述用下划线隔开
4. 类变量以m开头lowerCamelCase风格编写，如`private LocationFudger mLocationFudger`;
5. 类静态变量以s开头lowerCamelCase风格编写，如`private static Handler sHandler`;
6. 其它变量，如局部变量，参数等，以lowerCamelCase风格编写
7. enum的命名同类，成员同常量

## 7.非C风格的数组声明

中括号是类型的一部分：  
`String[] args`， 而非`String args[]`

## 8. switch 语句



