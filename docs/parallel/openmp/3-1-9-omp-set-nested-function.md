---
title: "3.1.9 omp_set_nested 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: e4afc3aa-bb96-4314-9849-fd5df5f437d9
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6a70406e42904c40ac81901ffd174991c0ebc54d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="319-ompsetnested-function"></a>3.1.9 omp_set_nested 函数
**Omp_set_nested**函数启用或禁用嵌套并行度。 格式如下所示：  
  
```  
#include <omp.h>  
void omp_set_nested(int nested);  
```  
  
 如果*嵌套*计算结果为 0，嵌套并行处于禁用状态，这是默认设置，以及嵌套并行区域的序列化和由当前线程执行。 如果*嵌套*计算结果为非零值，启用了嵌套并行机制，并将其嵌套的并行区域可能部署以形成嵌套的团队的其他线程。  
  
 此函数具有从一部分的程序中调用时，上面所述的效果其中**omp_in_parallel**函数将返回零。 如果它从一部分的程序调用其中**omp_in_parallel**函数将返回一个非零值，此函数的行为是不确定。  
  
 此调用的优先级高于**OMP_NESTED**环境变量。  
  
 启用嵌套的并行后，用于执行嵌套并行区域的线程数是实现定义的。 因此，允许 OpenMP 符合实现序列化嵌套并行区域，即使启用了嵌套并行度。  
  
## <a name="cross-references"></a>交叉引用：  
  
-   **OMP_NESTED**环境变量，请参阅[部分 4.4](../../parallel/openmp/4-4-omp-nested.md)页 49 上。  
  
-   **omp_in_parallel**函数中，请参阅[部分 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md)在第 38 页上。