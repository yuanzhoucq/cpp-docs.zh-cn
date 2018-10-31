---
title: CHeapPtrList 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList::CHeapPtrList
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtrList class
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 56dad973f415fa4944bd4561dab94636e10e6539
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50058916"
---
# <a name="cheapptrlist-class"></a>CHeapPtrList 类

构造的堆指针的列表时，此类提供了有用的方法。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template<typename E, class Allocator = ATL::CCRTAllocator>
class CHeapPtrList
   : public CAtlList<ATL::CHeapPtr<E, Allocator>,
                     CHeapPtrElementTraits<E, Allocator>>
```

#### <a name="parameters"></a>参数

*E*<br/>
要存储在集合类的对象类型。

*分配器*<br/>
要使用的内存分配类。 默认值是[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CHeapPtrList::CHeapPtrList](#cheapptrlist)|构造函数。|

## <a name="remarks"></a>备注

此类提供构造函数，并派生方法从[CAtlList](../../atl/reference/catllist-class.md)并[CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)来帮助存储堆指针集合类对象的创建。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CAtlList](../../atl/reference/catllist-class.md)

`CHeapPtrList`

## <a name="requirements"></a>要求

**标头：** atlcoll.h

##  <a name="cheapptrlist"></a>  CHeapPtrList::CHeapPtrList

构造函数。

```
CHeapPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>参数

*nBlockSize*<br/>
块大小。

### <a name="remarks"></a>备注

块大小为分配的新元素时所需的内存量的度量值。 更大的块大小降低对内存分配例程的调用，但使用更多的资源。

## <a name="see-also"></a>请参阅

[CAtlList 类](../../atl/reference/catllist-class.md)<br/>
[CHeapPtr 类](../../atl/reference/cheapptr-class.md)<br/>
[CHeapPtrElementTraits 类](../../atl/reference/cheapptrelementtraits-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
