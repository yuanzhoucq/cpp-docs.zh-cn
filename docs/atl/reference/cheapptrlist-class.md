---
title: CHeapPtrList 类
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList::CHeapPtrList
helpviewer_keywords:
- CHeapPtrList class
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
ms.openlocfilehash: 0500ab8f76049aeaf1c89355ea5450a93243b734
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326863"
---
# <a name="cheapptrlist-class"></a>CHeapPtrList 类

此类提供构造堆指针列表时有用的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template<typename E, class Allocator = ATL::CCRTAllocator>
class CHeapPtrList
   : public CAtlList<ATL::CHeapPtr<E, Allocator>,
                     CHeapPtrElementTraits<E, Allocator>>
```

#### <a name="parameters"></a>参数

*E*<br/>
要存储在集合类中的对象类型。

*分配器*<br/>
要使用的内存分配类。 默认值为[CCRT分配器](../../atl/reference/ccrtallocator-class.md)。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CHeapPtr 列表：CHeapPtrList](#cheapptrlist)|构造函数。|

## <a name="remarks"></a>备注

此类提供一个构造函数，并从[CAtlList](../../atl/reference/catllist-class.md)和[CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)派生方法，以帮助创建存储堆指针的集合类对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CAtlList](../../atl/reference/catllist-class.md)

`CHeapPtrList`

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="cheapptrlistcheapptrlist"></a><a name="cheapptrlist"></a>CHeapPtr 列表：CHeapPtrList

构造函数。

```
CHeapPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
块大小。

### <a name="remarks"></a>备注

块大小是需要新元素时分配的内存量的度量。 较大的块大小减少了对内存分配例程的调用，但使用的资源更多。

## <a name="see-also"></a>另请参阅

[CAtlList 类](../../atl/reference/catllist-class.md)<br/>
[CHeapPtr 类](../../atl/reference/cheapptr-class.md)<br/>
[CHeapPtrElementTraits 类](../../atl/reference/cheapptrelementtraits-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
