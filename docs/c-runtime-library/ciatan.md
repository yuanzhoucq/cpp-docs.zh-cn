---
title: "_CIatan | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CIatan"
apilocation: 
  - "msvcr120.dll"
  - "msvcr110.dll"
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr90.dll"
  - "msvcr110_clr0400.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_CIatan"
  - "CIatan"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CIatan 内部"
  - "_CIatan 内部"
ms.assetid: 3baa0429-fe46-4bab-8b00-868e2186dc8c
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# _CIatan
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在堆栈中计算值顶部的反正切值。  
  
## 语法  
  
```  
void __cdecl _CIatan();  
```  
  
## 备注  
 `atan` 函数的该版本存在编译器理解的专门调用约定。  因为它可以防止拷贝的产生和寄存器分配的帮助，所以加快执行的速度。  
  
 结果值被推送到堆栈顶部。  
  
## 要求  
 **Platform:** x86  
  
## 请参阅  
 [按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [atan、atanf、atanl、atan2、atan2f、atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)