---
title: "Microsoft C 和 C++ 扩展 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "! 运算符, 扩展到 C++"
  - "!= 运算符"
  - "& 运算符, C/C++ 的扩展"
  - "&& 运算符"
  - "&= 运算符"
  - "^ 运算符, C/C++ 的扩展"
  - "^= 运算符, C++ 扩展"
  - "| 运算符, 扩展"
  - "|| 运算符"
  - "|= 运算符"
  - "~ 运算符, C/C++ 的扩展"
  - "And 运算符, C/C++ 的扩展"
  - "and_eq 运算符"
  - "compl 方法"
  - "扩展"
  - "扩展, C 语言"
  - "iso646.h "
  - "Microsoft C/C++ 扩展"
  - "NOT 运算符"
  - "not_eq 运算符"
  - "Or 运算符, Microsoft C/C++ 扩展"
  - "or_eq 运算符"
  - "Visual C, Microsoft 扩展"
  - "Visual C++, C/C++ 的扩展"
  - "异或运算符, Microsoft C/C++ 扩展"
  - "xor_eq 运算符"
ms.assetid: e811a74a-45ba-4c00-b206-2f2321b8689a
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Microsoft C 和 C++ 扩展
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 如下扩展 ANSI C 和 ANSI C\+\+ 标准。  
  
## 关键字  
 多个关键字被添加。  在 [C\+\+ 关键字](../../cpp/keywords-cpp.md)的列表中，有两个前导下划线的关键字是 Visual C\+\+ 扩展。  
  
## static const 整型（或枚举）成员的类外定义  
 在标准 \(**\/Za**\) 下，需要为数据成员做出类外定义，如下所示：  
  
```  
class CMyClass  {  
   static const int max = 5;  
   int m_array[max];  
}  
...  
const int CMyClass::max;   // out of class definition  
```  
  
 在 **\/Ze** 下，类外定义对于静态、常量整型和常量枚举数据成员是可选的。  在类中只有静态和常数的整型和枚举可以有初始值设定项；初始化表达式必须是常数表达式。  
  
 在多个资源文件的标头文件中提供一个外部类定义时，若要避免错误，请使用 [selectany](../../cpp/selectany.md)。  例如：  
  
```  
__declspec(selectany) const int CMyClass::max = 5;  
```  
  
## 强制转换  
 C\+\+ 编译器和 C 编译器支持这些非 ANSI 转换：  
  
-   使用非 ANSI 转换产生左值。  例如：  
  
    ```  
    char *p;  
    (( int * ) p )++;  
    ```  
  
    > [!NOTE]
    >  此扩展仅适用于 C 语言。  在 C\+\+ 代码中使用下列 ANSI C 标准窗体修改指向不同类型的指针。  
  
     可用如下方式重写上例，以符合 ANSI C 标准。  
  
    ```  
    p = ( char * )(( int * )p + 1 );  
    ```  
  
-   将函数指针以非 ANSI 方式转换为数据指针。  例如：  
  
    ```  
    int ( * pfunc ) ();   
    int *pdata;  
    pdata = ( int * ) pfunc;  
    ```  
  
     若要在保持 ANSI 兼容性的同时执行上述转换，必须在将函数指针转换为数据指针前先将其转换为 `uintptr_t`：  
  
    ```  
    pdata = ( int * ) (uintptr_t) pfunc;  
    ```  
  
## 变长参数列表  
 C\+\+ 和 C 编译器支持使用指定可变个数参数的函数声明符，其后为提供替换类型的函数定义：  
  
```  
void myfunc( int x, ... );  
void myfunc( int x, char * c )  
{ }  
```  
  
## 单行注释  
 C 编译器支持单行注释，它是用两个正斜杠 \(\/\/\) 字符引入的：  
  
```  
// This is a single-line comment.  
```  
  
## 范围  
 C 编译器支持下列与范围相关的功能。  
  
-   将 extern 项重定义为 static：  
  
    ```  
    extern int clip();  
    static int clip()  
    {}  
    ```  
  
-   在同一范围内使用良性的 typedef 重定义：  
  
    ```  
    typedef int INT;  
    typedef int INT;  
    ```  
  
-   函数声明符具有文件范围：  
  
    ```  
    void func1()  
    {  
        extern int func2( double );  
    }  
    int main( void )  
    {  
        func2( 4 );    //  /Ze passes 4 as type double  
    }                  //  /Za passes 4 as type int  
    ```  
  
-   用非常数表达式初始化块范围变量的使用：  
  
    ```  
    int clip( int );  
    int bar( int );  
    int main( void )  
    {  
        int array[2] = { clip( 2 ), bar( 4 ) };  
    }  
    int clip( int x )  
    {  
        return x;  
    }  
    int bar( int x )  
    {  
        return x;  
    }  
    ```  
  
## 数据声明和定义  
 C 编译器支持下列数据声明和定义功能。  
  
-   初始值设定项中的混合字符和字符串常数：  
  
    ```  
    char arr[5] = {'a', 'b', "cde"};  
    ```  
  
-   除了 **unsigned int** 或 **signed int**外，还有基类型的位域。  
  
-   没有类型的声明：  
  
    ```  
    x;  
    int main( void )  
    {  
        x = 1;  
    }  
    ```  
  
-   未确定大小的数组，作为结构和联合中的最后字段：  
  
    ```  
    struct zero  
    {  
        char *c;  
        int zarray[];  
    };  
    ```  
  
-   未命名（匿名）结构：  
  
    ```  
    struct  
    {  
        int i;  
        char *s;  
    };  
    ```  
  
-   未命名（匿名）联合：  
  
    ```  
    union  
    {  
        int i;  
        float fl;  
    };  
    ```  
  
-   未命名成员：  
  
    ```  
    struct s  
    {  
       unsigned int flag : 1;  
       unsigned int : 31;  
    }  
    ```  
  
## 内部浮点函数  
 当指定**\/Oi** 时，C\+\+ 和 C 编译器支持以内联方式生成  **x86 Specific \>** 和 **END x86 Specific**的 `atan、``atan2、``cos、``exp、``log、``log10、``sin、``sqrt 和` `tan`  函数。  对于 C 编译器，当使用这些内部函数时会丢失 ANSI 一致性，因为它们没有设置 `errno` 变量。  
  
## 将非常数指针参数传递给需要常数指针参数的引用的函数  
 这是对 C\+\+ 的扩展。  此代码将编译 **\/Ze**:  
  
```  
typedef   int   T;  
  
const T  acT = 9;      // A constant of type 'T'  
const T* pcT = &acT;   // A pointer to a constant of type 'T'  
  
void func2 ( const T*& rpcT )   // A reference to a pointer to a constant of type 'T'  
{  
   rpcT = pcT;  
}  
  
T*   pT;               // A pointer to a 'T'  
  
void func ()  
{  
   func2 ( pT );      // Should be an error, but isn't detected  
   *pT   = 7;         // Invalidly overwrites the constant 'acT'  
}  
```  
  
## 未启用 ISO646.H  
 在 **\/Ze** 下，如果希望使用下列运算符的文本形式，必须包含 iso646.h：  
  
-   && \(和\)  
  
-   &\= \(和\_平衡\)  
  
-   & \(位和\)  
  
-   &#124; \(bitor\)  
  
-   ~ \(compl\)  
  
-   \!\(not\)  
  
-   \!\= \(not\_eq\)  
  
-   &#124;&#124; \(or\)  
  
-   &#124;\= \(or\_eq\)  
  
-   ^ \(xor\)  
  
-   ^\= \(xor\_eq\)  
  
## 字符串的地址具有类型 const char \[\]，而不是 const char \(\*\) \[\]  
 下面的示例在 **\/Za** 下输出 char const \(\*\)\[4\]，但在 **\/Ze** 下输出 char const \[4\]。  
  
```  
#include <stdio.h>  
#include <typeinfo>  
  
int main()  
{  
    printf_s("%s\n", typeid(&"abc").name());  
}  
```  
  
## 请参阅  
 [\/Za、\/Ze（禁用语言扩展）](../../build/reference/za-ze-disable-language-extensions.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)