---
title: barrier | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- barrier
dev_langs:
- C++
helpviewer_keywords:
- barrier OpenMP directive
ms.assetid: 5c73ad4f-c768-443a-8f9e-4fd8bc2253c7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0008c343130bf47170957204793cf3c85b22f1e3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
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