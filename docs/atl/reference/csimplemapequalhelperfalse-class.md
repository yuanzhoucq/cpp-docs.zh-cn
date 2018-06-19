---
title: CSimpleMapEqualHelperFalse 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualValue
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bebd9c6628924b5927fb48518925bdd665b0ee14
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360013"
---
# <a name="csimplemapequalhelperfalse-class"></a>CSimpleMapEqualHelperFalse 类
此类是帮助器[CSimpleMap](../../atl/reference/csimplemap-class.md)类。  
  
## <a name="syntax"></a>语法  
  
```
template <class TKey, class TVal>  
class CSimpleMapEqualHelperFalse
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|（静态）测试两个键相等。|  
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|（静态）返回 false。|  
  
## <a name="remarks"></a>备注  
 此特征类是对的补充`CSimpleMap`类。 它提供用于比较两个元素中包含的方法`CSimpleMap`对象，具体而言两个值元素或两个关键元素。  
  
 值比较将始终返回 false，并且此外，将调用`ATLASSERT`用 false 如果曾引用自变量。 在其中相等性测试未充分定义的情况下，此类允许包含键/值对，若要正确运行的大多数方法，但失败的如依赖于比较的方法定义完善的方式映射[CSimpleMap::FindVal](../../atl/reference/csimplemap-class.md#findval)。  
  
## <a name="requirements"></a>要求  
 **标头：** atlsimpcoll.h  
  
##  <a name="isequalkey"></a>  CSimpleMapEqualHelperFalse::IsEqualKey  
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
  
### <a name="remarks"></a>备注  
 此方法调用[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)。  
  
##  <a name="isequalvalue"></a>  CSimpleMapEqualHelperFalse::IsEqualValue  
 返回 false。  
  
```
static bool IsEqualValue(const TVal&, const TVal&);
```  
  
### <a name="return-value"></a>返回值  
 返回 false。  
  
### <a name="remarks"></a>备注  
 此方法始终返回 false，并且将调用`ATLASSERT`用 false 如果曾引用自变量。 用途`CSimpleMapEqualHelperFalse::IsEqualValue`是强制使用比较时没有充分定义相等性测试，以定义完善的方式失败的方法。  
  
## <a name="see-also"></a>请参阅  
 [CSimpleMapEqualHelper 类](../../atl/reference/csimplemapequalhelper-class.md)   
 [类概述](../../atl/atl-class-overview.md)
