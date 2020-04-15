---
title: CAutoVectorPtrElementTraits 类
ms.date: 11/04/2016
f1_keywords:
- CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CAutoVectorPtrElementTraits class
ms.assetid: 16b81a56-55fb-46ca-b376-66a1884231a6
ms.openlocfilehash: 956fe39c4d3ba89bb9def2f996dca59905753edb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318745"
---
# <a name="cautovectorptrelementtraits-class"></a>CAutoVectorPtrElementTraits 类

此类提供使用矢量新运算符和删除运算符创建智能指针集合时有用的方法、静态函数和 typedef。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <typename T>
class CAutoVectorPtrElementTraits :
   public CDefaultElementTraits<ATL::CAutoVectorPtr<T>>
```

#### <a name="parameters"></a>参数

*T*<br/>
指针类型。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[C自动矢量元素：：INARGTYPE](#inargtype)|用于向集合类对象添加元素的数据类型。|
|[C自动矢量元素：：OUTARGTYPE](#outargtype)|用于从集合类对象检索元素的数据类型。|

## <a name="remarks"></a>备注

此类提供用于帮助创建包含智能指针的集合类对象的方法、静态函数和 typedef。 与[CAutoPtrElementTraits 不同](../../atl/reference/cautoptrelementtraits-class.md)，此类使用矢量新运算符和删除运算符。

## <a name="inheritance-hierarchy"></a>继承层次结构

[C默认比较特征](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[元素库](../../atl/reference/celementtraitsbase-class.md)

[CDefault元素](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoVectorPtrElementTraits`

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="cautovectorptrelementtraitsinargtype"></a><a name="inargtype"></a>C自动矢量元素：：INARGTYPE

用于向集合类对象添加元素的数据类型。

```
typedef CAutoVectorPtr<T>& INARGTYPE;
```

## <a name="cautovectorptrelementtraitsoutargtype"></a><a name="outargtype"></a>C自动矢量元素：：OUTARGTYPE

用于从集合类对象检索元素的数据类型。

```
typedef T*& OUTARGTYPE;
```

## <a name="see-also"></a>另请参阅

[CDefaultElementTraits 类](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[CAutoVectorPtr 类](../../atl/reference/cautovectorptr-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
