---
title: x64 异常处理
ms.date: 12/17/2018
helpviewer_keywords:
- C++ exception handling, x64
- exception handling, x64
ms.assetid: 41fecd2d-3717-4643-b21c-65dcd2f18c93
ms.openlocfilehash: 7dab7f3b6593bf4eaed1b8c804deb915677ccf5b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195200"
---
# <a name="x64-exception-handling"></a>x64 异常处理

结构化的异常处理的概述和C++编码约定和行为在 x64 上的异常处理。 异常处理的常规信息，请参阅[视觉对象中的异常处理C++ ](../cpp/exception-handling-in-visual-cpp.md)。

## <a name="unwind-data-for-exception-handling-debugger-support"></a>展开的异常处理，调试器支持的数据

多个数据结构所需的异常处理和调试支持。

### <a name="struct-runtimefunction"></a>RUNTIME_FUNCTION 结构

基于表的异常处理的分配堆栈空间或调用另一个函数 （例如，非叶函数） 的所有功能要求表条目。 函数表条目具有以下格式：

|||
|-|-|
|ULONG|函数起始地址|
|ULONG|函数结束地址|
|ULONG|展开信息地址|

Runtime_function 结构结构必须对齐在内存中的 DWORD。 所有地址都是相对的映像，也就是说，它们都是相对于包含函数表项的图像的起始地址的 32 位偏移量。 这些项排序，放入 PE32 + 映像的.pdata 部分。 对于动态生成的函数 [JIT 编译器]，运行时以支持这些函数必须使用 RtlInstallFunctionTableCallback 或 RtlAddFunctionTable 来向操作系统提供此信息。 如果不这样做将导致不可靠的异常处理和调试的进程。

### <a name="struct-unwindinfo"></a>UNWIND_INFO 结构

展开数据信息结构用于记录的函数有堆栈指针和非易失寄存器在堆栈上的保存位置的影响：

|||
|-|-|
|UBYTE:3|Version|
|UBYTE:5|Flags|
|UBYTE|序言的大小|
|UBYTE|展开代码的计数|
|UBYTE:4|帧寄存器|
|UBYTE:4|帧寄存器偏移量 （缩放）|
|USHORT \* n|展开代码数组|
|变量|可以是窗体的 （1） 或 （2） 下面|

（1） 异常处理程序

|||
|-|-|
|ULONG|异常处理程序的地址|
|变量|特定于语言的处理程序数据 （可选）|

（2） 链式展开信息

|||
|-|-|
|ULONG|函数起始地址|
|ULONG|函数结束地址|
|ULONG|展开信息地址|

UNWIND_INFO 结构必须对齐在内存中的 DWORD。 下面是每个字段的含义：

- **Version**

   展开数据，当前为 1 的版本号。

- **标记**

   当前定义三个标记：

   |Flag|描述|
   |-|-|
   |`UNW_FLAG_EHANDLER`| 该函数具有寻找需要检查异常的函数时，应调用的异常处理程序。|
   |`UNW_FLAG_UHANDLER`| 该函数具有展开异常时，应调用终止处理程序。|
   |`UNW_FLAG_CHAININFO`| 此展开信息结构不是主要的过程。 相反，连锁展开项是上一 runtime_function 结构项的内容的信息。 有关信息，请参阅[Chained 展开信息结构](#chained-unwind-info-structures)。 如果设置此标志，则必须清除 UNW_FLAG_EHANDLER 和 UNW_FLAG_UHANDLER 标志。 此外，框架注册和已修复堆栈分配字段必须具有相同的值如下所示主展开信息。|

- **序言的大小**

   函数序言中以字节为单位的长度。

- **展开代码的计数**

   展开代码数组中的槽数。 一些展开代码，例如，UWOP_SAVE_NONVOL，需要在数组中的多个槽。

- **帧寄存器**

   如果非零值，然后该函数使用帧指针 (FP)，并且该字段用作帧指针，使用相同的编码表示的操作信息字段的 unwind_code 结构节点的非易失性寄存器的数量。

- **框架注册偏移量 （缩放）**

   如果帧注册字段为非零值，此字段是从应用于 FP RSP 缩放偏移量建立时注册。 实际的 FP 寄存器设置为 RSP + 16\*此编号，允许从 0 到 240 之间的偏移量。 此偏移量允许指向到动态堆栈帧，允许更好的代码密度较短的指令 （详细说明可以使用 8 位有符号偏移量窗体） 通过本地堆栈分配的中间 FP 寄存器。

- **展开代码数组**

   说明了非易失性寄存器和 RSP 序言的效果的项数组。 请参阅 unwind_code 结构上的各个项的含义。 出于对齐目的，此数组始终具有偶数数目的条目，并最后一项是可能未使用。 在这种情况下，该数组是一个超过由展开代码字段的计数。

- **异常处理程序的地址**

   为函数的特定于语言的异常或终止处理程序，如果清除标志 UNW_FLAG_CHAININFO 且 UNW_FLAG_EHANDLER 或 UNW_FLAG_UHANDLER 的标志已设置相对于映像的指针。

- **特定于语言的处理程序的数据**

   函数的特定于语言的异常处理程序的数据。 此数据的格式是未指定，并完全由正在使用的特定异常处理程序。

- **链式展开信息**

   如果设置了标志 UNW_FLAG_CHAININFO UNWIND_INFO 结构以三个 UWORDs 结尾。  这些 UWORDs 表示该函数的 runtime_function 结构信息的链接展开。

### <a name="struct-unwindcode"></a>UNWIND_CODE 结构

展开代码数组用于会影响非易失寄存器和 RSP prolog 中记录的操作序列。 每个代码项目具有以下格式：

|||
|-|-|
|UBYTE|偏移量在 prolog|
|UBYTE:4|展开操作代码|
|UBYTE:4|操作信息|

数组是按降序排序顺序的 prolog 中的偏移量。

#### <a name="offset-in-prolog"></a>偏移量在 prolog

从执行此操作，再加 1 （即下, 一个指令开头的偏移量） 指令的末尾的 prolog 开头的偏移量。

#### <a name="unwind-operation-code"></a>展开操作代码

注意:某些操作代码需要本地堆栈帧中的值的无符号偏移量。 此偏移量为从一开始，即固定的堆栈分配的最小地址。 Unwind_info 结构中的框架注册字段为零，如果此偏移量是从 RSP。 如果帧注册字段不为零，这是从建立 FP 寄存器时 RSP 所在的位置的偏移量。 这等于减去 FP 寄存器偏移量的 FP 寄存器 (16\*框架的 unwind_info 结构中注册偏移量)。 如果使用 FP 寄存器，则任何采用某一偏移量的展开代码必须仅使用 FP 寄存器建立在序言中之后。

对于除以外的所有操作码`UWOP_SAVE_XMM128`和`UWOP_SAVE_XMM128_FAR`、 偏移量始终是 8 的倍数，因为所有 stack 感兴趣的值将存储在 （堆栈本身始终是对齐的 16 字节） 的 8 字节边界上。 对于采用短偏移量 (不超过 512 K) 的操作码，此代码的节点中最终 USHORT 保存除以 8 的偏移量。 对于采用长时间的偏移量的操作代码 (512 K < = < 4 GB 的偏移量)，此代码的最后两个 USHORT 节点 （在 little-endian 格式） 保留偏移量。

有关操作码`UWOP_SAVE_XMM128`和`UWOP_SAVE_XMM128_FAR`，偏移量始终是为 16，倍数，因为所有的 128 位 XMM 操作必须发生在 16 字节对齐的内存。 因此，用于为 16 的比例因子`UWOP_SAVE_XMM128`，允许不超过 1 百万的偏移量。

展开操作代码是下列值之一：

- `UWOP_PUSH_NONVOL` (0) 1 个节点

  推送一个非易失性的整数寄存器，减少 RSP 由 8。 操作信息是寄存器的数量。 由于在 epilog，约束`UWOP_PUSH_NONVOL`展开代码必须首先出现在序言中，并相应地，最后一个展开代码数组中。 此相对顺序适用于除之外的所有其他展开代码`UWOP_PUSH_MACHFRAME`。

- `UWOP_ALLOC_LARGE` （1) 2 或 3 个节点

  分配大型大小的区域，在堆栈上。 有两种形式。 如果操作信息等于 0，则除以分配的大小 8 记录中的下一个段，允许最多 512 个 K-8 的分配。 如果操作信息等于 1，则在 little-endian 格式，从而允许分配的下两个槽中记录不成比例分配的大小最大 4 GB-8。

- `UWOP_ALLOC_SMALL` （2) 1 个节点

  分配在堆栈上的小型区域。 分配的大小是操作信息字段\*8 + 8，允许从 8 到 128 个字节的分配。

  堆栈分配的展开代码应始终使用最短的编码：

  |**分配大小**|**展开代码**|
  |-|-|
  |8 到 128 个字节|`UWOP_ALLOC_SMALL`|
  |第 136 到 512 K-8 个字节|`UWOP_ALLOC_LARGE`操作信息 = 0|
  |512k 到 4 G-8 个字节|`UWOP_ALLOC_LARGE`操作信息 = 1|

- `UWOP_SET_FPREG` （3) 1 个节点

  通过将注册设置当前 RSP 的某个偏移量为建立的帧指针寄存器。 偏移量等于 unwind_info 结构中的帧注册的偏移量 （缩放） 字段\*16，允许从 0 到 240 之间的偏移量。 偏移量的使用允许建立指向固定的堆栈分配，要使用短指令格式的更多权限，从而帮助代码密度中间的帧指针。 操作信息字段被保留，因此不应。

- `UWOP_SAVE_NONVOL` （4） 2 个节点

  将非易失性整数寄存器保存使用 MOV 而不推送到堆栈上。 此代码主要用于*紧缩*、 非易失寄存器保存到位于以前分配的某个位置堆栈的位置。 操作信息是寄存器的数量。 在下一步中记录缩放由 8 堆栈偏移量的展开操作码槽，如上面的说明中所述。

- `UWOP_SAVE_NONVOL_FAR` （5） 3 个节点

  将非易失性整数寄存器保存具有长时间的偏移量，而不推送使用 MOV 在堆栈上。 此代码主要用于*紧缩*、 非易失寄存器保存到位于以前分配的某个位置堆栈的位置。 操作信息是寄存器的数量。 在下一步中记录不成比例的堆栈偏移量的两个展开操作代码槽，如上面的说明中所述。

- `UWOP_SAVE_XMM128` （8） 2 个节点

  将所有的 128 位的非易失 XMM 寄存器保存在堆栈上。 操作信息是寄存器的数量。 缩放 × 16 堆栈偏移量的记录中的下一个段。

- `UWOP_SAVE_XMM128_FAR` （9） 3 个节点

  将所有的 128 位的非易失 XMM 寄存器保存具有长时间的偏移量在堆栈上。 操作信息是寄存器的数量。 不成比例的堆栈偏移量的记录在接下来两个槽中。

- `UWOP_PUSH_MACHFRAME` （10) 1 个节点

  推送机帧。  这用于记录硬件中断或异常的影响。 有两种形式。 如果操作信息等于 0，已在堆栈上推送这些帧之一：

  |||
  |-|-|
  |RSP+32|SS|
  |RSP+24|旧 RSP|
  |RSP+16|EFLAGS|
  |RSP+8|CS|
  |RSP|RIP|

  如果操作信息等于 1，然后这些帧之一已推送：

  |||
  |-|-|
  |RSP+40|SS|
  |RSP+32|旧 RSP|
  |RSP+24|EFLAGS|
  |RSP+16|CS|
  |RSP+8|RIP|
  |RSP|错误代码|

  此展开代码始终出现在伪序言中，其永远不会实际执行，但改为出现在之前的真正入口点的一个中断例程，并存在只是为了提供一个位置来模拟计算机帧的推送。 `UWOP_PUSH_MACHFRAME` 记录该模拟，指示计算机已从概念上讲中完成此操作：

  1. RIP 寄信人地址从顶部到堆栈中弹出*Temp*
  
  1. 推送 SS

  1. 推送旧 RSP

  1. 推送 EFLAGS

  1. 推送 CS

  1. 推送*Temp*

  1. 推送错误代码 （如果操作信息等于 1）

  模拟`UWOP_PUSH_MACHFRAME`操作递减 RSP 由 40 （op 信息等于 0） 或 48 （操作信息等于 1）。

#### <a name="operation-info"></a>操作信息

操作信息位的含义取决于在操作代码。 若要编码常规用途 （整数） 注册，请使用此映射：

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
|8 到 15|到 R15 R8|

### <a name="chained-unwind-info-structures"></a>链式展开信息结构

如果设置 UNW_FLAG_CHAININFO 标志，则展开信息结构是一个辅助和共享的异常处理程序/链接在一起的信息地址字段包含主展开信息。 此示例代码会检索主展开的信息，前提假设`unwindInfo`是结构，它具有 UNW_FLAG_CHAININFO 标志设置。

```cpp
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

链接的信息是在两种情况下很有用。 首先，它可以用于非连续的代码段。 通过使用链接的信息，可以减少需要的展开信息的大小，因为您不需要重复主展开信息中的展开代码数组。

此外可以使用链接的信息进行分组易失寄存器保存。 编译器可能会延迟保存一些易失寄存器，直至这不在函数入口 prolog。 您可以通过主展开信息之前分组的代码，该函数的部分记录这，然后设置链式与序言中，其中链接信息中的展开代码反映非易失性寄存器的保存的非零大小的信息。 在这种情况下，展开代码是 UWOP_SAVE_NONVOL 的所有实例。 不支持的分组，它将非易失寄存器保存通过使用请求或使用其他固定的堆栈分配修改 RSP 注册。

Unwind_info 结构项具有 UNW_FLAG_CHAININFO 集可以包含其 unwind_info 结构的项也具有 UNW_FLAG_CHAININFO 设置，一个 runtime_function 结构有时称为*多个紧缩*。 最终，链式展开信息指针到达具有 UNW_FLAG_CHAININFO 清除; unwind_info 结构项这是主 unwind_info 结构项目，指向实际过程入口点。

## <a name="unwind-procedure"></a>展开过程

展开代码数组按降序排列。 异常发生时，上下文记录中的操作系统存储完整的上下文。 然后调用异常调度逻辑，它将重复执行这些步骤以查找异常处理程序：

1. 使用存储在上下文记录当前 RIP 搜索 runtime_function 结构表条目描述当前函数 （或函数部分时，连锁 unwind_info 结构条目）。

1. 如果未找到函数表条目，则在叶函数中，以及 RSP 直接处理返回的指针。 [RSP] 处的返回指针存储在更新后的上下文中，模拟的 RSP 加 8，并且重复步骤 1。

1. 如果找到函数表条目，则可以在三个区域内位于 RIP: a） 在 epilog、 b） 在序言中，或 c） 可能受异常处理程序的代码中。

   - 大小写) 如果 RIP 在 epilog 中，则控件正在退出函数，可能没有与此函数中，此异常关联的异常处理程序并且必须继续执行的 epilog 影响来计算调用方函数的上下文。 若要确定 RIP 是否在 epilog 中，从 RIP 代码流上检查。 如果可以与合法 epilog 的尾部匹配该代码流，则在 epilog 中，并且模拟的 epilog 的剩余部分，使用更新为每个指令的上下文记录进行处理。 在此之后，重复步骤 1。

   - 案例 b） 如果 RIP 内序言，则控件不具有进入函数可以有任何与此函数中，此异常关联的异常处理程序，必须撤消序言的效果，以便计算调用方函数的上下文。 RIP 位于序言中，如果从函数开始进行翻录的距离小于或等于 prolog 大小展开信息进行编码。 序言的效果是展开前扫描通过的偏移量小于或等于从函数开始翻录的偏移量的第一项的展开代码数组然后撤消展开代码数组中的所有剩余项的效果。 然后重复步骤 1。

   - 案例 c) 如果 RIP 不在 prolog 或 epilog 和函数内具有 （设置 UNW_FLAG_EHANDLER） 异常处理程序，则会调用特定于语言的处理程序。 该处理程序扫描其数据，并调用筛选器作为相应的函数。 异常已得到处理或搜索将可继续运行，可以返回特定于语言的处理程序。 它还可以直接启动展开代码。

1. 如果特定于语言的处理程序返回处理的状态，则继续执行使用原始上下文记录。

1. 如果没有特定于语言的处理程序或处理程序返回"继续搜索"状态，则上下文记录必须展开到调用方的状态。 这是通过所有撤消的每个效果的展开代码数组元素的处理实现的。 然后重复步骤 1。

链式展开信息所涉及，仍然遵循以下基本步骤。 唯一的区别是，要展开序言的效果，一旦达到数组末尾的展开代码数组的每个步骤，它被链接到父展开信息而遍历整个展开代码数组可在此处找到。 此链接将继续，直到到达而无需 UNW_CHAINED_INFO 标志中，展开信息问题，然后完成其展开代码数组的每个步骤。

最小集展开数据为 8 个字节。 这表示仅分配 128 个字节的堆栈或更低，并可能保存了一个非易失寄存器的函数。 这也是大小的链式展开信息结构与未展开代码长度为零的 prolog。

## <a name="language-specific-handler"></a>特定于语言的处理程序

只要设置了标志 UNW_FLAG_EHANDLER 或 UNW_FLAG_UHANDLER 特定于语言的处理程序的相对地址 unwind_info 结构中存在。 如前一部分中所述，搜索异常处理程序的一部分或作为展开代码的一部分调用的特定于语言的处理程序。 它具有以下原型：

```cpp
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**ExceptionRecord**提供一个指向具有标准 Win64 定义的异常记录。

**EstablisherFrame**是此函数的固定的堆栈分配的基本地址。

**ContextRecord**指向 （中异常处理程序的情况下） 引发了异常的时间或当前的异常上下文"展开"（在终止处理程序示例） 的上下文。

**DispatcherContext**指向此函数的调度程序上下文。 它具有此定义：

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

**ControlPc**是 RIP 中此函数的值。 此值为异常地址或控制这将建立函数保留的地址。 RIP 用于确定控件是否在某一受保护构造中此函数，例如，`__try`阻塞`__try` / `__except`或`__try` / `__finally`。

**ImageBase**是映像基映像 （加载地址） 包含此函数中，将添加到函数入口中使用的 32 位偏移量和展开以记录相对地址的信息的模块。

**函数项进行**提供一个指向 runtime_function 结构指针的函数保存该函数的入口和展开此函数的信息基于映像的相对地址。

**EstablisherFrame**是此函数的固定的堆栈分配的基本地址。

**TargetIp**提供了指定展开的继续符地址的可选指令地址。 如果此地址将被忽略**EstablisherFrame**未指定。

**ContextRecord**指向异常上下文，以供系统异常展开调度/代码。

**LanguageHandler**指向被调用的特定于语言的语言处理程序例程。

**HandlerData**指向此函数的特定于语言的处理程序数据。

## <a name="unwind-helpers-for-masm"></a>MASM 的展开帮助器

若要编写正确的程序集例程，是一组可以与实际的程序集说明用于创建相应的.pdata 和.xdata 的伪操作。 有一组提供的宏也简化其最常见的用途的伪操作使用。

### <a name="raw-pseudo-operations"></a>原始伪操作

|伪操作|描述|
|-|-|
|PROC 帧\[:*ehandler*]|原因 MASM 来生成函数表条目中的.pdata 和展开.xdata 中的信息的函数的结构化异常处理展开行为。  如果*ehandler*存在，则此过程中为特定于语言的处理程序.xdata 输入。<br /><br /> 当使用帧属性时，它必须后接。ENDPROLOG 指令。  如果该函数是叶函数 (如中所定义[函数类型](../build/stack-usage.md#function-types)) 帧属性是不必要的因为这些伪操作的剩余部分。|
|.PUSHREG *register*|生成使用当前偏移量在序言中指定的寄存器号 UWOP_PUSH_NONVOL 展开代码项。<br /><br /> 这应仅用于非易失性整数寄存器。  对于推送易失寄存器的内容，请使用。ALLOCSTACK 8 改为|
|.SETFRAME*注册*，*偏移量*|填写在帧中使用指定的寄存器和偏移量的展开信息寄存器字段和偏移量。 偏移量必须为 16 的倍数且小于或等于 240。 此指令还会生成使用当前的序言偏移量的指定寄存器 UWOP_SET_FPREG 展开代码项。|
|.ALLOCSTACK*大小*|在序言中生成 UWOP_ALLOC_SMALL 或 UWOP_ALLOC_LARGE 与当前的偏移量为指定的大小。<br /><br /> *大小*操作数必须是 8 的倍数。|
|.SAVEREG*注册*，*偏移量*|生成 UWOP_SAVE_NONVOL 或指定的注册和使用当前的序言偏移的偏移量的 UWOP_SAVE_NONVOL_FAR 展开代码项。 MASM 选择最有效的编码。<br /><br /> *偏移量*必须为正数，且为 8 的倍数。 *偏移量*相对于基过程的框架，它通常位于 RSP，或者，如果使用帧指针，不成比例的帧指针。|
|.SAVEXMM128*注册*，*偏移量*|生成 UWOP_SAVE_XMM128 或指定的 XMM 寄存器和使用当前的序言偏移的偏移量的 UWOP_SAVE_XMM128_FAR 展开代码项。 MASM 选择最有效的编码。<br /><br /> *偏移量*必须为正数，且 16 的倍数。  *偏移量*相对于基过程的框架，它通常位于 RSP，或者，如果使用帧指针，不成比例的帧指针。|
|.PUSHFRAME \[*code*]|生成 UWOP_PUSH_MACHFRAME 展开代码项。 如果可选*代码*指定，则展开代码项提供的修饰符为 1。 否则修饰符为 0。|
|.ENDPROLOG|表示结束的序言声明。  必须在函数的第一个 255 字节中。|

下面是示例函数 prolog 与大部分操作码的正确用法：

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
; if we didn’t have a frame pointer, this would be illegal
; if we didn’t make this modification,
; there would be no need for a frame pointer

    sub rsp, 060h

; we can unwind from the next AV because of the frame pointer

    mov rax, 0
    mov rax, [rax] ; AV!

; restore the registers that weren’t saved with a push
; this isn’t part of the official epilog, as described in section 2.5

    movdqa xmm7, [rbp]
    mov rsi, [rbp+018h]
    mov rdi, [rbp-010h]

; Here’s the official epilog

    lea rsp, [rbp-020h]
    pop rbp
    ret
sample ENDP
```

### <a name="masm-macros"></a>MASM 宏

为了简化使用[原始伪操作](#raw-pseudo-operations)，还有一组在 ksamd64.inc，可以用于创建典型的过程序言和尾声中定义的宏。

|宏|描述|
|-|-|
|alloc_stack(n)|分配的 n 个字节的堆栈帧 (使用`sub rsp, n`)，并发出相应的展开信息 (.allocstack n)|
|save_reg *reg*， *loc*|将非易失寄存器保存*reg* RSP 在堆栈上偏移量*loc*，并发出相应的展开信息。 (.savereg reg，loc)|
|push_reg *reg*|推送非易失寄存器*reg*在堆栈上，并发出相应的展开信息。 (.pushreg reg)|
|rex_push_reg *reg*|将非易失寄存器保存使用 2 字节推送到堆栈，并发出相应展开函数中的第一个指令，以确保函数是可热修补推送是否应使用此信息 (.pushreg reg)。|
|save_xmm128 *reg*， *loc*|将保存非易失性 XMM 寄存器*reg* RSP 在堆栈上偏移量*loc*，并发出相应的展开 （.savexmm128 reg，loc） 的信息|
|set_frame *reg*，*偏移量*|设置帧寄存器*reg*为 RSP +*偏移量*(使用`mov`，或`lea`)，并发出相应的展开 （.set_frame reg，偏移量） 的信息|
|push_eflags|推送与 eflags`pushfq`指令，并发出相应的展开信息 (.alloc_stack 8)|

下面是示例函数 prolog 使用宏的正确用法：

```MASM
SkFrame struct
    Fill    dq ?; fill to 8 mod 16
    SavedRdi dq ?; saved register RDI
    SavedRsi dq ?; saved register RSI
SkFrame ends

sampleFrame struct
    Filldq?; fill to 8 mod 16
    SavedRdidq?; Saved Register RDI
    SavedRsi  dq?; Saved Register RSI
sampleFrame ends

sample2 PROC FRAME
    alloc_stack(sizeof sampleFrame)
    save_reg rdi, sampleFrame.SavedRdi
    save_reg rsi, sampleFrame.SavedRsi
    .end_prolog

; function body

    mov rsi, sampleFrame.SavedRsi[rsp]
    mov rdi, sampleFrame.SavedRdi[rsp]

; Here’s the official epilog

    add rsp, (sizeof sampleFrame)
    ret
sample2 ENDP
```

## <a name="unwind-data-definitions-in-c"></a>展开 C 中的数据定义

以下是 C 说明的展开数据：

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
