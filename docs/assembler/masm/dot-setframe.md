---
title: .SETFRAME
ms.date: 08/30/2018
f1_keywords:
- .SETFRAME
helpviewer_keywords:
- .SETFRAME directive
ms.assetid: eaa9b5ed-4daa-4f1e-bdb6-100758007ab3
ms.openlocfilehash: a21dda496d32abcfeb4692d0228afdbcfd4e5ebb
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397922"
---
# <a name="setframe"></a>.SETFRAME

使用指定的寄存器（*reg*）和偏移量（*偏移量*）在展开信息中填充帧寄存器字段和偏移量。 偏移量必须是16的倍数，小于或等于240。 此指令还使用当前的序言偏移量为指定的寄存器生成 `UWOP_SET_FPREG` 的展开代码项。

## <a name="syntax"></a>语法

> **..SETFRAME** *reg*， *offset*

## <a name="remarks"></a>备注

**..SETFRAME**允许 ml64.exe 用户指定框架函数的展开方式，并且仅允许在序言中使用，该函数从[过程](../../assembler/masm/proc.md)框架声明扩展到[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指令。 这些指令不生成代码;它们仅生成 `.xdata` 和 `.pdata`。 **..SETFRAME**后面应是实际实现要展开的操作的说明。 最好将展开指令和它们要展开的代码封装在一个宏中，以确保协议。

有关详细信息，请参阅[MASM for x64 （ml64.exe）](../../assembler/masm/masm-for-x64-ml64-exe.md)。

## <a name="sample"></a>示例

### <a name="description"></a>说明

下面的示例演示如何使用帧指针：

### <a name="code"></a>代码

```asm
; ml64 frmex2.asm /link /entry:frmex2 /SUBSYSTEM:CONSOLE
_text SEGMENT
frmex2 PROC FRAME
   push rbp
.pushreg rbp
   sub rsp, 010h
.allocstack 010h
   mov rbp, rsp
.setframe rbp, 0
.endprolog
   ; modify the stack pointer outside of the prologue (similar to alloca)
   sub rsp, 060h

   ; we can unwind from the following AV because of the frame pointer
   mov rax, 0
   mov rax, [rax] ; AV!

   add rsp, 060h
   add rsp, 010h
   pop rbp
   ret
frmex2 ENDP
_text ENDS
END
```

## <a name="see-also"></a>另请参阅

[指令参考](directives-reference.md)
