---
title: PROC
ms.date: 08/30/2018
f1_keywords:
- PROC
helpviewer_keywords:
- PROC directive
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
ms.openlocfilehash: e7931c97570c0fefcacb0123d75934867793fba4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439619"
---
# <a name="proc"></a>PROC

将标记调用一个过程块的开头和结尾*标签*。 可以使用调用块中的语句**调用**指令或[INVOKE](../../assembler/masm/invoke.md)指令。

## <a name="syntax"></a>语法

> *标签*PROC [[*距离*]] [[*langtype*]] [[*可见性*]] [[\<*prologuearg*>]] [[使用*reglist*]] [[，*参数*[[:*标记*]]]...<br/>
> [[帧 [[:*ehandler 地址*]]]]<br/>
> *语句*<br/>
> *标签*ENDP

## <a name="remarks"></a>备注

[[帧 [[:*ehandler 地址*]]]] 才有效，且 ml64.exe，并导致 MASM 将生成函数表条目中的.pdata 和展开.xdata 中的信息的函数的结构化异常处理展开行为。

当**帧**属性，它的后面必须跟[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指令。

请参阅[MASM 的 x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md)有关使用 ml64.exe 的详细信息。

## <a name="example"></a>示例

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

上面的代码将发出以下函数表和展开的信息：

```Output
FileHeader->Machine 34404
Dumping Unwind Information for file ex2.exe

.pdata entry 1 0x00001000 0x00001023

  Unwind data: 0x00002000

    Unwind version: 1
    Unwind Flags: None
    Size of prologue: 0x08
    Count of codes: 3
    Frame register: rbp
    Frame offset: 0x0
    Unwind codes:

      Code offset: 0x08, SET_FPREG, register=rbp, offset=0x00
      Code offset: 0x05, ALLOC_SMALL, size=0x10
      Code offset: 0x01, PUSH_NONVOL, register=rbp
```

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>