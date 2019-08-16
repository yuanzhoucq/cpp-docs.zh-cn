---
title: CMFCToolBarFontComboBox 类
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::GetFontDesc
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::SetFont
helpviewer_keywords:
- CMFCToolBarFontComboBox [MFC], CMFCToolBarFontComboBox
- CMFCToolBarFontComboBox [MFC], GetFontDesc
- CMFCToolBarFontComboBox [MFC], SetFont
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
ms.openlocfilehash: 7e19fc9257c1fe986ff09a8bbc86bf2fb55af7ee
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504734"
---
# <a name="cmfctoolbarfontcombobox-class"></a>CMFCToolBarFontComboBox 类

包含组合框控件的工具栏按钮, 该控件使用户能够从系统字体列表中选择一种字体。

## <a name="syntax"></a>语法

```
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|name|描述|
|----------|-----------------|
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|构造 `CMFCToolBarFontComboBox` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|返回一个指向组合框`CMFCFontInfo`中指定索引的对象的指针。|
|[CMFCToolBarFontComboBox::SetFont](#setfont)|根据字体的名称或字体的前缀和字符集, 在 "字体" 组合框中选择一种字体。|

### <a name="data-members"></a>数据成员

[CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)<br/>
字体组合框中字符的高度。

## <a name="remarks"></a>备注

若要将字体组合框按钮添加到工具栏, 请执行以下步骤:

1. 在父级工具栏资源中保留该按钮的虚拟资源 ID。

1. `CMFCToolBarFontComboBox`构造对象。

1. 在处理 AFX_WM_RESETTOOLBAR 消息的消息处理程序中, 使用[CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)将原始按钮替换为新组合框按钮。

1. 使用[CMFCToolBarFontComboBox:: SetFont](#setfont)方法同步在组合框中选择的字体和文档中的字体。

若要使用组合框中所选的字体同步文档字体, 请使用[CMFCToolBarFontComboBox:: GetFontDesc](#getfontdesc)方法检索选定字体的属性, 并使用这些属性创建[CFont 类](../../mfc/reference/cfont-class.md)对象。

字体组合框按钮调用 Win32 函数[EnumFontFamiliesEx](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesexw) , 以确定可用于系统的屏幕和打印机字体。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

## <a name="requirements"></a>要求

**标头:** afxtoolbarfontcombobox

##  <a name="cmfctoolbarfontcombobox"></a>CMFCToolBarFontComboBox::CMFCToolBarFontComboBox

构造[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)对象。

```
public:
CMFCToolBarFontComboBox(
    UINT uiID,
    int iImage,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    DWORD dwStyle = CBS_DROPDOWN,
    int iWidth = 0,
    BYTE nPitchAndFamily = DEFAULT_PITCH);

protected:
CMFCToolBarFontComboBox(
    CObList* pLstFontsExternal,
    int nFontType,
    BYTE nCharSet,
    BYTE nPitchAndFamily);

CMFCToolBarFontComboBox();
```

### <a name="parameters"></a>参数

*uiID*<br/>
中组合框的命令 ID。

*iImage*<br/>
中工具栏图像的从零开始的索引。 该图像位于[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)维护的[CMFCToolBarImages 类](../../mfc/reference/cmfctoolbarimages-class.md)对象中。

*nFontType*<br/>
中组合框包含的字体类型。 此参数可以是下列值的组合 (布尔值或):

DEVICE_FONTTYPE

RASTER_FONTTYPE

TRUETYPE_FONTTYPE

*nCharSet*<br/>
中如果设置为 DEFAULT_CHARSET, 则组合框包含所有字符集中所有唯一命名的字体。 (如果两个字体具有相同的名称, 组合框会包含其中一种。)如果设置为有效的字符集值, 组合框只包含指定字符集中的字体。 有关可能的字符集的列表, 请参阅[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) 。

*dwStyle*<br/>
中组合框的样式。 (请参见[组合框样式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))

*iWidth*<br/>
中编辑控件的宽度 (以像素为单位)。

*nPitchAndFamily*<br/>
中如果设置为 DEFAULT_PITCH, 组合框将包含字体, 而不考虑间距。 如果设置为 "FIXED_PITCH" 或 "VARIABLE_PITCH", 则组合框仅包含具有该螺距类型的字体。 当前不支持基于字体系列的筛选。

*pLstFontsExternal*<br/>
弄指向存储可用字体的[CObList 类](../../mfc/reference/coblist-class.md)对象的指针。

### <a name="remarks"></a>备注

通常, `CMFCToolBarFontComboBox`对象会在单个共享`CObList`对象中存储可用字体的列表。 如果使用构造函数的第二个重载, 并提供指向*pLstFontsExternal*的有效指针, `CMFCToolBarFontComboBox`则该对象`CObList`将改为使用可用字体填充*pLstFontsExternal*指向的内容。

### <a name="example"></a>示例

下面的示例演示如何构造`CMFCToolBarFontComboBox`对象。 此代码片段属于 [Word Pad 示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]

##  <a name="getfontdesc"></a>  CMFCToolBarFontComboBox::GetFontDesc

返回一个指向组合框`CMFCFontInfo`中指定索引的对象的指针。

```
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;
```

### <a name="parameters"></a>参数

*iIndex*<br/>
中指定组合框项的从零开始的索引。

### <a name="return-value"></a>返回值

指向 `CMFCFontInfo` 对象的指针。 如果*iIndex*未指定有效的项索引, 则返回值为 NULL。

##  <a name="m_nfontheight"></a>CMFCToolBarFontComboBox::m_nFontHeight

如果组合框具有所有者绘制样式, 则指定字体组合框中字符的高度 (以像素为单位)。

```
static int m_nFontHeight
```

### <a name="remarks"></a>备注

`m_nFontHeight`如果变量是 0, 则会根据组合框的默认字体自动计算高度。 高度包括基线上方的字符的上移量和基线下的字符的下降量。

##  <a name="setfont"></a>CMFCToolBarFontComboBox::SetFont

根据参数中指定的字体名称和字符集, 在 "字体" 组合框中选择字体。

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET,
    BOOL bExact=FALSE);
```

### <a name="parameters"></a>参数

*lpszName*<br/>
中指定字体名称或前缀。

*nCharSet*<br/>
中指定字符集。

*bExact*<br/>
中指定*lpszName*是否包含字体名称或字体前缀。

### <a name="return-value"></a>返回值

如果成功选择字体, 则为非零值;否则为0。

### <a name="remarks"></a>备注

如果*bExact*为 TRUE, 则此方法将选择与指定为*lpszName*的名称完全匹配的字体。 如果*bExact*为 FALSE, 此方法将选择一个字体, 该字体以指定为*lpszName*的文本开头, 并使用指定为*nCharSet*的字符集。 如果将*nCharSet*设置为 DEFAULT_CHARSET, 则将忽略字符集, 并且仅将*lpszName*用于选择字体。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton 类](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo 类](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[演练：将控件添加到工具栏](../../mfc/walkthrough-putting-controls-on-toolbars.md)
