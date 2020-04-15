---
title: CAutoPtrElementTraits 类
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CAutoPtrElementTraits class
ms.assetid: 777c1b14-6ab7-491f-b9a5-be149e71d4a2
ms.openlocfilehash: ac29116dc9beedf587c42cc0e52f8c9dbaf3d782
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318874"
---
# <a name="cautoptrelementtraits-class"></a>CAutoPtrElementTraits 类

此类提供创建智能指针集合时有用的方法、静态函数和 typedef。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template<typename T>
class CAutoPtrElementTraits
    : public CDefaultElementTraits<ATL::CAutoPtr<T>>
```

#### <a name="parameters"></a>参数

*T*<br/>
指针类型。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[CAutoPtr元素：：INARGTYPE](#inargtype)|用于向集合类对象添加元素的数据类型。|
|[CAutoPtr元素：：OUTARGTYPE](#outargtype)|用于从集合类对象检索元素的数据类型。|

## <a name="remarks"></a>备注

此类提供用于帮助创建包含智能指针的集合类对象的方法、静态函数和 typedef。 类[CAutoPtrarray](../../atl/reference/cautoptrarray-class.md)和[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)派生自`CAutoPtrElementTraits`。 如果构建需要矢量新运算符和删除运算符的智能指针集合，请使用[CAutoVectorPtrElementTraits。](../../atl/reference/cautovectorptrelementtraits-class.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

[C默认比较特征](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[元素库](../../atl/reference/celementtraitsbase-class.md)

[CDefault元素](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoPtrElementTraits`

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="cautoptrelementtraitsinargtype"></a><a name="inargtype"></a>CAutoPtr元素：：INARGTYPE

用于向集合类对象添加元素的数据类型。

```
typedef CAutoPtr<T>& INARGTYPE;
```

## <a name="cautoptrelementtraitsoutargtype"></a><a name="outargtype"></a>CAutoPtr元素：：OUTARGTYPE

用于从集合类对象检索元素的数据类型。

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>另请参阅

[CDefaultElementTraits 类](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
