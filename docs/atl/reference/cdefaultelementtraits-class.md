---
title: CDefaultElementTraits 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDefaultElementTraits
- atlcoll/ATL::CDefaultElementTraits
dev_langs:
- C++
helpviewer_keywords:
- CDefaultElementTraits class
ms.assetid: ac5ee610-7957-4b7c-92b6-38ff72e4118e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 16574857f4f5bd4566fcef551fa5e56290b7ce6b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360957"
---
# <a name="cdefaultelementtraits-class"></a>CDefaultElementTraits 类
此类提供的集合类的默认方法和函数。  
  
## <a name="syntax"></a>语法  
  
```
template <typename T>  
class CDefaultElementTraits : public CElementTraitsBase<T>,
    public CDefaultHashTraits<T>,
    public CDefaultCompareTraits<T>
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要存储在集合中的数据类型。  
  
## <a name="remarks"></a>备注  
 此类移动、 复制、 比较和集合类对象中存储的哈希元素提供默认静态函数和方法。 此类派生其函数和方法从[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)， [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)，和[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)，并使用[CElementTraits](../../atl/reference/celementtraits-class.md)， [CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)，和[CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** atlcoll.h  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
