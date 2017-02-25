---
title: "_CIexp | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CIexp"
apilocation: 
  - "msvcr120.dll"
  - "msvcr80.dll"
  - "msvcr110.dll"
  - "msvcr100.dll"
  - "msvcrt.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "CIexp"
  - "_CIexp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CIexp 内部"
  - "_CIexp 内部"
ms.assetid: f8a3e3b7-fa57-41a3-9983-6c81914cbb55
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# _CIexp
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在堆栈中计算值顶部的指数值。  
  
## 语法  
  
```  
void __cdecl _CIexp();  
```  
  
## 备注  
 `exp` 函数的该版本存在编译器理解的专门调用约定。  因为它可以防止拷贝的产生和寄存器分配的帮助，所以加快执行的速度。  
  
 结果值被推送到堆栈顶部。  
  
## 要求  
 **Platform:** x86  
  
## 请参阅  
 [按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [exp、expf](../c-runtime-library/reference/exp-expf.md)