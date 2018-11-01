---
title: CHwndRenderTarget 类
ms.date: 11/04/2016
f1_keywords:
- CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::Attach
- AFXRENDERTARGET/CHwndRenderTarget::CheckWindowState
- AFXRENDERTARGET/CHwndRenderTarget::Create
- AFXRENDERTARGET/CHwndRenderTarget::Detach
- AFXRENDERTARGET/CHwndRenderTarget::GetHwnd
- AFXRENDERTARGET/CHwndRenderTarget::GetHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::ReCreate
- AFXRENDERTARGET/CHwndRenderTarget::Resize
- AFXRENDERTARGET/CHwndRenderTarget::m_pHwndRenderTarget
helpviewer_keywords:
- CHwndRenderTarget [MFC], CHwndRenderTarget
- CHwndRenderTarget [MFC], Attach
- CHwndRenderTarget [MFC], CheckWindowState
- CHwndRenderTarget [MFC], Create
- CHwndRenderTarget [MFC], Detach
- CHwndRenderTarget [MFC], GetHwnd
- CHwndRenderTarget [MFC], GetHwndRenderTarget
- CHwndRenderTarget [MFC], ReCreate
- CHwndRenderTarget [MFC], Resize
- CHwndRenderTarget [MFC], m_pHwndRenderTarget
ms.assetid: aa65b69f-7202-46ea-af81-ef325da0b840
ms.openlocfilehash: 439ff0152ec69575f21faa332d8fac4bbe779a16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551861"
---
# <a name="chwndrendertarget-class"></a>CHwndRenderTarget 类

ID2D1HwndRenderTarget 包装器。

## <a name="syntax"></a>语法

```
class CHwndRenderTarget : public CRenderTarget;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CHwndRenderTarget::CHwndRenderTarget](#chwndrendertarget)|构造一个 CHwndRenderTarget 对象从 HWND。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CHwndRenderTarget::Attach](#attach)|附加现有呈现器目标接口的对象|
|[CHwndRenderTarget::CheckWindowState](#checkwindowstate)|指示是否封闭的与此呈现器目标相关联的 HWND。|
|[CHwndRenderTarget::Create](#create)|创建呈现器目标与窗口相关联|
|[CHwndRenderTarget::Detach](#detach)|分离对象中的呈现器目标接口|
|[CHwndRenderTarget::GetHwnd](#gethwnd)|返回与此相关的 HWND 呈现器目标。|
|[CHwndRenderTarget::GetHwndRenderTarget](#gethwndrendertarget)|返回 ID2D1HwndRenderTarget 接口。|
|[CHwndRenderTarget::ReCreate](#recreate)|重新创建呈现器目标与窗口相关联|
|[CHwndRenderTarget::Resize](#resize)|呈现器目标的大小更改为指定的像素大小|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CHwndRenderTarget::operator ID2D1HwndRenderTarget *](#operator_id2d1hwndrendertarget_star)|返回 ID2D1HwndRenderTarget 接口。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CHwndRenderTarget::m_pHwndRenderTarget](#m_phwndrendertarget)|指向 ID2D1HwndRenderTarget 对象的指针。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[CHwndRenderTarget](../../mfc/reference/chwndrendertarget-class.md)

## <a name="requirements"></a>要求

**标头：** afxrendertarget.h

##  <a name="attach"></a>  CHwndRenderTarget::Attach

附加现有呈现器目标接口的对象

```
void Attach(ID2D1HwndRenderTarget* pTarget);
```

### <a name="parameters"></a>参数

*pTarget*<br/>
现有呈现器目标的接口。 不能为 NULL

##  <a name="checkwindowstate"></a>  CHwndRenderTarget::CheckWindowState

指示是否封闭的与此呈现器目标相关联的 HWND。

```
D2D1_WINDOW_STATE CheckWindowState() const;
```

### <a name="return-value"></a>返回值

一个值，指示是否与此相关的 HWND 呈现器目标是封闭的像素。

##  <a name="chwndrendertarget"></a>  CHwndRenderTarget::CHwndRenderTarget

构造一个 CHwndRenderTarget 对象从 HWND。

```
CHwndRenderTarget(HWND hwnd = NULL);
```

### <a name="parameters"></a>参数

*hwnd*<br/>
与此相关的 HWND 呈现器目标

##  <a name="create"></a>  CHwndRenderTarget::Create

创建呈现器目标与窗口相关联

```
BOOL Create(HWND hWnd);
```

### <a name="parameters"></a>参数

*hWnd*<br/>
与此相关的 HWND 呈现器目标

### <a name="return-value"></a>返回值

如果该方法成功，则返回 TRUE。 否则，它将返回 FALSE

##  <a name="detach"></a>  CHwndRenderTarget::Detach

分离对象中的呈现器目标接口

```
ID2D1HwndRenderTarget* Detach();
```

### <a name="return-value"></a>返回值

指向已分离的呈现器目标接口。

##  <a name="gethwnd"></a>  CHwndRenderTarget::GetHwnd

返回与此相关的 HWND 呈现器目标。

```
HWND GetHwnd() const;
```

### <a name="return-value"></a>返回值

与此相关的 HWND 呈现器目标。

##  <a name="gethwndrendertarget"></a>  CHwndRenderTarget::GetHwndRenderTarget

返回 ID2D1HwndRenderTarget 接口。

```
ID2D1HwndRenderTarget* GetHwndRenderTarget();
```

### <a name="return-value"></a>返回值

指向 ID2D1HwndRenderTarget 接口或如果对象尚未初始化，则为 NULL 指针。

##  <a name="m_phwndrendertarget"></a>  CHwndRenderTarget::m_pHwndRenderTarget

指向 ID2D1HwndRenderTarget 对象的指针。

```
ID2D1HwndRenderTarget* m_pHwndRenderTarget;
```

##  <a name="operator_id2d1hwndrendertarget_star"></a>  CHwndRenderTarget::operator ID2D1HwndRenderTarget *

返回 ID2D1HwndRenderTarget 接口。

```
operator ID2D1HwndRenderTarget*();
```

### <a name="return-value"></a>返回值

指向 ID2D1HwndRenderTarget 接口或如果对象尚未初始化，则为 NULL 指针。

##  <a name="recreate"></a>  CHwndRenderTarget::ReCreate

重新创建呈现器目标与窗口相关联

```
BOOL ReCreate(HWND hWnd);
```

### <a name="parameters"></a>参数

*hWnd*<br/>
与此相关的 HWND 呈现器目标

### <a name="return-value"></a>返回值

如果该方法成功，则返回 TRUE。 否则，它返回 FALSE。

##  <a name="resize"></a>  CHwndRenderTarget::Resize

呈现器目标的大小更改为指定的像素大小

```
BOOL Resize(const CD2DSizeU& size);
```

### <a name="parameters"></a>参数

*size*<br/>
与设备像素呈现器目标的新的大小

### <a name="return-value"></a>返回值

如果该方法成功，则返回 TRUE。 否则，它返回 FALSE。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
