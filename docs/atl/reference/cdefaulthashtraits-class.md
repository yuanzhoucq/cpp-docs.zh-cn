---
title: "CDefaultHashTraits 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
dev_langs: C++
helpviewer_keywords: CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2407ffdd5d8ea327cd4669f2c33ccda5e0246d6d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdefaulthashtraits-class"></a>CDefaultHashTraits 类
此类提供用于计算哈希值的静态函数。  
  
## <a name="syntax"></a>语法  
  
```
template<typename T>  
class CDefaultHashTraits
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要存储在集合中的数据类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDefaultHashTraits::Hash](#hash)|（静态）调用此函数可计算给定元素的哈希值。|  
  
## <a name="remarks"></a>备注  
 此类包含一个返回给定元素的哈希值的单个静态函数。 使用此类[CDefaultElementTraits 类](../../atl/reference/cdefaultelementtraits-class.md)。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlcoll.h  
  
##  <a name="hash"></a>CDefaultHashTraits::Hash  
 调用此函数可计算给定元素的哈希值。  
  
```
static ULONG Hash(const T& element) throw();
```  
  
### <a name="parameters"></a>参数  
 `element`  
 元素。  
  
### <a name="return-value"></a>返回值  
 返回哈希值。  
  
### <a name="remarks"></a>备注  
 默认哈希算法是非常简单： 返回的值是元素数。 如果需要更复杂的算法，重写此函数。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
