---
title: OMP_NESTED |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_NESTED
dev_langs:
- C++
helpviewer_keywords:
- OMP_NESTED OpenMP environment variable
ms.assetid: c43f5287-a548-40d0-bd54-0c6b2b9f9a53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c6b51df88ae700f81cf84250cc06ae24c9131fec
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="ompnested"></a>OMP_NESTED
指定是否已启用嵌套的并行度，除非启用或禁用与嵌套的并行`omp_set_nested`。  
  
## <a name="syntax"></a>语法  
  
```  
set OMP_NESTED[=TRUE | =FALSE]  
```  
  
## <a name="remarks"></a>备注  
 `OMP_NESTED`环境变量可以通过重写[omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md)函数。  
  
 OpenMP 标准的 Visual c + + 实现中的默认值是`OMP_DYNAMIC=FALSE`。  
  
 有关详细信息，请参阅[4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md)。  
  
## <a name="example"></a>示例  
 下面的命令集`OMP_NESTED`为 TRUE 的环境变量：  
  
```  
set OMP_NESTED=TRUE  
```  
  
 下面的命令显示的当前设置`OMP_NESTED`环境变量：  
  
```  
set OMP_NESTED  
```  
  
## <a name="see-also"></a>请参阅  
 [环境变量](../../../parallel/openmp/reference/openmp-environment-variables.md)