---
title: "__readcr0 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__readcr0"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__readcr0 intrinsic"
ms.assetid: 25bdb093-d83c-48d7-9c0f-224de8e2c61c
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# __readcr0
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 读取 CR0 寄存器并返回其值。  
  
## 语法  
  
```  
unsigned long __readcr0(void);  /* X86 */ unsigned __int64 __readcr0(void);  /* X64 */   
```  
  
## 返回值  
 CR0 寄存器中的值。  
  
## 要求  
  
|内部函数|体系结构|  
|----------|----------|  
|`__readcr0`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此内部函数只在内核模式下可用，例程只能用作内部函数。  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)