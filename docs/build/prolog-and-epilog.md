---
title: "保护现场和恢复现场 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 保护现场和恢复现场
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每个分配堆栈空间、调用其他函数、保存非易失寄存器或使用异常处理的函数必须具有 Prolog，Prolog 的地址限制在与各自的函数表项关联的展开数据中予以说明（请参见 [异常处理 \(x64\)](../build/exception-handling-x64.md)）。  Prolog 将执行以下操作：必要时将参数寄存器保存在其内部地址中；将非易失寄存器推入堆栈；为局部变量和临时变量分配堆栈的固定部分；（可选）建立帧指针。  关联的展开数据必须描述 Prolog 的操作，必须提供撤消 Prolog 代码的影响所需的信息。  
  
 如果堆栈中的固定分配超过一页（即大于 4096 字节），则该堆栈分配的范围可能超过一个虚拟内存页，因此在实际分配之前必须检查分配情况。  为此，提供了一个特殊的例程，该例程可从 Prolog 调用，并且不会损坏任何参数寄存器。  
  
 保存非易失寄存器的首选方法是：在进行固定堆栈分配之前将这些寄存器移入堆栈。  如果在保存非易失寄存器之前执行了固定堆栈分配，则很可能需要 32 位位移以便对保存的寄存器区域进行寻址（据说寄存器的压栈操作与移动操作一样快，并且在可预见的未来一段时间内都应该是这样，尽管压栈操作之间存在隐含的相关性）。  可按任何顺序保存非易失寄存器。  但是，在 Prolog 中第一次使用非易失寄存器时必须对其进行保存。  
  
 典型的 Prolog 代码可以为：  
  
```  
mov       [RSP + 8], RCX  
push   R15  
push   R14  
push   R13  
sub      RSP, fixed-allocation-size  
lea      R13, 128[RSP]  
...  
```  
  
 此 Prolog 执行以下操作：将参数寄存器 RCX 存储在其标识位置；保存非易失寄存器 R13、R14、R15；分配堆栈帧的固定部分；建立帧指针，该指针将 128 字节地址指向固定分配区域。  使用偏移量以后，便可以通过单字节偏移量对多个固定分配区域进行寻址。  
  
 如果固定分配大小大于或等于一页内存，则在修改 RSP 之前必须调用 helper 函数。  此 \_\_chkstk helper 函数负责探测待分配的堆栈范围，以确保对堆栈进行正确的扩展。  在这种情况下，前面的 Prolog 示例应变为：  
  
```  
mov       [RSP + 8], RCX  
push   R15  
push   R14  
push   R13  
mov      RAX,  fixed-allocation-size  
call   __chkstk  
sub      RSP, RAX  
lea      R13, 128[RSP]  
...  
```  
  
 除了 R10、R11 和条件代码以外，此 \_\_chkstk helper 函数不会修改任何寄存器。  特别是，此函数将返回未更改的 RAX，并且不会修改所有非易失寄存器和参数传递寄存器。  
  
 Epilog 代码位于函数的每个出口。  通常只有一个 Prolog，但可以有多个 Epilog。  Epilog 代码执行以下操作：必要时将堆栈修整为其固定分配大小；释放固定堆栈分配；从堆栈中弹出非易失寄存器的保存值以还原这些寄存器；返回。  
  
 对于展开代码，Epilog 代码必须遵守一组严格的规则，以便通过异常和中断进行可靠的展开。  这样可以减少所需的展开数据量，因为描述每个 Epilog 不需要额外数据。  通过向前扫描整个代码流以标识 Epilog，展开代码可以确定 Epilog 正在执行。  
  
 如果函数中没有使用任何帧指针，则 Epilog 必须首先释放堆栈的固定部分，弹出非易失寄存器，然后将控制返回调用函数。  例如，  
  
```  
add      RSP, fixed-allocation-size  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 如果函数中使用了帧指针，则在执行 Epilog 之前必须将堆栈修整为其固定分配。  这在技术上不属于 Epilog。  例如，下面的 Epilog 可用于撤消前面使用的 Prolog：  
  
```  
lea      RSP, -128[R13]  
; epilogue proper starts here  
add      RSP, fixed-allocation-size  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 在实际应用中，使用帧指针时，没有必要分两个步骤调整 RSP，因此应改用以下 Epilog：  
  
```  
lea      RSP, fixed-allocation-size – 128[R13]  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 以上是 Epilog 的唯一合法形式。  它必须由 `add RSP,constant` 或 `lea RSP,constant[FPReg]` 组成，后跟一系列零或多个 8 字节寄存器 pop、一个 return 或一个 jmp。  （Epilog 中只允许 jmp 语句的子集。  仅限于具有 ModRM 内存引用的 jmp 类，其中 ModRM mod 字段值为 00。  在 ModRM mod 字段值为 01 或 10 的 Epilog 中禁止使用 jmp。  有关允许使用的 ModRM 引用的更多信息，请参见“AMD x86\-64 Architecture Programmer’s Manual Volume 3: General Purpose and System Instructions”（AMD x86\-64 结构程序员手册第 3 卷：通用指令和系统指令）中的表 A\-15。）  不能出现其他代码。  特别是，不能在 Epilog 内进行调度，包括加载返回值。  
  
 请注意，未使用帧指针时，Epilog 必须使用 `add RSP,constant` 释放堆栈的固定部分，  而不能使用 `lea RSP,constant[RSP]`。  由于此限制，在搜索 Epilog 时展开代码具有较少的识别模式。  
  
 通过遵守这些规则，展开代码便可以确定某个 Epilog 当前正在执行，并可以模拟该 Epilog 其余部分的执行，从而允许重新创建调用函数的上下文。  
  
## 请参阅  
 [x64 软件约定](../build/x64-software-conventions.md)