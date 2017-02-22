---
title: "原始伪操作 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 4def1a0e-ec28-4736-91fb-fac95fba1f36
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# 原始伪操作
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题列出了伪操作。  
  
## 备注  
  
|伪操作|描述|  
|---------|--------|  
|PROC FRAME \[:ehandler\]|导致 MASM 为函数的结构化异常处理展开行为在 .pdata 中生成函数表项并在 .xdata 中生成展开信息。  如果提供 ehandler，则此进程将作为语言特定处理程序输入到 .xdata 中。<br /><br /> 使用 FRAME 特性时，其后必须跟 .ENDPROLOG 指令。  如果函数是叶函数（如在 [函数类型](../build/function-types.md) 中定义的那样），则不需要 FRAME 特性，就像不需要这些伪操作的剩余部分一样。|  
|.PUSHREG reg|使用 Prolog 中的当前偏移量为指定的寄存器号生成 UWOP\_PUSH\_NONVOL 展开代码项。<br /><br /> 这只能用于非易失的整数寄存器。  对于易失寄存器的推送操作，请改用 .ALLOCSTACK 8|  
|.SETFRAME reg, offset|使用指定的寄存器和偏移量填写展开信息中的帧寄存器字段和偏移量。  偏移量必须是 16 的倍数，且小于或等于 240。  此指令还使用当前 Prolog 偏移量为指定的寄存器生成 UWOP\_SET\_FPREG 展开代码项。|  
|.ALLOCSTACK size|为 Prolog 中的当前偏移量生成指定大小的 UWOP\_ALLOC\_SMALL 或 UWOP\_ALLOC\_LARGE。<br /><br /> 大小操作数必须为 8 的倍数。|  
|.SAVEREG reg, offset|使用当前 Prolog 偏移量为指定的寄存器和偏移量生成 UWOP\_SAVE\_NONVOL 或 UWOP\_SAVE\_NONVOL\_FAR 展开代码项。  MASM 将选择最有效的编码。<br /><br /> 偏移量必须为正数，且为 8 的倍数。  偏移量与过程框架的基有关（该框架通常位于 RSP 中）或与不成比例的帧指针（如果使用帧指针）有关。|  
|.SAVEXMM128 reg, offset|使用当前 Prolog 偏移量为指定的 XMM 寄存器和偏移量生成 UWOP\_SAVE\_XMM128 或 UWOP\_SAVE\_XMM128\_FAR 展开代码项。  MASM 将选择最有效的编码。<br /><br /> 偏移量必须为正数，且为 16 的倍数。  偏移量与过程框架的基有关（该框架通常位于 RSP 中）或与不成比例的帧指针（如果使用帧指针）有关。|  
|.PUSHFRAME \[code\]|生成 UWOP\_PUSH\_MACHFRAME 展开代码项。  如果指定可选代码，则向展开代码项提供的修饰符为 1。  否则该修饰符为 0。|  
|.ENDPROLOG|通知 Prolog 声明的结尾。  必须出现在函数的前 255 个字节中。|  
  
 以下是正确使用多数操作码的示例函数 Prolog：  
  
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
  
## 请参阅  
 [MASM 的展开帮助器](../build/unwind-helpers-for-masm.md)