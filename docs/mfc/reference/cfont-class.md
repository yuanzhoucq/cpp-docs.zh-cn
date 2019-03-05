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
ms.openlocfilehash: 60a717136f69b29df48dd8f449ddaffe5c15ccbf
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271861"
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
|[CFont::CreateFont](#createfont)|初始化`CFont`与指定的特性。|
|[CFont::CreateFontIndirect](#createfontindirect)|初始化`CFont`对象中给定的特征`LOGFONT`结构。|
|[CFont::CreatePointFont](#createpointfont)|初始化`CFont`与指定的高度，以点和字样的十分之几。|
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|与相同`CreateFontIndirect`不同之处在于字体高度以点而不是逻辑单元的十分之几。|
|[CFont::FromHandle](#fromhandle)|返回一个指向`CFont`对象在给定 Windows HFONT。|
|[CFont::GetLogFont](#getlogfont)|填充`LOGFONT`附加到的逻辑字体信息`CFont`对象。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CFont::operator HFONT](#operator_hfont)|返回 Windows GDI 字体句柄附加到`CFont`对象。|

## <a name="remarks"></a>备注

若要使用`CFont`对象，构造`CFont`对象，并与它附加 Windows 字体[CreateFont](#createfont)， [CreateFontIndirect](#createfontindirect)， [CreatePointFont](#createpointfont)，或[CreatePointFontIndirect](#createpointfontindirect)，然后使用该对象的成员函数来操作该字体。

`CreatePointFont`并`CreatePointFontIndirect`函数通常是更轻松地使用比`CreateFont`或`CreateFontIndirect`由于它们自动进行转换的高度的字体的磅值从到逻辑单元。

有关详细信息`CFont`，请参阅[图形对象](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CFont`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cfont"></a>  CFont::CFont

构造 `CFont` 对象。

```
CFont();
```

### <a name="remarks"></a>备注

生成的对象必须使用初始化`CreateFont`， `CreateFontIndirect`， `CreatePointFont`，或`CreatePointFontIndirect`然后才能使用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]

##  <a name="createfont"></a>  CFont::CreateFont

初始化`CFont`具有指定特征的对象。

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
指定字体的所需的高度 （以逻辑单位）。 请参阅`lfHeight`的成员[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)说明 Windows SDK 中的结构。 值的绝对值*nHeight*转换后不能超过 16,384 设备单位。 对于所有高度比较，字体映射器看起来不超过所请求的大小的最大字体或最小字体如果所有字体都超出了所请求的大小。

*nWidth*<br/>
指定该字体中字符的平均宽度 （以逻辑单位）。 如果*nWidth*为 0，则将以查找由的差异的绝对值的最接近的可用字体数字化纵横比与匹配的设备的纵横比。

*nEscapement*<br/>
指定的行距向量和 x 轴的显示图面之间的角度 （以 0.1 度为单位）。 行距向量是通过在行上的第一个和最后一个字符的源服务器的行。 表示的角度从 x 轴按逆时针方向测量。 请参阅`lfEscapement`中的成员`LOGFONT`Windows SDK for 的详细信息中的结构。

*nOrientation*<br/>
指定字符的基线和 x 轴之间的角度 （以 0.1 度为单位）。 表示的角度是按逆时针方向测量从 x 轴的坐标系统中的 y 轴方向已关闭并且从 y 轴方向已启动的坐标系统的 x 轴顺时针旋转。

*nWeight*<br/>
指定的字体粗细 （以每 1000 个的绘制的像素为单位）。 请参阅*lfWeight*中的成员`LOGFONT`Windows SDK for 的详细信息中的结构。 所述的值是近似的;实际的外观取决于字样。 某些字体具有仅 FW_NORMAL、 FW_REGULAR 和 FW_BOLD 的权重。 如果指定 FW_DONTCARE，则使用默认权重。

*bItalic*<br/>
指定字体为斜体。

*bUnderline*<br/>
指定字体是否带下划线。

*cStrikeOut*<br/>
指定该字体中的字符让。如果指定删除线字体设置为非零值。

*nCharSet*<br/>
指定字体的字符 setSee`lfCharSet`中的成员`LOGFONT`适用于一系列值的 Windows SDK 中的结构。

OEM 字符集与系统相关。

在系统中可能存在与其他字符集的字体。 使用具有未知的字符集的字体的应用程序必须尝试转换或解释要使用该字体呈现的字符串。 相反，应直接向输出设备驱动程序传递字符串。

字体映射器不使用 DEFAULT_CHARSET 值。 应用程序可以使用此值允许的名称和完整描述的逻辑字体的字体大小。 如果不存在具有指定名称的字体，则可以为指定的字体替换从任何字符集的字体。 若要避免意外的结果，应用程序应尽量少使用 DEFAULT_CHARSET 值。

*nOutPrecision*<br/>
指定所需的输出精度。 输出精度定义输出必须请求的字体的高度、 宽度、 字符方向、 escapement 和间距的匹配程度。 请参阅`lfOutPrecision`中的成员`LOGFONT`Windows SDK for 值和的详细信息的列表中的结构。

*nClipPrecision*<br/>
指定所需的剪辑精度。 剪辑精度定义如何剪辑部分剪辑区域外的字符。 请参阅`lfClipPrecision`中的成员`LOGFONT`适用于一系列值的 Windows SDK 中的结构。

若要使用的嵌入的只读的字体，应用程序必须指定 CLIP_ENCAPSULATE。

若要实现一致旋转的设备、 TrueType 和矢量字体，应用程序可以使用或运算符将与任何其他 CLIP_LH_ANGLES 值合并*nClipPrecision*值。 如果设置 CLIP_LH_ANGLES 位，则所有字体的旋转取决于坐标系统的方向是惯用左手还是惯用右手。 (有关坐标系统的方向的详细信息，请参阅的说明*nOrientation*参数。)如果未设置 CLIP_LH_ANGLES，设备字体始终逆时针，旋转，但其他字体的旋转所依赖的坐标系统的方向。

*nQuality*<br/>
指定字体的输出质量，它定义如何仔细 GDI 必须尝试匹配与实际的物理字体的逻辑字体属性。 请参阅`lfQuality`中的成员`LOGFONT`适用于一系列值的 Windows SDK 中的结构。

*nPitchAndFamily*<br/>
指定的间距和系列的字体。 请参阅`lfPitchAndFamily`中的成员`LOGFONT`Windows SDK for 值和的详细信息的列表中的结构。

*lpszFacename*<br/>
一个`CString`或指定的字体的字样名称的以 null 结尾的字符串指针。 此字符串的长度不得超过 30 个字符。 Windows [EnumFontFamilies](/windows/desktop/api/wingdi/nf-wingdi-enumfontfamiliesa)函数可用来枚举所有当前可用的字体。 如果*lpszFacename*为 NULL，GDI 使用独立于设备的字样。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

随后可以为任何设备上下文的字体选择字体。

`CreateFont`函数不会创建一个新的 Windows GDI 字体。 它只是选择最接近的匹配项从可用的物理字体到 GDI。

创建一个逻辑字体时，应用程序可以为参数最多使用默认设置。 应始终提供特定值的参数是*nHeight*并*lpszFacename*。 如果*nHeight*并*lpszFacename*未设置应用程序创建的逻辑字体与设备相关。

完成通过`CFont`对象创建`CreateFont`函数中，使用`CDC::SelectObject`若要在设备上下文选择不同的字体，然后删除`CFont`不再需要的对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]

##  <a name="createfontindirect"></a>  CFont::CreateFontIndirect

初始化`CFont`对象中给定的特征[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)结构。

```
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```

### <a name="parameters"></a>参数

*lpLogFont*<br/>
指向`LOGFONT`结构，它定义的逻辑字体特征。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

随后可以为任何设备的当前字体选择字体。

此字体已在指定的特征[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)结构。 当通过使用选择字体[cdc:: selectobject](../../mfc/reference/cdc-class.md#selectobject)成员函数的 GDI 字体映射器将尝试匹配与现有的物理字体的逻辑字体。 如果无法找到完全匹配的逻辑字体字体映射器，它提供了其特征与尽可能多的请求尽可能特征替代字体。

当不再需要`CFont`对象创建`CreateFontIndirect`函数中，使用`CDC::SelectObject`若要在设备上下文选择不同的字体，然后删除`CFont`不再需要的对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]

##  <a name="createpointfont"></a>  CFont::CreatePointFont

此函数提供了简单的方法来创建指定的字样的字体和磅值。

```
BOOL CreatePointFont(
    int nPointSize,
    LPCTSTR lpszFaceName,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>参数

*nPointSize*<br/>
请求的中点的十分之几秒的字体高度。 （例如，传递请求 12 点字体的 120。）

*lpszFaceName*<br/>
一个`CString`或指定的字体的字样名称的以 null 结尾的字符串指针。 此字符串的长度不得超过 30 个字符。 Windows EnumFontFamilies 函数可用来枚举所有当前可用的字体。 如果*lpszFaceName*为 NULL，GDI 使用独立于设备的字样。

*pDC*<br/>
指向[CDC](../../mfc/reference/cdc-class.md)对象，用于将转换的高度以*nPointSize*到逻辑单元。 如果为 NULL，则屏幕设备上下文用于转换。

### <a name="return-value"></a>返回值

非零，如果成功，否则为 0。

### <a name="remarks"></a>备注

它会自动将转换的高度以*nPointSize*逻辑单元使用的 CDC 对象指向*pDC*。

完成通过`CFont`对象创建`CreatePointFont`函数，请先选择从设备上下文的字体，然后删除`CFont`对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]

##  <a name="createpointfontindirect"></a>  CFont::CreatePointFontIndirect

此函数等同于[CreateFontIndirect](#createfontindirect)只不过`lfHeight`的成员`LOGFONT`解释中点而不是设备单位的十分之几。

```
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>参数

*lpLogFont*<br/>
指向[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)结构，它定义的逻辑字体特征。 `lfHeight`的成员`LOGFONT`结构大小的单位点而不是逻辑单元的十分之几。 (例如，设置`lfHeight`为 120 请求 12 点字体。)

*pDC*<br/>
指向[CDC](../../mfc/reference/cdc-class.md)对象，用于将转换的高度以`lfHeight`到逻辑单元。 如果为 NULL，则屏幕设备上下文用于转换。

### <a name="return-value"></a>返回值

非零，如果成功，否则为 0。

### <a name="remarks"></a>备注

此函数会自动将转换的高度以`lfHeight`逻辑单元使用的 CDC 对象指向*pDC*然后才传递`LOGFONT`到 Windows 的结构。

完成通过`CFont`对象创建`CreatePointFontIndirect`函数，请先选择从设备上下文的字体，然后删除`CFont`对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]

##  <a name="fromhandle"></a>  CFont::FromHandle

返回一个指向`CFont`对象时提供给 Windows GDI 字体对象的 HFONT 句柄。

```
static CFont* PASCAL FromHandle(HFONT hFont);
```

### <a name="parameters"></a>参数

*hFont*<br/>
Windows 字体 HFONT 句柄。

### <a name="return-value"></a>返回值

一个指向`CFont`如果成功，否则该值为 NULL 的对象。

### <a name="remarks"></a>备注

如果`CFont`对象尚未附加到句柄，临时`CFont`创建并附加对象。 此临时`CFont`对象仅用于有效直到下一次应用程序在其事件循环内有空闲时间，在该时间所有临时图形对象会被删除。 另一种说法： 这是仅在一个窗口消息处理期间的临时对象有效。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]

##  <a name="getlogfont"></a>  CFont::GetLogFont

调用此函数可检索的副本`LOGFONT`结构`CFont`。

```
int GetLogFont(LOGFONT* pLogFont);
```

### <a name="parameters"></a>参数

*pLogFont*<br/>
指向[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)接收字体信息的结构。

### <a name="return-value"></a>返回值

如果函数成功，否则为 0，非零值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]

##  <a name="operator_hfont"></a>  CFont::operator HFONT

此运算符用于获取附加到的字体的 Windows GDI 句柄`CFont`对象。

```
operator HFONT() const;
```

### <a name="return-value"></a>返回值

Windows GDI 字体对象的句柄附加到`CFont`如果成功，否则该值为 NULL。

### <a name="remarks"></a>备注

由于为从转换会自动使用此运算符`CFont`到[字体和文本](/windows/desktop/gdi/fonts-and-text)，可以将传递`CFont`HFONTs 函数的对象。

有关使用图形对象的详细信息，请参阅[图形对象](/windows/desktop/gdi/graphic-objects)Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 HIERSVR](../../visual-cpp-samples.md)<br/>
[CGdiObject 类](../../mfc/reference/cgdiobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
