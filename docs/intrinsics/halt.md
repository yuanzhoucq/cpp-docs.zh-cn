---
title: "__halt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__halt"
  - "__halt_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__halt 内部函数"
  - "HLT 指令"
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __halt
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 暂停微处理器，直到已启用中断、一个屏障不可 \(NMI\)中断或重置发生。  
  
## 语法  
  
```  
void __halt( void );  
```  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__halt`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 `__halt` 功能与 `HLT` 指令等效，并且只能在的核心架构。  有关更多信息，搜索文档， “Intel 体系结构软件开发人员的准则，数量 2:设置命令在该站点引用， [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) ”。  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)