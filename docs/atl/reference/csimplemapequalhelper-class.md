---
title: CSimpleMapEqualHelper 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b4bfef99d12ae724c2ca6e70375f08a8dc1fb15b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="csimplemapequalhelper-class"></a>CSimpleMapEqualHelper 类
此类是帮助器[CSimpleMap](../../atl/reference/csimplemap-class.md)类。  
  
## <a name="syntax"></a>语法  
  
```
template <class TKey, class TVal>  
class CSimpleMapEqualHelper
```  
  
#### <a name="parameters"></a>参数  
 `TKey`  
 键的元素。  
  
 `TVal`  
 值元素中。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|（静态）测试两个键相等。|  
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|（静态）测试两个值相等。|  
  
## <a name="remarks"></a>备注  
 此特征类是对的补充`CSimpleMap`类。 它提供用于比较两个方法`CSimpleMap`对象是否相等的元素 （具体而言，键和值的组件）。 默认情况下，键和值进行比较使用`operator==()`，但如果 map 包含缺少其自己的相等运算符的复杂数据类型，可以替代此类以提供额外所需的功能。  
  
## <a name="requirements"></a>要求  
 **标头：** atlsimpcoll.h  
  
##  <a name="isequalkey"></a>  CSimpleMapEqualHelper::IsEqualKey  
 测试两个键相等。  
  
```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```  
  
### <a name="parameters"></a>参数  
 `k1`  
 第一个键。  
  
 `k2`  
 第二个密钥。  
  
### <a name="return-value"></a>返回值  
 如果密钥均相等，则返回 false，则返回 true。  
  
##  <a name="isequalvalue"></a>  CSimpleMapEqualHelper::IsEqualValue  
 测试两个值相等。  
  
```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```  
  
### <a name="parameters"></a>参数  
 *V1*  
 第一个值。  
  
 *V2*  
 第二个值。  
  
### <a name="return-value"></a>返回值  
 如果值均相等，则返回 false，则返回 true。  
  
## <a name="see-also"></a>请参阅  
 [CSimpleMapEqualHelperFalse 类](../../atl/reference/csimplemapequalhelperfalse-class.md)   
 [类概述](../../atl/atl-class-overview.md)
