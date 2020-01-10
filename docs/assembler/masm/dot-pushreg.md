---
title: .PUSHREG
ms.date: 12/16/2019
f1_keywords:
- .PUSHREG
helpviewer_keywords:
- .PUSHREG directive
ms.assetid: e0c83758-dfed-40ea-afe6-cb833c8d2d30
ms.openlocfilehash: de6ffd3668f47732144e8c632410f6dfde6b2f31
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318288"
---
# <a name="pushreg"></a>.PUSHREG

使用序言中的当前偏移量为指定寄存器号生成 `UWOP_PUSH_NONVOL` 的展开代码项。

## <a name="syntax"></a>语法

> .PUSHREG*注册*

## <a name="remarks"></a>备注

**.PUSHREG**允许 ml64.exe 用户指定框架函数的展开方式，并且仅允许在序言中使用，该函数从[过程](proc.md)**框架**声明扩展到[。ENDPROLOG](dot-endprolog.md)指令。 这些指令不生成代码;它们仅生成 `.xdata` 和 `.pdata`。 **.PUSHREG**后面应是实际实现要展开的操作的说明。 最好将展开指令和它们要展开的代码封装在一个宏中，以确保协议。

*注册*可以是以下项之一： \
RAX |RCX |RDX |RBX |RDI.TPL |RSI |RBP |R8 |R9 |R10 |R11 |R12 |R13 |R14 |R15.

有关详细信息，请参阅[MASM for x64 （ml64.exe）](masm-for-x64-ml64-exe.md)。

## <a name="sample"></a>示例

### <a name="description"></a>描述

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

[指令引用](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)
