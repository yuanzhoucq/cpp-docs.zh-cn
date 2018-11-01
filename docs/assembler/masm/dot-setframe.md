---
title: .SETFRAME
ms.date: 08/30/2018
f1_keywords:
- .SETFRAME
helpviewer_keywords:
- .SETFRAME directive
ms.assetid: eaa9b5ed-4daa-4f1e-bdb6-100758007ab3
ms.openlocfilehash: c2c35cdb2889350b27e9fb11c397b684506972c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506869"
---
# <a name="setframe"></a>.SETFRAME

填写在帧中使用指定的寄存器的展开信息寄存器字段和偏移量 (`reg`) 和偏移量 (`offset`)。 偏移量必须为 16 的倍数且小于或等于 240。 此指令还会生成`UWOP_SET_FPREG`展开代码条目指定注册使用当前的序言偏移量。

## <a name="syntax"></a>语法

> .SETFRAME reg、 偏移量

## <a name="remarks"></a>备注

.SETFRAME 允许 ml64.exe 用户指定帧函数如何将回退，并只允许在序言中，从扩展了[PROC](../../assembler/masm/proc.md)帧声明到[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指令。 这些指令不会生成代码;它们只能生成`.xdata`和`.pdata`。 .SETFRAME 前面应带有实际实现是展开的操作的说明。 它是包装展开指令和它们专门为在宏展开用于确保协议的代码的好办法。

有关详细信息，请参阅[MASM 的 x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md)。

## <a name="sample"></a>示例

### <a name="description"></a>描述

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

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>