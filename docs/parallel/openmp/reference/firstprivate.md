---
title: "firstprivate | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "firstprivate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "firstprivate OpenMP clause"
ms.assetid: db479766-6d3b-4bbd-b28e-b192d826788c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# firstprivate
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定每个线程都应具有其变量自己的实例，因此，应该初始化该变量与变量的值，，因为它在并行构造之前存在。  
  
## 语法  
  
```  
firstprivate(var)  
```  
  
#### 参数  
  
|Parameter|说明|  
|---------------|--------|  
|`var`|，因为它在并行构造之前，存在一个具有的变量在每个线程和的实例将初始化该变量的值。  如果多于变量中指定，请用逗号分隔的变量名。|  
  
## 备注  
  
## 备注  
 `firstprivate` 适用于以下指令:  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
-   [single](../../../parallel/openmp/reference/single.md)  
  
 有关更多信息，请参见 [2.7.2.2 firstprivate](../../../parallel/openmp/2-7-2-2-firstprivate.md)。  
  
## 示例  
 有关示例 `firstprivate`，请参见。 [private](../../../parallel/openmp/reference/private-openmp.md)的示例。  
  
## 请参阅  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)