---
title: CComQIPtrElementTraits 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits::INARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CComQIPtrElementTraits class
ms.assetid: 9df9250a-5413-4362-b133-332932a597c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6dbc0e10f2747b9a9a2ad3ff345a580d4797ea72
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079305"
---
# <a name="ccomqiptrelementtraits-class"></a>CComQIPtrElementTraits 类

创建的 COM 接口指针的集合时，此类提供了方法、 静态函数和有用的 typedef。

## <a name="syntax"></a>语法

```
template<typename I, const IID* piid=& __uuidof(I)>
class CComQIPtrElementTraits : 
   public CDefaultElementTraits<ATL::CComQIPtr<I, piid>>
```

#### <a name="parameters"></a>参数

*I*<br/>
指定要存储的指针的类型的 COM 接口。

*piid*<br/>
指向 IID*我*。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|[CComQIPtrElementTraits::INARGTYPE](#inargtype)|要用于将元素添加到集合类对象的数据类型。|

## <a name="remarks"></a>备注

此类派生方法并提供有用的 typedef 时创建的集合类[CComQIPtr](../../atl/reference/ccomqiptr-class.md) COM 接口指针对象。 此类使用的同时[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)并[CInterfaceList](../../atl/reference/cinterfacelist-class.md)类。

有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CComQIPtrElementTraits`

## <a name="requirements"></a>要求

**标头：** atlcoll.h

##  <a name="inargtype"></a>  CComQIPtrElementTraits::INARGTYPE

要用于将元素添加到集合类对象的数据类型。

```
typedef I* INARGTYPE;
```

## <a name="see-also"></a>请参阅

[CDefaultElementTraits 类](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
