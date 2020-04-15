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
ms.openlocfilehash: 24cf4127c2f429f66143af3a0f49625f23a4e6ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372463"
---
# <a name="chwndrendertarget-class"></a>CHwndRenderTarget 类

ID2D1HwndRender目标包装器。

## <a name="syntax"></a>语法

```
class CHwndRenderTarget : public CRenderTarget;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CHwndRender目标：：CHwndRender目标](#chwndrendertarget)|从 HWND 构造 CHwndRenderTarget 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CHwndRender目标：：附加](#attach)|将现有渲染目标接口附加到对象|
|[CHwndRender目标：：检查窗口状态](#checkwindowstate)|指示是否已占用与此渲染目标关联的 HWND。|
|[CHwndRender目标：：创建](#create)|创建与窗口关联的渲染目标|
|[CHwndRenderTarget：:D埃塔奇](#detach)|从对象分离渲染目标接口|
|[CHwndRender目标：：GetHwnd](#gethwnd)|返回与此渲染目标关联的 HWND。|
|[CHwndRender目标：：获取HwndRender目标](#gethwndrendertarget)|返回 ID2D1HwndRenderTarget 接口。|
|[CHwndRender目标：：重新创建](#recreate)|重新创建与窗口关联的渲染目标|
|[CHwndRender目标：：调整大小](#resize)|将渲染目标的大小更改为指定的像素大小|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CHwndRender目标：：操作员 ID2D1HwndRenderTarget*](#operator_id2d1hwndrendertarget_star)|返回 ID2D1HwndRenderTarget 接口。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CHwndRenderTarget：：m_pHwndRenderTarget](#m_phwndrendertarget)|指向 ID2D1HwndRenderTarget 对象的指针。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CRender目标](../../mfc/reference/crendertarget-class.md)

[CHwndRender目标](../../mfc/reference/chwndrendertarget-class.md)

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="chwndrendertargetattach"></a><a name="attach"></a>CHwndRender目标：：附加

将现有渲染目标接口附加到对象

```
void Attach(ID2D1HwndRenderTarget* pTarget);
```

### <a name="parameters"></a>参数

*p目标*<br/>
现有渲染目标接口。 不能为 NULL

## <a name="chwndrendertargetcheckwindowstate"></a><a name="checkwindowstate"></a>CHwndRender目标：：检查窗口状态

指示是否已占用与此渲染目标关联的 HWND。

```
D2D1_WINDOW_STATE CheckWindowState() const;
```

### <a name="return-value"></a>返回值

指示是否锁定与此渲染目标关联的 HWND 的值。

## <a name="chwndrendertargetchwndrendertarget"></a><a name="chwndrendertarget"></a>CHwndRender目标：：CHwndRender目标

从 HWND 构造 CHwndRenderTarget 对象。

```
CHwndRenderTarget(HWND hwnd = NULL);
```

### <a name="parameters"></a>参数

*霍恩德*<br/>
与此渲染目标关联的 HWND

## <a name="chwndrendertargetcreate"></a><a name="create"></a>CHwndRender目标：：创建

创建与窗口关联的渲染目标

```
BOOL Create(HWND hWnd);
```

### <a name="parameters"></a>参数

*hwnd*<br/>
与此渲染目标关联的 HWND

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE

## <a name="chwndrendertargetdetach"></a><a name="detach"></a>CHwndRenderTarget：:D埃塔奇

从对象分离渲染目标接口

```
ID2D1HwndRenderTarget* Detach();
```

### <a name="return-value"></a>返回值

指向分离的渲染目标接口的指针。

## <a name="chwndrendertargetgethwnd"></a><a name="gethwnd"></a>CHwndRender目标：：GetHwnd

返回与此渲染目标关联的 HWND。

```
HWND GetHwnd() const;
```

### <a name="return-value"></a>返回值

与此渲染目标关联的 HWND。

## <a name="chwndrendertargetgethwndrendertarget"></a><a name="gethwndrendertarget"></a>CHwndRender目标：：获取HwndRender目标

返回 ID2D1HwndRenderTarget 接口。

```
ID2D1HwndRenderTarget* GetHwndRenderTarget();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1HwndRenderTarget 接口或 NULL 的指针。

## <a name="chwndrendertargetm_phwndrendertarget"></a><a name="m_phwndrendertarget"></a>CHwndRenderTarget：：m_pHwndRenderTarget

指向 ID2D1HwndRenderTarget 对象的指针。

```
ID2D1HwndRenderTarget* m_pHwndRenderTarget;
```

## <a name="chwndrendertargetoperator-id2d1hwndrendertarget"></a><a name="operator_id2d1hwndrendertarget_star"></a>CHwndRender目标：：操作员 ID2D1HwndRenderTarget*

返回 ID2D1HwndRenderTarget 接口。

```
operator ID2D1HwndRenderTarget*();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1HwndRenderTarget 接口或 NULL 的指针。

## <a name="chwndrendertargetrecreate"></a><a name="recreate"></a>CHwndRender目标：：重新创建

重新创建与窗口关联的渲染目标

```
BOOL ReCreate(HWND hWnd);
```

### <a name="parameters"></a>参数

*hwnd*<br/>
与此渲染目标关联的 HWND

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE。

## <a name="chwndrendertargetresize"></a><a name="resize"></a>CHwndRender目标：：调整大小

将渲染目标的大小更改为指定的像素大小

```
BOOL Resize(const CD2DSizeU& size);
```

### <a name="parameters"></a>参数

*大小*<br/>
以设备像素为单位的渲染目标的新大小

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
