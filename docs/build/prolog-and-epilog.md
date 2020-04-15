---
title: x64 prolog 和 epilog
ms.date: 12/17/2018
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
ms.openlocfilehash: d0b7444af6e434a09f6af5f5b1c144b46c79ad56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328435"
---
# <a name="x64-prolog-and-epilog"></a>x64 prolog 和 epilog

分配堆栈空间、调用其他函数、保存非易失性寄存器或使用异常处理的每个函数都必须具有一个 prolog，其地址限制在与相应的函数表条目关联的展开数据中描述。 有关详细信息，请参阅[x64 异常处理](../build/exception-handling-x64.md)。 如有必要，prolog 会在其主地址中保存参数寄存器，在堆栈上推送非易失性寄存器，为局部变量和临时数据分配堆栈的固定部分，并选择建立帧指针。 关联的展开数据必须描述 prolog 的操作，并且必须提供必要的信息来撤消 prolog 代码的效果。

如果堆栈中的固定分配是多个页面（即大于 4096 字节），则堆栈分配可能跨越多个虚拟内存页，因此，在分配分配之前必须检查分配。 为此提供了一个特殊例程，该例程可以从 prolog 调用，并且不会销毁任何参数寄存器。

保存非易失性寄存器的首选方法是在固定堆栈分配之前将它们移动到堆栈上。 如果在保存非易失性寄存器之前执行固定堆栈分配，则很可能需要 32 位位位位处理保存的寄存器区域。 （据报道，寄存器的推送与移动一样快，在可预见的将来，尽管推送之间存在隐含的依赖性，但仍保持此速度。可按任意顺序保存非易失寄存器。 但是，在 Prolog 中首次使用非易失性寄存器必须是保存它。

## <a name="prolog-code"></a>Prolog 代码

典型 prolog 的代码可能是：

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    sub    RSP, fixed-allocation-size
    lea    R13, 128[RSP]
    ...
```

此 prolog 将参数寄存器 RCX 存储在其主位置，保存非易失性寄存器 R13-R15，分配堆栈帧的固定部分，并建立一个帧指针，将 128 字节点入固定分配区域。 使用偏移允许使用一字节偏移处理更多的固定分配区域。

如果固定分配大小大于或等于一页内存，则必须在修改 RSP 之前调用帮助器函数。 此帮助程序`__chkstk`探测要分配的堆栈范围，以确保堆栈得到正确扩展。 在这种情况下，前面的 prolog 示例将改为：

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    mov    RAX,  fixed-allocation-size
    call   __chkstk
    sub    RSP, RAX
    lea    R13, 128[RSP]
    ...
```

`__chkstk`帮助程序不会修改 R10、R11 和条件代码以外的任何寄存器。 特别是，它将返回 RAX 不变，并保留所有未修改的非易失寄存器和参数传递寄存器。

## <a name="epilog-code"></a>Epilog 代码

函数的每个出口都存在 Epilog 代码。 虽然通常只有一个象号，但可以有许多的表观。 Epilog 代码将堆栈修剪到其固定分配大小（如有必要），取消分配固定堆栈分配，通过从堆栈中弹出保存的值来还原非易失性寄存器，然后返回。

epilog 代码必须遵循一组严格的解放代码规则，以便可靠地展开异常和中断。 这些规则减少了所需的展开数据量，因为无需额外数据来描述每个描述。 相反，展开代码可以通过向前扫描代码流来标识表征来确定正在执行。

如果函数中不使用帧指针，则 epilog 必须首先解调堆栈的固定部分，弹出非易失性寄存器，并将控件返回到调用函数。 例如，

```MASM
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

如果在函数中使用帧指针，则必须在执行分义之前将堆栈修剪为其固定分配。 从技术上讲，此操作不是该说明的一部分。 例如，以下表征可用于撤消以前使用的 prolog：

```MASM
    lea      RSP, -128[R13]
    ; epilogue proper starts here
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

实际上，当使用帧指针时，没有充分理由分两步调整 RSP，因此将改为使用以下表示名词：

```MASM
    lea      RSP, fixed-allocation-size - 128[R13]
    pop      R13
    pop      R14
    pop      R15
    ret
```

这些表格是征词的唯一合法形式。 `add RSP,constant`它必须由`lea RSP,constant[FPReg]`或 ，后跟一系列零或更多 8 字节寄存器弹出和 a`return`或 。 `jmp` （在声明中只允许`jmp`语句的子集。 子集是具有 ModRM`jmp`内存引用的语句类，其中 ModRM mod 字段值为 00。 `jmp`禁止在与 ModRM mod 字段值 01 或 10 一起使用声明。 有关允许的 ModRM 参考的更多信息，请参阅 AMD x86-64 架构程序员手册第 3 卷：通用和系统说明中的表 A-15。无法显示其他代码。 特别是，无法在分词中安排任何内容，包括加载返回值。

不使用帧指针时，该表征必须用于`add RSP,constant`解分配堆栈的固定部分。 它可能不使用`lea RSP,constant[RSP]`。 存在此限制，因此展开代码在搜索表皮时需要识别的模式较少。

遵循这些规则允许展开代码确定当前正在执行的表名，并模拟对分词的其余部分的执行，以允许重新创建调用函数的上下文。

## <a name="see-also"></a>另请参阅

[x64 软件约定](x64-software-conventions.md)
