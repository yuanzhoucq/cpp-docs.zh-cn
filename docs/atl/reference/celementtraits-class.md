---
title: "CElementTraits 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CElementTraits
- atlcoll/ATL::CElementTraits
dev_langs: C++
helpviewer_keywords: CElementTraits class
ms.assetid: 496528e5-7f80-4b45-be0c-6f646feb43c5
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ebe629a08170ce011b22595c8b821b278e16faa7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="celementtraits-class"></a>CElementTraits 类
此类是集合类用于为移动、 复制、 比较、 和哈希操作提供方法和函数。  
  
## <a name="syntax"></a>语法  
  
```
template<typename T>  
class CElementTraits : public CDefaultElementTraits<T>
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要存储在集合中的数据类型。  
  
## <a name="remarks"></a>备注  
 此类移动、 复制、 比较和集合类对象中存储的哈希元素提供默认静态函数和方法。 `CElementTraits`通过集合类指定为默认的提供程序的这些操作[CAtlArray](../../atl/reference/catlarray-class.md)， [CAtlList](../../atl/reference/catllist-class.md)， [CRBMap](../../atl/reference/crbmap-class.md)， [CRBMultiMap](../../atl/reference/crbmultimap-class.md)，和[CRBTree](../../atl/reference/crbtree-class.md)。  
  
 默认实现将满足简单数据类型，但如果的集合类用于存储更复杂的对象，必须由用户提供实现替代函数和方法。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlcoll.h  
  
## <a name="see-also"></a>请参阅  
 [CDefaultElementTraits 类](../../atl/reference/cdefaultelementtraits-class.md)   
 [类概述](../../atl/atl-class-overview.md)
