---
title: "_CIsin | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CIsin"
apilocation: 
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcrt.dll"
  - "msvcr110.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcr110_clr0400.dll"
apitype: "DLLExport"
f1_keywords: 
  - "CIsin"
  - "_CIsin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CIsin 内部"
  - "CIsin 内部"
ms.assetid: f215f39a-2341-4f1c-ba8e-cb522451ceb2
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CIsin
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

计算在堆栈中顶部数的正弦值。  
  
## 语法  
  
```  
void __cdecl _CIsin();  
```  
  
## 备注  
 `sin` 函数的该版本存在编译器理解的专门调用约定。  因为它可以防止拷贝的产生和寄存器分配的帮助，所以加快执行的速度。  
  
 结果值被推送到堆栈顶部。  
  
## 要求  
 **Platform:** x86  
  
## 请参阅  
 [按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [sin、sinf、sinl、sinh、sinhf、sinhl](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)