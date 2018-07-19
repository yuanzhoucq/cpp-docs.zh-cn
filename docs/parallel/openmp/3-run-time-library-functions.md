---
title: 3. 运行时库函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d747f775509c6b3b2b95be51d95ea937816d3cd1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688110"
---
# <a name="3-run-time-library-functions"></a>3.运行时库函数
本部分介绍 OpenMP C 和 c + + 运行时库函数。 标头 **\<omp.h >** 声明两种类型，可以用于控制和查询并行执行环境中，以及锁定可用于同步对数据的访问的函数的几个函数。  
  
 类型**omp_lock_t**是一种对象类型能够表示锁时可用，或一个线程拥有锁。 这些锁被称为*简单锁*。  
  
 类型**omp_nest_lock_t**是一种对象类型能够表示任一的锁时可用，或这两个线程的标识的拥有锁和*嵌套计数*（如下所述）。 这些锁被称为*nestable 锁*。  
  
 库函数是具有"C"链接的外部函数。  
  
 本章中的说明分为以下主题：  
  
-   执行环境函数 (请参阅[第 3.1 节](../../parallel/openmp/3-1-execution-environment-functions.md)第 35 页上)。  
  
-   锁定函数 (请参阅[第 3.2 节](../../parallel/openmp/3-2-lock-functions.md)页 41 上)。