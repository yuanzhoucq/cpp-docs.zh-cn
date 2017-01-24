---
title: "MASM 宏 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 21410432-72fc-4795-bc93-e78123f9f14f
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# MASM 宏
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为了简化 [原始伪操作](../build/raw-pseudo-operations.md) 的使用，在 ksamd64.inc 中定义了一组宏，可以使用这些宏创建典型的过程 Prolog 和 Epilog。  
  
## 备注  
  
|宏|描述|  
|-------|--------|  
|alloc\_stack\(n\)|分配 n 字节堆栈帧（使用“sub rsp, n”），并发出合适的展开信息 \(.allocstack n\)|  
|save\_reg reg, loc|将非易失寄存器 reg 保存到堆栈的 RSP 偏移量 loc 处，并发出合适的展开信息。  \(.savereg reg, loc\)|  
|push\_reg reg|将非易失寄存器 reg 推送到堆栈上，并发出合适的展开信息。  \(.pushreg reg\)|  
|rex\_push\_reg reg|使用 2 个字节驱动器，保存非易失寄存器在堆栈，而发出相应展开信息 \(.pushreg reg\) 应使用方法，如果驱动器是函数的第一命令确保该函数是快捷的 patchable。|  
|save\_xmm128 reg, loc|将非易失 XMM 寄存器 reg 保存到堆栈的 RSP 偏移量 loc 处，并发出合适的展开信息 \(.savexmm128 reg, loc\)|  
|set\_frame reg, offset|将帧寄存器 reg 设置为 RSP \+ 偏移量（通过使用 mov 或 lea），并发出合适的展开信息 \(.set\_frame reg, offset\)|  
|push\_eflags|使用 pushfq 指令推送 eflag，并发出合适的展开信息 \(.alloc\_stack 8\)|  
  
 此处为示例函数 Prolog，演示了这些宏的正确用法：  
  
```  
SkFrame struct   
Fill    dq ?; fill to 8 mod 16   
SavedRdi dq ?; saved register RDI   
SavedRsi dq ?; saved register RSI   
SkFrame ends  
  
sampleFrame struct  
Filldq?; fill to 8 mod 16  
SavedRdidq?; Saved Register RDI   
SavedRsi  dq?; Saved Register RSI  
sampleFrame ends  
  
sample2 PROC FRAME  
alloc_stack(sizeof sampleFrame)  
save_reg rdi, sampleFrame.SavedRdi  
save_reg rsi, sampleFrame.SavedRsi  
.end_prolog  
  
; function body  
  
mov rsi, sampleFrame.SavedRsi[rsp]  
mov rdi, sampleFrame.SavedRdi[rsp]  
  
; Here’s the official epilog  
  
add rsp, (sizeof sampleFrame)  
ret  
sample2 ENDP  
```  
  
## 请参阅  
 [MASM 的展开帮助器](../build/unwind-helpers-for-masm.md)