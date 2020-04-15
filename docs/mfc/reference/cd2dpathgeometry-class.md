---
title: CD2DPathGeometry 类
ms.date: 11/04/2016
f1_keywords:
- CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::Attach
- AFXRENDERTARGET/CD2DPathGeometry::Create
- AFXRENDERTARGET/CD2DPathGeometry::Destroy
- AFXRENDERTARGET/CD2DPathGeometry::Detach
- AFXRENDERTARGET/CD2DPathGeometry::GetFigureCount
- AFXRENDERTARGET/CD2DPathGeometry::GetSegmentCount
- AFXRENDERTARGET/CD2DPathGeometry::Open
- AFXRENDERTARGET/CD2DPathGeometry::Stream
- AFXRENDERTARGET/CD2DPathGeometry::m_pPathGeometry
helpviewer_keywords:
- CD2DPathGeometry [MFC], CD2DPathGeometry
- CD2DPathGeometry [MFC], Attach
- CD2DPathGeometry [MFC], Create
- CD2DPathGeometry [MFC], Destroy
- CD2DPathGeometry [MFC], Detach
- CD2DPathGeometry [MFC], GetFigureCount
- CD2DPathGeometry [MFC], GetSegmentCount
- CD2DPathGeometry [MFC], Open
- CD2DPathGeometry [MFC], Stream
- CD2DPathGeometry [MFC], m_pPathGeometry
ms.assetid: 686216eb-5080-4242-ace5-8fa1ce96307c
ms.openlocfilehash: 59ef82151983720b654502ccf3ca647e55366268
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369168"
---
# <a name="cd2dpathgeometry-class"></a>CD2DPathGeometry 类

ID2D1Path几何的包装。

## <a name="syntax"></a>语法

```
class CD2DPathGeometry : public CD2DGeometry;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2D路径几何：CD2D路径几何](#cd2dpathgeometry)|构造 CD2DPath 几何对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CD2DPath几何：附加](#attach)|将现有资源接口附加到对象|
|[CD2DPath几何：创建](#create)|创建 CD2DPath 几何体。 （覆盖[CD2D 资源：创建](../../mfc/reference/cd2dresource-class.md#create).）|
|[CD2DPath几何：:D](#destroy)|销毁 CD2DPath 几何对象。 （覆盖[CD2D 几何：:Destroy](../../mfc/reference/cd2dgeometry-class.md#destroy).）|
|[CD2DPath几何：:Detach](#detach)|从对象分离资源接口|
|[CD2DPath几何：获取图计数](#getfigurecount)|检索路径几何体中的图形数。|
|[CD2D路径几何：获取细分计数](#getsegmentcount)|检索路径几何体中的线段数。|
|[CD2DPath几何：打开](#open)|检索用于用图形和线段填充路径几何体的几何接收器。|
|[CD2DPath几何：流](#stream)|将路径几何体的内容复制到指定的 ID2D1 几何基克。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CD2DPath几何：：m_pPathGeometry](#m_ppathgeometry)|指向 ID2D1 路径几何的指针。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 资源](../../mfc/reference/cd2dresource-class.md)

[CD2D 几何](../../mfc/reference/cd2dgeometry-class.md)

`CD2DPathGeometry`

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2dpathgeometryattach"></a><a name="attach"></a>CD2DPath几何：附加

将现有资源接口附加到对象

```
void Attach(ID2D1PathGeometry* pResource);
```

### <a name="parameters"></a>参数

*p资源*<br/>
现有资源接口。 不能为 NULL

## <a name="cd2dpathgeometrycd2dpathgeometry"></a><a name="cd2dpathgeometry"></a>CD2D路径几何：CD2D路径几何

构造 CD2DPath 几何对象。

```
CD2DPathGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>参数

*p 父目标*<br/>
指向渲染目标的指针。

*bAuto销毁*<br/>
指示对象将被所有者（pParentTarget）销毁。

## <a name="cd2dpathgeometrycreate"></a><a name="create"></a>CD2DPath几何：创建

创建 CD2DPath 几何体。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>参数

*pRender目标*<br/>
指向渲染目标的指针。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="cd2dpathgeometrydestroy"></a><a name="destroy"></a>CD2DPath几何：:D

销毁 CD2DPath 几何对象。

```
virtual void Destroy();
```

## <a name="cd2dpathgeometrydetach"></a><a name="detach"></a>CD2DPath几何：:Detach

从对象分离资源接口

```
ID2D1PathGeometry* Detach();
```

### <a name="return-value"></a>返回值

指向分离的资源接口的指针。

## <a name="cd2dpathgeometrygetfigurecount"></a><a name="getfigurecount"></a>CD2DPath几何：获取图计数

检索路径几何体中的图形数。

```
int GetFigureCount() const;
```

### <a name="return-value"></a>返回值

返回路径几何体中的图形数。

## <a name="cd2dpathgeometrygetsegmentcount"></a><a name="getsegmentcount"></a>CD2D路径几何：获取细分计数

检索路径几何体中的线段数。

```
int GetSegmentCount() const;
```

### <a name="return-value"></a>返回值

返回路径几何体中的线段数。

## <a name="cd2dpathgeometrym_ppathgeometry"></a><a name="m_ppathgeometry"></a>CD2DPath几何：：m_pPathGeometry

指向 ID2D1 路径几何的指针。

```
ID2D1PathGeometry* m_pPathGeometry;
```

## <a name="cd2dpathgeometryopen"></a><a name="open"></a>CD2DPath几何：打开

检索用于用图形和线段填充路径几何体的几何接收器。

```
ID2D1GeometrySink* Open();
```

### <a name="return-value"></a>返回值

指向 ID2D1 GeometrySink 的指针，用于用图形和线段填充路径几何体。

## <a name="cd2dpathgeometrystream"></a><a name="stream"></a>CD2DPath几何：流

将路径几何体的内容复制到指定的 ID2D1 几何基克。

```
BOOL Stream(ID2D1GeometrySink* geometrySink);
```

### <a name="parameters"></a>参数

*几何结构*<br/>
将路径几何体的内容复制到的接收器。 修改此接收器不会更改此路径几何体的内容。

### <a name="return-value"></a>返回值

如果该方法成功，它将返回 TRUE。 否则，它将返回 FALSE。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
