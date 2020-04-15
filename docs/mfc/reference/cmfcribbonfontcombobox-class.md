---
title: CMFCRibbonFontComboBox 类
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::BuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetCharSet
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontDesc
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontType
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetPitchAndFamily
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::RebuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::SetFont
helpviewer_keywords:
- CMFCRibbonFontComboBox [MFC], CMFCRibbonFontComboBox
- CMFCRibbonFontComboBox [MFC], BuildFonts
- CMFCRibbonFontComboBox [MFC], GetCharSet
- CMFCRibbonFontComboBox [MFC], GetFontDesc
- CMFCRibbonFontComboBox [MFC], GetFontType
- CMFCRibbonFontComboBox [MFC], GetPitchAndFamily
- CMFCRibbonFontComboBox [MFC], RebuildFonts
- CMFCRibbonFontComboBox [MFC], SetFont
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
ms.openlocfilehash: 822f4f6fe76bb5b82b455daec54ed96568ea6ba7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375169"
---
# <a name="cmfcribbonfontcombobox-class"></a>CMFCRibbonFontComboBox 类

实现包含字体列表的组合框。 将组合框置于功能区面板上。

## <a name="syntax"></a>语法

```
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|析构函数。|

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|构造并初始化一个 `CMFCRibbonFontComboBox` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|使用具有指定字体类型、字符集以及间距和系列的字体填充功能区字体组合框。|
|`CMFCRibbonFontComboBox::CreateObject`|由框架用于创建此类类型的动态实例。|
|[CMFC功能放大缩小字体功能 放大缩小字体功能](#getcharset)|返回指定字符集。|
|[CMFC功能放大缩小字体功能 放大缩小字体功能](#getfontdesc)||
|[CMFC功能放大缩小字体功能 放大缩小字体功能](#getfonttype)|返回要在组合框中显示的字体类型。 有效选项是是 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE 或是它们的任何按位组合。|
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|返回组合框中显示的字体的间距和系列。|
|`CMFCRibbonFontComboBox::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|使用具有以前指定的字体类型、字符集以及间距和系列的字体填充功能区字体组合框。|
|[CMFCRibbonFontComboBox::SetFont](#setfont)|选择组合框中的指定字体。|

## <a name="remarks"></a>备注

创建`CMFCRibbonFontComboBox`对象后，请调用[CMFC 功能面板将其添加到功能区面板：：：添加](../../mfc/reference/cmfcribbonpanel-class.md#add)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)

## <a name="requirements"></a>要求

**标题：** afxRibbonComboBox.h

## <a name="cmfcribbonfontcomboboxbuildfonts"></a><a name="buildfonts"></a>CMFC功能放大缩小字体功能 放大缩小字体功能

使用字体填充功能区上的组合框。

```
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```

### <a name="parameters"></a>参数

*n字体类型*<br/>
[在]指定要添加的字体的字体类型。

*nCharSet*<br/>
[在]指定要添加的字体的字符集。

*n 皮奇和家庭*<br/>
[在]指定要添加的字体的间距和族。

## <a name="cmfcribbonfontcomboboxcmfcribbonfontcombobox"></a><a name="cmfcribbonfontcombobox"></a>CMFC 功能丰丰盒：：CMFC 功能丰丰博盒

构造并初始化[CMFC 功能丰博盒](../../mfc/reference/cmfcribbonfontcombobox-class.md)对象。

```
CMFCRibbonFontComboBox(
    UINT nID,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH,
    int nWidth = -1);
```

### <a name="parameters"></a>参数

*nID*<br/>
[在]当用户从组合框中选择项时执行的命令的命令 ID。

*n字体类型*<br/>
[在]指定要在组合框中显示的字体类型。 有效选项是是 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE 或是它们的任何按位组合。

*nCharSet*<br/>
[在]将组合框中的字体筛选为属于指定字符集的字体。

*n 皮奇和家庭*<br/>
[在]指定组合框中显示的字体的间距和族。

*n 宽度*<br/>
[在]指定组合框的宽度（以像素为单位）。

### <a name="remarks"></a>备注

有关可能的*nFontType*参数值的详细信息，请参阅 Windows SDK 文档中的[EnumFontFamProc。](/previous-versions/dd162621\(v=vs.85\))

有关可分配给*nCharSet*的有效字符集的详细信息，以及可分配给*nPitch 和Family*的有效值，请参阅 Windows SDK 文档中的[LOGFONT。](/windows/win32/api/wingdi/ns-wingdi-logfontw)

## <a name="cmfcribbonfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a>CMFC功能放大缩小字体功能 放大缩小字体功能

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;
```

### <a name="parameters"></a>参数

[在]*iIndex*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcribbonfontcomboboxrebuildfonts"></a><a name="rebuildfonts"></a>CMFC功能放大缩小字体功能 放大缩小字体功能

使用以前指定的字体类型、字符集、间距和族的字体填充功能区上的组合框。

```
void RebuildFonts();
```

### <a name="remarks"></a>备注

您可以指定字体类型、字符集、间距以及字体的音调以及要包含在此类[构造函数](#cmfcribbonfontcombobox)的功能区字体组合框中，或者通过调用[CMFCRibbonFontCombox：：BuildFonts。](#buildfonts)

## <a name="cmfcribbonfontcomboboxsetfont"></a><a name="setfont"></a>CMFC 功能放大缩小字体功能 放大缩小字体功能

选择组合框中的指定字体。

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet = DEFAULT_CHARSET,
    BOOL bExact = FALSE);
```

### <a name="parameters"></a>参数

"lpszName" 指定要选择的字体的名称。

*nCharSet*<br/>
指定所选字体的字符集。

*b精确*<br/>
TRUE 指定字符集在选择字体时必须匹配;FALSE 指定在选择字体时可以忽略字符集。

### <a name="return-value"></a>返回值

如果找到并选择了指定的字体，则非零;否则，零。

### <a name="remarks"></a>备注

## <a name="cmfcribbonfontcomboboxgetcharset"></a><a name="getcharset"></a>CMFC功能放大缩小字体功能 放大缩小字体功能

返回指定字符集。

```
BYTE GetCharSet() const;
```

### <a name="return-value"></a>返回值

字符集（请参阅 Windows SDK 文档中的 LOGFONT）。

### <a name="remarks"></a>备注

## <a name="cmfcribbonfontcomboboxgetfonttype"></a><a name="getfonttype"></a>CMFC功能放大缩小字体功能 放大缩小字体功能

返回要在组合框中显示的字体类型。 有效选项是是 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE 或是它们的任何按位组合。

```
int GetFontType() const;
```

### <a name="return-value"></a>返回值

字体类型（请参阅 Windows SDK 文档中的 EnumFontFamProc）。

### <a name="remarks"></a>备注

## <a name="cmfcribbonfontcomboboxgetpitchandfamily"></a><a name="getpitchandfamily"></a>CMFC功能放大缩小字体功能 放大缩小字体功能

返回组合框中显示的字体的间距和系列。

```
BYTE GetPitchAndFamily() const;
```

### <a name="return-value"></a>返回值

间距和系列（请参阅 Windows SDK 文档中的 LOGFONT）。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC 功能通信盒类](../../mfc/reference/cmfcribboncombobox-class.md)
