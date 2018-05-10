---
title: 4. 环境变量 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: edd4f795a3511358d2b95b93e180b9b21b964dd2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="4-environment-variables"></a>4.环境变量
本部分介绍的 OpenMP C 和 c + + API 环境变量 （或等效的特定于平台的机制） 控制并行代码的执行。  环境变量的名称必须大写。 分配给它们的值区分大小写，并且可能必须前导和尾随空格。  修改程序已开始后的值将被忽略。  
  
 环境变量如下所示：  
  
-   **OMP_SCHEDULE**设置运行时计划类型和块大小。  
  
-   **OMP_NUM_THREADS**设置要在执行过程中使用的线程数。  
  
-   **OMP_DYNAMIC**启用或禁用动态调整的线程数。  
  
-   **OMP_NESTED**启用或禁用嵌套并行度。  
  
 本章中的示例仅演示了如何可能 Unix C shell (csh) 环境中设置这些变量。 Korn shell 和 DOS 环境操作中相似，，如下所示：  
  
 csh:  
 setenv OMP_SCHEDULE"动态"  
  
 ksh:  
 导出 OMP_SCHEDULE ="动态"  
  
 DOS:  
 设置 OMP_SCHEDULE ="动态"