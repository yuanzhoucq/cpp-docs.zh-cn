---
title: ".MODEL | Microsoft Docs"
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
  - ".MODEL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".MODEL directive"
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .MODEL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

初始化程序内存模型。  
  
## 语法  
  
```  
.MODEL memorymodel [[, langtype]] [[, stackoption]]  
```  
  
#### 参数  
 `memorymodel`  
 必选的参数，用于确定代码和数据的指针的大小。  
  
 `langtype`  
 设置过程和公共符号的呼叫和命名约定的可选参数。  
  
 `stackoption`  
 可选参数。  
  
 `stackoption`is not used if `memorymodel` is `FLAT`.  
  
 指定`NEARSTACK`分组到单个物理网段的堆栈段 \(`DGROUP`） 与数据一起。  堆栈段寄存器 \(`SS`） 即被保存在相同的数据段寄存器地址 \(`DS`\)。  `FARSTACK`未分组的堆栈与`DGROUP`。 因此`SS`不等于`DS`。  
  
## 备注  
 .`MODEL`在不使用[MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
 当目标 16 位和 32 位平台时下, 表列出可能的值为每个参数：  
  
|Parameter|32 位的值|16 位值 （16 位的早期开发支持）|  
|---------------|------------|-------------------------|  
|`memorymodel`|`FLAT`|`TINY`, `SMALL`, `COMPACT`, `MEDIUM`, `LARGE`, `HUGE`, `FLAT`|  
|`langtype`|`C`, `STDCALL`|`C`, `BASIC`, `FORTRAN`, `PASCAL`, `SYSCALL`, `STDCALL`|  
|`stackoption`|未使用|`NEARSTACK`, `FARSTACK`|  
  
## 代码  
 有关 MASM 相关的示例，下载中的编译器示例[Visual C\+\+ 示例和相关文档 Visual Studio 2010年](http://go.microsoft.com/fwlink/?LinkID=178749)。  
  
 下面的示例演示如何使用`.MODEL`指令。  
  
## 示例  
  
```  
; file simple.asm  
; For x86 (32-bit), assemble with debug information:   
;   ml -c -Zi simple.asm  
; For x64 (64-bit), assemble with debug information:   
;   ml64 -c -DX64 -Zi simple.asm  
;  
; In this sample, the 'X64' define excludes source not used   
;  when targeting the x64 architecture  
  
ifndef X64  
.686p  
.XMM  
.model flat, C  
endif  
  
.data  
; user data  
  
.code  
; user code  
  
fxn PROC public  
  xor eax, eax ; zero function return value  
  ret  
fxn ENDP  
  
end  
```  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)   
 [Visual C\+\+ 示例和相关的文档 Visual Studio 2010年](http://go.microsoft.com/fwlink/?LinkID=178749)