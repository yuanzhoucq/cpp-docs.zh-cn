---
title: 固定和可变指针 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- volatile keyword [C++], and pointers
- pointers, and const
- pointers, and volatile
- const keyword [C++], volatile pointers
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6582f8ace33c552f05c6f8d94634d3861ef04e6e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066632"
---
# <a name="const-and-volatile-pointers"></a>固定和可变指针

[Const](../cpp/const-cpp.md)并[易失性](../cpp/volatile-cpp.md)关键字更改指针的方式。 **Const**关键字指定指针不能在初始化之后修改; 此后修改保护指针。

**易失性**关键字指定操作以外的用户应用程序中的操作可以修改与跟的名称关联的值。 因此，**易失性**关键字可用于声明可由多个进程或用于与中断服务例程通信的全局数据区域访问的共享内存中的对象。

当名称声明为**易失性**，编译器重新加载内存中的值每次访问该程序。 这将显著减少可能的优化。 但是，当对象的状态可能意外更改时，这是保证可预见的程序性能的唯一方法。

若要声明为指针指向的对象**const**或**易失性**，使用窗体的声明：

```cpp
const char *cpch;
volatile char *vpch;
```

来声明指针的值 — 即指针中存储的实际地址 — 作为**const**或**易失性**，使用窗体的声明：

```cpp
char * const pchc;
char * volatile pchv;
```

C++ 语言禁止将允许修改的对象的分配或指针声明为**const**。 此类赋值会移除用来声明对象或指针的信息，从而违反原始声明的意图。 请考虑以下声明：

```cpp
const char cch = 'A';
char ch = 'B';
```

假定前面声明的两个对象 (`cch`，类型的**const char**，和`ch`，类型的**char)**，以下声明/初始化存在有效：

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

`pch2` 的声明声明了一个可以用来修改常量对象的指针，因此不允许使用。 声明`pch3`指定指针是常量，不是对象; 不允许使用相同的原因`pch2`不允许使用。

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

指针声明为**易失性**，或作为混合**const**并**易失性**，遵循相同的规则。

指向**const**对象通常用于函数声明中，如下所示：

```cpp
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );
```

前面的语句声明一个函数[strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)，其中两个三个参数是指针类型的**char**。 因为通过引用传递的参数，并且不由值，该函数可以随意修改这两`strDestination`并`strSource`如果`strSource`未声明为**const**。 声明`strSource`作为**const**调用方保证`strSource`所调用的函数不能更改。

> [!NOTE]
> 因为没有从的标准转换*typename* <strong>\*</strong>到**const** *typename*  <strong>\*</strong>，它是合法的类型的自变量传递`char *`到[strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)。 但是，反之不成立;删除的目的是隐式转换**const**从对象或指针的属性。

一个**const**给定类型的指针可以分配给同一类型的指针。 但是，指针的不是**const**不能分配给**const**指针。 以下代码显示了正确和错误的赋值：

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

## <a name="see-also"></a>请参阅

[指针](../cpp/pointers-cpp.md)