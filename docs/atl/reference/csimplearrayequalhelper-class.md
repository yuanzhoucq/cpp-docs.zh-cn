---
title: CSimpleArrayEqualHelper 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d6660f72dbd91a41670b3c5f8772d21caf4b8abc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362123"
---
# <a name="csimplearrayequalhelper-class"></a>CSimpleArrayEqualHelper 类
此类是帮助器[CSimpleArray](../../atl/reference/csimplearray-class.md)类。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
class CSimpleArrayEqualHelper
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 派生的类。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSimpleArrayEqualHelper::IsEqual](#isequal)|（静态）测试两个`CSimpleArray`对象是否相等的元素。|  
  
## <a name="remarks"></a>备注  
 此特征类是对的补充`CSimpleArray`类。 它提供一种方法比较两个元素存储在`CSimpleArray`对象。 默认情况下，对元素进行比较使用**operator=()**，但如果数组包含缺少其自己的相等运算符的复杂数据类型，你将需要重写此类。  
  
## <a name="requirements"></a>要求  
 **标头：** atlsimpcoll.h  
  
##  <a name="isequal"></a>  CSimpleArrayEqualHelper::IsEqual  
 测试两个`CSimpleArray`对象是否相等的元素。  
  
```
static bool IsEqual(
    const T& t1,
    const T& t2);
```  
  
### <a name="parameters"></a>参数  
 *T1*  
 一个对象类型为 t。  
  
 *T2*  
 一个对象类型为 t。  
  
### <a name="return-value"></a>返回值  
 如果元素均相等，则返回 false，则返回 true。  
  
## <a name="see-also"></a>请参阅  
 [CSimpleArray 类](../../atl/reference/csimplearray-class.md)   
 [CSimpleArrayEqualHelperFalse 类](../../atl/reference/csimplearrayequalhelperfalse-class.md)   
 [类概述](../../atl/atl-class-overview.md)
