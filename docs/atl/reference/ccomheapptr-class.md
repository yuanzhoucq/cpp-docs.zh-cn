---
title: CComHeapPtr 类
ms.date: 11/04/2016
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
helpviewer_keywords:
- CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
ms.openlocfilehash: ace8dbb174bd6585e61bd941a60dad28296af72a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273241"
---
# <a name="ccomheapptr-class"></a>CComHeapPtr 类

用于管理堆指针的智能指针类。

## <a name="syntax"></a>语法

```
template<typename T>
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```

#### <a name="parameters"></a>参数

*T*<br/>
要存储在堆上的对象类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComHeapPtr::CComHeapPtr](#ccomheapptr)|构造函数。|

## <a name="remarks"></a>备注

`CComHeapPtr` 派生自`CHeapPtr`，但使用[CComAllocator](../../atl/reference/ccomallocator-class.md)以使用 COM 例程分配内存。 请参阅[CHeapPtr](../../atl/reference/cheapptr-class.md)并[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)为可用的方法。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

[CHeapPtr](../../atl/reference/cheapptr-class.md)

`CComHeapPtr`

## <a name="requirements"></a>要求

**标头：** atlbase.h

##  <a name="ccomheapptr"></a>  CComHeapPtr::CComHeapPtr

构造函数。

```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```

### <a name="parameters"></a>参数

*pData*<br/>
一个现有的 `CComHeapPtr` 对象。

### <a name="remarks"></a>备注

（可选） 可以使用一个现有创建堆指针`CComHeapPtr`对象。 如果是这样，新`CComHeapPtr`对象负责管理的新指针和资源。

## <a name="see-also"></a>请参阅

[CHeapPtr 类](../../atl/reference/cheapptr-class.md)<br/>
[CHeapPtrBase 类](../../atl/reference/cheapptrbase-class.md)<br/>
[CComAllocator 类](../../atl/reference/ccomallocator-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
