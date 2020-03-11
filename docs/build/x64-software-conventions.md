---
title: x64 软件约定
ms.date: 12/17/2018
helpviewer_keywords:
- x64 coding conventions
- Visual C++, x64 calling conventions
ms.assetid: 750f3d97-1706-4840-b2fc-41a007329a08
ms.openlocfilehash: 11d29b6c31ccecfe5b9c51c2f9311213bd4a6732
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865595"
---
# <a name="x64-software-conventions"></a>x64 软件约定

本部分介绍 x64 C++的调用约定方法，x86 体系结构的64位扩展。

## <a name="overview-of-x64-calling-conventions"></a>X64 调用约定概述

X86 和 x64 之间有两个重要的区别：64位寻址功能，以及一组用于常规使用的一组固定的 16 64 位寄存器。 给定扩展的寄存器集，x64 使用[__fastcall](../cpp/fastcall.md)调用约定和基于 RISC 的异常处理模型。 `__fastcall` 约定使用第四个参数的寄存器和堆栈帧传递其他参数。 有关 x64 调用约定的详细信息，包括寄存器用法、堆栈参数、返回值和堆栈展开，请参阅[x64 调用约定](x64-calling-convention.md)。

## <a name="enable-optimization-for-x64"></a>启用 x64 优化

以下编译器选项有助于优化 x64 应用程序：

- [/favor（优化体系结构详细信息）](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="types-and-storage"></a>类型和存储

本部分介绍 x64 体系结构的数据类型的枚举和存储。

### <a name="scalar-types"></a>标量类型

尽管可以使用任何对齐方式访问数据，但建议将数据置于其自然边界或一些倍数上，以避免性能损失。 枚举是常量整数，被视为32位整数。 下表描述了数据的类型定义和推荐的存储，这些数据与使用以下对齐值进行对齐的情况有关：

- 字节-8 位

- Word-16 位

- 双字-32 位

- 四字-64 位

- Octaword-128 位

|||||
|-|-|-|-|
|标量类型|C 数据类型|存储大小（以字节为单位）|建议的对齐方式|
|**INT8**|**char**|1|Byte|
|**UINT8**|**unsigned char**|1|Byte|
|**INT16**|**short**|2|Word|
|**UINT16**|**unsigned short**|2|Word|
|**INT32**|**int**、 **long**|4|字|
|**UINT32**|**无符号整数，无符号长**|4|字|
|**INT64**|**__int64**|8|四|
|**UINT64**|unsigned __int64|8|四|
|**FP32 （单精度）**|**float**|4|字|
|**FP64 （双精度）**|**double**|8|四|
|**变为**|__\*__|8|四|
|**__m64**|**结构 __m64**|8|四|
|**__m128**|**结构 __m128**|16|Octaword|

### <a name="aggregates-and-unions"></a>聚合和联合

其他类型（如数组、结构和联合）具有更严格的对齐要求，这些要求可确保一致的聚合和联合存储和数据检索。 下面是数组、结构和联合的定义：

- Array

   包含相邻数据对象的有序组。 每个对象称为一个*元素*。 数组中的所有元素都具有相同的大小和数据类型。

- 结构

   包含一组有序的数据对象。 与数组的元素不同，结构中的数据对象可以具有不同的数据类型和大小。 结构中的每个数据对象称为*成员*。

- Union

   一个对象，该对象包含一组已命名成员中的任何一个。 命名集的成员可以是任何类型。 为联合分配的存储等于该联合的最大成员所需的存储，以及对齐所需的任何填充。

下表显示了联合和结构的标量成员的强建议对齐方式。

||||
|-|-|-|
|标量类型|C 数据类型|所需对齐|
|**INT8**|**char**|Byte|
|**UINT8**|**unsigned char**|Byte|
|**INT16**|**short**|Word|
|**UINT16**|**unsigned short**|Word|
|**INT32**|**int**、 **long**|字|
|**UINT32**|**无符号整数，无符号长**|字|
|**INT64**|**__int64**|四|
|**UINT64**|unsigned __int64|四|
|**FP32 （单精度）**|**float**|字|
|**FP64 （双精度）**|**double**|四|
|**变为**|<strong>\*</strong>|四|
|**__m64**|**结构 __m64**|四|
|**__m128**|**结构 __m128**|Octaword|

以下聚合对齐规则适用：

- 数组的对齐方式与数组中某个元素的对齐方式相同。

- 结构或联合的开头对齐是任何单个成员的最大对齐方式。 结构或联合中的每个成员都必须按照上表中定义的正确对齐方式放置，这可能需要隐式内部填充（具体取决于以前的成员）。

- 结构大小必须是其对齐的整数倍，这可能需要最后一个成员后的填充。 由于可以将结构和联合分组到数组中，因此结构或联合的每个数组元素必须以之前确定的正确对齐方式开始和结束。

- 只要保留了前面的规则，就可以使数据的对齐方式大于对齐要求。

- 由于大小原因，单个编译器可能会调整结构的封装。 例如， [/Zp （结构成员对齐）](../build/reference/zp-struct-member-alignment.md)允许调整结构的封装。

### <a name="examples-of-structure-alignment"></a>结构对齐示例

以下四个示例分别声明对齐的结构或联合，相应的图说明了内存中该结构或联合的布局。 图中的每一列都表示一个内存字节，列中的数字指示该字节的位移。 每个图形的第二行中的名称对应于声明中的变量名称。 带阴影的列指示实现指定的对齐所需的填充。

#### <a name="example-1"></a>示例 1

```C
// Total size = 2 bytes, alignment = 2 bytes (word).

_declspec(align(2)) struct {
    short a;      // +0; size = 2 bytes
}
```

![AMD 转换示例1结构布局](../build/media/vcamd_conv_ex_1_block.png "AMD 转换示例1结构布局")

#### <a name="example-2"></a>示例 2

```C
// Total size = 24 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) struct {
    int a;       // +0; size = 4 bytes
    double b;    // +8; size = 8 bytes
    short c;     // +16; size = 2 bytes
}
```

![AMD 转换示例2结构布局](../build/media/vcamd_conv_ex_2_block.png "AMD 转换示例2结构布局")

#### <a name="example-3"></a>示例 3

```C
// Total size = 12 bytes, alignment = 4 bytes (doubleword).

_declspec(align(4)) struct {
    char a;       // +0; size = 1 byte
    short b;      // +2; size = 2 bytes
    char c;       // +4; size = 1 byte
    int d;        // +8; size = 4 bytes
}
```

![AMD 转换示例2结构布局](../build/media/vcamd_conv_ex_3_block.png "AMD 转换示例2结构布局")

#### <a name="example-4"></a>示例 4

```C
// Total size = 8 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) union {
    char *p;      // +0; size = 8 bytes
    short s;      // +0; size = 2 bytes
    long l;       // +0; size = 4 bytes
}
```

![AMD 转换示例4联合 layouit](../build/media/vcamd_conv_ex_4_block.png "AMD 转换示例4联合 layouit")

### <a name="bitfields"></a>位域

结构位域限制为64位，可以为有符号的 int、无符号整数、int64 或无符号 int64 类型。 跨类型边界的位域会跳过位，以将位域与下一类型对齐进行对齐。 例如，整数位域不能跨32位 boundry。

### <a name="conflicts-with-the-x86-compiler"></a>与 x86 编译器冲突

当使用 x86 编译器编译应用程序时，大于4个字节的数据类型不会在堆栈上自动对齐。 由于 x86 编译器的体系结构是4字节对齐的堆栈，大于4个字节的任何内容（例如，64位整数）都无法自动对齐到8字节地址。

使用未对齐的数据有两个含义。

- 访问未对齐的位置可能需要更长的时间，而不是访问对齐位置所需的时间。

- 联锁操作中不能使用未对齐的位置。

如果需要更严格的对齐方式，请对变量声明使用 `__declspec(align(N))`。 这将导致编译器根据你的规范动态地对齐堆栈。 但是，在运行时动态调整堆栈可能会导致应用程序的执行速度变慢。

## <a name="register-usage"></a>注册使用情况

X64 体系结构提供了16个通用寄存器（以后称为整数寄存器）以及16个可用于浮点使用的 XMM/YMM 寄存器。 易失寄存器是由调用方假想的临时寄存器，并要在调用过程中销毁。 非易失寄存器需要在整个函数调用过程中保留其值，并且一旦使用，则必须由被调用方保存。

### <a name="register-volatility-and-preservation"></a>注册波动性和保留

下表说明了每种寄存器在整个函数调用过程中的使用方法：

||||
|-|-|-|
|注册|状态|用途|
|RAX|易失的|返回值寄存器|
|RCX|易失的|第一个整型自变量|
|RDX|易失的|第二个整型自变量|
|R8|易失的|第三个整型自变量|
|R9|易失的|第四个整型自变量|
|R10:R11|易失的|必须根据需要由调用方保留；在 syscall/sysret 指令中使用|
|R12:R15|非易失的|必须由被调用方保留|
|RDI|非易失的|必须由被调用方保留|
|RSI|非易失的|必须由被调用方保留|
|RBX|非易失的|必须由被调用方保留|
|RBP|非易失的|可用作帧指针；必须由被调用方保留|
|RSP|非易失的|堆栈指针|
|XMM0、YMM0|易失的|第一个 FP 参数；使用 `__vectorcall` 时的第一个矢量类型参数|
|XMM1、YMM1|易失的|第二个 FP 参数；使用 `__vectorcall` 时的第二个矢量类型参数|
|XMM2、YMM2|易失的|第三个 FP 参数；使用 `__vectorcall` 时的第三个矢量类型参数|
|XMM3、YMM3|易失的|第四个 FP 自变量；使用 `__vectorcall` 时的第四个矢量类型参数|
|XMM4、YMM4|易失的|必须根据需要由调用方保留；使用 `__vectorcall` 时的第五个矢量类型参数|
|XMM5、YMM5|易失的|必须根据需要由调用方保留；使用 `__vectorcall` 时的第六个矢量类型参数|
|XMM6:XMM15、YMM6:YMM15|非易失的 (XMM)，易失的（YMM 的上半部分）|必须由被调用方保留。 YMM 寄存器必须根据需要由调用方保留。|

在函数 exit 和 on 函数进入 C 运行库调用和 Windows 系统调用时，应清除 CPU 标志寄存器中的方向标志。

## <a name="stack-usage"></a>堆栈使用情况

有关 x64 上的堆栈分配、对齐方式、函数类型和堆栈帧的详细信息，请参阅[x64 stack 使用](stack-usage.md)。

## <a name="prolog-and-epilog"></a>Prolog 和 epilog

分配堆栈空间、调用其他函数、保存非易失寄存器或使用异常处理的每个函数都必须具有一个 prolog，其地址限制在与相应函数表条目关联的展开数据中进行描述，epilogs 位于每个出口到一个函数。 有关 x64 上所需的 prolog 和 epilog 代码的详细信息，请参阅[x64 prolog 和 epilog](prolog-and-epilog.md)。

## <a name="x64-exception-handling"></a>x64 异常处理

有关用于实现结构化异常处理的约定和数据结构以及C++ x64 上的异常处理行为的信息，请参阅[x64 异常处理](exception-handling-x64.md)。

## <a name="intrinsics-and-inline-assembly"></a>内部函数和内联程序集

X64 编译器的一个约束是没有内联汇编程序支持。 这意味着不能用 C 编写的函数或C++必须将其编写为子例程或编译器支持的内部函数。 某些函数会对性能敏感，而其他功能则是不敏感的。 应将性能敏感的函数作为内部函数实现。

编译器支持的内部函数在[编译器内部函数](../intrinsics/compiler-intrinsics.md)中介绍。

## <a name="image-format"></a>图像格式

X64 可执行图像的格式为 PE32 +。 可执行映像（Dll 和 Exe）限制为最大大小 2 gb，因此，可以使用32位置换的相对寻址来寻址静态图像数据。 此数据包含导入地址表、字符串常量、静态全局数据等。

## <a name="see-also"></a>另请参阅

[调用约定](../cpp/calling-conventions.md)
