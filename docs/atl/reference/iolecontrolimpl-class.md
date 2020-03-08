---
title: IOleControlImpl 类
ms.date: 11/04/2016
f1_keywords:
- IOleControlImpl
- ATLCTL/ATL::IOleControlImpl
- ATLCTL/ATL::IOleControlImpl::FreezeEvents
- ATLCTL/ATL::IOleControlImpl::GetControlInfo
- ATLCTL/ATL::IOleControlImpl::OnAmbientPropertyChange
- ATLCTL/ATL::IOleControlImpl::OnMnemonic
helpviewer_keywords:
- IOleControlImpl class
ms.assetid: 5a4255ad-ede4-49ca-ba9a-07c2e919fa85
ms.openlocfilehash: 3bdb501d8210c98ce982719358564c4937991e12
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864942"
---
# <a name="iolecontrolimpl-class"></a>IOleControlImpl 类

此类提供 `IOleControl` 接口的默认实现并实现 `IUnknown`。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>参数

*T*<br/>
派生自 `IOleControlImpl`的类。

## <a name="members"></a>Members

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IOleControlImpl：： Freezeevents 时调用](#freezeevents)|指示容器是否忽略或接受来自控件的事件。|
|[IOleControlImpl：： GetControlInfo](#getcontrolinfo)|填充有关控件键盘行为的信息。 ATL 实现返回 E_NOTIMPL。|
|[IOleControlImpl：： OnAmbientPropertyChange](#onambientpropertychange)|通知控件一个或多个容器的环境属性已更改。 ATL 实现返回 S_OK。|
|[IOleControlImpl::OnMnemonic](#onmnemonic)|通知控件用户已按下了指定的击键。 ATL 实现返回 E_NOTIMPL。|

## <a name="remarks"></a>备注

类 `IOleControlImpl` 提供[IOleControl](/windows/win32/api/ocidl/nn-ocidl-iolecontrol)接口的默认实现，并通过在调试版本中将信息发送到转储设备来实现 `IUnknown`。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 atl 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>要求

**标头：** atlctl

##  <a name="freezeevents"></a>IOleControlImpl：： Freezeevents 时调用

在 ATL 的实现中，如果 `bFreeze` 为 TRUE，则 `FreezeEvents` 递增控件类的 `m_nFreezeEvents` 数据成员，如果 `bFreeze` 为 FALSE，则递减 `m_nFreezeEvents`。

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>备注

然后 `FreezeEvents` 返回 S_OK。

请参阅 Windows SDK 中的[IOleControl：： freezeevents 时调用](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-freezeevents)。

##  <a name="getcontrolinfo"></a>IOleControlImpl：： GetControlInfo

填充有关控件键盘行为的信息。

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleControl： GetControlInfo](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) 。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

##  <a name="onambientpropertychange"></a>IOleControlImpl：： OnAmbientPropertyChange

通知控件一个或多个容器的环境属性已更改。

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleControl：： OnAmbientPropertyChange](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) 。

##  <a name="onmnemonic"></a>IOleControlImpl::OnMnemonic

通知控件用户已按下了指定的击键。

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleControl：： OnMnemonic](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) 。

## <a name="see-also"></a>另请参阅

[IOleObjectImpl 类](../../atl/reference/ioleobjectimpl-class.md)<br/>
[ActiveX 控件接口](/windows/win32/com/activex-controls-interfaces)<br/>
[类概述](../../atl/atl-class-overview.md)
