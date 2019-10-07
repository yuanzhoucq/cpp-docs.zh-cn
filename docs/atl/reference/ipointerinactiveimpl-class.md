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
ms.openlocfilehash: 6fb5d9f2bcbdeda61f32947bf339d134c4924b72
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495656"
---
# <a name="ipointerinactiveimpl-class"></a>IPointerInactiveImpl 类

此类实现`IUnknown`和[IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive)接口方法。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template<class T>
class IPointerInactiveImpl
```

#### <a name="parameters"></a>参数

*T*<br/>
派生自`IPointerInactiveImpl`的类。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|检索对象的当前激活策略。 ATL 实现返回 E_NOTIMPL。|
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|通知对象: 鼠标指针已移动到该对象, 指示对象可以引发鼠标事件。 ATL 实现返回 E_NOTIMPL。|
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|设置非活动对象的鼠标指针。 ATL 实现返回 E_NOTIMPL。|

## <a name="remarks"></a>备注

非活动对象是一个简单的加载或运行的对象。 与活动对象不同, 非活动对象不能接收 Windows 鼠标和键盘消息。 因此, 非活动对象使用更少的资源, 通常更有效。

[IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive)接口允许对象支持最小级别的鼠标交互, 同时保持不活动状态。 此功能对控件特别有用。

类`IPointerInactiveImpl`只需`IPointerInactive`返回 E_NOTIMPL 即可实现这些方法。 但是, 它通过`IUnknown`在调试版本中将信息发送到转储设备来实现。

**相关文章**[Atl 教程](../../atl/active-template-library-atl-tutorial.md),[创建 atl 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>要求

**标头:** atlctl

##  <a name="getactivationpolicy"></a>IPointerInactiveImpl::GetActivationPolicy

检索对象的当前激活策略。

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IPointerInactive:: GetActivationPolicy](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy) 。

##  <a name="oninactivemousemove"></a>  IPointerInactiveImpl::OnInactiveMouseMove

通知对象: 鼠标指针已移动到该对象, 指示对象可以引发鼠标事件。

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

请参阅 Windows SDK 中的[IPointerInactive:: OnInactiveMouseMove](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove) 。

##  <a name="oninactivesetcursor"></a>IPointerInactiveImpl::OnInactiveSetCursor

设置非活动对象的鼠标指针。

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

请参阅 Windows SDK 中的[IPointerInactive:: OnInactiveSetCursor](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor) 。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
