---
title: "_CItan | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CItan"
apilocation: 
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr80.dll"
  - "msvcrt.dll"
  - "msvcr110.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_CItan"
  - "CItan"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CItan 内部"
  - "_CItan 内部"
ms.assetid: d1ea3113-50a2-45a6-b6bc-680fcdcc0928
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# _CItan
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在堆栈中计算值顶部的正切值。  
  
## 语法  
  
```  
void __cdecl _CItan();  
```  
  
## 备注  
 `tan` 函数的该版本存在编译器理解的专门调用约定。  因为函数可以防止拷贝的产生和寄存器分配的帮助，所以加快执行的速度。  
  
 结果值被推送到堆栈顶部。  
  
## 要求  
 **Platform:** x86  
  
## 请参阅  
 [按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [tan, tanf, tanl, tanh, tanhf, tanhl](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)