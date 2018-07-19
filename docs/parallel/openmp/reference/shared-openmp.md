---
title: 共享 (OpenMP) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- Shared
dev_langs:
- C++
helpviewer_keywords:
- shared OpenMP clause
ms.assetid: 7887dc95-67a2-462f-a3a2-8e0632bf5d04
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8287f96f80748272e29b22ed5c43c364f4353b86
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691672"
---
# <a name="shared-openmp"></a>shared (OpenMP)
将指定应所有线程间共享一个或多个变量。  
  
## <a name="syntax"></a>语法  
  
```  
shared(var)  
```  
  
## <a name="remarks"></a>备注  
 其中，  
  
 `var`  
 要共享的一个更多个变量。 如果指定多个变量，则请用逗号分隔变量名。  
  
## <a name="remarks"></a>备注  
 若要共享线程间的变量的另一个方法是使用[copyprivate](../../../parallel/openmp/reference/copyprivate.md)子句。  
  
 `shared` 适用于以下指令：  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [部分](../../../parallel/openmp/reference/sections-openmp.md)  
  
 有关详细信息，请参阅[2.7.2.4 共享](../../../parallel/openmp/2-7-2-4-shared.md)。  
  
## <a name="example"></a>示例  
 请参阅[私有](../../../parallel/openmp/reference/private-openmp.md)有关的使用示例`shared`。  
  
## <a name="see-also"></a>请参阅  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)