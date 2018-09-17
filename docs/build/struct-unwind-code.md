---
title: unwind_code 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 104955d8-7e33-4c5a-b0c6-3254648f0af3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1da6f078741c598099e71da9164f54b56da3f355
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726643"
---
# <a name="struct-unwindcode"></a>UNWIND_CODE 结构

展开代码数组用于会影响非易失寄存器和 RSP prolog 中记录的操作序列。 每个代码项的格式如下：

|||
|-|-|
|UBYTE|偏移量在 prolog|
|UBYTE: 4|展开操作代码|
|UBYTE: 4|操作信息|

数组是按降序排序顺序的 prolog 中的偏移量。

## <a name="offset-in-prolog"></a>偏移量在 prolog

从执行此操作，再加 1 （即下, 一个指令开头的偏移量） 指令的末尾的 prolog 开头的偏移量。

## <a name="unwind-operation-code"></a>展开操作代码

注意： 某些操作代码要求本地堆栈帧中的值的无符号偏移量。 此偏移量是从固定的堆栈分配 （最小地址） 开头。 Unwind_info 结构中的框架注册字段为零，如果此偏移量是从 RSP。 如果帧注册字段不为零，这是从建立 FP reg 时 RSP 所在的位置的偏移量。 这等于 FP reg 减去 FP reg 偏移量 (16\*框架的 unwind_info 结构中注册偏移量)。 如果使用 FP reg，则任何采用某一偏移量的展开代码必须仅使用 FP reg 建立在序言中之后。

对于除以外的所有操作码`UWOP_SAVE_XMM128`和`UWOP_SAVE_XMM128_FAR`，偏移量将始终为 8 的倍数，因为所有 stack 感兴趣的值存储在 （堆栈本身始终是对齐的 16 字节） 的 8 字节边界上。 对于采用短偏移量 (不超过 512 K) 的操作码，此代码的节点中最终 USHORT 保存除以 8 的偏移量。 对于采用长时间的偏移量的操作代码 (512 K < = < 4 GB 的偏移量)，此代码的最后两个 USHORT 节点 （在 little-endian 格式） 保留偏移量。

有关操作码`UWOP_SAVE_XMM128`和`UWOP_SAVE_XMM128_FAR`，偏移量始终是 16 的倍数，因为所有的 128 位 XMM 操作必须发生在 16 字节对齐的内存。 因此，用于为 16 的比例因子`UWOP_SAVE_XMM128`，允许不超过 1 百万的偏移量。

展开操作代码是以下值之一：

`UWOP_PUSH_NONVOL` (0) 1 个节点

推送一个非易失性的整数寄存器，减少 RSP 由 8。 操作信息是寄存器的数量。 请注意，由于在 epilog，约束`UWOP_PUSH_NONVOL`展开代码必须首先出现在序言中，并相应地，最后一个展开代码数组中。 此相对顺序适用于除之外的所有其他展开代码`UWOP_PUSH_MACHFRAME`。

`UWOP_ALLOC_LARGE` （1) 2 或 3 个节点

分配大型大小的区域，在堆栈上。 有两种形式。 如果操作信息等于 0，则除以分配的大小 8 记录中的下一个段，允许最多 512 个 K-8 的分配。 如果操作信息等于 1，则在 little-endian 格式，从而允许分配的下两个槽中记录不成比例分配的大小最大 4 GB-8。

`UWOP_ALLOC_SMALL` (2) 1 个节点

分配在堆栈上的小型区域。 分配的大小是操作信息字段\*8 + 8，允许从 8 到 128 个字节的分配。

堆栈分配的展开代码应始终使用最短的编码：

|**分配大小**|**展开代码**|
|-|-|
|8 到 128 个字节|`UWOP_ALLOC_SMALL`|
|第 136 到 512 K-8 个字节|`UWOP_ALLOC_LARGE`操作信息 = 0|
|512k 到 4 G-8 个字节|`UWOP_ALLOC_LARGE`操作信息 = 1|

`UWOP_SET_FPREG` （3) 1 个节点

通过将注册设置当前 RSP 的某个偏移量为建立的帧指针寄存器。 偏移量等于 unwind_info 结构中的帧注册的偏移量 （缩放） 字段\*16，允许从 0 到 240 之间的偏移量。 偏移量的使用允许建立指向固定的堆栈分配，要使用短指令格式的更多权限，从而帮助代码密度中间的帧指针。 请注意，操作信息字段被保留并且不应使用。

`UWOP_SAVE_NONVOL` （4） 2 个节点

将非易失性整数寄存器保存使用 MOV 而不推送到堆栈上。 这是主要用于紧缩套装，其中非易失寄存器保存到位于以前分配的某个位置堆栈。 操作信息是寄存器的数量。 在下一步中记录缩放由 8 堆栈偏移量的展开操作码槽，如上面的说明中所述。

`UWOP_SAVE_NONVOL_FAR` （5） 3 个节点

将非易失性整数寄存器保存具有长时间的偏移量，而不推送使用 MOV 在堆栈上。 这是主要用于紧缩套装，其中非易失寄存器保存到位于以前分配的某个位置堆栈。 操作信息是寄存器的数量。 在下一步中记录不成比例的堆栈偏移量的两个展开操作代码槽，如上面的说明中所述。

`UWOP_SAVE_XMM128` （8） 2 个节点

将所有的 128 位的非易失 XMM 寄存器保存在堆栈上。 操作信息是寄存器的数量。 缩放 × 16 堆栈偏移量的记录中的下一个段。

`UWOP_SAVE_XMM128_FAR` （9） 3 个节点

将所有的 128 位的非易失 XMM 寄存器保存具有长时间的偏移量在堆栈上。 操作信息是寄存器的数量。 不成比例的堆栈偏移量的记录在接下来两个槽中。

`UWOP_PUSH_MACHFRAME` （10) 1 个节点

推送机帧。  这用于记录硬件中断或异常的影响。 有两种形式。 如果操作信息等于 0，以下已推送到堆栈上：

|||
|-|-|
|RSP + 32|SS|
|RSP + 24|旧 RSP|
|RSP + 16|EFLAGS|
|RSP + 8|CS|
|RSP|RIP|

如果操作信息等于 1，则改为已推送以下：

|||
|-|-|
|RSP + 40|SS|
|RSP + 32|旧 RSP|
|RSP + 24|EFLAGS|
|RSP + 16|CS|
|RSP + 8|RIP|
|RSP|错误代码|

此展开代码将始终出现在伪序言中，其永远不会实际执行，但改为出现在之前的真正入口点的一个中断例程，并存在只是为了提供一个位置来模拟计算机帧的推送。 `UWOP_PUSH_MACHFRAME` 记录该模拟，指示计算机已从概念上讲完成下列活动：

1. RIP 寄信人地址从顶部到堆栈中弹出*Temp*

2. 推送 SS

3. 推送旧 RSP

4. 推送 EFLAGS

5. 推送 CS

6. 推送*Temp*

7. 推送错误代码 （如果操作信息等于 1）

模拟`UWOP_PUSH_MACHFRAME`操作递减 RSP 由 40 （op 信息等于 0） 或 48 （操作信息等于 1）。

## <a name="operation-info"></a>操作信息

这 4 位的含义取决于在操作代码。 若要编码常规用途 （整数） 注册，请使用以下映射：

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

## <a name="see-also"></a>请参阅

[为异常处理和调试器支持展开数据](../build/unwind-data-for-exception-handling-debugger-support.md)