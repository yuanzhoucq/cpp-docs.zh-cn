---
title: CComDynamicUnkarray 类
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
ms.openlocfilehash: 51b1d7e81c98bd5dbcf957b1705e7a717bfb9ab0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747987"
---
# <a name="ccomdynamicunkarray-class"></a>CComDynamicUnkarray 类

此类存储指针数组`IUnknown`。

## <a name="syntax"></a>语法

```
class CComDynamicUnkArray
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComDynamicUnkarray：：CComDynamicUnkarray](#ccomdynamicunkarray)|构造函数。 将集合值初始化为 NULL，将集合大小初始化为零。|
|[CComDynamicUnkarray：~CComDynamicUnkarray](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComDynamicUnkarray：：添加](#add)|调用此方法以向数组添加`IUnknown`指针。|
|[CComDynamicUnkarray：开始](#begin)|返回指向集合中第一`IUnknown`个指针的指针。|
|[CComDynamicUnkarray：：清除](#clear)|清空数组。|
|[CComDynamicUnkarray：：结束](#end)|返回指向集合中最后`IUnknown`一个指针的指针。|
|[CComDynamicUnkarray：：GetAt](#getat)|检索指定索引处的元素。|
|[CComDynamicUnkarray：：获取饼干](#getcookie)|调用此方法获取与给定`IUnknown`指针关联的 Cookie。|
|[CComDynamicUnkarray：：获取Size](#getsize)|返回数组的长度。|
|[CComDynamicUnkarray：获取未知](#getunknown)|调用此方法获取与给定`IUnknown`Cookie 关联的指针。|
|[CComDynamicUnkarray：：删除](#remove)|调用此方法从数组中删除`IUnknown`指针。|

## <a name="remarks"></a>备注

`CComDynamicUnkArray`保存动态分配的`IUnknown`指针数组，每个指针位于连接点上的接口。 `CComDynamicUnkArray`可用作[IConnectPointImpl](../../atl/reference/iconnectionpointimpl-class.md)模板类的参数。

方法`CComDynamicUnkArray`[开始和结束](#begin)[可用于循环](#end)遍历所有连接点（例如，触发事件时）。

有关自动创建连接点代理的详细信息[，请参阅向对象添加连接点](../../atl/adding-connection-points-to-an-object.md)。

> [!NOTE]
> **注意**创建具有`CComDynamicUnkArray`连接点的控件时，"**添加类"** 向导使用该类。 如果要手动指定连接点的数量，请将引用从`CComDynamicUnkArray`更改为`CComUnkArray<` *n* `>`，其中*n*是所需的连接点数。

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ccomdynamicunkarrayadd"></a><a name="add"></a>CComDynamicUnkarray：：添加

调用此方法以向数组添加`IUnknown`指针。

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>参数

*朋 克*<br/>
要`IUnknown`添加到数组的指针。

### <a name="return-value"></a>返回值

返回与新添加的指针关联的 Cookie。

## <a name="ccomdynamicunkarraybegin"></a><a name="begin"></a>CComDynamicUnkarray：开始

返回指向接口指针集合开头的`IUnknown`指针。

```
IUnknown**
    begin();
```

### <a name="return-value"></a>返回值

指向接口指针的`IUnknown`指针。

### <a name="remarks"></a>备注

集合包含指向本地存储为`IUnknown`的接口的指针。 将每个`IUnknown`接口强制转换为真正的接口类型，然后通过该接口类型调用它。 您不需要首先查询接口。

在使用接口`IUnknown`之前，应检查该接口是否为 NULL。

## <a name="ccomdynamicunkarrayclear"></a><a name="clear"></a>CComDynamicUnkarray：：清除

清空数组。

```cpp
void clear();
```

## <a name="ccomdynamicunkarrayccomdynamicunkarray"></a><a name="ccomdynamicunkarray"></a>CComDynamicUnkarray：：CComDynamicUnkarray

构造函数。

```
CComDynamicUnkArray();
```

### <a name="remarks"></a>备注

将集合大小设置为零，并将值初始化为 NULL。 如有必要，析构函数释放集合。

## <a name="ccomdynamicunkarrayccomdynamicunkarray"></a><a name="dtor"></a>CComDynamicUnkarray：~CComDynamicUnkarray

析构函数。

```
~CComDynamicUnkArray();
```

### <a name="remarks"></a>备注

释放类构造函数分配的资源。

## <a name="ccomdynamicunkarrayend"></a><a name="end"></a>CComDynamicUnkarray：：结束

返回指向集合中最后`IUnknown`一个指针的指针。

```
IUnknown**
    end();
```

### <a name="return-value"></a>返回值

指向接口指针的`IUnknown`指针。

## <a name="ccomdynamicunkarraygetat"></a><a name="getat"></a>CComDynamicUnkarray：：GetAt

检索指定索引处的元素。

```
IUnknown* GetAt(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索的元素的索引。

### <a name="return-value"></a>返回值

指向 I[未知](/windows/win32/api/unknwn/nn-unknwn-iunknown)接口的指针。

## <a name="ccomdynamicunkarraygetcookie"></a><a name="getcookie"></a>CComDynamicUnkarray：：获取饼干

调用此方法获取与给定`IUnknown`指针关联的 Cookie。

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>参数

*ppFind*<br/>
需要`IUnknown`关联的 Cookie 的指针。

### <a name="return-value"></a>返回值

返回与`IUnknown`指针关联的 Cookie，如果未找到匹配`IUnknown`的指针，则返回零。

### <a name="remarks"></a>备注

如果同`IUnknown`一指针有多个实例，则此函数将返回第一个指针的 Cookie。

## <a name="ccomdynamicunkarraygetsize"></a><a name="getsize"></a>CComDynamicUnkarray：：获取Size

返回数组的长度。

```
int GetSize() const;
```

### <a name="return-value"></a>返回值

数组的长度。

## <a name="ccomdynamicunkarraygetunknown"></a><a name="getunknown"></a>CComDynamicUnkarray：获取未知

调用此方法获取与给定`IUnknown`Cookie 关联的指针。

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>参数

*dwCookie*<br/>
需要关联`IUnknown`指针的 Cookie。

### <a name="return-value"></a>返回值

如果未找到`IUnknown`匹配的 Cookie，则返回指针或 NULL。

## <a name="ccomdynamicunkarrayremove"></a><a name="remove"></a>CComDynamicUnkarray：：删除

调用此方法从数组中删除`IUnknown`指针。

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>参数

*dwCookie*<br/>
引用要从数组中删除`IUnknown`的指针的 Cookie。

### <a name="return-value"></a>返回值

如果删除指针，则返回 TRUE;如果删除指针，则返回 TRUE。否则 FALSE。

## <a name="see-also"></a>请参阅

[CComUnkArray 类](../../atl/reference/ccomunkarray-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
