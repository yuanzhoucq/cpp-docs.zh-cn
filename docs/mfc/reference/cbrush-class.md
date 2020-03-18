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
ms.openlocfilehash: a99d8c8022d23f627320b66c3f376be803c9c839
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426011"
---
# <a name="cbrush-class"></a>CBrush 类

封装一个 Windows 图形设备接口 (GDI) 画笔。

## <a name="syntax"></a>语法

```
class CBrush : public CGdiObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CBrush：： CBrush](#cbrush)|构造 `CBrush` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CBrush：： CreateBrushIndirect](#createbrushindirect)|使用在[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)结构中指定的样式、颜色和模式初始化画笔。|
|[CBrush：： CreateDIBPatternBrush](#createdibpatternbrush)|使用由与设备无关的位图（DIB）指定的模式初始化画笔。|
|[CBrush：： CreateHatchBrush](#createhatchbrush)|使用指定的阴影模式和颜色初始化画笔。|
|[CBrush：： CreatePatternBrush](#createpatternbrush)|使用位图指定的模式初始化画笔。|
|[CBrush：： CreateSolidBrush](#createsolidbrush)|使用指定的纯色初始化画笔。|
|[CBrush：： CreateSysColorBrush](#createsyscolorbrush)|创建作为默认系统颜色的画笔。|
|[CBrush：： FromHandle](#fromhandle)|给定 Windows `HBRUSH` 对象的句柄时，返回指向 `CBrush` 对象的指针。|
|[CBrush：： GetLogBrush](#getlogbrush)|获取[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)结构。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[CBrush：： operator HBRUSH](#operator_hbrush)|返回附加到 `CBrush` 对象的 Windows 句柄。|

## <a name="remarks"></a>备注

若要使用 `CBrush` 对象，请构造一个 `CBrush` 对象并将其传递给任何需要使用画笔的 `CDC` 成员函数。

画笔可以为纯色、阴影线或图案。

有关 `CBrush`的详细信息，请参阅[图形对象](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBrush`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cbrush"></a>CBrush：： CBrush

构造 `CBrush` 对象。

```
CBrush();
CBrush(COLORREF crColor);
CBrush(int nIndex, COLORREF crColor);
explicit CBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>parameters

*crColor*<br/>
指定画笔的前景色作为 RGB 颜色。 如果画笔为影线，则此参数指定阴影的颜色。

*nIndex*<br/>
指定画笔的阴影样式。 它可以是下列值之一：

- 从45度 HS_BDIAGONAL 向下影线（从左到右）

- HS_CROSS 水平和垂直交叉影线

- 45度 HS_DIAGCROSS 交叉影线

- HS_FDIAGONAL 向上影线（从左到右），45度

- HS_HORIZONTAL 水平影线

- HS_VERTICAL 垂直影线

*pBitmap*<br/>
指向一个 `CBitmap` 对象，该对象指定画笔绘制的位图。

### <a name="remarks"></a>备注

`CBrush` 具有四个重载构造函数。不带参数的构造函数将构造一个未初始化的 `CBrush` 对象，该对象在使用之前必须进行初始化。

如果使用不带参数的构造函数，则必须用[CreateSolidBrush](#createsolidbrush)、 [CreateHatchBrush](#createhatchbrush)、 [CreateBrushIndirect](#createbrushindirect)、 [CreatePatternBrush](#createpatternbrush)或[CreateDIBPatternBrush](#createdibpatternbrush)初始化生成的 `CBrush` 对象。 如果使用采用参数的构造函数之一，则无需进行进一步的初始化。 如果遇到错误，带参数的构造函数可能会引发异常，而不带参数的构造函数将始终会成功。

具有单个[COLORREF](/windows/win32/gdi/colorref)参数的构造函数使用指定的颜色构造纯色画笔。 颜色指定一个 RGB 值，并且可以使用 WINDOWS 中的 RGB 宏来构造。高.

具有两个参数的构造函数构造一个阴影画笔。 *NIndex*参数指定阴影模式的索引。 *CrColor*参数指定颜色。

具有 `CBitmap` 参数的构造函数将构造一个图案画笔。 参数用于标识位图。 假定已通过使用[CBitmap：： CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap)、 [CBitmap：： CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)、 [CBitmap：： LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)或[CBitmap：： CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)创建了该位图。 填充模式中要使用的位图的最小大小为 8 x 8 像素。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]

##  <a name="createbrushindirect"></a>CBrush：： CreateBrushIndirect

使用在[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)结构中指定的样式、颜色和模式初始化画笔。

```
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```

### <a name="parameters"></a>parameters

*lpLogBrush*<br/>
指向包含有关画笔的信息的[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)结构。

### <a name="return-value"></a>返回值

如果该函数成功，则为非 0；否则为 0。

### <a name="remarks"></a>备注

然后，可以选择该画笔作为任何设备上下文的当前画笔。

使用单色（1平面，1位/像素）位图创建的画笔使用当前文本和背景颜色绘制。 设置为0的位所表示的像素将用当前文本颜色绘制。 设置为1的位设置为1的像素将用当前背景颜色绘制。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]

##  <a name="createdibpatternbrush"></a>CBrush：： CreateDIBPatternBrush

使用与设备无关的位图（DIB）指定的模式初始化画笔。

```
BOOL CreateDIBPatternBrush(
    HGLOBAL hPackedDIB,
    UINT nUsage);

BOOL CreateDIBPatternBrush(
    const void* lpPackedDIB,
    UINT nUsage);
```

### <a name="parameters"></a>parameters

*hPackedDIB*<br/>
标识包含打包的与设备无关的位图（DIB）的全局内存对象。

*nUsage*<br/>
指定[BITMAPINFO](/windows/win32/api/wingdi/ns-wingdi-bitmapinfo)数据结构的 `bmiColors[]` 字段（"打包的 DIB" 的一部分）是否在当前已实现的逻辑调色板中包含显式 RGB 值或索引。 参数必须是下列值之一：

- DIB_PAL_COLORS 颜色表包含16位索引的数组。

- DIB_RGB_COLORS color 表包含原义文本值。

*lpPackedDIB*<br/>
指向打包的 DIB，其中包含一个 `BITMAPINFO` 结构，后跟一个定义位图像素的字节数组。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

然后，可以为支持光栅操作的任何设备上下文选择画笔。

这两个版本在处理 DIB 的方式上有所不同：

- 在第一个版本中，若要获取 DIB 的句柄，请调用 Windows `GlobalAlloc` 函数分配全局内存块，然后使用打包的 DIB 填充内存。

- 在第二个版本中，无需调用 `GlobalAlloc` 为打包的 DIB 分配内存。

打包的 DIB 包含一个 `BITMAPINFO` 数据结构，该结构后跟定义位图像素的字节数组。 用作填充图案的位图的像素应为8像素。 如果位图更大，则 Windows 只使用对应于位图左上角的前8行和8列像素的位创建填充模式。

当应用程序在单色设备上下文中选择双色 DIB 模式画笔时，Windows 将忽略 DIB 中指定的颜色，而是使用设备上下文的当前文本和背景色显示模式画笔。 映射到 DIB 的第一种颜色（在 DIB 颜色表中为偏移量0）的像素使用文本颜色显示。 映射到第二种颜色（颜色表中偏移量为1）的像素使用背景色显示。

有关使用以下 Windows 函数的信息，请参阅 Windows SDK：

- [CreateDIBPatternBrush](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrush) （提供此功能只是为了与版本低于3.0 的 Windows 版本编写的应用程序兼容; 请使用 `CreateDIBPatternBrushPt` 函数。）

- [CreateDIBPatternBrushPt](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrushpt) （此函数应用于基于 Win32 的应用程序。）

- [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc)

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]

##  <a name="createhatchbrush"></a>CBrush：： CreateHatchBrush

使用指定的阴影模式和颜色初始化画笔。

```
BOOL CreateHatchBrush(
    int nIndex,
    COLORREF crColor);
```

### <a name="parameters"></a>parameters

*nIndex*<br/>
指定画笔的阴影样式。 它可以是下列值之一：

- 从45度 HS_BDIAGONAL 向下影线（从左到右）

- HS_CROSS 水平和垂直交叉影线

- 45度 HS_DIAGCROSS 交叉影线

- HS_FDIAGONAL 向上影线（从左到右），45度

- HS_HORIZONTAL 水平影线

- HS_VERTICAL 垂直影线

*crColor*<br/>
指定画笔的前景色作为 RGB 颜色（阴影的颜色）。 有关详细信息，请参阅 Windows SDK 中的[COLORREF](/windows/win32/gdi/colorref) 。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

然后，可以选择该画笔作为任何设备上下文的当前画笔。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]

##  <a name="createpatternbrush"></a>CBrush：： CreatePatternBrush

使用位图指定的模式初始化画笔。

```
BOOL CreatePatternBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>parameters

*pBitmap*<br/>
标识位图。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

然后，可以为支持光栅操作的任何设备上下文选择画笔。 通常使用[CBitmap：： CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap)、 [CBitmap：： CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)、 [CBitmap：： LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)或[CBitmap：： CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)函数初始化由*pBitmap*标识的位图。

用作填充图案的位图的像素应为8像素。 如果位图更大，则 Windows 将仅使用与位图左上角的前8行和像素列相对应的位。

可以删除模式画笔，而不会影响关联的位图。 这意味着位图可用于创建任意数量的模式画笔。

使用单色位图创建的画笔（1个颜色平面，每个像素1位）使用当前的文本和背景颜色绘制。 位设置为0的像素由当前文本颜色绘制。 设置为1的位设置为1的像素将用当前背景颜色绘制。

有关使用[CreatePatternBrush](/windows/win32/api/wingdi/nf-wingdi-createpatternbrush)的信息，请参阅 Windows SDK。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]

##  <a name="createsolidbrush"></a>CBrush：： CreateSolidBrush

使用指定的纯色初始化画笔。

```
BOOL CreateSolidBrush(COLORREF crColor);
```

### <a name="parameters"></a>parameters

*crColor*<br/>
指定画笔颜色的[COLORREF](/windows/win32/gdi/colorref)结构。 颜色指定一个 RGB 值，并且可以使用 WINDOWS 中的 RGB 宏来构造。高.

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

然后，可以选择该画笔作为任何设备上下文的当前画笔。

当应用程序使用 `CreateSolidBrush`创建的画笔完成后，应从设备上下文中选择画笔。

### <a name="example"></a>示例

  请参阅[CBrush：： CBrush](#cbrush)的示例。

##  <a name="createsyscolorbrush"></a>CBrush：： CreateSysColorBrush

初始化画笔颜色。

```
BOOL CreateSysColorBrush(int nIndex);
```

### <a name="parameters"></a>parameters

*nIndex*<br/>
指定颜色索引。 此值对应于用于绘制21个窗口元素之一的颜色。 有关值的列表，请参阅 Windows SDK 中的[GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) 。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

然后，可以选择该画笔作为任何设备上下文的当前画笔。

当应用程序使用 `CreateSysColorBrush`创建的画笔完成后，应从设备上下文中选择画笔。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]

##  <a name="fromhandle"></a>CBrush：： FromHandle

给定 Windows [HBRUSH](#operator_hbrush)对象的句柄时，返回指向 `CBrush` 对象的指针。

```
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```

### <a name="parameters"></a>parameters

*hBrush*<br/>
Windows GDI 画笔的句柄。

### <a name="return-value"></a>返回值

如果成功，则为指向 `CBrush` 对象的指针;否则为 NULL。

### <a name="remarks"></a>备注

如果 `CBrush` 对象尚未附加到句柄，则会创建并附加一个临时 `CBrush` 对象。 此临时 `CBrush` 对象仅在下一次应用程序的事件循环中有空闲时间之前有效。 此时，将删除所有临时图形对象。 换言之，只有在处理一条窗口消息的过程中，临时对象才有效。

有关使用图形对象的详细信息，请参阅 Windows SDK 中的[图形对象](/windows/win32/gdi/graphic-objects)。

### <a name="example"></a>示例

  请参阅[CBrush：： CBrush](#cbrush)的示例。

##  <a name="getlogbrush"></a>CBrush：： GetLogBrush

调用此成员函数以检索 `LOGBRUSH` 结构。

```
int GetLogBrush(LOGBRUSH* pLogBrush);
```

### <a name="parameters"></a>parameters

*pLogBrush*<br/>
指向包含有关画笔的信息的[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)结构。

### <a name="return-value"></a>返回值

如果函数成功，且*pLogBrush*为有效指针，则返回值为存储到缓冲区中的字节数。

如果函数成功，且*pLogBrush*为 NULL，则返回值是保存函数将存储到缓冲区中的信息所需的字节数。

如果函数失败，则返回值为0。

### <a name="remarks"></a>备注

`LOGBRUSH` 结构定义画笔的样式、颜色和模式。

例如，调用 `GetLogBrush` 匹配位图的特定颜色或图案。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]

##  <a name="operator_hbrush"></a>CBrush：： operator HBRUSH

使用此运算符可获取 `CBrush` 对象的附加 Windows GDI 句柄。

```
operator HBRUSH() const;
```

### <a name="return-value"></a>返回值

如果成功，则为 `CBrush` 对象表示的 Windows GDI 对象的句柄;否则为 NULL。

### <a name="remarks"></a>备注

此运算符是支持直接使用 HBRUSH 对象的强制转换运算符。

有关使用图形对象的详细信息，请参阅 Windows SDK 中的[图形对象](/windows/win32/gdi/graphic-objects)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 示例 PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 类](../../mfc/reference/cgdiobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CBitmap 类](../../mfc/reference/cbitmap-class.md)<br/>
[CDC 类](../../mfc/reference/cdc-class.md)
