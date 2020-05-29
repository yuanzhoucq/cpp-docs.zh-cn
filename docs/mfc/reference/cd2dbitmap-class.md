---
title: CD2DBitmap 类
ms.date: 11/04/2016
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
ms.openlocfilehash: a3cabb00ded7dbc5f9c396a1de767058443a4436
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754206"
---
# <a name="cd2dbitmap-class"></a>CD2DBitmap 类

ID2D1Bitmap 的包装器。

## <a name="syntax"></a>语法

```
class CD2DBitmap : public CD2DResource;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2DBitmap：CD2DBitmap](#cd2dbitmap)|已重载。 从 HBITMAP 构造 CD2DBitmap 对象。|
|[CD2DBitmap：*CD2DBitmap](#_dtorcd2dbitmap)|析构函数。 销毁 D2D 位图对象时调用。|

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[CD2DBitmap：CD2DBitmap](#cd2dbitmap)|已重载。 构造 CD2DBitmap 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CD2DBitmap：：附加](#attach)|将现有资源接口附加到对象|
|[CD2DBitmap：：从比特图复制](#copyfrombitmap)|将指定区域从指定位图复制到当前位图|
|[CD2DBitmap：：从内存复制](#copyfrommemory)|将指定区域从内存复制到当前位图|
|[CD2DBitmap：：从渲染目标复制](#copyfromrendertarget)|将指定区域从指定的渲染目标复制到当前位图|
|[CD2DBitmap：创建](#create)|创建 CD2DBitmap。 （覆盖[CD2D 资源：创建](../../mfc/reference/cd2dresource-class.md#create).）|
|[CD2DBitmap：:D](#destroy)|销毁 CD2DBitmap 对象。 （覆盖[CD2D 资源：:D）](../../mfc/reference/cd2dresource-class.md#destroy)|
|[CD2DBitmap：:Detach](#detach)|从对象分离资源接口|
|[CD2DBitmap：获取](#get)|返回 ID2D1 位图接口|
|[CD2DBitmap：GetDPI](#getdpi)|返回位图每英寸 （DPI） 的点|
|[CD2DBitmap：：获取像素格式](#getpixelformat)|检索位图的像素格式和 Alpha 模式|
|[CD2DBitmap：：获取像素大小](#getpixelsize)|返回位图的大小（以与设备相关的单位（像素）|
|[CD2DBitmap：获取大小](#getsize)|返回位图的大小（以与设备无关的像素 （DIP）|
|[CD2DBitmap：有效](#isvalid)|检查资源有效性（覆盖[CD2D 资源：：有效](../../mfc/reference/cd2dresource-class.md#isvalid)。）|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CD2DBitmap：：共同信息](#commoninit)|初始化对象|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CD2DBitmap：：操作员 ID2D1 位图*](#operator_id2d1bitmap_star)|返回 ID2D1 位图接口|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CD2DBitmap：m_bAutoDestroyHBMP](#m_bautodestroyhbmp)|如果m_hBmpSrc应销毁，则为 TRUE;否则 FALSE。|
|[CD2DBitmap：：m_hBmpSrc](#m_hbmpsrc)|源位图句柄。|
|[CD2DBitmap：m_lpszType](#m_lpsztype)|资源类型。|
|[CD2DBitmap：m_pBitmap](#m_pbitmap)|存储指向 ID2D1Bitmap 对象的指针。|
|[CD2DBitmap：m_sizeDest](#m_sizedest)|位图目标大小。|
|[CD2DBitmap：m_strPath](#m_strpath)|机器人映射文件路径。|
|[CD2DBitmap：m_uiResID](#m_uiresid)|位图资源 ID。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 资源](../../mfc/reference/cd2dresource-class.md)

`CD2DBitmap`

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2dbitmapcd2dbitmap"></a><a name="_dtorcd2dbitmap"></a>CD2DBitmap：*CD2DBitmap

析构函数。 销毁 D2D 位图对象时调用。

```
virtual ~CD2DBitmap();
```

## <a name="cd2dbitmapattach"></a><a name="attach"></a>CD2DBitmap：：附加

将现有资源接口附加到对象。

```cpp
void Attach(ID2D1Bitmap* pResource);
```

### <a name="parameters"></a>参数

*p资源*<br/>
现有资源接口。 不能为 NULL。

## <a name="cd2dbitmapcd2dbitmap"></a><a name="cd2dbitmap"></a>CD2DBitmap：CD2DBitmap

从资源构造 CD2DBitmap 对象。

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

*p 父目标*<br/>
指向渲染目标的指针。

*uiResID*<br/>
资源的资源 ID 号。

*lpszType*<br/>
指向包含资源类型的空端字符串的指针。

*大小 D 最大*<br/>
位图的目标大小。

*bAuto销毁*<br/>
指示对象将被所有者（pParentTarget）销毁。

*lpszPath*<br/>
指向包含文件名称的 null 终止字符串的指针。

*赫布普斯克*<br/>
处理位图。

## <a name="cd2dbitmapcommoninit"></a><a name="commoninit"></a>CD2DBitmap：：共同信息

初始化对象。

```cpp
void CommonInit();
```

## <a name="cd2dbitmapcopyfrombitmap"></a><a name="copyfrombitmap"></a>CD2DBitmap：：从比特图复制

将指定区域从指定的位图复制到当前位图中。

```
HRESULT CopyFromBitmap(
    const CD2DBitmap* pBitmap,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>参数

*pBitmap*<br/>
要复制的位图。

*destPoint*<br/>
在当前位图中，复制 srcRect 指定的区域的左上角。

*斯克拉特*<br/>
要复制的位图区域。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="cd2dbitmapcopyfrommemory"></a><a name="copyfrommemory"></a>CD2DBitmap：：从内存复制

将指定区域从内存复制到当前位图中。

```
HRESULT CopyFromMemory(
    const void* srcData,
    UINT32 pitch,
    const CD2DRectU* destRect = NULL);
```

### <a name="parameters"></a>参数

*srcData*<br/>
要复制的数据。

*沥青*<br/>
存储在 srcData 中的源位图的步长或间距。 步长是扫描线的字节计数（内存中的一行像素）。 可以从以下公式计算步长：像素宽度\*字节/像素 = 内存填充。

*destRect*<br/>
在当前位图中，复制 srcRect 指定的区域的左上角。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="cd2dbitmapcopyfromrendertarget"></a><a name="copyfromrendertarget"></a>CD2DBitmap：：从渲染目标复制

将指定的区域从指定的渲染目标复制到当前位图中。

```
HRESULT CopyFromRenderTarget(
    const CRenderTarget* pRenderTarget,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>参数

*pRender目标*<br/>
包含要复制的区域的渲染目标。

*destPoint*<br/>
在当前位图中，复制 srcRect 指定的区域的左上角。

*斯克拉特*<br/>
要复制的渲染目标区域。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="cd2dbitmapcreate"></a><a name="create"></a>CD2DBitmap：创建

创建 CD2DBitmap。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>参数

*pRender目标*<br/>
指向渲染目标的指针。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="cd2dbitmapdestroy"></a><a name="destroy"></a>CD2DBitmap：:D

销毁 CD2DBitmap 对象。

```
virtual void Destroy();
```

## <a name="cd2dbitmapdetach"></a><a name="detach"></a>CD2DBitmap：:Detach

从对象分离资源接口。

```
ID2D1Bitmap* Detach();
```

### <a name="return-value"></a>返回值

指向分离的资源接口的指针。

## <a name="cd2dbitmapget"></a><a name="get"></a>CD2DBitmap：获取

返回 ID2D1 位图接口。

```
ID2D1Bitmap* Get();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1Bitmap 接口或 NULL 的指针。

## <a name="cd2dbitmapgetdpi"></a><a name="getdpi"></a>CD2DBitmap：GetDPI

返回位图每英寸 （DPI） 的点。

```
CD2DSizeF GetDPI() const;
```

### <a name="return-value"></a>返回值

位图的水平和垂直 DPI。

## <a name="cd2dbitmapgetpixelformat"></a><a name="getpixelformat"></a>CD2DBitmap：：获取像素格式

检索位图的像素格式和 Alpha 模式

```
D2D1_PIXEL_FORMAT GetPixelFormat() const;
```

### <a name="return-value"></a>返回值

位图的像素格式和 alpha 模式。

## <a name="cd2dbitmapgetpixelsize"></a><a name="getpixelsize"></a>CD2DBitmap：：获取像素大小

返回位图的大小（以与设备相关的单位（像素）。

```
CD2DSizeU GetPixelSize() const;
```

### <a name="return-value"></a>返回值

位图的大小（以像素为单位）。

## <a name="cd2dbitmapgetsize"></a><a name="getsize"></a>CD2DBitmap：获取大小

返回位图的大小（以与设备无关的像素 （DIP）。

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>返回值

位图的大小（以 DIP 表示）。

## <a name="cd2dbitmapisvalid"></a><a name="isvalid"></a>CD2DBitmap：有效

检查资源有效性。

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>返回值

如果资源有效，则为 TRUE;否则 FALSE。

## <a name="cd2dbitmapm_bautodestroyhbmp"></a><a name="m_bautodestroyhbmp"></a>CD2DBitmap：m_bAutoDestroyHBMP

如果m_hBmpSrc应销毁，则为 TRUE;否则 FALSE。

```
BOOL m_bAutoDestroyHBMP;
```

## <a name="cd2dbitmapm_hbmpsrc"></a><a name="m_hbmpsrc"></a>CD2DBitmap：：m_hBmpSrc

源位图句柄。

```
HBITMAP m_hBmpSrc;
```

## <a name="cd2dbitmapm_lpsztype"></a><a name="m_lpsztype"></a>CD2DBitmap：m_lpszType

资源类型。

```
LPCTSTR m_lpszType;
```

## <a name="cd2dbitmapm_pbitmap"></a><a name="m_pbitmap"></a>CD2DBitmap：m_pBitmap

存储指向 ID2D1Bitmap 对象的指针。

```
ID2D1Bitmap* m_pBitmap;
```

## <a name="cd2dbitmapm_sizedest"></a><a name="m_sizedest"></a>CD2DBitmap：m_sizeDest

位图目标大小。

```
CD2DSizeU m_sizeDest;
```

## <a name="cd2dbitmapm_strpath"></a><a name="m_strpath"></a>CD2DBitmap：m_strPath

机器人映射文件路径。

```
CString m_strPath;
```

## <a name="cd2dbitmapm_uiresid"></a><a name="m_uiresid"></a>CD2DBitmap：m_uiResID

位图资源 ID。

```
UINT m_uiResID;
```

## <a name="cd2dbitmapoperator-id2d1bitmap"></a><a name="operator_id2d1bitmap_star"></a>CD2DBitmap：：操作员 ID2D1 位图*

返回 ID2D1 位图接口

```
operator ID2D1Bitmap*();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1Bitmap 接口或 NULL 的指针。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
