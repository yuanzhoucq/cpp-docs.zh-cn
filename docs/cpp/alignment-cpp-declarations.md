---
title: 对齐方式（C++ 声明）
description: 现代版中指定数据对齐的方式C++。
ms.date: 05/30/2019
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
ms.openlocfilehash: b6e03ac2b89624a0eb6602183d4ff4bf8b518f8d
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450768"
---
# <a name="alignment-c-declarations"></a>对齐方式（C++ 声明）

C + + 的低级功能之一是能够指定内存中对象的精确对齐方式，以最大限度利用特定的硬件体系结构。 默认情况下，编译器将根据其大小值类和结构成员对齐：`bool`并`char`1 字节边界上`short`2 字节边界上`int`， `long`，并`float`4 字节边界和`long long`， `double`，和`long double`8 字节边界上。 在大多数情况下，无需因为默认对齐方式已经是最佳面对对齐方式。 在某些情况下，但是，你可以获得显著的性能提升或节约内存，通过指定自定义数据结构的对齐。 在 Visual Studio 2015 之前，您可以使用 Microsoft 专用关键字`__alignof`和`declspec(alignas)`指定大于默认对齐方式。 从 Visual Studio 2015 开始，应使用 C++ 11 标准关键字[alignof 和 alignas](../cpp/alignof-and-alignas-cpp.md)获得最大代码可移植性。 新关键字实质上方式与 Microsoft 专用扩展相同的行为。 这些扩展的文档也适用于新的关键字。 有关详细信息，请参阅[__alignof 运算符](../cpp/alignof-operator.md)并[对齐](../cpp/align-cpp.md)。 C++标准不会指定为对齐的装箱行为在小于目标平台的编译器默认边界因此仍需要使用 Microsoft #pragma [pack](../preprocessor/pack.md)这种情况下。

使用[aligned_storage 类](../standard-library/aligned-storage-class.md)的自定义对齐方式的数据结构的内存分配。 [Aligned_union 类](../standard-library/aligned-union-class.md)用于与非普通构造函数或析构函数中指定的联合的对齐方式。

## <a name="about-alignment"></a>关于对齐方式

对齐方式是内存地址的一个属性，表示为数字地址对 2 的幂次方取模。 例如，地址 0x0001103F 对 4 取模为 3。 该地址被认为将对齐到 4n + 3，其中 4 表示所选的 2 次幂。 一个地址的对齐方式取决于所选的 2 次幂。 相同的地址对 8 取模为 7。 如果一个地址的对齐方式是 Xn+0，它将对齐到 X。

Cpu 在内存中存储的数据执行操作的说明。 其地址在内存中的标识数据。 单个基准也具有大小。 我们调用一个基准*自然对齐*如果其地址对齐到其大小。 它称为*未对齐*否则为。 例如，如果使用来标识该地址中有 8 字节对齐方式自然对齐 8 字节浮点基准。

## <a name="compiler-handling-of-data-alignment"></a>编译器处理的数据对齐

编译器将尝试阻止数据未对齐的方式使数据分配。

对于简单的数据类型，编译器将分配是数据类型的大小（以字节为单位）的倍数的地址。 例如，编译器将地址分配给类型的变量`long`是 4，底部的地址的 2 位设置为零的倍数。

编译器还填充结构自然对齐结构的每个元素的方式。 请考虑结构`struct x_`在下面的代码示例：

```cpp
struct x_
{
   char a;     // 1 byte
   int b;      // 4 bytes
   short c;    // 2 bytes
   char d;     // 1 byte
} MyStruct;
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
}
```

1. 这两个声明返回`sizeof(struct x_)`作为 12 个字节。

1. 第二个声明包括两个填充元素：

1. `char _pad0[3]` 若要对齐`int b`4 字节边界上的成员

1. `char _pad1[1]` 若要对齐数组元素的结构 `struct _x bar[3];`

1. 填充对齐的元素`bar[3]`中允许自然访问的方式。

下面的代码示例演示`bar[3]`数组布局：

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

## <a name="see-also"></a>请参阅

[数据结构对齐方式](https://en.wikipedia.org/wiki/Data_structure_alignment)
