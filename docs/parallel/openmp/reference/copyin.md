---
title: copyin |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- copyin
dev_langs:
- C++
helpviewer_keywords:
- copyin OpenMP clause
ms.assetid: 369efa88-613c-4cb1-9e11-7b9ee08a4b25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 32137534a43eeb0b038eae547f9bc19283412159
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688240"
---
# <a name="copyin"></a>copyin
允许访问主线程的值的线程[threadprivate](../../../parallel/openmp/reference/threadprivate.md)变量。  
  
## <a name="syntax"></a>语法  
  
```  
copyin(var)  
```  
  
## <a name="remarks"></a>备注  
 其中，  
  
 `var`  
 `threadprivate`如同它存在并行构造之前，主线程中变量的值用于初始化的变量。  
  
## <a name="remarks"></a>备注  
 `copyin` 适用于以下指令：  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [部分](../../../parallel/openmp/reference/sections-openmp.md)  
  
 有关详细信息，请参阅[2.7.2.7 copyin](../../../parallel/openmp/2-7-2-7-copyin.md)。  
  
## <a name="example"></a>示例  
 请参阅[threadprivate](../../../parallel/openmp/reference/threadprivate.md)有关的使用示例`copyin`。  
  
## <a name="see-also"></a>请参阅  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)