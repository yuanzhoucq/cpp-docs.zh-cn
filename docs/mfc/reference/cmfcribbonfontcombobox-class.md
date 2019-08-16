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
ms.openlocfilehash: 186c4bc3e1b26529ed0e000d2893e1b2d81c4304
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504957"
---
# <a name="cmfcribbonfontcombobox-class"></a>CMFCRibbonFontComboBox 类

实现包含字体列表的组合框。 将组合框置于功能区面板上。

## <a name="syntax"></a>语法

```
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|析构函数。|

### <a name="protected-constructors"></a>受保护的构造函数

|name|描述|
|----------|-----------------|
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|构造并初始化一个 `CMFCRibbonFontComboBox` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|使用具有指定字体类型、字符集以及间距和系列的字体填充功能区字体组合框。|
|`CMFCRibbonFontComboBox::CreateObject`|由框架用于创建此类类型的动态实例。|
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|返回指定字符集。|
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|返回要在组合框中显示的字体类型。 有效选项是是 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE 或是它们的任何按位组合。|
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|返回组合框中显示的字体的间距和系列。|
|`CMFCRibbonFontComboBox::GetThisClass`|由框架用于获取指向与此类类型相关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|使用具有以前指定的字体类型、字符集以及间距和系列的字体填充功能区字体组合框。|
|[CMFCRibbonFontComboBox::SetFont](#setfont)|选择组合框中的指定字体。|

## <a name="remarks"></a>备注

创建`CMFCRibbonFontComboBox`对象后, 可以通过调用[CMFCRibbonPanel:: add](../../mfc/reference/cmfcribbonpanel-class.md#add)将其添加到功能区面板。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)

## <a name="requirements"></a>要求

**标头:** afxRibbonComboBox

##  <a name="buildfonts"></a>CMFCRibbonFontComboBox::BuildFonts

用字体填充功能区上的组合框。

```
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```

### <a name="parameters"></a>参数

*nFontType*<br/>
中指定要添加的字体的字体类型。

*nCharSet*<br/>
中指定要添加的字体的字符集。

*nPitchAndFamily*<br/>
中指定要添加的字体的间距和系列。

##  <a name="cmfcribbonfontcombobox"></a>CMFCRibbonFontComboBox::CMFCRibbonFontComboBox

构造并初始化[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)对象。

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
中用户从组合框中选择项时执行的命令的命令 ID。

*nFontType*<br/>
中指定要在组合框中显示的字体类型。 有效选项是是 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE 或是它们的任何按位组合。

*nCharSet*<br/>
中将组合框中的字体筛选为属于指定字符集的字体。

*nPitchAndFamily*<br/>
中指定组合框中显示的字体的间距和系列。

*nWidth*<br/>
中指定组合框的宽度 (以像素为单位)。

### <a name="remarks"></a>备注

有关可能的*nFontType*参数值的详细信息, 请参阅 Windows SDK 文档中的[EnumFontFamProc](/previous-versions/dd162621\(v=vs.85\)) 。

有关可分配给*nCharSet*的有效字符集以及可分配给*nPitchAndFamily*的有效值的详细信息, 请参阅 Windows SDK 文档中的[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) 。

##  <a name="getfontdesc"></a>CMFCRibbonFontComboBox::GetFontDesc

有关更多详细信息, 请参阅位于 Visual Studio 安装的**VC\\atlmfc\\src\\mfc**文件夹中的源代码。

```
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;
```

### <a name="parameters"></a>参数

中*iIndex*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="rebuildfonts"></a>CMFCRibbonFontComboBox::RebuildFonts

使用以前指定的字体类型、字符集以及间距和系列的字体填充功能区上的组合框。

```
void RebuildFonts();
```

### <a name="remarks"></a>备注

可以指定要包含在此类的[构造函数](#cmfcribbonfontcombobox)的功能区字体组合框中的字体类型、字符集以及间距和系列, 也可以通过调用[CMFCRibbonFontComboBox:: BuildFonts](#buildfonts)来指定。

##  <a name="setfont"></a>CMFCRibbonFontComboBox::SetFont

选择组合框中的指定字体。

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet = DEFAULT_CHARSET,
    BOOL bExact = FALSE);
```

### <a name="parameters"></a>参数

' lpszName * 指定要选择的字体的名称。

*nCharSet*<br/>
指定所选字体的字符集。

*bExact*<br/>
若要指定在选择字体时字符集必须匹配, 则为 TRUE;若要指定在选择字体时可以忽略字符集, 则为 FALSE。

### <a name="return-value"></a>返回值

如果找到并选中指定的字体, 则为非零值;否则为零。

### <a name="remarks"></a>备注

##  <a name="getcharset"></a>CMFCRibbonFontComboBox::GetCharSet

返回指定字符集。

```
BYTE GetCharSet() const;
```

### <a name="return-value"></a>返回值

字符集 (请参阅 Windows SDK 文档中的 LOGFONT)。

### <a name="remarks"></a>备注

##  <a name="getfonttype"></a>CMFCRibbonFontComboBox::GetFontType

返回要在组合框中显示的字体类型。 有效选项是是 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE 或是它们的任何按位组合。

```
int GetFontType() const;
```

### <a name="return-value"></a>返回值

字体类型 (请参阅 Windows SDK 文档中的 EnumFontFamProc)。

### <a name="remarks"></a>备注

##  <a name="getpitchandfamily"></a>CMFCRibbonFontComboBox::GetPitchAndFamily

返回组合框中显示的字体的间距和系列。

```
BYTE GetPitchAndFamily() const;
```

### <a name="return-value"></a>返回值

间距和系列 (请参阅 Windows SDK 文档中的 LOGFONT)。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonComboBox 类](../../mfc/reference/cmfcribboncombobox-class.md)
