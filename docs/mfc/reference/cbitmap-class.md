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
ms.openlocfilehash: 7161a4cf4484b6cc9e76e6955de558ca6e9121ca
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424679"
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
|[CBitmap：： CBitmap](#cbitmap)|构造 `CBitmap` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CBitmap：： CreateBitmap](#createbitmap)|使用具有指定的宽度、高度和位模式的设备相关的内存位图初始化对象。|
|[CBitmap：： CreateBitmapIndirect](#createbitmapindirect)|使用在 `BITMAP` 结构中给定的宽度、高度和位模式（如果已指定）初始化对象。|
|[CBitmap：： CreateCompatibleBitmap](#createcompatiblebitmap)|使用位图初始化对象，使其与指定的设备兼容。|
|[CBitmap：： CreateDiscardableBitmap](#creatediscardablebitmap)|使用与指定设备兼容的可放弃位图初始化对象。|
|[CBitmap：： FromHandle](#fromhandle)|给定 Windows `HBITMAP` 位图的句柄时，返回指向 `CBitmap` 对象的指针。|
|[CBitmap：： GetBitmap](#getbitmap)|使用有关位图的信息填充 `BITMAP` 结构。|
|[CBitmap：： GetBitmapBits](#getbitmapbits)|将指定位图的位复制到指定的缓冲区中。|
|[CBitmap：： GetBitmapDimension](#getbitmapdimension)|返回位图的宽度和高度。 高度和宽度假定之前已由[SetBitmapDimension](#setbitmapdimension)成员函数设置。|
|[CBitmap：： LoadBitmap](#loadbitmap)|通过从应用程序的可执行文件加载命名位图资源并将位图附加到对象，初始化对象。|
|[CBitmap：： LoadMappedBitmap](#loadmappedbitmap)|加载位图并将颜色映射到当前系统颜色。|
|[CBitmap：： LoadOEMBitmap](#loadoembitmap)|通过加载预定义的 Windows 位图并将位图附加到对象来初始化对象。|
|[CBitmap：： SetBitmapBits](#setbitmapbits)|将位图的位设置为指定的位值。|
|[CBitmap：： SetBitmapDimension](#setbitmapdimension)|为位图指定宽度和高度（以0.1 毫米为单位）。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[CBitmap：： operator HBITMAP](#operator_hbitmap)|返回附加到 `CBitmap` 对象的 Windows 句柄。|

## <a name="remarks"></a>备注

若要使用 `CBitmap` 对象，请构造对象，将位图句柄附加到一个初始化成员函数，然后调用该对象的成员函数。

有关使用 `CBitmap`图形对象的详细信息，请参阅[图形对象](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBitmap`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cbitmap"></a>CBitmap：： CBitmap

构造 `CBitmap` 对象。

```
CBitmap();
```

### <a name="remarks"></a>备注

必须用其中一个初始化成员函数初始化生成的对象。

##  <a name="createbitmap"></a>CBitmap：： CreateBitmap

初始化具有指定的宽度、高度和位模式的设备相关的内存位图。

```
BOOL CreateBitmap(
    int nWidth,
    int nHeight,
    UINT nPlanes,
    UINT nBitcount,
    const void* lpBits);
```

### <a name="parameters"></a>parameters

*nWidth*<br/>
指定位图的宽度（以像素为单位）。

*nHeight*<br/>
指定位图的高度（以像素为单位）。

*nPlanes*<br/>
指定位图中的颜色平面的数量。

*nBitcount*<br/>
指定每个显示像素的颜色位的数量。

*lpBits*<br/>
指向包含的初始位图位值的字节的数组。 如果它是 NULL，新位图则未初始化。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

对于颜色位图，应将*nPlanes*或*nBitcount*参数设置为1。 如果这些参数均设为 1， `CreateBitmap` 则会创建一个单色位图。

尽管无法为显示设备直接选择位图，但可以使用 [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) 选择将它作为“内存设备上下文”的当前位图，并使用 [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) 函数将其复制到任何兼容的设备上下文中。

完成通过 `CBitmap` 函数创建的 `CreateBitmap` 对象后，首先选择设备上下文中的位图，然后删除 `CBitmap` 对象。

有关详细信息，请参阅 `BITMAP` 结构中 `bmBits` 字段的说明。 [BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap) 结构根据 [CBitmap::CreateBitmapIndirect](#createbitmapindirect) 成员函数进行说明。

##  <a name="createbitmapindirect"></a>CBitmap：： CreateBitmapIndirect

初始化一个位图，该位图具有宽度、高度和位模式（如果已指定），并在*lpBitmap*指向的结构中给定。

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>parameters

*lpBitmap*<br/>
指向包含位图相关信息的[位图](/windows/win32/api/wingdi/ns-wingdi-bitmap)结构。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

尽管无法为显示设备直接选择位图，但可以使用[cdc：： SelectObject](../../mfc/reference/cdc-class.md#selectobject)将其选为内存设备上下文的当前位图，并使用[Cdc：： BitBlt](../../mfc/reference/cdc-class.md#bitblt)或[cdc：： StretchBlt](../../mfc/reference/cdc-class.md#stretchblt)函数将其复制到任何兼容的设备上下文。 （ [CDC：:P atblt](../../mfc/reference/cdc-class.md#patblt)函数可以将当前画笔的位图直接复制到显示设备上下文。）

如果通过使用 `GetObject` 函数填充了*lpBitmap*参数指向的 `BITMAP` 结构，则不会指定位图的位，也不会初始化位图。 若要初始化位图，应用程序可以使用函数（如[CDC：： BitBlt](../../mfc/reference/cdc-class.md#bitblt)或[SetDIBits](/windows/win32/api/wingdi/nf-wingdi-setdibits) ）将位从 `CGdiObject::GetObject` 的第一个参数所标识的位图复制到 `CreateBitmapIndirect`创建的位图。

完成用 `CreateBitmapIndirect` 函数创建的 `CBitmap` 对象后，首先选择设备上下文中的位图，然后删除 `CBitmap` 对象。

##  <a name="createcompatiblebitmap"></a>CBitmap：： CreateCompatibleBitmap

初始化与*pDC*指定的设备兼容的位图。

```
BOOL CreateCompatibleBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>parameters

*pDC*<br/>
指定设备上下文。

*nWidth*<br/>
指定位图的宽度（以像素为单位）。

*nHeight*<br/>
指定位图的高度（以像素为单位）。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

位图具有相同的颜色平面数，或与指定的设备上下文相同的每像素位数。 对于与*pDC*指定的内存设备兼容的任何内存设备，可以选择它作为当前位图。

如果*pDC*是内存设备上下文，则返回的位图的格式与该设备上下文中当前选定的位图的格式相同。 "内存设备上下文" 是表示显示图面的内存块。 它可用于在内存中准备图像，然后将其复制到兼容设备的实际显示表面。

创建内存设备上下文时，GDI 会自动为其选择单色股票位图。

由于彩色内存设备上下文可选择彩色或单色位图，因此 `CreateCompatibleBitmap` 函数返回的位图的格式并不总是相同;但是，nonmemory 设备上下文的兼容位图格式始终采用设备的格式。

完成用 `CreateCompatibleBitmap` 函数创建的 `CBitmap` 对象后，首先选择设备上下文中的位图，然后删除 `CBitmap` 对象。

##  <a name="creatediscardablebitmap"></a>CBitmap：： CreateDiscardableBitmap

初始化与*pDC*标识的设备上下文兼容的可放弃位图。

```
BOOL CreateDiscardableBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>parameters

*pDC*<br/>
指定设备上下文。

*nWidth*<br/>
指定位图的宽度（以位为单位）。

*nHeight*<br/>
指定位图的高度（位）。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

位图具有相同的颜色平面数，或与指定的设备上下文相同的每像素位数。 应用程序可以选择此位图作为与*pDC*指定的内存设备兼容的当前位图。

仅当应用程序未将其选定到显示上下文时，Windows 才能丢弃此函数创建的位图。 如果 Windows 在未选择该位图时将其丢弃，且应用程序稍后尝试选择它，则[CDC：： SelectObject](../../mfc/reference/cdc-class.md#selectobject)函数将返回 NULL。

完成用 `CreateDiscardableBitmap` 函数创建的 `CBitmap` 对象后，首先选择设备上下文中的位图，然后删除 `CBitmap` 对象。

##  <a name="fromhandle"></a>CBitmap：： FromHandle

当给定 Windows GDI 位图的句柄时，返回指向 `CBitmap` 对象的指针。

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>parameters

*hBitmap*<br/>
指定 Windows GDI 位图。

### <a name="return-value"></a>返回值

如果成功，则为指向 `CBitmap` 对象的指针;否则为 NULL。

### <a name="remarks"></a>备注

如果 `CBitmap` 对象尚未附加到句柄，则会创建并附加一个临时 `CBitmap` 对象。 此临时 `CBitmap` 对象仅在下一次应用程序的事件循环中有空闲时间之前有效，在这段时间内删除所有临时图形对象。 指出这一点的另一种方法是：只有在处理一条窗口消息的过程中，临时对象才有效。

##  <a name="getbitmap"></a>CBitmap：： GetBitmap

检索附加位图的图像属性。

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>parameters

*pBitMap*<br/>
指向将接收图像属性的[位图](/windows/win32/api/wingdi/ns-wingdi-bitmap)结构的指针。 此参数不得为 NULL。

### <a name="return-value"></a>返回值

如果方法成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

##  <a name="getbitmapbits"></a>CBitmap：： GetBitmapBits

将附加位图的位模式复制到指定的缓冲区中。

```
DWORD GetBitmapBits(
    DWORD dwCount,
    LPVOID lpBits) const;
```

### <a name="parameters"></a>parameters

*dwCount*<br/>
要复制到缓冲区的字节数。

*lpBits*<br/>
指向将接收位图的缓冲区的指针。

### <a name="return-value"></a>返回值

如果方法成功，则复制到缓冲区的字节数;否则为0。

### <a name="remarks"></a>备注

使用[CBitmap：： GetBitmap](#getbitmap)来确定所需的缓冲区大小。

##  <a name="getbitmapdimension"></a>CBitmap：： GetBitmapDimension

返回位图的宽度和高度。

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>返回值

位图的宽度和高度（以 0.1-毫米为单位）。 高度位于 `CSize` 对象的 `cy` 成员中，并且宽度在 `cx` 成员中。 如果未使用 `SetBitmapDimension`设置位图的宽度和高度，则返回值为0。

### <a name="remarks"></a>备注

使用[SetBitmapDimension](#setbitmapdimension)成员函数之前已设置了高度和宽度。

##  <a name="loadbitmap"></a>CBitmap：： LoadBitmap

加载由*lpszResourceName*命名的位图资源，或从应用程序的可执行文件的*NIDRESOURCE*中的 ID 号标识。

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>parameters

*lpszResourceName*<br/>
指向以 null 结尾的字符串，该字符串包含位图资源的名称。

*nIDResource*<br/>
指定位图资源的资源 ID 号。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

加载的位图附加到 `CBitmap` 对象上。

如果*lpszResourceName*标识的位图不存在，或者如果内存不足而无法加载位图，则函数返回0。

您可以使用[CGdiObject：:D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject)函数删除 `LoadBitmap` 函数加载的位图，否则 `CBitmap` 析构函数将删除该对象。

> [!CAUTION]
>  删除对象之前，请确保未在设备上下文中选择它。

在 Windows 版本3.1 及更高版本中添加了以下位图：

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

在 Windows 版本3.0 及更早版本的设备驱动程序中找不到这些位图。 有关位图的完整列表及其外观的显示，请参阅 Windows SDK。

##  <a name="loadmappedbitmap"></a>CBitmap：： LoadMappedBitmap

调用此成员函数以加载位图并将颜色映射到当前系统颜色。

```
BOOL LoadMappedBitmap(
    UINT nIDBitmap,
    UINT nFlags = 0,
    LPCOLORMAP lpColorMap = NULL,
    int nMapSize = 0);
```

### <a name="parameters"></a>parameters

*nIDBitmap*<br/>
位图资源的 ID。

*nFlags*<br/>
位图标志。 可以为零或 CMB_MASKED。

*lpColorMap*<br/>
指向 `COLORMAP` 结构的指针，该结构包含映射位图所需的颜色信息。 如果此参数为 NULL，则该函数使用默认颜色映射。

*nMapSize*<br/>
*LpColorMap*指向的颜色图的数目。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

默认情况下，`LoadMappedBitmap` 会映射按钮字形中常用的颜色。

有关创建映射的位图的信息，请参阅 Windows SDK 中的 Windows 函数[CreateMappedBitmap](https://go.microsoft.com/fwlink/p/?linkid=230562)和[COLORMAP](/windows/win32/api/commctrl/ns-commctrl-colormap)结构。

##  <a name="loadoembitmap"></a>CBitmap：： LoadOEMBitmap

加载 Windows 使用的预定义位图。

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>parameters

*nIDBitmap*<br/>
预定义的 Windows 位图的 ID 号。 下面从 WINDOWS 列出了可能的值。高

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

以 OBM_OLD 开头的位图名称表示3.0 之前的 Windows 版本使用的位图。

请注意，必须在包括 WINDOWS 之前定义常量 OEMRESOURCE。H，以便使用任意**OBM_** 常量。

##  <a name="operator_hbitmap"></a>CBitmap：： operator HBITMAP

使用此运算符可获取 `CBitmap` 对象的附加 Windows GDI 句柄。

```
operator HBITMAP() const;
```

### <a name="return-value"></a>返回值

如果成功，则为 `CBitmap` 对象表示的 Windows GDI 对象的句柄;否则为 NULL。

### <a name="remarks"></a>备注

此运算符是支持直接使用 `HBITMAP` 对象的强制转换运算符。

有关使用图形对象的详细信息，请参阅 Windows SDK 中的[图形对象](/windows/win32/gdi/graphic-objects)。

##  <a name="setbitmapbits"></a>CBitmap：： SetBitmapBits

将位图的位设置为*lpBits*给出的位值。

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>parameters

*dwCount*<br/>
指定*lpBits*指向的字节数。

*lpBits*<br/>
指向包含要复制到 `CBitmap` 对象的像素值的字节数组。 为了使位图能够正确呈现其图像，应将这些值设置为符合在创建 CBitmap 实例时指定的高度、宽度和颜色深度值。 有关详细信息，请参阅[CBitmap：： CreateBitmap](#createbitmap)。

### <a name="return-value"></a>返回值

设置位图位时使用的字节数;如果函数失败，则为0。

##  <a name="setbitmapdimension"></a>CBitmap：： SetBitmapDimension

为位图指定宽度和高度（以0.1 毫米为单位）。

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>parameters

*nWidth*<br/>
指定位图的宽度（以0.1 毫米为单位）。

*nHeight*<br/>
指定位图的高度（以0.1 毫米为单位）。

### <a name="return-value"></a>返回值

先前的位图尺寸。 高度位于 `CSize` 对象的 `cy` 成员变量中，而 width 位于 `cx` 成员变量中。

### <a name="remarks"></a>备注

GDI 不会使用这些值，只是在应用程序调用[GetBitmapDimension](#getbitmapdimension)成员函数时返回这些值。

## <a name="see-also"></a>另请参阅

[MFC 示例 MDI](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 类](../../mfc/reference/cgdiobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
