---
title: "omp_get_dynamic |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_get_dynamic
dev_langs: C++
helpviewer_keywords: omp_get_dynamic OpenMP function
ms.assetid: efa843c5-7266-4a75-8db3-22992663d9db
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2715b7b27871f6b6ee0449bf96b81bef727dd45b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ompgetdynamic"></a>omp_get_dynamic
返回一个值，该值指示是否可以由运行时调整后续并行区域中的可用线程数。  
  
## <a name="syntax"></a>语法  
  
```  
int omp_get_dynamic();  
```  
  
## <a name="return-value"></a>返回值  
 如果不为零，则启用动态调整的线程。  
  
## <a name="remarks"></a>备注  
 使用指定的线程的动态调整[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)和[OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)。  
  
 有关详细信息，请参阅[3.1.7 omp_set_dynamic 函数](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)。  
  
## <a name="example"></a>示例  
 请参阅[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)有关的使用示例`omp_get_dynamic`。  
  
## <a name="see-also"></a>请参阅  
 [函数](../../../parallel/openmp/reference/openmp-functions.md)