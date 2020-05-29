---
title: CDefaultCompareTraits 类
ms.date: 11/04/2016
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
helpviewer_keywords:
- CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
ms.openlocfilehash: 8262800ef613424c37c53931d97dd4b1b1a71321
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327064"
---
# <a name="cdefaultcomparetraits-class"></a>CDefaultCompareTraits 类

此类提供默认元素比较函数。

## <a name="syntax"></a>语法

```
template<typename T>
class CDefaultCompareTraits
```

#### <a name="parameters"></a>参数

*T*<br/>
要存储在集合中的数据类型。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[默认比较特征：：比较元素](#compareelements)|（静态）调用此函数以比较两个元素以实现相等性。|
|[默认比较特征：：比较元素排序](#compareelementsordered)|（静态）调用此函数以确定更大和更小的元素。|

## <a name="remarks"></a>备注

此类包含两个静态函数，用于比较存储在集合类对象中的元素。 此类由[CDefaultElementTraits 类](../../atl/reference/cdefaultelementtraits-class.md)使用。

有关详细信息，请参阅[ATL 收集类](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="cdefaultcomparetraitscompareelements"></a><a name="compareelements"></a>默认比较特征：：比较元素

调用此函数以比较两个元素以实现相等性。

```
static bool CompareElements(const T& element1, const T& element2);
```

### <a name="parameters"></a>参数

*元素1*<br/>
第一个元素。

*元素2*<br/>
第二个元素。

### <a name="return-value"></a>返回值

如果元素相等，则返回 true，否则为 false。

### <a name="remarks"></a>备注

此函数的默认实现是相等 （**==**） 运算符。 对于简单数据类型以外的对象，可能需要重写此函数。

## <a name="cdefaultcomparetraitscompareelementsordered"></a><a name="compareelementsordered"></a>默认比较特征：：比较元素排序

调用此函数以确定更大和更小的元素。

```
static int CompareElementsOrdered(const T& element1, const T& element2);
```

### <a name="parameters"></a>参数

*元素1*<br/>
第一个元素。

*元素2*<br/>
第二个元素。

### <a name="return-value"></a>返回值

返回基于下表的整数：

|条件|返回值|
|---------------|------------------|
|*元素1* < *元素2*|<0|
|*元素1* == *元素2*|0|
|*元素1* > *元素2*|>0|

### <a name="remarks"></a>备注

此函数的默认实现使用**==**、**\<** 和**>** 运算符。 对于简单数据类型以外的对象，可能需要重写此函数。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
