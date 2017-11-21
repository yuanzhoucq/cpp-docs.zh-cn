---
title: "CSimpleArrayEqualHelper 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
dev_langs: C++
helpviewer_keywords: CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0d53e09c64aa19b4e843297b64bad132c64a75a2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
  
##  <a name="isequal"></a>CSimpleArrayEqualHelper::IsEqual  
 测试两个`CSimpleArray`对象是否相等的元素。  
  
```
static bool IsEqual(
    const T& t1,
    const T& t2);
```  
  
### <a name="parameters"></a>参数  
 *t1*  
 一个对象类型为 t。  
  
 *t2*  
 一个对象类型为 t。  
  
### <a name="return-value"></a>返回值  
 如果元素均相等，则返回 false，则返回 true。  
  
## <a name="see-also"></a>另请参阅  
 [CSimpleArray 类](../../atl/reference/csimplearray-class.md)   
 [CSimpleArrayEqualHelperFalse 类](../../atl/reference/csimplearrayequalhelperfalse-class.md)   
 [类概述](../../atl/atl-class-overview.md)
