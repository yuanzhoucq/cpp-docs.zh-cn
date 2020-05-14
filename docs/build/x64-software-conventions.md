---
title: x64 软件约定
ms.date: 12/17/2018
helpviewer_keywords:
- x64 coding conventions
- Visual C++, x64 calling conventions
ms.assetid: 750f3d97-1706-4840-b2fc-41a007329a08
ms.openlocfilehash: 11d29b6c31ccecfe5b9c51c2f9311213bd4a6732
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422720"
---
# <a name="x64-software-conventions"></a>x64 软件约定

本部分介绍 x64（x86 体系结构的 64 位扩展）的 C++ 调用约定方法。

## <a name="overview-of-x64-calling-conventions"></a>x64 调用约定概述

x86 和 x64 之间的两个重要区别是 64 位寻址功能和一组用于常规用途的平面 16 64 位寄存器。 给定扩展的寄存器组 x64 使用 [__fastcall ](../cpp/fastcall.md) 调用约定和基于 RISC 的异常处理模型。 `__fastcall` 约定使用前四个参数的寄存器和堆栈帧来传递其他参数。 有关 x64 调用约定的详细信息，包括寄存器使用情况、堆栈参数、返回值和堆栈展开，请参阅 [x64 调用约定](x64-calling-convention.md)。

## <a name="enable-optimization-for-x64"></a>对 x64 启动优化

以下编译器选项有助于优化 x64 应用程序：

- [/favor（优化体系结构详细信息）](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="types-and-storage"></a>类型和存储

本部分介绍 x64 体系结构的数据类型的枚举和存储。

### <a name="scalar-types"></a>标量类型

尽管可以以任何对齐方式访问数据，但建议在其自然边界或某些倍数上对齐数据，以避免性能损失。 枚举是常量整数，并视为 32 位整数。 下表描述了类型定义和建议的数据存储，因为它与使用以下对齐值的对齐有关：

- 字节 - 8 位

- 字 - 16 位

- 双字 - 32 位

- 四字 - 64 位

- 八倍长字 - 128 位

|||||
|-|-|-|-|
|标量类型|C 数据类型|存储大小（以字节为单位）|建议的对齐方式|
|**INT8**|**char**|1|Byte|
|**UINT8**|**unsigned char**|1|Byte|
|**INT16**|**short**|2|字|
|**UINT16**|**unsigned short**|2|字|
|**INT32**|**int**, **long**|4|双字|
|**UINT32**|**unsigned int, unsigned long**|4|双字|
|**INT64**|**__int64**|8|四字|
|**UINT64**|unsigned __int64 |8|四字|
|**FP32（单精度）**|**float**|4|双字|
|**FP64（双精度）**|**double**|8|四字|
|**POINTER**|__\*__|8|四字|
|**__m64**|**struct __m64**|8|四字|
|**__m128**|**struct __m128**|16|八倍长字|

### <a name="aggregates-and-unions"></a>聚合和联合

其他类型（如 arrays、struct 和 union）具有更严格的对齐要求，可确保一致的聚合和联合存储和数据检索。 下面是数组、结构和联合的定义：

- 数组

   包含相邻数据对象的有序组。 每个对象称为一个“元素”  。 数组中的所有元素都具有相同的大小和数据类型。

- 结构

   包含数据对象的有序组。 与数组的元素不同，结构中的数据对象可以有不同的数据类型和大小。 结构中的每个数据对象称为“成员”  。

- 联合

   包含一组已命名成员的任一成员的对象。 已命名组成员可以是任何类型。 为联合分配的存储等于该联合的最大成员所需的存储，外加对齐所需的任何填充字节。

下表显示了对联合和结构的标量成员强烈建议的对齐方式。

||||
|-|-|-|
|标量类型|C 数据类型|所需的对齐方式|
|**INT8**|**char**|Byte|
|**UINT8**|**unsigned char**|Byte|
|**INT16**|**short**|字|
|**UINT16**|**unsigned short**|字|
|**INT32**|**int**, **long**|双字|
|**UINT32**|**unsigned int, unsigned long**|双字|
|**INT64**|**__int64**|四字|
|**UINT64**|unsigned __int64 |四字|
|**FP32（单精度）**|**float**|双字|
|**FP64（双精度）**|**double**|四字|
|**POINTER**|<strong>\*</strong>|四字|
|**__m64**|**struct __m64**|四字|
|**__m128**|**struct __m128**|八倍长字|

以下聚合对齐规则适用于：

- 数组的对齐方式与数组的一个元素的对齐方式相同。

- 结构或联合的开头对齐方式是任何单个成员的最大对齐方式。 结构或联合中的每个成员必须置于上表中定义的正确对齐方式，这可能需要隐式内部填充，具体取决于前一个成员。

- 结构大小必须是其对齐的整数倍，这可能需要在最后一个成员之后填充字节。 由于结构和联合可以分组在数组中，因此结构或联合的每个数组元素都必须在先前确定的正确对齐方式下开始和结束。

- 只要保留以前的规则，就可以以大于对齐要求的方式对齐数据。

- 单个编译器可能会出于大小原因调整结构的包装。 例如 [/Zp（结构成员对齐）](../build/reference/zp-struct-member-alignment.md)允许调整结构的封装。

### <a name="examples-of-structure-alignment"></a>结构对齐示例

以下四个示例分别声明对齐的结构或联合，相应的数字说明了该结构或内存中的联合的布局。 图中的每列表示内存的字节，列中的数字表示该字节的位移。 每个图形的第二行中的名称对应于声明中变量的名称。 有阴影的列表示实现指定对齐所需的填充。

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

![AMD 转换示例 4 联合布局](../build/media/vcamd_conv_ex_4_block.png "AMD 转换示例 4 联合布局")

### <a name="bitfields"></a>位域

结构位字段限制为 64 位，可以是类型符号 int、无符号 int、int64 或无符号 int64。 跨越类型边界的位字段将跳过位以将位字段与下一个类型对齐方式对齐。 例如，整数位域不能跨 32 位边界。

### <a name="conflicts-with-the-x86-compiler"></a>与 x86 编译器冲突

使用 x86 编译器编译应用程序时，大于 4 个字节的数据类型不会在堆栈上自动对齐。 由于 x86 编译器的体系结构是 4 字节对齐堆栈，因此任何大于 4 字节（例如 64 位整数）都不能自动与 8 字节地址对齐。

使用未对齐的数据有两个含义。

- 访问未对齐位置所需的时间可能比访问对齐位置所需的时间长。

- 未对齐的位置不能用于互锁操作。

如果需要更严格的对齐方式，请使用变量声明上的 `__declspec(align(N))`。 这将导致编译器动态对齐堆栈以满足你的规范。 但是，在运行时动态调整堆栈可能会导致应用程序执行速度变慢。

## <a name="register-usage"></a>寄存器使用

x64 体系结构提供了 16 个通用寄存器（以后称为整数寄存器），以及 16 个可供浮点使用的 XMM/YMM 寄存器。 易失寄存器是由调用方假想的临时寄存器，并要在调用过程中销毁。 非易失寄存器需要在整个函数调用过程中保留其值，并且一旦使用，则必须由被调用方保存。

### <a name="register-volatility-and-preservation"></a>寄存器的易失性和保存方式

下表说明了每种寄存器在整个函数调用过程中的使用方法：

||||
|-|-|-|
|寄存器|状态|使用|
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

当函数进入和退出 C 运行时库调用和 Windows 系统调用时，CPU 标志寄存器的方向位标志将被清除。

## <a name="stack-usage"></a>堆栈使用

有关 x64 的堆栈分配、对齐、函数类型和堆栈帧的详细信息，请参阅 [ x64 堆栈使用](stack-usage.md)。

## <a name="prolog-and-epilog"></a>Prolog 和 Epilog

分配堆栈空间、调用其他函数、保存非易失性寄存器或使用异常处理的每个函数都必须具有 prolog，其地址限制在与相应函数表条目和每个函数出口上的 epilog 关联的展开数据中进行了描述。 有关 x64 上所需的 prolog 和 epilog 代码的详细信息，请参阅 [x64 prolog 和 epilog](prolog-and-epilog.md)。

## <a name="x64-exception-handling"></a>x64 异常处理

有关用于在 x64 上实现结构化异常处理和 C++ 异常处理行为的约定和数据结构的信息，请参阅 [x64 异常处理](exception-handling-x64.md)。

## <a name="intrinsics-and-inline-assembly"></a>内部函数和内联程序集

x64 编译器的约束之一是没有内联汇编器支持。 这意味着不能用 C 或 C++ 编写的函数必须编写为子例程，或必须编写为编译器支持的内部函数。 某些函数对性能敏感，而其他函数则不敏感。 对性能敏感的函数应作为内部函数实现。

有关编译器支持的内部函数，请参阅[编译器内部函数](../intrinsics/compiler-intrinsics.md)。

## <a name="image-format"></a>映像格式

x64 可执行映像的格式为 PE32 +。 可执行映像（DLL 和 EXE）的最大大小限制为 2 GB，因此具有 32 位偏移的相对寻址可用于处理静态映像数据。 此数据包括导入地址表、字符串常量、静态全局数据等。

## <a name="see-also"></a>请参阅

[调用约定](../cpp/calling-conventions.md)
