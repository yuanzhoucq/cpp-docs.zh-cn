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
ms.openlocfilehash: a220596b880ee74d5f9ebf683d087156224ee7c5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751475"
---
# <a name="gray-and-dithered-bitmap-functions"></a>灰色和抖色位图函数

**灰色位图函数**

MFC 提供了两个函数为位图提供已禁用控件的外观。

![灰色图标版本与原始图标版本之比较](../../mfc/reference/media/vcgraybitmap.gif "灰色图标版本与原始图标版本之比较")

|||
|-|-|
|[AfxDrawGrayBitmap](#afxdrawgraybitmap)|绘制灰色版本的位图。|
|[AfxGetGrayBitmap](#afxgetgraybitmap)|复制灰色版本的位图。|

**抖色位图函数**

MFC 还提供了两个函数以将位图背景替换为抖色样式。

![抖动图标版本与原始图标版本之比较](../../mfc/reference/media/vcditheredbitmap.gif "抖动图标版本与原始图标版本之比较")

|||
|-|-|
|[AfxDrawDitheredBitmap](#afxdrawditheredbitmap)|绘制抖色背景位图。|
|[AfxGetDitheredBitmap](#afxgetditheredbitmap)|复制抖色背景位图。|

## <a name="afxdrawgraybitmap"></a><a name="afxdrawgraybitmap"></a>AfxDraw灰色位图

绘制灰色版本的位图。

```cpp
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

*Y*<br/>
目标 y 坐标。

*rSrc*<br/>
源位图。

*cr背景*<br/>
新背景色（通常为灰色，如 COLOR_MENU）。

### <a name="remarks"></a>备注

使用 `AfxDrawGrayBitmap` 绘制的位图将具有禁用控件的外观。

![灰色图标版本与原始图标版本之比较](../../mfc/reference/media/vcgraybitmap.gif "灰色图标版本与原始图标版本之比较")

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#191](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_1.cpp)]

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="afxgetgraybitmap"></a><a name="afxgetgraybitmap"></a>AfxGet格雷比特图

复制灰色版本的位图。

```cpp
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

*cr背景*<br/>
新背景色（通常为灰色，如 COLOR_MENU）。

### <a name="remarks"></a>备注

使用 `AfxGetGrayBitmap` 复制的位图将具有禁用控件的外观。

![灰色图标版本与原始图标版本之比较](../../mfc/reference/media/vcgraybitmap.gif "灰色图标版本与原始图标版本之比较")

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#193](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_2.cpp)]

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="afxdrawditheredbitmap"></a><a name="afxdrawditheredbitmap"></a>AfxDrawDitheredBitmap

绘制位图，将其背景替换为抖抖（跳棋）图案。

```cpp
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

*Y*<br/>
目标 y 坐标。

*rSrc*<br/>
源位图。

*cr1*<br/>
两种递色中的一种，通常为白色。

*cr2*<br/>
另一种递色，通常为浅灰色 (COLOR_MENU)。

### <a name="remarks"></a>备注

源位图在目标 DC 上绘制，其双色 *（cr1*和*cr2）* 格格模式取代了位图的背景。 根据定义，源位图的背景指的是指位图的白色像素以及与位图左上角的像素颜色匹配的所有像素。

![抖动图标版本与原始图标版本之比较](../../mfc/reference/media/vcditheredbitmap.gif "抖动图标版本与原始图标版本之比较")

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#190](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_3.cpp)]

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="afxgetditheredbitmap"></a><a name="afxgetditheredbitmap"></a>AfxGetDitheredBitmap

复制位图，并将其背景替换为递色（棋盘格）图案。

```cpp
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

源位图以双色 *（cr1*和*cr2）* 的方格模式复制到目标位图，替换源位图的背景。 根据定义，源位图的背景指的是指位图的白色像素以及与位图左上角的像素颜色匹配的所有像素。

![抖动图标版本与原始图标版本之比较](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]

### <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="see-also"></a>请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
