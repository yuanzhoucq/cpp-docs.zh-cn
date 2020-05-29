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
ms.openlocfilehash: 48c7ad6fe13c5f5fbbe5829c25ce1c27896841be
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318807"
---
# <a name="cautoptrlist-class"></a>CAutoPtrList 类

此类提供在构造智能指针列表时有用的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

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

|名称|说明|
|----------|-----------------|
|[CAutoPtr列表：CAutoPtr列表](#cautoptrlist)|构造函数。|

## <a name="remarks"></a>备注

此类提供一个构造函数，并从[CAtlList](../../atl/reference/catllist-class.md)和[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)派生方法，以帮助创建存储智能指针的列表对象。 类[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)为数组对象提供了类似的函数。

有关详细信息，请参阅[ATL 收集类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CAtlList](../../atl/reference/catllist-class.md)

`CAutoPtrList`

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="cautoptrlistcautoptrlist"></a><a name="cautoptrlist"></a>CAutoPtr列表：CAutoPtr列表

构造函数。

```
CAutoPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
块大小，默认值为 10。

### <a name="remarks"></a>备注

块大小是需要新元素时分配的内存量的度量。 较大的块大小减少了对内存分配例程的调用，但使用的资源更多。

## <a name="see-also"></a>另请参阅

[CAtlList 类](../../atl/reference/catllist-class.md)<br/>
[CAutoPtrElementTraits 类](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
