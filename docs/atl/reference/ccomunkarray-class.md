---
title: CComUnkArray 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComUnkArray
- ATLCOM/ATL::CComUnkArray
- ATLCOM/ATL::CComUnkArray::CComUnkArray
- ATLCOM/ATL::CComUnkArray::Add
- ATLCOM/ATL::CComUnkArray::begin
- ATLCOM/ATL::CComUnkArray::end
- ATLCOM/ATL::CComUnkArray::GetCookie
- ATLCOM/ATL::CComUnkArray::GetUnknown
- ATLCOM/ATL::CComUnkArray::Remove
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], managing
- CComUnkArray class
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7cab0ea4ecf4bfabede365b9e0fbc9d4a02e2515
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057441"
---
# <a name="ccomunkarray-class"></a>CComUnkArray 类

此类存储`IUnknown`指针，它旨在用作参数[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)模板类。

## <a name="syntax"></a>语法

```
template<unsigned int nMaxSize>
class CComUnkArray
```

#### <a name="parameters"></a>参数

*nMaxSize*<br/>
最大数目`IUnknown`可以保存在静态数组的指针。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComUnkArray::CComUnkArray](#ccomunkarray)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComUnkArray::Add](#add)|调用此方法以添加`IUnknown`指向该数组。|
|[CComUnkArray::begin](#begin)|返回一个指向第一个`IUnknown`集合中的指针。|
|[CComUnkArray::end](#end)|返回一个指向一个过去的最后一个`IUnknown`集合中的指针。|
|[CComUnkArray::GetCookie](#getcookie)|调用此方法以获取与关联的 cookie 给定`IUnknown`指针。|
|[CComUnkArray::GetUnknown](#getunknown)|调用此方法以获取`IUnknown`与给定的 cookie 关联的指针。|
|[CComUnkArray::Remove](#remove)|调用此方法来删除`IUnknown`从数组的指针。|

## <a name="remarks"></a>备注

`CComUnkArray` 保存固定的数量的`IUnknown`指针，每个点的连接上的接口。 `CComUnkArray` 可以使用作为参数[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)模板类。 `CComUnkArray<1>` 模板专用化的`CComUnkArray`，经过优化的一个连接点。

`CComUnkArray`方法[开始](#begin)并[最终](#end)可用于循环访问所有连接点 （例如，激发的事件时）。

请参阅[添加到对象的连接点](../../atl/adding-connection-points-to-an-object.md)的详细信息自动创建的连接点的代理。

> [!NOTE]
> **请注意**该类[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)由**添加类**向导创建一个具有的连接点的控件时。 如果你想要手动指定连接点的数量，将更改从引用`CComDynamicUnkArray`到`CComUnkArray<` *n* `>`，其中*n*是连接点的数量必填。

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="add"></a>  CComUnkArray::Add

调用此方法以添加`IUnknown`指向该数组。

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>参数

*pUnk*<br/>
调用此方法以添加`IUnknown`指向该数组。

### <a name="return-value"></a>返回值

返回数组是否不足够大以包含新指针与新添加的指针，则为 0 关联的 cookie。

##  <a name="begin"></a>  CComUnkArray::begin

将指针返回到的集合的开头`IUnknown`接口指针。

```
IUnknown**
    begin();
```

### <a name="return-value"></a>返回值

一个指向`IUnknown`接口指针。

### <a name="remarks"></a>备注

集合中包含指向本地存储为接口的指针`IUnknown`。 您在将每个转换`IUnknown`实际接口类型的接口，然后通过它调用。 不需要首先查询接口。

使用之前`IUnknown`接口，应检查不为 NULL。

##  <a name="ccomunkarray"></a>  CComUnkArray::CComUnkArray

构造函数。

```
CComUnkArray();
```

### <a name="remarks"></a>备注

设置要保存的集合`nMaxSize``IUnknown`指针，并将初始化为 NULL 指针。

##  <a name="end"></a>  CComUnkArray::end

返回一个指向一个过去的最后一个`IUnknown`集合中的指针。

```
IUnknown**
    end();
```

### <a name="return-value"></a>返回值

一个指向`IUnknown`接口指针。

### <a name="remarks"></a>备注

`CComUnkArray`方法`begin`和`end`可用于遍历所有连接点，例如，激发的事件时。

[!code-cpp[NVC_ATL_COM#44](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]

##  <a name="getcookie"></a>  CComUnkArray::GetCookie

调用此方法以获取与关联的 cookie 给定`IUnknown`指针。

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>参数

*ppFind*<br/>
`IUnknown`为其关联的 cookie 是必需的指针。

### <a name="return-value"></a>返回值

返回与关联的 cookie`IUnknown`指针，或者，如果没有匹配的 0`IUnknown`找到指针。

### <a name="remarks"></a>备注

如果有多个实例的相同`IUnknown`指针，此函数返回的第一个 cookie。

##  <a name="getunknown"></a>  CComUnkArray::GetUnknown

调用此方法以获取`IUnknown`与给定的 cookie 关联的指针。

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>参数

*dwCookie*<br/>
为其 cookie 关联`IUnknown`指针是必需。

### <a name="return-value"></a>返回值

返回`IUnknown`指针或如果不找到任何匹配的 cookie，则为 NULL。

##  <a name="remove"></a>  CComUnkArray::Remove

调用此方法来删除`IUnknown`从数组的指针。

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>参数

*dwCookie*<br/>
Cookie 引用`IUnknown`指针要从数组中删除。

### <a name="return-value"></a>返回值

如果指针不删除，则为 FALSE，则返回 TRUE。

## <a name="see-also"></a>请参阅

[CComDynamicUnkArray 类](../../atl/reference/ccomdynamicunkarray-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
