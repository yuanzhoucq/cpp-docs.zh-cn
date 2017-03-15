---
title: "2.2 Conditional Compilation | Microsoft Docs"
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
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.2 Conditional Compilation
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\_**OPENMP** 宏名由 OpenMP 兼容实现定义为十进制常数 *yyyymm*，将被批准规范的年、月。  此宏不能是预处理指令的 **\#define** 或 **\#undef** 的主题。  
  
```  
#ifdef _OPENMP  
iam = omp_get_thread_num() + index;  
#endif  
```  
  
 如果供应商定义扩展到 OpenMP 中，可以指定附加的预定义宏。