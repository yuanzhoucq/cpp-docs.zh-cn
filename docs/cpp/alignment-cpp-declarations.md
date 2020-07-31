---
title: 对齐方式
description: 如何在新式 c + + 中指定数据对齐方式。
ms.date: 12/11/2019
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
ms.openlocfilehash: 7f6bef061fee41389bad644d9ac5244f5644da76
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227642"
---
# <a name="alignment"></a>对齐方式

C + + 的低级功能之一是能够指定内存中对象的精确对齐方式，以最大限度利用特定的硬件体系结构。 默认情况下，编译器会按大小值对类和结构成员进行对齐：在1个字节的边界上、在2字节边界上、 **`bool`** **`char`** **`short`** **`int`** 、和 **`long`** 4 字节 **`float`** **`long long`** **`double`** 边界上、、以及 **`long double`** 8 字节边界上。

在大多数情况下，你永远不需要关心对齐方式，因为默认对齐已经是最佳的。 但是，在某些情况下，您可以通过为数据结构指定自定义对齐方式来实现显著的性能改进或节省内存。 在 Visual Studio 2015 之前，可以使用 Microsoft 特定的关键字 **`__alignof`** 并 **`__declspec(align)`** 指定大于默认值的对齐方式。 从 Visual Studio 2015 开始，应使用 c + + 11 标准关键字 **`alignof`** ，并 **`alignas`** 获得最大的代码可移植性。 新关键字的行为方式与 Microsoft 特定的扩展相同。 这些扩展插件的文档也适用于新关键字。 有关详细信息，请参阅[ `alignof` 运算符](../cpp/alignof-operator.md)和[对齐](../cpp/align-cpp.md)。 C + + 标准不指定封装行为，以便在小于目标平台的编译器默认值的边界上对齐，因此 [`#pragma pack`](../preprocessor/pack.md) 在这种情况下仍需要使用 Microsoft。

使用[aligned_storage 类](../standard-library/aligned-storage-class.md)通过自定义对齐方式为数据结构分配内存。 [Aligned_union 类](../standard-library/aligned-union-class.md)用于为具有不常用构造函数或析构函数的联合指定对齐方式。

## <a name="alignment-and-memory-addresses"></a>对齐和内存地址

对齐方式是内存地址的一个属性，表示为数字地址对 2 的幂次方取模。 例如，地址0x0001103F 模数4为3。 该地址被视为与 drj-4n-yzg + 3 对齐，其中4表示所选的2的幂。 地址的对齐方式取决于所选的2的幂。 相同的地址对 8 取模为 7。 如果一个地址的对齐方式是 Xn+0，它将对齐到 X。

Cpu 执行对存储在内存中的数据执行的指令。 数据由其在内存中的地址标识。 单个基准还具有大小。 如果某个基准的地址与其大小一致，我们会将该基准*自然对齐*。 否则，将其称为未*对齐*。 例如，如果用于标识它的地址有8个字节的对齐方式，则8字节浮点基准自然对齐。

## <a name="compiler-handling-of-data-alignment"></a>数据对齐的编译器处理

编译器会尝试使用阻止数据不一致的方式来进行数据分配。

对于简单的数据类型，编译器将分配是数据类型的大小（以字节为单位）的倍数的地址。 例如，编译器会将地址分配给类型为4的倍数的变量 **`long`** ，将地址的下2位设置为零。

编译器还以自然对齐结构的每个元素的方式来填充结构。 请考虑 `struct x_` 以下代码示例中的结构：

```cpp
struct x_
{
   char a;     // 1 byte
   int b;      // 4 bytes
   short c;    // 2 bytes
   char d;     // 1 byte
} bar[3];
```

编译器填充此结构以自然强制实施对齐方式。

下面的代码示例演示编译器如何将填充的结构放置在内存中：

```cpp
// Shows the actual memory layout
struct x_
{
   char a;            // 1 byte
   char _pad0[3];     // padding to put 'b' on 4-byte boundary
   int b;            // 4 bytes
   short c;          // 2 bytes
   char d;           // 1 byte
   char _pad1[1];    // padding to make sizeof(x_) multiple of 4
} bar[3];
```

两个声明都返回 `sizeof(struct x_)` 为12个字节。

第二个声明包括两个填充元素：

1. `char _pad0[3]`用于使 `int b` 成员在4字节边界上对齐。

1. `char _pad1[1]`将结构的数组元素与 `struct _x bar[3];` 四个字节的边界对齐。

填充 `bar[3]` 以允许自然访问的方式对齐的元素。

下面的代码示例显示 `bar[3]` 数组布局：

```Output
adr offset   element
------   -------
0x0000   char a;         // bar[0]
0x0001   char pad0[3];
0x0004   int b;
0x0008   short c;
0x000a   char d;
0x000b   char _pad1[1];

0x000c   char a;         // bar[1]
0x000d   char _pad0[3];
0x0010   int b;
0x0014   short c;
0x0016   char d;
0x0017   char _pad1[1];

0x0018   char a;         // bar[2]
0x0019   char _pad0[3];
0x001c   int b;
0x0020   short c;
0x0022   char d;
0x0023   char _pad1[1];
```

## <a name="alignof-and-alignas"></a>`alignof` 和 `alignas`

**`alignas`** 类型说明符是一种可移植的 c + + 标准方法，用于指定变量和用户定义类型的自定义对齐方式。 **`alignof`** 运算符也是一种标准的可移植方法，用于获取指定类型或变量的对齐方式。

## <a name="example"></a>示例

可以 **`alignas`** 在类、结构或联合中使用，也可以在单个成员上使用。 如果遇到多个 **`alignas`** 说明符，编译器将选择最严格的说明符（值最大的一个）。

```cpp
// alignas_alignof.cpp
// compile with: cl /EHsc alignas_alignof.cpp
#include <iostream>

struct alignas(16) Bar
{
    int i;       // 4 bytes
    int n;      // 4 bytes
    alignas(4) char arr[3];
    short s;          // 2 bytes
};

int main()
{
    std::cout << alignof(Bar) << std::endl; // output: 16
}
```

## <a name="see-also"></a>另请参阅

[数据结构对齐](https://en.wikipedia.org/wiki/Data_structure_alignment)
