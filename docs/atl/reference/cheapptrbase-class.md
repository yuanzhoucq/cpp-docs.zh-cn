---
title: CHeapPtrBase 类
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase::AllocateBytes
- ATLCORE/ATL::CHeapPtrBase::Attach
- ATLCORE/ATL::CHeapPtrBase::Detach
- ATLCORE/ATL::CHeapPtrBase::Free
- ATLCORE/ATL::CHeapPtrBase::ReallocateBytes
- ATLCORE/ATL::CHeapPtrBase::m_pData
helpviewer_keywords:
- CHeapPtrBase class
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
ms.openlocfilehash: e247b4f488411ffdcde5d1d9016436c9c36fe793
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747682"
---
# <a name="cheapptrbase-class"></a>CHeapPtrBase 类

此类是多个智能堆指针类的基础。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <class T, class Allocator = CCRTAllocator>
class CHeapPtrBase
```

#### <a name="parameters"></a>参数

*T*<br/>
要存储在堆上的对象类型。

*分配器*<br/>
要使用的内存分配类。 默认情况下，CRT 例程用于分配和释放内存。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CHeapPtrBase：_CHeapPtrBase](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CHeapPtrBase：分配字节](#allocatebytes)|调用此方法以分配内存。|
|[CHeapPtrBase：附加](#attach)|调用此方法以获取现有指针的所有权。|
|[CHeapPtrBase：:D](#detach)|调用此方法以释放指针的所有权。|
|[CHeapPtrBase：免费](#free)|调用此方法以删除 指向 的对象`CHeapPtrBase`。|
|[CHeapPtrBase：：重新分配字节](#reallocatebytes)|调用此方法重新分配内存。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CHeapPtrBase：运算符 T*](#operator_t_star)|强制转换运算符。|
|[CHeapPtrBase：运算符&](#operator_amp)|& 运算符。|
|[CHeapPtrBase：：运算符 ->](#operator_ptr)|指针到成员运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CHeapPtrBase：m_pData](#m_pdata)|指针数据成员变量。|

## <a name="remarks"></a>备注

此类是多个智能堆指针类的基础。 派生类（例如[CHeapPtr](../../atl/reference/cheapptr-class.md)和[CComHeapPtr）](../../atl/reference/ccomheapptr-class.md)添加自己的构造函数和运算符。 有关实现示例，请参阅这些类。

## <a name="requirements"></a>要求

**标题：** atlcore.h

## <a name="cheapptrbaseallocatebytes"></a><a name="allocatebytes"></a>CHeapPtrBase：分配字节

调用此方法以分配内存。

```
bool AllocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>参数

*n 字节*<br/>
要分配的内存字节数。

### <a name="return-value"></a>返回值

如果已成功分配内存，则返回 true，否则为 false。

### <a name="remarks"></a>备注

在调试生成中，如果[CHeapPtrBase：：m_pData](#m_pdata)成员变量当前指向现有值，则断言失败将发生;也就是说，它不等于 NULL。

## <a name="cheapptrbaseattach"></a><a name="attach"></a>CHeapPtrBase：附加

调用此方法以获取现有指针的所有权。

```cpp
void Attach(T* pData) throw();
```

### <a name="parameters"></a>参数

*pData*<br/>
该`CHeapPtrBase`对象将取得此指针的所有权。

### <a name="remarks"></a>备注

当对象`CHeapPtrBase`取得指针的所有权时，当它超出范围时，它将自动删除指针和任何已分配的数据。

在调试生成中，如果[CHeapPtrBase：：m_pData](#m_pdata)成员变量当前指向现有值，则断言失败将发生;也就是说，它不等于 NULL。

## <a name="cheapptrbasecheapptrbase"></a><a name="dtor"></a>CHeapPtrBase：_CHeapPtrBase

析构函数。

```
~CHeapPtrBase() throw();
```

### <a name="remarks"></a>备注

释放所有分配的资源。

## <a name="cheapptrbasedetach"></a><a name="detach"></a>CHeapPtrBase：:D

调用此方法以释放指针的所有权。

```
T* Detach() throw();
```

### <a name="return-value"></a>返回值

返回指针的副本。

### <a name="remarks"></a>备注

释放指针的所有权，将[CHeapPtrBase：：m_pData](#m_pdata)成员变量设置为 NULL，并返回指针的副本。

## <a name="cheapptrbasefree"></a><a name="free"></a>CHeapPtrBase：免费

调用此方法以删除 指向 的对象`CHeapPtrBase`。

```cpp
void Free() throw();
```

### <a name="remarks"></a>备注

释放 下`CHeapPtrBase`指向的对象[，CHeapPtrBase：m_pData](#m_pdata)成员变量设置为 NULL。

## <a name="cheapptrbasem_pdata"></a><a name="m_pdata"></a>CHeapPtrBase：m_pData

指针数据成员变量。

```
T* m_pData;
```

### <a name="remarks"></a>备注

此成员变量保存指针信息。

## <a name="cheapptrbaseoperator-amp"></a><a name="operator_amp"></a>CHeapPtrBase：：运算符&amp;

& 运算符。

```
T** operator&() throw();
```

### <a name="return-value"></a>返回值

返回对象指向的对象的地址`CHeapPtrBase`。

## <a name="cheapptrbaseoperator--gt"></a><a name="operator_ptr"></a>CHeapPtrBase：运算符 -&gt;

指针到成员运算符。

```
T* operator->() const throw();
```

### <a name="return-value"></a>返回值

返回[CHeapPtrBase：m_pData](#m_pdata)成员变量的值。

### <a name="remarks"></a>备注

使用此运算符调用`CHeapPtrBase`对象指向的类中的方法。 在调试生成中，如果指向 NULL，`CHeapPtrBase`则会发生断言失败。

## <a name="cheapptrbaseoperator-t"></a><a name="operator_t_star"></a>CHeapPtrBase：运算符 T*

强制转换运算符。

```
operator T*() const throw();
```

### <a name="remarks"></a>备注

返回[CHeapPtrBase：m_pData](#m_pdata)。

## <a name="cheapptrbasereallocatebytes"></a><a name="reallocatebytes"></a>CHeapPtrBase：：重新分配字节

调用此方法重新分配内存。

```
bool ReallocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>参数

*n 字节*<br/>
要分配的新内存量（以字节为单位）。

### <a name="return-value"></a>返回值

如果已成功分配内存，则返回 true，否则为 false。

## <a name="see-also"></a>请参阅

[CHeapPtr 类](../../atl/reference/cheapptr-class.md)<br/>
[CComHeapPtr 类](../../atl/reference/ccomheapptr-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
