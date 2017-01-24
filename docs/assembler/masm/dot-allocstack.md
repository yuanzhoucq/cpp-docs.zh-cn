---
title: ".ALLOCSTACK | Microsoft Docs"
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
  - ".ALLOCSTACK"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".ALLOCSTACK directive"
ms.assetid: 9801594b-7ac2-4df2-a49d-07d9dd9af99e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .ALLOCSTACK
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

生成 **UWOP\_ALLOC\_SMALL** 或 **UWOP\_ALLOC\_LARGE** 使用指定的范围当前偏移量用的序言。  
  
## 语法  
  
```  
.ALLOCSTACK size  
```  
  
## 备注  
 MASM 中选择一个与给定范围的最有效的编码。  
  
 .ALLOCSTACK 允许 ml64.exe 用户指定框架功能如何在序言中展开并且只允许，从 [PROC](../../assembler/masm/proc.md) 帧声明扩展到 [.ENDPROLOG](../../assembler/masm/dot-endprolog.md) 指令。  这些指令不生成代码;它们只生成 `.xdata` 和 `.pdata`。  .ALLOCSTACK 应在实际实现将展开的事件的命令之后。  最好包装展开指令及其在宏被视为展开确保协议的代码。  
  
 `size` 操作数必须是多线程的 8。  
  
 有关更多信息，请参见[MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## 示例  
 下面的示例演示如何指定展开\/异常处理程序:  
  
```  
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
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)