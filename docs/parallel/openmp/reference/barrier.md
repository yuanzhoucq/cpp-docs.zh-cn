---
title: "屏障 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: barrier
dev_langs: C++
helpviewer_keywords: barrier OpenMP directive
ms.assetid: 5c73ad4f-c768-443a-8f9e-4fd8bc2253c7
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5d1e8076ecef41cf60bf34a0622ee53afb05910b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="barrier"></a>barrier
同步所有线程在一个组;所有线程在屏障，都暂停，直到所有线程都执行屏障。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma omp barrier  
```  
  
## <a name="remarks"></a>备注  
 `barrier`指令支持没有 OpenMP 子句。  
  
 有关详细信息，请参阅[2.6.3 barrier 指令](../../../parallel/openmp/2-6-3-barrier-directive.md)。  
  
## <a name="example"></a>示例  
 有关如何使用的示例`barrier`，请参阅[master](../../../parallel/openmp/reference/master.md)。  
  
## <a name="see-also"></a>请参阅  
 [指令](../../../parallel/openmp/reference/openmp-directives.md)