---
title: 编译器错误 C2666
ms.date: 11/04/2016
f1_keywords:
- C2666
helpviewer_keywords:
- C2666
ms.assetid: 78364d15-c6eb-439a-9088-e04a0176692b
ms.openlocfilehash: 4a1d46f3b000b5054564b05ca2c3c94a9e7b6398
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386871"
---
# <a name="compiler-error-c2666"></a>编译器错误 C2666

identifier： 数字重载有相似的转换

重载的函数或运算符不明确。   形参列表中可能是编译器要解决多义性问题非常相似。  若要解决此错误，显式转换一个或多个实际参数。

下面的示例生成 C2666:

```
// C2666.cpp
struct complex {
   complex(double);
};

void h(int,complex);
void h(double, double);

int main() {
   h(3,4);   // C2666
}
```

为 Visual Studio.NET 2003年执行的编译器一致性工作，还可以生成此错误：

- 二元运算符和用户定义转换为指针类型

- 限定转换不是标识转换相同

对于二元运算符\<，>， \<=、 和 > =、 传递参数现在隐式转换为操作数的类型如果参数的类型定义了一个用户定义的转换运算符，以将转换为操作数的类型。 现在可能会不明确。

在 Visual Studio.NET 2003年和 Visual Studio.NET 版本的视觉对象中是有效的代码的C++，调用类运算符显式使用函数的语法。

## <a name="example"></a>示例

```
// C2666b.cpp
#include <string.h>
#include <stdio.h>

struct T
{
    T( const T& copy )
    {
        m_str = copy.m_str;
    }

    T( const char* str )
    {
        int iSize = (strlen( str )+ 1);
        m_str = new char[ iSize ];
        if (m_str)
            strcpy_s( m_str, iSize, str );
    }

    bool operator<( const T& RHS )
    {
        return m_str < RHS.m_str;
    }

    operator char*() const
    {
        return m_str;
    }

    char* m_str;
};

int main()
{
    T str1( "ABCD" );
    const char* str2 = "DEFG";

    // Error - Ambiguous call to operator<()
    // Trying to convert str1 to char* and then call
    // operator<( const char*, const char* )?
    //  OR
    // trying to convert str2 to T and then call
    // T::operator<( const T& )?

    if( str1 < str2 )   // C2666

    if ( str1.operator < ( str2 ) )   // Treat str2 as type T
        printf_s("str1.operator < ( str2 )\n");

    if ( str1.operator char*() < str2 )   // Treat str1 as type char*
        printf_s("str1.operator char*() < str2\n");
}
```

## <a name="example"></a>示例

下面的示例生成 C2666

```
// C2666c.cpp
// compile with: /c

enum E
{
    E_A,   E_B
};

class A
{
    int h(const E e) const {return 0; }
    int h(const int i) { return 1; }
    // Uncomment the following line to resolve.
    // int h(const E e) { return 0; }

    void Test()
    {
        h(E_A);   // C2666
        h((const int) E_A);
        h((int) E_A);
    }
};
```