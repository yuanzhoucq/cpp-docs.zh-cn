---
title: CMFCFontComboBox 类
ms.date: 11/04/2016
f1_keywords:
- CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::GetSelFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::SelectFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::Setup
- AFXFONTCOMBOBOX/CMFCFontComboBox::m_bDrawUsingFont
helpviewer_keywords:
- CMFCFontComboBox [MFC], CMFCFontComboBox
- CMFCFontComboBox [MFC], GetSelFont
- CMFCFontComboBox [MFC], SelectFont
- CMFCFontComboBox [MFC], Setup
- CMFCFontComboBox [MFC], m_bDrawUsingFont
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
ms.openlocfilehash: 69e8f81e7e01d0610f3cbf88ac1725a21d59838f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505302"
---
# <a name="cmfcfontcombobox-class"></a>CMFCFontComboBox 类

`CMFCFontComboBox`类创建包含字体列表的组合框控件。

## <a name="syntax"></a>语法

```
class CMFCFontComboBox : public CComboBox
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCFontComboBox::CMFCFontComboBox](#cmfcfontcombobox)|构造 `CMFCFontComboBox` 对象。|
|`CMFCFontComboBox::~CMFCFontComboBox`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|`CMFCFontComboBox::CompareItem`|由框架调用, 以确定新项在当前字体组合框控件的已排序列表框中的相对位置。 (重写[CComboBox:: CompareItem](../../mfc/reference/ccombobox-class.md#compareitem)。)|
|`CMFCFontComboBox::DrawItem`|由框架调用, 用于绘制当前字体组合框控件中的指定项。 (重写[CComboBox::D rawitem](../../mfc/reference/ccombobox-class.md#drawitem)。)|
|[CMFCFontComboBox::GetSelFont](#getselfont)|检索当前选定字体的相关信息。|
|`CMFCFontComboBox::MeasureItem`|由框架调用, 以通知窗口当前字体组合框控件中列表框的尺寸。 (重写[CComboBox:: MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem)。)|
|`CMFCFontComboBox::PreTranslateMessage`|转换窗口消息, 然后将其调度到[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)和[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 函数。 （重写 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。）|
|[CMFCFontComboBox::SelectFont](#selectfont)|从 "字体" 组合框中选择与指定条件匹配的字体。|
|[CMFCFontComboBox::Setup](#setup)|初始化字体组合框中的项列表。|

### <a name="data-members"></a>数据成员

|名称|描述|
|----------|-----------------|
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|向框架指示在当前字体组合框中绘制项标签所使用的字体。|

## <a name="remarks"></a>备注

若要在`CMFCFontComboBox`对话框中使用对象, 请`CMFCFontComboBox`将变量添加到对话框类。 然后, 在`OnInitDialog`对话框类的方法中调用[CMFCFontComboBox:: Setup](#setup)方法以初始化组合框控件中的项列表。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

[CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)

## <a name="requirements"></a>要求

**标头:** afxfontcombobox

##  <a name="cmfcfontcombobox"></a>CMFCFontComboBox:: CMFCFontComboBox

构造 `CMFCFontComboBox` 对象。

```
CMFCFontComboBox();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="getselfont"></a>CMFCFontComboBox:: GetSelFont

检索当前选定字体的相关信息。

```
CMFCFontInfo* GetSelFont() const;
```

### <a name="return-value"></a>返回值

指向描述字体的[CMFCFontInfo 类](../../mfc/reference/cmfcfontinfo-class.md)对象的指针。 如果未在组合框中选择字体, 则可以为 NULL。

### <a name="remarks"></a>备注

##  <a name="m_bdrawusingfont"></a>CMFCFontComboBox:: m_bDrawUsingFont

向框架指示在当前字体组合框中绘制项标签所使用的字体。

```
static BOOL m_bDrawUsingFont;
```

### <a name="remarks"></a>备注

将此成员设置为 TRUE 可指示框架使用相同的字体绘制每个项标签。 将此成员设置为 FALSE 可指示框架用其名称与标签相同的字体绘制每个项标签。 此成员的默认值为 FALSE。

##  <a name="selectfont"></a>CMFCFontComboBox:: SelectFont

从 "字体" 组合框中选择与指定条件匹配的字体。

```
BOOL SelectFont(CMFCFontInfo* pDesc);

BOOL SelectFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET);
```

### <a name="parameters"></a>参数

*pDesc*<br/>
中指向字体说明对象。

*lpszName*<br/>
中指定字体名称。

*nCharSet*<br/>
中指定字符集。 默认值为 DEFAULT_CHARSET。 有关详细信息, 请参阅`lfCharSet` [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)结构的成员。

### <a name="return-value"></a>返回值

如果字体组合框中的项与指定的字体说明对象或字体名称和字符集相匹配, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

使用此方法可选择并滚动到与指定字体相对应的 "字体" 组合框中的项。

### <a name="example"></a>示例

下面的示例演示如何使用`SelectFont` `CMFCFontComboBox`类中的方法。 此示例是[新控件示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]

##  <a name="setup"></a>CMFCFontComboBox:: Setup

初始化字体组合框中的项列表。

```
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,
    BYTE nCharSet=DEFAULT_CHARSET,
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```

### <a name="parameters"></a>参数

*nFontType*<br/>
中指定字体类型。 默认值为 DEVICE_FONTTYPE、RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE 的按位组合 (OR)。

*nCharSet*<br/>
中指定字体字符集。 默认值为 DEFAULT_CHARSET。

*nPitchAndFamily*<br/>
中指定字体间距和系列。 默认值为 DEFAULT_PITCH。

### <a name="return-value"></a>返回值

如果已成功初始化字体组合框, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法通过枚举当前已安装的与指定参数匹配的字体并在 "字体" 组合框中插入这些字体名称, 初始化字体组合框。

### <a name="example"></a>示例

下面的示例演示如何使用`Setup` `CMFCFontComboBox`类中的方法。 此示例是[新控件示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCFontInfo 类](../../mfc/reference/cmfcfontinfo-class.md)
