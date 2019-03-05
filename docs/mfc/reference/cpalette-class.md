---
title: CPalette 类
ms.date: 11/04/2016
f1_keywords:
- CPalette
- AFXWIN/CPalette
- AFXWIN/CPalette::CPalette
- AFXWIN/CPalette::AnimatePalette
- AFXWIN/CPalette::CreateHalftonePalette
- AFXWIN/CPalette::CreatePalette
- AFXWIN/CPalette::FromHandle
- AFXWIN/CPalette::GetEntryCount
- AFXWIN/CPalette::GetNearestPaletteIndex
- AFXWIN/CPalette::GetPaletteEntries
- AFXWIN/CPalette::ResizePalette
- AFXWIN/CPalette::SetPaletteEntries
helpviewer_keywords:
- CPalette [MFC], CPalette
- CPalette [MFC], AnimatePalette
- CPalette [MFC], CreateHalftonePalette
- CPalette [MFC], CreatePalette
- CPalette [MFC], FromHandle
- CPalette [MFC], GetEntryCount
- CPalette [MFC], GetNearestPaletteIndex
- CPalette [MFC], GetPaletteEntries
- CPalette [MFC], ResizePalette
- CPalette [MFC], SetPaletteEntries
ms.assetid: 8cd95498-53ed-4852-85e1-70e522541114
ms.openlocfilehash: 8abd03ff2b133eb6040799eff6879a19a64783ef
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274656"
---
# <a name="cpalette-class"></a>CPalette 类

封装一个 Windows 调色板。

## <a name="syntax"></a>语法

```
class CPalette : public CGdiObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CPalette::CPalette](#cpalette)|构造`CPalette`对象没有附加 Windows 调色板。 必须初始化`CPalette`具有一个初始化成员函数才可以使用对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CPalette::AnimatePalette](#animatepalette)|替换由标识逻辑调色板中的条目`CPalette`对象。 应用程序没有要更新其工作区，因为 Windows 立即将映射到系统调色板的新条目。|
|[CPalette::CreateHalftonePalette](#createhalftonepalette)|创建设备上下文的半色调调色板，并将其附加到`CPalette`对象。|
|[CPalette::CreatePalette](#createpalette)|创建 Windows 调色板，并将其附加到`CPalette`对象。|
|[CPalette::FromHandle](#fromhandle)|返回一个指向`CPalette`对象时提供给 Windows 调色板对象的句柄。|
|[CPalette::GetEntryCount](#getentrycount)|检索调色板逻辑调色板中的条目数。|
|[CPalette::GetNearestPaletteIndex](#getnearestpaletteindex)|返回与颜色值最匹配的逻辑调色板中的项的索引。|
|[CPalette::GetPaletteEntries](#getpaletteentries)|检索一系列逻辑调色板中的调色板条目。|
|[CPalette::ResizePalette](#resizepalette)|指定的逻辑调色板的大小更改`CPalette`对象与指定的条目数。|
|[CPalette::SetPaletteEntries](#setpaletteentries)|设置逻辑调色板中的条目范围中的 RGB 颜色值和标志。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CPalette::operator HPALETTE](#operator_hpalette)|返回 HPALETTE 附加到`CPalette`。|

## <a name="remarks"></a>备注

调色板提供了应用程序和颜色输出设备 （如显示设备） 之间的接口。 接口允许应用程序以充分利用输出设备的颜色功能而不会严重干扰其他应用程序显示的颜色。 Windows 使用应用程序的逻辑调色板 （所需颜色的列表） 和系统调色板 （用于定义可用的颜色） 来确定使用的颜色。

一个`CPalette`对象提供成员函数的操作面板到引用的对象。 构造`CPalette`对象，并使用其成员函数来创建实际的面板中，图形设备接口 (GDI) 对象，并操作其项和其他属性。

有关使用的详细信息`CPalette`，请参阅[图形对象](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPalette`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="animatepalette"></a>  CPalette::AnimatePalette

替换附加到逻辑调色板中的条目`CPalette`对象。

```
void AnimatePalette(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>参数

*nStartIndex*<br/>
指定要进行动画处理的调色板中的第一个条目。

*nNumEntries*<br/>
指定要进行动画处理的调色板中的条目数。

*lpPaletteColors*<br/>
指向数组的第一个成员[PALETTEENTRY](https://msdn.microsoft.com/library/windows/desktop/dd162769)结构，以替换由标识调色板条目*nStartIndex*并*nNumEntries*。

### <a name="remarks"></a>备注

当应用程序调用`AnimatePalette`，它无需更新其工作区，因为 Windows 立即将映射到系统调色板的新条目。

`AnimatePalette`函数只会 PC_RESERVED 标志中相应设置更改条目`palPaletteEntry`的成员[LOGPALETTE](/windows/desktop/api/wingdi/ns-wingdi-taglogpalette)附加到的结构`CPalette`对象。 LOGPALETTE 在 Windows SDK 中有关此结构的详细信息，请参阅。

##  <a name="cpalette"></a>  CPalette::CPalette

构造 `CPalette` 对象。

```
CPalette();
```

### <a name="remarks"></a>备注

该对象具有没有附加的调色板，直到你调用`CreatePalette`以附加一个。

##  <a name="createhalftonepalette"></a>  CPalette::CreateHalftonePalette

创建设备上下文的半色调调色板。

```
BOOL CreateHalftonePalette(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
标识设备上下文。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

设备上下文的拉伸模式设置为半色调时，应用程序应创建半色调调色板。 返回由逻辑半色调调色板[CreateHalftonePalette](/windows/desktop/api/wingdi/nf-wingdi-createhalftonepalette)成员函数应然后选择并意识到之前在设备上下文[CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt)或[StretchDIBits](/windows/desktop/api/wingdi/nf-wingdi-stretchdibits)调用函数。

了解适用于的详细信息的 Windows SDK`CreateHalftonePalette`和`StretchDIBits`。

##  <a name="createpalette"></a>  CPalette::CreatePalette

初始化`CPalette`通过创建 Windows 逻辑调色板并将其附加到对象`CPalette`对象。

```
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```

### <a name="parameters"></a>参数

*lpLogPalette*<br/>
指向[LOGPALETTE](/windows/desktop/api/wingdi/ns-wingdi-taglogpalette)结构，其中包含有关逻辑调色板中的颜色的信息。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

了解适用于的详细信息的 Windows SDK`LOGPALETTE`结构。

##  <a name="fromhandle"></a>  CPalette::FromHandle

返回一个指向`CPalette`对象时提供给 Windows 调色板对象的句柄。

```
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```

### <a name="parameters"></a>参数

*hPalette*<br/>
Windows GDI 调色板的句柄。

### <a name="return-value"></a>返回值

一个指向`CPalette`如果成功，否则该值为 NULL 的对象。

### <a name="remarks"></a>备注

如果`CPalette`对象尚未附加到 Windows 调色板，临时`CPalette`创建并附加对象。 此临时`CPalette`对象仅用于有效直到下一次应用程序在其事件循环内有空闲时间，在该时间所有临时图形对象会被删除。 换而言之，仅在一个窗口消息处理期间的临时对象有效。

##  <a name="getentrycount"></a>  CPalette::GetEntryCount

调用此成员函数可检索给定逻辑调色板中的条目数。

```
int GetEntryCount();
```

### <a name="return-value"></a>返回值

逻辑调色板中的条目数。

##  <a name="getnearestpaletteindex"></a>  CPalette::GetNearestPaletteIndex

返回与指定的颜色值最匹配的逻辑调色板中的项的索引。

```
UINT GetNearestPaletteIndex(COLORREF crColor) const;
```

### <a name="parameters"></a>参数

*crColor*<br/>
指定要匹配的颜色。

### <a name="return-value"></a>返回值

逻辑调色板中的项的索引。 该条目包含与指定的颜色最近似匹配的颜色。

##  <a name="getpaletteentries"></a>  CPalette::GetPaletteEntries

检索一系列逻辑调色板中的调色板条目。

```
UINT GetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors) const;
```

### <a name="parameters"></a>参数

*nStartIndex*<br/>
指定要检索的逻辑调色板中的第一个条目。

*nNumEntries*<br/>
指定要检索的逻辑调色板中的条目数。

*lpPaletteColors*<br/>
指向数组[PALETTEENTRY](https://msdn.microsoft.com/library/windows/desktop/dd162769)数据结构，以接收调色板条目。 该数组必须包含至少多少数据结构由指定*nNumEntries*。

### <a name="return-value"></a>返回值

从逻辑调色板; 检索的条目数如果函数失败，则为 0。

##  <a name="operator_hpalette"></a>  CPalette::operator HPALETTE

此运算符用于获取附加的 Windows GDI 句柄的`CPalette`对象。

```
operator HPALETTE() const;
```

### <a name="return-value"></a>返回值

如果成功，Windows GDI 对象的句柄由`CPalette`对象; 否则为 NULL。

### <a name="remarks"></a>备注

此运算符是强制转换运算符，支持直接使用 HPALETTE 对象。

有关使用图形对象的详细信息，请参阅文章[图形对象](/windows/desktop/gdi/graphic-objects)Windows SDK 中。

##  <a name="resizepalette"></a>  CPalette::ResizePalette

更改附加到的逻辑调色板的大小`CPalette`对象与指定的项数*nNumEntries*。

```
BOOL ResizePalette(UINT nNumEntries);
```

### <a name="parameters"></a>参数

*nNumEntries*<br/>
已调整大小后，在调色板中指定条目的数。

### <a name="return-value"></a>返回值

调色板已成功地调整大小; 如果非零值否则为 0。

### <a name="remarks"></a>备注

如果应用程序调用`ResizePalette`若要减少的调色板的大小，调整过大小的面板中剩余的条目保持不变。 如果应用程序调用`ResizePalette`可将其放大调色板，附加调色板条目已设置为黑色 （红色、 绿色和蓝色值为全部由 0），并为所有其他项的标志设置为 0。

有关 Windows API 的详细信息`ResizePalette`，请参阅[ResizePalette](/windows/desktop/api/wingdi/nf-wingdi-resizepalette) Windows SDK 中。

##  <a name="setpaletteentries"></a>  CPalette::SetPaletteEntries

设置逻辑调色板中的条目范围中的 RGB 颜色值和标志。

```
UINT SetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>参数

*nStartIndex*<br/>
指定要设置的逻辑调色板中的第一个条目。

*nNumEntries*<br/>
指定要设置的逻辑调色板中的条目数。

*lpPaletteColors*<br/>
指向数组[PALETTEENTRY](https://msdn.microsoft.com/library/windows/desktop/dd162769)数据结构，以接收调色板条目。 该数组必须包含至少多少数据结构由指定*nNumEntries*。

### <a name="return-value"></a>返回值

在逻辑调色板; 中设置的条目数如果函数失败，则为 0。

### <a name="remarks"></a>备注

如果逻辑调色板选入设备上下文中，当应用程序调用`SetPaletteEntries`，所做的更改不会影响应用程序调用直到[CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette)。

有关详细信息的 Windows 结构`PALETTEENTRY`，请参阅[PALETTEENTRY](https://msdn.microsoft.com/library/windows/desktop/dd162769) Windows SDK 中。

## <a name="see-also"></a>请参阅

[MFC 示例 DIBLOOK](../../visual-cpp-samples.md)<br/>
[CGdiObject 类](../../mfc/reference/cgdiobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CPalette::GetPaletteEntries](#getpaletteentries)<br/>
[CPalette::SetPaletteEntries](#setpaletteentries)
