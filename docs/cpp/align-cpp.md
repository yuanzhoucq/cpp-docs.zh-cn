---
title: align (C++)
ms.date: 12/17/2018
f1_keywords:
- align_cpp
helpviewer_keywords:
- align __declspec keyword
- __declspec keyword [C++], align
ms.assetid: 9cb63f58-658b-4425-ac47-af8eabfc5878
ms.openlocfilehash: 0a1212f1c78f49029f82be5a2f5d82ea1788b6e0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227655"
---
# <a name="align-c"></a>align (C++)

在 Visual Studio 2015 和更高版本中，使用 c + + 11 标准 **`alignas`** 说明符来控制对齐。 有关详细信息，请参阅[对齐](../cpp/alignment-cpp-declarations.md)。

**Microsoft 专用**

使用 `__declspec(align(#))` 准确控制用户定义的数据的对齐方式（例如，函数中的静态分配或自动数据）。

## <a name="syntax"></a>语法

> **__declspec （align （** *#* **））** *声明符*

## <a name="remarks"></a>备注

编写使用最新的处理器指令的应用程序会引入一些新的约束和问题。 许多新指令要求数据与16字节边界对齐。 此外，通过将频繁使用的数据与处理器的缓存行大小对齐，可以提高缓存性能。 例如，如果定义一个大小小于32个字节的结构，则可能需要32字节对齐方式，以确保有效缓存该结构类型的对象。

\#对齐值。 有效项为介于 1 和 8192（字节）之间的 2 的整数幂，如 2、4、8、16、32 或 64。 `declarator`要声明为对齐的数据。

有关如何返回作为类型对齐要求的类型的值的信息 `size_t` ，请参阅 [`alignof`](../cpp/alignof-operator.md) 。 有关如何在面向64位处理器时声明未对齐指针的信息，请参阅 [`__unaligned`](../cpp/unaligned.md) 。

在 `__declspec(align(#))` 定义 **`struct`** 、 **`union`** 、或 **`class`** 时，或在声明变量时，可以使用。

在复制或数据转换操作期间，编译器不保证或尝试保留数据的对齐属性。 例如， [`memcpy`](../c-runtime-library/reference/memcpy-wmemcpy.md) 可以将使用声明的结构复制 `__declspec(align(#))` 到任何位置。 一般的分配器（例如， [`malloc`](../c-runtime-library/reference/malloc.md) c + + [`operator new`](new-operator-cpp.md) 和 Win32 分配器）通常返回未充分对齐 `__declspec(align(#))` 结构或结构数组的内存。 为了保证复制或数据转换操作的目标正确对齐，请使用 [`_aligned_malloc`](../c-runtime-library/reference/aligned-malloc.md) 。 或者，编写自己的分配器。

不能为函数参数指定对齐方式。 当通过值在堆栈上传递具有对齐属性的数据时，其对齐方式由调用约定控制。 如果数据对齐在所调用函数中很重要，请在使用前将参数复制到正确对齐的内存中。

如果没有 `__declspec(align(#))` ，则编译器通常会根据目标处理器和数据的大小、32位处理器上最多4个字节的边界以及64位处理器上的8字节边界来对齐自然边界上的数据。 类或结构中的数据在类或结构中的最小自然对齐和当前打包设置（来自 `#pragma pack` 或 `/Zp` 编译器选项）对齐。

本示例演示 `__declspec(align(#))` 的使用：

```cpp
__declspec(align(32)) struct Str1{
   int a, b, c, d, e;
};
```

此类型现在具有 32 字节对齐特性。 这意味着所有静态实例和自动实例都以32字节边界开始。 将此类型声明为成员的其他结构类型保留此类型的对齐特性，即，作为元素的任何结构 `Str1` 都具有至少32的对齐特性。

此处， `sizeof(struct Str1)` 等于32。 这意味着，如果创建了一个 `Str1` 对象数组，并且该数组的基为32字节的对齐方式，则数组的每个成员也会调整32个字节。 若要创建其基在动态内存中正确对齐的数组，请使用 [`_aligned_malloc`](../c-runtime-library/reference/aligned-malloc.md) 。 或者，编写自己的分配器。

**`sizeof`** 任何结构的值是最终成员的偏移量加上该成员的大小，向上舍入为最大成员对齐值的最接近倍数或整个结构的对齐值（以较大者为准）。

编译器使用以下结构对齐规则：

- 除非使用 `__declspec(align(#))` 进行重写，否则标量结构成员的对齐方式为其大小和当前包装的最小值。

- 除非使用 `__declspec(align(#))` 进行重写，否则结构的对齐方式是其成员单个对齐方式的最大值。

- 结构成员被放置在其父结构起始处的偏移位置，这是其对齐大于或等于前一个成员末尾的偏移量的最小倍数。

- 结构的大小是大于或等于其最后一个成员末尾的偏移量的对齐的最小倍数。

`__declspec(align(#))` 只能增大对齐限制。

有关详细信息，请参阅：

- [`align`示例](#vclrfalignexamples)

- [定义新类型`__declspec(align(#))`](#vclrf_declspecaligntypedef)

- [在线程本地存储区中对齐数据](#vclrfthreadlocalstorageallocation)

- [如何处理 `align` 数据打包](#vclrfhowalignworkswithdatapacking)

- [结构对齐示例](../build/x64-software-conventions.md#examples-of-structure-alignment)（特定于 x64）

## <a name="align-examples"></a><a name="vclrfalignexamples"></a>对齐示例

以下示例说明 `__declspec(align(#))` 如何影响数据结构的大小和对齐方式。 这些示例假定下列定义：

```cpp
#define CACHE_LINE  32
#define CACHE_ALIGN __declspec(align(CACHE_LINE))
```

在此示例中，通过使用 `S1` 定义 `__declspec(align(32))` 结构。 针对一个变量定义或其他类型声明中的全部 `S1` 使用均为 32 字节对齐。 `sizeof(struct S1)` 返回 32，并且 `S1` 在包含四个整数所需的 16 字节之后有 16 个填充字节。 每个 **`int`** 成员需要4字节对齐，但结构本身的对齐方式声明为32。 则总体对齐方式为32。

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

在此示例中，注意 `a` 具有自然类型的对齐方式，在这种情况下为 4 字节。 但是，`S1` 必须是对齐的 32 字节。 填充的28字节跟随 `a` ，因此 `s1` 从偏移量32开始。 `S4`然后，将继承的对齐要求 `S1` ，因为这是结构中的最大对齐要求。 `sizeof(struct S4)` 返回 64。

```cpp
struct S4 {
   int a;
   // 28 bytes padding
   struct S1 s1;      // S4 inherits cache alignment requirement of S1
};
```

以下三个变量声明还使用 `__declspec(align(#))`。 在每种情况下，变量必须是对齐的 32 字节。 在数组中，数组的基址，而不是每个数组成员，均为32字节。 **`sizeof`** 使用时，每个数组成员的值不受影响 `__declspec(align(#))` 。

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

在堆上分配了内存时，对齐方式取决于所调用的分配函数。  例如，如果你使用 `malloc`，则该结果取决于操作数大小。 如果*arg* >= 8，则返回的内存为8字节对齐。 如果*arg* < 8，则返回的内存的对齐是2小于*arg*的第一个幂。 例如，如果使用，则 `malloc(7)` 对齐方式为4字节。

## <a name="defining-new-types-with-__declspecalign"></a><a name="vclrf_declspecaligntypedef"></a>定义新类型`__declspec(align(#))`

可以使用对齐特性定义类型。

例如，可以 **`struct`** 通过这种方式定义具有对齐值的：

```cpp
struct aType {int a; int b;};
typedef __declspec(align(32)) struct aType bType;
```

现在， `aType` 和 `bType` 的大小相同（8字节），但类型的变量的大小 `bType` 为32字节。

## <a name="aligning-data-in-thread-local-storage"></a><a name="vclrfthreadlocalstorageallocation"></a>在线程本地存储中对齐数据

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

## <a name="how-align-works-with-data-packing"></a><a name="vclrfhowalignworkswithdatapacking"></a>如何处理 `align` 数据打包

`/Zp`编译器选项和 `pack` 杂注具有结构和联合成员的封装数据的效果。 此示例演示如何 `/Zp` 和 `__declspec(align(#))` 一起工作：

```cpp
struct S {
   char a;
   short b;
   double c;
   CACHE_ALIGN double d;
   char e;
   double f;
};
```

下表列出了不同（或）值下每个成员的偏移量 `/Zp` `#pragma pack` ，其中显示了这两个交互的方式。

|变量|/Zp1|/Zp2|/Zp4|/Zp8|
|--------------|-----------|-----------|-----------|-----------|
|a|0|0|0|0|
|b|1|2|2|2|
|c|3|4|4|8|
|d|32|32|32|32|
|e|40|40|40|40|
|F|41|42|44|48|
|sizeof(S)|64|64|64|64|

有关详细信息，请参阅[ `/Zp` （结构成员对齐）](../build/reference/zp-struct-member-alignment.md)。

对象的偏移量基于上一个对象的偏移量和当前打包设置，除非该对象具有 `__declspec(align(#))` 特性，在此情况下，对齐将基于上一个对象的偏移量和该对象的 `__declspec(align(#))` 值。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[`__declspec`](../cpp/declspec.md)<br/>
[ARM ABI 约定概述](../build/overview-of-arm-abi-conventions.md)<br/>
[x64 软件约定](../build/x64-software-conventions.md)
