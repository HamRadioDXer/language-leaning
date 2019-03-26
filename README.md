
##  C++ 学习
<<<<<<< HEAD

### 唐老师
#### 函数重载
* 参数个数不同
* 参数类型不同
* 参数顺序不同

##### 调用准则
* 将所有同名函数作为候选者
尝试寻找可行的候选函数
* 精确匹配实参
* 通过默认参数能够匹配实参
* 通过默认类型转换匹配实参
匹配失败
* 最终寻找到的候选函数不唯一，出现二义性
* 无法匹配所有候选者，函数未定义，编译失败
#### 函数重载本质
* 相互独立不同的函数
* 函数类型不同
* 返回值不能作为函数重载的依据
* **是由函数名和参数列表决定的  **
##### 函数重载遇上函数指针的时候
* 将重载函数名赋值给函数指针时
  * **将根据重载规则挑选与函数指针参数列表一致的候选者**
  * 严格匹配候选者的函数类型与函数指针的函数类型
  
```c++
#include <stdio.h>
#include <string.h>

int func(int x)
{
    return x;
}

int func(int a, int b)
{
    return a + b;
}

int func(const char* s)// 指针类型参数
{
    return strlen(s);
}

typedef int(*PFUNC)(int a); //指向函数类型为INT的函数指针 


int main(int argc, char *argv[])
{
    int c = 0;

    PFUNC p = func;
        
    c = p(1);   
    
    printf("c = %d\n", c);

    return 0;
}


  ```

  * 函数重载必须发生在同一个作用域中
  * 编译器需要用**参数列表**或**函数类型**进行函数选择
  * 无法直接通过函数名得到重载函数的入口地址
  ###  c和c++的相互调用
  **extern**关键字能够强制让C++ 编译器对C进行编译
  ```c
  extern "C"
  {
      #include "C语言编译的代码"
      //do c格式的方式编译

  }

```

> 如何进行C、c++的类型强制编译
> _cplusplus 是C++编译器的**内置标准宏定义**
> 意义
>   确保C代码以统一的方式被编译成目标文件
>

```C
#ifdef __cplusplus
extern "C"{

//这里是C方式代码 

#endif
#ifdef __cplusplus
}
#endif} 
```
C++ 编译器不能以C的方式编译重载函数
**编译方式**决定函数被编译后的目标名
  - C++编译方式将 **函数名**和参数列表 编译成目标名
  - C编译只将函数名作为目标名进行编译
---
 - 函数重载通过函数参数表区分不同的同名函数
 - **extern**关键字能够实现C/C++的相互调用
 - **编译方式决定**符号表中的函数最终目标名

### C++ 中新成员
#### 动态内存分配
    * C++ 通过 **new**关键字进行动态内存 **申请**
    * 是基于类型进行的e
    * **delete**关键字进行内存的释放
  ```c
  Type *pointer = new Type;
  //...
  delete pointer;
  ```
  数组申请
  ```c

Type *pointer = new Type[N];
//...
delete[] pointer;
  ```
  
=======

### 唐老师
#### 函数重载
* 参数个数不同
* 参数类型不同
* 参数顺序不同

##### 调用准则
* 将所有同名函数作为候选者
尝试寻找可行的候选函数
* 精确匹配实参
* 通过默认参数能够匹配实参
* 通过默认类型转换匹配实参
匹配失败
* 最终寻找到的候选函数不唯一，出现二义性
* 无法匹配所有候选者，函数未定义，编译失败
#### 函数重载本质
* 相互独立不同的函数
* 函数类型不同
* 返回值不能作为函数重载的依据
* **是由函数名和参数列表决定的  **
##### 函数重载遇上函数指针的时候
* 将重载函数名赋值给函数指针时
  * **将根据重载规则挑选与函数指针参数列表一致的候选者**
  * 严格匹配候选者的函数类型与函数指针的函数类型
  
```c++
#include <stdio.h>
#include <string.h>

int func(int x)
{
    return x;
}

int func(int a, int b)
{
    return a + b;
}

int func(const char* s)// 指针类型参数
{
    return strlen(s);
}

typedef int(*PFUNC)(int a); //指向函数类型为INT的函数指针 


int main(int argc, char *argv[])
{
    int c = 0;

    PFUNC p = func;
        
    c = p(1);   
    
    printf("c = %d\n", c);

    return 0;
}


  ```

  * 函数重载必须发生在同一个作用域中
  * 编译器需要用**参数列表**或**函数类型**进行函数选择
  * 无法直接通过函数名得到重载函数的入口地址
  ###  c和c++的相互调用
  **extern**关键字能够强制让C++ 编译器对C进行编译
  ```c
  extern "C"
  {
      #include "C语言编译的代码"
      //do c格式的方式编译

  }

```

> 如何进行C、c++的类型强制编译
> _cplusplus 是C++编译器的**内置标准宏定义**
> 意义
>   确保C代码以统一的方式被编译成目标文件
>

```C
#ifdef __cplusplus
extern "C"{

//这里是C方式代码 

#endif
#ifdef __cplusplus
}
#endif} 
```
C++ 编译器不能以C的方式编译重载函数
**编译方式**决定函数被编译后的目标名
  - C++编译方式将 **函数名**和参数列表 编译成目标名
  - C编译只将函数名作为目标名进行编译
---
 - 函数重载通过函数参数表区分不同的同名函数
 - **extern**关键字能够实现C/C++的相互调用
 - **编译方式决定**符号表中的函数最终目标名

>>>>>>> d7550978ef9f679767ba48ff101ef425d21c41ea
