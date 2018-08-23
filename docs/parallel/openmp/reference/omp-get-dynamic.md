---
title: omp_get_dynamic |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_get_dynamic OpenMP function
ms.assetid: efa843c5-7266-4a75-8db3-22992663d9db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d97cae8091f88c283412b36ef757b03c72f7580d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691258"
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