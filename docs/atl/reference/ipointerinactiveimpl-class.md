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
ms.openlocfilehash: 229b8c6803aa7b3817cb3d95474bde0502829f8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326448"
---
# <a name="ipointerinactiveimpl-class"></a>IPointerInactiveImpl 类

此类实现`IUnknown`和[IPointer 非活动](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive)接口方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

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

|名称|说明|
|----------|-----------------|
|[IPointerinactiveimpl：：获取激活策略](#getactivationpolicy)|检索对象的当前激活策略。 ATL 实现返回E_NOTIMPL。|
|[指针非活动化：：在活动鼠标移动上](#oninactivemousemove)|通知对象鼠标指针已移到该对象上，指示该对象可以触发鼠标事件。 ATL 实现返回E_NOTIMPL。|
|[Ipointerinactive：：oninactiveSet游标](#oninactivesetcursor)|设置非活动对象的鼠标指针。 ATL 实现返回E_NOTIMPL。|

## <a name="remarks"></a>备注

非活动对象只是加载或运行的对象。 与活动对象不同，非活动对象无法接收 Windows 鼠标和键盘消息。 因此，非活动对象使用的资源较少，并且通常效率更高。

[IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive)接口允许对象支持最小级别的鼠标交互，同时保持非活动状态。 此功能对控件特别有用。

类`IPointerInactiveImpl`只需返回`IPointerInactive`E_NOTIMPL即可实现这些方法。 但是，它通过在`IUnknown`调试版本中向转储设备发送信息来实现。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)， 创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="ipointerinactiveimplgetactivationpolicy"></a><a name="getactivationpolicy"></a>IPointerinactiveimpl：：获取激活策略

检索对象的当前激活策略。

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IPointerInactive：：在](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy)Windows SDK 中获取激活策略。

## <a name="ipointerinactiveimploninactivemousemove"></a><a name="oninactivemousemove"></a>指针非活动化：：在活动鼠标移动上

通知对象鼠标指针已移到该对象上，指示该对象可以触发鼠标事件。

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

请参阅[IPointerinactive：在](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove)Windows SDK 中打开活动鼠标移动。

## <a name="ipointerinactiveimploninactivesetcursor"></a><a name="oninactivesetcursor"></a>Ipointerinactive：：oninactiveSet游标

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

请参阅[IPointerinactive：：在 Windows SDK 中打开"非活动集游标](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor)"。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
