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
ms.openlocfilehash: 694127ceccc1d1b55e5da9abca799dff77dcfc60
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423266"
---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent 类

此类提供用于通知容器接收器有关控件属性更改的方法。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
class CFirePropNotifyEvent
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|静止通知容器接收器控件属性已更改。|
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|静止通知容器的接收器，控件属性即将发生更改。|

## <a name="remarks"></a>备注

`CFirePropNotifyEvent` 有两种方法，这些方法可通知容器的接收器控件属性已更改或将要更改。

如果实现控件的类派生自 `IPropertyNotifySink`，则调用 `FireOnRequestEdit` 或 `FireOnChanged`时将调用 `CFirePropNotifyEvent` 方法。 如果控件类不是从 `IPropertyNotifySink`派生的，则对这些函数的调用将返回 S_OK。

有关创建控件的详细信息，请参阅[ATL 教程](../../atl/active-template-library-atl-tutorial.md)。

## <a name="requirements"></a>要求

**标头：** atlctl

##  <a name="fireonchanged"></a>CFirePropNotifyEvent::FireOnChanged

通知所有连接的[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)接口（在对象的每个连接点上）指定的对象属性已更改。

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>parameters

*pUnk*<br/>
中指向发送通知的对象的 `IUnknown` 的指针。

*dispID*<br/>
中已更改的属性的标识符。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

即使您的控件不支持连接点，也可以安全地调用此函数。

##  <a name="fireonrequestedit"></a>CFirePropNotifyEvent::FireOnRequestEdit

通知所有连接的[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)接口（在对象的每个连接点），指定的对象属性将要更改。

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>parameters

*pUnk*<br/>
中指向发送通知的对象的 `IUnknown` 的指针。

*dispID*<br/>
中要更改的属性的标识符。

### <a name="return-value"></a>返回值

标准的 HRESULT 值之一。

### <a name="remarks"></a>备注

即使您的控件不支持连接点，也可以安全地调用此函数。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
