---
title: "__readcr4 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__readcr4"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__readcr4 内部函数"
ms.assetid: b841a27b-fe0d-4ee9-b76b-f91d3eb061fa
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __readcr4
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 读取 CR4 注册并返回其值。  
  
## 语法  
  
```  
unsigned __int64 __readcr4(void);  
```  
  
## 返回值  
 在 CR4 寄存器值。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__readcr4`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此内部只有在内核模式，并且，实例只能用作内部。  
  
## 关闭 Microsoft 特定  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)