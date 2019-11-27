---
title: .ALLOCSTACK
ms.date: 08/30/2018
f1_keywords:
- .ALLOCSTACK
helpviewer_keywords:
- .ALLOCSTACK directive
ms.assetid: 9801594b-7ac2-4df2-a49d-07d9dd9af99e
ms.openlocfilehash: 6d9d86371503992d1bebe738fb6e6773581b10e3
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398631"
---
# <a name="allocstack"></a>.ALLOCSTACK

为序言中的当前偏移量生成指定大小的**UWOP_ALLOC_SMALL**或**UWOP_ALLOC_LARGE** 。

## <a name="syntax"></a>语法

> **.ALLOCSTACK** *大小*

## <a name="remarks"></a>备注

MASM 将为给定大小选择最有效的编码。

**.ALLOCSTACK**允许 ml64.exe 用户指定框架函数的展开方式，并只允许在序言内进行扩展，这种情况下，它从[过程](../../assembler/masm/proc.md)框架声明扩展到[。ENDPROLOG](../../assembler/masm/dot-endprolog.md)指令。 这些指令不生成代码;它们仅生成 `.xdata` 和 `.pdata`。 **.ALLOCSTACK**后面应是实际实现要展开的操作的说明。 最好将展开指令和它们要展开的代码封装在一个宏中，以确保协议。

*大小*操作数必须是8的倍数。

有关详细信息，请参阅[MASM for x64 （ml64.exe）](../../assembler/masm/masm-for-x64-ml64-exe.md)。

## <a name="sample"></a>示例

下面的示例演示如何指定展开/异常处理程序：

```asm
; ml64 ex3.asm /link /entry:Example1  /SUBSYSTEM:Console
text SEGMENT
PUBLIC Example3
PUBLIC Example3_UW
Example3_UW PROC NEAR
   ; exception/unwind handler body

   ret 0

Example3_UW ENDP

Example3 PROC FRAME : Example3_UW

   sub rsp, 16
.allocstack 16

.endprolog

   ; function body
    add rsp, 16
   ret 0

Example3 ENDP
text ENDS
END
```

## <a name="see-also"></a>另请参阅

[指令参考](../../assembler/masm/directives-reference.md)
