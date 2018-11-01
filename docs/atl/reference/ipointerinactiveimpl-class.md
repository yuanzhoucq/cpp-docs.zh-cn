---
title: IPointerInactiveImpl 类
ms.date: 11/04/2016
f1_keywords:
- IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl::GetActivationPolicy
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveMouseMove
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveSetCursor
helpviewer_keywords:
- IPointerInactive ATL implementation
- inactive objects
- IPointerInactiveImpl class
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
ms.openlocfilehash: 2c072dd158616b04d10e4aed091c7e26a3512ce1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487888"
---
# <a name="ipointerinactiveimpl-class"></a>IPointerInactiveImpl 类

此类实现`IUnknown`并[IPointerInactive](/windows/desktop/api/ocidl/nn-ocidl-ipointerinactive)接口方法。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template<class T>
class IPointerInactiveImpl
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IPointerInactiveImpl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|检索对象的当前激活策略。 ATL 实现返回 E_NOTIMPL。|
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|通知鼠标指针移动到它上面，指示该对象的对象可触发鼠标事件。 ATL 实现返回 E_NOTIMPL。|
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|设置鼠标指针处于非活动状态的对象。 ATL 实现返回 E_NOTIMPL。|

## <a name="remarks"></a>备注

非活动状态的对象是指只需加载或运行。 与活动的对象，不同的非活动状态的对象不能接收 Windows 鼠标和键盘消息。 因此，处于非活动状态的对象使用较少的资源，并且通常效率更高。

[IPointerInactive](/windows/desktop/api/ocidl/nn-ocidl-ipointerinactive)接口允许对象支持鼠标交互，同时保持非活动状态的最低级别。 此功能是特别有用的控件。

类`IPointerInactiveImpl`实现`IPointerInactive`方法只返回 E_NOTIMPL。 但是，它实现`IUnknown`信息发送给转储调试中的设备生成。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>要求

**标头：** atlctl.h

##  <a name="getactivationpolicy"></a>  IPointerInactiveImpl::GetActivationPolicy

检索对象的当前激活策略。

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IPointerInactive::GetActivationPolicy](/windows/desktop/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy) Windows SDK 中。

##  <a name="oninactivemousemove"></a>  IPointerInactiveImpl::OnInactiveMouseMove

通知鼠标指针移动到它上面，指示该对象的对象可触发鼠标事件。

```
HRESULT OnInactiveMouseMove(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IPointerInactive::OnInactiveMouseMove](/windows/desktop/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove) Windows SDK 中。

##  <a name="oninactivesetcursor"></a>  IPointerInactiveImpl::OnInactiveSetCursor

设置鼠标指针处于非活动状态的对象。

```
HRESULT OnInactiveSetCursor(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg,
    BOOL fSetAlways);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IPointerInactive::OnInactiveSetCursor](/windows/desktop/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor) Windows SDK 中。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
