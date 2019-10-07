---
title: CFont 类
ms.date: 11/04/2016
f1_keywords:
- CFont
- AFXWIN/CFont
- AFXWIN/CFont::CFont
- AFXWIN/CFont::CreateFont
- AFXWIN/CFont::CreateFontIndirect
- AFXWIN/CFont::CreatePointFont
- AFXWIN/CFont::CreatePointFontIndirect
- AFXWIN/CFont::FromHandle
- AFXWIN/CFont::GetLogFont
helpviewer_keywords:
- CFont [MFC], CFont
- CFont [MFC], CreateFont
- CFont [MFC], CreateFontIndirect
- CFont [MFC], CreatePointFont
- CFont [MFC], CreatePointFontIndirect
- CFont [MFC], FromHandle
- CFont [MFC], GetLogFont
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
ms.openlocfilehash: c37b2f657105e0065e0cddb2c508424bd6c89b0a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506491"
---
# <a name="cfont-class"></a>CFont 类

封装一个 Windows 图形设备接口 (GDI) 字体并提供用于操作字体的成员函数。

## <a name="syntax"></a>语法

```
class CFont : public CGdiObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CFont::CFont](#cfont)|构造 `CFont` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CFont::CreateFont](#createfont)|`CFont`使用指定的特性初始化。|
|[CFont::CreateFontIndirect](#createfontindirect)|使用结构中给定的特征初始化对象。`CFont` `LOGFONT`|
|[CFont::CreatePointFont](#createpointfont)|`CFont`使用指定的高度（以十分之一的点和字样度量）来初始化。|
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|与`CreateFontIndirect`不同的是，字体高度的度量单位为十分之一点而不是逻辑单元。|
|[CFont::FromHandle](#fromhandle)|给定 Windows HFONT 时， `CFont`返回指向对象的指针。|
|[CFont::GetLogFont](#getlogfont)|使用与附加`CFont`到对象的逻辑字体相关的信息填充。 `LOGFONT`|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CFont：： operator HFONT](#operator_hfont)|返回附加到`CFont`对象的 Windows GDI 字体句柄。|

## <a name="remarks"></a>备注

若要使用`CFont`对象，请使用`CFont` [CreateFont](#createfont)、 [CreateFontIndirect](#createfontindirect)、 [CreatePointFont](#createpointfont)或[CreatePointFontIndirect](#createpointfontindirect)构造对象并将其附加到该对象，然后使用该对象的成员用于操作字体的函数。

和函数`CreatePointFontIndirect`通常比`CreateFont` 或`CreateFontIndirect`更易于使用，因为它们会自动将字体的高度从点大小转换为逻辑单元。 `CreatePointFont`

有关的详细信息`CFont`，请参阅[图形对象](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CFont`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cfont"></a>CFont：： CFont

构造 `CFont` 对象。

```
CFont();
```

### <a name="remarks"></a>备注

生成的对象`CreateFont`必须使用、、 `CreatePointFont`或`CreateFontIndirect` `CreatePointFontIndirect`进行初始化，然后才能使用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]

##  <a name="createfont"></a>CFont：： CreateFont

使用指定的特性初始化对象。`CFont`

```
BOOL CreateFont(
    int nHeight,
    int nWidth,
    int nEscapement,
    int nOrientation,
    int nWeight,
    BYTE bItalic,
    BYTE bUnderline,
    BYTE cStrikeOut,
    BYTE nCharSet,
    BYTE nOutPrecision,
    BYTE nClipPrecision,
    BYTE nQuality,
    BYTE nPitchAndFamily,
    LPCTSTR lpszFacename);
```

### <a name="parameters"></a>参数

*nHeight*<br/>
指定字体所需的高度（以逻辑单位为单位）。 有关说明，请参阅 Windows SDK 中[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)结构的成员。`lfHeight` 转换后， *nHeight*的绝对值不得超过16384个设备单位。 对于所有高度的比较，如果所有字体都超出了所需大小，则字体映射器将查找不会超出所需大小的最大字体或最小字体。

*nWidth*<br/>
指定字体中字符的平均宽度（以逻辑单位为单位）。 如果*nWidth*为0，则设备的纵横比将与可用字体的每个比例比长比匹配以查找最接近的匹配项，这取决于差异的绝对值。

*nEscapement*<br/>
指定显示图面的行距向量和 x 轴之间的角度（以0.1 度为单位）。 行距矢量是行中第一个字符和最后一个字符的源的行。 角度从 x 轴逆时针测量。 有关详细信息，请`LOGFONT`参阅 Windows SDK 结构中的成员。`lfEscapement`

*nOrientation*<br/>
指定字符基线和 x 轴之间的角度（以0.1 度为单位）。 从 y 轴向下旋转，坐标系统从 x 轴沿 y 轴向下旋转，坐标系统从 x 轴顺时针测量角度，坐标系统在 y 方向上朝下旋转。

*nWeight*<br/>
指定字体粗细（以绘制像素/1000 为单位）。 有关详细信息，请参阅`LOGFONT` Windows SDK 结构中的 lfWeight 成员。 所述的值为近似值;实际外观取决于字样。 某些字体仅具有 FW_NORMAL、FW_REGULAR 和 FW_BOLD 的权重。 如果指定了 FW_DONTCARE，则使用默认权重。

*bItalic*<br/>
指定字体是否为斜体。

*bUnderline*<br/>
指定字体是否带下划线。

*cStrikeOut*<br/>
指定字体中的字符是否为线向外。如果设置为非零值，则指定删除线字体。

*nCharSet*<br/>
指定字体的字符 setSee `lfCharSet` `LOGFONT`结构中的成员在值列表的 Windows SDK 中。

OEM 字符集与系统相关。

具有其他字符集的字体可能存在于系统中。 如果应用程序使用的字体具有未知字符集，则不能尝试转换或解释将使用该字体呈现的字符串。 相反，应将字符串直接传递到输出设备驱动程序。

字体映射器不使用 DEFAULT_CHARSET 值。 应用程序可以使用此值来允许字体的名称和大小充分描述逻辑字体。 如果指定的字体不存在，则可以将任何字符集中的字体替换为指定的字体。 为了避免意外的结果，应用程序应慎用 DEFAULT_CHARSET 值。

*nOutPrecision*<br/>
指定所需的输出精度。 输出精度定义输出必须与请求字体的高度、宽度、字符方向、行距和间距匹配程度。 有关值列表和详细`LOGFONT`信息，请参阅 Windows SDK 结构中的成员。`lfOutPrecision`

*nClipPrecision*<br/>
指定所需的剪辑精度。 剪切精度定义了如何剪辑部分位于剪辑区域之外的字符。 有关值的列表， `LOGFONT`请参阅 Windows SDK 结构中的成员。`lfClipPrecision`

若要使用嵌入的只读字体，应用程序必须指定 CLIP_ENCAPSULATE。

若要实现设备、TrueType 和矢量字体的一致旋转，应用程序可以使用 OR 运算符将 CLIP_LH_ANGLES 值与任何其他*nClipPrecision*值组合。 如果设置了 CLIP_LH_ANGLES 位，则所有字体的旋转都取决于坐标系统的方向是左手还是右手。 （有关坐标系统方向的详细信息，请参阅*nOrientation*参数的说明。）如果未设置 CLIP_LH_ANGLES，则设备字体始终以逆时针方向旋转，但其他字体的旋转取决于坐标系统的方向。

*nQuality*<br/>
指定字体的输出质量，该质量定义 GDI 必须如何谨慎地尝试将逻辑字体属性与实际的物理字体的属性进行匹配。 有关值的列表， `LOGFONT`请参阅 Windows SDK 结构中的成员。`lfQuality`

*nPitchAndFamily*<br/>
指定字体的间距和系列。 有关值列表和详细`LOGFONT`信息，请参阅 Windows SDK 结构中的成员。`lfPitchAndFamily`

*lpszFacename*<br/>
一个`CString`或一个指向以 null 结尾的字符串的指针，该字符串指定字体的字体名称。 此字符串的长度不能超过30个字符。 Windows [EnumFontFamilies](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesw)函数可用于枚举当前可用的所有字体。 如果*lpszFacename*为 NULL，则 GDI 将使用与设备无关的字样。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

然后，可以选择该字体作为任何设备上下文的字体。

`CreateFont`函数不会创建新的 Windows GDI 字体。 它仅从可用于 GDI 的物理字体中选择最接近的匹配项。

创建逻辑字体时，应用程序可以使用大多数参数的默认设置。 应始终给予特定值的参数为*nHeight*和*lpszFacename*。 如果应用程序未设置*nHeight*和*lpszFacename* ，则创建的逻辑字体与设备相关。

完成`CreateFont`函数所创建的`CFont`对象后，使用`CDC::SelectObject`选择不同的字体`CFont`到设备上下文中，并删除不再需要的对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]

##  <a name="createfontindirect"></a>CFont：： CreateFontIndirect

使用[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)结构中给定的特征初始化对象。`CFont`

```
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```

### <a name="parameters"></a>参数

*lpLogFont*<br/>
指向定义逻辑字体特征的结构。`LOGFONT`

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

然后，可以选择该字体作为任何设备的当前字体。

此字体具有在[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)结构中指定的特征。 当使用[CDC：： SelectObject](../../mfc/reference/cdc-class.md#selectobject)成员函数选择字体时，GDI 字体映射器会尝试使用现有的物理字体来匹配逻辑字体。 如果字体映射器找不到与逻辑字体完全匹配的匹配项，则它会提供一种替代字体，其特征与尽可能多的请求特征匹配。

`CFont`如果不再需要该`CreateFontIndirect`函数创建的对象，请使用`CDC::SelectObject`在设备上下文中选择其他字体，然后删除`CFont`不再需要的对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]

##  <a name="createpointfont"></a>CFont：： CreatePointFont

此函数提供了一种简单的方法来创建指定字样和点大小的字体。

```
BOOL CreatePointFont(
    int nPointSize,
    LPCTSTR lpszFaceName,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>参数

*nPointSize*<br/>
在十分之一的点中请求的字体高度。 （例如，传递120请求12点字体。）

*lpszFaceName*<br/>
一个`CString`或一个指向以 null 结尾的字符串的指针，该字符串指定字体的字体名称。 此字符串的长度不能超过30个字符。 Windows 的 EnumFontFamilies 函数可用于枚举当前可用的所有字体。 如果*lpszFaceName*为 NULL，则 GDI 将使用与设备无关的字样。

*pDC*<br/>
指向要用于将*nPointSize*中的高度转换为逻辑单元的[CDC](../../mfc/reference/cdc-class.md)对象的指针。 如果为 NULL，则用于转换的屏幕设备上下文。

### <a name="return-value"></a>返回值

如果成功，则为非零; 否则为0。

### <a name="remarks"></a>备注

它使用*pDC*指向的 CDC 对象自动将*nPointSize*中的高度转换为逻辑单元。

完成`CFont` `CreatePointFont`函数创建的对象后，首先选择设备`CFont`上下文之外的字体，然后删除对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]

##  <a name="createpointfontindirect"></a>  CFont::CreatePointFontIndirect

此函数与[CreateFontIndirect](#createfontindirect)相同，不同之处在于`lfHeight` ，的`LOGFONT`成员在一个点而不是设备单位中进行解释。

```
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>参数

*lpLogFont*<br/>
指向定义逻辑字体特征的[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)结构。 `LOGFONT`结构的成员按十分之一的点而不是逻辑单元来度量。 `lfHeight` （例如，设置`lfHeight`为120以请求12点字体。）

*pDC*<br/>
指向要用于将`lfHeight`高度转换为逻辑单元的 [CDC](../../mfc/reference/cdc-class.md) 对象的指针。 如果为 NULL，则用于转换的屏幕设备上下文。

### <a name="return-value"></a>返回值

如果成功，则为非零; 否则为0。

### <a name="remarks"></a>备注

在将`LOGFONT`结构传递到 Windows 之前`lfHeight` ，此函数使用*pDC*指向的 CDC 对象自动将的高度转换为逻辑单元。

完成`CFont` `CreatePointFontIndirect`函数创建的对象后，首先选择设备`CFont`上下文之外的字体，然后删除对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]

##  <a name="fromhandle"></a>CFont：： FromHandle

当给定 Windows GDI 字体`CFont`对象的 HFONT 句柄时，返回指向对象的指针。

```
static CFont* PASCAL FromHandle(HFONT hFont);
```

### <a name="parameters"></a>参数

*hFont*<br/>
Windows 字体的 HFONT 句柄。

### <a name="return-value"></a>返回值

如果成功，则`CFont`为指向对象的指针; 否则为 NULL。

### <a name="remarks"></a>备注

如果对象尚未附加到句柄，则会创建并附加`CFont`一个临时对象。 `CFont` 此临时`CFont`对象仅在下一次应用程序的事件循环中有空闲时间时才有效，此时所有临时图形对象都会被删除。 指出这一点的另一种方法是：只有在处理一条窗口消息的过程中，临时对象才有效。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]

##  <a name="getlogfont"></a>CFont：： GetLogFont

调用此函数可检索`LOGFONT` `CFont`结构的副本。

```
int GetLogFont(LOGFONT* pLogFont);
```

### <a name="parameters"></a>参数

*pLogFont*<br/>
指向[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)结构的指针，该结构用于接收字体信息。

### <a name="return-value"></a>返回值

如果函数成功，则为非零; 否则为0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]

##  <a name="operator_hfont"></a>CFont：： operator HFONT

使用此运算符可获取附加到`CFont`对象的字体的 Windows GDI 句柄。

```
operator HFONT() const;
```

### <a name="return-value"></a>返回值

如果成功，则为附加到`CFont`的 Windows GDI 字体对象的句柄; 否则为 NULL。

### <a name="remarks"></a>备注

由于此运算符自动用于从`CFont`到[字体和文本](/windows/win32/gdi/fonts-and-text)的转换，因此您可以将`CFont`对象传递到预期 HFONTs 的函数。

有关使用图形对象的详细信息，请参阅 Windows SDK 中的[图形对象](/windows/win32/gdi/graphic-objects)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 类](../../mfc/reference/cgdiobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
