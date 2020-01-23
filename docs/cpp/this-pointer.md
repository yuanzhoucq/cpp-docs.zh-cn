---
title: this 指针
description: this 指针是一个由编译器生成的指针，指向非静态成员函数中的当前对象。
ms.date: 01/22/2020
f1_keywords:
- this_cpp
helpviewer_keywords:
- nonstatic member functions [C++]
- pointers, to class instance
- this pointer
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
no-loc:
- this
- class
- struct
- union
- sizeof
- const
- volatile
ms.openlocfilehash: 58bba2edd7a457c624b747b5a65d209995852848
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518330"
---
# <a name="opno-locthis-pointer"></a>this 指针

**this** 指针只能在 **class** 、 **struct** 或 **union** 类型的非静态成员函数中访问指针。 它指向为其调用成员函数的对象。 静态成员函数没有 **this** 的指针。

## <a name="syntax"></a>语法

```cpp
this
this->member-identifier
```

## <a name="remarks"></a>备注

对象的 **this** 指针不是对象本身的组成部分。 它不会在对象的 **sizeof** 语句的结果中反映出来。 当为某个对象调用非静态成员函数时，编译器会将该对象的地址作为隐藏参数传递给该函数。 例如，以下函数调用：

```cpp
myDate.setMonth( 3 );
```

可以解释为：

```cpp
setMonth( &myDate, 3 );
```

对象的地址可从成员函数内作为 **this** 指针。 大多数 **this** 指针都是隐式的。 尽管在引用 class的成员时，使用显式 **this** 却是合法的。 例如：

```cpp
void Date::setMonth( int mn )
{
   month = mn;            // These three statements
   this->month = mn;      // are equivalent
   (*this).month = mn;
}
```

表达式 `*this` 通常用于从成员函数返回当前对象：

```cpp
return *this;
```

**this** 指针还用于防止自引用：

```cpp
if (&Object != this) {
// do not execute in cases of self-reference
```

> [!NOTE]
> 由于 **this** 指针不可更改，因此不允许向 **this** 指针赋值。 的C++早期实现允许分配到 **this** 。

有时会直接使用 **this** 指针（例如，用于处理自引用数据结构，此时需要当前对象的地址）。

## <a name="example"></a>示例

```cpp
// this_pointer.cpp
// compile with: /EHsc

#include <iostream>
#include <string.h>

using namespace std;

class Buf
{
public:
    Buf( char* szBuffer, size_t sizeOfBuffer );
    Buf& operator=( const Buf & );
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

Buf& Buf::operator=( const Buf &otherbuf )
{
    if( &otherbuf != this )
    {
        if (buffer)
            delete [] buffer;

        sizeOfBuffer =  strlen( otherbuf.buffer ) + 1;
        buffer = new char[sizeOfBuffer];
        strcpy_s( buffer, sizeOfBuffer, otherbuf.buffer );
    }
    return *this;
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

## <a name="type-of-the-opno-locthis-pointer"></a>this 指针的类型

**this** 指针的类型可由 **const** 和 **volatile** 关键字在函数声明中修改。 若要声明一个具有这些属性的函数，请在函数参数列表后面添加关键字。

请看一个示例：

```cpp
// type_of_this_pointer1.cpp
class Point
{
    unsigned X() const;
};
int main()
{
}
```

前面的代码声明一个成员函数 `X`，其中 **this** 指针被视为指向 **const** 对象的 **const** 指针。 可以使用*cv-现代型列表*选项的组合，但它们始终修改由 **this** 指针指向的对象，而不是指针本身。 下面的声明声明函数 `X`，其中 **this** 指针是指向 **const** 对象的 **const** 指针：

```cpp
// type_of_this_pointer2.cpp
class Point
{
    unsigned X() const;
};
int main()
{
}
```

成员函数中 **this** 的类型由以下语法描述。 *Cv 限定符列表*是从成员函数的声明符中确定的。 它可以是 **const** 或 **volatile** （或两者）。 *class类型*是 class的名称：

[*cv 限定符列表*] *class类型* **\* const this**

换句话说， **this** 指针始终是 const 指针。 不能重新分配它。  成员函数声明中使用的 **const** 或 **volatile** 限定符适用于在该函数的作用域中 **this** 指针指向的 class 实例。

下表介绍了有关这些修饰符的工作方式的更多信息。

### <a name="semantics-of-opno-locthis-modifiers"></a>this 修饰符的语义

|修饰符|含义|
|--------------|-------------|
|**const**|无法更改成员数据;无法调用不 **const** 的成员函数。|
|**volatile**|每次访问成员数据时，都将从内存中加载该成员数据;禁用某些优化。|

将 **const** 对象传递到不 **const** 的成员函数是错误的。

同样，将 **volatile** 对象传递到不 **volatile** 的成员函数也是错误的。

声明为 **const** 的成员函数无法更改成员数据，在此类函数中， **this** 指针是指向 **const** 对象的指针。

> [!NOTE]
> 构造函数和析构函数不能声明为 **const** 或 **volatile** 。 但是，可以在 **const** 或 **volatile** 对象上调用它们。

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)
