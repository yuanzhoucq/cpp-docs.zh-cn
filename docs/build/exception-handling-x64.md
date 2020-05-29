---
title: x64 异常处理
ms.date: 10/14/2019
helpviewer_keywords:
- C++ exception handling, x64
- exception handling, x64
ms.assetid: 41fecd2d-3717-4643-b21c-65dcd2f18c93
ms.openlocfilehash: eff4f1a22512b597b5479dbcaabcc9d5fc93c940
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303195"
---
# <a name="x64-exception-handling"></a>x64 异常处理

x64 上的结构化异常处理和 C++ 异常处理编码约定和行为的概述。 有关异常处理的常规信息，请参阅 [Visual C++ 中的异常处理](../cpp/exception-handling-in-visual-cpp.md)。

## <a name="unwind-data-for-exception-handling-debugger-support"></a>为异常处理和调试器支持展开数据

异常处理和调试支持需要几个数据结构。

### <a name="struct-runtime_function"></a>RUNTIME_FUNCTION 结构

基于表的异常处理要求分配堆栈空间或调用另一个函数（例如非叶函数）的所有函数都有一个表条目。 函数表条目的格式为：

|||
|-|-|
|ULONG|函数起始地址|
|ULONG|函数结束地址|
|ULONG|展开信息地址|

RUNTIME_FUNCTION 结构必须在内存中为 DWORD 对齐。 所有地址都相对于映像，也就是说，它们是相对于包含函数表条目的映像起始地址的 32 位偏移。 这些条目会进行排序，并放入 PE32+ 映像的 .pdata 节中。 对于动态生成的函数 [JIT 编译器]，支持这些函数的运行时必须使用 RtlInstallFunctionTableCallback 或 RtlAddFunctionTable 将此信息提供给操作系统。 否则将导致不可靠的异常处理和进程调试。

### <a name="struct-unwind_info"></a>UNWIND_INFO 结构

展开数据信息结构用于记录函数对堆栈指针的影响，以及非易失寄存器在堆栈上保存的位置：

|||
|-|-|
|UBYTE：3|Version|
|UBYTE：5|Flags|
|UBYTE|prolog 的大小|
|UBYTE|展开代码的计数|
|UBYTE：4|帧寄存器|
|UBYTE：4|帧寄存器偏移（比例）|
|USHORT \* n|展开代码数组|
|变量|可以采用下面的形式 (1) 或 (2)|

(1) 异常处理程序

|||
|-|-|
|ULONG|异常处理程序的地址|
|变量|特定于语言的处理程序数据（可选）|

(2) 链式展开信息

|||
|-|-|
|ULONG|函数起始地址|
|ULONG|函数结束地址|
|ULONG|展开信息地址|

UNWIND_INFO 结构必须在内存中为 DWORD 对齐。 下面是每个字段的含义：

- **Version**

   展开数据的版本号，当前为 1。

- **标记**

   当前定义了三个标志：

   |Flag|描述|
   |-|-|
   |`UNW_FLAG_EHANDLER`| 函数具有一个异常处理程序，应在查找需要检查异常的函数时调用该处理程序。|
   |`UNW_FLAG_UHANDLER`| 函数具有一个终止处理程序，应在展开异常时调用该处理程序。|
   |`UNW_FLAG_CHAININFO`| 此展开信息结构不是过程的主结构。 相反，链式展开信息条目是上一个 RUNTIME_FUNCTION 条目的内容。 有关信息，请参阅[链式展开信息结构](#chained-unwind-info-structures)。 如果设置了此标志，则必须清除 UNW_FLAG_EHANDLER 和 UNW_FLAG_UHANDLER 标志。 此外，帧寄存器和固定堆栈分配字段必须具有与主展开信息中相同的值。|

- prolog 的大小 

   函数 prolog 的长度（以字节为单位）。

- 展开代码的计数 

   展开代码数组中的槽数。 某些展开代码（例如 UWOP_SAVE_NONVOL）要求数组中有多个槽。

- 帧寄存器 

   如果为非零值，则函数使用帧指针 (FP)，并且此字段是用作帧指针的非易失性寄存器编号（对 UNWIND_CODE 节点的操作信息字段使用相同的编码）。

- 帧寄存器偏移（比例） 

   如果帧寄存器字段为非零值，则此字段是相对于在建立时应用于 FP 寄存器的 RSP 的比例偏移。 实际 FP 寄存器设置为 RSP + 16 \* 此数字，允许 0 到 240 的偏移。 此偏移允许将 FP 寄存器指向动态堆栈帧的本地堆栈分配中间，从而可通过更短的指令实现更好的代码密度。 （也就是说，更多指令可以使用 8 位有符号偏移形式。）

- 展开代码数组 

   说明 prolog 对非易失性寄存器和 RSP 的影响的项的数组。 有关各个项的含义，请参阅有关 UNWIND_CODE 的章节。 出于对齐目的，此数组始终具有偶数数量的条目，最后一个条目可能未使用。 在这种情况下，数组的长度会超过展开代码字段计数所指示的长度。

- 异常处理程序的地址 

   相对于映像的指针，指向函数特定于语言的异常或终止处理程序（如果清除了标志 UNW_FLAG_CHAININFO，并且设置了标志 UNW_FLAG_EHANDLER 或 UNW_FLAG_UHANDLER 中的一个）。

- 特定于语言的处理程序数据 

   函数特定于语言的异常处理程序数据。 此数据的格式未指定，完全由所使用的特定异常处理程序确定。

- 链式展开信息 

   如果设置了标志 UNW_FLAG_CHAININFO，则 UNWIND_INFO 结构以三个 UWORD 结尾。  这些 UWORD 表示链式展开函数的 RUNTIME_FUNCTION 信息。

### <a name="struct-unwind_code"></a>UNWIND_CODE 结构

展开代码数组用于记录 prolog 中影响非易失性寄存器和 RSP 的操作序列。 每个代码项都具有以下格式：

|||
|-|-|
|UBYTE|prolog 中的偏移|
|UBYTE：4|展开操作代码|
|UBYTE：4|操作信息|

数组按 prolog 中偏移的降序排序。

#### <a name="offset-in-prolog"></a>prolog 中的偏移

执行此操作的指令结尾的偏移（相对于 prolog 的开头）加 1（即下一个指令开头的偏移）。

#### <a name="unwind-operation-code"></a>展开操作代码

注意：某些操作代码需要本地堆栈帧中的值的无符号偏移。 此偏移相对于开头（即固定堆栈分配的最低地址）。 如果 UNWIND_INFO 中的帧寄存器字段为零，则此偏移相对于 RSP。 如果帧寄存器字段为非零值，则此偏移相对于建立 FP 寄存器时 RSP 所处的位置。 它等于 FP 寄存器减去 FP 寄存器偏移（16 \* UNWIND_INFO 中的比例帧寄存器偏移）。 如果使用 FP 寄存器，则必须仅在 prolog 中建立 FP 寄存器之后，才能使用任何采用偏移的展开代码。

对于除 `UWOP_SAVE_XMM128` 和 `UWOP_SAVE_XMM128_FAR` 之外的所有操作码，偏移始终为 8 的倍数，因为所有相关堆栈值都存储在 8 字节边界上（堆栈本身始终为 16 字节对齐）。 对于采用短偏移（小于 512K）的操作码，此代码的节点中的最后一个 USHORT 会保存偏移除以 8 的值。 对于采用长偏移（512K < = 偏移 < 4GB）的操作代码，此代码的最后两个 USHORT 节点会保存偏移（采用 little-endian 格式）。

对于操作码 `UWOP_SAVE_XMM128` 和 `UWOP_SAVE_XMM128_FAR`，偏移始终为 16 的倍数，因为所有 128 位 XMM 操作都必须在 16 字节对齐的内存上执行。 因此，将比例因子 16 用于 `UWOP_SAVE_XMM128`，允许小于 1M 的偏移。

展开操作代码是以下值之一：

- `UWOP_PUSH_NONVOL` (0) 1 个节点

  压入非易失性整数寄存器，按 8 递减 RSP。 操作信息是寄存器的编号。 由于对 epilog 的约束，`UWOP_PUSH_NONVOL` 展开代码必须首先出现在 prolog 中，并相应地最后出现在展开代码数组中。 此相对排序适用于除 `UWOP_PUSH_MACHFRAME` 以外的其他所有展开代码。

- `UWOP_ALLOC_LARGE` (1) 2 或 3 个节点

  在堆栈上分配大型区域。 有两种形式。 如果操作信息等于 0，则分配的大小除以 8 的值会记录在下一个槽中，允许分配最大为 512K - 8。 如果操作信息等于 1，则分配的无比例大小会采用 little-endian 格式记录在下两个槽中，允许分配最大为 4GB - 8。

- `UWOP_ALLOC_SMALL` (2) 1 个节点

  在堆栈上分配小型区域。 分配的大小是操作信息字段 \* 8 + 8，允许分配为 8 到 128 个字节。

  堆栈分配的展开代码应始终使用可能的最短编码：

  |分配大小 |展开代码 |
  |-|-|
  |8 到 128 个字节|`UWOP_ALLOC_SMALL`|
  |136 到 512K-8 个字节|`UWOP_ALLOC_LARGE` = 0|
  |512K 到 4G-8 个字节|`UWOP_ALLOC_LARGE`操作信息 = 1|

- `UWOP_SET_FPREG` (3) 1 个节点

  通过将寄存器设置为当前 RSP 的某个偏移，来建立帧指针寄存器。 偏移等于 UNWIND_INFO 中的帧寄存器偏移（比例）字段 \* 16，允许偏移为 0 到 240。 使用偏移可以建立指向固定堆栈分配中间的帧指针，允许更多访问使用短指令形式，从而帮助优化代码密度。 操作信息字段是保留字段，不应使用。

- `UWOP_SAVE_NONVOL` (4) 2 个节点

  使用 MOV（而不是 PUSH）将非易失性整数寄存器保存在堆栈上。 此代码主要用于紧缩套装  ，其中非易失性寄存器会保存到堆栈中以前分配的位置。 操作信息是寄存器的编号。 以 8 为比例的堆栈偏移会记录在下一个展开操作代码槽中，如上面的备注中所述。

- `UWOP_SAVE_NONVOL_FAR` (5) 3 个节点

  使用 MOV（而不是 PUSH），通过长偏移将非易失性整数寄存器保存在堆栈上。 此代码主要用于紧缩套装  ，其中非易失性寄存器会保存到堆栈中以前分配的位置。 操作信息是寄存器的编号。 无比例堆栈偏移会记录在下两个展开操作代码槽中，如上面的备注中所述。

- `UWOP_SAVE_XMM128` (8) 2 个节点

  将非易失性 XMM 寄存器的所有 128 位保存在堆栈上。 操作信息是寄存器的编号。 以 16 为比例的堆栈偏移会记录在下一个槽中。

- `UWOP_SAVE_XMM128_FAR` (9) 3 个节点

  通过长偏移将非易失性 XMM 寄存器的所有 128 位保存在堆栈上。 操作信息是寄存器的编号。 无比例堆栈偏移会记录在下两个槽中。

- `UWOP_PUSH_MACHFRAME` (10) 1 个节点

  压入计算机帧。  此展开代码用于记录硬件中断或异常的影响。 有两种形式。 如果操作信息等于 0，则其中一帧已压入堆栈：

  |||
  |-|-|
  |RSP+32|SS|
  |RSP+24|旧 RSP|
  |RSP+16|EFLAGS|
  |RSP+8|CS|
  |RSP|RIP|

  如果操作信息等于 1，则其中一帧已压入：

  |||
  |-|-|
  |RSP+40|SS|
  |RSP+32|旧 RSP|
  |RSP+24|EFLAGS|
  |RSP+16|CS|
  |RSP+8|RIP|
  |RSP|错误代码|

  此展开代码始终出现在虚拟 prolog 中，后者实际上不会执行，而是出现在中断例程的实际入口点之前，它的存在只是为了提供一个位置来模拟计算机帧的压入。 `UWOP_PUSH_MACHFRAME` 会记录该模拟，这表示计算机已在概念上执行此操作：

  1. 弹出 RIP 会将堆栈顶部的地址返回到 Temp  中
  
  1. 压入 SS

  1. 压入旧 RSP

  1. 压入 EFLAGS

  1. 压入 CS

  1. 压入 Temp 

  1. 压入错误代码（如果操作信息等于 1）

  模拟的 `UWOP_PUSH_MACHFRAME` 操作将 RSP 减 40（操作信息等于 0）或 48（操作信息等于 1）。

#### <a name="operation-info"></a>操作信息

操作信息位的含义取决于操作代码。 若要对常规用途（整数）寄存器进行编码，请使用此映射：

|||
|-|-|
|0|RAX|
|1|RCX|
|2|RDX|
|3|RBX|
|4|RSP|
|5|RBP|
|6|RSI|
|7|RDI|
|8 到 15|R8 到 R15|

### <a name="chained-unwind-info-structures"></a>链式展开信息结构

如果设置了 UNW_FLAG_CHAININFO 标志，则展开信息结构是辅助结构，共享异常处理程序/链接信息地址字段包含主展开信息。 此示例代码检索主展开信息，假设 `unwindInfo` 是设置了 UNW_FLAG_CHAININFO 标志的结构。

```cpp
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

链式信息在两种情况下十分有用。 首先，它可用于非连续代码段。 使用链式信息可以减少所需展开信息的大小，因为无需从主展开信息复制展开代码数组。

还可以使用链式信息对易失性寄存器保存进行分组。 编译器可能会延迟保存某些易失性寄存器，直到它位于函数入口 prolog 之外。 可以通过以下方式记录它们：让函数部分的主展开信息处于分组代码之前，然后使用非零大小的 prolog 设置链式信息（其中链式信息中的展开代码反映非易失性寄存器的保存）。 在这种情况下，展开代码是 UWOP_SAVE_NONVOL 的所有实例。 不支持使用 PUSH 保存非易失性寄存器或使用其他固定堆栈分配修改 RSP 寄存器的分组。

设置了 UNW_FLAG_CHAININFO 的 UNWIND_INFO 项可以包含其 UNWIND_INFO 项也设置了 UNW_FLAG_CHAININFO 的 RUNTIME_FUNCTION 条目，有时称为多个紧缩套装  。 最后，链式展开信息指针会到达清除了 UNW_FLAG_CHAININFO 的 UNWIND_INFO 项。 此项是主 UNWIND_INFO 项，它指向实际过程入口点。

## <a name="unwind-procedure"></a>展开过程

展开代码数组按降序排序。 发生异常时，操作系统会在上下文记录中存储完整上下文。 然后调用异常调度逻辑，这会重复执行以下步骤来查找异常处理程序：

1. 使用上下文记录中存储的当前 RIP 搜索描述当前函数（或对于链式 UNWIND_INFO 条目为函数部分）的 RUNTIME_FUNCTION 表条目。

1. 如果未找到任何函数表条目，则它位于叶函数中，并且 RSP 直接对返回指针寻址。 [RSP] 上的返回指针存储在更新后的上下文中，模拟的 RSP 按 8 递增，并且步骤 1 重复执行。

1. 如果找到函数表条目，则 RIP 可能位于三个区域中：a) epilog 中，b) prolog 中，或 c) 可能由异常处理程序所涵盖的代码中。

   - 情况 a) 如果 RIP 在 epilog 中，则控制会离开函数，此函数可能没有与此异常关联的异常处理程序，epilog 的效果必须继续以计算调用方函数的上下文。 若要确定 RIP 是否在 epilog 中，请检查从 RIP 开始的代码流。 如果该代码流可与合法 epilog 的尾随部分匹配，则它在 epilog 中，epilog 的剩余部分会进行模拟，并在处理每个指令时更新上下文记录。 此处理完成之后，会重复步骤 1。

   - 情况 b) 如果 RIP 在 prologue 中，则控制未进入函数，此函数可能没有与此异常关联的异常处理程序，prolog 的效果必须撤消以计算调用方函数的上下文。 如果从函数开头到 RIP 的距离小于或等于在展开信息中编码的 prolog 大小，则 RIP 在 prolog 中。 prolog 的效果通过以下方式展开：在展开代码数组中向前扫描，查找偏移小于或等于 RIP 相对于函数开头的偏移的第一个条目，然后撤消展开代码数组中所有剩余项的效果。 然后重复步骤 1。

   - 情况 c) 如果 RIP 不在 prolog 或 epilog 中，并且函数具有异常处理程序（设置了 UNW_FLAG_EHANDLER），则调用特定于语言的处理程序。 处理程序会扫描其数据，并根据需要调用筛选器函数。 特定于语言的处理程序可以返回已处理异常或继续搜索。 它还可以直接启动展开。

1. 如果特定于语言的处理程序返回已处理状态，则使用原始上下文记录继续执行。

1. 如果没有特定于语言的处理程序或处理程序返回“继续搜索”状态，则必须将上下文记录展开为调用方的状态。 实现方法是处理所有展开代码数组元素，从而撤消每个元素的效果。 然后重复步骤 1。

涉及到链式展开信息时，仍然遵循这些基本步骤。 唯一的区别在于，当遍历展开代码数组以展开 prolog 的效果时，一旦到达数组末尾，它便会链接到父展开信息，并且遍历在其中找到的整个展开代码数组。 此链接将继续，直到到达没有 UNW_CHAINED_INFO 标志的展开信息，随后完成遍历其展开代码数组。

最小的展开数据集是 8 个字节。 这表示一个函数，该函数只分配了 128 个字节或更少的堆栈，并且可能保存了一个非易失性寄存器。 它也是不带展开代码的零长度 prolog 的链式展开信息结构大小。

## <a name="language-specific-handler"></a>特定于语言的处理程序

每当设置了标志 UNW_FLAG_EHANDLER 或 UNW_FLAG_UHANDLER 时，特定于语言的处理程序的相对地址便会出现在 UNWIND_INFO 中。 如上一节所述，特定于语言的处理程序作为异常处理程序搜索的一部分或是展开的一部分进行调用。 它具有以下原型：

```cpp
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

ExceptionRecord  提供指向具有标准 Win64 定义的异常记录的指针。

EstablisherFrame  是此函数的固定堆栈分配的基址。

ContextRecord  指向引发异常时的异常上下文（在异常处理程序情况下）或当前“展开”上下文（在终止处理程序情况下）。

DispatcherContext  指向此函数的调度程序上下文。 它具有以下定义：

```cpp
typedef struct _DISPATCHER_CONTEXT {
    ULONG64 ControlPc;
    ULONG64 ImageBase;
    PRUNTIME_FUNCTION FunctionEntry;
    ULONG64 EstablisherFrame;
    ULONG64 TargetIp;
    PCONTEXT ContextRecord;
    PEXCEPTION_ROUTINE LanguageHandler;
    PVOID HandlerData;
} DISPATCHER_CONTEXT, *PDISPATCHER_CONTEXT;
```

ControlPc  是此函数中的 RIP 值。 此值可以是异常地址，也可以是控制离开建立函数的位置处的地址。 RIP 用于确定控制是否在此函数内的某个受保护构造中，例如，`__try`/`__except` 或 `__try`/`__finally` 的 `__try` 块。

ImageBase  是包含此函数的模块的映像基（加载地址），要与函数入口和展开信息中使用的 32 位偏移相加，以记录相对地址。

FunctionEntry  提供指向 RUNTIME_FUNCTION 函数入口的指针，其中为此函数保存函数和展开信息映像基相对地址。

EstablisherFrame  是此函数的固定堆栈分配的基址。

TargetIp  提供指定展开的延续地址的可选指令地址。 如果未指定 EstablisherFrame  ，则忽略此地址。

ContextRecord  指向异常上下文，供系统异常调度/展开代码使用。

LanguageHandler  指向所调用的特定于语言的语言处理程序例程。

HandlerData  指向此函数的特定于语言的处理程序数据。

## <a name="unwind-helpers-for-masm"></a>MASM 的展开帮助程序

为了编写正确的程序集例程，有一组伪操作可与实际的程序集指令并行使用，以创建适当的 .pdata 和 .xdata。 并且有一组宏可简化伪操作的使用，以实现其最常见的用途。

### <a name="raw-pseudo-operations"></a>原始伪操作

|伪操作|描述|
|-|-|
|PROC FRAME \[:ehandler  ]|使 MASM 在 .pdata 中生成函数表条目，并在 .xdata 中生成展开信息，以实现函数的结构化异常处理展开行为。  如果 ehandler  存在，则此过程作为特定于语言的处理程序在 .xdata 中输入。<br /><br /> 使用 FRAME 特性时，它必须后跟 .ENDPROLOG 指令。  如果函数是叶函数（如[函数类型](../build/stack-usage.md#function-types)所定义），则不需要 FRAME 特性，其余的这些伪操作也是如此。|
|.PUSHREG register |使用序言中的当前偏移为指定寄存器编号生成 UWOP_PUSH_NONVOL 展开代码条目。<br /><br /> 仅将它与非易失性整数寄存器一起使用。  对于易失性寄存器的压入，改为使用 .ALLOCSTACK 8|
|.SETFRAME register  , offset |使用指定寄存器和偏移在展开信息中填充帧寄存器字段和偏移。 偏移必须是 16 的倍数，并且小于或等于 240。 此指令还使用当前序言偏移为指定寄存器生成 UWOP_SET_FPREG 展开代码条目。|
|.ALLOCSTACK size |针对序言中的当前偏移生成具有指定大小的 UWOP_ALLOC_SMALL 或 UWOP_ALLOC_LARGE。<br /><br /> size  操作数必须是 8 的倍数。|
|.SAVEREG register  , offset |使用当前序言偏移为指定寄存器和偏移生成 UWOP_SAVE_NONVOL 或 UWOP_SAVE_NONVOL_FAR 展开代码条目。 MASM 会选择最高效的编码。<br /><br /> offset  必须为正，并且是 8 的倍数。 offset  相对于过程帧（通常在 RSP 中）的基址或无比例帧指针（如果使用帧指针）。|
|.SAVEXMM128 register, offset  |使用当前序言偏移为指定 XMM 寄存器和偏移生成 UWOP_SAVE_XMM128 或 UWOP_SAVE_XMM128_FAR 展开代码条目。 MASM 会选择最高效的编码。<br /><br /> offset  必须为正，并且是 16 的倍数。  offset  相对于过程帧（通常在 RSP 中）的基址或无比例帧指针（如果使用帧指针）。|
|.PUSHFRAME \[code  ]|生成 UWOP_PUSH_MACHFRAME 展开代码条目。 如果指定了可选的 code  ，则为展开代码条目提供修饰符 1。 否则修饰符为 0。|
|.ENDPROLOG|指示序言声明的结尾。  必须出现在函数的前 255 个字节中。|

下面是一个示例函数 prolog，其中包含大多数操作码的正确用法：

```MASM
sample PROC FRAME
    db      048h; emit a REX prefix, to enable hot-patching
    push rbp
    .pushreg rbp
    sub rsp, 040h
    .allocstack 040h
    lea rbp, [rsp+020h]
    .setframe rbp, 020h
    movdqa [rbp], xmm7
    .savexmm128 xmm7, 020h ;the offset is from the base of the frame
                           ;not the scaled offset of the frame
    mov [rbp+018h], rsi
    .savereg rsi, 038h
    mov [rsp+010h], rdi
    .savereg rdi, 010h ; you can still use RSP as the base of the frame
                       ; or any other register you choose
    .endprolog

; you can modify the stack pointer outside of the prologue (similar to alloca)
; because we have a frame pointer.
; if we didn't have a frame pointer, this would be illegal
; if we didn't make this modification,
; there would be no need for a frame pointer

    sub rsp, 060h

; we can unwind from the next AV because of the frame pointer

    mov rax, 0
    mov rax, [rax] ; AV!

; restore the registers that weren't saved with a push
; this isn't part of the official epilog, as described in section 2.5

    movdqa xmm7, [rbp]
    mov rsi, [rbp+018h]
    mov rdi, [rbp-010h]

; Here's the official epilog

    lea rsp, [rbp+020h] ; deallocate both fixed and dynamic portions of the frame
    pop rbp
    ret
sample ENDP
```

有关 epilog 示例的详细信息，请参阅 [x64 prolog 和 epilog](prolog-and-epilog.md) 中的 [Epilog 代码](prolog-and-epilog.md#epilog-code)。

### <a name="masm-macros"></a>MASM 宏

为了简化[原始伪操作](#raw-pseudo-operations)的使用，在 ksamd64.inc 中定义了一组宏，可用于创建典型过程序言和尾声。

|宏|描述|
|-|-|
|alloc_stack(n)|分配 n 个字节的堆栈帧（使用 `sub rsp, n`），并发出适当的展开信息 (.allocstack n)|
|save_reg reg, loc  |将非易失性寄存器 reg  保存在堆栈上 RSP 偏移为 loc  的位置处，并发出适当的展开信息。 (.savereg reg, loc)|
|push_reg reg |将非易失性寄存器 reg  压入堆栈，并发出适当的展开信息。 (.pushreg reg)|
|rex_push_reg reg |使用 2 字节压入将非易失性寄存器保存在堆栈中，并发出适当的展开信息 (.pushreg reg)。  如果压入是函数中的第一个指令，则使用此宏，以确保函数是可进行热修补。|
|save_xmm128 reg, loc  |将非易失性 XMM 寄存器 reg  保存在堆栈上 RSP 偏移为 loc  的位置处，并发出适当的展开信息 (.savexmm128 reg, loc)|
|set_frame reg, offset  |将帧寄存器 reg  设置为 RSP + offset  （使用 `mov` 或 `lea`），并发出适当的展开信息 (.set_frame reg, offset)|
|push_eflags|将 eflags 与 `pushfq` 指令一起压入，并发出适当的展开信息 (.alloc_stack 8)|

下面是一个示例函数 prolog，其中包含宏的正确用法：

```MASM
sampleFrame struct
    Fill     dq ?; fill to 8 mod 16
    SavedRdi dq ?; Saved Register RDI
    SavedRsi dq ?; Saved Register RSI
sampleFrame ends

sample2 PROC FRAME
    alloc_stack(sizeof sampleFrame)
    save_reg rdi, sampleFrame.SavedRdi
    save_reg rsi, sampleFrame.SavedRsi
    .end_prolog

; function body

    mov rsi, sampleFrame.SavedRsi[rsp]
    mov rdi, sampleFrame.SavedRdi[rsp]

; Here's the official epilog

    add rsp, (sizeof sampleFrame)
    ret
sample2 ENDP
```

## <a name="unwind-data-definitions-in-c"></a>展开数据定义（C 语言描述）

下面是展开数据的 C 语言描述：

```C
typedef enum _UNWIND_OP_CODES {
    UWOP_PUSH_NONVOL = 0, /* info == register number */
    UWOP_ALLOC_LARGE,     /* no info, alloc size in next 2 slots */
    UWOP_ALLOC_SMALL,     /* info == size of allocation / 8 - 1 */
    UWOP_SET_FPREG,       /* no info, FP = RSP + UNWIND_INFO.FPRegOffset*16 */
    UWOP_SAVE_NONVOL,     /* info == register number, offset in next slot */
    UWOP_SAVE_NONVOL_FAR, /* info == register number, offset in next 2 slots */
    UWOP_SAVE_XMM128 = 8, /* info == XMM reg number, offset in next slot */
    UWOP_SAVE_XMM128_FAR, /* info == XMM reg number, offset in next 2 slots */
    UWOP_PUSH_MACHFRAME   /* info == 0: no error-code, 1: error-code */
} UNWIND_CODE_OPS;

typedef union _UNWIND_CODE {
    struct {
        UBYTE CodeOffset;
        UBYTE UnwindOp : 4;
        UBYTE OpInfo   : 4;
    };
    USHORT FrameOffset;
} UNWIND_CODE, *PUNWIND_CODE;

#define UNW_FLAG_EHANDLER  0x01
#define UNW_FLAG_UHANDLER  0x02
#define UNW_FLAG_CHAININFO 0x04

typedef struct _UNWIND_INFO {
    UBYTE Version       : 3;
    UBYTE Flags         : 5;
    UBYTE SizeOfProlog;
    UBYTE CountOfCodes;
    UBYTE FrameRegister : 4;
    UBYTE FrameOffset   : 4;
    UNWIND_CODE UnwindCode[1];
/*  UNWIND_CODE MoreUnwindCode[((CountOfCodes + 1) & ~1) - 1];
*   union {
*       OPTIONAL ULONG ExceptionHandler;
*       OPTIONAL ULONG FunctionEntry;
*   };
*   OPTIONAL ULONG ExceptionData[]; */
} UNWIND_INFO, *PUNWIND_INFO;

typedef struct _RUNTIME_FUNCTION {
    ULONG BeginAddress;
    ULONG EndAddress;
    ULONG UnwindData;
} RUNTIME_FUNCTION, *PRUNTIME_FUNCTION;

#define GetUnwindCodeEntry(info, index) \
    ((info)->UnwindCode[index])

#define GetLanguageSpecificDataPtr(info) \
    ((PVOID)&GetUnwindCodeEntry((info),((info)->CountOfCodes + 1) & ~1))

#define GetExceptionHandler(base, info) \
    ((PEXCEPTION_HANDLER)((base) + *(PULONG)GetLanguageSpecificDataPtr(info)))

#define GetChainedFunctionEntry(base, info) \
    ((PRUNTIME_FUNCTION)((base) + *(PULONG)GetLanguageSpecificDataPtr(info)))

#define GetExceptionDataPtr(info) \
    ((PVOID)((PULONG)GetLanguageSpecificData(info) + 1)
```

## <a name="see-also"></a>请参阅

[x64 软件约定](../build/x64-software-conventions.md)
