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
ms.openlocfilehash: 60b4b7cdfdace2332de35dd93c43eacf592e99e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367493"
---
# <a name="cmfcfontcombobox-class"></a>CMFCFontComboBox 类

类`CMFCFontComboBox`创建一个包含字体列表的组合框控件。

## <a name="syntax"></a>语法

```
class CMFCFontComboBox : public CComboBox
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC方康博盒：CMFC方康博盒](#cmfcfontcombobox)|构造 `CMFCFontComboBox` 对象。|
|`CMFCFontComboBox::~CMFCFontComboBox`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|`CMFCFontComboBox::CompareItem`|由框架调用以确定当前字体组合框控件的排序列表框中新项目的相对位置。 （覆盖[CComboBox：比较项目](../../mfc/reference/ccombobox-class.md#compareitem).）|
|`CMFCFontComboBox::DrawItem`|由框架调用以在当前字体组合框控件中绘制指定项。 （覆盖[CComboBox：:D原始项目](../../mfc/reference/ccombobox-class.md#drawitem).）|
|[CMFC方康博盒：：获取塞尔方特](#getselfont)|检索有关当前所选字体的信息。|
|`CMFCFontComboBox::MeasureItem`|由框架调用，以通知 Windows 当前字体组合框控件中列表框的尺寸。 （覆盖[CComboBox：测量项](../../mfc/reference/ccombobox-class.md#measureitem).）|
|`CMFCFontComboBox::PreTranslateMessage`|在窗口消息发送到[翻译消息](/windows/win32/api/winuser/nf-winuser-translatemessage)和[调度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)窗口功能之前进行翻译。 （重写 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。）|
|[CMFC方博博信箱：：选择字体](#selectfont)|从字体组合框中选择与指定条件匹配的字体。|
|[CMFCFontCombox：设置](#setup)|初始化字体组合框中的项目列表。|

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[CMFCFontComboBox：m_bDrawUsingFont](#m_bdrawusingfont)|指示框架在当前字体组合框中用于绘制项目标签的字体。|

## <a name="remarks"></a>备注

要在`CMFCFontComboBox`对话框中使用对象，向对话框类添加`CMFCFontComboBox`变量。 然后在对话框类`OnInitDialog`的方法中，调用[CMFCFontCombox：：设置](#setup)方法以初始化组合框控件中的项列表。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

[CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)

## <a name="requirements"></a>要求

**标题：** afxfontcombox.h

## <a name="cmfcfontcomboboxcmfcfontcombobox"></a><a name="cmfcfontcombobox"></a>CMFC方康博盒：CMFC方康博盒

构造 `CMFCFontComboBox` 对象。

```
CMFCFontComboBox();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcfontcomboboxgetselfont"></a><a name="getselfont"></a>CMFC方康博盒：：获取塞尔方特

检索有关当前所选字体的信息。

```
CMFCFontInfo* GetSelFont() const;
```

### <a name="return-value"></a>返回值

指向[CMFCFontInfo 类](../../mfc/reference/cmfcfontinfo-class.md)对象的指针，用于描述字体。 如果在组合框中未选择字体，则可以为 NULL。

### <a name="remarks"></a>备注

## <a name="cmfcfontcomboboxm_bdrawusingfont"></a><a name="m_bdrawusingfont"></a>CMFCFontComboBox：m_bDrawUsingFont

指示框架在当前字体组合框中用于绘制项目标签的字体。

```
static BOOL m_bDrawUsingFont;
```

### <a name="remarks"></a>备注

将此成员设置为 TRUE 以指示框架使用相同的字体绘制每个项目标签。 将此成员设置为 FALSE，以指示框架使用名称与标签相同的字体绘制每个项目标签。 此成员的默认值为 FALSE。

## <a name="cmfcfontcomboboxselectfont"></a><a name="selectfont"></a>CMFC方博博信箱：：选择字体

从字体组合框中选择与指定条件匹配的字体。

```
BOOL SelectFont(CMFCFontInfo* pDesc);

BOOL SelectFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET);
```

### <a name="parameters"></a>参数

*pDesc*<br/>
[在]指向字体描述对象。

*lpsz名称*<br/>
[在]指定字体名称。

*nCharSet*<br/>
[在]指定字符集。 默认值为DEFAULT_CHARSET。 有关详细信息，请参阅`lfCharSet`[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)结构的成员。

### <a name="return-value"></a>返回值

如果字体组合框中的项目与指定的字体描述对象或字体名称和字符集匹配，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

使用此方法可以选择并滚动到字体组合框中对应于指定字体的项目。

### <a name="example"></a>示例

下面的示例演示如何在`SelectFont``CMFCFontComboBox`类中使用 方法。 此示例是["新控件"示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]

## <a name="cmfcfontcomboboxsetup"></a><a name="setup"></a>CMFCFontCombox：设置

初始化字体组合框中的项目列表。

```
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,
    BYTE nCharSet=DEFAULT_CHARSET,
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```

### <a name="parameters"></a>参数

*n字体类型*<br/>
[在]指定字体类型。 默认值是DEVICE_FONTTYPE、RASTER_FONTTYPE和TRUETYPE_FONTTYPE的位组合 （OR）。

*nCharSet*<br/>
[在]指定字体字符集。 默认值为DEFAULT_CHARSET。

*n 皮奇和家庭*<br/>
[在]指定字体间距和族。 默认值为DEFAULT_PITCH。

### <a name="return-value"></a>返回值

如果字体组合框已成功初始化，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法通过枚举当前安装的与指定参数匹配的字体并在字体组合框中插入这些字体名称来初始化字体组合框。

### <a name="example"></a>示例

下面的示例演示如何在`Setup``CMFCFontComboBox`类中使用 方法。 此示例是["新控件"示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCFontInfo 类](../../mfc/reference/cmfcfontinfo-class.md)
