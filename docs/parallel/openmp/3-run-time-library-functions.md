---
title: "3.运行时库函数 | Microsoft Docs"
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
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.运行时库函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本部分介绍 OpenMP C 和 c + + 运行时库函数。 标头 **\< omp.h >** 声明了两种类型，可以用于控制和查询并行执行环境中，和锁定可用于同步对数据的访问的函数的几个函数。  
  
 类型 **omp_lock_t** 是一种对象类型能够表示锁定就可用，或一个线程拥有锁。 这些锁被称为 *简单锁*。  
  
 类型 **omp_nest_lock_t** 能够表示的任一对象类型的锁是可用，或这两个线程的标识的，拥有锁和 *嵌套计数* （如下所述）。 这些锁被称为 *可嵌套锁*。  
  
 库函数都是通过"C"链接的外部函数。  
  
 这一章中的说明分为以下主题︰  
  
-   执行环境函数 (请参阅 [第 3.1 节](../../parallel/openmp/3-1-execution-environment-functions.md) 第 35 页上)。  
  
-   锁定的函数 (请参阅 [第 3.2 节](../../parallel/openmp/3-2-lock-functions.md) 第 41 页上)。