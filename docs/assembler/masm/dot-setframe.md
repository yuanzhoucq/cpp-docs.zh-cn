---
title: ".SETFRAME | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - ".SETFRAME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".SETFRAME directive"
ms.assetid: eaa9b5ed-4daa-4f1e-bdb6-100758007ab3
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .SETFRAME
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

填充帧注册字段和扭曲在展开信息使用指定的寄存器 \(`reg`\) 和扭曲 \(`offset`\)。  偏移量必须是 16 的倍数，且小于或等于 240。  使用当前 \(偏移量，此指令还会生成 `UWOP_SET_FPREG` 展开指定注册的代码项。  
  
## 语法  
  
```  
.SETFRAME reg, offset  
```  
  
## 备注  
 .SETFRAME 允许 ml64.exe 用户指定框架功能如何展开和在序言中只允许，从 [PROC](../../assembler/masm/proc.md) 帧声明扩展到 [.ENDPROLOG](../../assembler/masm/dot-endprolog.md) 指令。  这些指令不生成代码;它们只生成 `.xdata` 和 `.pdata`。  .SETFRAME 应在实际实现将展开的事件的命令之后。  最好包装展开指令及其在宏被视为展开确保协议的代码。  
  
 有关更多信息，请参见 [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## 示例  
  
### 说明  
 下面的示例演示如何使用帧指针:  
  
### 代码  
  
```  
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
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)