---
title: CBrush 类
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
ms.openlocfilehash: f2a2e385a9f210b3644d7fade00b72c4befa47ef
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "58778866"
---
# <a name="cbrush-class"></a>CBrush 类

封装一个 Windows 图形设备接口 (GDI) 画笔。

## <a name="syntax"></a>语法

```
class CBrush : public CGdiObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CBrush::CBrush](#cbrush)|构造 `CBrush` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CBrush::CreateBrushIndirect](#createbrushindirect)|初始化具有样式、 颜色和模式中指定的画笔[LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush)结构。|
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|初始化具有指定的与设备无关位图 (DIB) 模式的画笔。|
|[CBrush::CreateHatchBrush](#createhatchbrush)|初始化具有指定阴影的模式和颜色的画笔。|
|[CBrush::CreatePatternBrush](#createpatternbrush)|初始化具有指定的位图模式的画笔。|
|[CBrush::CreateSolidBrush](#createsolidbrush)|初始化具有指定纯色画笔。|
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|创建为默认系统颜色的画笔。|
|[CBrush::FromHandle](#fromhandle)|返回一个指向`CBrush`对象时提供给 Windows 的一个句柄`HBRUSH`对象。|
|[CBrush::GetLogBrush](#getlogbrush)|获取[LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush)结构。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CBrush::operator HBRUSH](#operator_hbrush)|返回附加到的 Windows 句柄`CBrush`对象。|

## <a name="remarks"></a>备注

若要使用`CBrush`对象，构造`CBrush`对象，并将其传递给任何`CDC`需要画笔的成员函数。

画笔可以 solid，影线，或图案。

有关详细信息`CBrush`，请参阅[图形对象](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBrush`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cbrush"></a>  CBrush::CBrush

构造 `CBrush` 对象。

```
CBrush();
CBrush(COLORREF crColor);
CBrush(int nIndex, COLORREF crColor);
explicit CBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>参数

*crColor*<br/>
指定为 RGB 颜色的前景色的画笔。 如果影线画笔，则此参数指定阴影的颜色。

*nIndex*<br/>
指定画笔的阴影样式。 它可以是以下值之一：

- 45 度的位置 （从左到右） 的向下 HS_BDIAGONAL 阴影

- HS_CROSS 水平和垂直交叉影线

- HS_DIAGCROSS 交叉影线 45 度

- 向上 HS_FDIAGONAL 阴影 （从左到右） 45 度的位置

- HS_HORIZONTAL 水平阴影

- HS_VERTICAL 垂直阴影

*pBitmap*<br/>
指向`CBitmap`对象，它指定与画笔绘制的位图。

### <a name="remarks"></a>备注

`CBrush` 有四个重载的构造函数。不带任何参数的构造函数构造未经初始化即`CBrush`可以使用它之前，必须初始化的对象。

如果你使用不带任何参数的构造函数，则必须初始化生成`CBrush`对象使用[CreateSolidBrush](#createsolidbrush)， [CreateHatchBrush](#createhatchbrush)， [CreateBrushIndirect](#createbrushindirect)， [CreatePatternBrush](#createpatternbrush)，或[CreateDIBPatternBrush](#createdibpatternbrush)。 如果你使用采用参数的构造函数之一，则无需再初始化是所必需。 如果遇到错误，而不带任何参数的构造函数将始终成功，则使用参数的构造函数可以引发异常。

使用单个构造函数[COLORREF](/windows/desktop/gdi/colorref)参数构造具有指定颜色的实心画笔。 颜色指定 RGB 值，并可以构造与 WINDOWS 中的 RGB 宏。H.

具有两个参数的构造函数构造阴影画笔。 *NIndex*参数指定的索引的阴影模式。 *CrColor*参数指定的颜色。

使用构造函数`CBitmap`参数构造模式的画笔。 此参数用于标识位图。 假定已使用已创建位图[CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap)， [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)， [cbitmap:: Loadbitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)，或[CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)。 要填充模式中使用的位图的最小大小是 8 x 8 像素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]

##  <a name="createbrushindirect"></a>  CBrush::CreateBrushIndirect

初始化具有样式、 颜色和模式中指定的画笔[LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush)结构。

```
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```

### <a name="parameters"></a>参数

*lpLogBrush*<br/>
指向[LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush)结构，其中包含有关画笔的信息。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

随后可以为任何设备上下文的当前画笔选择画笔。

使用当前的文本和背景色绘制字符使用 （1 平面，每像素 1 位） 的单色位图创建的画笔。 将使用当前的文本颜色绘制像素为单位表示的位设置为 0。 将使用当前的背景色绘制像素位设置为 1 表示。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]

##  <a name="createdibpatternbrush"></a>  CBrush::CreateDIBPatternBrush

使用画笔初始化与设备无关位图 (DIB) 指定的模式。

```
BOOL CreateDIBPatternBrush(
    HGLOBAL hPackedDIB,
    UINT nUsage);

BOOL CreateDIBPatternBrush(
    const void* lpPackedDIB,
    UINT nUsage);
```

### <a name="parameters"></a>参数

*hPackedDIB*<br/>
标识包含已打包的设备无关位图 (DIB) 的全局内存对象。

*nUsage*<br/>
指定是否`bmiColors[]`的字段[BITMAPINFO](/windows/desktop/api/wingdi/ns-wingdi-tagbitmapinfo)数据结构 （"打包 DIB"的一部分） 包含显式的 RGB 值或索引的当前实现逻辑调色板。 参数必须为下列值之一：

- DIB_PAL_COLORS 颜色表包含 16 位索引的数组。

- DIB_RGB_COLORS 颜色表包含文本的 RGB 值。

*lpPackedDIB*<br/>
指向包含的已打包 DIB`BITMAPINFO`紧随其后的定义位图的像素的字节数组的结构。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

随后可以为任何支持光栅操作的设备上下文选择画笔。

两个版本的不同处理 DIB 的方法：

- 在第一个版本中，若要获取的句柄 DIB 你调用 Windows`GlobalAlloc`函数分配的全局内存块，然后打包 DIB 并用来填充内存。

- 在第二个版本中，它不需要调用`GlobalAlloc`分配内存来存放已打包 DIB。

已打包的 DIB 组成`BITMAPINFO`紧随其后定义位图的像素的字节数组的数据结构。 位图作为填充模式应为 8 x 8 像素。 如果位图大小，Windows 将创建使用仅为前 8 行和 8 个列的左上角的位图的像素对应的位的填充模式。

当应用程序到单色设备上下文选择两种颜色 DIB 模式画笔时，Windows 将忽略 DIB 中指定的颜色，并改为显示模式画笔使用设备上下文的当前文本和背景颜色。 使用的文本颜色显示像素映射到的 DIB （按 DIB 颜色表中的偏移量 0） 的第一个颜色。 使用背景色显示映射到 （以颜色表中的偏移量 1） 的第二个颜色的像素为单位。

有关使用以下 Windows 功能的信息，请参阅 Windows SDK:

- [CreateDIBPatternBrush](/windows/desktop/api/wingdi/nf-wingdi-createdibpatternbrush) (此函数仅用于与 Windows 的版本早于 3.0 编写的应用程序兼容性; 使用`CreateDIBPatternBrushPt`函数。)

- [CreateDIBPatternBrushPt](/windows/desktop/api/wingdi/nf-wingdi-createdibpatternbrushpt) （此函数应基于 Win32 的应用程序。）

- [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc)

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]

##  <a name="createhatchbrush"></a>  CBrush::CreateHatchBrush

初始化具有指定阴影的模式和颜色的画笔。

```
BOOL CreateHatchBrush(
    int nIndex,
    COLORREF crColor);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定画笔的阴影样式。 它可以是以下值之一：

- 45 度的位置 （从左到右） 的向下 HS_BDIAGONAL 阴影

- HS_CROSS 水平和垂直交叉影线

- HS_DIAGCROSS 交叉影线 45 度

- 向上 HS_FDIAGONAL 阴影 （从左到右） 45 度的位置

- HS_HORIZONTAL 水平阴影

- HS_VERTICAL 垂直阴影

*crColor*<br/>
指定为的 RGB 颜色 （阴影的颜色） 的前景色的画笔。 请参阅[COLORREF](/windows/desktop/gdi/colorref) Windows SDK for 的详细信息中。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

随后可以为任何设备上下文的当前画笔选择画笔。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]

##  <a name="createpatternbrush"></a>  CBrush::CreatePatternBrush

初始化具有指定的位图模式的画笔。

```
BOOL CreatePatternBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>参数

*pBitmap*<br/>
标识一个位图。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

随后可以为任何支持光栅操作的设备上下文选择画笔。 由标识位图*pBitmap*通常使用初始化[CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap)， [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)， [CBitmap::LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)，或[CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)函数。

位图作为填充模式应为 8 x 8 像素。 如果位图大小，Windows 将只使用对应的前 8 行和列的左上角的位图的像素的位。

模式画笔可以删除而不会影响相关联的位图。 这意味着位图可用于创建任意数量的模式的画笔。

使用单色位图 （每像素 1 位 1 平面） 创建一个画笔是使用当前的文本和背景色绘制字符。 使用当前的文本颜色绘制像素位设置为 0 表示。 使用当前的背景色绘制像素为单位表示的位设置为 1。

有关使用信息[CreatePatternBrush](/windows/desktop/api/wingdi/nf-wingdi-createpatternbrush)，Windows 函数中，请参阅 Windows SDK。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]

##  <a name="createsolidbrush"></a>  CBrush::CreateSolidBrush

初始化使用指定纯色画笔。

```
BOOL CreateSolidBrush(COLORREF crColor);
```

### <a name="parameters"></a>参数

*crColor*<br/>
一个[COLORREF](/windows/desktop/gdi/colorref)结构，它指定画笔的颜色。 颜色指定 RGB 值，并可以构造与 WINDOWS 中的 RGB 宏。H.

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

随后可以为任何设备上下文的当前画笔选择画笔。

当应用程序已完成使用创建的画笔`CreateSolidBrush`，应已选择不在设备上下文画笔。

### <a name="example"></a>示例

  有关示例，请参阅[CBrush::CBrush](#cbrush)。

##  <a name="createsyscolorbrush"></a>  CBrush::CreateSysColorBrush

初始化画笔颜色。

```
BOOL CreateSysColorBrush(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
指定颜色索引。 此值对应于用来绘制一个 21 窗口元素的颜色。 请参阅[GetSysColor](/windows/desktop/api/winuser/nf-winuser-getsyscolor) Windows SDK for 值的列表中。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

随后可以为任何设备上下文的当前画笔选择画笔。

当应用程序已完成使用创建的画笔`CreateSysColorBrush`，应已选择不在设备上下文画笔。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]

##  <a name="fromhandle"></a>  CBrush::FromHandle

返回一个指向`CBrush`对象时提供给 Windows 的一个句柄[HBRUSH](#operator_hbrush)对象。

```
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```

### <a name="parameters"></a>参数

*hBrush*<br/>
Windows GDI 画笔的句柄。

### <a name="return-value"></a>返回值

一个指向`CBrush`如果成功，否则该值为 NULL 的对象。

### <a name="remarks"></a>备注

如果`CBrush`对象尚未附加到句柄，临时`CBrush`创建并附加对象。 此临时`CBrush`对象仅在应用程序必须在其事件循环内的空闲时间的下一步时间前是否有效。 在此期间，会删除所有临时图形对象。 换而言之，仅在一个窗口消息处理期间的临时对象有效。

有关使用图形对象的详细信息，请参阅[图形对象](/windows/desktop/gdi/graphic-objects)Windows SDK 中。

### <a name="example"></a>示例

  有关示例，请参阅[CBrush::CBrush](#cbrush)。

##  <a name="getlogbrush"></a>  CBrush::GetLogBrush

调用此成员函数以检索`LOGBRUSH`结构。

```
int GetLogBrush(LOGBRUSH* pLogBrush);
```

### <a name="parameters"></a>参数

*pLogBrush*<br/>
指向[LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush)结构，其中包含有关画笔的信息。

### <a name="return-value"></a>返回值

如果函数成功，并*pLogBrush*是有效的指针，返回值是存储到缓冲区的字节数。

如果函数成功，并*pLogBrush*为 NULL，则返回值是保存该函数的信息所需的字节数将存储到缓冲区。

如果函数失败，返回值为 0。

### <a name="remarks"></a>备注

`LOGBRUSH`结构定义样式、 颜色和画笔的模式。

例如，调用`GetLogBrush`以匹配的特定颜色或图案的位图。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]

##  <a name="operator_hbrush"></a>  CBrush::operator HBRUSH

此运算符用于获取附加的 Windows GDI 句柄的`CBrush`对象。

```
operator HBRUSH() const;
```

### <a name="return-value"></a>返回值

如果成功，Windows GDI 对象的句柄由`CBrush`对象; 否则为 NULL。

### <a name="remarks"></a>备注

此运算符是强制转换运算符，支持直接使用 HBRUSH 对象。

有关使用图形对象的详细信息，请参阅[图形对象](/windows/desktop/gdi/graphic-objects)Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 类](../../mfc/reference/cgdiobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CBitmap 类](../../mfc/reference/cbitmap-class.md)<br/>
[CDC 类](../../mfc/reference/cdc-class.md)
