---
title: "_CIcos | Microsoft Docs"
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
  - "_CIcos"
apilocation: 
  - "msvcr90.dll"
  - "msvcrt.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
apitype: "DLLExport"
f1_keywords: 
  - "CIcos"
  - "_CIcos"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CIcos 内部"
  - "CIcos 内部"
ms.assetid: 6fc203fb-66f3-4ead-9784-f85833c26f1b
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CIcos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

计算在堆栈中顶部数的余弦值。  
  
## 语法  
  
```  
void __cdecl _CIcos();  
```  
  
## 备注  
 `cos` 函数的该版本存在编译器理解的专门调用约定。  因为它可以防止拷贝的产生和寄存器分配的帮助，所以加快执行的速度。  
  
 结果值被推送到堆栈顶部。  
  
## 要求  
 **Platform:** x86  
  
## 请参阅  
 [按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [cos、cosf、cosl、cosh、coshf、coshl](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)