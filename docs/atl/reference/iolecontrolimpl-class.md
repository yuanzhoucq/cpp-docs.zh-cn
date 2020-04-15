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
ms.openlocfilehash: 947ec16e91b99cc42cff90abe7df4a5d13576e98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329620"
---
# <a name="iolecontrolimpl-class"></a>IOleControlImpl 类

此类提供接口和实现`IOleControl``IUnknown`的默认实现。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

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

|名称|说明|
|----------|-----------------|
|[IOleControlimpl：：冻结事件](#freezeevents)|指示容器是否忽略或接受来自控件的事件。|
|[IOleControlimpl：获取控制信息](#getcontrolinfo)|填写有关控件的键盘行为的信息。 ATL 实现返回E_NOTIMPL。|
|[IOleControlimpl：：环境属性更改](#onambientpropertychange)|通知控件一个或多个容器的环境属性已更改。 ATL 实现返回S_OK。|
|[IOleControlimpl：：对内记](#onmnemonic)|通知控件用户已按下指定的击键。 ATL 实现返回E_NOTIMPL。|

## <a name="remarks"></a>备注

类`IOleControlImpl`提供[IOleControl](/windows/win32/api/ocidl/nn-ocidl-iolecontrol)接口的默认实现，并通过`IUnknown`在调试版本中向转储设备发送信息实现。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)， 创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="iolecontrolimplfreezeevents"></a><a name="freezeevents"></a>IOleControlimpl：：冻结事件

在 ATL 的实现`FreezeEvents`中，如果`m_nFreezeEvents``bFreeze`为 TRUE，则增加控制类的数据成员，`m_nFreezeEvents`如果`bFreeze`为 FALSE，则递减。

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>备注

`FreezeEvents`然后返回S_OK。

请参阅[IOleControl：Windows](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-freezeevents) SDK 中的冻结事件。

## <a name="iolecontrolimplgetcontrolinfo"></a><a name="getcontrolinfo"></a>IOleControlimpl：获取控制信息

填写有关控件的键盘行为的信息。

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>备注

请参阅[IOleControl：在](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo)Windows SDK 中获取控制信息。

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

## <a name="iolecontrolimplonambientpropertychange"></a><a name="onambientpropertychange"></a>IOleControlimpl：：环境属性更改

通知控件一个或多个容器的环境属性已更改。

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

请参阅[IOleControl：Windows](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) SDK 中的环境属性更改。

## <a name="iolecontrolimplonmnemonic"></a><a name="onmnemonic"></a>IOleControlimpl：：对内记

通知控件用户已按下指定的击键。

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IOleControl：Windows SDK 中的"OnMnemonic"。](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onmnemonic)

## <a name="see-also"></a>另请参阅

[IOleObjectImpl 类](../../atl/reference/ioleobjectimpl-class.md)<br/>
[ActiveX 控制接口](/windows/win32/com/activex-controls-interfaces)<br/>
[类概述](../../atl/atl-class-overview.md)
