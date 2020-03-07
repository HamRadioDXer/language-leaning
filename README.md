[![996.icu](https://img.shields.io/badge/link-996.icu-red.svg)](https://996.icu)
##  C++ 学习


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

  *   C++ 通过 **new**关键字进行动态内存 **申请**
 *  是基于类型进行的e
*  delete**关键字进行内存的释放

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

  

  **new** 与 **malloc**的区别
  * new是C++的一部分
  * malloc 是C函数库提供的函数
  * new以具体类型为单位进行内存分配
  * **malloc是以字节为单位进行内存分配**
  * new在申请单个变量时可进行初始化
  * malloc不具备内存初始化的特性
  * C++动态内存分配专用关键字 **new**
  * 内存分配的同时可进行初始化
  * 是基于类型进行的，C是基于字节进行的
  * 命名空间用于解决名字冲突问题
  * 
#### C++命名空间
 * c语言只有一个全局作用域
   * C语言中 **所有全局标识符共享同一个作用域**
   * 标识符之间可能发生冲突
 * C++提出了命名空间概念
   * 将 **全局作用域分成不同部分**
   * 不同命名空间中的标识符可以同名而不会发生冲突
   * 命名空间相互嵌套
<<<<<<< HEAD
   * 全局作用域也叫默认命名空间
  

  ## 继承

  * 从已经存在的类细分出来的类和原类之间继承关系
  * 子类拥有和父类的所有属性和行为
  ## 组合
  * 一些类的纯在必须依赖其他的类，这种关系叫做组合
  * 组合的类在某一局部上由其他类组成
#### 类成员的作用域
* 类成员的作用域都只在类的内部，外部无法直接访问
* 类的成员函数可以直接访问成员变量和 **调用成员函数**
* 类的外部可以访问公有变量public成员
* 类成员的作用域与其访问级别没有关系
  * c++中所有以struct定义的类属性全为public

```c

#include <stdio.h>

int i = 1;

struct Test
{
private:
    int i;

public:
    int j;
        
    int getI()
    {
        i = 3;
        
        return i;
    }
};

int main()
{
    int i = 2;
    
    Test test;
    
    test.j = 4;
    
    printf("i = %d\n", i);              // i = 2;manin函数里的局部变量
    printf("::i = %d\n", ::i);          // ::i = 1;访问默认命名空间中的变量，代表本空间中的全局变量，全局作用域
    // printf("test.i = %d\n", test.i);    // Error
    printf("test.j = %d\n", test.j);    // test.j = 4
    printf("test.getI() = %d\n", test.getI());  // test.getI() = 3
    
    return 0;
}

```
**但凡要访问一个成员变量或者成员函数，都必须得通过具体的对象访问才可以（是否访问成功还是要看访问级别）**
##### 小结
* 类分为内部实现方式和内部细节
* 类的封装机制使得类的 **使用方式**和 **实现方式**相分离（我感觉C也可以）
* C++中通过定义访问级别实现封装机制
* public成员在类的内部和外部可访问和调用
* private成员只能在内部访问调用
*   全局作用域也叫默认命名空间

#### 类的真正形态
  * 如果没有声明访问权限，默认是private
  * struct默认是public
  * 类的实现和应用的区别


```c
#include "Operator.h"

bool Operator::setOperator(char op)
{
    bool ret = false;
        
    if( (op == '+') || (op == '-') || (op == '*') || (op == '/') )
    {
        ret = true;
        mOp = op;
    }
    else
    {
        mOp = '\0';
    }
        
    return ret;
}

void Operator::setParameter(double p1, double p2)
{
    mP1 = p1;
    mP2 = p2;
}
    
bool Operator::result(double& r) //bool返回计算是否成功
{
    bool ret = true;
        
    switch( mOp )
    {
        case '/':
            if( (-0.000000001 < mP2) && (mP2 < 0.000000001) )
            {
                ret = false;
            }
            else
            {
                r = mP1 / mP2;
            }
            break;
        case '+':
            r = mP1 + mP2;
            break;
        case '*':
            r = mP1 * mP2;
            break;
        case '-':
            r = mP1 - mP2;
            break;
        default:
            ret = false;
            break;
    }
        
    return ret;
}

```C++
#include <stdio.h>

class Test
{
private:
    int i;
    int j;
public:
    int getI() { return i; }
    int getJ() { return j; }
};

Test gt; //全局变量默认初始化为0

int main()
{
    printf("gt.i = %d\n", gt.getI()); //输出为0
    printf("gt.j = %d\n", gt.getJ());
    
      Test t1;
    
    printf("t1.i = %d\n", t1.getI());//局部输出为乱码
    printf("t1.j = %d\n", t1.getJ());
    
    Test* pt = new Test;//类也是一个变量类型，指向一个指针也是可以的
    printf("pt->i = %d\n", pt->getI());
  //指针访问类的成员函数的形式“p->成员函数”
    printf("pt->i = %d\n", pt->getI());
    printf("pt->j = %d\n", pt->getJ());
    
    delete pt;
    
    return 0;
}





```

> 如何做到一个变量不管是在哪里定义的他的初始值都是确定的呢？

* 程序设计角度，对象也只是变量
  * 在栈上创建的初始值是随机的
  * 在堆上创建的也是随机值 
  * 在 **静态存储区**创建的成员初始值是 **0**值

C++中与函数名字相同的函数，这个特殊的成员函数叫做 **构造函数**
   * 没有任何返回类型的说明
   * 与函数值同名
   * 构造函数在定义时被自动调用
   * 构造函数可以根据需要定义参数
   * 一个函数中可以存在 **多个重载的构造函数**
   * 构造函数重载遵循C++的重载规则
   ```C++
   class Test
   {
     public :
       Test(int v)
       //v作为成员变量
       //可以定义多个构造函数，用参数的不同区分开



   }


   ```
###### 定义和声明的不同

* 定义对象--申请空间并调用构造函数
  
  * Test t； 
* 对象声明---告诉编译器存在这么一个对象
  ```C++
  int main {
    extern Test t； 
  }
  return 0；
  ```



>释放堆空间（delete pt）

赋值和初始化不同



###### 手动调用构造函数
```c++
#include <stdio.h>

class Test
{
private:
    int m_value;
public:
    Test() 
    { 
        printf("Test()\n");
        
        m_value = 0;
    }
    Test(int v) 
    { 
        printf("Test(int v), v = %d\n", v);
        
        m_value = v;
    }
    int getValue()
    {
        return m_value;
    }
};

int main()
{
    Test ta[3] = {Test(), Test(1), Test(2)};      
    
    for(int i=0; i<3; i++)
    {
        printf("ta[%d].getValue() = %d\n", i , ta[i].getValue());
    }
    
    Test t = Test(100);//c++的灵活性
    
    printf("t.getValue() = %d\n", t.getValue());
    
    return 0;
}


```

#### 无参构造函数

#### 拷贝构造函数
**const class_name&**


默认拷贝构造函数

浅拷贝：拷贝后物理状态相同

深拷贝：拷贝后逻辑状态相同

**编译器提供的拷贝只进行浅拷贝**
```c++

#include <stdio.h>

class Test
{
private:
    int i;
    int j;
    int* p;
public:
    int getI()
    {
        return i;
    }
    int getJ()
    {
        return j;
    }
    int* getP()
    {
        return p;
    }
    Test(const Test& t) //深拷贝
    {
        i = t.i;
        j = t.j;
        p = new int;//指针P用来指向一个动态的内存，新空间空间
        
        *p = *t.p;//地址当中的值进行重新的指定
        //t对象里面的值给拿出来，指向p所指的堆空间
    }
    Test(int v)
    {
        i = 1;
        j = 2;
        p = new int;
        
        *p = v; //再将内存空间的内容赋值为传入的v
    }
    void free()
    {
        delete p;
    }
};

int main()
{
    Test t1(3);
    Test t2(t1);
    
    printf("t1.i = %d, t1.j = %d, *t1.p = %d\n", t1.getI(), t1.getJ(), *t1.getP());
    printf("t2.i = %d, t2.j = %d, *t2.p = %d\n", t2.getI(), t2.getJ(), *t2.getP());
    
    t1.free();
    t2.free();
    
    return 0;
}

```



* 有了构造函数就不再去调用默认构造函数，如果对象建立时不用自定义的构造函数格式那么会编译通不过
* 什么时候需要深拷贝
* 成员打开了动态内存空间
* 成员打开了外存中的文件
* 成员使用了系统中的网络端口

 * 全局作用域也叫默认命名空间

#### 自定义的拷贝构造函数，**必然要实现深拷贝**

```C++
#include "IntArray.h"

IntArray::IntArray(int len)
{
    m_pointer = new int[len];//定义一个数组类
    
    for(int i=0; i<len; i++)
    {
        m_pointer[i] = 0;//挨个赋值
    }
    
    m_length = len;
}
//数组类深层拷贝函数
IntArray::IntArray(const IntArray& obj)
{
    m_length = obj.m_length; //m_length是上面的构造函数变量，赋给当前函数
    
    m_pointer = new int[obj.m_length];//申请一块新的内存指针。。。。不懂，，，，这样只是一个数字而已没有什么意义，为了告诉下面有几个循环。。。。。实际工作是产生三个新的动态内存指针哈哈
    
    for(int i=0; i<obj.m_length; i++)
    {
        m_pointer[i] = obj.m_pointer[i];
    }
}

int IntArray::length()
{
    return m_length;
}

bool IntArray::get(int index, int& value)
{
    bool ret = (0 <= index) && (index < length());
    
    if( ret )
    {
        value = m_pointer[index];
    }
    
    return ret;
}

bool IntArray::set(int index, int value)
{
    bool ret = (0 <= index) && (index < length());
    
    if( ret )
    {
        m_pointer[index] = value;
    }
    
    return ret;
}

void IntArray::free()
{
    delete[]m_pointer;
}

```


### 初始化列表的使用（C++引入）

构造函数之后函数体之前
```c++
ClassName:ClaseName():
            m1(v1),m2(v1,v2),m3(v1,v2,v3)
{
//v1对m1初始化，不意味着m1先比m2初始化
}
```

* 成员的初始化顺序与成员的声明顺序相同；**依赖于成员的声明顺序**
* 成员的初始化顺序与初始化列表中的位置无关
* 初始化列表优先于函数先执行

```c++
#include <stdio.h>

class Value
{
private:
    int mi;
public:
    Value(int i)
    {
        printf("i = %d\n", i);
        mi = i;
    }
    int getI()
    {
        return mi;
    }
};

class Test
{
private:
    Value m2; //类中的对象实现
    Value m3;
    Value m1;
public:
    Test() : m1(1), m2(2), m3(3)
    {
        printf("Test::Test()\n");
    }
};


int main()
{
    Test t;
    
    return 0;
}

```

* 类中的const成员只能在初始化列表中指定初始值
* 编译器无法直接的到const成员的初始值 ，因此无法进入符号表成为真正的常量




# 设计原则
###
* 模块间仅通过接口进行关联
    * 必然存在模块会使用接口
    * 必然存在模块实现的接口
* 模块间的关系是单项依赖的
   * 避免模块间存在循环依赖的情况
   * 循环设计比较糟糕

   纯虚类实现接口功能
#### 单个对象创建时构造函数的调用顺序
   * 调用父类的构造过程
   * 成员变量
   * 类自身的构造函数
   * 析构函数的调用顺序相反
 #### const能否修饰类的对象
 * 能，为只读对象，对象的成员变量不允许被改变
 * 只读对象是编译阶段的概念，运行时无效
 * 在类成员之后加 const就行了   
 #### 
 对象由属性（成员变量）和方法（成员函数）
 从运行的角度
   * 对象由数据和函数构成

    * 数据可以位于栈，堆和全局数据区

    * 函数只能位于代码段

    * 每个对象拥有自己的独立属性(成员变量)
    * 所有的对象共享类的方法（成员函数）
    * 方法直接访问对象的属性
    * 方法中隐含this指针指代本对象
    * 只读对象只能调用const成员函数
#### 类的静态成员变量
* 程序在运行过程中得知每个类的对象个数，不使用全局变量，随时获取成员个数


* 需要在类外单独定义静态类成员变量
* 全局数据区分配空间
#### 类的静态成员函数
* 随时获取对象个数怎么满足
* 不依赖对象就可以访问
* 不申请对象的访问
这时就可以用静态成员函数来做这个
* 直接static关键字修饰
* 使用上差异不大
* 静态成员函数通过类名访问
#### 二阶构造模式（开发中小小的方法）
* 如何判断构造函数执行结果

* 构造中用return 发生什么》》》立即返回

* 执行结束是否代表构造成功？？？不意味着构造成功
* 



```C++
#include <stdio.h>

class Test
{
    int mi;
    int mj;
    bool mStatus;
public:
    Test(int i, int j) : mStatus(false) //强行返回值
    {
        mi = i;
        
        return;
        
        mj = j;
        
        mStatus = true;
    }
    int getI()
    {
        return mi;
    }
    int getJ()
    {
        return mj;
    }
    int status()
    {
        return mStatus;
    }
};

int main()
{  
    Test t1(1, 2);
    
    if( t1.status() )
    {
        printf("t1.mi = %d\n", t1.getI());
        printf("t1.mj = %d\n", t1.getJ());
    
    }
    
    return 0;
}
```


* 构造函数只是决定函数的初始状态，不能决定飞翔的创建
* 半成品对象
* 伪指针
* 

* 资源无关的初始化操作
* 需要系统资源的操作（内存申请）

![](photo/Slide11.png)
![](photo/Slide12.png)

列表初始化

```c++
int units_sold = 0;
               = {0};
int units_sold{0};
int units_sold(0);
```

* 花括号初始化对类型转换不支持

* 在函数体内部的内置类型变量不会被初始化，其值未定义。类的对象如果没有明显被显示初始化，其值由类决定

每个类各自决定其初始化对象的方式

```c++
std::string empty;
Sales_item item ;
这样的初始化是被允许的
```

* 建议还是显式初始化，运行时未初始化引发故障

**声明**：使得名字被程序所知，文件想使用别处定义的名字则必须包含那个名字的声明

**定义**：负责创建与名字关联的实体

* 定义在类型和名字之外，还会申请空间，会赋一个初值。
* 我们可以个**extern**关键字赋一个初值，但是这么做抵消了关键字的作用。
* 在函数内部如果试图初始化一个由**extern**关键字的变量，将引发错误

* 变量能被定义一次，可以被声明多次

***

变量名一般用小写

用户自定义类名一般大写字母开头

***

### 引用

定义引用时，程序把引用和初始胡初始值绑定在一起，而不是将初始值拷贝给引用。初始化完成则一直绑定在一起

### 指针

不同点

* 指针本身是一个对象，允许指针赋值和拷贝，而且在指针的生命周期内它可以先后指向几个不同的对象

* 指针在定义时无需赋初值也是可以的

* 引用不是对象，不能定义指向引用的指针，引用没有实际地址

  * 指针的值指向一个对象
  * 指向近邻对象所占空间的下一个位置
  * 空指针
  * 无效指针，访问无效指针的后果无法估计

* 利用指针访问对象

  * 如果指针指向了一个对象，则允许使用解引用符*访问对象

    * ```c++	
      int ival = 43;
      int *p= &ival;
      count << *p;
      ```

    * 对解引用赋值，实际上也就是对指针所指的对象赋值

    * 解引用操作仅适用于那些指向了某个对象的有效指针

* 空指针

  * ```c++
    int *p =nullptr;
    int *p= 0 ;
    #include cstdlib
    int *p =NULL;
    //nullptr 是特殊类型字面值，可以转化成任意其他类型的指针，尽量避免使用NULL
    ```

  * ```c++
    int zero=0;
    pi =zero;//错误做法，不能把int变量直接赋值给指针
    ```

* **赋值永远改变的是等号左侧的对象**

* 利用void * **void* ** 能做的：指针比较、座位函数的输入输出、赋值给另外一个void*指针，**不能直接操作void所指的对象、（不知道里面到底是什么类型）**

* **int* p1**强调声明了一种是复合类型指针

* int *p1 强调变量所具有的复合类型

#### 指向指针的引用

```c++
int i = 42 ;
int *p ;
int *&r = p;//r是一个对指针P的引用
int* &r = p；

r = &i; //r引用了一个指针，因此给r赋值&i就是指令p指向i
		//从右往左阅读r的定义，距变量名最近的符号，对变量的类型有罪直接的影响。
*r = 0;//解引用的而奥i

```

#### const限定符

* 只在头文件中定义const，而在其他多个文件中声明并使用它
* **对于const变量不管是声明还是定义都添加extern加以限定时期被其他文件使用**
* 头文件中队常量const 使用extern代表，此常量并非本文件所独有，他的定义将在别处出现

##### const的引用，对常量的引用

引用的类型必须与其所引用的对象类型一致，但是有两个意外。

* 在初始化常量引用时允许，用任意表达式作为初值，只要该表达式可以转化为引用的类型即可。
* 对 const 的引用可能引用一个并非const的对象

##### 指针和CONST

* 需要存放常量对象的地址，只能使用指向常量的指针
* 允许令一个指向常量的指针指向一个非常量的对象
* 指向常量的指针没有规定其所指的对象必须是一个常量，所谓指向常量的指针仅仅要求不能通过指针改变对象的值，没有规定那个对象的值不能通过其他途径改变
* **所谓指向常量的指针或引用，不过是指针或者引用“自以为是”罢了，他们觉得自己指向了常量，所以自掘地不去改变所指对象的值**

const指针

```c++
* const 指针，*放在const之前用以说明指针是一个常量，即不变的时指针本身的值而非指向的那个值
```

**指针本身是常量，不代表不能通过指针修改其所指的对象的值，能否这样做完全取决于所指对象的类型**

* 顶层const：本身是常量

* 底层const：所指向的东西是常量

  ```c++
  const int ci = 42;
  const int *p2 = &ci;  // 允许改变p2的值，这是一个底层const
  const int *const p3 = p2 ; //左边的是 顶层 右边是底层
  const int &r = ci ; // 用以声明引用的const都是底层const
  ```

* 拷贝时底层const的限制不能忽视，当之乡拷贝和考出的对象必须具有相同的地城const资格

##### constexpr和常量表达式

**常量表达式**：不会改变并且编译过程就能得到计算结果的表达式，又数据类型和初始值共同决定

**constexpr**变量



### vector需要注意的几个点

* 在初始化的时候区分列表初始化（后面加花括号）和拷贝初始化方式
  * vector<string> a (10,"word" );
  * vector<int> a {'a','b','c'}
* 当vector为空的时候，不能通过下标访问
* 只有当元素能比较时，vector才能被比较
* vector<int>  a(10) //代表有十个元素，但是在初始化后进行索引时范围----0-9

## 迭代器介绍

**begin**：负责返回指向第一个元素（或第一个字符）的迭代器

**end**：返回“尾元素的下一个位置的迭代器，指向一个本不存在的·’尾后‘

> 如果容器为空，则begin和end返回的时同一个迭代器，都是尾后迭代器。

```c++
*iter //返回迭代器的引用
    
iter->mem  //解引用iter并获取，该元素的名为men的成员，等价于（*iter）.men
++iter 
--iter
```

* 试图解引用一个非法迭代器或者尾后迭代器都是未被定义的行为
* 迭代器的递增是将迭代器“前像移动一个位置”
* end返回的且待期不实际指向某个元素，所以不嫩对齐进行递增或者解引用的操作

```c++
for (auto it =s.begin();it != s.end() && !isspace(*it) ; ++it)//每次迭代后指向++i令迭代器前移一个位置访问s的下一个字符
    *it = toupper(*it); //将当前字符改写成大写形式
```

* 只有string和vector等一些有下标运算符，而非全都如此
* 要习惯！=

##### 迭代器类型

* 不知道字符串和vector的size_tyoe成员到底是什么类型一样，一般来说不知道迭代器的类型
* 每个容器定义了一个名为iterator的类型，代表支持迭代器所规定的的一套操作

##### begin和end

* c++ 11 为了只去读取定义了 

  * ```c++
    auto it = v.cbegin();
    ```

  * 类型是 vector<int>::const_iterator

##### 解引用

```c++
it->men
    
(*it).men
```

##### 但凡是使用了迭代器的循环体，都不要向迭代器所属的容器添加元素

### 迭代器运算

```c++
iter + n
    
    iter - n
    iter+=n
    iter _= n
    iter - iter1
    >/>=/<=/<
    
```

##### 迭代器的算术运算

两个迭代器相间的结果是这两个迭代器之间的距离，**difference_type**,带符号类型。

#### 使用迭代器完成二分搜索

```c++
auto begin =t.begin(),end=t.end();
auto mid   =t.begin()+(end - beg)/2;
while (mid != end && *mid != sought){
    if (sought < mid)
        end = mid;
    else
        beg = mid + 1;
    mid = beg + (end - beg)/2; // 新的中间点
}
```

## 数组

数组大小确定不变

* 使用数组类型的对象其实是使用一个指向该数组首元素的指针

~~~c++
int a[]={0,1,2,3,4,5,6,7,8,9};
auto ar2(a); //ar2是一个指向数组a的第一个元素的整形指针
ar2 = 42;    // 错误，
~~~

##### 指针也是迭代器

数组指针支持string和vector的操作

###### c++11 对指针新加入begin和end

~~~c++
int a[]={0,1,2,3,4,5,6,7,8,9};
int *beg = begin(a); //指向a首元素的指针
int *end = end(a);
~~~

#### 混用string和c风格字符串

*  允许使用以空字符结束的字符数组来初始化string对象
* 在string假发中，可以视同空字符结束的字符数组作为一个对象
* 可以用字符数组代替string，不能用string代替字符数组

~~~c++
const char *str = s.c_str();//s是string类型，c_str()代表返回c风格的字符串
~~~

**使用数组初始化vector对象**

~~~c++
int a[]={0,1,2,3,4,5,6,7,8,9};
vector<int>  ivec(begin(a),end(a));
vector<int>  subVec(a+1,a+5);
~~~

 **尽量使用标准库而非字符串数组**

 # 第四章 表达式



有四种运算符明确定义运算对象的顺序

* && 逻辑与，左侧为真才继续右边
*  || 
* ?:
* ,

1.拿不准是最好用括号括起来

2.一个运算改变了运算对象的值，那个在表达式的其他地方就不要再使用这个对象了



**推荐使用++，--运算符的前置版本，原因：前置是吧对象加一然后将改变后的对象作为结果，后置版本的结果是运算对象改变之前的那个值的副本，运算成本大，在vector中成本更大**

##### 在一条语句中混用解引用和递增运算符

---

~~~c++
string s1 ={"djalskdjkasljdlas"},*p =&s1;
auto n = s1.size();
n =(*p).size();  //解引用的优先级低于点运算符，要加括号
n = p->size();
~~~



**try****语句块**

~~~c++
try{
    //---------/////
} catch (异常声明){
    handler_staments
}catch (exceptions-declaration){
    handler_staments
}
~~~

**注意命名空间问题，try和catch的变量不互通，是不合法的**

#### 标准异常

* **exception**头文件只报告了异常的发生
* **stdexcept**头文件定义的最通用的异常类
* **new** **头文件定义了bad_alloc**异常类型
* **type_info**头文件定义了 **bad_cast**异常

| exception       | 最常见问题                               |
| --------------- | ---------------------------------------- |
| runtime_error   | **只有在运行时才能出现的问题**           |
| range_error     | 生成的结果超出了有<br>意义的结果范围     |
| overflow_erroe  | 计算上溢                                 |
| underflow_error | 计算下溢                                 |
| logic_error     | 逻辑错误                                 |
| domain_error    | 对应的结果值不存在                       |
| invalid_arguent | 无效参数                                 |
| length_error    |                                          |
| out_of_range    | 逻辑错误，使用一个超出<br>有效范围的数值 |

## 第六章：函数

#### 6.1函数基础

函数名字

返回类型

函数体

参数列表，形参

* 函数的返回类型不能是数组，也不能是函数。但可以是指向数组或函数的指针
* 名字的作用域是程序文本的一部分，名字在其中可见
* 对象的声明周期是程序执行过程中该对象存在的一段时间
* 局部变量还会隐藏在外层作用域中同名的其他所有声明
* 自动对象：只存在于块执行期间的对象，形参是自动对象
* 静态局部对象： 在经过的第一次时进行初始化，并且到程序终止时才被销毁。默认的内置类型局部静态变量初始化为0。
* 如果形参是引用类型，它将绑定到对应的实参上；否则将实参的拷贝纸赋给形参
* 引用传递、函数被传引用调用
* **指针形参，指针的行为和其他非引用类型一样，当执行指针拷贝操作时，拷贝的时指针的值。拷贝之后，两个指针是不同的指针，因为指针使得我们可以间接地访问它所指的对象，所以通过指针我们可以修改它所指对象的值**
* 熟悉C语言常使用指针吉祥访问函数的外部对象，在c++语言中，建议使用引用类型的形参代替指针
* 

# 

# <font color='red'> 明天4号一定把270页搞定</font>



### P212 默认实参初始值

局部变量不能作为默认实参，只要能转换成形参所需的类型就能作为实参



**consttexpr**函数：能用于常量表达式的函数

#### 调试帮助

**assert**预处理宏定义，预处理变量，和内联函数类似

宏名字在程序内必须唯一，常用于检查“不能发生的事情”

### NDEBUG预处理变量

assert依赖于一个名为 **NDEBUG**的预处理变量的状态，定义了非debug则assert什么也不用做，没有ndebug则金乡运行时检查

函数类型由他的返回类型和形参类型共同决定，与函数名称无关

~~~c++
bool (*pf) (const string & , const string &);//一个纸箱函数的指针
~~~

**把函数名用作一个值使用时，函数自动转换成指针**

还能直接使用指向函数的指针调用该函数，无需提前解引用

~~~c++
bool b1 = pf()
bool b2 = (*pf)
bool fun()
    三个同样的调用
~~~









# 第七章：类

## 7.1定义抽象数据类型

某些类不能依赖于合成的版本

把函数作为一个友元只需在前面加 **friend** 声明即可

类外成员函数的实现和类的声明放在头文件中

#### 封装的好处

* 确保用户代码不会无意间破坏封装对象的状态
* 被封装的了具体实现细节可以随时改变，而无需调整用户级别的代码
* 为了使友元对用户可见，我们把友元声明和类的声明放在同一个头文件中

~~~c++
typedef std:string::size_type name;
using name = std::string::size_type;
~~~

~~~c++
class Screen{
    public: 
    		typedef std::string::type_size pos;
    Screen() = default;
    Screen(pos ht, pos wd , char c ):heigh(ht),weight(wd),contents(ht * wd , c ){ }
    char get ()const
    {return contents [cursor]}
    
    inline char get (pos ht ,pos wd )const;
    Screen &move(pos r , pos c);
    
    private:
    pos cursor = 0;
    pos height = 0;
    pos weight = 0;
    std::string constnts ;
    
}
~~~

* 在类内定义的函数默认是inline的
* inline函数也应该和类的声明一样放在头文件中

##### 重载成员函数

成员函数可被重载

~~~c++
char get ()const
    {return contents [cursor]}
    
inline char get (pos ht ,pos wd )const;
~~~

#### 可变数据成员

希望能修改类内对的某个数据成员，即使在一个const成员函数内

可以在变量的声明中加入 **mutable** 关键字做到

> **一个可变数据成员** 永远不会是 **const **

~~~c++
mutable valiuate；
~~~

##### 类内初始值

~~~c++
class Eindow{
    private :
    //初始化一个类内初始值时，必须以 = 号 或者 花括号表示
    std::vector<Screen> screens{Screen(24,80,'')};
    
};
~~~

#### 返回*this的成员函数

~~~c++
class Screen {
    public:
    Screen &set(char);
    Screen &set(pos,pos,char);
    
};
inline Screen &Screen::set (char c){
    constens[cursor] = c;//设置当前光标所在的位置新值
    return *this    //将This对象作为左值返回
}
inline Screen &Screen::set (pos r , pos w , char ch){
    contens[r * width + col] = ch ;//设置对象的新值
    return *this;
}
~~~

调用的set对象的引用，返回的是函数的左值的，**意味着返回的是对象本身**

~~~c++
myscreen.move(4,0).set('#');

//等价于

myscreen.move(4,0);
myscreen.set('#');
~~~

如果返回的不是引用而是拷贝效果大大不同

~~~c++
Screen temp = myscreen.move(4,0);
temp.set('#');
~~~

#### 从const成员函数返回*this

~~~c++
//假设desplay是返回
// const Sales_data&
myscreen.display(cout).set('a');
//不能通过编译
~~~



#### **一个const成员含糊是如果引用形式的返回形式是*this，那么它的返回类型将是一个常量引用**

## 7.2 访问控制与封装

## 7.3 类的其他特性

## 7.4 构造函数再探

## 7.5 类的静态成员



# 第八章： I/O库

## 8.1 i/o类

p710介绍c++的继承机制

~~~;c++
ofstream out1 ，out2 ；
    
    out1 = out2 ；//不能对流对象赋值
    ofstream print(ofstream); //不能初始化ofstream参数
    out12 = print(out2); //不能拷贝流对象
~~~

**执行I/O操作的函数通常以引用凡是传递和返回，读写一个io会改变其状态，因此传递和返回的引用不能是const的**

### 条件状态

 当流处于无错误状态时我们才能对之后的算法运行，代码在度入流之后先检查再使用

~~~c++
while(cin>> word)
~~~

查询流的状态

查询流为什么会失败

~~~c++
cin.clear(cin.rdstate() & ~cin.failbit & ~cin.badbit);
~~~

### 缓冲输出

* 程序正常借宿，作为main的return一部分，缓冲刷新被执行
* 缓冲区满，刷新缓冲区
* 使用endl操作符号显式手动刷新缓冲区
* 每个输出操作之后，使用 **unitbuf** 设置流的内部状态，来清空缓存区
* 流之间进行了关联，被关联的刷新

**刷新输出缓冲区 **

操作符： **flush** ：直接输出不加字符

**ends：输出后加空字符** 

**endl：输出和换行**

**unitbuf**操纵符号

~~~c
count << unitbuf ;
//
count << nounitbuf; //回到正常的缓冲方式
~~~

**程序崩溃，缓存不会刷新** 太古老。。。。

## 8.2 文件输入输出

**ifstream**从特定文件读取数据

**ofstream** 向一个给定文件写入数据

**fstream  **读写给定文件

~~~c
fstream fstrm;//创建
fstream fstrm(s);//创建fstream并打开s ，s:string 或者字符串指针
fstream fstrm(s,mode);//以mode的方式打开文件

fstrm.open(s)
    
fstrm.close();
fstrm.isopen();

~~~

### 8.2.1 使用文件流对象

读写一个文件是，可以定义一个文件流对象，并将对象和文件关联起来。

每个文件流都定义了一个名为open的成员函数，完成一些系统相关的工作，来定位给定文件



**用fstream替换iostream&**

 

当一个fstream对象被销毁时，close会自动被调用

### 文件模式，如何使用文件

几个模式

* in
* out
* app 添加的意思，写操作前定位到文件末尾
* ate  打开后立即定位到文件尾
* trunc 截断文件
* binary 二进制方式进行IO

### 以out 模式打开文件会丢弃已有数据

阻止被清空的方法是指定app模式

~~~c++
ofstream out("file1");
ofstream out2("file1",ofstream::out);
//为了保留内容，必须以显示指向append模式
ofstream out3("file3",ofstream::app);
~~~

保留文件内容的唯一方式是显式声明为app 模式或者以in模式（只读）打开

### 8.3 string 流

**istringstream** 从string读数据

**ostringstream**向string写数据

**stringstream** 读写数据

可以对stringtream的操作（不能对其他io）



- [ ] 第九章：顺序容器
- [ ] 第十章： 泛型算法
- [ ] 第十一章： 关联容器
- [ ] 第十二章： 动态内存



~~~c++
#define BinNodePosi(T) BinNode<T>* //节点位置
 #define stature(p) ((p) ? (p)->height : -1) //节点高度（不“空树高度为-1”癿约定相统一）
 typedef enum { RB_RED, RB_BLACK} RBColor; //节点颜色

 template <typename T> struct BinNode { //二叉树节点模板类
 // 成员（为简化描述起见统一开放，读者可根据需要迕一步封装）
 T data; //数值
 BinNodePosi(T) parent; BinNodePosi(T) lc; BinNodePosi(T) rc; //父节点及左、右孩子
 int height; //高度（通用）
0 int npl; //Null Path Length（左式堆，也可直接用height代替）
 RBColor color; //颜色（红黑树）
 // 极造函数
 BinNode() :
 parent ( NULL ), lc ( NULL ), rc ( NULL ), height ( 0 ), npl ( 1 ), color ( RB_RED ) { }
 BinNode ( T e, BinNodePosi(T) p = NULL, BinNodePosi(T) lc = NULL, BinNodePosi(T) rc = NULL,
 int h = 0, int l = 1, RBColor c = RB_RED ) :
17 data ( e ), parent ( p ), lc ( lc ), rc ( rc ), height ( h ), npl ( l ), color ( c ) { }
18 // 操作接口
19 int size(); //统计弼前节点后代总数，亦即以其为根癿子树癿觃模
20 BinNodePosi(T) insertAsLC ( T const& ); //作为弼前节点癿左孩子揑入新节点
21 BinNodePosi(T) insertAsRC ( T const& ); //作为弼前节点癿右孩子揑入新节点
22 BinNodePosi(T) succ(); //叏弼前节点癿直接后继
23 template <typename VST> void travLevel ( VST& ); //子树局次遍历
24 template <typename VST> void travPre ( VST& ); //子树先序遍历
25 template <typename VST> void travIn ( VST& ); //子树中序遍历
26 template <typename VST> void travPost ( VST& ); //子树后序遍历
27 // 比较器、刞等器（各列其一，其余自行补充）
28 bool operator< ( BinNode const& bn ) { return data < bn.data; } //小亍
29 bool operator== ( BinNode const& bn ) { return data == bn.data; } //等亍
30 };
~~~



1. 把数据结构第五章整理完
2. primer整到p333 泛型算法部分
3. 两节计算机网络
4. 两节计算机操作系统



### 第九章 顺序容器

### 顺序容器概述

提供了控制元素存储和访问顺序的能力，不依赖元素的值，而是与元素加入容器时的位置相对应

* 向容器添加或从容器中删除元素的代价
* 非顺序访问容器中元素的代价

   

| 类型         |                                                              |
| ------------ | ------------------------------------------------------------ |
| vector       | 可变大小数组，**支持*快速随机访问*，在尾部之外的位置插入或删除元素可能较慢** |
| deque        | 双端队列。支持**快速随机访问**。**在头尾插入/删除速度很快**  |
| list         | **双向链表**，支持双向顺序访问。**在list中任何位置进行插入/删除都很快** |
| forward_list | 单项链表。只支持单向顺序访问。**在链表的任何位置进行插入/删除操作都很快.** |
| array        | **固定大小数**组。**支持快速随机访问。不能添加或删除元素。** |
| string       | 与vector相似的容器，但专门用于保存字符。随机访问快。在尾部插入/删除快 |



| string/vector            | 是连续储存的，根据下标计算地址是非常快的，但是在容器的中间添加元素就非常慢，因为在中间插入、删除元素后之后的元素都得挪位置，如果需要扩容，所有元素还需要拷贝一次 |
| :----------------------- | ------------------------------------------------------------ |
| **list<br>forward_list** | 设计的目的是让容器的任何位置插入/删除都很快，**这两个容器不支持元素的随机访问**，这两个容器在访问时需要遍历整个容器，内存开销也大 |
| **deque**                | 是更为复杂的数据结构，支持随机访问，在中间插入删除代价高。**在双端插入删除和list、forwa_list速度相当** |
|                          |                                                              |
| forward_list             | 设计的目的是达到与最好的手写的单向链表数据结构相当的性能，因此没有size**操作对其他容器而言size是快速操作** |
| array                    | 目的是代替数组，对象大小固定，不支持添加和删除元素，以及改变容器大小的操作 |

#### 现代C++应使用标准容器库而不是原始的数据声明

#### 确定使用哪种顺序容器

**通常vector是最好的选择，除非有更好的理由**

* 除非更好的理由，那么选择 **vector**
* 程序有很多小的元素，而且空间的额外开销很重要，**那么不要**使用list和forward_list
* 随机访问元素，选 **vector和deque**
* 要在 **中间插入元素**，那么使用 list 和forward_list
* 头尾插入，不会在中间插入 那么 deque
* 程序只有在读取输入时才需要在容器中间位置插入元素，随后需要随机访问元素。则
  * 首先确定是否真的需要在元素中间位置添加元素。处理输入数据时可以容易的在vector **追加**数据，然后再用std::sort()排序，避免在中间添加
  * 输入阶段用list，输入完成将list中的内容拷贝到一个vector中
* 如果不知道使用哪个，可以选择在程序使用vector和list的公共操作：使用迭代器，不使用下标操作，避免随机访问。

~~~c++
list<Sales_data>
deque<double>
~~~

假定aaa是一个没有默认构造函数的类型

~~~c++
vector<aaa> v1(10,init); //yes
vector<aaa> v2(10);//flase
~~~

| 类型别名        |                                                      |
| --------------- | ---------------------------------------------------- |
| iterator        | 此容器类型的迭代器类型                               |
| const_iterator  | 只读不能能写类型                                     |
| size_type       | 无符号整数类型，足够保存此容器类型最大可能容器的大小 |
| difference_type | 带符号整数类型                                       |
|                 |                                                      |
|                 |                                                      |

之后补上

### 921 迭代器

如果一个迭代器提供某个操作，那么所有提供相同相同操作的迭代器对这个操作的实现方式都是相同的

啥意思？？？

~~~c++
*iter
    iter->men
    ++iter
    --iter
    iter1 == iter2
    iter1 != iter2
    
  //只能适合于 STRING VECTOR /DEQUE /ARRAY	  
~~~

**类型库一般用iterator和const_iterator**



迭代器范围：begin 和 end

[begin,end)

~~~c++
while(begin != end){
    *begin = vale;
    ++begin;
}
~~~

容器类型成员

如果需要元素类型的一个引用，可以使用 **reference**或者 **const_reference**类型别名在泛型编程中有用

~~~c++
list<string>::iterator iter; //iter是一个迭代器类型，通过list<string>定义
vector<int>::difference_type count;
//通过作用域::说明了我们希望使用list<string>类的iterator成员
~~~

**begin 和 end**

最常用用法是生成一个包含容器中所有元素的迭代器范围

版本： 带r的反向迭代版本， 带c的const版本

###### 容器的拷贝

两个容器的类型必须匹配，元素类型也得匹配。不过当穿戴迭代器参数来拷贝一个范围时就不用时相同 类型的了

接收两个迭代器参数的构造函数用两个迭代器表示我们想要拷贝的一个元素的范围，新容器和这个范围相同

~~~c++
deque<string> authoe (authoe.begin , it);//假设it【是authoe中的一个元素
~~~

#### 列表初始化

~~~c++
list<string> list =  {"a","b","c"};

~~~

##### 与顺序容器大小（带有数字）的构造函数

如果容器内的元素类型是内置类型，可以只提供一个容器大小参数。如果是没默认构造函数，除了大小参数外还需有显示的元素初始值

> zhi只有顺序容器的构造函数才接受大小参数，关联容器不支持

##### array有固定大小



















容器库

操作

vector如何增长

额外的string操作

容器适配器

























~~~c
 template <typename T> //二叉树子树接入算法：将S弼作节点x癿左子树接入，S本身置空
2 BinNodePosi(T) BinTree<T>::attachAsLC ( BinNodePosi(T) x, BinTree<T>* &S ) { //x->lc == NULL
3 if ( x->lc = S->_root ) x->lc->parent = x; //接入
4 _size += S->_size; updateHeightAbove ( x ); //更新全树觃模不x所有祖先癿高度
5 S->_root = NULL; S->_size = 0; release ( S ); S = NULL; return x; //释放原树，迒回接入位置
6 }
7
8 template <typename T> //二叉树子树接入算法：将S弼作节点x癿右子树接入，S本身置空
9 BinNodePosi(T) BinTree<T>::attachAsRC ( BinNodePosi(T) x, BinTree<T>* &S ) { //x->rc == NULL
10 if ( x->rc = S->_root ) x->rc->parent = x; //接入
11 _size += S->_size; updateHeightAbove ( x ); //更新全树觃模不x所有祖先癿高度
12 S->_root = NULL; S->_size = 0; release ( S ); S = NULL; return x; //释放原树，迒回接入位置
13 }
~~~

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200307154714377.png" alt="image-20200307154714377" style="zoom:50%;" />

~~~c
template <typename T > BinNodePosi(T) BinTree<T>::attachAsLC(BinNodePosi(T) x,BinTree<T> * &s){
    if (x -> lc = S ->_root) x->lc->parent = x;// 首先将待植入的二叉树S的根节点作为x的左孩子，同时令x作为该根节点的父亲
    _size +=S->_size;uodateHeightAboce(x);//更新全书规模
    S->_root = NULL;S->_size=0;release(s);S=NULL;return x;//释放S树，返回x的位置
}
~~~

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200307154847416.png" alt="image-20200307154847416" style="zoom:50%;" />



~~~c
1 template <typename T> //初除二叉树中位置x处癿节点及其后代，迒回被初除节点癿数值
2 int BinTree<T>::remove ( BinNodePosi(T) x ) { //assert: x为二叉树中癿合法位置
3 FromParentTo ( *x ) = NULL; //切断来自父节点癿指针
4 updateHeightAbove ( x->parent ); //更新祖先高度
5 int n = removeAt ( x ); _size -= n; return n; //初除子树x，更新觃模，迒回初除节点总数
6 }
~~~



~~~c
template <typename T> int BinTree<T>::remove (BinNodePosi(T) x ){
    //抛离父亲节点指针
    //更新深度
    //
}
~~~



###### 对二叉树的访问多可抽象为如下形式：按照某种约定的次序，对节点各访问一次且仅一次。

###### 与向量和列表等线性结构一样，二叉树的这类访问也称作遍历（traversal）

![image-20200307164043073](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200307164043073.png)



### 先序遍历

~~~c
1 template <typename T, typename VST> //元素类型、操作器
2 void travPre_R ( BinNodePosi(T) x, VST& visit ) { //二叉树先序遍历算法（逑弻版）
3 if ( !x ) return;
4 visit ( x->data );
5 travPre_R ( x->lc, visit );
6 travPre_R ( x->rc, visit );
7 }
~~~

![image-20200307164615162](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200307164615162.png)



### 后序遍历

~~~c++
1 template <typename T, typename VST> //元素类型、操作器
2 void travPost_R ( BinNodePosi(T) x, VST& visit ) { //二叉树后序遍历算法（逑弻版）
3 if ( !x ) return;
4 travPost_R ( x->lc, visit );
5 travPost_R ( x->rc, visit );
6 visit ( x->data );
7 }
~~~



![image-20200307164931241](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200307164931241.png)

















