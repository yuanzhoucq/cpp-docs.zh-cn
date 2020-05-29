---
title: x64 prolog 和 epilog
ms.date: 12/17/2018
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
ms.openlocfilehash: d0b7444af6e434a09f6af5f5b1c144b46c79ad56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328435"
---
# <a name="x64-prolog-and-epilog"></a>x64 prolog 和 epilog

分配堆栈空间、调用其他函数、保存非易失性寄存器或使用异常处理的每个函数都必须具有 prolog，其地址限制在与相应函数表条目关联的展开数据中进行了描述。 有关详细信息，请参阅 [x64 异常处理](../build/exception-handling-x64.md)。 prolog 会在需要时将参数寄存器保存在其主地址中、将非易失性寄存器压入堆栈、为局部变量和临时内存分配堆栈的固定部分并且可选择建立帧指针。 关联展开数据必须描述 prolog 的操作，并且必须提供撤消 prolog 代码效果所需的信息。

如果堆栈中的固定分配是多个页（即大于 4096 个字节），则堆栈分配可以跨越多个虚拟内存页，因此必须在分配之前检查分配。 为此，提供了一个可从 prolog 调用并且不会销毁任何参数寄存器的特殊例程。

保存非易失性寄存器的首选方法是在固定堆栈分配之前将它们移动到堆栈上。 如果在保存非易失性寄存器之前执行固定堆栈分配，则很可能需要进行 32 位置换来处理已保存的寄存器区域。 （据报道，寄存器的压入与移动一样快，并且应在可预见的未来保持如此，尽管压入之间隐含着依赖关系。）可按任意顺序保存非易失性寄存器。 但是，在 prolog 中首次使用非易失性寄存器必须是保存它。

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

此 prolog 将参数寄存器 RCX 存储在其主位置，保存非易失性寄存器 R13-R15，分配堆栈帧的固定部分，并建立将 128 个字节指向固定分配区域的帧指针。 使用偏移可以通过一字节偏移对更多固定分配区域进行寻址。

如果固定分配大小大于或等于一页内存，则在修改 RSP 之前，必须调用帮助程序函数。 此帮助程序 `__chkstk` 会探测要分配的堆栈范围，以确保正确扩展堆栈。 在这种情况下，前面的 prolog 示例会改为：

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

`__chkstk` 帮助程序将不会修改除 R10、R11 和条件代码以外的任何寄存器。 具体而言，它将返回未更改的 RAX，并使所有非易失性寄存器和参数传递寄存器保持未修改。

## <a name="epilog-code"></a>Epilog 代码

Epilog 代码在每次退出到函数时出现。 通常只有一个 prolog，而可以有向上 epilog。 Epilog 代码将堆栈剪裁为固定分配大小（如有必要），解除分配固定堆栈分配，通过从堆栈中弹出其保存的值来还原非易失性寄存器，然后返回。

epilog 代码必须遵循一组严格的规则，展开代码才能可靠地通过异常和中断展开。 这些规则可减少所需的展开数据量，因为描述每个 epilog 不需要额外数据。 相反，展开代码可以向前扫描代码流来标识 epilog，从而确定是否在执行 epilog。

如果函数中未使用帧指针，则 epilog 必须首先解除分配堆栈的固定部分，弹出非易失性寄存器，然后将控制权返回给调用函数。 例如，应用于对象的

```MASM
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

如果函数中使用了帧指针，则必须在执行 epilog 之前，将堆栈剪裁为其固定分配。 在技术上，此操作不属于 epilog。 例如，以下 epilog 可用于撤消以前使用的 prolog：

```MASM
    lea      RSP, -128[R13]
    ; epilogue proper starts here
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

实际上，使用帧指针时，没有充分理由分两个步骤调整 RSP，因此将改用以下 epilog：

```MASM
    lea      RSP, fixed-allocation-size - 128[R13]
    pop      R13
    pop      R14
    pop      R15
    ret
```

这些窗体是 epilog 的唯一合法窗体。 它必须由 `add RSP,constant` 或 `lea RSP,constant[FPReg]` 组成，后跟一系列零个或多个 8 字节寄存器弹出以及一个 `return` 或 `jmp`。 （epilog 中只允许存在 `jmp` 语句的子集。 该子集只是具有 ModRM 内存引用的 `jmp` 语句的类，其中 ModRM mod 字段值为 00。 禁止在 ModRM mod 字段值为 01 或 10 的 epilog 中使用 `jmp` 语句。 请参阅 AMD x86-64 体系结构程序员手册第 3 卷中的表 A-15：常规用途和系统说明，以了解有关允许的 ModRM 引用的详细信息。）无法显示其他代码。 具体而言，无法在 epilog 内计划任何内容，包括加载返回值。

未使用帧指针时，epilog 必须使用 `add RSP,constant` 解除分配堆栈的固定部分。 它不得改用 `lea RSP,constant[RSP]`。 存在此限制是为了减少展开代码在搜索 epilog 时要识别的模式。

遵循这些规则使展开代码可以确定当前在执行 epilog，并模拟 epilog 剩余部分的执行，以便可以重新创建调用函数的上下文。

## <a name="see-also"></a>请参阅

[x64 软件约定](x64-software-conventions.md)
