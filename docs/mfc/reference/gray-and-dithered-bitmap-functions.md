---
title: 灰色和抖色位图函数
ms.date: 11/19/2018
f1_keywords:
- AFXWIN/AfxDrawGrayBitmap
- AFXWIN/AfxGetGrayBitmap
- AFXWIN/AfxDrawDitheredBitmap
- AFXWIN/AfxGetDitheredBitmap
helpviewer_keywords:
- gray and dithered bitmap functions [MFC]
ms.assetid: cb139a77-b85e-4504-9d93-24156ad77a41
ms.openlocfilehash: fb764dbd71d89ae3317816df3539c2881b9695b6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290776"
---
# <a name="gray-and-dithered-bitmap-functions"></a>灰色和抖色位图函数

**灰色位图函数**

MFC 提供了两个函数为位图提供已禁用控件的外观。

![灰色和原始图标版本的比较](../../mfc/reference/media/vcgraybitmap.gif "的原始图标版本比较")

|||
|-|-|
|[AfxDrawGrayBitmap](#afxdrawgraybitmap)|绘制灰色版本的位图。|
|[AfxGetGrayBitmap](#afxgetgraybitmap)|复制灰色版本的位图。|

**抖色位图函数**

MFC 还提供了两个函数以将位图背景替换为抖色样式。

![抖色与原始图标版本的比较](../../mfc/reference/media/vcditheredbitmap.gif "抖色与原始图标版本比较")

|||
|-|-|
|[AfxDrawDitheredBitmap](#afxdrawditheredbitmap)|绘制抖色背景位图。|
|[AfxGetDitheredBitmap](#afxgetditheredbitmap)|复制抖色背景位图。|

##  <a name="afxdrawgraybitmap"></a>  AfxDrawGrayBitmap

绘制灰色版本的位图。

```
void AFXAPI AfxDrawGrayBitmap(
    CDC* pDC,
    int x,
    int y,
    const CBitmap& rSrc,
    COLORREF crBackground);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向目标值 DC 的指针。

*x*<br/>
目标 x 坐标。

*y*<br/>
目标 y 坐标。

*rSrc*<br/>
源位图。

*crBackground*<br/>
新背景色（通常为灰色，如 COLOR_MENU）。

### <a name="remarks"></a>备注

使用 `AfxDrawGrayBitmap` 绘制的位图将具有禁用控件的外观。

![灰色和原始图标版本的比较](../../mfc/reference/media/vcgraybitmap.gif "的原始图标版本比较")

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#191](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_1.cpp)]

### <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="afxgetgraybitmap"></a>  AfxGetGrayBitmap

复制灰色版本的位图。

```
void AFXAPI AfxGetGrayBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF crBackground);
```

### <a name="parameters"></a>参数

*rSrc*<br/>
源位图。

*pDest*<br/>
目标位图。

*crBackground*<br/>
新背景色（通常为灰色，如 COLOR_MENU）。

### <a name="remarks"></a>备注

使用 `AfxGetGrayBitmap` 复制的位图将具有禁用控件的外观。

![灰色和原始图标版本的比较](../../mfc/reference/media/vcgraybitmap.gif "的原始图标版本比较")

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#193](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_2.cpp)]

### <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="afxdrawditheredbitmap"></a>  AfxDrawDitheredBitmap

绘制一个位图，其背景替换为抖色 （棋盘格） 图案。

```
void AFXAPI AfxDrawDitheredBitmap(
    CDC* pDC,
    int x,
    int y,
    const CBitmap& rSrc,
    COLORREF cr1  ,
    COLORREF cr2);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向目标值 DC 的指针。

*x*<br/>
目标 x 坐标。

*y*<br/>
目标 y 坐标。

*rSrc*<br/>
源位图。

*cr1*<br/>
两种递色中的一种，通常为白色。

*cr2*<br/>
另一种递色，通常为浅灰色 (COLOR_MENU)。

### <a name="remarks"></a>备注

在两种颜色与目标 DC 上绘制的源位图 (*cr1*并*cr2*) 棋盘格的图案替换位图的背景。 根据定义，源位图的背景指的是指位图的白色像素以及与位图左上角的像素颜色匹配的所有像素。

![抖色与原始图标版本的比较](../../mfc/reference/media/vcditheredbitmap.gif "抖色与原始图标版本比较")

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#190](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_3.cpp)]

### <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="afxgetditheredbitmap"></a>  AfxGetDitheredBitmap

复制位图，并将其背景替换为递色（棋盘格）图案。

```
void AFXAPI AfxGetDitheredBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF cr1  ,
    COLORREF cr2);
```

### <a name="parameters"></a>参数

*rSrc*<br/>
源位图。

*pDest*<br/>
目标位图。

*cr1*<br/>
两种递色中的一种，通常为白色。

*cr2*<br/>
另一种递色，通常为浅灰色 (COLOR_MENU)。

### <a name="remarks"></a>备注

源位图复制到目标位图与两种颜色 (*cr1*并*cr2*) 棋盘格的图案替换源位图的背景。 根据定义，源位图的背景指的是指位图的白色像素以及与位图左上角的像素颜色匹配的所有像素。

![抖色与原始图标版本的比较](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="see-also"></a>请参阅

[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
