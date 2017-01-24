---
title: "MASM for x64 (ml64.exe) | Microsoft Docs"
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
helpviewer_keywords: 
  - "ml64.exe"
  - "ml"
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# MASM for x64 (ml64.exe)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ml64.exe 是接受 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 汇编语言的汇编。  有关 ml64.exe 编译器选项的信息，请参见 [ML and ML64 Command\-Line Reference](../../assembler/masm/ml-and-ml64-command-line-reference.md)。  
  
 内联 ASM 没有为 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]支持。  使用 MASM 或编译器内部函数 \([x64 Intrinsics](http://msdn.microsoft.com/zh-cn/5d1f5d3e-156e-4ebf-932e-fd09be7ced62)\)。  
  
 两个工作区是具有单独的程序集完全支持 x64\) 的 MASM \(和编译器内部函数。  我们添加大量内部允许客户利用特殊功能命令 \(即。  特权，扫描位\/测试，互锁，等等\) 尽可能接近跨平台的方式尽可能。  
  
## ml64 特定指令  
 使用 ml64.exe 的以下指令:  
  
-   [.ALLOCSTACK](../../assembler/masm/dot-allocstack.md)  
  
-   [.ENDPROLOG](../../assembler/masm/dot-endprolog.md)  
  
-   [.PUSHFRAME](../../assembler/masm/dot-pushframe.md)  
  
-   [.PUSHREG](../../assembler/masm/dot-pushreg.md)  
  
-   [.SAVEREG](../../assembler/masm/dot-savereg.md)  
  
-   [.SAVEXMM128](../../assembler/masm/dot-savexmm128.md)  
  
-   [.SETFRAME](../../assembler/masm/dot-setframe.md)  
  
 此外， [PROC](../../assembler/masm/proc.md) 指令是更新用于 ml64.exe 的使用。  
  
## 32 位地址方式 \(地址范围重写\)  
 ，如果内存操作数包括 32 位寄存器， MASM 将发出 0x67 地址范围重写。  例如，下面的示例导致地址范围重写发出:  
  
```  
mov rax, QWORD PTR [ecx]  
mov eax, DWORD PTR [ecx*2+r10d]  
mov eax, DWORD PTR [ecx*2+r10d+0100h]  
prefetch [eax]  
movnti rax, QWORD PTR [r8d]  
```  
  
 MASM，假设，如果 32 位置换单独出现作为内存操作数， 64 位路由的意图。  没有为 32 位解决当前支持使用此类操作数。  
  
 最后，在一个内存操作数中的混合注册大小，如下面的代码所示，将生成错误。  
  
```  
mov eax, DWORD PTR [rcx*2+r10d]  
mov eax, DWORD PTR [ecx*2+r10+0100h]  
```  
  
## 请参阅  
 [Microsoft Macro Assembler Reference](../../assembler/masm/microsoft-macro-assembler-reference.md)