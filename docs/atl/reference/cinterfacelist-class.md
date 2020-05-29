---
title: CInterfaceList 类
ms.date: 11/04/2016
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
helpviewer_keywords:
- CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
ms.openlocfilehash: 0a7fd781c63e4ea084cf078e49fc9efb9cfa2d85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326780"
---
# <a name="cinterfacelist-class"></a>CInterfaceList 类

此类提供了构造 COM 接口指针列表时有用的方法。

## <a name="syntax"></a>语法

```
template<class I, const IID* piid =& __uuidof(I)>
class CInterfaceList
   : public CAtlList<ATL::CComQIPtr<I, piid>,
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
|[C接口列表：C接口列表](#cinterfacelist)|接口列表的构造函数。|

## <a name="remarks"></a>备注

此类提供用于创建 COM 接口指针列表的构造函数和派生方法。 当需要数组时，请使用[CInterfaceArray。](../../atl/reference/cinterfacearray-class.md)

有关详细信息，请参阅[ATL 收集类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CAtlList](../../atl/reference/catllist-class.md)

`CInterfaceList`

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="cinterfacelistcinterfacelist"></a><a name="cinterfacelist"></a>C接口列表：C接口列表

接口列表的构造函数。

```
CInterfaceList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
块大小，默认值为 10。

### <a name="remarks"></a>备注

块大小是需要新元素时分配的内存量的度量。 较大的块大小减少了对内存分配例程的调用，但使用的资源更多。

## <a name="see-also"></a>另请参阅

[CAtlList 类](../../atl/reference/catllist-class.md)<br/>
[CComQIPtr 类](../../atl/reference/ccomqiptr-class.md)<br/>
[CComQIPtrElementTraits 类](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
