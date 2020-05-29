---
title: 画笔类
ms.date: 11/04/2016
f1_keywords:
- CBrush
- AFXWIN/CBrush
- AFXWIN/CBrush::CBrush
- AFXWIN/CBrush::CreateBrushIndirect
- AFXWIN/CBrush::CreateDIBPatternBrush
- AFXWIN/CBrush::CreateHatchBrush
- AFXWIN/CBrush::CreatePatternBrush
- AFXWIN/CBrush::CreateSolidBrush
- AFXWIN/CBrush::CreateSysColorBrush
- AFXWIN/CBrush::FromHandle
- AFXWIN/CBrush::GetLogBrush
helpviewer_keywords:
- CBrush [MFC], CBrush
- CBrush [MFC], CreateBrushIndirect
- CBrush [MFC], CreateDIBPatternBrush
- CBrush [MFC], CreateHatchBrush
- CBrush [MFC], CreatePatternBrush
- CBrush [MFC], CreateSolidBrush
- CBrush [MFC], CreateSysColorBrush
- CBrush [MFC], FromHandle
- CBrush [MFC], GetLogBrush
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
ms.openlocfilehash: 15132bb5497886638edfe431ae769dd446785df8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352483"
---
# <a name="cbrush-class"></a>画笔类

封装一个 Windows 图形设备接口 (GDI) 画笔。

## <a name="syntax"></a>语法

```
class CBrush : public CGdiObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[画笔：：CBrush](#cbrush)|构造 `CBrush` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[画笔：：创建画笔间接](#createbrushindirect)|使用[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)结构中指定的样式、颜色和图案初始化画笔。|
|[画笔：：创建DIB模式画笔](#createdibpatternbrush)|使用与设备无关的位图 （DIB） 指定的模式初始化画笔。|
|[画笔：：创建阴影画笔](#createhatchbrush)|使用指定的阴影图案和颜色初始化画笔。|
|[画笔：：创建模式画笔](#createpatternbrush)|使用位图指定的模式初始化画笔。|
|[画笔：：创建实心笔](#createsolidbrush)|使用指定的纯色初始化画笔。|
|[画笔：：创建Sys颜色画笔](#createsyscolorbrush)|创建默认系统颜色的画笔。|
|[画笔：：从手柄](#fromhandle)|为 Windows`HBRUSH`对象`CBrush`指定句柄时，返回指向对象的指针。|
|[画笔：：获取日志画笔](#getlogbrush)|获取[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)结构。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[画笔：：操作员 HBRUSH](#operator_hbrush)|返回附加到`CBrush`对象的 Windows 句柄。|

## <a name="remarks"></a>备注

要使用`CBrush`对象，构造对象`CBrush`并将其传递给需要画笔的任何`CDC`成员函数。

画笔可以是实心的、阴影的或图案的。

有关 的详细信息`CBrush`，请参阅[图形对象](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBrush`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cbrushcbrush"></a><a name="cbrush"></a>画笔：：CBrush

构造 `CBrush` 对象。

```
CBrush();
CBrush(COLORREF crColor);
CBrush(int nIndex, COLORREF crColor);
explicit CBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>参数

*crColor*<br/>
将画笔的前景颜色指定为 RGB 颜色。 如果填充画笔，此参数指定阴影的颜色。

*nIndex*<br/>
指定画笔的填充样式。 它可以是以下任一值：

- HS_BDIAGONAL在 45 度下向下舱口（从左到右）

- HS_CROSS水平和垂直剖面

- HS_DIAGCROSS十字哈奇在 45 度

- HS_FDIAGONAL向上舱口（从左到右）在 45 度

- HS_HORIZONTAL水平舱口

- HS_VERTICAL垂直舱口

*pBitmap*<br/>
指向指定画笔`CBitmap`绘制的位图的对象。

### <a name="remarks"></a>备注

`CBrush`有四个重载构造函数。没有参数的构造函数构造了一个未初始化`CBrush`的对象，该对象必须先初始化才能使用。

如果使用没有参数的构造函数，`CBrush`则必须使用[CreateSolidBrush、CreateHatchBrush、](#createsolidbrush)[创建Brush间接](#createbrushindirect)、[创建模式画笔](#createpatternbrush)或[创建DIBPatternBrush](#createdibpatternbrush)来初始化生成的对象。 [CreateHatchBrush](#createhatchbrush) 如果使用一个采用参数的构造函数，则无需进一步初始化。 如果遇到错误，具有参数的构造函数可以引发异常，而没有参数的构造函数将始终成功。

具有单个[COLORREF](/windows/win32/gdi/colorref)参数的构造函数构造具有指定颜色的实体画笔。 颜色指定 RGB 值，可以使用 WINDOWS 中的 RGB 宏构造。H。

具有两个参数的构造函数构造一个剖面线画笔。 *nIndex*参数指定阴影模式的索引。 *crColor*参数指定颜色。

具有参数的`CBitmap`构造函数构造了模式画笔。 参数标识位图。 假定位图是通过使用[CBitmap：：createBitmap、CBitmap：create](../../mfc/reference/cbitmap-class.md#createbitmap)间接映射[、CBitmap：：：LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)或[CBitmap：：创建兼容位图](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)创建的。 [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect) 在填充图案中使用的位图的最小大小为 8 像素 x 8 像素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]

## <a name="cbrushcreatebrushindirect"></a><a name="createbrushindirect"></a>画笔：：创建画笔间接

使用[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)结构中指定的样式、颜色和图案初始化画笔。

```
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```

### <a name="parameters"></a>参数

*lpLogBrush*<br/>
指向包含有关画笔信息的[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)结构。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

随后，可以选择画笔作为任何设备上下文的当前画笔。

使用单色（1 平面，每像素 1 位）位图创建的画笔使用当前文本和背景颜色绘制。 由位设置为 0 表示的像素将用当前文本颜色绘制。 由设置为 1 的位表示的像素将绘制为当前背景颜色。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]

## <a name="cbrushcreatedibpatternbrush"></a><a name="createdibpatternbrush"></a>画笔：：创建DIB模式画笔

使用与设备无关的位图 （DIB） 指定的模式初始化画笔。

```
BOOL CreateDIBPatternBrush(
    HGLOBAL hPackedDIB,
    UINT nUsage);

BOOL CreateDIBPatternBrush(
    const void* lpPackedDIB,
    UINT nUsage);
```

### <a name="parameters"></a>参数

*h包装DIB*<br/>
标识包含打包的设备无关位图 （DIB） 的全局内存对象。

*n使用*<br/>
指定`bmiColors[]`[BITMAPINFO](/windows/win32/api/wingdi/ns-wingdi-bitmapinfo)数据结构的字段（"打包 DIB"的一部分）是否包含显式 RGB 值或索引到当前已实现的逻辑调色板中。 参数必须是以下值之一：

- DIB_PAL_COLORS 颜色表由 16 位索引组成的数组组成。

- DIB_RGB_COLORS 颜色表包含文本 RGB 值。

*lpPackedDIB*<br/>
指向由`BITMAPINFO`结构组成的打包 DIB，紧接着是定义位图像素的字节数组。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

随后，可以为支持栅格操作的任何设备上下文选择画笔。

这两个版本在处理 DIB 时有所不同：

- 在第一个版本中，要获取 DIB 的句柄，请调用`GlobalAlloc`Windows 函数来分配全局内存块，然后用打包的 DIB 填充内存。

- 在第二个版本中，无需调用`GlobalAlloc`为打包的 DIB 分配内存。

打包的 DIB 由`BITMAPINFO`一个数据结构组成，紧接定义位图像素的字节数组。 用作填充图案的位图应为 8 像素 x 8 像素。 如果位图较大，Windows 仅使用与位图左上角的前 8 行和 8 列像素对应的位创建填充模式。

当应用程序在单色设备上下文中选择双色 DIB 图案画笔时，Windows 会忽略 DIB 中指定的颜色，而是使用设备上下文的当前文本和背景颜色显示图案画笔。 使用文本颜色显示映射到 DIB 的第一种颜色（DIB 颜色表中的偏移 0）的像素。 使用背景颜色显示映射到第二种颜色的像素（在颜色表中的偏移量 1）。

有关使用以下 Windows 功能的信息，请参阅 Windows SDK：

- [CreateDIBPatternBrush（](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrush)此函数仅用于与为 3.0 早于 Windows 版本编写的应用程序兼容而提供;使用`CreateDIBPatternBrushPt`该函数。

- [创建DIBPatternBrushPt（](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrushpt)此功能应用于基于 Win32 的应用程序。

- [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc)

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]

## <a name="cbrushcreatehatchbrush"></a><a name="createhatchbrush"></a>画笔：：创建阴影画笔

使用指定的阴影图案和颜色初始化画笔。

```
BOOL CreateHatchBrush(
    int nIndex,
    COLORREF crColor);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定画笔的填充样式。 它可以是以下任一值：

- HS_BDIAGONAL在 45 度下向下舱口（从左到右）

- HS_CROSS水平和垂直剖面

- HS_DIAGCROSS十字哈奇在 45 度

- HS_FDIAGONAL向上舱口（从左到右）在 45 度

- HS_HORIZONTAL水平舱口

- HS_VERTICAL垂直舱口

*crColor*<br/>
将画笔的前景颜色指定为 RGB 颜色（阴影的颜色）。 有关详细信息，请参阅 Windows SDK 中的[COLORREF。](/windows/win32/gdi/colorref)

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

随后，可以选择画笔作为任何设备上下文的当前画笔。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]

## <a name="cbrushcreatepatternbrush"></a><a name="createpatternbrush"></a>画笔：：创建模式画笔

使用位图指定的模式初始化画笔。

```
BOOL CreatePatternBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>参数

*pBitmap*<br/>
标识位图。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

随后，可以为支持栅格操作的任何设备上下文选择画笔。 *pBitmap*标识的位图通常使用[CBitmap：createBitmap、CBitmap：create](../../mfc/reference/cbitmap-class.md#createbitmap)间接[、CBitmap：：LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)或[CBitmap：create 兼容位图](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)函数进行初始化。 [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)

用作填充图案的位图应为 8 像素 x 8 像素。 如果位图较大，Windows 将仅使用与位图左上角的前 8 行和像素列对应的位。

可以删除模式画笔，而不会影响关联的位图。 这意味着位图可用于创建任意数量的模式画笔。

使用单色位图（1 色平面，每像素 1 位）创建的画笔使用当前文本和背景颜色绘制。 由设置为 0 的位表示的像素使用当前文本颜色绘制。 由设置为 1 的位表示的像素使用当前背景颜色绘制。

有关使用[创建模式画笔](/windows/win32/api/wingdi/nf-wingdi-createpatternbrush)（Windows 函数）的信息，请参阅 Windows SDK。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]

## <a name="cbrushcreatesolidbrush"></a><a name="createsolidbrush"></a>画笔：：创建实心笔

使用指定的纯色初始化画笔。

```
BOOL CreateSolidBrush(COLORREF crColor);
```

### <a name="parameters"></a>参数

*crColor*<br/>
指定画笔颜色的[COLORREF](/windows/win32/gdi/colorref)结构。 颜色指定 RGB 值，可以使用 WINDOWS 中的 RGB 宏构造。H。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

随后，可以选择画笔作为任何设备上下文的当前画笔。

当应用程序使用 创建的`CreateSolidBrush`画笔完成时，它应从设备上下文中选择画笔。

### <a name="example"></a>示例

  请参阅[CBrush 的示例：：CBrush](#cbrush)。

## <a name="cbrushcreatesyscolorbrush"></a><a name="createsyscolorbrush"></a>画笔：：创建Sys颜色画笔

初始化画笔颜色。

```
BOOL CreateSysColorBrush(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定颜色索引。 此值对应于用于绘制 21 个窗口元素之一的颜色。 有关值列表，请参阅 Windows SDK 中的[GetSysColor。](/windows/win32/api/winuser/nf-winuser-getsyscolor)

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

随后，可以选择画笔作为任何设备上下文的当前画笔。

当应用程序使用 创建的`CreateSysColorBrush`画笔完成时，它应从设备上下文中选择画笔。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]

## <a name="cbrushfromhandle"></a><a name="fromhandle"></a>画笔：：从手柄

当为 Windows `CBrush` [HBRUSH](#operator_hbrush)对象的句柄指定时，返回指向对象的指针。

```
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```

### <a name="parameters"></a>参数

*hBrush*<br/>
处理到 Windows GDI 画笔。

### <a name="return-value"></a>返回值

指向`CBrush`对象的指针（如果成功）;如果成功，则指向对象。否则 NULL。

### <a name="remarks"></a>备注

如果对象`CBrush`尚未附加到句柄，则创建并附加临时`CBrush`对象。 此临时`CBrush`对象仅在下次应用程序在其事件循环中有空闲时间之前才有效。 此时，将删除所有临时图形对象。 换句话说，临时对象仅在处理一个窗口消息期间有效。

有关使用图形对象的详细信息，请参阅 Windows SDK 中的[图形对象](/windows/win32/gdi/graphic-objects)。

### <a name="example"></a>示例

  请参阅[CBrush 的示例：：CBrush](#cbrush)。

## <a name="cbrushgetlogbrush"></a><a name="getlogbrush"></a>画笔：：获取日志画笔

调用此成员函数以检索`LOGBRUSH`结构。

```
int GetLogBrush(LOGBRUSH* pLogBrush);
```

### <a name="parameters"></a>参数

*pLogBrush*<br/>
指向包含有关画笔信息的[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)结构。

### <a name="return-value"></a>返回值

如果函数成功，并且*pLogBrush*是有效的指针，则返回值是存储在缓冲区中的字节数。

如果函数成功，并且*pLogBrush*为 NULL，则返回值是保存函数将存储到缓冲区中的信息所需的字节数。

如果函数失败，则返回值为 0。

### <a name="remarks"></a>备注

结构`LOGBRUSH`定义画笔的风格、颜色和图案。

例如，调用`GetLogBrush`以匹配位图的特定颜色或模式。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]

## <a name="cbrushoperator-hbrush"></a><a name="operator_hbrush"></a>画笔：：操作员 HBRUSH

使用此运算符获取`CBrush`对象的附加 Windows GDI 句柄。

```
operator HBRUSH() const;
```

### <a name="return-value"></a>返回值

如果成功，则对对象表示的 Windows GDI`CBrush`对象的句柄;如果成功，则对对象表示的 Windows GDI 对象的句柄。否则 NULL。

### <a name="remarks"></a>备注

此运算符是强制转换运算符，支持直接使用 HBRUSH 对象。

有关使用图形对象的详细信息，请参阅 Windows SDK 中的[图形对象](/windows/win32/gdi/graphic-objects)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 类](../../mfc/reference/cgdiobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CBitmap 类](../../mfc/reference/cbitmap-class.md)<br/>
[CDC 类](../../mfc/reference/cdc-class.md)
