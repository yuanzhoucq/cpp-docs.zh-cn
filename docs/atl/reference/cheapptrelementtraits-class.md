---
title: CHeapPtrElementTraits 类
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CHeapPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CHeapPtrElementTraits class
ms.assetid: 910e0e06-3c8b-4242-bf00-b57eb74fbc77
ms.openlocfilehash: f09da968b264463eba759372e4e0756397e9978e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326878"
---
# <a name="cheapptrelementtraits-class"></a>CHeapPtrElementTraits 类

此类提供在创建堆指针集合时有用的方法、静态函数和 typedef。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template<typename T, class Allocator = ATL::CCRTAllocator>
class CHeapPtrElementTraits :
   public CDefaultElementTraits<ATL::CHeapPtr<T, Allocator>>
```

#### <a name="parameters"></a>参数

*T*<br/>
要存储在集合类中的对象类型。

*分配器*<br/>
要使用的内存分配类。 默认值为[CCRT分配器](../../atl/reference/ccrtallocator-class.md)。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[CHeapPtr元素：：INARGTYPE](#inargtype)|用于向集合类对象添加元素的数据类型。|
|[CHeapPtr元素：：OUTARGTYPE](#outargtype)|用于从集合类对象检索元素的数据类型。|

## <a name="remarks"></a>备注

此类提供用于帮助创建包含堆指针的集合类对象的方法、静态函数和 typedef。 类`CHeapPtrList`派生自`CHeapPtrElementTraits`。

有关详细信息，请参阅[ATL 收集类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[C默认比较特征](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[元素库](../../atl/reference/celementtraitsbase-class.md)

[CDefault元素](../../atl/reference/cdefaultelementtraits-class.md)

`CHeapPtrElementTraits`

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="cheapptrelementtraitsinargtype"></a><a name="inargtype"></a>CHeapPtr元素：：INARGTYPE

用于向集合类对象添加元素的数据类型。

```
typedef CHeapPtr<T, Allocator>& INARGTYPE;
```

## <a name="cheapptrelementtraitsoutargtype"></a><a name="outargtype"></a>CHeapPtr元素：：OUTARGTYPE

用于从集合类对象检索元素的数据类型。

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>另请参阅

[CDefaultElementTraits 类](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[CComHeapPtr 类](../../atl/reference/ccomheapptr-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
