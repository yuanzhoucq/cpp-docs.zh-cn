---
title: OMP_DYNAMIC |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_DYNAMIC
dev_langs:
- C++
helpviewer_keywords:
- OMP_DYNAMIC OpenMP environment variable
ms.assetid: e306049d-b644-4b73-8b63-46c835bff98b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de4a81d861bf72943a67356577da37c36df63f69
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="ompdynamic"></a>OMP_DYNAMIC
指定运行时 OpenMP 是否可以调整并行区域中的线程数。  
  
## <a name="syntax"></a>语法  
  
```  
set OMP_DYNAMIC[=TRUE | =FALSE]  
```  
  
## <a name="remarks"></a>备注  
 `OMP_DYNAMIC`环境变量可以通过重写[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)函数。  
  
 OpenMP 标准的 Visual c + + 实现中的默认值是`OMP_DYNAMIC=FALSE`。  
  
 有关详细信息，请参阅[4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md)。  
  
## <a name="example"></a>示例  
 下面的命令集`OMP_DYNAMIC`为 TRUE 的环境变量：  
  
```  
set OMP_DYNAMIC=TRUE  
```  
  
 下面的命令显示的当前设置`OMP_DYNAMIC`环境变量：  
  
```  
set OMP_DYNAMIC  
```  
  
## <a name="see-also"></a>请参阅  
 [环境变量](../../../parallel/openmp/reference/openmp-environment-variables.md)