---
title: "PROC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PROC directive"
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# PROC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

标记开始和过程的结束块调用的 *标签*。  块中的语句可以调用与 **调用** 命令或 [调用](../../assembler/masm/invoke.md) 指令。  
  
## 语法  
  
```  
  
   label PROC [[distance]] [[langtype]] [[visibility]] [[<prologuearg>]]   
[[USES reglist]] [[, parameter [[:tag]]]]...  
[FRAME [:ehandler-address] ]  
statements  
label ENDP  
```  
  
## 备注  
 \[帧 \[:*ehandler 地址*\] out\] ml64.exe 才有效，并使 MASM 生成在 .pdata 的函数表项目，然后展开在 .xdata 功能的信息的结构化异常处理的展开行为。  
  
 当使用时 **框架** 属性，必须由 [.ENDPROLOG](../../assembler/masm/dot-endprolog.md) 指令后跟它。  
  
 请参见 [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md) 有关使用 ml64.exe 的更多信息。  
  
## 示例  
  
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
  
 上面的代码将发出以下函数表并展开信息:  
  
```  
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
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)