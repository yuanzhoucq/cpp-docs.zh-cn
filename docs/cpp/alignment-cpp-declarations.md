---
title: 对齐方式（C++ 声明）
description: 如何在新式C++中指定数据对齐方式。
ms.date: 09/19/2019
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
ms.openlocfilehash: 67debc00343b8bee4184e020c9269011e2fcebc9
ms.sourcegitcommit: f907b15f50a6b945d0b87c03af0050946157d701
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2019
ms.locfileid: "71158751"
---
# <a name="alignment-c-declarations"></a>对齐方式（C++ 声明）

C + + 的低级功能之一是能够指定内存中对象的精确对齐方式，以最大限度利用特定的硬件体系结构。 默认情况下，编译器会按大小值对类和结构成员进行`bool`对齐`char` ：在1个字节的`short`边界上，在2字节`int`边界`long`、、 `float`和 4个字节的边界上对齐和`long long`、和在`long double` 8 字节边界上。 `double` 在大多数情况下，你永远不需要关心对齐方式，因为默认对齐已经是最佳的。 但是，在某些情况下，您可以通过为数据结构指定自定义对齐方式来实现显著的性能改进或节省内存。 在 Visual Studio 2015 之前，可以使用 Microsoft 特定的关键字`__alignof`并`declspec(alignas)`指定大于默认值的对齐方式。 从 Visual Studio 2015 开始，应使用 C++ 11 标准关键字[alignof 和 alignas](../cpp/alignof-and-alignas-cpp.md)获得最大代码可移植性。 新关键字的行为方式与 Microsoft 特定的扩展相同。 这些扩展插件的文档也适用于新关键字。 有关详细信息，请参阅[__Alignof 运算符](../cpp/alignof-operator.md)和[align](../cpp/align-cpp.md)。 C++标准不指定在边界比目标平台的编译器默认值小的边界上对齐的封装行为，因此在这种情况下仍需要使用 Microsoft #pragma [pack](../preprocessor/pack.md) 。

使用[aligned_storage 类](../standard-library/aligned-storage-class.md)通过自定义对齐方式为数据结构分配内存。 [Aligned_union 类](../standard-library/aligned-union-class.md)用于为具有不常用构造函数或析构函数的联合指定对齐方式。

## <a name="about-alignment"></a>关于对齐方式

对齐方式是内存地址的一个属性，表示为数字地址对 2 的幂次方取模。 例如，地址0x0001103F 模数4为3。 该地址被视为与 drj-4n-yzg + 3 对齐，其中4表示所选的2的幂。 地址的对齐方式取决于所选的2的幂。 相同的地址对 8 取模为 7。 如果一个地址的对齐方式是 Xn+0，它将对齐到 X。

Cpu 执行对存储在内存中的数据执行的指令。 数据由其在内存中的地址标识。 单个基准还具有大小。 如果某个基准的地址与其大小一致，我们会将该基准*自然对齐*。 否则，将其称为未*对齐*。 例如，如果用于标识它的地址有8个字节的对齐方式，则8字节浮点基准自然对齐。

## <a name="compiler-handling-of-data-alignment"></a>数据对齐的编译器处理

编译器会尝试使用阻止数据不一致的方式来进行数据分配。

对于简单的数据类型，编译器将分配是数据类型的大小（以字节为单位）的倍数的地址。 例如，编译器会将地址分配给类型`long`为4的倍数的变量，将地址的下2位设置为零。

编译器还以自然对齐结构的每个元素的方式来填充结构。 请考虑以下`struct x_`代码示例中的结构：

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

两个声明`sizeof(struct x_)`都返回为12个字节。

第二个声明包括两个填充元素：

1. `char _pad0[3]`用于使`int b`成员在4字节边界上对齐。

1. `char _pad1[1]`将结构`struct _x bar[3];`的数组元素与四个字节的边界对齐。

填充`bar[3]`以允许自然访问的方式对齐的元素。

下面的代码示例显示`bar[3]`数组布局：

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

[数据结构对齐](https://en.wikipedia.org/wiki/Data_structure_alignment)
