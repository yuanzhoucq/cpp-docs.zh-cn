---
title: ':::no-loc(this)::: 指针'
description: :::no-loc(this):::指针是一个由编译器生成的指针，指向非静态成员函数中的当前对象。
ms.date: 01/22/2020
f1_keywords:
- :::no-loc(this):::_cpp
helpviewer_keywords:
- nonstatic member functions [C++]
- 'pointers, to :::no-loc(class)::: instance'
- ':::no-loc(this)::: pointer'
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
no-loc:
- ':::no-loc(this):::'
- ':::no-loc(class):::'
- ':::no-loc(struct):::'
- ':::no-loc(union):::'
- ':::no-loc(sizeof):::'
- ':::no-loc(const):::'
- ':::no-loc(volatile):::'
ms.openlocfilehash: c851beaba7fe1091ffd7827714f90307303058c1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225821"
---
# <a name="no-locthis-pointer"></a>:::no-loc(this)::: 指针

**`:::no-loc(this):::`** 指针是只能在 **`:::no-loc(class):::`** 、 **`:::no-loc(struct):::`** 或类型的非静态成员函数内访问的指针 **`:::no-loc(union):::`** 。 它指向为其调用成员函数的对象。 静态成员函数没有 **`:::no-loc(this):::`** 指针。

## <a name="syntax"></a>语法

```cpp
:::no-loc(this):::
:::no-loc(this):::->member-identifier
```

## <a name="remarks"></a>备注

对象的 **`:::no-loc(this):::`** 指针不是对象本身的组成部分。 它不会在对象的语句结果中反映出来 **`:::no-loc(sizeof):::`** 。 当为某个对象调用非静态成员函数时，编译器会将该对象的地址作为隐藏参数传递给该函数。 例如，以下函数调用：

```cpp
myDate.setMonth( 3 );
```

可以解释为：

```cpp
setMonth( &myDate, 3 );
```

对象的地址在成员函数内作为 **`:::no-loc(this):::`** 指针提供。 大多数 **`:::no-loc(this):::`** 指针使用都是隐式的。 虽然不必要，但 **`:::no-loc(this):::`** 在引用的成员时使用显式是合法的 :::no-loc(class)::: 。 例如：

```cpp
void Date::setMonth( int mn )
{
   month = mn;            // These three statements
   :::no-loc(this):::->month = mn;      // are equivalent
   (*:::no-loc(this):::).month = mn;
}
```

表达式 **`*:::no-loc(this):::`** 通常用于从成员函数返回当前对象：

```cpp
return *:::no-loc(this):::;
```

**`:::no-loc(this):::`** 指针还用于防止自引用：

```cpp
if (&Object != :::no-loc(this):::) {
// do not execute in cases of self-reference
```

> [!NOTE]
> 由于 **`:::no-loc(this):::`** 指针不可更改，因此 **`:::no-loc(this):::`** 不允许向指针赋值。 C + + 的早期实现允许向赋值 **`:::no-loc(this):::`** 。

有时， **`:::no-loc(this):::`** 指针是直接使用的（例如，为了处理自引用数据 :::no-loc(struct)::: ures，其中需要当前对象的地址）。

## <a name="example"></a>示例

```cpp
// :::no-loc(this):::_pointer.cpp
// compile with: /EHsc

#include <iostream>
#include <string.h>

using namespace std;

:::no-loc(class)::: Buf
{
public:
    Buf( char* szBuffer, size_t sizeOfBuffer );
    Buf& operator=( :::no-loc(const)::: Buf & );
    void Display() { cout << buffer << endl; }

private:
    char*   buffer;
    size_t  sizeOfBuffer;
};

Buf::Buf( char* szBuffer, size_t sizeOfBuffer )
{
    sizeOfBuffer++; // account for a NULL terminator

    buffer = new char[ sizeOfBuffer ];
    if (buffer)
    {
        strcpy_s( buffer, sizeOfBuffer, szBuffer );
        sizeOfBuffer = sizeOfBuffer;
    }
}

Buf& Buf::operator=( :::no-loc(const)::: Buf &otherbuf )
{
    if( &otherbuf != :::no-loc(this)::: )
    {
        if (buffer)
            delete [] buffer;

        sizeOfBuffer =  strlen( otherbuf.buffer ) + 1;
        buffer = new char[sizeOfBuffer];
        strcpy_s( buffer, sizeOfBuffer, otherbuf.buffer );
    }
    return *:::no-loc(this):::;
}

int main()
{
    Buf myBuf( "my buffer", 10 );
    Buf yourBuf( "your buffer", 12 );

    // Display 'my buffer'
    myBuf.Display();

    // assignment operator
    myBuf = yourBuf;

    // Display 'your buffer'
    myBuf.Display();
}
```

```Output
my buffer
your buffer
```

## <a name="type-of-the-no-locthis-pointer"></a>指针的类型 :::no-loc(this):::

在 **`:::no-loc(this):::`** 函数声明中，可以使用和关键字修改指针的类型 **`:::no-loc(const):::`** **`:::no-loc(volatile):::`** 。 若要声明一个具有这些属性的函数，请在函数参数列表后面添加关键字。

请看一个示例：

```cpp
// type_of_:::no-loc(this):::_pointer1.cpp
:::no-loc(class)::: Point
{
    unsigned X() :::no-loc(const):::;
};
int main()
{
}
```

前面的代码声明一个成员函数，该函数 `X` 中的 **`:::no-loc(this):::`** 指针被视为 **`:::no-loc(const):::`** 指向对象的指针 **`:::no-loc(const):::`** 。 可以使用*cv-现代型列表*选项的组合，但它们始终修改指针所指向的对象 **`:::no-loc(this):::`** ，而不是指针本身。 下面的声明声明 function `X` ，其中 **`:::no-loc(this):::`** 指针是 **`:::no-loc(const):::`** 指向对象的指针 **`:::no-loc(const):::`** ：

```cpp
// type_of_:::no-loc(this):::_pointer2.cpp
:::no-loc(class)::: Point
{
    unsigned X() :::no-loc(const):::;
};
int main()
{
}
```

**`:::no-loc(this):::`** 成员函数中的类型由以下语法描述。 *Cv 限定符列表*是从成员函数的声明符中确定的。 它可以是 **`:::no-loc(const):::`** 或 **`:::no-loc(volatile):::`** （或两者）。 * :::no-loc(class)::: -type*是的名称 :::no-loc(class)::: ：

[*cv 限定符列表*]* :::no-loc(class)::: -type* ** \* :::no-loc(const)::: :::no-loc(this)::: **

换言之， **`:::no-loc(this):::`** 指针始终是一个 :::no-loc(const)::: 指针。 不能重新分配它。  **`:::no-loc(const):::`** **`:::no-loc(volatile):::`** 成员函数声明中使用的或限定符适用于指针所 :::no-loc(class)::: 指向的实例 **`:::no-loc(this):::`** ，在该函数的作用域中。

下表介绍了有关这些修饰符的工作方式的更多信息。

### <a name="semantics-of-no-locthis-modifiers"></a>修饰符的语义 :::no-loc(this):::

|修饰符|含义|
|--------------|-------------|
|**`:::no-loc(const):::`**|无法更改成员数据;无法调用不是的成员函数 **`:::no-loc(const):::`** 。|
|**`:::no-loc(volatile):::`**|每次访问成员数据时，都将从内存中加载该成员数据;禁用某些优化。|

将对象传递给不是的 **`:::no-loc(const):::`** 成员函数是错误的 **`:::no-loc(const):::`** 。

同样，将对象传递给不是的成员函数也是错误的 **`:::no-loc(volatile):::`** **`:::no-loc(volatile):::`** 。

声明为的成员函数 **`:::no-loc(const):::`** 不能更改成员数据-在此类函数中， **`:::no-loc(this):::`** 指针是指向 **`:::no-loc(const):::`** 对象的指针。

> [!NOTE]
> Con :::no-loc(struct)::: or 和 de :::no-loc(struct)::: or 不能声明为 **`:::no-loc(const):::`** 或 **`:::no-loc(volatile):::`** 。 但是，它们可以在 **`:::no-loc(const):::`** 或对象上调用 **`:::no-loc(volatile):::`** 。

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)
