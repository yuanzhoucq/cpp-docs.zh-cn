---
title: CD2DBitmap 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::Attach
- AFXRENDERTARGET/CD2DBitmap::CopyFromBitmap
- AFXRENDERTARGET/CD2DBitmap::CopyFromMemory
- AFXRENDERTARGET/CD2DBitmap::CopyFromRenderTarget
- AFXRENDERTARGET/CD2DBitmap::Create
- AFXRENDERTARGET/CD2DBitmap::Destroy
- AFXRENDERTARGET/CD2DBitmap::Detach
- AFXRENDERTARGET/CD2DBitmap::Get
- AFXRENDERTARGET/CD2DBitmap::GetDPI
- AFXRENDERTARGET/CD2DBitmap::GetPixelFormat
- AFXRENDERTARGET/CD2DBitmap::GetPixelSize
- AFXRENDERTARGET/CD2DBitmap::GetSize
- AFXRENDERTARGET/CD2DBitmap::IsValid
- AFXRENDERTARGET/CD2DBitmap::CommonInit
- AFXRENDERTARGET/CD2DBitmap::m_bAutoDestroyHBMP
- AFXRENDERTARGET/CD2DBitmap::m_hBmpSrc
- AFXRENDERTARGET/CD2DBitmap::m_lpszType
- AFXRENDERTARGET/CD2DBitmap::m_pBitmap
- AFXRENDERTARGET/CD2DBitmap::m_sizeDest
- AFXRENDERTARGET/CD2DBitmap::m_strPath
- AFXRENDERTARGET/CD2DBitmap::m_uiResID
dev_langs:
- C++
helpviewer_keywords:
- CD2DBitmap [MFC], CD2DBitmap
- CD2DBitmap [MFC], CD2DBitmap
- CD2DBitmap [MFC], Attach
- CD2DBitmap [MFC], CopyFromBitmap
- CD2DBitmap [MFC], CopyFromMemory
- CD2DBitmap [MFC], CopyFromRenderTarget
- CD2DBitmap [MFC], Create
- CD2DBitmap [MFC], Destroy
- CD2DBitmap [MFC], Detach
- CD2DBitmap [MFC], Get
- CD2DBitmap [MFC], GetDPI
- CD2DBitmap [MFC], GetPixelFormat
- CD2DBitmap [MFC], GetPixelSize
- CD2DBitmap [MFC], GetSize
- CD2DBitmap [MFC], IsValid
- CD2DBitmap [MFC], CommonInit
- CD2DBitmap [MFC], m_bAutoDestroyHBMP
- CD2DBitmap [MFC], m_hBmpSrc
- CD2DBitmap [MFC], m_lpszType
- CD2DBitmap [MFC], m_pBitmap
- CD2DBitmap [MFC], m_sizeDest
- CD2DBitmap [MFC], m_strPath
- CD2DBitmap [MFC], m_uiResID
ms.assetid: 2b3686f1-812c-462b-b449-9f0cb6949bf6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 57a64b1a07305c154efdfdf57651ffe3cf5f3dad
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059945"
---
# <a name="cd2dbitmap-class"></a>CD2DBitmap 类

ID2D1Bitmap 包装器。

## <a name="syntax"></a>语法

```
class CD2DBitmap : public CD2DResource;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|已重载。 构造从 HBITMAP CD2DBitmap 对象。|
|[CD2DBitmap:: ~ CD2DBitmap](#_dtorcd2dbitmap)|析构函数。 当 D2D 位图对象被销毁时调用。|

### <a name="protected-constructors"></a>受保护的构造函数

|名称|描述|
|----------|-----------------|
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|已重载。 构造一个 CD2DBitmap 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CD2DBitmap::Attach](#attach)|附加现有的资源的对象的接口|
|[CD2DBitmap::CopyFromBitmap](#copyfrombitmap)|将指定的区域中指定位图复制到的当前位图|
|[CD2DBitmap::CopyFromMemory](#copyfrommemory)|将指定的区域从内存复制到当前的位图|
|[CD2DBitmap::CopyFromRenderTarget](#copyfromrendertarget)|副本从指定的指定的区域呈现目标的当前位图到|
|[CD2DBitmap::Create](#create)|创建 CD2DBitmap。 (重写[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|
|[CD2DBitmap::Destroy](#destroy)|销毁 CD2DBitmap 对象。 (重写[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy)。)|
|[CD2DBitmap::Detach](#detach)|分离对象中的资源接口|
|[CD2DBitmap::Get](#get)|返回 ID2D1Bitmap 接口|
|[CD2DBitmap::GetDPI](#getdpi)|返回每英寸点数 (DPI) 的位图|
|[CD2DBitmap::GetPixelFormat](#getpixelformat)|检索位图的像素格式和 alpha 模式|
|[CD2DBitmap::GetPixelSize](#getpixelsize)|返回该位图的大小，以依赖于设备的单位 （像素）|
|[CD2DBitmap::GetSize](#getsize)|位图的返回的大小，以设备无关的像素 (Dip)|
|[CD2DBitmap::IsValid](#isvalid)|检查资源有效性 (重写[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)。)|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CD2DBitmap::CommonInit](#commoninit)|初始化对象|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CD2DBitmap::operator ID2D1Bitmap *](#operator_id2d1bitmap_star)|返回 ID2D1Bitmap 接口|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CD2DBitmap::m_bAutoDestroyHBMP](#m_bautodestroyhbmp)|如果应销毁 m_hBmpSrc; 则为 TRUE否则为 FALSE。|
|[CD2DBitmap::m_hBmpSrc](#m_hbmpsrc)|源位图的句柄。|
|[CD2DBitmap::m_lpszType](#m_lpsztype)|资源类型。|
|[CD2DBitmap::m_pBitmap](#m_pbitmap)|存储指向 ID2D1Bitmap 对象的指针。|
|[CD2DBitmap::m_sizeDest](#m_sizedest)|目标大小的位图。|
|[CD2DBitmap::m_strPath](#m_strpath)|位图文件路径。|
|[CD2DBitmap::m_uiResID](#m_uiresid)|位图的资源 id。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DBitmap`

## <a name="requirements"></a>要求

**标头：** afxrendertarget.h

##  <a name="_dtorcd2dbitmap"></a>  CD2DBitmap:: ~ CD2DBitmap

析构函数。 当 D2D 位图对象被销毁时调用。

```
virtual ~CD2DBitmap();
```

##  <a name="attach"></a>  CD2DBitmap::Attach

附加现有的资源的对象的接口。

```
void Attach(ID2D1Bitmap* pResource);
```

### <a name="parameters"></a>参数

*pResource*<br/>
现有资源的接口。 不能为 NULL。

##  <a name="cd2dbitmap"></a>  CD2DBitmap::CD2DBitmap

构造资源从一个 CD2DBitmap 对象。

```
CD2DBitmap(
    CRenderTarget* pParentTarget,
    UINT uiResID,
    LPCTSTR lpszType = NULL,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    LPCTSTR lpszPath,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    HBITMAP hbmpSrc,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>参数

*pParentTarget*<br/>
指向该呈现器目标的指针。

*uiResID*<br/>
资源的资源 ID 号。

*lpszType*<br/>
包含资源类型的以 null 结尾的字符串指针。

*sizeDest*<br/>
位图的目标大小。

*bAutoDestroy*<br/>
指示所有者 (pParentTarget) 将销毁该对象。

*lpszPath*<br/>
包含文件的名称的以 null 结尾的字符串指针。

*hbmpSrc*<br/>
位图的句柄。

##  <a name="commoninit"></a>  CD2DBitmap::CommonInit

初始化的对象。

```
void CommonInit();
```

##  <a name="copyfrombitmap"></a>  CD2DBitmap::CopyFromBitmap

将指定的区域中指定位图复制到当前的位图。

```
HRESULT CopyFromBitmap(
    const CD2DBitmap* pBitmap,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>参数

*pBitmap*<br/>
要从复制的位图。

*destPoint*<br/>
中的当前位图，复制 srcRect 到指定区域的区域的左上角。

*srcRect*<br/>
要复制的位图区域。

### <a name="return-value"></a>返回值

如果该方法成功，它会返回 S_OK。 否则，它返回一个 HRESULT 错误代码。

##  <a name="copyfrommemory"></a>  CD2DBitmap::CopyFromMemory

将指定的区域从内存复制到当前的位图。

```
HRESULT CopyFromMemory(
    const void* srcData,
    UINT32 pitch,
    const CD2DRectU* destRect = NULL);
```

### <a name="parameters"></a>参数

*srcData*<br/>
要复制的数据。

*间距*<br/>
跨距或的源位图存储在 srcData 音调。 跨距是扫描行 （一行像素在内存中） 的字节数。 可以从下面的公式计算跨距： 像素宽度\*每像素 + 内存填充的字节数。

*destRect*<br/>
中的当前位图，复制 srcRect 到指定区域的区域的左上角。

### <a name="return-value"></a>返回值

如果该方法成功，它会返回 S_OK。 否则，它返回一个 HRESULT 错误代码。

##  <a name="copyfromrendertarget"></a>  CD2DBitmap::CopyFromRenderTarget

副本从指定的指定的区域的当前位图到呈现目标。

```
HRESULT CopyFromRenderTarget(
    const CRenderTarget* pRenderTarget,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>参数

*pRenderTarget*<br/>
包含要复制的区域在呈现器目标。

*destPoint*<br/>
中的当前位图，复制 srcRect 到指定区域的区域的左上角。

*srcRect*<br/>
呈现器目标复制区域。

### <a name="return-value"></a>返回值

如果该方法成功，它会返回 S_OK。 否则，它返回一个 HRESULT 错误代码。

##  <a name="create"></a>  CD2DBitmap::Create

创建 CD2DBitmap。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>参数

*pRenderTarget*<br/>
指向该呈现器目标的指针。

### <a name="return-value"></a>返回值

如果该方法成功，它会返回 S_OK。 否则，它返回一个 HRESULT 错误代码。

##  <a name="destroy"></a>  CD2DBitmap::Destroy

销毁 CD2DBitmap 对象。

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DBitmap::Detach

分离对象中的资源接口。

```
ID2D1Bitmap* Detach();
```

### <a name="return-value"></a>返回值

指向已分离的资源接口指针。

##  <a name="get"></a>  CD2DBitmap::Get

返回 ID2D1Bitmap 接口。

```
ID2D1Bitmap* Get();
```

### <a name="return-value"></a>返回值

指向 ID2D1Bitmap 接口或如果对象尚未初始化，则为 NULL 指针。

##  <a name="getdpi"></a>  CD2DBitmap::GetDPI

返回每英寸点数 (DPI) 的位图。

```
CD2DSizeF GetDPI() const;
```

### <a name="return-value"></a>返回值

位图的水平和垂直 DPI。

##  <a name="getpixelformat"></a>  CD2DBitmap::GetPixelFormat

检索位图的像素格式和 alpha 模式

```
D2D1_PIXEL_FORMAT GetPixelFormat() const;
```

### <a name="return-value"></a>返回值

位图的像素格式和 alpha 模式。

##  <a name="getpixelsize"></a>  CD2DBitmap::GetPixelSize

返回该位图的大小，以依赖于设备的单位 （像素）。

```
CD2DSizeU GetPixelSize() const;
```

### <a name="return-value"></a>返回值

以像素为单位，位图的大小...

##  <a name="getsize"></a>  CD2DBitmap::GetSize

返回的位图的大小，以设备无关的像素 (Dip)。

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>返回值

以 dip 为单位，位图的大小。

##  <a name="isvalid"></a>  CD2DBitmap::IsValid

检查资源的有效性。

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>返回值

如果资源是有效，则为，TRUE否则为 FALSE。

##  <a name="m_bautodestroyhbmp"></a>  CD2DBitmap::m_bAutoDestroyHBMP

如果应销毁 m_hBmpSrc; 则为 TRUE否则为 FALSE。

```
BOOL m_bAutoDestroyHBMP;
```

##  <a name="m_hbmpsrc"></a>  CD2DBitmap::m_hBmpSrc

源位图的句柄。

```
HBITMAP m_hBmpSrc;
```

##  <a name="m_lpsztype"></a>  CD2DBitmap::m_lpszType

资源类型。

```
LPCTSTR m_lpszType;
```

##  <a name="m_pbitmap"></a>  CD2DBitmap::m_pBitmap

存储指向 ID2D1Bitmap 对象的指针。

```
ID2D1Bitmap* m_pBitmap;
```

##  <a name="m_sizedest"></a>  CD2DBitmap::m_sizeDest

目标大小的位图。

```
CD2DSizeU m_sizeDest;
```

##  <a name="m_strpath"></a>  CD2DBitmap::m_strPath

位图文件路径。

```
CString m_strPath;
```

##  <a name="m_uiresid"></a>  CD2DBitmap::m_uiResID

位图的资源 id。

```
UINT m_uiResID;
```

##  <a name="operator_id2d1bitmap_star"></a>  CD2DBitmap::operator ID2D1Bitmap *

返回 ID2D1Bitmap 接口

```
operator ID2D1Bitmap*();
```

### <a name="return-value"></a>返回值

指向 ID2D1Bitmap 接口或如果对象尚未初始化，则为 NULL 指针。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
