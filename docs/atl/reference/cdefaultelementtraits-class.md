---
title: "CDefaultElementTraits 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDefaultElementTraits
- atlcoll/ATL::CDefaultElementTraits
dev_langs:
- C++
helpviewer_keywords:
- CDefaultElementTraits class
ms.assetid: ac5ee610-7957-4b7c-92b6-38ff72e4118e
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 918694610bd029c5cc6f67e7227a9a1461b1408b
ms.lasthandoff: 03/17/2017

---
# <a name="cdefaultelementtraits-class"></a>CDefaultElementTraits 类
此类集合类提供的默认方法和函数。  
  
## <a name="syntax"></a>语法  
  
```
template <typename T>  
class CDefaultElementTraits : public CElementTraitsBase<T>,
    public CDefaultHashTraits<T>,
    public CDefaultCompareTraits<T>
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要在集合中存储的数据类型。  
  
## <a name="remarks"></a>备注  
 此类用于移动、 复制、 比较和哈希存储在集合类对象中的元素提供默认静态函数和方法。 此类派生自其函数和方法从[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)， [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)，和[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)，并通过利用[CElementTraits](../../atl/reference/celementtraits-class.md)， [CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)，和[CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcoll.h  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

