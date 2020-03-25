---
title: 别名和 typedef (C++)
ms.date: 11/04/2016
f1_keywords:
- typedef_cpp
ms.assetid: af1c24d2-4bfd-408a-acfc-482e264232f5
ms.openlocfilehash: 7a45c4570341aca056b9d4c30ea496317a1ac96f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181559"
---
# <a name="aliases-and-typedefs-c"></a>别名和 typedef (C++)

可以使用*别名声明*来声明一个名称，用作之前声明的类型的同义词。 （此机制也称为 "*类型别名*"。 你还可以使用此机制来创建*别名模板*，该模板对于自定义分配器特别有用。

## <a name="syntax"></a>语法

```
using identifier = type;
```

## <a name="remarks"></a>备注

*identifier*<br/>
别名的名称。

type<br/>
您为其创建别名的类型标识符。

别名未引入新类型，且无法更改现有类型名称的含义。

别名的最简单形式等效于 c + + 03 中的**typedef**机制：

```cpp
// C++11
using counter = long;

// C++03 equivalent:
// typedef long counter;
```

二者都支持创建“计数器”类型的变量。 对于 `std::ios_base::fmtflags` 而言，像这样的类型别名会更有用：

```cpp
// C++11
using fmtfl = std::ios_base::fmtflags;

// C++03 equivalent:
// typedef std::ios_base::fmtflags fmtfl;

fmtfl fl_orig = std::cout.flags();
fmtfl fl_hex = (fl_orig & ~std::cout.basefield) | std::cout.showbase | std::cout.hex;
// ...
std::cout.flags(fl_hex);
```

别名还能使用函数指针，但其可读性比等效的 typedef 更多：

```cpp
// C++11
using func = void(*)(int);

// C++03 equivalent:
// typedef void (*func)(int);

// func can be assigned to a function pointer value
void actual_function(int arg) { /* some code */ }
func fptr = &actual_function;
```

**Typedef**机制的限制是不能用于模板。 但是，C++11 中的类型别名语法支持创建别名模板：

```cpp
template<typename T> using ptr = T*;

// the name 'ptr<T>' is now an alias for pointer to T
ptr<int> ptr_int;
```

## <a name="example"></a>示例

以下示例说明如何将别名模板与自定义分配器一起使用 - 在此示例中，它是一个整数矢量类型。 您可以使用**int**的任何类型来创建一个方便的别名，以便在主功能代码中隐藏复杂的参数列表。 通过在代码中使用自定义分配器，您可以提高可读性并降低引入由拼写错误导致的 Bug 的风险。

```cpp
#include <stdlib.h>
#include <new>

template <typename T> struct MyAlloc {
    typedef T value_type;

    MyAlloc() { }
    template <typename U> MyAlloc(const MyAlloc<U>&) { }

    bool operator==(const MyAlloc&) const { return true; }
    bool operator!=(const MyAlloc&) const { return false; }

    T * allocate(const size_t n) const {
        if (n == 0) {
            return nullptr;
        }

        if (n > static_cast<size_t>(-1) / sizeof(T)) {
            throw std::bad_array_new_length();
        }

        void * const pv = malloc(n * sizeof(T));

        if (!pv) {
            throw std::bad_alloc();
        }

        return static_cast<T *>(pv);
    }

    void deallocate(T * const p, size_t) const {
        free(p);
    }
};

#include <vector>
using MyIntVector = std::vector<int, MyAlloc<int>>;

#include <iostream>

int main ()
{
    MyIntVector foov = { 1701, 1764, 1664 };

    for (auto a: foov) std::cout << a << " ";
    std::cout << "\n";

    return 0;
}
```

```Output
1701 1764 1664
```

## <a name="typedefs"></a>Typedef

**Typedef**声明引入一个名称，该名称在其作用域内成为声明的*类型声明*部分提供的类型的同义词。

使用 typedef 声明，可以为已由语言定义的类型和对你已声明的类型构造更短或更有意义的名称。 利用 Typedef 名称，您可以封装可能会发生更改的实现详细信息。

与**类**、**结构**、**联合**和**枚举**声明相比， **typedef**声明不会引入新类型，而是引入现有类型的新名称。

使用**typedef**声明的名称将占用与其他标识符相同的命名空间（不包括语句标签）。 因此，它们不能使用与前一个声明的名称相同的标识符（除了在类类型声明中）。 请考虑以下示例：

```cpp
// typedef_names1.cpp
// C2377 expected
typedef unsigned long UL;   // Declare a typedef name, UL.
int UL;                     // C2377: redefined.
```

与其他标识符相关的名称隐藏规则还可控制使用**typedef**声明的名称的可见性。 因此，以下示例在 C++ 中是合法的：

```cpp
// typedef_names2.cpp
typedef unsigned long UL;   // Declare a typedef name, UL
int main()
{
   unsigned int UL;   // Redeclaration hides typedef name
}

// typedef UL back in scope
```

```cpp
// typedef_specifier1.cpp
typedef char FlagType;

int main()
{
}

void myproc( int )
{
    int FlagType;
}
```

当通过与 typedef 相同的名称声明本地范围标识符时，或者在同一范围内或内部范围内声明结构或联合的成员时，必须指定类型说明符。 例如：

```cpp
typedef char FlagType;
const FlagType x;
```

若要对标识符、结构成员或联合成员重用 `FlagType` 名称，则必须提供类型：

```cpp
const int FlagType;  // Type specifier required
```

仅仅编写以下语句是不够的

```cpp
const FlagType;      // Incomplete specification
```

由于 `FlagType` 被当做该类型的一部分，因此没有要重新声明的标识符。 此声明被视为非法声明，例如

```cpp
int;  // Illegal declaration
```

可以使用 typedef 声明任何类型，包括指针、函数和数组类型。 只要定义具有与声明相同的可见性，那么在定义结构或联合类型之前，您就可以为指向结构或联合类型的指针声明 typedef 名称。

### <a name="examples"></a>示例

**Typedef**声明的一种用途是使声明更加统一和紧凑。 例如：

```cpp
typedef char CHAR;          // Character type.
typedef CHAR * PSTR;        // Pointer to a string (char *).
PSTR strchr( PSTR source, CHAR target );
typedef unsigned long ulong;
ulong ul;     // Equivalent to "unsigned long ul;"
```

若要使用**typedef**指定同一声明中的基础类型和派生类型，可以使用逗号分隔声明符。 例如：

```cpp
typedef char CHAR, *PSTR;
```

下面的示例为不返回值并采用两个 int 自变量的函数提供了类型 `DRAWF`

```cpp
typedef void DRAWF( int, int );
```

在上述**typedef**语句之后，声明

```cpp
DRAWF box;
```

将等效于声明

```cpp
void box( int, int );
```

**typedef**通常与**struct**组合在一起，以声明和命名用户定义的类型：

```cpp
// typedef_specifier2.cpp
#include <stdio.h>

typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;

int main()
{
    mystruct ms;
    ms.i = 10;
    ms.f = 0.99;
    printf_s("%d   %f\n", ms.i, ms.f);
}
```

```Output
10   0.990000
```

### <a name="re-declaration-of-typedefs"></a>typedef 的重新声明

可以使用**typedef**声明来重新声明相同的名称，以引用同一类型。 例如：

```cpp
// FILE1.H
typedef char CHAR;

// FILE2.H
typedef char CHAR;

// PROG.CPP
#include "file1.h"
#include "file2.h"   // OK
```

程序*进程。CPP*包括两个标头文件，这两个文件都包含名称 `CHAR`的**typedef**声明。 只要两个声明都引用同一个类型，则此类重新声明是可以接受的。

**Typedef**不能重新定义之前声明为其他类型的名称。 因此，如果*FILE2。H*包含

```cpp
// FILE2.H
typedef int CHAR;     // Error
```

由于尝试了将名称 `CHAR` 重新声明为引用不同类型，编译器引发了错误。 此错误的影响范围包含了构造，例如：

```cpp
typedef char CHAR;
typedef CHAR CHAR;      // OK: redeclared as same type

typedef union REGS      // OK: name REGS redeclared
{                       //  by typedef name with the
    struct wordregs x;  //  same meaning.
    struct byteregs h;
} REGS;
```

### <a name="typedefs-in-c-vs-c"></a>与 C C++中的 typedef

在很大程度上支持使用具有类类型的**typedef**说明符，因为在**typedef**声明中声明未命名的结构时存在 ANSI C 的做法。 例如，许多 C 程序员都使用：

```cpp
// typedef_with_class_types1.cpp
// compile with: /c
typedef struct {   // Declare an unnamed structure and give it the
                   // typedef name POINT.
   unsigned x;
   unsigned y;
} POINT;
```

此类声明的优点是它允许如下声明：

```cpp
POINT ptOrigin;
```

而不是：

```cpp
struct point_t ptOrigin;
```

在C++中， **typedef**名称与实类型（用**类**、**结构**、**联合**和**枚举**关键字声明）之间的差异更不同。 尽管在**typedef**语句中声明无编号结构的 C 惯例仍有效，但它不像在 c 中那样提供任何符号的优势。

```cpp
// typedef_with_class_types2.cpp
// compile with: /c /W1
typedef struct {
   int POINT();
   unsigned x;
   unsigned y;
} POINT;
```

前面的示例使用未命名的类**typedef**语法声明名为 `POINT` 的类。 `POINT` 被视为类名称；但是，以下限制适用于通过这种方式引入的名称：

- 名称（同义词）不能出现在**类**、**结构**或**联合**前缀之后。

- 名称不能用作类声明中的构造函数名称或析构函数名称。

总之，该语法不提供针对继承、构造或析构的任何机制。
