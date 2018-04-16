---
title: "3.2 锁函数 |Microsoft 文档"
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
ms.assetid: 0ec855c6-55a9-49d7-bee4-5edae6e86a1b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 151c809a7bd28a2e4384371f5cec3bd192eed9d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="32-lock-functions"></a>3.2 锁函数
本节中所述的函数操作用于同步的锁。  
  
 对于以下函数，锁定变量必须具有类型**omp_lock_t**。 此变量仅必须通过这些函数来访问。 所有锁函数都需要具有到指针参数**omp_lock_t**类型。  
  
-   `omp_init_lock`函数初始化简单锁。  
  
-   `omp_destroy_lock`函数中删除一个简单的锁定。  
  
-   `omp_set_lock`函数等待，直到简单锁是可用。  
  
-   `omp_unset_lock`函数释放简单锁。  
  
-   `omp_test_lock`函数测试一个简单的锁定。  
  
 对于以下函数，锁定变量必须具有类型**omp_nest_lock_t**。  此变量仅必须通过这些函数来访问。 所有 nestable 锁函数需要具有到指针参数**omp_nest_lock_t**类型。  
  
-   `omp_init_nest_lock`函数初始化 nestable 锁。  
  
-   `omp_destroy_nest_lock`函数中移除 nestable 锁。  
  
-   `omp_set_nest_lock`函数等待，直到 nestable 锁时可用。  
  
-   `omp_unset_nest_lock`函数释放 nestable 锁。  
  
-   `omp_test_nest_lock`函数测试 nestable 锁。  
  
 OpenMP 锁函数访问它们始终读取和更新的锁定变量的最新值的方式的锁定变量。 因此，不需要的 OpenMP 程序以包括显式**刷新**指令以确保锁定变量的值在不同线程之间保持一致。 (可能有需要**刷新**指令以使其他变量的值保持一致。)