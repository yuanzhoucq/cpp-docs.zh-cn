---
title: omp_get_nested |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_nested
dev_langs:
- C++
helpviewer_keywords:
- omp_get_nested OpenMP function
ms.assetid: e9784847-516e-40d3-89f7-b8b6898d8667
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 59900f0a1aba1cbc3bacc5cd1d8832e60aebe30b
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="ompgetnested"></a>omp_get_nested
返回一个值，该值指示是否启用了嵌套并行度。  
  
## <a name="syntax"></a>语法  
  
```  
int omp_get_nested( );  
```  
  
## <a name="return-value"></a>返回值  
 如果不为零，启用了嵌套并行机制。  
  
## <a name="remarks"></a>备注  
 使用指定嵌套的并行[omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md)和[OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md)。  
  
 有关详细信息，请参阅[3.1.10 omp_get_nested 函数](../../../parallel/openmp/3-1-10-omp-get-nested-function.md)。  
  
## <a name="example"></a>示例  
 请参阅[omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md)有关的使用示例`omp_get_nested`。  
  
## <a name="see-also"></a>请参阅  
 [函数](../../../parallel/openmp/reference/openmp-functions.md)