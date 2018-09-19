---
title: 共享 (OpenMP) |Microsoft Docs
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
ms.openlocfilehash: 078d4b01d2c797fa11c3603c79a341f75e11f18c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115471"
---
# <a name="shared-openmp"></a>shared (OpenMP)
指定应在所有线程之间共享一个或多个变量。  
  
## <a name="syntax"></a>语法  
  
```  
shared(var)  
```  
  
### <a name="parameters"></a>参数
  
*var*<br/>
若要共享的一个或多个变量。 如果指定多个变量，请用逗号分隔的变量名称。  
  
## <a name="remarks"></a>备注  
 共享变量在线程之间的另一个方法是使用[copyprivate](../../../parallel/openmp/reference/copyprivate.md)子句。  
  
 `shared` 适用于以下指令：  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [部分](../../../parallel/openmp/reference/sections-openmp.md)  
  
 有关详细信息，请参阅[2.7.2.4 共享](../../../parallel/openmp/2-7-2-4-shared.md)。  
  
## <a name="example"></a>示例  
 请参阅[私有](../../../parallel/openmp/reference/private-openmp.md)有关的使用示例`shared`。  
  
## <a name="see-also"></a>请参阅  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)