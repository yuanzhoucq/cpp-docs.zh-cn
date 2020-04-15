---
title: CFirePropNotifyEvent 类
ms.date: 11/04/2016
f1_keywords:
- CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnChanged
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnRequestEdit
helpviewer_keywords:
- sinks, notifying of ATL events
- CFirePropNotifyEvent class
- connection points [C++], notifying of events
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
ms.openlocfilehash: 1dfce42176341d74ffc7d9b42f856e71b17bf4f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326968"
---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent 类

此类提供了有关控件属性更改的通知容器接收器的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CFirePropNotifyEvent
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CFireProp通知事件：：火种](#fireonchanged)|（静态）通知容器的接收器控件属性已更改。|
|[CFireProp通知事件：：火对请求编辑](#fireonrequestedit)|（静态）通知容器的接收器控件属性即将更改。|

## <a name="remarks"></a>备注

`CFirePropNotifyEvent`有两种方法通知容器的接收器控件属性已更改或即将更改。

如果实现控件的`IPropertyNotifySink`类派生自 调用`CFirePropNotifyEvent``FireOnRequestEdit`或`FireOnChanged`时调用 的方法。 如果控件类不是派生自`IPropertyNotifySink`，则对这些函数的调用将返回S_OK。

有关创建控件的详细信息，请参阅[ATL 教程](../../atl/active-template-library-atl-tutorial.md)。

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="cfirepropnotifyeventfireonchanged"></a><a name="fireonchanged"></a>CFireProp通知事件：：火种

通知所有连接的[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)接口（在对象的每个连接点上），指定对象属性已更改。

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>参数

*朋 克*<br/>
[在]指向`IUnknown`发送通知的对象的指针。

*脱从ID*<br/>
[在]已更改的属性的标识符。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

即使控件不支持连接点，此函数也是安全的调用。

## <a name="cfirepropnotifyeventfireonrequestedit"></a><a name="fireonrequestedit"></a>CFireProp通知事件：：火对请求编辑

通知所有连接的[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)接口（在对象的每个连接点上），指定对象属性即将更改。

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>参数

*朋 克*<br/>
[在]指向`IUnknown`发送通知的对象的指针。

*脱从ID*<br/>
[在]要更改的属性的标识符。

### <a name="return-value"></a>返回值

标准 HRESULT 值之一。

### <a name="remarks"></a>备注

即使控件不支持连接点，此函数也是安全的调用。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
