---
title: "对齐 （C++） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- align_cpp
dev_langs:
- C++
helpviewer_keywords:
- align __declspec keyword
- __declspec keyword [C++], align
ms.assetid: 9cb63f58-658b-4425-ac47-af8eabfc5878
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 10c83ebb195cf4ee75c7be15b4d2ab9607f46743
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2018
---
# <a name="align-c"></a>align (C++)

在 Visual Studio 2015 及更高版本，使用 C++ 11 标准`alignas`说明符来控制对齐效果。 有关详细信息，请参阅[对齐](../cpp/alignment-cpp-declarations.md)。

**Microsoft 专用**

使用 `__declspec(align(#))` 准确控制用户定义的数据的对齐方式（例如，函数中的静态分配或自动数据）。

## <a name="syntax"></a>语法

> **__declspec( align(** *#* **) )** *declarator*  

## <a name="remarks"></a>备注

编写使用最新的处理器指令的应用程序会引入一些新的约束和问题。 具体而言，许多新指令要求数据必须与 16 字节边界对齐。 另外，通过将常用数据与特定处理器的缓存行大小对齐，可以提高缓存性能。 例如，如果你定义一个大小小于 32 字节的结构，你可能希望将此结构对齐到 32 字节，以确保有效缓存该结构类型的对象。

\#是对齐值。 有效项为介于 1 和 8192（字节）之间的 2 的整数幂，如 2、4、8、16、32 或 64。 `declarator` 是你声明为对齐的数据。

有关如何返回类型的值信息`size_t`类型的对齐要求，请参阅[__alignof](../cpp/alignof-operator.md)。 有关如何面向 64 位处理器时声明未对齐的指针的信息，请参阅[__unaligned](../cpp/unaligned.md)。

在定义 `__declspec(align(#))`、`struct` 或 `union` 时或声明变量时，可以使用 `class`。

编译器不保证或不尝试保留复制过程中或数据转换操作中数据的对齐特性。 例如， [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)可以将复制与声明的结构`__declspec(align(#))`到任何位置。 请注意，普通分配器 — 例如， [malloc](../c-runtime-library/reference/malloc.md)，C++[运算符 new](new-operator-cpp.md)，和 Win32 分配器-返回的通常不充分对齐的内存`__declspec(align(#))`结构或者的数组结构。 若要保证复制或数据转换操作的目标正确对齐，使用[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)，或编写你自己的分配器。

不能指定函数参数的对齐方式。 当通过堆栈上的值传递具有对齐特性的数据，它的对齐由调用约定控制。 如果数据对齐在所调用函数中很重要，请在使用前将参数复制到正确对齐的内存中。

而无需`__declspec(align(#))`，编译器通常对齐自然边界根据目标处理器和之前在 32 位处理器上的 4 字节边界的数据的大小和 64 位处理器上的 8 字节边界上的数据。 类或结构中的数据的对齐方式的类或结构的最小值其自然对齐和当前包装设置 (从 #pragma`pack`或**/Zp**编译器选项)。

本示例演示 `__declspec(align(#))` 的使用：

```cpp
__declspec(align(32)) struct Str1{
   int a, b, c, d, e;
};
```

此类型现在具有 32 字节对齐特性。 这意味着所有静态和自动实例都在 32 字节边界上启动。 使用此类型作为成员声明的其他结构类型保留此类型的对齐特性，即，任何结构与`Str1`如元素具有对齐特性至少 32 个。

请注意，`sizeof(struct Str1)` 等于 32。 这意味着，如果创建 Str1 对象的数组，并且该数组的基为对齐的 32 字节，则数组的每个成员也是对齐的 32 字节。 若要在动态内存中创建其基本正确对齐的数组，使用[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)，或编写你自己的分配器。

任何结构的 `sizeof` 值是最终成员的偏移量加上该成员的大小，向上舍入为最大成员对齐值的最接近倍数或整个结构的对齐值（以较大者为准）。

编译器使用以下结构对齐规则：

- 除非使用 `__declspec(align(#))` 进行重写，否则标量结构成员的对齐方式为其大小和当前包装的最小值。

- 除非使用 `__declspec(align(#))` 进行重写，否则结构的对齐方式是其成员单个对齐方式的最大值。

- 结构成员被放置从其父级结构的开头的偏移量位置，父级结构是大于或等于前一个成员末尾的偏移量的对齐的最小倍数。

- 结构的大小是大于或等于其最后一个成员末尾的偏移量的对齐的最小倍数。

`__declspec(align(#))` 只能增大对齐限制。

有关详细信息，请参见:

- [对齐示例](#vclrfalignexamples)

- [使用 __declspec(align(#)) 定义新类型](#vclrf_declspecaligntypedef)

- [在线程本地存储区中对齐数据](#vclrfthreadlocalstorageallocation)

- [对齐如何与数据打包配合使用](#vclrfhowalignworkswithdatapacking)

- [结构对齐示例](../build/examples-of-structure-alignment.md)(特定于 x64)

##  <a name="vclrfalignexamples"></a>对齐示例

以下示例说明 `__declspec(align(#))` 如何影响数据结构的大小和对齐方式。 这些示例假定下列定义：

```cpp
#define CACHE_LINE  32
#define CACHE_ALIGN __declspec(align(CACHE_LINE))
```

在此示例中，通过使用 `S1` 定义 `__declspec(align(32))` 结构。 针对一个变量定义或其他类型声明中的全部 `S1` 使用均为 32 字节对齐。 `sizeof(struct S1)` 返回 32，并且 `S1` 在包含四个整数所需的 16 字节之后有 16 个填充字节。 每个 `int` 成员要求为 4 字节对齐，但它自身结构的对齐声明为 32 字节。 因此，整体为 32 字节对齐。

```cpp
struct CACHE_ALIGN S1 { // cache align all instances of S1
   int a, b, c, d;
};
struct S1 s1;   // s1 is 32-byte cache aligned
```

在此示例中，`sizeof(struct S2)` 返回 16，它恰好为成员大小的总和，因为这是最大对齐要求的倍数（8 的倍数）。

```cpp
__declspec(align(8)) struct S2 {
   int a, b, c, d;
};
```

在下面的示例中，`sizeof(struct S3)` 返回 64。

```cpp
struct S3 {
   struct S1 s1;   // S3 inherits cache alignment requirement
                  // from S1 declaration
   int a;         // a is now cache aligned because of s1
                  // 28 bytes of trailing padding
};
```

在此示例中，注意 `a` 具有自然类型的对齐方式，在这种情况下为 4 字节。 但是，`S1` 必须是对齐的 32 字节。 填充的 28 个字节遵循 `a`，因此 `s1` 从偏移量 32 开始。 然后，`S4` 将继承 `S1` 的对齐要求，因为这是结构中的最大对齐要求。 `sizeof(struct S4)` 返回 64。

```cpp
struct S4 {
   int a;
   // 28 bytes padding
    struct S1 s1;      // S4 inherits cache alignment requirement of S1
};
```

以下三个变量声明还使用 `__declspec(align(#))`。 在每种情况下，变量必须是对齐的 32 字节。 对于数组，数组的基址（而非每个数组成员）是对齐的 32 字节。 使用 `sizeof` 不会影响每个数组成员的 `__declspec(align(#))` 值。

```cpp
CACHE_ALIGN int i;
CACHE_ALIGN int array[128];
CACHE_ALIGN struct s2 s;
```

若要对齐数组的每个成员，应使用如下代码：

```cpp
typedef CACHE_ALIGN struct { int a; } S5;
S5 array[10];
```

在此示例中，注意对齐结构本身与对齐第一个元素具有相同的效果：

```cpp
CACHE_ALIGN struct S6 {
   int a;
   int b;
};

struct S7 {
   CACHE_ALIGN int a;
               int b;
};
```

`S6` 和 `S7` 具有相同的对齐、分配和大小特性。

在此示例中，a、b、c 和 d 的起始地址的对齐方式分别为 4、1、4 和 1。

```cpp
void fn() {
   int a;
   char b;
   long c;
   char d[10]
}
```

在堆上分配了内存时，对齐方式取决于所调用的分配函数。  例如，如果你使用 `malloc`，则该结果取决于操作数大小。 如果*arg* > = 8，返回的内存为 8 字节对齐。 如果*arg* < 8，返回的内存的对齐方式是 2 的一次幂小于*arg*。 例如，如果你使用 malloc(7)，则对齐方式为 4 字节。

##  <a name="vclrf_declspecaligntypedef"></a>使用 __declspec(align(#)) 定义新类型

可以使用对齐特性定义类型。

例如，你可以定义`struct`带的对齐方式值这种方式：

```cpp
struct aType {int a; int b;};
typedef __declspec(align(32)) struct aType bType;
```

现在，`aType`和`bType`（8 字节） 的大小相同但类型的变量`bType`均为 32 字节对齐。

##  <a name="vclrfthreadlocalstorageallocation"></a>在线程本地存储区中对齐数据

使用 `__declspec(thread)` 特性创建的置于映像中的 TLS 部分中的静态线程-本地存储 (TLS) 与常规静态数据一样适用于对齐。 若要创建 TLS 数据，操作系统需分配 TLS 部分大小的内存并遵循 TLS 部分对齐特性。

此示例说明用于将对齐的数据置于线程本地存储区中的各种方法。

```cpp
// put an aligned integer in TLS
__declspec(thread) __declspec(align(32)) int a;

// define an aligned structure and put a variable of the struct type
// into TLS
__declspec(thread) __declspec(align(32)) struct F1 { int a; int b; } a;

// create an aligned structure
struct CACHE_ALIGN S9 {
   int a;
   int b;
};
// put a variable of the structure type into TLS
__declspec(thread) struct S9 a;
```

##  <a name="vclrfhowalignworkswithdatapacking"></a>对齐如何与数据打包配合使用

**/Zp**编译器选项和`pack`杂注起的装箱的结构和联合成员的数据。此示例演示如何**/Zp**和`__declspec(align(#))`协同工作：

```c[[]]
struct S {
   char a;
   short b;
   double c;
   CACHE_ALIGN double d;
   char e;
   double f;
};
```

下表列出了在各种下每个成员的偏移量**/Zp** (或 #pragma `pack`) 值，显示两个交互的方式。

|变量|/Zp1|/Zp2|/Zp4|/Zp8|
|--------------|-----------|-----------|-----------|-----------|
|a|0|0|0|0|
|b|1|2|2|2|
|c|3|4|4|8|
|d|32|32|32|32|
|e|40|40|40|40|
|f|41|42|44|48|
|sizeof(S)|64|64|64|64|

有关详细信息，请参阅 [/Zp（结构成员对齐）](../build/reference/zp-struct-member-alignment.md)。

对象的偏移量基于上一个对象的偏移量和当前打包设置，除非该对象具有 `__declspec(align(#))` 特性，在此情况下，对齐将基于上一个对象的偏移量和该对象的 `__declspec(align(#))` 值。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__declspec](../cpp/declspec.md)  
[ARM ABI 约定概述](../build/overview-of-arm-abi-conventions.md)  
[x64 调用约定概述](../build/overview-of-x64-calling-conventions.md)  
