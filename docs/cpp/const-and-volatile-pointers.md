---
title: 固定和可变指针
ms.date: 11/19/2019
helpviewer_keywords:
- volatile keyword [C++], and pointers
- pointers, and const
- pointers, and volatile
- const keyword [C++], volatile pointers
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
ms.openlocfilehash: c0aafde9070275abcb270710e2d4a7a8d9806267
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246631"
---
# <a name="const-and-volatile-pointers"></a>固定和可变指针

[Const](const-cpp.md)和[volatile](volatile-cpp.md)关键字更改指针的处理方式。 **Const**关键字指定在初始化之后不能修改指针;此后，指针会受到保护。

**Volatile**关键字指定与后面的名称关联的值可以通过用户应用程序中的其他操作进行修改。 因此， **volatile**关键字适用于在共享内存中声明对象，这些对象可以由多个进程或用于与中断服务例程通信的全局数据区域访问。

如果将名称声明为**volatile**，则每次程序访问该名称时，编译器都将从内存中重新加载该值。 这将显著减少可能的优化。 但是，当对象的状态可能意外更改时，这是保证可预见的程序性能的唯一方法。

若要将指针指向的对象声明为**const**或**volatile**，请使用以下形式的声明：

```cpp
const char *cpch;
volatile char *vpch;
```

若要声明指针的值（即，存储在指针中的实际地址为**const**或**volatile**），请使用以下形式的声明：

```cpp
char * const pchc;
char * volatile pchv;
```

C++ 语言禁止将允许修改的对象的分配或指针声明为**const**。 此类赋值会移除用来声明对象或指针的信息，从而违反原始声明的意图。 请考虑以下声明：

```cpp
const char cch = 'A';
char ch = 'B';
```

由于前面的两个对象（`cch`、类型为**const char**、类型为 char 的 `ch` **）** ，以下声明/初始化有效：

```cpp
const char *pch1 = &cch;
const char *const pch4 = &cch;
const char *pch5 = &ch;
char *pch6 = &ch;
char *const pch7 = &ch;
const char *const pch8 = &ch;
```

以下声明/初始化存在错误。

```cpp
char *pch2 = &cch;   // Error
char *const pch3 = &cch;   // Error
```

`pch2` 的声明声明了一个可以用来修改常量对象的指针，因此不允许使用。 `pch3` 的声明指定指针是常量，而不是对象;由于同一原因，不允许声明 `pch2` 声明。

以下八个赋值显示了通过指针进行的赋值以及对前面的声明的指针值的更改；现在，假设 `pch1` 到 `pch8` 的初始化是正确的。

```cpp
*pch1 = 'A';  // Error: object declared const
pch1 = &ch;   // OK: pointer not declared const
*pch2 = 'A';  // OK: normal pointer
pch2 = &ch;   // OK: normal pointer
*pch3 = 'A';  // OK: object not declared const
pch3 = &ch;   // Error: pointer declared const
*pch4 = 'A';  // Error: object declared const
pch4 = &ch;   // Error: pointer declared const
```

声明为**volatile**或与**const**和**volatile**混合的指针遵循相同的规则。

指向**const**对象的指针通常在函数声明中使用，如下所示：

```cpp
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );
```

前面的语句声明一个函数， [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)，其中有两个参数的类型指针为**char**。 由于参数是通过引用传递的，而不是按值传递的，因此，如果 `strSource` 未声明为**const**，则函数将可以自由修改 `strDestination` 和 `strSource`。 作为**const** `strSource` 的声明可确保调用方不能通过被调用函数更改 `strSource`。

> [!NOTE]
> 由于存在从*typename* <strong>\*</strong>到**const** *typename* <strong>\*</strong>的标准转换，因此将类型 `char *` 的参数传递给[strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)是合法的。 但是，反之亦然。不存在用于从对象或指针中删除**const**特性的隐式转换。

可以将给定类型的**常量**指针分配给同一类型的指针。 但是，不能将不是**常量**的指针赋给**常量**指针。 以下代码显示了正确和错误的赋值：

```cpp
// const_pointer.cpp
int *const cpObject = 0;
int *pObject;

int main() {
pObject = cpObject;
cpObject = pObject;   // C3892
}
```

以下示例显示了当有指针指向某个指向对象的指针时如何将对象声明为 const。

```cpp
// const_pointer2.cpp
struct X {
   X(int i) : m_i(i) { }
   int m_i;
};

int main() {
   // correct
   const X cx(10);
   const X * pcx = &cx;
   const X ** ppcx = &pcx;

   // also correct
   X const cx2(20);
   X const * pcx2 = &cx2;
   X const ** ppcx2 = &pcx2;
}
```

## <a name="see-also"></a>另请参阅

[指针](pointers-cpp.md)
[原始指针](raw-pointers.md)