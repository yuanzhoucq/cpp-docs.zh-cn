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
ms.openlocfilehash: 36fd469b182d5f3e0d3449112d04c1a8623d7526
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373840"
---
# <a name="cfont-class"></a>CFont 类

封装一个 Windows 图形设备接口 (GDI) 字体并提供用于操作字体的成员函数。

## <a name="syntax"></a>语法

```
class CFont : public CGdiObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CFont：CFont](#cfont)|构造 `CFont` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CFont：：创建字体](#createfont)|使用指定的特征初始`CFont`化 。|
|[CFont：：创建字体间接](#createfontindirect)|初始化具有`CFont``LOGFONT`结构中给出的特征的对象。|
|[CFont：：创建点字体](#createpointfont)|初始化具有`CFont`指定高度（以点数的十分之一和字体为单位）。|
|[CFont：：创建点字体间接](#createpointfontindirect)|与`CreateFontIndirect`字体高度以点数而不是逻辑单位为单位度量的情况相同。|
|[CFont：：从手柄](#fromhandle)|在给定 Windows `CFont` HFONT 时返回指向对象的指针。|
|[CFont：：获取日志字体](#getlogfont)|`LOGFONT`填充有关附加到`CFont`对象的逻辑字体的信息。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CFont：：操作员惠普](#operator_hfont)|返回附加到`CFont`对象的 Windows GDI 字体句柄。|

## <a name="remarks"></a>备注

要使用`CFont`对象，请构造对象`CFont`并将 Windows 字体与[CreateFont、CreateFont](#createfont)[间接](#createfontindirect)、创建 PointFont 或[CreatePointFont 间接](#createpointfontindirect)一起附加到对象，然后使用对象的成员函数操作该字体。 [CreatePointFont](#createpointfont)

`CreatePointFont`和`CreatePointFontIndirect`函数通常比`CreateFont`或`CreateFontIndirect`因为它们自动将字体的高度从点大小转换为逻辑单位更容易使用。

有关 的详细信息`CFont`，请参阅[图形对象](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CFont`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cfontcfont"></a><a name="cfont"></a>CFont：CFont

构造 `CFont` 对象。

```
CFont();
```

### <a name="remarks"></a>备注

生成的对象必须`CreateFont`用 初始化为`CreateFontIndirect`、 `CreatePointFont`，`CreatePointFontIndirect`或在使用它之前。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]

## <a name="cfontcreatefont"></a><a name="createfont"></a>CFont：：创建字体

初始化具有指定`CFont`特征的对象。

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
指定字体所需的高度（以逻辑单位为单位）。 有关说明`lfHeight`，请参阅 Windows SDK 中的[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)结构成员。 *nHeight*的绝对值在转换后不得超过 16，384 个设备单位。 对于所有高度比较，如果所有字体都超过请求的大小，则字体映射器查找不超过请求大小或最小字体的最大字体。

*n 宽度*<br/>
指定字体中字符的平均宽度（以逻辑单位为单位）。 如果*nWidth*为 0，则设备的纵横比将与可用字体的数字化纵横比匹配，以查找最接近的匹配项，该匹配由差值的绝对值决定。

*n 逃生*<br/>
指定转义矢量与显示曲面的 x 轴之间的角度（以 0.1 度为单位）。 转义矢量是行上第一个和最后一个字符的原点。 角度从 x 轴逆时针测量。 有关详细信息，`lfEscapement`请参阅 Windows `LOGFONT` SDK 结构中的成员。

*n定向*<br/>
指定字符基线和 x 轴之间的角度（以 0.1 度为单位）。 角度从 y 方向向下的坐标系的 x 轴逆时针测量，从 y 方向向上的坐标系的 x 轴顺时针。

*n 重量*<br/>
指定字体粗细（每 1000 个以墨分像素为单位）。 有关详细信息，请参阅 Windows SDK`LOGFONT`结构中的*lfWeight*成员。 描述的值是近似值;实际外观取决于字体。 某些字体仅具有FW_NORMAL、FW_REGULAR和FW_BOLD权重。 如果指定FW_DONTCARE，则使用默认权重。

*比塔利奇*<br/>
指定字体是否为斜体。

*b 下线*<br/>
指定字体是否带有下划线。

*cStrikeOut*<br/>
指定是否已退出字体中的字符。如果设置为非零值，则指定删除字体。

*nCharSet*<br/>
指定字体的字符集 查看 Windows `lfCharSet` SDK`LOGFONT`结构中的成员，了解值列表。

OEM 字符集与系统相关。

系统中可能存在具有其他字符集的字体。 使用具有未知字符集的字体的应用程序不得尝试转换或解释要用该字体呈现的字符串。 相反，字符串应直接传递到输出设备驱动程序。

字体映射器不使用DEFAULT_CHARSET值。 应用程序可以使用此值允许字体的名称和大小来完全描述逻辑字体。 如果不存在具有指定名称的字体，则可以将任何字符集中的字体替换为指定的字体。 为了避免意外结果，应用程序应谨慎使用DEFAULT_CHARSET值。

*nOut精度*<br/>
指定所需的输出精度。 输出精度定义输出必须与请求的字体的高度、宽度、字符方向、转义和间距的匹配程度。 有关值`lfOutPrecision`的列表和详细信息`LOGFONT`，请参阅 Windows SDK 结构中的成员。

*nClip 精度*<br/>
指定所需的剪切精度。 裁剪精度定义如何剪辑部分超出剪辑区域的字符。 有关值`lfClipPrecision`列表，`LOGFONT`请参阅 Windows SDK 结构中的成员。

要使用嵌入的只读字体，应用程序必须指定CLIP_ENCAPSULATE。

为了实现设备、TrueType 和矢量字体的一致旋转，应用程序可以使用 OR 运算符将CLIP_LH_ANGLES值与任何其他*nClipPrecision*值合并。 如果设置了CLIP_LH_ANGLES位，则所有字体的旋转取决于坐标系的方向是左手还是右手。 （有关坐标系方向的详细信息，请参阅*n方向*参数的说明。如果未设置CLIP_LH_ANGLES，则设备字体始终逆时针旋转，但其他字体的旋转取决于坐标系的方向。

*n 质量*<br/>
指定字体的输出质量，该质量定义 GDI 必须仔细尝试将逻辑字体属性与实际物理字体的属性相匹配。 有关值`lfQuality`列表，`LOGFONT`请参阅 Windows SDK 结构中的成员。

*n 皮奇和家庭*<br/>
指定字体的间距和族。 有关值`lfPitchAndFamily`的列表和详细信息`LOGFONT`，请参阅 Windows SDK 结构中的成员。

*lpszFace名称*<br/>
指向`CString`null 端接字符串的 或 指针，该字符串指定字体名称。 此字符串的长度不得超过 30 个字符。 Windows [EnumFont 家庭](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesw)函数可用于枚举所有当前可用的字体。 如果*lpszFace 名称*为 NULL，则 GDI 使用与设备无关的字体。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

随后可以选择该字体作为任何设备上下文的字体。

该`CreateFont`功能不会创建新的 Windows GDI 字体。 它只是从 GDI 可用的物理字体中选择最接近的匹配项。

在创建逻辑字体时，应用程序可以使用大多数参数的默认设置。 应始终给出特定值的参数为*nHeight*和*lpszFace 名称*。 如果应用程序未设置*nHeight*和*lpszFace 名称*，则创建的逻辑字体与设备相关。

完成`CFont``CreateFont`函数创建的对象后，使用`CDC::SelectObject`在设备上下文中选择其他字体，然后删除不再需要`CFont`的对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]

## <a name="cfontcreatefontindirect"></a><a name="createfontindirect"></a>CFont：：创建字体间接

初始化具有`CFont` [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)结构中给出的特征的对象。

```
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```

### <a name="parameters"></a>参数

*lpLogFont*<br/>
指向定义逻辑`LOGFONT`字体特征的结构。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

随后可以选择该字体作为任何设备的当前字体。

此字体具有[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)结构中指定的特征。 使用[CDC：：选择对象](../../mfc/reference/cdc-class.md#selectobject)成员函数选择字体时，GDI 字体映射器会尝试将逻辑字体与现有物理字体匹配。 如果字体映射器找不到逻辑字体的精确匹配，则提供具有其特征与尽可能多的请求特征匹配的替代字体。

`CFont`当您不再需要`CreateFontIndirect`函数创建的对象时，请使用`CDC::SelectObject`在设备上下文中选择其他字体，然后删除不再需要`CFont`的对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]

## <a name="cfontcreatepointfont"></a><a name="createpointfont"></a>CFont：：创建点字体

此功能提供了创建指定字体和点大小的字体的简单方法。

```
BOOL CreatePointFont(
    int nPointSize,
    LPCTSTR lpszFaceName,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>参数

*n点大*<br/>
请求的字体高度（以点十分之一表示）。 （例如，通过 120 请求 12 点字体。

*lpszFace名称*<br/>
指向`CString`null 端接字符串的 或 指针，该字符串指定字体名称。 此字符串的长度不得超过 30 个字符。 Windows 'EnumFont 家庭函数可用于枚举所有当前可用的字体。 如果*lpszFaceName*为 NULL，则 GDI 使用与设备无关的字体。

*pDC*<br/>
指向用于以*nPointSize*为单位的高度转换为逻辑单位的[CDC](../../mfc/reference/cdc-class.md)对象。 如果为 NULL，则转换时将使用屏幕设备上下文。

### <a name="return-value"></a>返回值

如果成功，则非零，否则为 0。

### <a name="remarks"></a>备注

它使用*pDC*指向的 CDC 对象，自动将*nPointSize 的高度*转换为逻辑单位。

完成`CFont``CreatePointFont`函数创建的对象后，首先从设备上下文中选择字体，然后删除`CFont`该对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]

## <a name="cfontcreatepointfontindirect"></a><a name="createpointfontindirect"></a>CFont：：创建点字体间接

此函数与[CreateFont 间接函数](#createfontindirect)相同，`lfHeight`只不过 的成员`LOGFONT`以点的十分之一而不是设备单位进行解释。

```
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>参数

*lpLogFont*<br/>
指向定义逻辑字体特征的[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)结构。 `LOGFONT`结构`lfHeight`的成员以点的十分之一而不是逻辑单位来衡量。 （例如，设置为`lfHeight`120 以请求 12 点字体。

*pDC*<br/>
指向用于将[CDC](../../mfc/reference/cdc-class.md)高度`lfHeight`转换为逻辑单位的 CDC 对象。 如果为 NULL，则转换时将使用屏幕设备上下文。

### <a name="return-value"></a>返回值

如果成功，则非零，否则为 0。

### <a name="remarks"></a>备注

在将`LOGFONT`结构传递到 Windows 之前`lfHeight`，此功能使用*pDC*指向的 CDC 对象自动将 高度转换为逻辑单位。

完成`CFont``CreatePointFontIndirect`函数创建的对象后，首先从设备上下文中选择字体，然后删除`CFont`该对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]

## <a name="cfontfromhandle"></a><a name="fromhandle"></a>CFont：：从手柄

当为 Windows `CFont` GDI 字体对象提供 HFONT 句柄时，返回指向对象的指针。

```
static CFont* PASCAL FromHandle(HFONT hFont);
```

### <a name="parameters"></a>参数

*h字体*<br/>
Windows 字体的 HFONT 句柄。

### <a name="return-value"></a>返回值

指向`CFont`对象的指针（如果成功）;如果成功，则指向对象。否则 NULL。

### <a name="remarks"></a>备注

如果对象`CFont`尚未附加到句柄，则创建并附加临时`CFont`对象。 此临时`CFont`对象仅在下次应用程序在其事件循环中有空闲时间之前有效，此时将删除所有临时图形对象。 另一种说法是临时对象仅在处理一个窗口消息时有效。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]

## <a name="cfontgetlogfont"></a><a name="getlogfont"></a>CFont：：获取日志字体

调用此函数以检索`LOGFONT``CFont`的结构副本。

```
int GetLogFont(LOGFONT* pLogFont);
```

### <a name="parameters"></a>参数

*pLogFont*<br/>
指向[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)结构以接收字体信息。

### <a name="return-value"></a>返回值

如果函数成功，则非零，否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]

## <a name="cfontoperator-hfont"></a><a name="operator_hfont"></a>CFont：：操作员惠普

使用此运算符获取附加到`CFont`对象的字体的 Windows GDI 句柄。

```
operator HFONT() const;
```

### <a name="return-value"></a>返回值

`CFont`附加到的 Windows GDI 字体对象的句柄（如果成功）;否则 NULL。

### <a name="remarks"></a>备注

由于此运算符自动用于从`CFont`[字体和文本](/windows/win32/gdi/fonts-and-text)转换，因此您可以将对象传递给`CFont`预期 HFONT 的函数。

有关使用图形对象的详细信息，请参阅 Windows SDK 中的[图形对象](/windows/win32/gdi/graphic-objects)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 类](../../mfc/reference/cgdiobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
