---
title: "4. 环境变量 |Microsoft 文档"
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
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cef1bac78afbcc8b852c3bd42e0904e1963137c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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