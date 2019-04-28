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
ms.openlocfilehash: e740d891e279bb29eeef898de52698dc3f04fc67
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258625"
---
# <a name="cinterfacelist-class"></a>CInterfaceList 类

构造的 COM 接口指针的列表时，此类提供了有用的方法。

## <a name="syntax"></a>语法

```
template<class I, const IID* piid =& __uuidof(I)>
class CInterfaceList
   : public CAtlList<ATL::CComQIPtr<I, piid>,
                     CComQIPtrElementTraits<I, piid>>
```

#### <a name="parameters"></a>参数

*I*<br/>
指定要存储的指针的类型的 COM 接口。

*piid*<br/>
指向 IID*我*。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CInterfaceList::CInterfaceList](#cinterfacelist)|接口列表构造函数。|

## <a name="remarks"></a>备注

此类提供一个构造函数和创建的 COM 接口指针的列表的派生的方法。 使用[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)需要数组时。

有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CAtlList](../../atl/reference/catllist-class.md)

`CInterfaceList`

## <a name="requirements"></a>要求

**标头：** atlcoll.h

##  <a name="cinterfacelist"></a>  CInterfaceList::CInterfaceList

接口列表构造函数。

```
CInterfaceList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
块大小，默认值为 10。

### <a name="remarks"></a>备注

块大小为分配的新元素时所需的内存量的度量值。 更大的块大小降低对内存分配例程的调用，但使用更多的资源。

## <a name="see-also"></a>请参阅

[CAtlList 类](../../atl/reference/catllist-class.md)<br/>
[CComQIPtr 类](../../atl/reference/ccomqiptr-class.md)<br/>
[CComQIPtrElementTraits 类](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
