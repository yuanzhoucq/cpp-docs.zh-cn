---
title: CComUnkArray 类
ms.date: 11/04/2016
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
helpviewer_keywords:
- connection points [C++], managing
- CComUnkArray class
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
ms.openlocfilehash: c1d2f0296394d3979ef4f152e3f902c89adf5b45
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327307"
---
# <a name="ccomunkarray-class"></a>CComUnkArray 类

此类存储`IUnknown`指针，并设计为用作[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)模板类的参数。

## <a name="syntax"></a>语法

```
template<unsigned int nMaxSize>
class CComUnkArray
```

#### <a name="parameters"></a>参数

*nMaxSize*<br/>
可在静态数组中`IUnknown`持有的指针的最大数量。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComUnkarray：CComUnkarray](#ccomunkarray)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComUnkarray：添加](#add)|调用此方法以向数组添加`IUnknown`指针。|
|[CComUnkarray：开始](#begin)|返回指向集合中第一`IUnknown`个指针的指针。|
|[CComUnkarray：结束](#end)|返回指向集合中最后`IUnknown`一个指针的指针。|
|[CComUnkarray：获取饼干](#getcookie)|调用此方法获取与给定`IUnknown`指针关联的 Cookie。|
|[CComUnkarray：获取未知](#getunknown)|调用此方法获取与给定`IUnknown`Cookie 关联的指针。|
|[CComUnkarray：：删除](#remove)|调用此方法从数组中删除`IUnknown`指针。|

## <a name="remarks"></a>备注

`CComUnkArray`包含固定数量的`IUnknown`指针，每个指针位于连接点上。 `CComUnkArray`可用作[IConnectPointImpl](../../atl/reference/iconnectionpointimpl-class.md)模板类的参数。 `CComUnkArray<1>`是已针对一个`CComUnkArray`连接点优化的模板专门化。

方法`CComUnkArray`[开始和结束](#begin)[可用于循环](#end)遍历所有连接点（例如，触发事件时）。

有关自动创建连接点代理的详细信息[，请参阅向对象添加连接点](../../atl/adding-connection-points-to-an-object.md)。

> [!NOTE]
> **注意**添加**类**向导在创建具有连接点的控件时使用类[CComDynamicUnkarray。](../../atl/reference/ccomdynamicunkarray-class.md) 如果要手动指定连接点的数量，请将引用从`CComDynamicUnkArray`更改为`CComUnkArray<` *n* `>`，其中*n*是所需的连接点数。

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="ccomunkarrayadd"></a><a name="add"></a>CComUnkarray：添加

调用此方法以向数组添加`IUnknown`指针。

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>参数

*朋 克*<br/>
调用此方法以向数组添加`IUnknown`指针。

### <a name="return-value"></a>返回值

返回与新添加的指针关联的 Cookie，如果数组不够大以包含新指针，则返回 0。

## <a name="ccomunkarraybegin"></a><a name="begin"></a>CComUnkarray：开始

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

## <a name="ccomunkarrayccomunkarray"></a><a name="ccomunkarray"></a>CComUnkarray：CComUnkarray

构造函数。

```
CComUnkArray();
```

### <a name="remarks"></a>备注

将集合集集用于`nMaxSize``IUnknown`保存指针，并初始化指向 NULL 的指针。

## <a name="ccomunkarrayend"></a><a name="end"></a>CComUnkarray：结束

返回指向集合中最后`IUnknown`一个指针的指针。

```
IUnknown**
    end();
```

### <a name="return-value"></a>返回值

指向接口指针的`IUnknown`指针。

### <a name="remarks"></a>备注

`CComUnkArray`方法`begin`，`end`可用于循环遍历所有连接点，例如，触发事件时。

[!code-cpp[NVC_ATL_COM#44](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]

## <a name="ccomunkarraygetcookie"></a><a name="getcookie"></a>CComUnkarray：获取饼干

调用此方法获取与给定`IUnknown`指针关联的 Cookie。

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>参数

*ppFind*<br/>
需要`IUnknown`关联的 Cookie 的指针。

### <a name="return-value"></a>返回值

返回与`IUnknown`指针关联的 Cookie，如果未找到匹配`IUnknown`的指针，则返回 0。

### <a name="remarks"></a>备注

如果同`IUnknown`一指针有多个实例，则此函数将返回第一个指针的 Cookie。

## <a name="ccomunkarraygetunknown"></a><a name="getunknown"></a>CComUnkarray：获取未知

调用此方法获取与给定`IUnknown`Cookie 关联的指针。

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>参数

*dwCookie*<br/>
需要关联`IUnknown`指针的 Cookie。

### <a name="return-value"></a>返回值

如果未找到`IUnknown`匹配的 Cookie，则返回指针或 NULL。

## <a name="ccomunkarrayremove"></a><a name="remove"></a>CComUnkarray：：删除

调用此方法从数组中删除`IUnknown`指针。

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>参数

*dwCookie*<br/>
引用要从数组中删除`IUnknown`的指针的 Cookie。

### <a name="return-value"></a>返回值

如果删除指针，则返回 TRUE，否则返回 FALSE。

## <a name="see-also"></a>另请参阅

[CComDynamicUnkarray 类](../../atl/reference/ccomdynamicunkarray-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
