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
ms.openlocfilehash: d55a6d6bfbcc6921fa0633753365f5799388dc27
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497252"
---
# <a name="ccomdynamicunkarray-class"></a>CComDynamicUnkArray 类

此类存储指针的`IUnknown`数组。

## <a name="syntax"></a>语法

```
class CComDynamicUnkArray
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|构造函数。 将集合值初始化为 NULL，将集合大小初始化为零。|
|[CComDynamicUnkArray：： ~ CComDynamicUnkArray](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CComDynamicUnkArray：： Add](#add)|调用此方法可添加`IUnknown`指向该数组的指针。|
|[CComDynamicUnkArray：： begin](#begin)|返回指向集合中第一个`IUnknown`指针的指针。|
|[CComDynamicUnkArray：： clear](#clear)|清空数组。|
|[CComDynamicUnkArray：： end](#end)|返回指向集合中最后`IUnknown`一个指针之后的一个指针。|
|[CComDynamicUnkArray::GetAt](#getat)|检索指定索引处的元素。|
|[CComDynamicUnkArray::GetCookie](#getcookie)|调用此方法以获取与给定`IUnknown`指针关联的 cookie。|
|[CComDynamicUnkArray::GetSize](#getsize)|返回数组的长度。|
|[CComDynamicUnkArray::GetUnknown](#getunknown)|调用此方法以获取与`IUnknown`给定 cookie 关联的指针。|
|[CComDynamicUnkArray::Remove](#remove)|调用此方法可从数组`IUnknown`中删除指针。|

## <a name="remarks"></a>备注

`CComDynamicUnkArray`保存一个动态分配的`IUnknown`指针数组，其中每个都是连接点上的接口。 `CComDynamicUnkArray`可用作[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)模板类的参数。

`CComDynamicUnkArray`方法[开始](#begin)和[结束](#end)可用于循环遍历所有连接点（例如，触发事件时）。

有关自动创建连接点代理的详细信息，请参阅向[对象添加连接点](../../atl/adding-connection-points-to-an-object.md)。

> [!NOTE]
> **注意**类`CComDynamicUnkArray`由**添加类**向导在创建具有连接点的控件时使用。 如果要手动指定连接点的数目， `CComDynamicUnkArray`请将引用从更改为 `>` `CComUnkArray<` n，其中*n*是所需的连接点的数目。

## <a name="requirements"></a>要求

**标头：** atlcom。h

##  <a name="add"></a>CComDynamicUnkArray：： Add

调用此方法可添加`IUnknown`指向该数组的指针。

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>参数

*pUnk*<br/>
要`IUnknown`添加到数组中的指针。

### <a name="return-value"></a>返回值

返回与新添加的指针关联的 cookie。

##  <a name="begin"></a>CComDynamicUnkArray：： begin

返回指向`IUnknown`接口指针集合的开头的指针。

```
IUnknown**
    begin();
```

### <a name="return-value"></a>返回值

指向`IUnknown`接口指针的指针。

### <a name="remarks"></a>备注

集合包含指向本地存储的接口的`IUnknown`指针。 将每个`IUnknown`接口强制转换为实际接口类型，然后调用它。 不需要先查询接口。

使用`IUnknown`接口之前，应检查其是否不为 NULL。

##  <a name="clear"></a>CComDynamicUnkArray：： clear

清空数组。

```
void clear();
```

##  <a name="ccomdynamicunkarray"></a>CComDynamicUnkArray::CComDynamicUnkArray

构造函数。

```
CComDynamicUnkArray();
```

### <a name="remarks"></a>备注

将集合大小设置为零，并将值初始化为 NULL。 如果需要，析构函数将释放该集合。

##  <a name="dtor"></a>CComDynamicUnkArray：： ~ CComDynamicUnkArray

析构函数。

```
~CComDynamicUnkArray();
```

### <a name="remarks"></a>备注

释放由类构造函数分配的资源。

##  <a name="end"></a>CComDynamicUnkArray：： end

返回指向集合中最后`IUnknown`一个指针之后的一个指针。

```
IUnknown**
    end();
```

### <a name="return-value"></a>返回值

指向`IUnknown`接口指针的指针。

##  <a name="getat"></a>CComDynamicUnkArray：： GetAt

检索指定索引处的元素。

```
IUnknown* GetAt(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索的元素的索引。

### <a name="return-value"></a>返回值

指向[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)接口的指针。

##  <a name="getcookie"></a>CComDynamicUnkArray：： System.windows.application.getcookie

调用此方法以获取与给定`IUnknown`指针关联的 cookie。

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>参数

*ppFind*<br/>
需要相关 cookie 的指针。`IUnknown`

### <a name="return-value"></a>返回值

返回与`IUnknown`指针关联的 cookie; 如果找不到匹配`IUnknown`的指针，则返回零。

### <a name="remarks"></a>备注

如果有多个相同`IUnknown`指针的实例，则此函数将返回第一个实例的 cookie。

##  <a name="getsize"></a>CComDynamicUnkArray：： GetSize

返回数组的长度。

```
int GetSize() const;
```

### <a name="return-value"></a>返回值

数组的长度。

##  <a name="getunknown"></a>CComDynamicUnkArray::GetUnknown

调用此方法以获取与`IUnknown`给定 cookie 关联的指针。

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>参数

*dwCookie*<br/>
需要关联`IUnknown`指针的 cookie。

### <a name="return-value"></a>返回值

`IUnknown`返回指针，或者如果找不到匹配的 cookie，则为 NULL。

##  <a name="remove"></a>CComDynamicUnkArray：： Remove

调用此方法可从数组`IUnknown`中删除指针。

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>参数

*dwCookie*<br/>
引用要从数组`IUnknown`中移除的指针的 cookie。

### <a name="return-value"></a>返回值

如果指针被移除，则返回 TRUE;否则为 FALSE。

## <a name="see-also"></a>请参阅

[CComUnkArray 类](../../atl/reference/ccomunkarray-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
