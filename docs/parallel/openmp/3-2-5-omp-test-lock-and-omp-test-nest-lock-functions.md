---
title: "3.2.5 omp_test_lock 和 omp_test_nest_lock 函数 |Microsoft 文档"
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
ms.assetid: 36818945-c22c-4c24-b754-4e73eba6f3f8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8fcdacdbb38a9bb27e35ada74aa2139be10c6797
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 omp_test_lock 和 omp_test_nest_lock 函数
这些函数尝试设置锁定而不是会阻止线程的执行。 格式如下所示：  
  
```  
#include <omp.h>  
int omp_test_lock(omp_lock_t *lock);  
int omp_test_nest_lock(omp_nest_lock_t *lock);  
```  
  
 自变量必须指向一个初始化的锁定变量。 这些函数尝试中与相同的方式将锁`omp_set_lock`和`omp_set_nest_lock`，只不过它们不会阻止线程的执行。  
  
 简单锁，`omp_test_lock`如果成功地设置锁，函数将返回一个非零值; 否则，它将返回零。  
  
 Nestable 锁，`omp_test_nest_lock`函数返回新的嵌套计数，如果已成功设置锁; 否则，它将返回零。