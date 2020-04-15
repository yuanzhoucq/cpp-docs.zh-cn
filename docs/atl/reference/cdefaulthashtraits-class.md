---
title: CDefaultHashTraits 类
ms.date: 11/04/2016
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
ms.openlocfilehash: 43932092621d44cfc8b07270df92e2765665f23f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327089"
---
# <a name="cdefaulthashtraits-class"></a>CDefaultHashTraits 类

此类提供用于计算哈希值的静态函数。

## <a name="syntax"></a>语法

```
template<typename T>
class CDefaultHashTraits
```

#### <a name="parameters"></a>参数

*T*<br/>
要存储在集合中的数据类型。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDefaultHashTraits：哈希](#hash)|（静态）调用此函数以计算给定元素的哈希值。|

## <a name="remarks"></a>备注

此类包含单个静态函数，该函数返回给定元素的哈希值。 此类由[CDefaultElementTraits 类](../../atl/reference/cdefaultelementtraits-class.md)使用。

有关详细信息，请参阅[ATL 收集类](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="cdefaulthashtraitshash"></a><a name="hash"></a>CDefaultHashTraits：哈希

调用此函数以计算给定元素的哈希值。

```
static ULONG Hash(const T& element) throw();
```

### <a name="parameters"></a>参数

*元素*<br/>
元素。

### <a name="return-value"></a>返回值

返回哈希值。

### <a name="remarks"></a>备注

默认哈希算法非常简单：返回值是元素编号。 如果需要更复杂的算法，则重写此函数。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
