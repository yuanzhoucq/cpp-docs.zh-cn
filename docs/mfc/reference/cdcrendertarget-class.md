---
title: CDCRenderTarget 类
ms.date: 11/04/2016
f1_keywords:
- CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::Attach
- AFXRENDERTARGET/CDCRenderTarget::BindDC
- AFXRENDERTARGET/CDCRenderTarget::Create
- AFXRENDERTARGET/CDCRenderTarget::Detach
- AFXRENDERTARGET/CDCRenderTarget::GetDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::m_pDCRenderTarget
helpviewer_keywords:
- CDCRenderTarget [MFC], CDCRenderTarget
- CDCRenderTarget [MFC], Attach
- CDCRenderTarget [MFC], BindDC
- CDCRenderTarget [MFC], Create
- CDCRenderTarget [MFC], Detach
- CDCRenderTarget [MFC], GetDCRenderTarget
- CDCRenderTarget [MFC], m_pDCRenderTarget
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
ms.openlocfilehash: 8c07962c017d160cb3ce5841a75f1ae8a8761641
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753397"
---
# <a name="cdcrendertarget-class"></a>CDCRenderTarget 类

ID2D1DCRenderTarget 的包装器。

## <a name="syntax"></a>语法

```
class CDCRenderTarget : public CRenderTarget;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CDC 渲染目标：：CDC 呈现目标](#cdcrendertarget)|构造 CDCRenderTarget 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDC 呈现目标：：附加](#attach)|将现有渲染目标接口附加到对象|
|[CDC 呈现目标：：绑定DC](#binddc)|将渲染目标绑定到发出绘制命令的设备上下文|
|[CDC 呈现目标：：创建](#create)|创建 CDCRenderTarget。|
|[CDC 渲染目标：:D](#detach)|从对象分离渲染目标接口|
|[CDC 渲染目标：：获取DCRender目标](#getdcrendertarget)|返回 ID2D1DCRenderTarget 接口|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CDC 渲染目标：：操作员 ID2D1DCRenderTarget*](#operator_id2d1dcrendertarget_star)|返回 ID2D1DCRenderTarget 接口|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CDC 呈现目标：：m_pDCRenderTarget](#m_pdcrendertarget)|指向 ID2D1DCRenderTarget 对象的指针。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CRender目标](../../mfc/reference/crendertarget-class.md)

[CDC 渲染目标](../../mfc/reference/cdcrendertarget-class.md)

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cdcrendertargetattach"></a><a name="attach"></a>CDC 呈现目标：：附加

将现有渲染目标接口附加到对象

```cpp
void Attach(ID2D1DCRenderTarget* pTarget);
```

### <a name="parameters"></a>参数

*p目标*<br/>
现有渲染目标接口。 不能为 NULL

## <a name="cdcrendertargetbinddc"></a><a name="binddc"></a>CDC 呈现目标：：绑定DC

将渲染目标绑定到发出绘制命令的设备上下文

```
BOOL BindDC(
    const CDC& dc,
    const CRect& rect);
```

### <a name="parameters"></a>参数

*直流*<br/>
呈现目标发出绘制命令的设备上下文

*矩形*<br/>
呈现目标绑定到的设备上下文 （HDC） 的句柄的尺寸

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE。

## <a name="cdcrendertargetcdcrendertarget"></a><a name="cdcrendertarget"></a>CDC 渲染目标：：CDC 呈现目标

构造 CDCRenderTarget 对象。

```
CDCRenderTarget();
```

## <a name="cdcrendertargetcreate"></a><a name="create"></a>CDC 呈现目标：：创建

创建 CDCRenderTarget。

```
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```

### <a name="parameters"></a>参数

*道具*<br/>
渲染模式、像素格式、远程处理选项、DPI 信息以及硬件渲染所需的最小 DirectX 支持。

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE。

## <a name="cdcrendertargetdetach"></a><a name="detach"></a>CDC 渲染目标：:D

从对象分离渲染目标接口

```
ID2D1DCRenderTarget* Detach();
```

### <a name="return-value"></a>返回值

指向分离的渲染目标接口的指针。

## <a name="cdcrendertargetgetdcrendertarget"></a><a name="getdcrendertarget"></a>CDC 渲染目标：：获取DCRender目标

返回 ID2D1DCRenderTarget 接口

```
ID2D1DCRenderTarget* GetDCRenderTarget();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1DCRenderTarget 接口或 NULL 的指针。

## <a name="cdcrendertargetm_pdcrendertarget"></a><a name="m_pdcrendertarget"></a>CDC 呈现目标：：m_pDCRenderTarget

指向 ID2D1DCRenderTarget 对象的指针。

```
ID2D1DCRenderTarget* m_pDCRenderTarget;
```

## <a name="cdcrendertargetoperator-id2d1dcrendertarget"></a><a name="operator_id2d1dcrendertarget_star"></a>CDC 渲染目标：：操作员 ID2D1DCRenderTarget*

返回 ID2D1DCRenderTarget 接口

```
operator ID2D1DCRenderTarget*();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1DCRenderTarget 接口或 NULL 的指针。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
