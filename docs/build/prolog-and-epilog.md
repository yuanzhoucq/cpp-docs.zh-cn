---
title: Prolog 和 Epilog |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c2a1a9b1891af1c5616e78932cf4a530a300786
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718869"
---
# <a name="prolog-and-epilog"></a>保护现场和恢复现场

分配堆栈空间的每个函数，调用其他函数中，将非易失寄存器保存或使用异常处理必须具有与相应函数表条目相关联的展开数据中所述的地址限制 prolog (请参阅[异常处理 (x64)](../build/exception-handling-x64.md))。 在 prolog 将保存在他们的家庭住址寄存器必要情况下，在堆栈上推送非易失寄存器的参数、 局部变量和临时变量，为分配堆栈的固定的部分和 （可选） 建立的帧指针。 关联的展开数据必须描述序言中的操作，必须提供所需撤消 prolog 代码的作用的信息。

固定的分配，堆栈中是否是多个页 (即，超过 4096 个字节)，则可能堆栈分配无法跨越多个虚拟内存页，因此，必须实际分配之前检查分配。 这就是可从序言中调用，这不会销毁任何参数寄存器的特殊例程提供实现此目的。

用于将非易失寄存器保存的首选的方法是将它们移到之前固定的堆栈分配堆栈上。 如果固定的堆栈分配执行之前已保存的非易失性寄存器，则极有可能 32 位偏移量将要求要向其地址已保存注册 （据说，寄存器推送移动一样快并且应该是这样的区域在可预见未来尽管推送之间的隐式依赖关系。 可以按任意顺序保存非易失性寄存器。 但是，首次使用 prolog 中的非易失性寄存器必须是将其保存。

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

此 prolog 在其主位置中存储的参数寄存器 RCX，保存非易失注册 R13 R15、 分配固定的部分，该堆栈帧，并建立指向 128 个字节的固定的分配区域的帧指针。 通过使用偏移量，多个固定的分配，区域使用单字节偏移量进行寻址。

如果固定的分配的大小是大于或等于一页的内存，然后必须修改 RSP 之前调用一个帮助程序函数。 此帮助器，__chkstk，负责探测被分配堆栈范围，以确保已正确展开堆栈。 在这种情况下，系统将改为到前面的 prolog 示例：

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

__Chkstk 帮助程序将不会修改任何寄存器 R10、 R11，和的条件代码。 具体而言，它将返回到 RAX 保持不变，并保留所有非易失寄存器和未修改的形式自变量传递寄存器。

在每个退出时的函数存在 epilog 代码。 而通常情况下只有一个序言中，可以有许多 epilog。 Epilog 代码修剪为其分配固定的大小的堆栈 （如有必要）、 解除分配固定的堆栈分配、 通过弹出堆栈，它们已保存的值将还原非易失寄存器和返回。

Epilog 代码必须进行可靠通过异常和中断的展开遵循一组严格的规则的展开代码。 这可以减少的展开数据必需的因为描述每个 epilog 所不需的任何额外数据。 相反的展开代码可以确定 epilog，正在执行的向前扫描整个标识 epilog 代码流。

如果在不使用任何框架指针函数，然后 epilog 必须首先解除分配堆栈的固定的部分、 弹出，非易失寄存器，并控制返回到调用函数。 例如，应用于对象的

```
add      RSP, fixed-allocation-size
pop      R13
pop      R14
pop      R15
ret
```

如果在函数中使用帧指针，则必须向其固定分配，epilog 执行之前修整堆栈。 这是从技术上讲不属于 epilog。 例如，以下 epilog 无法用于撤消序言中以前使用过：

```
lea      RSP, -128[R13]
; epilogue proper starts here
add      RSP, fixed-allocation-size
pop      R13
pop      R14
pop      R15
ret
```

在实践中，当使用帧指针时，没有任何充分的理由，因此应改用以下 epilog 在两个步骤中，调整 RSP:

```
lea      RSP, fixed-allocation-size - 128[R13]
pop      R13
pop      R14
pop      R15
ret
```

这些是 epilog 的唯一合法窗体。 它必须包含其中的一`add RSP,constant`或`lea RSP,constant[FPReg]`后, 跟一系列的零个或多个 8 字节注册 pop 和退货或进程。 （只有一部分 jmp 语句都允许在 epilog 中。 这些 jmps ModRM 内存引用的以独占方式是类的，其中 ModRM mod 字段值 00。 禁止 jmps ModRM mod 字段值 01 或 10 在 epilog 中使用。 请参阅表 A-15 在 AMD x86-64 体系结构编程人员手册第 3 卷： 通用和系统指令，允许 ModRM 引用有关的详细信息。)。 可以显示没有其他代码。 具体而言，执行任何操作可以在 epilog 中，包括返回值的加载计划。

请注意，如果不使用帧指针，必须使用 epilog`add RSP,constant`先解除分配，堆栈的固定的部分。 它不能使用`lea RSP,constant[RSP]`相反。 因此的展开代码具有较少的模式识别 epilog 搜索时存在此限制。

遵循这些规则，以确定当前正在执行 epilog 和模拟的 epilog 以便重新创建上下文调用函数的其余部分执行的展开代码。

## <a name="see-also"></a>请参阅

[x64 软件约定](../build/x64-software-conventions.md)