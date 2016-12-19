---
title: "UNWIND_CODE 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 104955d8-7e33-4c5a-b0c6-3254648f0af3
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# UNWIND_CODE 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

展开代码数组用于记录影响非易失寄存器和 RSP 的 Prolog 中的操作序列。  每个代码项均具有以下格式：  
  
|||  
|-|-|  
|UBYTE|Prolog 中的偏移量|  
|UBYTE: 4|展开操作码|  
|UBYTE: 4|操作信息|  
  
 按 Prolog 中偏移量的降序对数组进行排序。  
  
 **Prolog 中的偏移量**  
 距执行此操作的指令末尾的 Prolog 开始处的偏移量加 1（即下一指令开始的偏移量）。  
  
 **展开操作码**  
 注意：某些操作码需要本机堆栈帧中值的无符号偏移量。  此偏移量从固定堆栈分配开始处（最低地址）开始。  如果 UNWIND\_INFO 中的帧寄存器字段为 0，则此偏移量从 RSP 开始。  如果帧寄存器字段不为 0，则该字段值就是建立 FP reg 时距 RSP 所在位置的偏移量，  它等于 FP reg 减去 FP reg 偏移量（16 \* UNWIND\_INFO 中成比例的帧寄存器偏移量）。  如果使用了 FP reg，则采用偏移量的任何展开代码只能在 Prolog 中建立了 FP reg 之后才能使用。  
  
 对于所有操作码（UWOP\_SAVE\_XMM128 和 UWOP\_SAVE\_XMM128\_FAR 除外），由于全部有意义的堆栈值都存储在 8 字节边界上（堆栈本身始终是 16 字节对齐的），因此，偏移量通常是 8 的倍数。  对于采用短偏移量（小于 512K）的操作码，此代码的节点中最后一个 USHORT 保存除以 8 所得的偏移量；  对于采用长偏移量（512K \<\= 偏移量 \< 4GB）的操作码，此代码的最后两个 USHORT 节点保存该偏移量（采用 Little\-Endian 格式）。  
  
 对于操作码 UWOP\_SAVE\_XMM128 和 UWOP\_SAVE\_XMM128\_FAR，由于所有 128 位 XMM 操作必须在 16 字节对齐的内存中进行，因此，偏移量通常是 16 的倍数。  因于是，对 UWOP\_SAVE\_XMM128 使用的比例因子为 16，允许偏移量小于 1M。  
  
 展开操作码为下列代码中的一个：  
  
 UWOP\_PUSH\_NONVOL \(0\)1 个节点  
  
 将一个非易失的整数寄存器推入堆栈，并将 RSP 减去 8。  操作信息是寄存器的编号。  请注意，由于 Epilog 的约束，UWOP\_PUSH\_NONVOL 展开代码必须首先出现在 Prolog 中，并且相应地出现在展开代码数组的最后。  这种相对顺序适用于 UWOP\_PUSH\_MACHFRAME 以外的所有其他展开代码。  
  
 UWOP\_ALLOC\_LARGE \(1\)2 或 3 个节点  
  
 在堆栈上分配一个大区域，  具体形式有两种。  如果操作信息等于 0，则将分配大小除以 8 记录在下一个槽中，允许的最大可分配范围为 512K – 8；  如果操作信息等于 1，则在下两个槽中以 Little\-Endian 格式记录不成比例的分配大小，允许的最大可分配范围为 4GB – 8。  
  
 UWOP\_ALLOC\_SMALL \(2\)1 个节点  
  
 在堆栈上分配一个小区域。  分配大小等于操作信息字段 \* 8 \+ 8，允许的分配范围在 8 到 128 字节之间。  
  
 堆栈分配的展开代码通常应使用尽可能短的编码：  
  
|||  
|-|-|  
|**分配大小**|**展开代码**|  
|8 到 128 字节|UWOP\_ALLOC\_SMALL|  
|136 到 512K\-8 字节|UWOP\_ALLOC\_LARGE，操作信息 \= 0|  
|512K 到 4G–8 字节|UWOP\_ALLOC\_LARGE，操作信息 \= 1|  
  
 UWOP\_SET\_FPREG \(3\)1 个节点  
  
 将寄存器设置为当前 RSP 的某个偏移量，从而建立帧指针寄存器。  偏移量等于 UNWIND\_INFO \* 16 中的帧寄存器偏移量（成比例的）字段，允许偏移量范围在 0 到 240 之间。  使用偏移量可以建立一个指向固定堆栈分配中部的帧指针，允许更多地使用短指令格式进行访问，从而有助于增加代码密度。  请注意，操作信息字段为保留字段，不应使用该字段。  
  
 UWOP\_SAVE\_NONVOL \(4\)2 个节点  
  
 使用 MOV 而不是 PUSH 在堆栈中保存非易失的整数寄存器。  这主要用于紧缩套装，此时将非易失寄存器保存到以前分配的堆栈位置中。  操作信息是寄存器的编号。  堆栈偏移量（8 的倍数）记录在下一个展开操作码槽中，如以上的注意事项中所述。  
  
 UWOP\_SAVE\_NONVOL\_FAR \(5\)3 个节点  
  
 使用 MOV 而不是 PUSH 在具有长偏移量的堆栈中保存非易失的整数寄存器。  这主要用于紧缩套装，此时将非易失寄存器保存到以前分配的堆栈位置中。  操作信息是寄存器的编号。  不成比例的堆栈偏移量记录在下两个展开操作码槽中，如以上的注意事项中所述。  
  
 UWOP\_SAVE\_XMM128 \(8\)2 个节点  
  
 在堆栈中保存非易失 XMM 寄存器的所有 128 位。  操作信息是寄存器的编号。  堆栈偏移量（16 的倍数）记录在下一个槽中。  
  
 UWOP\_SAVE\_XMM128\_FAR \(9\)3 个节点  
  
 在具有长偏移量的堆栈中保存非易失 XMM 寄存器的所有 128 位。  操作信息是寄存器的编号。  不成比例的堆栈偏移量记录在下两个槽中。  
  
 UWOP\_PUSH\_MACHFRAME \(10\)1 个节点  
  
 将计算机帧推入堆栈，  这是用来记录硬件中断或异常的影响。  具体形式有两种。  如果操作信息等于 0，则将以下内容推入堆栈：  
  
|||  
|-|-|  
|RSP\+32|SS|  
|RSP\+24|旧 RSP|  
|RSP\+16|EFLAGS|  
|RSP\+8|CS|  
|RSP|RIP|  
  
 如果操作信息等于 1，则将以下内容推入堆栈：  
  
|||  
|-|-|  
|RSP\+40|SS|  
|RSP\+32|旧 RSP|  
|RSP\+24|EFLAGS|  
|RSP\+16|CS|  
|RSP\+8|RIP|  
|RSP|错误代码|  
  
 此展开代码通常出现在虚拟 Prolog 中，虚拟 Prolog 实际上从不执行，但它出现在中断例程的真正入口点之前，只是提供一个位置用于模拟计算机帧的压栈。  UWOP\_PUSH\_MACHFRAME 记录这一模拟，指示计算机已完成（从理论上说）以下操作：  
  
 从栈顶弹出 RIP 返回地址，放入 *Temp* 中  
  
 推入 SS  
  
 推入旧 RSP  
  
 推入 EFLAGS  
  
 推入 CS  
  
 推入 *Temp*  
  
 推入错误代码（如果操作信息等于 1）  
  
 模拟的 UWOP\_PUSH\_MACHFRAME 操作将 RSP 减去 40（操作信息等于 0）或 48（操作信息等于 1）。  
  
 **操作信息**  
 这 4 位的含义取决于操作码。  若要对常规用途（整数）寄存器进行编码，则使用以下映射：  
  
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
|8 到 15|R8 to R15|  
  
## 请参阅  
 [为异常处理和调试器支持展开数据](../build/unwind-data-for-exception-handling-debugger-support.md)