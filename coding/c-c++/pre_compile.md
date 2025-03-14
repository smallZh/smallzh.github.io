# 预编译

预处理：在进行编译之前进行的工作，对名称进行替换
预处理命令：以 `#` 号开头的为预处理命令
分类：
(1)#define和#undef指令
(2)#include指令
(3)#if #endif和#if #else #endif指令

## 宏定义
宏：用一个标识符表示一个字符串
### 1 不带参数
格式：
```
#define 标识符 字符串
```
举例：
```c
// 定义一个宏
#define PI 3.1415926
float a = PI*r*r;
// 取消定义
#undef PI
```

### 2 带参数
格式：
```
#define 标识符(参数列表) 字符串
```
举例：
```c
// 定义一个宏
#define F(x) (x+3)*x
int a = F(5);
```
注意：

1. 宏名和形参之间不能有空格
2. 形参不分配内存单元，不需要写数据类型声明
3. 形参是一个标识符，调用时的实参可以是表达式
4. 字符串内的形参，通常用括号括起来

运算：

1. 字符串化运算符，即 `#` ，如： `#define F(n) "abc"#n` 
2. 并接运算符，即 `##` ,如： `#define M(n) n##n` 

## 文件包含
格式：
```
#include "文件名"
#include <文件名>
```
说明：

1. 使用双引号，则先从当前目录下查找，然后再从系统指定目录查找
2. 使用尖括号，直接从系统指定目录查找

## 条件编译
格式：
```
#ifdef常量表达式
　代码段1
#else 
　代码段2 
#endif
```
举例：
