---
title: x64 软件约定
ms.date: 12/17/2018
helpviewer_keywords:
- x64 coding conventions
- Visual C++, x64 calling conventions
ms.assetid: 750f3d97-1706-4840-b2fc-41a007329a08
ms.openlocfilehash: 55be8f381b39ee566b389350ff70a9b0a3fe7694
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702063"
---
# <a name="x64-software-conventions"></a>x64 软件约定

本部分介绍了 c + + 调用约定方法对于 x64，x86 的 64 位扩展体系结构。

## <a name="overview-of-x64-calling-conventions"></a>X64 调用约定的概述

X86 和 x64 的两个重要区别是 64 位寻址功能和一组展开为 16 个 64 位寄存器供常规使用。 提供扩展的注册组，使用 x64 [__fastcall](../cpp/fastcall.md)调用约定和一个基于 RISC 的异常处理模型。 `__fastcall`约定使用前四个参数和堆栈帧的寄存器传递其他参数。 对于 x64 调用约定，包括注册使用情况的详细信息堆栈参数，则返回值和堆栈展开，请参阅[x64 调用约定](x64-calling-convention.md)。

## <a name="enable-optimization-for-x64"></a>启用适用于 x64 的优化

以下编译器选项可帮助您优化用于 x64 应用程序：

- [/favor（优化体系结构详细信息）](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="types-and-storage"></a>类型和存储

本部分介绍枚举和 x64 的数据类型的存储体系结构。

### <a name="scalar-types"></a>标量类型

虽然可以访问数据的任何的对齐方式，但建议对齐上其自然边界或多，以避免性能丢失的数据。 枚举是常量整数，而是被视为 32 位整数。 下表描述的类型定义和建议的数据的存储，因为这与使用以下的对齐值的对齐方式：

- 8 位字节

- Word 的 16 位

- 双字的 32 位

- 四字的 64 位

- Octaword-128 位

|||||
|-|-|-|-|
|标量类型|C 数据类型|存储大小 （以字节为单位）|建议的对齐方式|
|**INT8**|**char**|1|Byte|
|**UINT8**|**unsigned char**|1|Byte|
|**INT16**|**short**|2|字|
|**UINT16**|**unsigned short**|2|字|
|**INT32**|**int**，**长**|4|双字|
|**UINT32**|**无符号的整型、 无符号长**|4|双字|
|**INT64**|**__int64**|8|四字|
|**UINT64**|unsigned __int64|8|四字|
|**FP32 （单精度）**|**float**|4|双字|
|**FP64 （双精度）**|**double**|8|四字|
|**指针**|__\*__|8|四字|
|**__m64**|**结构 __m64**|8|四字|
|**__m128**|**结构 __m128**|16|Octaword|

### <a name="aggregates-and-unions"></a>聚合和联合

其他类型，如数组、 结构和联合，具有更严格对齐要求，以确保一致聚合和联合存储和数据检索。 下面是数组、 结构和联合的定义：

- 数组

   包含相邻的数据对象的有序的组。 每个对象调用*元素*。 一个数组中的所有元素都具有相同的大小和数据类型。

- 结构

   包含数据对象的有序的组。 与数组的元素，在结构中的数据对象可以具有不同的数据类型和大小。 在结构中的每个数据对象称为*成员*。

- 联合

   保存一组命名的成员之一的对象。 命名集的成员可以是任何类型。 分配为联合的存储等于该联合，加上任何填充所需的对齐方式的最大成员所需的存储。

下表显示了标量联合和结构的成员的强烈建议对齐方式。

||||
|-|-|-|
|标量类型|C 数据类型|所需的对齐方式|
|**INT8**|**char**|Byte|
|**UINT8**|**unsigned char**|Byte|
|**INT16**|**short**|字|
|**UINT16**|**unsigned short**|字|
|**INT32**|**int**，**长**|双字|
|**UINT32**|**无符号的整型、 无符号长**|双字|
|**INT64**|**__int64**|四字|
|**UINT64**|unsigned __int64|四字|
|**FP32 （单精度）**|**float**|双字|
|**FP64 （双精度）**|**double**|四字|
|**指针**|<strong>\*</strong>|四字|
|**__m64**|**结构 __m64**|四字|
|**__m128**|**结构 __m128**|Octaword|

以下聚合对齐规则适用：

- 数组的对齐方式是一个数组的元素的对齐方式相同。

- 开始处的结构或联合的对齐方式为任何单个成员的最大对齐方式。 结构或联合中的每个成员必须位于其正确对齐上, 表中，这可能需要隐式内部的填充量，具体取决于上一个成员中定义。

- 结构大小必须为其对齐方式，可能需要填充的最后一个成员后的整数倍。 由于结构和联合可以分组在数组中，结构或联合的每个数组元素必须开始和结束处先前确定的适当对齐方式。

- 就可以保持一致的方式将其大于对齐要求，只要将保留以前的规则中的数据。

- 单个编译器可能会调整大小的原因的结构的包装。 例如[/Zp （结构成员对齐）](../build/reference/zp-struct-member-alignment.md)允许进行调整的结构的包装。

### <a name="examples-of-structure-alignment"></a>结构对齐示例

以下四个示例每个声明对齐的结构或联合和相应的图形说明了该结构或联合在内存中的布局。 在图中每一列代表一字节的内存，并在列中的数字表示的字节偏移量。 第二行的每个图形中的名称对应于在声明变量的名称。 阴影的列指示填充的所需实现指定的对齐方式。

#### <a name="example-1"></a>示例 1

```C
// Total size = 2 bytes, alignment = 2 bytes (word).

_declspec(align(2)) struct {
    short a;      // +0; size = 2 bytes
}
```

![AMD 转换示例 1 结构布局](../build/media/vcamd_conv_ex_1_block.png "AMD 转换示例 1 结构布局")

#### <a name="example-2"></a>示例 2

```C
// Total size = 24 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) struct {
    int a;       // +0; size = 4 bytes
    double b;    // +8; size = 8 bytes
    short c;     // +16; size = 2 bytes
}
```

![AMD 转换示例 2 结构布局](../build/media/vcamd_conv_ex_2_block.png "AMD 转换示例 2 结构布局")

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

![AMD 转换示例 2 结构布局](../build/media/vcamd_conv_ex_3_block.png "AMD 转换示例 2 结构布局")

#### <a name="example-4"></a>示例 4

```C
// Total size = 8 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) union {
    char *p;      // +0; size = 8 bytes
    short s;      // +0; size = 2 bytes
    long l;       // +0; size = 4 bytes
}
```

![AMD 转换示例 4 联合 layouit](../build/media/vcamd_conv_ex_4_block.png "AMD 转换示例 4 联合 layouit")

### <a name="bitfields"></a>位域

结构位域被限制为 64 位和可以为类型 int、 unsigned 的 int、 int64、 或 unsigned 的 int64 的签名。 交叉类型边界的位域将跳过位，以使位域到下一步类型对齐方式。 例如，整数位域可能不会跨 32 位边界。

### <a name="conflicts-with-the-x86-compiler"></a>冲突与 x86 编译器

数据类型包含大于 4 个字节都不会自动对齐在堆栈上时使用 x86 编译器来编译应用程序。 因为编译器是 4 字节对齐的堆栈，任何大于 4 个字节，例如，64 位整数，不能自动对齐到 8 字节地址 x86 体系结构。

处理未对齐的数据有两个含义。

- 可能需要更长时间才能访问未对齐的位置不是所需访问对齐的位置。

- 未对齐的位置不能使用互锁操作中。

如果需要更为严格的对齐，请使用`__declspec(align(N))`变量声明。 这将导致编译器动态对齐的堆栈，以满足您的规范。 但是，在运行时动态调整堆栈可能会导致应用程序的执行速度变慢。

## <a name="register-usage"></a>注册使用情况

X64 体系结构可提供 16 个通用寄存器 （以后称为整数寄存器），以及 16 XMM/YMM 寄存器可供浮点使用。 易失寄存器是由调用方假想的临时寄存器，并要在调用过程中销毁。 非易失寄存器需要在整个函数调用过程中保留其值，并且一旦使用，则必须由被调用方保存。

### <a name="register-volatility-and-preservation"></a>注册更新率和保留

下表说明了每种寄存器在整个函数调用过程中的使用方法：

||||
|-|-|-|
|寄存器|状态|使用|
|RAX|易失的|返回值寄存器|
|RCX|易失的|第一个整型参数|
|RDX|易失的|第二个整型参数|
|R8|易失的|第三个整型参数|
|R9|易失的|第四个整型参数|
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
|XMM3、YMM3|易失的|第四个 FP 参数；使用 `__vectorcall` 时的第四个矢量类型参数|
|XMM4、YMM4|易失的|必须根据需要由调用方保留；使用 `__vectorcall` 时的第五个矢量类型参数|
|XMM5、YMM5|易失的|必须根据需要由调用方保留；使用 `__vectorcall` 时的第六个矢量类型参数|
|XMM6:XMM15、YMM6:YMM15|非易失的 (XMM)，易失的（YMM 的上半部分）|必须由被调用方保留。 YMM 寄存器必须根据需要由调用方保留。|

在函数退出和函数进入到 C 运行库调用和 Windows 的系统调用、 CPU 中的方向标志标志注册应清除。

## <a name="stack-usage"></a>堆栈使用

堆栈分配、 对齐方式、 函数类型和在 x64 上的堆栈帧的详细信息，请参阅[x64 堆栈使用情况](stack-usage.md)。

## <a name="prolog-and-epilog"></a>Prolog 和 epilog

分配堆栈空间、 调用其他函数中，将非易失寄存器保存或使用异常处理的每个函数必须具有的 prolog 展开数据与关联的相应函数表条目中，以及在 epilog 中所述的地址限制每个退出函数。 详细信息所需的 prolog 和 epilog 代码在 x64 上的，请参阅[x64 prolog 和 epilog](prolog-and-epilog.md)。

## <a name="x64-exception-handling"></a>x64 异常处理

有关约定和用来实现结构化的异常处理和 c + + 异常处理行为在 x64 上的数据结构的信息，请参阅[x64 异常处理](exception-handling-x64.md)。

## <a name="intrinsics-and-inline-assembly"></a>内部函数和内联程序集

一个编译器不是内联汇编程序支持 x64 的约束。 函数，这意味着不能编写 C 或 c + + 将必须编写为子例程或编译器支持的内部函数。 某些功能是敏感的性能，而有些则不然。 性能敏感的函数应作为内部函数实现。

编译器支持的内部函数中所述[编译器内部函数](../intrinsics/compiler-intrinsics.md)。

## <a name="image-format"></a>图像格式

X64 可执行映像格式是 PE32 +。 可执行映像 （Dll 和 Exe） 是 2 千兆字节的最大大小限制为的因此使用 32 位偏移量相对地址可用于处理静态图像数据。 此数据包括导入地址表、 字符串常量，静态全局数据等。

## <a name="see-also"></a>请参阅

[调用约定](../cpp/calling-conventions.md)