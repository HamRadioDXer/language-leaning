
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
* 