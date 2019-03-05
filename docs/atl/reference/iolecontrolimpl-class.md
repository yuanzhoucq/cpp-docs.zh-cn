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
ms.openlocfilehash: 50119d21b041f37f03ca416a9a56ca9e29ae3344
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263528"
---
# <a name="iolecontrolimpl-class"></a>IOleControlImpl 类

此类提供的默认实现`IOleControl`接口并实现`IUnknown`。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IOleControlImpl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IOleControlImpl::FreezeEvents](#freezeevents)|指示忽略容器，也不接受来自控件的事件。|
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|填写有关控件的键盘行为的信息。 ATL 实现返回 E_NOTIMPL。|
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|通知控件已更改一个或多个容器的环境属性。 ATL 实现返回 S_OK。|
|[IOleControlImpl::OnMnemonic](#onmnemonic)|通知控件用户已按指定的键击。 ATL 实现返回 E_NOTIMPL。|

## <a name="remarks"></a>备注

类`IOleControlImpl`提供的默认实现[IOleControl](/windows/desktop/api/ocidl/nn-ocidl-iolecontrol)接口并实现`IUnknown`信息发送给转储调试中的设备生成。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>要求

**标头：** atlctl.h

##  <a name="freezeevents"></a>  IOleControlImpl::FreezeEvents

在 ATL 的实现中，`FreezeEvents`递增的控件类`m_nFreezeEvents`数据成员如果`bFreeze`为 TRUE，并减少`m_nFreezeEvents`如果`bFreeze`为 FALSE。

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>备注

`FreezeEvents` 然后，返回 S_OK。

请参阅[iolecontrol:: Freezeevents](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-freezeevents) Windows SDK 中。

##  <a name="getcontrolinfo"></a>  IOleControlImpl::GetControlInfo

填写有关控件的键盘行为的信息。

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>备注

请参阅[IOleControl:GetControlInfo](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) Windows SDK 中。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

##  <a name="onambientpropertychange"></a>  IOleControlImpl::OnAmbientPropertyChange

通知控件已更改一个或多个容器的环境属性。

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅[IOleControl::OnAmbientPropertyChange](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) Windows SDK 中。

##  <a name="onmnemonic"></a>  IOleControlImpl::OnMnemonic

通知控件用户已按指定的键击。

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IOleControl::OnMnemonic](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) Windows SDK 中。

## <a name="see-also"></a>请参阅

[IOleObjectImpl 类](../../atl/reference/ioleobjectimpl-class.md)<br/>
[ActiveX 控件接口](/windows/desktop/com/activex-controls-interfaces)<br/>
[类概述](../../atl/atl-class-overview.md)
