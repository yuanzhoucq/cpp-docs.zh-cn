---
title: CInterfaceArray 类
ms.date: 11/04/2016
f1_keywords:
- CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray::CInterfaceArray
helpviewer_keywords:
- CInterfaceArray class
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
ms.openlocfilehash: e6efe31989b06f0977ecff156a8f64053dc64ad1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326798"
---
# <a name="cinterfacearray-class"></a>CInterfaceArray 类

此类提供了构造 COM 接口指针数组时有用的方法。

## <a name="syntax"></a>语法

```
template <class I, const IID* piid=& __uuidof(I)>
class CInterfaceArray :
   public CAtlArray<ATL::CComQIPtr<I, piid>,
                    CComQIPtrElementTraits<I, piid>>
```

#### <a name="parameters"></a>参数

*Ⅰ*<br/>
指定要存储的指针类型的 COM 接口。

*皮伊德*<br/>
指向*I*的 IID 的指针。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C接口数组：C接口数组](#cinterfacearray)|接口数组的构造函数。|

## <a name="remarks"></a>备注

此类提供了用于创建 COM 接口指针数组的构造函数和派生方法。 当需要列表时，请使用[CInterfaceList。](../../atl/reference/cinterfacelist-class.md)

有关详细信息，请参阅[ATL 收集类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CAtlArray`

`CInterfaceArray`

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="cinterfacearraycinterfacearray"></a><a name="cinterfacearray"></a>C接口数组：C接口数组

构造函数。

```
CInterfaceArray() throw();
```

### <a name="remarks"></a>备注

初始化智能指针数组。

## <a name="see-also"></a>另请参阅

[CAtlarray 类](../../atl/reference/catlarray-class.md)<br/>
[CComQIPtr 类](../../atl/reference/ccomqiptr-class.md)<br/>
[CComQIPtrElementTraits 类](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
