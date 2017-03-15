---
title: ".PUSHREG | Microsoft Docs"
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
  - ".PUSHREG"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".PUSHREG directive"
ms.assetid: e0c83758-dfed-40ea-afe6-cb833c8d2d30
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .PUSHREG
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用当前偏移量在序言，生成 `UWOP_PUSH_NONVOL` 展开指定的注册数字的代码项。  
  
## 语法  
  
```  
.PUSHREG register  
```  
  
## 备注  
 .PUSHREG 允许 ml64.exe 用户指定框架功能如何展开和在序言中只允许，从 [PROC](../../assembler/masm/proc.md) 帧声明扩展到 [.ENDPROLOG](../../assembler/masm/dot-endprolog.md) 指令。  这些指令不生成代码;它们只生成 `.xdata` 和 `.pdata`。  .PUSHREG 应在实际实现将展开的事件的命令之后。  最好包装展开指令及其在宏被视为展开确保协议的代码。  
  
 有关更多信息，请参见 [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## 示例  
  
### 说明  
 下面的示例演示如何使非易失 tegisters。  
  
### 代码  
  
```  
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
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)