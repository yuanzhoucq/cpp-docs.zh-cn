---
title: .PUSHREG
ms.date: 08/30/2018
f1_keywords:
- .PUSHREG
helpviewer_keywords:
- .PUSHREG directive
ms.assetid: e0c83758-dfed-40ea-afe6-cb833c8d2d30
ms.openlocfilehash: 2190bd05667de82dada34a63f11647c653f97247
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398027"
---
# <a name="pushreg"></a>.PUSHREG

使用序言中的当前偏移量为指定寄存器号生成 `UWOP_PUSH_NONVOL` 的展开代码项。

## <a name="syntax"></a>语法

> .PUSHREG 注册

## <a name="remarks"></a>备注

**.PUSHREG**允许 ml64.exe 用户指定框架函数的展开方式，并且仅允许在序言中使用，该函数从[过程](../../assembler/masm/proc.md)**框架**声明扩展到[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指令。 这些指令不生成代码;它们仅生成 `.xdata` 和 `.pdata`。 **.PUSHREG**后面应是实际实现要展开的操作的说明。 最好将展开指令和它们要展开的代码封装在一个宏中，以确保协议。

有关详细信息，请参阅[MASM for x64 （ml64.exe）](../../assembler/masm/masm-for-x64-ml64-exe.md)。

## <a name="sample"></a>示例

### <a name="description"></a>说明

下面的示例演示如何推送非易失性寄存器。

### <a name="code"></a>代码

```asm
; ml64 ex1.asm /link /entry:Example1 /SUBSYSTEM:CONSOLE
_text SEGMENT
Example1 PROC FRAME
   push r10
.pushreg r10
   push r15
.pushreg r15
   push rbx
.pushreg rbx
   push rsi
.pushreg rsi
.endprolog
   ; rest of function ...
   ret
Example1 ENDP
_text ENDS
END
```

## <a name="see-also"></a>另请参阅

[指令参考](directives-reference.md)
