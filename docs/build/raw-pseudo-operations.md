---
title: 原始伪操作 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4def1a0e-ec28-4736-91fb-fac95fba1f36
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff3b9dd065b4bf1f64950f97237dec08b10d23cd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369924"
---
# <a name="raw-pseudo-operations"></a>原始伪操作
本主题列出了伪操作。  
  
## <a name="remarks"></a>备注  
  
|伪操作|描述|  
|----------------------|-----------------|  
|PROC 帧 [: ehandler]|原因 MASM 以生成一个函数表中的.pdata 项和展开.xdata 中的信息的函数的结构化异常处理展开行为。  如果存在 ehandler，则此进程被进入.xdata 语言特定的处理程序。<br /><br /> 当使用帧属性时，它后面必须跟。ENDPROLOG 指令。  如果该函数使用 leaf 函数 (中定义[函数类型](../build/function-types.md)) 帧属性是不必要的因为这些伪操作的剩余部分。|  
|.PUSHREG reg|生成使用当前在序言中偏移量的指定的寄存器号 UWOP_PUSH_NONVOL 展开代码条目。<br /><br /> 这应仅用于非易失性的整数寄存器。  对于易失寄存器的推送操作，使用。ALLOCSTACK 8，改为|  
|.SETFRAME reg、 偏移量|填写帧中使用指定的寄存器和偏移量的展开信息寄存器字段和偏移量。 偏移量必须为 16 的倍数且小于或等于 240。 此指令还会生成指定使用当前的序言偏移量的寄存器的 UWOP_SET_FPREG 展开代码项。|  
|.ALLOCSTACK 大小|在序言中将生成 UWOP_ALLOC_SMALL 或具有指定大小的当前偏移量为 UWOP_ALLOC_LARGE。<br /><br /> 大小操作数必须是 8 的倍数。|  
|.SAVEREG reg、 偏移量|生成 UWOP_SAVE_NONVOL 或指定的寄存器和使用的当前序言偏移量的偏移量的 UWOP_SAVE_NONVOL_FAR 展开代码条目。 MASM 将选择最有效的编码。<br /><br /> 偏移量必须为正数，且是 8 的倍数。  偏移量是相对于基过程的框架，其中通常处于 RSP，或者，如果使用帧指针，不成比例的帧指针。|  
|.SAVEXMM128 reg、 偏移量|生成 UWOP_SAVE_XMM128 或指定的 XMM 寄存器和使用的当前序言偏移量的偏移量的 UWOP_SAVE_XMM128_FAR 展开代码条目。 MASM 将选择最有效的编码。<br /><br /> 偏移量必须为正数、 且为 16 的倍数。  偏移量是相对于基过程的框架，其中通常处于 RSP，或者，如果使用帧指针，不成比例的帧指针。|  
|.PUSHFRAME [代码]|生成 UWOP_PUSH_MACHFRAME 展开代码项。 如果指定可选的代码，则展开代码项提供的修饰符为 1。 否则修饰符为 0。|  
|.ENDPROLOG|用信号通知的序言声明的末尾。  必须出现在函数前 255 个字节。|  
  
 下面是示例函数 prolog 与大部分操作码的正确用法：  
  
```  
sample PROC FRAME     
   db      048h; emit a REX prefix, to enable hot-patching  
push rbp  
.pushreg rbp  
sub rsp, 040h  
.allocstack 040h     
lea rbp, [rsp+020h]  
.setframe rbp, 020h  
movdqa [rbp], xmm7  
.savexmm128 xmm7, 020h;the offset is from the base of the frame  
;not the scaled offset of the frame  
mov [rbp+018h], rsi  
.savereg rsi, 038h  
mov [rsp+010h], rdi  
.savereg rdi, 010h; you can still use RSP as the base of the frame  
; or any other register you choose  
.endprolog  
  
; you can modify the stack pointer outside of the prologue (similar to alloca)  
; because we have a frame pointer.  
; if we didn’t have a frame pointer, this would be illegal  
; if we didn’t make this modification,  
; there would be no need for a frame pointer  
  
sub rsp, 060h  
  
; we can unwind from the following AV because of the frame pointer  
  
mov rax, 0  
mov rax, [rax] ; AV!  
  
; restore the registers that weren’t saved with a push  
; this isn’t part of the official epilog, as described in section 2.5  
  
movdqa xmm7, [rbp]  
mov rsi, [rbp+018h]  
mov rdi, [rbp-010h]  
  
; Here’s the official epilog  
  
lea rsp, [rbp-020h]  
pop rbp  
ret  
sample ENDP  
```  
  
## <a name="see-also"></a>请参阅  
 [MASM 的展开帮助器](../build/unwind-helpers-for-masm.md)