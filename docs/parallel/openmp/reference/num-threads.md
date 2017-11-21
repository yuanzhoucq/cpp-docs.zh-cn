---
title: "num_threads |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: num_threads
dev_langs: C++
helpviewer_keywords: num_threads OpenMP clause
ms.assetid: 09a56fc8-25c7-43e4-bbb5-71cb955d0b93
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d07c2f59572b5e771013d5162f974d865ed97880
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="numthreads"></a>num_threads
在线程团队设置线程的数。  
  
## <a name="syntax"></a>语法  
  
```  
num_threads(num)  
```  
  
## <a name="remarks"></a>备注  
 其中，  
  
 `num`  
 线程数  
  
## <a name="remarks"></a>备注  
 `num_threads`子句具有与相同的功能[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)函数。  
  
 `num_threads`适用于以下指令：  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [部分](../../../parallel/openmp/reference/sections-openmp.md)  
  
 有关详细信息，请参阅[2.3 parallel 构造](../../../parallel/openmp/2-3-parallel-construct.md)。  
  
## <a name="example"></a>示例  
 请参阅[并行](../../../parallel/openmp/reference/parallel.md)有关的使用示例`num_threads`子句。  
  
## <a name="see-also"></a>另请参阅  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)