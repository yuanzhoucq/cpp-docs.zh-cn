---
title: "OMP_SCHEDULE | Microsoft Docs"
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
  - "OMP_SCHEDULE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OMP_SCHEDULE OpenMP environment variable"
ms.assetid: 2295a801-e584-4d2f-826f-7ca4c88846a6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OMP_SCHEDULE
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

，当 `schedule(runtime)` 在 `for` 或 `parallel for` 指令时，指定修改 [schedule](../../../parallel/openmp/reference/schedule.md) 子句的行为。  
  
## 语法  
  
```  
set OMP_SCHEDULE[=type[,size]]  
```  
  
## 备注  
 其中，  
  
 `size`（可选）  
 指定迭代的大小。  `size` 必须是正整数。  ，当 `type` 是静态的，则默认值为 1，但。  无效，当 `type` 是 `runtime`。  
  
 `type`  
 此计划:  
  
-   `dynamic`  
  
-   `guided`  
  
-   `runtime`  
  
-   `static`  
  
## 备注  
 在 OpenMP 标准的 Visual C\+\+ 实现的默认值为 `OMP_SCHEDULE=static,0`。  
  
 有关更多信息，请参见 [4.1 OMP\_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md)。  
  
## 示例  
 以下命令将 **OMP\_SCHEDULE** 环境变量:  
  
```  
set OMP_SCHEDULE="guided,2"  
```  
  
 下面的命令演示当前设置 **OMP\_SCHEDULE** 环境变量:  
  
```  
set OMP_SCHEDULE  
```  
  
## 请参阅  
 [Environment Variables](../../../parallel/openmp/reference/openmp-environment-variables.md)