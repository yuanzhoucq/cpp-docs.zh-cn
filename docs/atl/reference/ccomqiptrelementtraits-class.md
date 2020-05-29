---
title: CComQIPtrElementTraits 类
ms.date: 11/04/2016
f1_keywords:
- CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits::INARGTYPE
helpviewer_keywords:
- CComQIPtrElementTraits class
ms.assetid: 9df9250a-5413-4362-b133-332932a597c4
ms.openlocfilehash: 19f2669c157310be02f746672b22f6c0ed005075
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327409"
---
# <a name="ccomqiptrelementtraits-class"></a>CComQIPtrElementTraits 类

此类提供在创建 COM 接口指针集合时有用的方法、静态函数和 typedef。

## <a name="syntax"></a>语法

```
template<typename I, const IID* piid=& __uuidof(I)>
class CComQIPtrElementTraits :
   public CDefaultElementTraits<ATL::CComQIPtr<I, piid>>
```

#### <a name="parameters"></a>参数

*Ⅰ*<br/>
指定要存储的指针类型的 COM 接口。

*皮伊德*<br/>
指向*I*的 IID 的指针。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[CComQIPtr元素：：INARGTYPE](#inargtype)|用于向集合类对象添加元素的数据类型。|

## <a name="remarks"></a>备注

类派生方法并提供类型def，用于创建[CComQIPtr](../../atl/reference/ccomqiptr-class.md) COM 接口指针对象的集合类。 [CInterfaceArray](../../atl/reference/cinterfacearray-class.md)和[CInterfaceList](../../atl/reference/cinterfacelist-class.md)类都使用此类。

有关详细信息，请参阅[ATL 收集类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[C默认比较特征](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[元素库](../../atl/reference/celementtraitsbase-class.md)

[CDefault元素](../../atl/reference/cdefaultelementtraits-class.md)

`CComQIPtrElementTraits`

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="ccomqiptrelementtraitsinargtype"></a><a name="inargtype"></a>CComQIPtr元素：：INARGTYPE

用于向集合类对象添加元素的数据类型。

```
typedef I* INARGTYPE;
```

## <a name="see-also"></a>另请参阅

[CDefaultElementTraits 类](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
