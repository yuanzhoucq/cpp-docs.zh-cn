---
title: firstprivate |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- firstprivate
dev_langs:
- C++
helpviewer_keywords:
- firstprivate OpenMP clause
ms.assetid: db479766-6d3b-4bbd-b28e-b192d826788c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 10b5a270feb638a98c060b58e90af8146ff97325
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691698"
---
# <a name="firstprivate"></a>firstprivate
指定每个线程都应具有自己的变量中，实例和变量应用变量的值进行初始化，因为它在并行构造之前已存在。  
  
## <a name="syntax"></a>语法  
  
```  
firstprivate(var)  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`var`|此变量具有实例在每个线程，并将用变量的值初始化，因为它在并行构造之前已存在。 如果指定多个变量，则请用逗号分隔变量名。|  
  
## <a name="remarks"></a>备注  
  
## <a name="remarks"></a>备注  
 `firstprivate` 适用于以下指令：  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [部分](../../../parallel/openmp/reference/sections-openmp.md)  
  
-   [single](../../../parallel/openmp/reference/single.md)  
  
 有关详细信息，请参阅[2.7.2.2 firstprivate](../../../parallel/openmp/2-7-2-2-firstprivate.md)。  
  
## <a name="example"></a>示例  
 有关使用示例`firstprivate`，请参阅中的示例[私有](../../../parallel/openmp/reference/private-openmp.md)。  
  
## <a name="see-also"></a>请参阅  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)