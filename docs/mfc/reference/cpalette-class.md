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
ms.openlocfilehash: 83cd125fa7ab64aa39c606bc048022400d158e72
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374764"
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
|[CPalette：CPalette](#cpalette)|构造没有附加`CPalette`的 Windows 调色板的对象。 必须先使用初始化成员`CPalette`函数之一初始化对象，然后才能使用它。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CPalette：动画调色板](#animatepalette)|替换对象标识的逻辑调色板中的`CPalette`条目。 应用程序不必更新其工作区，因为 Windows 会立即将新条目映射到系统调色板中。|
|[CPalette：：创建半色调调色板](#createhalftonepalette)|为设备上下文创建半色调调色板并将其附加到`CPalette`对象。|
|[CPalette：：创建调色板](#createpalette)|创建 Windows 调色板并将其附加到`CPalette`对象。|
|[CPalette：从手柄](#fromhandle)|当为 Windows`CPalette`调色板对象的句柄时，返回指向对象的指针。|
|[CPalette：获取入口计数](#getentrycount)|检索逻辑调色板中的调色板条目数。|
|[CPalette：获取最接近的调色板索引](#getnearestpaletteindex)|返回逻辑调色板中最匹配颜色值的条目的索引。|
|[CPalette：获取调色板](#getpaletteentries)|检索逻辑调色板中的一系列调色板条目。|
|[CPalette：调整调色板的大小](#resizepalette)|将`CPalette`对象指定的逻辑调色板的大小更改为指定的条目数。|
|[CPalette：：设置调色板](#setpaletteentries)|在逻辑调色板中的一系列条目中设置 RGB 颜色值和标志。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CPalette：：操作员 HPALETTE](#operator_hpalette)|返回附加到 的`CPalette`HPALETTE。|

## <a name="remarks"></a>备注

调色板提供应用程序和颜色输出设备（如显示设备）之间的接口。 该接口允许应用程序充分利用输出设备的颜色功能，而不会严重干扰其他应用程序显示的颜色。 Windows 使用应用程序的逻辑调色板（所需颜色的列表）和系统调色板（定义可用颜色）来确定使用的颜色。

对象`CPalette`提供用于操作对象引用的调色板的成员函数。 构造`CPalette`对象并使用其成员函数创建实际调色板、图形设备接口 （GDI） 对象，并操作其条目和其他属性。

有关 使用`CPalette`的详细信息，请参阅[图形对象](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPalette`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cpaletteanimatepalette"></a><a name="animatepalette"></a>CPalette：动画调色板

替换附加到`CPalette`对象的逻辑调色板中的条目。

```
void AnimatePalette(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>参数

*nStartIndex*<br/>
指定要进行动画处理的调色板中的第一个条目。

*nNum条目*<br/>
指定要进行动画处理的调色板中的条目数。

*lpPalette颜色*<br/>
指向[PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\))结构数组的第一个成员，以替换*nStartIndex*和*nNumentry*标识的调色板条目。

### <a name="remarks"></a>备注

当应用程序调用`AnimatePalette`时，它不必更新其工作区，因为 Windows 会立即将新条目映射到系统调色板中。

该`AnimatePalette`函数将仅更改附加到对象的[LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette)结构的`CPalette`相应`palPaletteEntry`成员中设置PC_RESERVED标志的条目。 有关此结构的详细信息，请参阅 Windows SDK 中的 LOGPALETTE。

## <a name="cpalettecpalette"></a><a name="cpalette"></a>CPalette：CPalette

构造 `CPalette` 对象。

```
CPalette();
```

### <a name="remarks"></a>备注

在调用`CreatePalette`附加一个调色板之前，该对象没有附加的调色板。

## <a name="cpalettecreatehalftonepalette"></a><a name="createhalftonepalette"></a>CPalette：：创建半色调调色板

为设备上下文创建半色调调色板。

```
BOOL CreateHalftonePalette(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
标识设备上下文。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

当设备上下文的拉伸模式设置为 HALFTONE 时，应用程序应创建半色调调色板。 然后，在调用[CDC：：：拉伸Blt](../../mfc/reference/cdc-class.md#stretchblt)或[拉伸DIBits](/windows/win32/api/wingdi/nf-wingdi-stretchdibits)函数之前，应选择[CreateHalftonePalette](/windows/win32/api/wingdi/nf-wingdi-createhalftonepalette)成员函数返回的逻辑半色调调色板并将其实现到设备上下文中。

有关`CreateHalftonePalette`和`StretchDIBits`的详细信息，请参阅 Windows SDK。

## <a name="cpalettecreatepalette"></a><a name="createpalette"></a>CPalette：：创建调色板

通过创建 Windows`CPalette`逻辑调色板并将其附加到对象来`CPalette`初始化对象。

```
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```

### <a name="parameters"></a>参数

*lpLogPalette*<br/>
指向包含逻辑调色板中颜色信息的[LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette)结构。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

有关结构的详细信息，`LOGPALETTE`请参阅 Windows SDK。

## <a name="cpalettefromhandle"></a><a name="fromhandle"></a>CPalette：从手柄

当为 Windows`CPalette`调色板对象的句柄时，返回指向对象的指针。

```
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```

### <a name="parameters"></a>参数

*hPalette*<br/>
Windows GDI 调色板的句柄。

### <a name="return-value"></a>返回值

指向`CPalette`对象的指针（如果成功）;如果成功，则指向对象。否则 NULL。

### <a name="remarks"></a>备注

如果对象`CPalette`尚未附加到 Windows 调色板，则创建并附加临时`CPalette`对象。 此临时`CPalette`对象仅在下次应用程序在其事件循环中有空闲时间之前有效，此时将删除所有临时图形对象。 换句话说，临时对象仅在处理一个窗口消息期间有效。

## <a name="cpalettegetentrycount"></a><a name="getentrycount"></a>CPalette：获取入口计数

调用此成员函数以检索给定逻辑调色板中的条目数。

```
int GetEntryCount();
```

### <a name="return-value"></a>返回值

逻辑调色板中的条目数。

## <a name="cpalettegetnearestpaletteindex"></a><a name="getnearestpaletteindex"></a>CPalette：获取最接近的调色板索引

返回逻辑调色板中最与指定颜色值匹配的条目的索引。

```
UINT GetNearestPaletteIndex(COLORREF crColor) const;
```

### <a name="parameters"></a>参数

*crColor*<br/>
指定要匹配的颜色。

### <a name="return-value"></a>返回值

逻辑调色板中条目的索引。 该条目包含最接近与指定颜色匹配的颜色。

## <a name="cpalettegetpaletteentries"></a><a name="getpaletteentries"></a>CPalette：获取调色板

检索逻辑调色板中的一系列调色板条目。

```
UINT GetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors) const;
```

### <a name="parameters"></a>参数

*nStartIndex*<br/>
指定要检索的逻辑调色板中的第一个条目。

*nNum条目*<br/>
指定要检索的逻辑调色板中的条目数。

*lpPalette颜色*<br/>
指向[PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\))数据结构数组以接收调色板条目。 数组必须包含至少与*nNumentries*指定的相同数量的数据结构。

### <a name="return-value"></a>返回值

从逻辑调色板检索的条目数;如果函数失败，为 0。

## <a name="cpaletteoperator-hpalette"></a><a name="operator_hpalette"></a>CPalette：：操作员 HPALETTE

使用此运算符获取`CPalette`对象的附加 Windows GDI 句柄。

```
operator HPALETTE() const;
```

### <a name="return-value"></a>返回值

如果成功，则对对象表示的 Windows GDI`CPalette`对象的句柄;如果成功，则对对象表示的 Windows GDI 对象的句柄。否则 NULL。

### <a name="remarks"></a>备注

此运算符是强制转换运算符，支持直接使用 HPALETTE 对象。

有关使用图形对象的详细信息，请参阅 Windows SDK 中的["图形对象](/windows/win32/gdi/graphic-objects)"一文。

## <a name="cpaletteresizepalette"></a><a name="resizepalette"></a>CPalette：调整调色板的大小

将附加到`CPalette`对象的逻辑调色板的大小更改为*nNumentries*指定的条目数。

```
BOOL ResizePalette(UINT nNumEntries);
```

### <a name="parameters"></a>参数

*nNum条目*<br/>
指定调色板调整大小后条目数。

### <a name="return-value"></a>返回值

如果调色板成功调整大小，则非零;否则 0。

### <a name="remarks"></a>备注

如果应用程序调用`ResizePalette`以减小调色板的大小，则调整大小的调色板中剩余的条目将保持不变。 如果应用程序调用`ResizePalette`以放大调色板，则其他调色板条目设置为黑色（红色、绿色和蓝色值为 0），所有附加条目的标志设置为 0。

有关 Windows API`ResizePalette`的详细信息，请参阅在 Windows SDK 中[调整调色板的大小](/windows/win32/api/wingdi/nf-wingdi-resizepalette)。

## <a name="cpalettesetpaletteentries"></a><a name="setpaletteentries"></a>CPalette：：设置调色板

在逻辑调色板中的一系列条目中设置 RGB 颜色值和标志。

```
UINT SetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>参数

*nStartIndex*<br/>
指定要设置的逻辑调色板中的第一个条目。

*nNum条目*<br/>
指定要设置的逻辑调色板中的条目数。

*lpPalette颜色*<br/>
指向[PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\))数据结构数组以接收调色板条目。 数组必须包含至少与*nNumentries*指定的相同数量的数据结构。

### <a name="return-value"></a>返回值

逻辑调色板中设置的条目数;如果函数失败，为 0。

### <a name="remarks"></a>备注

如果在应用程序调用`SetPaletteEntries`时将逻辑调色板选择到设备上下文中，则在应用程序调用[CDC：：：实现调色板](../../mfc/reference/cdc-class.md#realizepalette)之前，更改不会生效。

有关详细信息，请参阅 Windows SDK 中的[PALETTEENTRY。](/previous-versions/dd162769\(v=vs.85\))

## <a name="see-also"></a>另请参阅

[MFC 样品 DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 类](../../mfc/reference/cgdiobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CPalette：获取调色板](#getpaletteentries)<br/>
[CPalette：：设置调色板](#setpaletteentries)
