---
title: "2.4.3 single Construct | Microsoft Docs"
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
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.4.3 single Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**单个** 指令标识指定的构造关联的构造块仅由团队 \(不一定是主线程\) 的一个线程执行。  **单个** 指令的语法如下所示:  
  
```  
#pragma omp single [clause[[,] clause] ...] new-line  
   structured-block  
```  
  
 子句为下列之一:  
  
 **\(专用** *变量列表* **\)**  
  
 **\(firstprivate** *变量列表* **\)**  
  
 **\(copyprivate** *变量列表* **\)**  
  
 **nowait**  
  
 ，除非 **nowait** 子句指定，包含隐式障碍在 **单个** 构造之后。  
  
 为 **单个** 指令的限制如下所示:  
  
-   唯一 **nowait** 子句可以出现在 **单个** 指令。  
  
-   不能使用 **copyprivate** 子句与 **nowait** 子句。  
  
## 交叉引用:  
  
-   **专用**、 **firstprivate**和 **copyprivate** 子句，请参见中的第 25 页的 [第2.7.2部分](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) 。