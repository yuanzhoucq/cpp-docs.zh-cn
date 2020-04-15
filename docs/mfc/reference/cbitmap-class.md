---
title: CBitmap 类
ms.date: 11/04/2016
f1_keywords:
- CBitmap
- AFXWIN/CBitmap
- AFXWIN/CBitmap::CBitmap
- AFXWIN/CBitmap::CreateBitmap
- AFXWIN/CBitmap::CreateBitmapIndirect
- AFXWIN/CBitmap::CreateCompatibleBitmap
- AFXWIN/CBitmap::CreateDiscardableBitmap
- AFXWIN/CBitmap::FromHandle
- AFXWIN/CBitmap::GetBitmap
- AFXWIN/CBitmap::GetBitmapBits
- AFXWIN/CBitmap::GetBitmapDimension
- AFXWIN/CBitmap::LoadBitmap
- AFXWIN/CBitmap::LoadMappedBitmap
- AFXWIN/CBitmap::LoadOEMBitmap
- AFXWIN/CBitmap::SetBitmapBits
- AFXWIN/CBitmap::SetBitmapDimension
helpviewer_keywords:
- CBitmap [MFC], CBitmap
- CBitmap [MFC], CreateBitmap
- CBitmap [MFC], CreateBitmapIndirect
- CBitmap [MFC], CreateCompatibleBitmap
- CBitmap [MFC], CreateDiscardableBitmap
- CBitmap [MFC], FromHandle
- CBitmap [MFC], GetBitmap
- CBitmap [MFC], GetBitmapBits
- CBitmap [MFC], GetBitmapDimension
- CBitmap [MFC], LoadBitmap
- CBitmap [MFC], LoadMappedBitmap
- CBitmap [MFC], LoadOEMBitmap
- CBitmap [MFC], SetBitmapBits
- CBitmap [MFC], SetBitmapDimension
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
ms.openlocfilehash: 9a33a6e1bea601422e043d7f2a80029c72d97e50
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352748"
---
# <a name="cbitmap-class"></a>CBitmap 类

封装一个 Windows 图形设备接口 (GDI) 位图并提供成员函数以操作位图。

## <a name="syntax"></a>语法

```
class CBitmap : public CGdiObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C 位图：：C 位图](#cbitmap)|构造 `CBitmap` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C 位图：：创建位图](#createbitmap)|使用具有指定宽度、高度和位模式的与设备相关的内存位图初始化对象。|
|[C 位映射：：创建位图间接](#createbitmapindirect)|使用在`BITMAP`结构中给出的宽度、高度和位模式（如果指定）的位图初始化对象。|
|[C 位映射：：创建兼容位图](#createcompatiblebitmap)|使用位图初始化对象，使其与指定的设备兼容。|
|[C 位映射：：创建可丢弃的位图](#creatediscardablebitmap)|使用与指定设备兼容的可丢弃位图初始化对象。|
|[CBitmap：：从手处理](#fromhandle)|当为 Windows`CBitmap``HBITMAP`位图指定句柄时，返回指向对象的指针。|
|[C 位图：：获取位图](#getbitmap)|使用有关位`BITMAP`图的信息填充结构。|
|[C 位映射：：获取位图位](#getbitmapbits)|将指定位图的位数复制到指定的缓冲区中。|
|[C 位映射：：获取位图维度](#getbitmapdimension)|返回位图的宽度和高度。 假定高度和宽度以前由[SetBitmapDimension 成员](#setbitmapdimension)函数设置。|
|[C 位映射：：加载位图](#loadbitmap)|通过从应用程序的可执行文件加载指定的位图资源并将位映射附加到对象来初始化对象。|
|[C 位映射：：加载映射的位图](#loadmappedbitmap)|加载位图并将颜色映射到当前系统颜色。|
|[C 位图：：加载OEM比特图](#loadoembitmap)|通过加载预定义的 Windows 位图并将位图附加到对象来初始化对象。|
|[C 位映射：：设置位图位](#setbitmapbits)|将位图的位位设置到指定的位值。|
|[C 位映射：：设置位图维度](#setbitmapdimension)|以 0.1 毫米单位为单位将宽度和高度分配给位图。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CBitmap：：运算符 HBITMAP](#operator_hbitmap)|返回附加到`CBitmap`对象的 Windows 句柄。|

## <a name="remarks"></a>备注

要使用`CBitmap`对象，构造对象，使用初始化成员函数之一将位图句柄附加到对象，然后调用对象的成员函数。

有关使用图形对象的详细信息，请参阅`CBitmap`图形[对象](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBitmap`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cbitmapcbitmap"></a><a name="cbitmap"></a>C 位图：：C 位图

构造 `CBitmap` 对象。

```
CBitmap();
```

### <a name="remarks"></a>备注

生成的对象必须使用初始化成员函数之一进行初始化。

## <a name="cbitmapcreatebitmap"></a><a name="createbitmap"></a>C 位图：：创建位图

初始化具有指定的宽度、高度和位模式的设备相关的内存位图。

```
BOOL CreateBitmap(
    int nWidth,
    int nHeight,
    UINT nPlanes,
    UINT nBitcount,
    const void* lpBits);
```

### <a name="parameters"></a>参数

*n 宽度*<br/>
指定位图的宽度（以像素为单位）。

*nHeight*<br/>
指定位图的高度（以像素为单位）。

*n飞机*<br/>
指定位图中的颜色平面的数量。

*nBitcount*<br/>
指定每个显示像素的颜色位的数量。

*lpBits*<br/>
指向包含的初始位图位值的字节的数组。 如果它是 NULL，新位图则未初始化。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

对于颜色位图，应将*nPlanes*或*nBitcount*参数设置为 1。 如果这些参数均设为 1， `CreateBitmap` 则会创建一个单色位图。

尽管无法为显示设备直接选择位图，但可以使用 [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) 选择将它作为“内存设备上下文”的当前位图，并使用 [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) 函数将其复制到任何兼容的设备上下文中。

完成通过 `CBitmap` 函数创建的 `CreateBitmap` 对象后，首先选择设备上下文中的位图，然后删除 `CBitmap` 对象。

有关详细信息，请参阅`bmBits``BITMAP`结构中字段的说明。 [BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap) 结构根据 [CBitmap::CreateBitmapIndirect](#createbitmapindirect) 成员函数进行说明。

## <a name="cbitmapcreatebitmapindirect"></a><a name="createbitmapindirect"></a>C 位映射：：创建位图间接

初始化具有*lpBitmap*指向的结构中给出的宽度、高度和位模式的位图（如果指定了）。

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>参数

*lpBitmap*<br/>
指向包含位图信息的[BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap)结构。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

尽管无法直接为显示设备选择位图，但可以使用[CDC：：选择Object，](../../mfc/reference/cdc-class.md#selectobject)并使用[CDC：：BitBlt](../../mfc/reference/cdc-class.md#bitblt)或[CDC：：StretchBlt](../../mfc/reference/cdc-class.md#stretchblt)函数将其作为内存设备上下文的当前位图选择。 [（CDC：:PatBlt](../../mfc/reference/cdc-class.md#patblt)函数可以将当前画笔的位图直接复制到显示设备上下文。

如果使用`BITMAP``GetObject`*函数填充了 lpBitmap*参数指向的结构，则不会指定位图位位，并且位图未初始化。 要初始化位图，应用程序可以使用[CDC：：BitBlt](../../mfc/reference/cdc-class.md#bitblt)或[SetDIBits](/windows/win32/api/wingdi/nf-wingdi-setdibits)等函数将位从`CGdiObject::GetObject``CreateBitmapIndirect`

完成使用`CBitmap``CreateBitmapIndirect`函数创建的对象后，首先从设备上下文中选择位图，然后删除`CBitmap`该对象。

## <a name="cbitmapcreatecompatiblebitmap"></a><a name="createcompatiblebitmap"></a>C 位映射：：创建兼容位图

初始化与*pDC*指定的设备兼容的位图。

```
BOOL CreateCompatibleBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指定设备上下文。

*n 宽度*<br/>
指定位图的宽度（以像素为单位）。

*nHeight*<br/>
指定位图的高度（以像素为单位）。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

位图的颜色平面数或每像素位格式与指定设备上下文相同。 它可以选择作为当前位图的任何内存设备，兼容*pDC*指定的。

如果*pDC*是内存设备上下文，则返回的位图的格式与该设备上下文中当前选择的位图相同。 "内存设备上下文"是表示显示表面的内存块。 它可用于在将图像复制到兼容设备的实际显示表面之前在内存中准备图像。

创建内存设备上下文时，GDI 会自动为其选择单色股票位图。

由于颜色存储器设备上下文可以选择颜色或单色位图，`CreateCompatibleBitmap`因此函数返回的位图格式并不总是相同的;因此，该函数返回的位图格式并不总是相同的。否则，该函数返回的位图格式将始终相同。但是，非内存设备上下文的兼容位图的格式始终采用设备的格式。

完成使用`CBitmap``CreateCompatibleBitmap`函数创建的对象后，首先从设备上下文中选择位图，然后删除`CBitmap`该对象。

## <a name="cbitmapcreatediscardablebitmap"></a><a name="creatediscardablebitmap"></a>C 位映射：：创建可丢弃的位图

初始化可丢弃的位图，该位图与*pDC*标识的设备上下文兼容。

```
BOOL CreateDiscardableBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指定设备上下文。

*n 宽度*<br/>
指定位图的宽度（以位表示）。

*nHeight*<br/>
指定位图的高度（以位表示）。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

位图的颜色平面数或每像素位格式与指定设备上下文相同。 应用程序可以选择此位图作为与*pDC*指定的内存设备的当前位图。

仅当应用程序未将其选择到显示上下文中时，Windows 才能丢弃由此函数创建的位图。 如果 Windows 在未选中位图时丢弃位图，并且应用程序以后尝试选择它，[则 CDC：：SelectObject](../../mfc/reference/cdc-class.md#selectobject)函数将返回 NULL。

完成使用`CBitmap``CreateDiscardableBitmap`函数创建的对象后，首先从设备上下文中选择位图，然后删除`CBitmap`该对象。

## <a name="cbitmapfromhandle"></a><a name="fromhandle"></a>CBitmap：：从手处理

当为 Windows `CBitmap` GDI 位图指定句柄时，返回指向对象的指针。

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>参数

*hBitmap*<br/>
指定 Windows GDI 位图。

### <a name="return-value"></a>返回值

指向`CBitmap`对象的指针（如果成功）;如果成功，则指向对象。否则 NULL。

### <a name="remarks"></a>备注

如果对象`CBitmap`尚未附加到句柄，则创建并附加临时`CBitmap`对象。 此临时`CBitmap`对象仅在下次应用程序在其事件循环中有空闲时间之前有效，此时将删除所有临时图形对象。 另一种说法是临时对象仅在处理一个窗口消息期间有效。

## <a name="cbitmapgetbitmap"></a><a name="getbitmap"></a>C 位图：：获取位图

检索附加位图的图像属性。

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>参数

*pBitMap*<br/>
指向将接收图像属性的[BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap)结构的指针。 此参数不能为 NULL。

### <a name="return-value"></a>返回值

如果方法成功，则非零;否则 0。

### <a name="remarks"></a>备注

## <a name="cbitmapgetbitmapbits"></a><a name="getbitmapbits"></a>C 位映射：：获取位图位

将附加位图的位模式复制到指定的缓冲区中。

```
DWORD GetBitmapBits(
    DWORD dwCount,
    LPVOID lpBits) const;
```

### <a name="parameters"></a>参数

*dwCount*<br/>
要复制到缓冲区的字节数。

*lpBits*<br/>
指向将接收位图的缓冲区的指针。

### <a name="return-value"></a>返回值

如果方法成功，则复制到缓冲区的字节数;否则 0。

### <a name="remarks"></a>备注

使用[CBitmap：：GetBitmap](#getbitmap)确定所需的缓冲区大小。

## <a name="cbitmapgetbitmapdimension"></a><a name="getbitmapdimension"></a>C 位映射：：获取位图维度

返回位图的宽度和高度。

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>返回值

位图的宽度和高度，以 0.1 毫米为单位测量。 高度位于对象`cy`的成员中`CSize`，宽度位于成员中。 `cx` 如果未使用`SetBitmapDimension`设置位图宽度和高度，则返回值为 0。

### <a name="remarks"></a>备注

使用[SetBitmapDimension 成员](#setbitmapdimension)函数假定高度和宽度以前已设置。

## <a name="cbitmaploadbitmap"></a><a name="loadbitmap"></a>C 位映射：：加载位图

从应用程序的可执行文件加载由*lpszResourceName*命名的位图资源，或由*nIDResource*中的 ID 号标识。

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>参数

*lpsz 资源名称*<br/>
指向包含位图资源名称的 null 端接字符串。

*nID资源*<br/>
指定位图资源的资源 ID 号。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

加载的位图附加到`CBitmap`对象。

如果*lpszResourceName*标识的位图不存在，或者内存不足以加载位图，则函数返回 0。

您可以使用[CGdiObject：:DeleteObject 函数](../../mfc/reference/cgdiobject-class.md#deleteobject)删除函数加载的`LoadBitmap`位图，否则`CBitmap`析构函数将为您删除对象。

> [!CAUTION]
> 在删除对象之前，请确保未将其选择到设备上下文中。

以下位图已添加到 Windows 版本 3.1 及更高版本：

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

这些位图在 Windows 版本 3.0 和更早版本的设备驱动程序中找不到。 有关位图的完整列表及其外观的显示，请参阅 Windows SDK。

## <a name="cbitmaploadmappedbitmap"></a><a name="loadmappedbitmap"></a>C 位映射：：加载映射的位图

调用此成员函数以加载位图并将颜色映射到当前系统颜色。

```
BOOL LoadMappedBitmap(
    UINT nIDBitmap,
    UINT nFlags = 0,
    LPCOLORMAP lpColorMap = NULL,
    int nMapSize = 0);
```

### <a name="parameters"></a>参数

*nIDBitmap*<br/>
位图资源的 ID。

*nFlags*<br/>
位图的标志。 可以是零或CMB_MASKED。

*lpColorMap*<br/>
指向包含映射位`COLORMAP`图所需的颜色信息的结构的指针。 如果此参数为 NULL，则函数使用默认颜色映射。

*nMapSize*<br/>
由 lpColorMap 指向的颜色*贴图的数量*。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

默认情况下，`LoadMappedBitmap`将映射按钮字形中常用的颜色。

有关创建映射位图的信息，请参阅 Windows 函数[创建映射的双边地图](https://go.microsoft.com/fwlink/p/?linkid=230562)和 Windows SDK 中的[COLORMAP](/windows/win32/api/commctrl/ns-commctrl-colormap)结构。

## <a name="cbitmaploadoembitmap"></a><a name="loadoembitmap"></a>C 位图：：加载OEM比特图

加载 Windows 使用的预定义位图。

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>参数

*nIDBitmap*<br/>
预定义的 Windows 位图的 ID 号。 以下 WINDOWS 列出了可能的值。H：

|||
|-|-|
|OBM_BTNCORNERS|OBM_OLD_RESTORE|
|OBM_BTSIZE|OBM_OLD_RGARROW|
|OBM_CHECK|OBM_OLD_UPARROW|
|OBM_CHECKBOXES|OBM_OLD_ZOOM|
|OBM_CLOSE|OBM_REDUCE|
|OBM_COMBO|OBM_REDUCED|
|OBM_DNARROW|OBM_RESTORE|
|OBM_DNARROWD|OBM_RESTORED|
|OBM_DNARROWI|OBM_RGARROW|
|OBM_LFARROW|OBM_RGARROWD|
|OBM_LFARROWD|OBM_RGARROWI|
|OBM_LFARROWI|OBM_SIZE|
|OBM_MNARROW|OBM_UPARROW|
|OBM_OLD_CLOSE|OBM_UPARROWD|
|OBM_OLD_DNARROW|OBM_UPARROW|
|OBM_OLD_LFARROW|OBM_ZOOM|
|OBM_OLD_REDUCE|OBM_ZOOMD|

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

以OBM_OLD开头的位图名称表示 Windows 版本在 3.0 之前使用的位图。

请注意，在包括 WINDOWS 之前，必须定义常量 OEM 资源。H 以便使用**OBM_常量**中的任何一个。

## <a name="cbitmapoperator-hbitmap"></a><a name="operator_hbitmap"></a>CBitmap：：运算符 HBITMAP

使用此运算符获取`CBitmap`对象的附加 Windows GDI 句柄。

```
operator HBITMAP() const;
```

### <a name="return-value"></a>返回值

如果成功，则对对象表示的 Windows GDI`CBitmap`对象的句柄;如果成功，则对对象表示的 Windows GDI 对象的句柄。否则 NULL。

### <a name="remarks"></a>备注

此运算符是强制转换运算符，支持直接使用`HBITMAP`对象。

有关使用图形对象的详细信息，请参阅 Windows SDK 中的[图形对象](/windows/win32/gdi/graphic-objects)。

## <a name="cbitmapsetbitmapbits"></a><a name="setbitmapbits"></a>C 位映射：：设置位图位

将位图的位位设置到*lpBits*给出的位值。

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>参数

*dwCount*<br/>
指定*lpBits*指向的字节数。

*lpBits*<br/>
指向包含要复制到`CBitmap`对象的像素值的 BYTE 数组。 为了使位图能够正确呈现其图像，应设置这些值的格式，使其与创建 CBitmap 实例时指定的高度、宽度和颜色深度值一致。 有关详细信息，请参阅[CBitmap：：创建位图](#createbitmap)。

### <a name="return-value"></a>返回值

用于设置位图位的字节数;如果函数失败，为 0。

## <a name="cbitmapsetbitmapdimension"></a><a name="setbitmapdimension"></a>C 位映射：：设置位图维度

以 0.1 毫米单位为单位将宽度和高度分配给位图。

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>参数

*n 宽度*<br/>
指定位图的宽度（以 0.1 毫米为单位）。

*nHeight*<br/>
指定位图的高度（以 0.1 毫米为单位）。

### <a name="return-value"></a>返回值

前面的位图尺寸。 高度位于对象`cy`的成员变量中`CSize`，宽度位于成员变量中。 `cx`

### <a name="remarks"></a>备注

GDI 不使用这些值，除非在应用程序调用[GetBitmapDimension 成员](#getbitmapdimension)函数时返回它们。

## <a name="see-also"></a>另请参阅

[MFC 样品 MDI](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 类](../../mfc/reference/cgdiobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
