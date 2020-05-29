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
ms.openlocfilehash: 78cadfff9a278cf080393ab919f3891b201c91aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327767"
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

|名称|说明|
|----------|-----------------|
|[CComHeapPtr：CComHeapPtr](#ccomheapptr)|构造函数。|

## <a name="remarks"></a>备注

`CComHeapPtr`派生自`CHeapPtr`，但使用[CComAllocator 器](../../atl/reference/ccomallocator-class.md)使用 COM 例程分配内存。 有关可用方法，请参阅[CHeapPtr](../../atl/reference/cheapptr-class.md)和[CHeapPtrBase。](../../atl/reference/cheapptrbase-class.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

[CHeapPtr](../../atl/reference/cheapptr-class.md)

`CComHeapPtr`

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="ccomheapptrccomheapptr"></a><a name="ccomheapptr"></a>CComHeapPtr：CComHeapPtr

构造函数。

```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```

### <a name="parameters"></a>参数

*pData*<br/>
一个现有的 `CComHeapPtr` 对象。

### <a name="remarks"></a>备注

可以使用现有`CComHeapPtr`对象选择创建堆指针。 如果是这样，新`CComHeapPtr`对象将负责管理新的指针和资源。

## <a name="see-also"></a>另请参阅

[CHeapPtr 类](../../atl/reference/cheapptr-class.md)<br/>
[CHeapPtrBase 类](../../atl/reference/cheapptrbase-class.md)<br/>
[CComAllocator 类](../../atl/reference/ccomallocator-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
