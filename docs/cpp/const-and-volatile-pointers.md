---
title: 固定和可变指针
ms.date: 11/19/2019
helpviewer_keywords:
- volatile keyword [C++], and pointers
- pointers, and const
- pointers, and volatile
- const keyword [C++], volatile pointers
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
ms.openlocfilehash: a8fd25777d1169ba281fbee173c1c8f5673c8b56
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227564"
---
# <a name="const-and-volatile-pointers"></a>固定和可变指针

[Const](const-cpp.md)和[volatile](volatile-cpp.md)关键字更改指针的处理方式。 **`const`** 关键字指定在初始化之后不能修改指针; 之后，该指针将受到保护以防止修改。

**`volatile`** 关键字指定与后面的名称关联的值可以通过用户应用程序中的其他操作进行修改。 因此， **`volatile`** 关键字适用于在共享内存中声明对象，这些对象可以由多个进程或用于与中断服务例程进行通信的全局数据区域访问。

如果将名称声明为 **`volatile`** ，则编译器会在每次访问该程序时从内存中重新加载该值。 这将显著减少可能的优化。 但是，当对象的状态可能意外更改时，这是保证可预见的程序性能的唯一方法。

若要将指针指向的对象声明为 **`const`** 或 **`volatile`** ，请使用以下形式的声明：

```cpp
const char *cpch;
volatile char *vpch;
```

若要声明指针的值（即，存储在指针中的实际地址），请 **`const`** **`volatile`** 使用以下形式的声明：

```cpp
char * const pchc;
char * volatile pchv;
```

C + + 语言会阻止允许修改声明为的对象或指针的赋值 **`const`** 。 此类赋值会移除用来声明对象或指针的信息，从而违反原始声明的意图。 请考虑以下声明：

```cpp
const char cch = 'A';
char ch = 'B';
```

如果前面有两个对象的声明（ `cch` 、类型为**const char**、类型 `ch` 为**char）**，则以下声明/初始化有效：

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

`pch2` 的声明声明了一个可以用来修改常量对象的指针，因此不允许使用。 的声明 `pch3` 指定指针是常量，而不是对象; 由于同一原因，不允许声明，因此不 `pch2` 允许声明。

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

声明为的指针 **`volatile`** 或与 and 组合的 **`const`** 指针 **`volatile`** 遵循相同的规则。

指向 **`const`** 对象的指针通常在函数声明中使用，如下所示：

```cpp
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );
```

前面的语句声明一个函数[strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)，其中有两个参数的类型为指针 **`char`** 。 由于参数是通过引用传递的，而不是按值传递的，因此， `strDestination` `strSource` 如果 `strSource` 未将声明为，则函数将可以自由修改和 **`const`** 。 的声明 `strSource` **`const`** 可确保 `strSource` 被调用函数无法更改调用方。

> [!NOTE]
> 由于存在从*typename* <strong>\*</strong> 到 typename 的标准转换 **`const`** *typename* <strong>\*</strong> ，因此将类型的参数传递 `char *` 到[strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)是合法的。 但是，反之亦然。不存在用于 **`const`** 从对象或指针中删除特性的隐式转换。

**`const`** 可以将给定类型的指针分配给同一类型的指针。 但是，不 **`const`** 能将指针分配给 **`const`** 指针。 以下代码显示了正确和错误的赋值：

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
