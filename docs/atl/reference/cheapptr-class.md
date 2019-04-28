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
ms.openlocfilehash: 8cb35139e707d81a53edb762a2b7fc2ab41ff247
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258671"
---
# <a name="cheapptr-class"></a>CHeapPtr 类

用于管理堆指针的智能指针类。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template<typename T, class Allocator=CCRTAllocator>
class CHeapPtr : public CHeapPtrBase<T, Allocator>
```

#### <a name="parameters"></a>参数

*T*<br/>
要存储在堆上的对象类型。

*Allocator*<br/>
要使用的内存分配类。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CHeapPtr::CHeapPtr](#cheapptr)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CHeapPtr::Allocate](#allocate)|调用此方法来存储对象在堆上分配内存。|
|[CHeapPtr::Reallocate](#reallocate)|调用此方法以重新分配堆上的内存。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CHeapPtr::operator =](#operator_eq)|赋值运算符。|

## <a name="remarks"></a>备注

`CHeapPtr` 派生自[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) ，并默认情况下使用的 CRT 例程 (在[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)) 来分配和释放内存。 该类[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)可能用于构造的堆指针的列表。 另请参阅[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)，它使用 COM 内存分配例程。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

`CHeapPtr`

## <a name="requirements"></a>要求

**标头：** atlcore.h

##  <a name="allocate"></a>  CHeapPtr::Allocate

调用此方法来存储对象在堆上分配内存。

```
bool Allocate(size_t nElements = 1) throw();
```

### <a name="parameters"></a>参数

*nElements*<br/>
用于计算要分配的内存量的元素数。 默认值为 1。

### <a name="return-value"></a>返回值

如果内存已成功，则返回 true 分配，失败的 false。

### <a name="remarks"></a>备注

用于保留足够的内存来存储在堆上分配器例程*nElement*构造函数中定义的类型的对象。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#77](../../atl/codesnippet/cpp/cheapptr-class_1.cpp)]

##  <a name="cheapptr"></a>  CHeapPtr::CHeapPtr

构造函数。

```
CHeapPtr() throw();
explicit CHeapPtr(T* p) throw();
CHeapPtr(CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>参数

*p*<br/>
现有堆指针或`CHeapPtr`。

### <a name="remarks"></a>备注

（可选） 可以使用的现有指针创建堆指针或`CHeapPtr`对象。 如果是这样，新`CHeapPtr`对象负责管理的新指针和资源。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#78](../../atl/codesnippet/cpp/cheapptr-class_2.cpp)]

##  <a name="operator_eq"></a>  CHeapPtr::operator =

赋值运算符。

```
CHeapPtr<T, Allocator>& operator=(
    CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>参数

*p*<br/>
一个现有的 `CHeapPtr` 对象。

### <a name="return-value"></a>返回值

返回对已更新的引用`CHeapPtr`。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#80](../../atl/codesnippet/cpp/cheapptr-class_3.cpp)]

##  <a name="reallocate"></a>  CHeapPtr::Reallocate

调用此方法以重新分配堆上的内存。

```
bool Reallocate(size_t nElements) throw();
```

### <a name="parameters"></a>参数

*nElements*<br/>
新的用于计算要分配的内存量的元素数。

### <a name="return-value"></a>返回值

如果内存已成功，则返回 true 分配，失败的 false。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#79](../../atl/codesnippet/cpp/cheapptr-class_4.cpp)]

## <a name="see-also"></a>请参阅

[CHeapPtrBase 类](../../atl/reference/cheapptrbase-class.md)<br/>
[CCRTAllocator 类](../../atl/reference/ccrtallocator-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
