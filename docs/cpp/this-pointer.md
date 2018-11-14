---
title: this 指针
ms.date: 11/04/2016
f1_keywords:
- this_cpp
helpviewer_keywords:
- nonstatic member functions [C++]
- pointers, to class instance
- this pointer
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
ms.openlocfilehash: 586ed9d7e07165af71eeb2ee7ab22aba9570bcd3
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328872"
---
# <a name="this-pointer"></a>this 指针

**这**指针是只能在非静态成员函数中访问指针**类**，**结构**，或者**联合**类型。 它指向为其调用成员函数的对象。 静态成员函数不具有**这**指针。

## <a name="syntax"></a>语法

```
this
this->member-identifier
```

## <a name="remarks"></a>备注

对象的**这**指针不是对象本身; 的一部分不会反映结果中的**sizeof**对象上的语句。 相反，当对某个对象调用非静态成员函数时，该对象的地址将由编译器作为隐藏的自变量传递给函数。 例如，以下函数调用：

```cpp
myDate.setMonth( 3 );
```

可以按以下方式解释：

```cpp
setMonth( &myDate, 3 );
```

对象的地址可用于从作为成员函数的内部**这**指针。 大多数用途**这**是隐式的。 它是合法的但没有必要显式使用**这**引用类的成员时。 例如：

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

**这**指针还用于防止自引用：

```cpp
if (&Object != this) {
// do not execute in cases of self-reference
```

> [!NOTE]
>  因为**这**指针是不可修改，赋值**这**不允许。 C++ 的早期实现允许对分配**这**。

有时，**这**直接使用指针 — 例如，操作自引用数据结构，其中当前对象的地址是必需的。

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

    // assignment opperator
    myBuf = yourBuf;

    // Display 'your buffer'
    myBuf.Display();
}
```

```Output
my buffer
your buffer
```

## <a name="type-of-the-this-pointer"></a>this 指针的类型

**这**指针的类型可以通过在函数声明中修改**const**并**易失性**关键字。 若要将函数声明为具有一个或多个关键字的特性，请将关键字添加到函数自变量列表的后面。

请看以下示例：

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

前面的代码声明成员函数时， `X`，在其中**这**指针被视为**const**指向**const**对象。 组合*cv mod 列表*可以使用选项，但它们始终修改指向的对象**这**，而不**这**指针本身。 因此，以下声明将声明函数`X`;**这**指针位于**const**指向**const**对象：

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

类型**这**中成员函数描述的以下语法，其中*cv 限定符列表*从成员函数声明符中确定和可以为**const**或**易失性**（或两者），并*类类型*是类的名称：

*[cv 限定符列表] 类类型***&#42; const 这**

换而言之，**这**始终是 const 指针; 无法重新分配。  **Const**或**易失性**成员函数声明中使用的限定符应用于类实例，指向**这**该函数的作用域中。

下表介绍了有关这些修饰符的工作方式的更多信息。

### <a name="semantics-of-this-modifiers"></a>this 修饰符的语义

|修饰符|含义|
|--------------|-------------|
|**const**|不能更改成员数据;无法调用成员函数不是**const**。|
|**volatile**|每次访问成员数据时，都会从内存中加载该数据；禁用某些优化。|

它是传递错误**const**对象的成员函数不是**const**。 同样，它是错误传递**可变**对象的成员函数不是**易失性**。

成员函数声明为**const**不能更改成员数据 — 在此类函数**这**指针是指向**const**对象。

> [!NOTE]
>  构造函数和析构函数不能声明为**const**或**易失性**。 它们，但是，可以在调用**const**或**易失性**对象。

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)