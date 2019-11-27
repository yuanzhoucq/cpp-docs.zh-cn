---
title: PROC
ms.date: 08/30/2018
f1_keywords:
- PROC
helpviewer_keywords:
- PROC directive
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
ms.openlocfilehash: 5d1e44fcc4adbbe012b2f31fe9c6c27511bafff1
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74395031"
---
# <a name="proc"></a>PROC

标记名为*label*的过程块的开头和结尾。 可以通过**调用**指令或[调用](../../assembler/masm/invoke.md)指令调用块中的语句。

## <a name="syntax"></a>语法

> *标签* **PROC** ⟦*远处*⟧⟦*language-type*⟧⟦*visibility*⟧⟦ __\<__ *prologuearg* __>__ ⟧⟦**使用** *reglist*⟧⟦ __，__ *参数*⟦ __：__ *tag*⟧ .。。⟧\
> ⟦**FRAME** ⟦ __：__ *ehandler-address*⟧⟧ \
> *语句*\
> *标签* **ENDP**

## <a name="remarks"></a>备注

⟦**FRAME** ⟦ __：__ *ehandler-address*⟧⟧仅对 ml64.exe 有效，并使 MASM 在 pdata 中生成函数表项，xdata 中的展开信息用于函数的结构化异常处理展开行为。

当使用**FRAME**属性时，它必须后跟[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指令。

有关使用 ml64.exe 的详细信息，请参阅[MASM （ml64.exe）](../../assembler/masm/masm-for-x64-ml64-exe.md) 。

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

上面的代码将发出以下函数表和展开信息：

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

## <a name="see-also"></a>另请参阅

[指令参考](../../assembler/masm/directives-reference.md)
