---
title: "UNWIND_CODE 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 104955d8-7e33-4c5a-b0c6-3254648f0af3
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 76059ff24b46fd537db0c2670a30cf3f42ee2166
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="struct-unwindcode"></a>UNWIND_CODE 结构
展开代码数组用于在会影响非易失寄存器和 RSP prolog 中记录的操作序列。 每个代码项均具有以下格式：  
  
|||  
|-|-|  
|UBYTE|偏移量的 prolog|  
|UBYTE: 4|展开操作代码|  
|UBYTE: 4|操作信息|  
  
 对数组进行排序按降序顺序在序言中的偏移量。  
  
 **偏移量的 prolog**  
 从开始处结尾处执行此操作，加 1 （即下, 一条指令的起始偏移量） 指令的 prolog 偏移量。  
  
 **展开操作代码**  
 注意： 某些操作码需要本地堆栈帧中的值的无符号偏移量。 此偏移量是从固定的堆栈分配的开头 （最低地址）。 Unwind_info 结构中的帧注册字段为零，如果此偏移量是从 RSP。 如果框架注册字段不为零，这是从建立 FP reg 时 RSP 所在的位置的偏移量。 这等于 FP reg 减去 FP reg 偏移量 (16 * 缩放后的帧在 unwind_info 结构中注册偏移量)。 如果使用 FP reg，则任何的展开代码，采用偏移量必须仅使用后 FP reg 建立在序言中。  
  
 对于除 UWOP_SAVE_XMM128 和 UWOP_SAVE_XMM128_FAR 以外的所有操作码，偏移量将始终为 8 的倍数，因为感兴趣的所有堆栈值都存储在 （堆栈本身始终为 16 字节对齐） 的 8 字节边界上。 有关采用短偏移量 (小于 512 K) 的操作代码，最后一个 USHORT 此代码的节点中保存的偏移量除以 8。 采用长的偏移量的操作代码 (512k < = 偏移量 < 4 GB)，此代码的最后两个 USHORT 节点保存偏移量 （以 little-endian 格式）。  
  
 对于 UWOP_SAVE_XMM128 和 UWOP_SAVE_XMM128_FAR 的操作码，偏移量将始终为 16 的倍数，因为所有的 128 位 XMM 操作必须出现在 16 字节对齐的内存。 因此，16 缩放比例用于 UWOP_SAVE_XMM128，允许不超过一百万的偏移量。  
  
 展开操作代码是以下项之一：  
  
 UWOP_PUSH_NONVOL (0) 1 个节点  
  
 将一个非易失性的整数寄存器，由 8 递减 RSP 推送。 操作信息是寄存器的数目。 请注意，由于上 epilog 约束，UWOP_PUSH_NONVOL 展开代码必须首先显示在序言中并相应地，最后一个展开代码数组中。 此相对顺序适用于除 UWOP_PUSH_MACHFRAME 之外的所有其他展开代码。  
  
 UWOP_ALLOC_LARGE (1) 2 或 3 节点  
  
 分配在堆栈上的大型区域。 有两种形式。 如果操作信息等于 0，则除以分配的大小 8 会记录在下一步的槽中，允许最多 512 个 K-8 分配。 如果操作信息等于 1，则分配的不成比例的大小记录在 little-endian 格式，允许分配中的下两个槽中最多 4 GB-8。  
  
 UWOP_ALLOC_SMALL (2) 1 个节点  
  
 分配在堆栈上的小型区域。 分配的大小是操作信息字段 * 8 + 8，允许从 8 到 128 个字节的分配。  
  
 堆栈分配的展开代码应始终使用最短的编码：  
  
|||  
|-|-|  
|**分配大小**|**展开代码**|  
|8 到 128 字节|UWOP_ALLOC_SMALL|  
|136 至 512 K-8 个字节|UWOP_ALLOC_LARGE，操作信息 = 0|  
|512k 到 4g-8 个字节|UWOP_ALLOC_LARGE，操作信息 = 1|  
  
 UWOP_SET_FPREG (3) 1 个节点  
  
 通过将寄存器设置为当前 RSP 的某个偏移量建立帧指针寄存器。 偏移量等于 unwind_info 结构中的帧寄存器的偏移量 （缩放） 字段 * 16，允许从 0 到 240 之间的偏移量。 将偏移量使用允许建立到固定的堆栈分配，通过允许使用短指令窗体的多个访问帮助代码密度的中间点的帧指针。 请注意，操作信息字段被保留，并且不应使用。  
  
 UWOP_SAVE_NONVOL (4) 2 个节点  
  
 将一个非易失性的整数寄存器保存使用 MOV 而不推送到堆栈上。 这主要用于紧缩套装，非易失寄存器保存为以前分配的位置的堆栈的位置。 操作信息是寄存器的数目。 在下一步中记录缩放由 8 堆栈偏移量的展开操作码槽中，如上面的说明中所述。  
  
 UWOP_SAVE_NONVOL_FAR (5) 3 个节点  
  
 将一个非易失性的整数寄存器保存长偏移量，而不推送使用 MOV 的堆栈上。 这主要用于紧缩套装，非易失寄存器保存为以前分配的位置的堆栈的位置。 操作信息是寄存器的数目。 在下一步中记录缩放的堆栈偏移量的两个展开操作代码槽，如上面的说明中所述。  
  
 UWOP_SAVE_XMM128 (8) 2 个节点  
  
 将所有 128 位的非易失 XMM 寄存器保存在堆栈上。 操作信息是寄存器的数目。 扩展由 16 堆栈偏移量的记录在下一步的槽中。  
  
 UWOP_SAVE_XMM128_FAR (9) 3 个节点  
  
 将所有 128 位的非易失 XMM 寄存器保存长偏移量的堆栈上。 操作信息是寄存器的数目。 无比例的堆栈偏移量的记录在下两个槽中。  
  
 UWOP_PUSH_MACHFRAME (10) 1 个节点  
  
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
  
 此的展开代码，将始终出现在 dummy 序言中，其永远不会实际执行，但改为出现之前中断例程的真正入口点并存在只是为了提供用来模拟计算机帧的推送的位置。 UWOP_PUSH_MACHFRAME 记录该模拟，该值指示计算机从概念上讲已完成以下：  
  
 RIP 寄信人地址从顶部到堆栈中弹出*Temp*  
  
 推送 SS  
  
 推送旧 RSP  
  
 推送 EFLAGS  
  
 推送 CS  
  
 推送*Temp*  
  
 （如果操作信息等于 1） 推入错误代码  
  
 通过 40 模拟的 UWOP_PUSH_MACHFRAME 操作递减 RSP （操作信息等于 0） 或 48 （操作信息等于 1）。  
  
 **操作信息**  
 这些 4 位的含义取决于操作代码。 若要编码通用 （整数） 注册，请使用以下映射：  
  
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