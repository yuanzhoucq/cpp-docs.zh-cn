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
ms.openlocfilehash: 27f4f14c9e93091728e256c890dcffee26a43de4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855435"
---
# <a name="cpalette-class"></a>CPalette 类

封装一个 Windows 调色板。

## <a name="syntax"></a>语法

```
class CPalette : public CGdiObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CPalette：： CPalette](#cpalette)|构造一个没有附加的 Windows 调色板的 `CPalette` 对象。 必须使用某个初始化成员函数初始化 `CPalette` 对象，然后才能使用该对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CPalette：： AnimatePalette](#animatepalette)|替换 `CPalette` 对象标识的逻辑调色板中的条目。 应用程序无需更新其客户端区域，因为 Windows 会立即将新项映射到系统调色板。|
|[CPalette：： CreateHalftonePalette](#createhalftonepalette)|为设备上下文创建半色调调色板，并将其附加到 `CPalette` 对象上。|
|[CPalette：： CreatePalette](#createpalette)|创建一个 Windows 调色板，并将其附加到 `CPalette` 对象上。|
|[CPalette：： FromHandle](#fromhandle)|当给定 Windows 调色板对象的句柄时，返回指向 `CPalette` 对象的指针。|
|[CPalette：： GetEntryCount](#getentrycount)|检索逻辑调色板中的调色板项的数目。|
|[CPalette：： GetNearestPaletteIndex](#getnearestpaletteindex)|返回与颜色值最匹配的逻辑调色板中的项的索引。|
|[CPalette：： GetPaletteEntries](#getpaletteentries)|检索逻辑调色板中的一系列调色板项。|
|[CPalette：： ResizePalette](#resizepalette)|将 `CPalette` 对象指定的逻辑调色板的大小更改为指定的项数。|
|[CPalette：： SetPaletteEntries](#setpaletteentries)|设置逻辑调色板中某一范围的项的 RGB 颜色值和标志。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CPalette：： operator HPALETTE](#operator_hpalette)|返回附加到 `CPalette`的 HPALETTE。|

## <a name="remarks"></a>备注

调色板在应用程序和彩色输出设备（如显示设备）之间提供了一个接口。 使用接口，应用程序可以充分利用输出设备的颜色功能，而不会严重影响其他应用程序显示的颜色。 Windows 使用应用程序的逻辑调色板（所需颜色的列表）和系统调色板（定义可用颜色）来确定所使用的颜色。

`CPalette` 对象提供用于操作由对象引用的调色板的成员函数。 构造 `CPalette` 对象并使用其成员函数创建实际调色板、图形设备接口（GDI）对象，以及操作其项和其他属性。

有关使用 `CPalette`的详细信息，请参阅[图形对象](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPalette`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="animatepalette"></a>CPalette：： AnimatePalette

替换附加到 `CPalette` 对象的逻辑调色板中的条目。

```
void AnimatePalette(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>parameters

*nStartIndex*<br/>
指定要进行动画处理的调色板中的第一个条目。

*nNumEntries*<br/>
指定要进行动画处理的调色板中的条目数。

*lpPaletteColors*<br/>
指向[PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\))结构数组的第一个成员，以替换*nStartIndex*和*nNumEntries*标识的调色板项。

### <a name="remarks"></a>备注

当应用程序调用 `AnimatePalette`时，无需更新其客户端区域，因为 Windows 会立即将新项映射到系统调色板。

`AnimatePalette` 函数将只更改附加到 `CPalette` 对象的[LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette)结构的相应 `palPaletteEntry` 成员中具有 PC_RESERVED 标志的条目。 有关此结构的详细信息，请参阅 Windows SDK 中的 LOGPALETTE。

##  <a name="cpalette"></a>CPalette：： CPalette

构造 `CPalette` 对象。

```
CPalette();
```

### <a name="remarks"></a>备注

对象没有附加调色板，直到你调用 `CreatePalette` 以附加一个。

##  <a name="createhalftonepalette"></a>CPalette：： CreateHalftonePalette

创建设备上下文的半色调调色板。

```
BOOL CreateHalftonePalette(CDC* pDC);
```

### <a name="parameters"></a>parameters

*pDC*<br/>
标识设备上下文。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

当设备上下文的拉伸模式设置为半色调时，应用程序应创建半色调调色板。 然后，在调用[CDC：： StretchBlt](../../mfc/reference/cdc-class.md#stretchblt)或[StretchDIBits](/windows/win32/api/wingdi/nf-wingdi-stretchdibits)函数之前，应选择[CreateHalftonePalette](/windows/win32/api/wingdi/nf-wingdi-createhalftonepalette)成员函数返回的逻辑半色调调色板，并将其实现到设备上下文。

有关 `CreateHalftonePalette` 和 `StretchDIBits`的详细信息，请参阅 Windows SDK。

##  <a name="createpalette"></a>CPalette：： CreatePalette

通过创建 Windows 逻辑调色板并将其附加到 `CPalette` 对象，初始化 `CPalette` 对象。

```
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```

### <a name="parameters"></a>parameters

*lpLogPalette*<br/>
指向[LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette)结构，该结构包含有关逻辑调色板中的颜色的信息。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

有关 `LOGPALETTE` 结构的详细信息，请参阅 Windows SDK。

##  <a name="fromhandle"></a>CPalette：： FromHandle

当给定 Windows 调色板对象的句柄时，返回指向 `CPalette` 对象的指针。

```
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```

### <a name="parameters"></a>parameters

*hPalette*<br/>
Windows GDI 调色板的句柄。

### <a name="return-value"></a>返回值

如果成功，则为指向 `CPalette` 对象的指针;否则为 NULL。

### <a name="remarks"></a>备注

如果 `CPalette` 对象尚未附加到 Windows 调色板，则会创建并附加一个临时 `CPalette` 对象。 此临时 `CPalette` 对象仅在下一次应用程序的事件循环中有空闲时间之前有效，在这段时间内删除所有临时图形对象。 换言之，只有在处理一条窗口消息的过程中，临时对象才有效。

##  <a name="getentrycount"></a>CPalette：： GetEntryCount

调用此成员函数以检索给定逻辑调色板中的条目数。

```
int GetEntryCount();
```

### <a name="return-value"></a>返回值

逻辑调色板中的项数。

##  <a name="getnearestpaletteindex"></a>CPalette：： GetNearestPaletteIndex

返回与指定的颜色值最匹配的逻辑调色板中的项的索引。

```
UINT GetNearestPaletteIndex(COLORREF crColor) const;
```

### <a name="parameters"></a>parameters

*crColor*<br/>
指定要匹配的颜色。

### <a name="return-value"></a>返回值

逻辑调色板中的项的索引。 此条目包含与指定颜色最接近的颜色。

##  <a name="getpaletteentries"></a>CPalette：： GetPaletteEntries

检索逻辑调色板中的一系列调色板项。

```
UINT GetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors) const;
```

### <a name="parameters"></a>parameters

*nStartIndex*<br/>
指定要检索的逻辑调色板中的第一个条目。

*nNumEntries*<br/>
指定要检索的逻辑调色板中的条目数。

*lpPaletteColors*<br/>
指向[PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\))数据结构的数组以接收调色板项。 数组包含的数据结构必须至少包含*nNumEntries*指定的数量。

### <a name="return-value"></a>返回值

从逻辑调色板检索的项数;如果函数失败，则为0。

##  <a name="operator_hpalette"></a>CPalette：： operator HPALETTE

使用此运算符可获取 `CPalette` 对象的附加 Windows GDI 句柄。

```
operator HPALETTE() const;
```

### <a name="return-value"></a>返回值

如果成功，则为 `CPalette` 对象表示的 Windows GDI 对象的句柄;否则为 NULL。

### <a name="remarks"></a>备注

此运算符是支持直接使用 HPALETTE 对象的强制转换运算符。

有关使用图形对象的详细信息，请参阅文章 Windows SDK 中的[图形对象](/windows/win32/gdi/graphic-objects)。

##  <a name="resizepalette"></a>CPalette：： ResizePalette

将附加到 `CPalette` 对象的逻辑调色板的大小更改为*nNumEntries*指定的项数。

```
BOOL ResizePalette(UINT nNumEntries);
```

### <a name="parameters"></a>parameters

*nNumEntries*<br/>
指定调整后调色板中的条目数。

### <a name="return-value"></a>返回值

如果成功调整调色板的大小，则为非零值;否则为0。

### <a name="remarks"></a>备注

如果应用程序调用 `ResizePalette` 来减小调色板的大小，则已调整大小的调色板中剩余的条目保持不变。 如果应用程序调用 `ResizePalette` 来放大调色板，则附加调色板项设置为黑色（红色、绿色和蓝色值均为0），所有其他项的标志设置为0。

有关 Windows API `ResizePalette`的详细信息，请参阅 Windows SDK 中的[ResizePalette](/windows/win32/api/wingdi/nf-wingdi-resizepalette) 。

##  <a name="setpaletteentries"></a>CPalette：： SetPaletteEntries

设置逻辑调色板中某一范围的项的 RGB 颜色值和标志。

```
UINT SetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>parameters

*nStartIndex*<br/>
指定要设置的逻辑调色板中的第一个条目。

*nNumEntries*<br/>
指定要设置的逻辑调色板中的条目数。

*lpPaletteColors*<br/>
指向[PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\))数据结构的数组以接收调色板项。 数组包含的数据结构必须至少包含*nNumEntries*指定的数量。

### <a name="return-value"></a>返回值

逻辑调色板中设置的项数;如果函数失败，则为0。

### <a name="remarks"></a>备注

当应用程序调用 `SetPaletteEntries`时，如果在设备上下文中选择了逻辑调色板，则在应用程序调用[CDC：： RealizePalette](../../mfc/reference/cdc-class.md#realizepalette)之前，这些更改不会生效。

有关详细信息，请参阅 Windows SDK 中的[PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) 。

## <a name="see-also"></a>另请参阅

[MFC 示例 DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 类](../../mfc/reference/cgdiobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CPalette：： GetPaletteEntries](#getpaletteentries)<br/>
[CPalette：： SetPaletteEntries](#setpaletteentries)
