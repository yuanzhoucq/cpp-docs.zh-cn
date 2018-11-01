---
title: CAutoPtrList 类
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList::CAutoPtrList
helpviewer_keywords:
- CAutoPtrList class
ms.assetid: 11de4aca-28b0-4ff2-a74a-cb602312ffbd
ms.openlocfilehash: a7e5c2db31100da8901deaae61527c65655faa7e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551406"
---
# <a name="cautoptrlist-class"></a>CAutoPtrList 类

构造的智能指针的列表时，此类提供了有用的方法。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template<typename E>
class CAutoPtrList :
   public CAtlList<ATL::CAutoPtr<E>, CAutoPtrElementTraits<E>>
```

#### <a name="parameters"></a>参数

*E*<br/>
指针类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAutoPtrList::CAutoPtrList](#cautoptrlist)|构造函数。|

## <a name="remarks"></a>备注

此类提供构造函数，并派生方法从[CAtlList](../../atl/reference/catllist-class.md)并[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)来帮助列表对象存储智能指针的创建。 该类[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)为一个数组对象提供类似功能。

有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CAtlList](../../atl/reference/catllist-class.md)

`CAutoPtrList`

## <a name="requirements"></a>要求

**标头：** atlcoll.h

##  <a name="cautoptrlist"></a>  CAutoPtrList::CAutoPtrList

构造函数。

```
CAutoPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
块大小，默认值为 10。

### <a name="remarks"></a>备注

块大小为分配的新元素时所需的内存量的度量值。 更大的块大小降低对内存分配例程的调用，但使用更多的资源。

## <a name="see-also"></a>请参阅

[CAtlList 类](../../atl/reference/catllist-class.md)<br/>
[CAutoPtrElementTraits 类](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
