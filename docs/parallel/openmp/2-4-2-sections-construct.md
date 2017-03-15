---
title: "2.4.2 sections Construct | Microsoft Docs"
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
ms.assetid: e9e6e3ea-7fc9-4925-8f68-92b8a5bb1e76
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.4.2 sections Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**部分** 指令标识指定设置构造将在团队的线程之间拆分 noniterative 的工作划分构造。  每个部分由团队的线程调用一次。  **部分** 指令的语法如下所示:  
  
```  
#pragma omp sections [clause[[,] clause] ...] new-line  
   {  
   [#pragma omp section new-line]  
      structured-block  
   [#pragma omp section new-line  
      structured-block ]  
...  
}  
```  
  
 子句为下列之一:  
  
 **\(专用** *变量列表* **\)**  
  
 **\(firstprivate** *变量列表* **\)**  
  
 **\(lastprivate** *变量列表* **\)**  
  
 **\(减少** *运算符* **:**  *变量列表* **\)**  
  
 **nowait**  
  
 每个部分。 **部分** 指令之后，不过， **部分** 指令对于第一部分是可选的。  **部分** 指令必须在 **部分** 指令内的词法区域出现。  ，除非 **nowait** 指定，包含隐式障碍在 **部分** 构造结束时。  
  
 为 **部分** 指令的限制如下所示:  
  
-   **部分** 指令不能在 **部分** 指令之外的词法区域出现。  
  
-   唯一 **nowait** 子句可以出现在 **部分** 指令。  
  
## 交叉引用:  
  
-   **专用**、 **firstprivate**、 **lastprivate**和 **减少** 子句，请参见中的第 25 页的 [第2.7.2部分](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) 。