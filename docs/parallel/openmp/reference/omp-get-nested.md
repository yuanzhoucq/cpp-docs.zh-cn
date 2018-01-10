---
title: "omp_get_nested |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_get_nested
dev_langs: C++
helpviewer_keywords: omp_get_nested OpenMP function
ms.assetid: e9784847-516e-40d3-89f7-b8b6898d8667
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 557625a40707119633adc1d73775b1e66f67efec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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