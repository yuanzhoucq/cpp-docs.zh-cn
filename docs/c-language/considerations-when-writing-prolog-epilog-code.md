---
title: 编写 Prolog-Epilog 代码时的注意事项
ms.date: 11/04/2016
helpviewer_keywords:
- layouts, stack frame
- stack frame layout
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: 3b8addec-e809-48e4-b1d0-5bad133bd4b8
ms.openlocfilehash: e7bfeccf41b9e4dace49e9ab209a94598c492b41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515526"
---
# <a name="considerations-when-writing-prologepilog-code"></a>编写 Prolog/Epilog 代码时的注意事项

**Microsoft 专用**

在编写你自己的 prolog 和 epilog 代码序列之前，请务必了解堆栈帧的布局方式。了解如何使用 __LOCAL_SIZE 预定义的常量也很有用。

##  <a name="_clang_c_stack_frame_layout"></a> C 堆栈帧布局

此示例显示了可能出现在 32 位函数中的标准 prolog 代码：

```
push     ebp                 ; Save ebp
mov      ebp, esp            ; Set stack frame pointer
sub      esp, localbytes     ; Allocate space for locals
push     <registers>         ; Save registers
```

`localbytes` 变量表示局部变量堆栈上所需的字节数，`registers` 变量是表示要保存在堆栈上的寄存器列表的占位符。 推入寄存器后，您可以将任何其他适当的数据放置在堆栈上。 下面是相应的 epilog 代码：

```
pop      <registers>         ; Restore registers
mov      esp, ebp            ; Restore stack pointer
pop      ebp                 ; Restore ebp
ret                          ; Return from function
```

堆栈始终向下增长（从高内存地址到低内存地址）。 基指针 (`ebp`) 指向 `ebp` 的推入值。 局部变量区域从 `ebp-2` 开始。 若要访问局部变量，可通过从 `ebp` 中减去适当的值来计算 `ebp` 的偏移量。

##  <a name="_clang_the___local_size_constant"></a> __LOCAL_SIZE 常量

编译器提供常量 __LOCAL_SIZE 以用于函数 prolog 代码的内联汇编程序块。 此常数用于在自定义 prolog 代码中的堆栈帧上为局部变量分配空间。

编译器确定 __LOCAL_SIZE 的值。 该值是所有用户定义的局部变量和编译器生成的临时变量的总字节数。 __LOCAL_SIZE 只能用作即时操作数；它不能在表达式中使用。 您不得更改或重新定义此常量的值。 例如:

```
mov      eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov      eax, [ebp - __LOCAL_SIZE]   ;Error
```

包含自定义 prolog 和 epilog 序列的 naked 函数的以下示例在 prolog 序列中使用 __LOCAL_SIZE：

```
__declspec ( naked ) func()
{
   int i;
   int j;

   __asm      /* prolog */
      {
      push   ebp
      mov      ebp, esp
      sub      esp, __LOCAL_SIZE
      }

   /* Function body */

   __asm      /* epilog */
      {
      mov      esp, ebp
      pop      ebp
      ret
      }
}
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[naked 函数](../c-language/naked-functions.md)