---
title: "3.2 Lock Functions | Microsoft Docs"
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
ms.assetid: 0ec855c6-55a9-49d7-bee4-5edae6e86a1b
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.2 Lock Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本节描述的功能操作用于同步锁。  
  
 为以下功能，锁变量必须具有类型 **omp\_lock\_t**。  必须通过这些功能仅捕获此变量。  所有死锁函数具有指向 **omp\_lock\_t** 类型的参数。  
  
-   `omp_init_lock` 函数来初始化一个简单的锁。  
  
-   `omp_destroy_lock` 功能移除一个简单的锁。  
  
-   `omp_set_lock` 函数等待，直到简单的锁可用。  
  
-   `omp_unset_lock` 函数释放一个简单的锁。  
  
-   `omp_test_lock` 函数可测试一个简单的锁。  
  
 为以下功能，锁变量必须具有类型 **omp\_nest\_lock\_t**。  必须通过这些功能仅捕获此变量。  所有可套上的死锁函数具有指向 **omp\_nest\_lock\_t** 类型的参数。  
  
-   `omp_init_nest_lock` 函数初始化可套上的锁。  
  
-   `omp_destroy_nest_lock` 功能移除可套上的锁。  
  
-   `omp_set_nest_lock` 函数等待，直到可套上的锁可用。  
  
-   `omp_unset_nest_lock` 函数释放可套上的锁。  
  
-   `omp_test_nest_lock` 函数可测试可套上的锁。  
  
 OpenMP 死锁函数访问锁定变量，因此总是读取和更新锁定变量的当前值。  因此，包括显式 **刷新** 指令确保 OpenMP 程序并不是必需的锁变量值在不同的线程之间保持一致。  \(可能需要 **刷新** 指令使值其他变量一致。\)