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
ms.openlocfilehash: 11e210680bdf68f1a1dcbfaed18ae56ce006c8ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388444"
---
# <a name="cbitmap-class"></a>CBitmap 类

封装一个 Windows 图形设备接口 (GDI) 位图并提供成员函数以操作位图。

## <a name="syntax"></a>语法

```
class CBitmap : public CGdiObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CBitmap::CBitmap](#cbitmap)|构造 `CBitmap` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CBitmap::CreateBitmap](#createbitmap)|初始化具有指定的宽度、 高度和位模式的设备相关的内存位图对象。|
|[CBitmap::CreateBitmapIndirect](#createbitmapindirect)|初始化与位图的宽度、 高度和位模式 （如果已指定） 中提供的对象`BITMAP`结构。|
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|初始化与位图对象，以便它与指定的设备兼容。|
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|初始化与指定的设备兼容的可放弃位图对象。|
|[CBitmap::FromHandle](#fromhandle)|返回一个指向`CBitmap`对象时提供给 Windows 的一个句柄`HBITMAP`位图。|
|[CBitmap::GetBitmap](#getbitmap)|填充`BITMAP`位图有关的信息的结构。|
|[CBitmap::GetBitmapBits](#getbitmapbits)|将指定的位图的位复制到指定的缓冲区。|
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|返回的宽度和位图的高度。 被假定已由以前设置的高度和宽度[SetBitmapDimension](#setbitmapdimension)成员函数。|
|[CBitmap::LoadBitmap](#loadbitmap)|从应用程序的可执行文件加载命名的位图资源并附加到对象的位图初始化的对象。|
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|加载位图并映射到当前的系统颜色的颜色。|
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|正在加载预定义的 Windows 位图将位图附加到对象来初始化对象。|
|[CBitmap::SetBitmapBits](#setbitmapbits)|将位图的位设置为指定的位值。|
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|将分配给 0.1 毫米为单位中的位图的宽度和高度。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CBitmap::operator HBITMAP](#operator_hbitmap)|返回附加到的 Windows 句柄`CBitmap`对象。|

## <a name="remarks"></a>备注

若要使用`CBitmap`对象、 构造对象、 将位图句柄附加到其中一个成员函数的初始化，它，然后调用对象的成员函数。

有关详细信息使用图形对象，如`CBitmap`，请参阅[图形对象](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBitmap`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cbitmap"></a>  CBitmap::CBitmap

构造 `CBitmap` 对象。

```
CBitmap();
```

### <a name="remarks"></a>备注

必须使用一个成员函数的初始化初始化生成的对象。

##  <a name="createbitmap"></a>  CBitmap::CreateBitmap

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

*nWidth*<br/>
指定位图的宽度（以像素为单位）。

*nHeight*<br/>
指定位图的高度（以像素为单位）。

*nPlanes*<br/>
指定位图中的颜色平面的数量。

*nBitcount*<br/>
指定每个显示像素的颜色位的数量。

*lpBits*<br/>
指向包含的初始位图位值的字节的数组。 如果它为 NULL，新位图则未初始化。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

对于颜色位图，任一*nPlanes*或*nBitcount*参数应设置为 1。 如果这些参数均设为 1， `CreateBitmap` 则会创建一个单色位图。

尽管无法为显示设备直接选择位图，但可以使用 [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) 选择将它作为“内存设备上下文”的当前位图，并使用 [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) 函数将其复制到任何兼容的设备上下文中。

完成通过 `CBitmap` 函数创建的 `CreateBitmap` 对象后，首先选择设备上下文中的位图，然后删除 `CBitmap` 对象。

有关详细信息，请参阅的说明`bmBits`字段中`BITMAP`结构。 [BITMAP](/windows/desktop/api/wingdi/ns-wingdi-tagbitmap) 结构根据 [CBitmap::CreateBitmapIndirect](#createbitmapindirect) 成员函数进行说明。

##  <a name="createbitmapindirect"></a>  CBitmap::CreateBitmapIndirect

初始化具有宽度、 高度和通过指向的结构中给出的位模式 （如果已指定） 的位图*lpBitmap*。

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>参数

*lpBitmap*<br/>
指向[位图](/windows/desktop/api/wingdi/ns-wingdi-tagbitmap)结构，其中包含有关位图的信息。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

尽管不能为显示设备直接选择位图，但它可以选择作为内存设备上下文的当前位图使用[cdc:: selectobject](../../mfc/reference/cdc-class.md#selectobject)和复制到任何兼容的设备上下文的使用[Cdc:: bitblt](../../mfc/reference/cdc-class.md#bitblt)或[CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt)函数。 ( [CDC::PatBlt](../../mfc/reference/cdc-class.md#patblt)函数可以将当前画笔的位图复制直接到显示设备上下文。)

如果`BITMAP`指向结构*lpBitmap*使用已填写参数`GetObject`函数中，未指定位图的位和位图未初始化。 若要初始化位图，应用程序可以使用一个函数如[cdc:: bitblt](../../mfc/reference/cdc-class.md#bitblt)或[SetDIBits](/windows/desktop/api/wingdi/nf-wingdi-setdibits)若要将位数复制中的第一个参数所标识的位图`CGdiObject::GetObject`到创建的位图`CreateBitmapIndirect`.

完成通过`CBitmap`使用创建的对象`CreateBitmapIndirect`函数，首先选择设备上下文中的位图，然后删除`CBitmap`对象。

##  <a name="createcompatiblebitmap"></a>  CBitmap::CreateCompatibleBitmap

初始化与指定的设备兼容的位图*pDC*。

```
BOOL CreateCompatibleBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指定设备上下文。

*nWidth*<br/>
指定位图的宽度（以像素为单位）。

*nHeight*<br/>
指定位图的高度（以像素为单位）。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

位图有相同数量的颜色平面或与指定的设备上下文相同的位每像素格式。 它可以选择作为符合指定的任何内存设备的当前位图*pDC*。

如果*pDC*是内存设备上下文，返回该位图在该设备上下文中具有相同的格式为当前所选的位图。 "内存设备上下文"是内存的表示显示图面块。 它可以用于准备在内存中的映像，然后将其复制到兼容的设备的实际显示图面。

创建内存设备上下文，GDI 将自动为其选择股票的单色位图。

由于颜色内存设备上下文可以具有颜色或所选的单色位图，位图的格式返回的`CreateCompatibleBitmap`函数并不总是相同; 但是，无内存设备上下文的兼容位图的格式是始终在设备的格式。

完成通过`CBitmap`使用创建的对象`CreateCompatibleBitmap`函数，首先选择设备上下文中的位图，然后删除`CBitmap`对象。

##  <a name="creatediscardablebitmap"></a>  CBitmap::CreateDiscardableBitmap

初始化由标识的设备上下文与兼容的可放弃位图*pDC*。

```
BOOL CreateDiscardableBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指定设备上下文。

*nWidth*<br/>
指定位图的宽度 （以位为单位）。

*nHeight*<br/>
指定位图的高度 （以位为单位）。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

位图有相同数量的颜色平面或与指定的设备上下文相同的位每像素格式。 应用程序可以选择将该位图作为符合指定的内存设备的当前位图*pDC*。

Windows 可以放弃创建此函数，仅当应用程序尚未选择它显示上下文的位图。 如果 Windows 时未选择和更高版本的应用程序尝试以选中它，将放弃位图[cdc:: selectobject](../../mfc/reference/cdc-class.md#selectobject)函数将返回 NULL。

完成通过`CBitmap`使用创建的对象`CreateDiscardableBitmap`函数，首先选择设备上下文中的位图，然后删除`CBitmap`对象。

##  <a name="fromhandle"></a>  CBitmap::FromHandle

返回一个指向`CBitmap`对象时提供给 Windows GDI 位图的句柄。

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>参数

*hBitmap*<br/>
指定 Windows GDI 位图。

### <a name="return-value"></a>返回值

一个指向`CBitmap`如果成功，否则该值为 NULL 的对象。

### <a name="remarks"></a>备注

如果`CBitmap`对象尚未附加到句柄，临时`CBitmap`创建并附加对象。 此临时`CBitmap`对象仅用于有效直到下一次应用程序在其事件循环内有空闲时间，在该时间所有临时图形对象会被删除。 另一种说法： 这是一个窗口消息处理过程才有效的临时对象。

##  <a name="getbitmap"></a>  CBitmap::GetBitmap

检索附加位图图像属性。

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>参数

*pBitMap*<br/>
指向[位图](/windows/desktop/api/wingdi/ns-wingdi-tagbitmap)结构，它将接收映像属性。 此参数不能为 NULL。

### <a name="return-value"></a>返回值

如果此方法已成功，则非零值否则为 0。

### <a name="remarks"></a>备注

##  <a name="getbitmapbits"></a>  CBitmap::GetBitmapBits

将附加的位图的位模式复制到指定的缓冲区。

```
DWORD GetBitmapBits(
    DWORD dwCount,
    LPVOID lpBits) const;
```

### <a name="parameters"></a>参数

*dwCount*<br/>
要复制到缓冲区的字节数。

*lpBits*<br/>
指向将接收该位图的缓冲区的指针。

### <a name="return-value"></a>返回值

如果此方法已成功，则将复制到缓冲区的字节数否则为 0。

### <a name="remarks"></a>备注

使用[CBitmap::GetBitmap](#getbitmap)来确定所需的缓冲区大小。

##  <a name="getbitmapdimension"></a>  CBitmap::GetBitmapDimension

返回的宽度和位图的高度。

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>返回值

宽度和高度的位图，以 0.1 毫米为单位。 高度处于`cy`的成员`CSize`对象，并且宽度是在`cx`成员。 如果位图宽度和高度不使用已设置`SetBitmapDimension`，返回值为 0。

### <a name="remarks"></a>备注

被假定已通过使用以前设置的高度和宽度[SetBitmapDimension](#setbitmapdimension)成员函数。

##  <a name="loadbitmap"></a>  CBitmap::LoadBitmap

加载命名的位图资源*lpszResourceName*或者识别出的 ID 号*nIDResource*从应用程序的可执行文件。

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>参数

*lpszResourceName*<br/>
指向包含位图资源的名称的以 null 结尾的字符串。

*nIDResource*<br/>
指定位图资源的资源 ID 号。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

加载的位图附加到`CBitmap`对象。

如果由标识位图*lpszResourceName*不存在或是否存在内存不足，无法加载位图，该函数返回 0。

可以使用[CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)函数来删除位图加载`LoadBitmap`函数，或`CBitmap`析构函数将为你删除对象。

> [!CAUTION]
>  删除对象之前，请确保它不选入设备上下文。

Windows 版本 3.1 和更高版本中添加以下位图：

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

3.0 版及更早版本的 Windows 版本的设备驱动程序中不存在这些位图。 位图和显示的顺序的显示的完整列表，请参阅 Windows SDK。

##  <a name="loadmappedbitmap"></a>  CBitmap::LoadMappedBitmap

调用此成员函数以加载位图并映射到当前的系统颜色的颜色。

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
位图的标志。 可以为零或 CMB_MASKED。

*lpColorMap*<br/>
一个指向`COLORMAP`结构，其中包含所需映射位图的颜色信息。 如果此参数为 NULL，则该函数使用默认的颜色映射。

*nMapSize*<br/>
指向数量的颜色映射*lpColorMap*。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

默认情况下，`LoadMappedBitmap`将映射按钮标志符号中常用的颜色。

有关创建映射的位图的信息，请参阅 Windows 函数[CreateMappedBitmap](http://go.microsoft.com/fwlink/p/?linkid=230562)并[颜色映射](/windows/desktop/api/commctrl/ns-commctrl-_colormap)Windows SDK 中的结构。

##  <a name="loadoembitmap"></a>  CBitmap::LoadOEMBitmap

加载 Windows 所使用的预定义的位图。

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>参数

*nIDBitmap*<br/>
预定义的 Windows 位图的 ID 号。 从 WINDOWS 下面列出可能的值。H:

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

位图名称开头 OBM_OLD 表示使用 3.0 之前的 Windows 版本的位图。

请注意，必须在包含 WINDOWS 之前定义常量 OEMRESOURCE。若要使用的任何 H **OBM_** 常量。

##  <a name="operator_hbitmap"></a>  CBitmap::operator HBITMAP

此运算符用于获取附加的 Windows GDI 句柄的`CBitmap`对象。

```
operator HBITMAP() const;
```

### <a name="return-value"></a>返回值

如果成功，Windows GDI 对象的句柄由`CBitmap`对象; 否则为 NULL。

### <a name="remarks"></a>备注

此运算符是强制转换运算符，支持直接使用`HBITMAP`对象。

有关使用图形对象的详细信息，请参阅[图形对象](/windows/desktop/gdi/graphic-objects)Windows SDK 中。

##  <a name="setbitmapbits"></a>  CBitmap::SetBitmapBits

将位图的位设置为给定的位值*lpBits*。

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>参数

*dwCount*<br/>
指定指向的字节数*lpBits*。

*lpBits*<br/>
指向包含要复制到的像素值的字节数组`CBitmap`对象。 为了使要将无法正确呈现其图像的位图，值应进行格式设置为与创建 CBitmap 实例时指定的高度、 宽度和颜色深度值。 有关详细信息，请参阅[CBitmap::CreateBitmap](#createbitmap)。

### <a name="return-value"></a>返回值

将位图位; 设置中使用的字节数如果函数失败，则为 0。

##  <a name="setbitmapdimension"></a>  CBitmap::SetBitmapDimension

将分配给 0.1 毫米为单位中的位图的宽度和高度。

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>参数

*nWidth*<br/>
指定 （以 0.1 毫米为单位） 位图的宽度。

*nHeight*<br/>
指定的高度 （以 0.1 毫米为单位） 的位图。

### <a name="return-value"></a>返回值

以前的位图尺寸。 高度处于`cy`成员变量`CSize`对象，并且宽度是在`cx`成员变量。

### <a name="remarks"></a>备注

GDI 不使用这些值，但若要返回其应用程序调用时除外[GetBitmapDimension](#getbitmapdimension)成员函数。

## <a name="see-also"></a>请参阅

[MFC 示例 MDI](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 类](../../mfc/reference/cgdiobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
