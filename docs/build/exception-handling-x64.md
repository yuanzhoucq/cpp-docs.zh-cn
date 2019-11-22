---
title: x64 异常处理
ms.date: 10/14/2019
helpviewer_keywords:
- C++ exception handling, x64
- exception handling, x64
ms.assetid: 41fecd2d-3717-4643-b21c-65dcd2f18c93
ms.openlocfilehash: eff4f1a22512b597b5479dbcaabcc9d5fc93c940
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303195"
---
# <a name="x64-exception-handling"></a>x64 异常处理

概括介绍了结构化异常处理C++以及 x64 上的异常处理代码约定和行为。 有关异常处理的常规信息，请参阅[Visual C++中的异常处理](../cpp/exception-handling-in-visual-cpp.md)。

## <a name="unwind-data-for-exception-handling-debugger-support"></a>用于异常处理和调试器支持的展开数据

异常处理和调试支持需要几个数据结构。

### <a name="struct-runtime_function"></a>RUNTIME_FUNCTION 结构

基于表的异常处理需要一个表条目用于分配堆栈空间或调用另一个函数（例如非叶函数）的所有函数。 函数表项的格式为：

|||
|-|-|
|ULONG|函数起始地址|
|ULONG|函数结束地址|
|ULONG|展开信息地址|

RUNTIME_FUNCTION 结构必须在内存中对齐 DWORD。 所有地址都是相对的，也就是说，它们是从包含函数表项的图像的起始地址开始的32位偏移量。 将对这些项进行排序，并将其放入 PE32 + 图像的 pdata 节中。 对于动态生成的函数 [JIT 编译器]，支持这些函数的运行时必须使用 RtlInstallFunctionTableCallback 或 RtlAddFunctionTable 将此信息提供给操作系统。 否则，将导致不可靠的异常处理和进程调试。

### <a name="struct-unwind_info"></a>UNWIND_INFO 结构

展开数据信息结构用于记录函数对堆栈指针的影响，以及非易失寄存器保存在堆栈上的位置：

|||
|-|-|
|UBYTE：3|版本|
|UBYTE：5|标志|
|UBYTE|序言大小|
|UBYTE|展开代码计数|
|UBYTE：4|帧寄存器|
|UBYTE：4|帧寄存器偏移量（缩放）|
|USHORT \* n|展开代码数组|
|变量|格式可以是（1）或以下（2）|

（1）异常处理程序

|||
|-|-|
|ULONG|异常处理程序的地址|
|变量|特定于语言的处理程序数据（可选）|

（2）链式展开信息

|||
|-|-|
|ULONG|函数起始地址|
|ULONG|函数结束地址|
|ULONG|展开信息地址|

UNWIND_INFO 结构必须在内存中对齐 DWORD。 每个字段的含义如下：

- **版本**

   展开数据的版本号，当前为1。

- **标记**

   当前定义了三个标志：

   |Flag|描述|
   |-|-|
   |`UNW_FLAG_EHANDLER`| 函数包含一个异常处理程序，该处理程序在查找需要检查异常的函数时应调用。|
   |`UNW_FLAG_UHANDLER`| 函数具有一个终止处理程序，该处理程序应在展开异常时调用。|
   |`UNW_FLAG_CHAININFO`| 此展开信息结构不是过程的主结构。 相反，链式展开信息项是上一个 RUNTIME_FUNCTION 条目的内容。 有关信息，请参阅[链式展开信息结构](#chained-unwind-info-structures)。 如果设置了此标志，则必须清除 UNW_FLAG_EHANDLER 和 UNW_FLAG_UHANDLER 标志。 此外，帧寄存器和固定堆栈分配字段必须具有与主展开信息中相同的值。|

- **序言大小**

   函数 prolog 的长度（以字节为单位）。

- **展开代码计数**

   展开代码数组中的槽数。 某些展开代码（例如 UWOP_SAVE_NONVOL）需要数组中有多个槽。

- **帧寄存器**

   如果为非零值，则函数使用帧指针（FP），并且此字段是用作帧指针的非易失寄存器号，对于 UNWIND_CODE 节点的操作信息字段，使用相同的编码。

- **帧寄存器偏移量（缩放）**

   如果帧寄存器字段为非零值，则此字段是在建立该字段时，将应用于该 实际的 FP 寄存器设置为 RSP + 16 \* 此数字，允许从0到240的偏移量。 此偏移量允许将 FP 注册到动态堆栈帧的本地堆栈分配中间，并通过更短的指令使代码密度更好。 （也就是说，更多说明可使用8位有符号偏移量形式。）

- **展开代码数组**

   一个项的数组，这些项说明 prolog 对非易失性寄存器和 RSP 的影响。 有关各个项的含义，请参阅 UNWIND_CODE 上的部分。 出于对齐目的，此数组始终具有偶数数目的条目，最终条目可能未使用。 在这种情况下，数组的长度超过 "展开代码" 字段的计数。

- **异常处理程序的地址**

   指向函数的特定于语言的异常或终止处理程序的图像相对指针，如果标志 UNW_FLAG_CHAININFO 清晰，并且已设置其中一个标志 UNW_FLAG_EHANDLER 或 UNW_FLAG_UHANDLER。

- **特定于语言的处理程序数据**

   函数的特定于语言的异常处理程序数据。 此数据的格式未指定，并由正在使用的特定异常处理程序完全确定。

- **链式展开信息**

   如果设置了标志 UNW_FLAG_CHAININFO，则 UNWIND_INFO 结构以三个 UWORDs 结束。  这些 UWORDs 表示链式展开功能的 RUNTIME_FUNCTION 信息。

### <a name="struct-unwind_code"></a>UNWIND_CODE 结构

展开代码数组用于记录 prolog 中影响非易失性寄存器和 RSP 的操作顺序。 每个代码项都具有以下格式：

|||
|-|-|
|UBYTE|序言中的偏移|
|UBYTE：4|展开操作代码|
|UBYTE：4|操作信息|

数组按序言中偏移量的降序排序。

#### <a name="offset-in-prolog"></a>序言中的偏移

执行此操作的指令末尾的偏移量（从 prolog 开头开始）加上1（即下一指令开头的偏移量）。

#### <a name="unwind-operation-code"></a>展开操作代码

注意：某些操作代码要求本地堆栈帧中的值有无符号偏移量。 此偏移量来自开始，即固定堆栈分配的最低地址。 如果 UNWIND_INFO 中的 "帧注册" 字段为零，则此偏移量来自 RSP。 如果帧寄存器字段为非零值，则此偏移量是在建立 FP 注册时的位置。 它等于 FP register 减去 FP 寄存器偏移量（16 \* UNWIND_INFO 中的缩放帧寄存器偏移量）。 如果使用 FP 寄存器，则只有在序言中建立 FP 注册后，才必须使用任何采用偏移量的展开代码。

对于除 `UWOP_SAVE_XMM128` 和 `UWOP_SAVE_XMM128_FAR`之外的所有操作码，偏移量始终为8的倍数，因为所有相关堆栈值都存储在8字节边界上（堆栈本身始终是16个字节的对齐）。 对于采用短偏移量（小于512K）的操作代码，此代码的节点中的最后 USHORT 将保留偏移量除以8。 对于采用长偏移量（512K < = offset < 4GB）的操作代码，此代码的最后两个 USHORT 节点将保存偏移量（以小字节序格式）。

对于操作码 `UWOP_SAVE_XMM128` 和 `UWOP_SAVE_XMM128_FAR`，偏移量始终为16的倍数，因为所有128位 XMM 操作都必须在16字节对齐的内存上执行。 因此，`UWOP_SAVE_XMM128`使用的缩放比例为16，允许小于1M 的偏移量。

展开操作代码是以下值之一：

- `UWOP_PUSH_NONVOL` （0）1节点

  推送非易失性整数寄存器，并按8递减 RSP。 操作信息是寄存器的编号。 由于对 epilogs 的约束，`UWOP_PUSH_NONVOL` 展开代码必须首先出现在序言中，并相应地出现在展开代码数组中。 此相对排序适用于除 `UWOP_PUSH_MACHFRAME`以外的其他所有展开代码。

- `UWOP_ALLOC_LARGE` （1）2或3节点

  在堆栈上分配大的区域。 有两种形式。 如果操作信息等于0，则分配的大小除以8，以允许分配最大为 512K-8。 如果操作信息等于1，则分配的无比例大小将记录在下两个采用小 endian 格式的槽中，并允许分配最大为 4GB-8。

- `UWOP_ALLOC_SMALL` （2）1节点

  在堆栈上分配小尺寸的区域。 分配的大小为操作信息字段 \* 8 + 8，允许分配8到128字节。

  堆栈分配的展开代码应始终使用可能的最短编码：

  |**分配大小**|**展开代码**|
  |-|-|
  |8到128字节|`UWOP_ALLOC_SMALL`|
  |136到 512K-8 字节|`UWOP_ALLOC_LARGE`，操作信息 = 0|
  |512K 到 4G-8 字节|`UWOP_ALLOC_LARGE`，操作信息 = 1|

- `UWOP_SET_FPREG` （3）1节点

  通过将寄存器设置为当前 RSP 的某个偏移量，建立帧指针寄存器。 偏移量等于 UNWIND_INFO \* 16 中的帧寄存器偏移量（缩放）字段，允许从0到240的偏移量。 使用偏移量允许建立指向固定堆栈分配中间的帧指针，通过允许更多访问来使用简短的指令窗体来帮助代码密度。 "操作信息" 字段是保留字段，不应使用。

- `UWOP_SAVE_NONVOL` （4）2个节点

  使用 MOV 而不是推送将非易失性整数寄存器保存在堆栈上。 此代码主要用于*收缩环绕*，其中的非易失寄存器保存到堆栈中以前分配的位置。 操作信息是寄存器的编号。 按上述说明中所述，在下一个展开操作代码槽中记录按8扩展的堆栈偏移量。

- `UWOP_SAVE_NONVOL_FAR` （5）个节点

  使用 MOV 而不是推送，将非易失性整数寄存器保存在带有长偏移量的堆栈上。 此代码主要用于*收缩环绕*，其中的非易失寄存器保存到堆栈中以前分配的位置。 操作信息是寄存器的编号。 在接下来的两个展开操作代码槽中记录了不成比例的堆栈偏移，如上文所述。

- `UWOP_SAVE_XMM128` （8）2个节点

  在堆栈上保存非易失性 XMM 寄存器的所有128位。 操作信息是寄存器的编号。 下一个槽中记录的按16个堆栈偏移量。

- `UWOP_SAVE_XMM128_FAR` （9）3节点

  在带有长偏移量的堆栈上保存非易失 XMM 寄存器的所有128位。 操作信息是寄存器的编号。 在接下来的两个槽中记录未缩放的堆栈偏移量。

- `UWOP_PUSH_MACHFRAME` （10）1节点

  推送计算机帧。  此展开代码用于记录硬件中断或异常的影响。 有两种形式。 如果操作信息等于0，则表示已将其中一帧推入堆栈：

  |||
  |-|-|
  |RSP+32|SS|
  |RSP+24|旧 RSP|
  |RSP+16|EFLAGS|
  |RSP+8|CS|
  |RSP|RIP|

  如果操作信息等于1，则会推送其中一帧：

  |||
  |-|-|
  |RSP+40|SS|
  |RSP+32|旧 RSP|
  |RSP+24|EFLAGS|
  |RSP+16|CS|
  |RSP+8|RIP|
  |RSP|错误代码|

  此展开代码始终出现在虚拟序言中，这实际上不会执行，而是出现在中断例程的实际入口点之前，而只是为了提供模拟计算机帧推送的位置。 模拟模拟 `UWOP_PUSH_MACHFRAME` 记录，指示计算机在概念上完成了此操作：

  1. 从堆栈顶部到*Temp*的 Pop RIP 返回地址
  
  1. 推送 SS

  1. 推送旧 RSP

  1. 推送 EFLAGS

  1. 推送 CS

  1. 推送*临时*

  1. 推送错误代码（如果 op info 等于1）

  模拟 `UWOP_PUSH_MACHFRAME` 操作将 RSP 减40（op info 等于0）或48（op info 等于1）。

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
|8到15|R8 到 R15|

### <a name="chained-unwind-info-structures"></a>链式展开信息结构

如果设置了 UNW_FLAG_CHAININFO 标志，则展开信息结构为辅助结构，共享异常处理程序/链接信息地址字段包含主展开信息。 此示例代码检索主展开信息，前提是 `unwindInfo` 是设置了 UNW_FLAG_CHAININFO 标志的结构。

```cpp
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

链接信息在两种情况下很有用。 首先，它可用于非连续代码段。 通过使用链式信息，你可以减少所需的展开信息的大小，因为无需从主展开信息复制展开代码数组。

你还可以使用链式信息对易失寄存器保存进行分组。 编译器可能会延迟保存某些易失寄存器，直到其位于函数入口 prolog 之外。 您可以通过在分组代码之前为函数的部分设置主展开信息，然后使用非零大小的 prolog 设置链式信息（其中链式信息中的展开代码反映非易失寄存器的保存）来记录这些问题。 在这种情况下，展开代码是 UWOP_SAVE_NONVOL 的所有实例。 不支持通过使用 PUSH 来保存非易失寄存器或使用其他固定堆栈分配来修改 RSP 寄存器的分组。

具有 UNW_FLAG_CHAININFO 集的 UNWIND_INFO 项可以包含一个 RUNTIME_FUNCTION 项，该项的 UNWIND_INFO 项也具有 UNW_FLAG_CHAININFO 集，有时称为*多个收缩包装*。 最终，链式展开信息指针到达 UNW_FLAG_CHAININFO 清除的 UNWIND_INFO 项。 此项是主 UNWIND_INFO 项，它指向实际过程入口点。

## <a name="unwind-procedure"></a>展开过程

展开代码数组按降序排序。 发生异常时，操作系统会在上下文记录中存储完整的上下文。 然后调用异常调度逻辑，这会重复执行以下步骤来查找异常处理程序：

1. 使用上下文记录中存储的当前 RIP 搜索描述当前函数（或函数部分，对于链式 UNWIND_INFO 条目）的 RUNTIME_FUNCTION 表项。

1. 如果未找到任何函数表项，则它位于叶函数中，并且 RSP 直接寻址返回指针。 [RSP] 上的返回指针存储在更新后的上下文中，模拟的 RSP 递增8，步骤1是重复的。

1. 如果找到函数表项，则 RIP 可以位于 prolog （b）中的 epilog、b）中的三个区域内，或 c 中的代码中，该代码可由异常处理程序所涵盖。

   - Case a）如果 RIP 位于 epilog 内，则控制将离开函数，此函数可能没有与此异常相关联的异常处理程序，并且必须继续计算调用方函数的上下文。 若要确定 RIP 是否在 epilog 内，请检查来自 RIP 的代码流。 如果该代码流可与合法 epilog 的尾随部分匹配，则它在 epilog 中，并模拟 epilog 的剩余部分，并在处理每个指令时更新上下文记录。 此处理完成后，将重复步骤1。

   - Case b）如果 RIP 位于序言内，则 control 尚未进入函数，此函数没有与此异常相关联的异常处理程序，并且必须撤消序言的效果来计算调用方函数的上下文。 如果从函数开始到 RIP 的距离小于或等于在展开信息中编码的序言大小，则 RIP 处于 prolog 内。 通过以下方法展开序言的效果：在以下情况下，向前扫描：向偏移量小于或等于 RIP 从函数开始的偏移量的第一个条目，然后撤消展开代码数组中所有剩余项的效果。 然后重复步骤1。

   - 情况 c）如果 RIP 不在 prolog 或 epilog 内，并且函数有异常处理程序（UNW_FLAG_EHANDLER 设置），则调用特定于语言的处理程序。 处理程序会扫描其数据，并根据需要调用筛选器函数。 特定于语言的处理程序可以返回已处理的异常或继续搜索。 它还可以直接启动展开。

1. 如果特定于语言的处理程序返回已处理状态，则继续使用原始上下文记录执行。

1. 如果没有特定于语言的处理程序或处理程序返回 "继续搜索" 状态，则必须将上下文记录展开为调用方的状态。 完成此操作的方法是处理所有展开代码数组元素，并撤消每个元素的影响。 然后重复步骤1。

涉及到链式展开信息时，仍然遵循这些基本步骤。 唯一的不同之处在于，当遍历代码数组展开序言的效果时，一旦到达数组的末尾，就会将其链接到父展开信息，并且在遍历的整个展开代码数组中找到。 此链接将继续，直到到达没有 UNW_CHAINED_INFO 标志的展开信息，然后遍历其展开代码数组。

最小的展开数据集是8个字节。 这会表示一个函数，该函数只分配了堆栈或更少的128个字节，并且可能会保存一个非易失寄存器。 它也是不带展开代码的零长度 prolog 的链接展开信息结构的大小。

## <a name="language-specific-handler"></a>特定于语言的处理程序

只要设置了标志 UNW_FLAG_EHANDLER 或 UNW_FLAG_UHANDLER，特定于语言的处理程序的相对地址就会出现在 UNWIND_INFO 中。 如上一节所述，特定于语言的处理程序作为异常处理程序搜索的一部分或在展开过程中被调用。 它具有以下原型：

```cpp
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**ExceptionRecord**提供一个指针，该指针指向具有标准 Win64 定义的异常记录。

**EstablisherFrame**是此函数的固定堆栈分配的基址。

**ContextRecord**指向引发异常时的异常上下文（在异常处理程序的情况下）或当前的 "展开" 上下文（在终止处理程序的情况下）。

**DispatcherContext**指向此函数的调度程序上下文。 它具有以下定义：

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

**ControlPc**是此函数中的 RIP 值。 此值可以是异常地址，也可以是控制离开建立函数的地址。 裂缝用于确定控件是否在此函数内的某些受保护的构造中，例如，`__try`/的 `__try` 块 `__except` 或 `__try`/`__finally`。

**ImageBase**是包含此函数的模块的映像基（加载地址），将其添加到函数入口中使用的32位偏移，以记录相对地址。

**FunctionEntry**提供一个指针，该指针指向保存此函数的函数和展开信息图像基相对地址的 RUNTIME_FUNCTION 函数入口。

**EstablisherFrame**是此函数的固定堆栈分配的基址。

**TargetIp**提供指定展开的延续地址的可选指令地址。 如果未指定**EstablisherFrame** ，则忽略此地址。

**ContextRecord**指向异常上下文，供系统异常调度/展开代码使用。

**LanguageHandler**指向所调用的特定于语言的语言处理程序例程。

**HandlerData**指向此函数的特定于语言的处理程序数据。

## <a name="unwind-helpers-for-masm"></a>MASM 的展开帮助器

为了编写正确的程序集例程，有一组伪操作可与实际的程序集指令并行使用，以创建适当的 pdata 和. xdata。 另外还有一组宏，可为其最常见的用途简化伪操作的使用。

### <a name="raw-pseudo-operations"></a>原始伪操作

|伪操作|描述|
|-|-|
|处理器框架 \[：*ehandler*]|使 MASM 在 pdata 中生成函数表项，并在 xdata 中为函数的结构化异常处理展开行为生成展开信息。  如果*ehandler*存在，则在 xdata 中将此过程输入为特定于语言的处理程序。<br /><br /> 当使用 FRAME 属性时，它必须后跟。ENDPROLOG 指令。  如果函数是叶函数（在[函数类型](../build/stack-usage.md#function-types)中定义），则不需要帧属性，这与这些伪操作的其余部分相同。|
|.PUSHREG*注册*|使用序言中的当前偏移量为指定寄存器号生成 UWOP_PUSH_NONVOL 的展开代码项。<br /><br /> 仅将它与非易失性整数寄存器一起使用。  对于易失寄存器的推送，请使用。ALLOCSTACK 8，而不是|
|..SETFRAME*寄存器*，*偏移量*|使用指定的寄存器和偏移量在展开信息中填充帧寄存器字段和偏移量。 偏移量必须是16的倍数，小于或等于240。 此指令还使用当前的序言偏移量为指定的寄存器生成 UWOP_SET_FPREG 的展开代码项。|
|.ALLOCSTACK*大小*|为序言中的当前偏移量生成指定大小的 UWOP_ALLOC_SMALL 或 UWOP_ALLOC_LARGE。<br /><br /> *大小*操作数必须是8的倍数。|
|.SAVEREG*寄存器*，*偏移量*|使用当前的序言偏移量为指定的寄存器生成 UWOP_SAVE_NONVOL 或 UWOP_SAVE_NONVOL_FAR 展开代码项。 MASM 选择最有效的编码。<br /><br /> *偏移量*必须为正，且为8的倍数。 *偏移量*是相对于过程框架的基，后者通常在 RSP 中，或者如果使用帧指针，则是未缩放的帧指针。|
|.SAVEXMM128*寄存器*，*偏移量*|为指定的 XMM register 生成 UWOP_SAVE_XMM128 或 UWOP_SAVE_XMM128_FAR 展开代码项，并使用当前的序言偏移量偏移。 MASM 选择最有效的编码。<br /><br /> *偏移量*必须为正，且为16的倍数。  *偏移量*是相对于过程框架的基，后者通常在 RSP 中，或者如果使用帧指针，则是未缩放的帧指针。|
|.SYSTEM.WINDOWS.THREADING.DISPATCHER.PUSHFRAME \[*代码*]|生成 UWOP_PUSH_MACHFRAME 展开代码项。 如果指定了可选*代码*，则为展开代码条目指定修饰符1。 否则，修饰符为0。|
|.ENDPROLOG|指示序言声明的结尾。  必须出现在函数的前255个字节中。|

下面是一个示例函数 prolog，其中包含对大多数操作码的正确使用：

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

有关 epilog 示例的详细信息，请参阅[x64 prolog 和 epilog](prolog-and-epilog.md)中的[epilog 代码](prolog-and-epilog.md#epilog-code)。

### <a name="masm-macros"></a>MASM 宏

为了简化[原始伪操作](#raw-pseudo-operations)的使用，ksamd64 中定义了一组宏，可用于创建典型的过程序言和尾声。

|宏|描述|
|-|-|
|alloc_stack(n)|分配 n 个字节的堆栈帧（使用 `sub rsp, n`），并发出适当的展开信息（. allocstack n）|
|save_reg *reg*， *loc*|将非易失寄存器*reg*保存在堆栈上的*RSP 偏移位置*，并发出适当的展开信息。 （. savereg reg）|
|push_reg *reg*|在*堆栈上推送*非易失寄存器，并发出适当的展开信息。 （. pushreg reg）|
|rex_push_reg *reg*|使用2字节推送在堆栈上保存非易失性寄存器，并发出适当的展开信息（. pushreg reg）。  如果推送是函数中的第一个指令，则使用此宏，以确保函数是可修补的。|
|save_xmm128 *reg*， *loc*|将非易失性寄存器*reg*保存在堆栈上的*RSP 偏移位置*，并发出适当的展开信息（. savexmm128 reg，loc）|
|set_frame *reg*、 *offset*|将帧寄存器*reg*设置为 RSP +*偏移量*（使用 `mov`或 `lea`），并发出适当的展开信息（set_frame reg、offset）|
|push_eflags|将 eflags 与 `pushfq` 指令一起推送，并发出适当的展开信息（alloc_stack 8）|

下面是正确使用宏的示例函数 prolog：

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

## <a name="unwind-data-definitions-in-c"></a>C 中的展开数据定义

下面是展开数据的 C 说明：

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

## <a name="see-also"></a>另请参阅

[x64 软件约定](../build/x64-software-conventions.md)
