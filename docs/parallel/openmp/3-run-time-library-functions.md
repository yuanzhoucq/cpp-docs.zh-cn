---
title: "3. 运行时库函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f1cbedf8782c9c5ccb25bda3f8b43df8a526f268
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="3-run-time-library-functions"></a>3.运行时库函数
本部分介绍 OpenMP C 和 c + + 运行时库函数。 标头 **\<omp.h >**声明两种类型，可以用于控制和查询并行执行环境中，以及锁定可用于同步对数据的访问的函数的几个函数。  
  
 类型**omp_lock_t**是一种对象类型能够表示锁时可用，或一个线程拥有锁。 这些锁被称为*简单锁*。  
  
 类型**omp_nest_lock_t**是一种对象类型能够表示任一的锁时可用，或这两个线程的标识的拥有锁和*嵌套计数*（如下所述）。 这些锁被称为*nestable 锁*。  
  
 库函数是具有"C"链接的外部函数。  
  
 本章中的说明分为以下主题：  
  
-   执行环境函数 (请参阅[第 3.1 节](../../parallel/openmp/3-1-execution-environment-functions.md)第 35 页上)。  
  
-   锁定函数 (请参阅[第 3.2 节](../../parallel/openmp/3-2-lock-functions.md)页 41 上)。