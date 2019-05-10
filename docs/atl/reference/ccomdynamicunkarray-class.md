---
title: CComDynamicUnkArray 类
ms.date: 11/04/2016
f1_keywords:
- CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::Add
- ATLCOM/ATL::CComDynamicUnkArray::begin
- ATLCOM/ATL::CComDynamicUnkArray::clear
- ATLCOM/ATL::CComDynamicUnkArray::end
- ATLCOM/ATL::CComDynamicUnkArray::GetAt
- ATLCOM/ATL::CComDynamicUnkArray::GetCookie
- ATLCOM/ATL::CComDynamicUnkArray::GetSize
- ATLCOM/ATL::CComDynamicUnkArray::GetUnknown
- ATLCOM/ATL::CComDynamicUnkArray::Remove
helpviewer_keywords:
- connection points [C++], managing
- CComDynamicUnkArray class
ms.assetid: 202470d7-9a1b-498f-b96d-659d681acd65
ms.openlocfilehash: 39f137f199db1d7519801c19375baea6cd08db93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259477"
---
# <a name="ccomdynamicunkarray-class"></a>CComDynamicUnkArray 类

此类存储数组的`IUnknown`指针。

## <a name="syntax"></a>语法

```
class CComDynamicUnkArray
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|构造函数。 初始化集合的值为 NULL 和集合大小为零。|
|[CComDynamicUnkArray::~CComDynamicUnkArray](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComDynamicUnkArray::Add](#add)|调用此方法以添加`IUnknown`指向该数组。|
|[CComDynamicUnkArray::begin](#begin)|返回一个指向第一个`IUnknown`集合中的指针。|
|[CComDynamicUnkArray::clear](#clear)|清空该数组。|
|[CComDynamicUnkArray::end](#end)|返回一个指向一个过去的最后一个`IUnknown`集合中的指针。|
|[CComDynamicUnkArray::GetAt](#getat)|检索位于指定索引处的元素。|
|[CComDynamicUnkArray::GetCookie](#getcookie)|调用此方法以获取与关联的 cookie 给定`IUnknown`指针。|
|[CComDynamicUnkArray::GetSize](#getsize)|返回数组的长度。|
|[CComDynamicUnkArray::GetUnknown](#getunknown)|调用此方法以获取`IUnknown`与给定的 cookie 关联的指针。|
|[CComDynamicUnkArray::Remove](#remove)|调用此方法来删除`IUnknown`从数组的指针。|

## <a name="remarks"></a>备注

`CComDynamicUnkArray` 保存动态分配的数组`IUnknown`指针，每个点的连接上的接口。 `CComDynamicUnkArray` 可以使用作为参数[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)模板类。

`CComDynamicUnkArray`方法[开始](#begin)并[最终](#end)可用于循环访问所有连接点 （例如，激发的事件时）。

请参阅[添加到对象的连接点](../../atl/adding-connection-points-to-an-object.md)的详细信息自动创建的连接点的代理。

> [!NOTE]
> **请注意**该类`CComDynamicUnkArray`由**添加类**向导创建一个具有的连接点的控件时。 如果你想要手动指定连接点的数量，将更改从引用`CComDynamicUnkArray`到`CComUnkArray<` *n* `>`，其中*n*是连接点的数量必填。

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="add"></a>  CComDynamicUnkArray::Add

调用此方法以添加`IUnknown`指向该数组。

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>参数

*pUnk*<br/>
`IUnknown`用于添加到数组的指针。

### <a name="return-value"></a>返回值

返回新添加的指针与关联的 cookie。

##  <a name="begin"></a>  CComDynamicUnkArray::begin

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

##  <a name="clear"></a>  CComDynamicUnkArray::clear

清空该数组。

```
void clear();
```

##  <a name="ccomdynamicunkarray"></a>  CComDynamicUnkArray::CComDynamicUnkArray

构造函数。

```
CComDynamicUnkArray();
```

### <a name="remarks"></a>备注

集合大小设置为零并初始化为 NULL 的值。 析构函数释放集合中，如有必要。

##  <a name="dtor"></a>  CComDynamicUnkArray:: ~ CComDynamicUnkArray

析构函数。

```
~CComDynamicUnkArray();
```

### <a name="remarks"></a>备注

释放由类构造函数分配的资源。

##  <a name="end"></a>  CComDynamicUnkArray::end

返回一个指向一个过去的最后一个`IUnknown`集合中的指针。

```
IUnknown**
    end();
```

### <a name="return-value"></a>返回值

一个指向`IUnknown`接口指针。

##  <a name="getat"></a>  CComDynamicUnkArray::GetAt

检索位于指定索引处的元素。

```
IUnknown* GetAt(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索的元素的索引。

### <a name="return-value"></a>返回值

一个指向[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)接口。

##  <a name="getcookie"></a>  CComDynamicUnkArray::GetCookie

调用此方法以获取与关联的 cookie 给定`IUnknown`指针。

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>参数

*ppFind*<br/>
`IUnknown`为其关联的 cookie 是必需的指针。

### <a name="return-value"></a>返回值

返回与关联的 cookie`IUnknown`指针或如果没有匹配的零`IUnknown`找到指针。

### <a name="remarks"></a>备注

如果有多个实例的相同`IUnknown`指针，此函数返回的第一个 cookie。

##  <a name="getsize"></a>  CComDynamicUnkArray::GetSize

返回数组的长度。

```
int GetSize() const;
```

### <a name="return-value"></a>返回值

数组的长度。

##  <a name="getunknown"></a>  CComDynamicUnkArray::GetUnknown

调用此方法以获取`IUnknown`与给定的 cookie 关联的指针。

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>参数

*dwCookie*<br/>
为其 cookie 关联`IUnknown`指针是必需。

### <a name="return-value"></a>返回值

返回`IUnknown`指针或如果不找到任何匹配的 cookie，则为 NULL。

##  <a name="remove"></a>  CComDynamicUnkArray::Remove

调用此方法来删除`IUnknown`从数组的指针。

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>参数

*dwCookie*<br/>
Cookie 引用`IUnknown`指针要从数组中删除。

### <a name="return-value"></a>返回值

如果该指针被删除; 将返回 TRUE否则为 FALSE。

## <a name="see-also"></a>请参阅

[CComUnkArray 类](../../atl/reference/ccomunkarray-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
