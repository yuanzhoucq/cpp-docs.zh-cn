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
ms.openlocfilehash: 168670709470d7b7fdd77edb3c29d5a9f4049ca3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260079"
---
# <a name="cautovectorptrelementtraits-class"></a>CAutoVectorPtrElementTraits 类

此类提供方法、 静态函数和类型定义时创建的使用向量的新的智能指针的集合和 delete 运算符很有用。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

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

|名称|描述|
|----------|-----------------|
|[CAutoVectorPtrElementTraits::INARGTYPE](#inargtype)|要用于将元素添加到集合类对象的数据类型。|
|[CAutoVectorPtrElementTraits::OUTARGTYPE](#outargtype)|要用于从集合类对象中检索元素的数据类型。|

## <a name="remarks"></a>备注

此类提供帮助包含智能指针集合类对象的创建方法，静态函数和 typedef。 与不同[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)，则此类使用矢量 new 和 delete 运算符。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoVectorPtrElementTraits`

## <a name="requirements"></a>要求

**标头：** atlcoll.h

##  <a name="inargtype"></a>  CAutoVectorPtrElementTraits::INARGTYPE

要用于将元素添加到集合类对象的数据类型。

```
typedef CAutoVectorPtr<T>& INARGTYPE;
```

##  <a name="outargtype"></a>  CAutoVectorPtrElementTraits::OUTARGTYPE

要用于从集合类对象中检索元素的数据类型。

```
typedef T*& OUTARGTYPE;
```

## <a name="see-also"></a>请参阅

[CDefaultElementTraits 类](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[CAutoVectorPtr 类](../../atl/reference/cautovectorptr-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
