---
title: CHeapPtr 类
ms.date: 11/04/2016
f1_keywords:
- CHeapPtr
- ATLCORE/ATL::CHeapPtr
- ATLCORE/ATL::CHeapPtr::CHeapPtr
- ATLCORE/ATL::CHeapPtr::Allocate
- ATLCORE/ATL::CHeapPtr::Reallocate
helpviewer_keywords:
- CHeapPtr class
ms.assetid: e5c5bfd4-9bf1-4164-8a83-8155fe253454
ms.openlocfilehash: a512aa974cb57072915f887f0c2a20ed1263ffa3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326919"
---
# <a name="cheapptr-class"></a>CHeapPtr 类

用于管理堆指针的智能指针类。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template<typename T, class Allocator=CCRTAllocator>
class CHeapPtr : public CHeapPtrBase<T, Allocator>
```

#### <a name="parameters"></a>参数

*T*<br/>
要存储在堆上的对象类型。

*分配器*<br/>
要使用的内存分配类。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CHeapPtr：CHeapPtr](#cheapptr)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CHeapPtr：分配](#allocate)|调用此方法以在堆上分配内存以存储对象。|
|[CHeapPtr：重新分配](#reallocate)|调用此方法以重新分配堆上的内存。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CHeapPtr：：运算符 |](#operator_eq)|分配运算符。|

## <a name="remarks"></a>备注

`CHeapPtr`派生自[CHeapPtrBase，](../../atl/reference/cheapptrbase-class.md)默认情况下使用 CRT 例程（在[CCRTAllocator）](../../atl/reference/ccrtallocator-class.md)来分配和释放内存。 类[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)可用于构造堆指针的列表。 另请参阅使用 COM 内存分配例程[的 CcomHeapPtr。](../../atl/reference/ccomheapptr-class.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

`CHeapPtr`

## <a name="requirements"></a>要求

**标题：** atlcore.h

## <a name="cheapptrallocate"></a><a name="allocate"></a>CHeapPtr：分配

调用此方法以在堆上分配内存以存储对象。

```
bool Allocate(size_t nElements = 1) throw();
```

### <a name="parameters"></a>参数

*n元素*<br/>
用于计算要分配的内存量的元素数。 默认值为 1。

### <a name="return-value"></a>返回值

如果内存已成功分配，则返回 true，在失败时为 false。

### <a name="remarks"></a>备注

分配器例程用于在堆上保留足够的内存，以存储构造函数中定义的类型的*nElement*对象。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#77](../../atl/codesnippet/cpp/cheapptr-class_1.cpp)]

## <a name="cheapptrcheapptr"></a><a name="cheapptr"></a>CHeapPtr：CHeapPtr

构造函数。

```
CHeapPtr() throw();
explicit CHeapPtr(T* p) throw();
CHeapPtr(CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
现有堆指针或`CHeapPtr`。

### <a name="remarks"></a>备注

可以使用现有指针或`CHeapPtr`对象选择创建堆指针。 如果是这样，新`CHeapPtr`对象将负责管理新的指针和资源。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#78](../../atl/codesnippet/cpp/cheapptr-class_2.cpp)]

## <a name="cheapptroperator-"></a><a name="operator_eq"></a>CHeapPtr：：运算符 |

赋值运算符。

```
CHeapPtr<T, Allocator>& operator=(
    CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
一个现有的 `CHeapPtr` 对象。

### <a name="return-value"></a>返回值

返回对更新`CHeapPtr`的 的 引用。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#80](../../atl/codesnippet/cpp/cheapptr-class_3.cpp)]

## <a name="cheapptrreallocate"></a><a name="reallocate"></a>CHeapPtr：重新分配

调用此方法以重新分配堆上的内存。

```
bool Reallocate(size_t nElements) throw();
```

### <a name="parameters"></a>参数

*n元素*<br/>
用于计算要分配的内存量的新元素数。

### <a name="return-value"></a>返回值

如果内存已成功分配，则返回 true，在失败时为 false。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#79](../../atl/codesnippet/cpp/cheapptr-class_4.cpp)]

## <a name="see-also"></a>另请参阅

[CHeapPtrBase 类](../../atl/reference/cheapptrbase-class.md)<br/>
[CCRTAllocator 类](../../atl/reference/ccrtallocator-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
