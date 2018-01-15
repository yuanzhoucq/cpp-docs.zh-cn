---
title: "Prolog 和 Epilog |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 700b467065d17a61dcfabf9dcaa6577a7ecffc11
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="prolog-and-epilog"></a>保护现场和恢复现场
每个分配堆栈空间的函数，调用其他函数将保存非易失寄存器，或使用异常处理必须具有的 prolog 中的相应函数表项与关联的展开数据描述其地址限制 (请参阅[异常处理 (x64)](../build/exception-handling-x64.md))。 Prolog 将保存在其内部地址寄存器必要情况下，在堆栈上推送非易失寄存器的参数、 局部变量和临时变量，为分配堆栈的固定的部分和 （可选） 建立帧指针。 关联的展开数据必须描述序言的操作，必须提供必需撤消了 prolog 代码的作用的信息。  
  
 如果堆栈中的固定的分配是多个页 (即，大于 4096 个字节)，则堆栈分配无法跨越多个虚拟内存页，并且有可能，因此，分配必须实际分配之前检查。 出于此目的被提供特殊的例程，可从序言调用与这不会销毁任何参数寄存器。  
  
 保存非易失寄存器的首选的方法是将它们移到之前固定的堆栈分配堆栈。 如果固定的堆栈分配都已执行之前已保存的非易失性寄存器，则最有可能 32 位偏移量将地址需要保存注册区域 （据说，寄存器推送移动一样快并且应保留用于讲解可预见未来而不考虑推送之间的隐式依赖关系）。 可以按任意顺序保存非易失寄存器。 但是，在序言中非易失寄存器首次使用必须将其保存。  
  
 可能的典型 prolog 代码：  
  
```  
mov       [RSP + 8], RCX  
push   R15  
push   R14  
push   R13  
sub      RSP, fixed-allocation-size  
lea      R13, 128[RSP]  
...  
```  
  
 此 prolog 在其主位置中存储的参数寄存器 RCX、 保存非易失寄存器 R13 R15、 分配该堆栈帧的固定的部分和建立点到固定的分配区域的 128 个字节的帧指针。 使用偏移量允许多个固定的分配区域单字节偏移量进行寻址。  
  
 如果固定的分配大小大于或等于一页的内存，则必须修改 RSP 之前调用 helper 函数。 此帮助器，__chkstk，负责探测将要分配堆栈范围，以确保已正确展开堆栈。 在这种情况下，系统将改为到前面的 prolog 示例：  
  
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
  
 __Chkstk 帮助程序将不会修改任何寄存器 R10、 R11、 和的条件代码以外。 具体而言，它将返回 RAX 保持不变，并保留所有非易失寄存器和自变量传递寄存器不做任何修改。  
  
 在每个退出时的函数存在 epilog 代码。 尽管通常只有一个 prolog，但是可以有许多 epilog。 Epilog 代码将堆栈修整为其固定的分配大小 （如果有必要）、 释放固定的堆栈分配、 通过弹出堆栈上，从其已保存的值还原非易失寄存器和返回。  
  
 Epilog 代码必须可靠地通过异常和中断的展开到遵循一组严格的规则的展开代码。 这可减少的数量展开所需，数据，因为描述每个 epilog 所不需的任何额外数据。 相反的展开代码可以确定 epilog，正在执行的向前扫描整个来标识 epilog 代码流。  
  
 如果在中不使用任何帧指针函数，然后 epilog 必须首先释放堆栈的固定的部分、 弹出，非易失寄存器，和控件返回到调用的函数。 例如，应用于对象的  
  
```  
add      RSP, fixed-allocation-size  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 如果在函数中使用帧指针，则必须为其固定分配的 epilog 执行之前修整堆栈。 这是从技术上讲不属于 epilog。 例如，以下 epilog 无法用于撤消以前使用 prolog:  
  
```  
lea      RSP, -128[R13]  
; epilogue proper starts here  
add      RSP, fixed-allocation-size  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 在实践中，当使用帧指针时，没有在两个步骤中，调整 RSP，因此将改用以下 epilog 充分的理由：  
  
```  
lea      RSP, fixed-allocation-size - 128[R13]  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 这些是 epilog 的唯一合法窗体。 它必须包含其中任何`add RSP,constant`或`lea RSP,constant[FPReg]`后, 跟零个或多个 8 字节注册 pop 和退货或 jmp 一系列。 （仅 jmp 语句的子集是 epilog 中允许的。 这些 jmps ModRM 内存引用使用的以独占方式是类的，其中 ModRM mod 字段值 00。 禁止在使用 ModRM mod 字段值 01 或 10 epilog jmps 的使用。 请参阅表 A-15 AMD x86-64 体系结构程序员手动卷 3 中： 通用寄存器和系统的说明，有关详细信息允许 ModRM 引用。)。 没有其他代码可以出现。 具体而言，执行任何操作可以计划内 epilog，包括返回值的加载。  
  
 请注意，当不使用帧指针时，必须使用 epilog`add RSP,constant`以释放堆栈的固定的部分。 它可能不会使用`lea RSP,constant[RSP]`相反。 因此的展开代码具有较少的模式来识别在搜索 epilog 时存在此限制。  
  
 遵循这些规则，以确定当前正在执行 epilog 并模拟 epilog 以便重新创建的调用函数的上下文的剩余部分执行的展开代码。  
  
## <a name="see-also"></a>请参阅  
 [x64 软件约定](../build/x64-software-conventions.md)