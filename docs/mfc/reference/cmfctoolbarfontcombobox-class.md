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
ms.openlocfilehash: 7b31f4b725a6983171162d9805d08224ad787808
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360464"
---
# <a name="cmfctoolbarfontcombobox-class"></a>CMFCToolBarFontComboBox 类

包含组合框控件的工具栏按钮，使用户能够从系统字体列表中选择字体。

## <a name="syntax"></a>语法

```
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[CMFCToolBarFontBox：CMFCToolBarFontCombox](#cmfctoolbarfontcombobox)|构造 `CMFCToolBarFontComboBox` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCToolBarFontComboBox：：获取丰得斯克](#getfontdesc)|返回指向组合框中指定`CMFCFontInfo`索引对象的指针。|
|[CMFCToolBarFontBox：：SetFont](#setfont)|根据字体的名称或字体的前缀和字符集在字体组合框中选择字体。|

### <a name="data-members"></a>数据成员

[CMFCToolBarFontComboBox：：m_nFontHeight](#m_nfontheight)<br/>
字体组合框中字符的高度。

## <a name="remarks"></a>备注

要向工具栏添加字体组合框按钮，请按照以下步骤操作：

1. 在父级工具栏资源中保留该按钮的虚拟资源 ID。

1. 构造`CMFCToolBarFontComboBox`对象。

1. 在处理AFX_WM_RESETTOOLBAR消息的消息处理程序中，使用[CMFCToolBar：：：替换Button，](../../mfc/reference/cmfctoolbar-class.md#replacebutton)将原始按钮替换为新的组合框按钮。

1. 使用[CMFCToolBarFontCombox：：setFont](#setfont)方法，将组合框中选择的字体与文档中的字体同步。

若要将文档的字体与组合框中选择的字体同步，请使用[CMFCToolBarFontComboBox：：GetFontDesc](#getfontdesc)方法检索所选字体的属性，并使用这些属性创建[CFont 类](../../mfc/reference/cfont-class.md)对象。

字体组合框按钮调用 Win32 功能[EnumFontSeEx](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesexw)以确定系统可用的屏幕和打印机字体。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComBox按钮](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

## <a name="requirements"></a>要求

**标题：** afxtoolbarfontcombox.h

## <a name="cmfctoolbarfontcomboboxcmfctoolbarfontcombobox"></a><a name="cmfctoolbarfontcombobox"></a>CMFCToolBarFontBox：CMFCToolBarFontCombox

构造[CMFCToolBarFontCombox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)对象。

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
[在]组合框的命令 ID。

*i图像*<br/>
[在]工具栏图像的零基索引。 图像位于[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)维护的[CMFCToolBar 图像类](../../mfc/reference/cmfctoolbarimages-class.md)对象中。

*n字体类型*<br/>
[在]组合框包含的字体类型。 此参数可以是以下值的组合（布尔或）：

DEVICE_FONTTYPE

RASTER_FONTTYPE

TRUETYPE_FONTTYPE

*nCharSet*<br/>
[在]如果设置为DEFAULT_CHARSET，组合框包含所有字符集中的所有唯一命名字体。 （如果有两个具有相同名称的字体，则组合框包含其中一种字体。如果设置为有效的字符集值，组合框仅包含指定字符集中的字体。 有关可能的字符集的列表，请参阅[LOGFONT。](/windows/win32/api/wingdi/ns-wingdi-logfontw)

*dwStyle*<br/>
[在]组合框的样式。 （请参阅[组合盒样式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)）

*iWidth*<br/>
[在]编辑控件的宽度（以像素为单位）。

*n 皮奇和家庭*<br/>
[在]如果设置为DEFAULT_PITCH，组合框包含字体，而不考虑间距。 如果设置为FIXED_PITCH或VARIABLE_PITCH，组合框仅包含具有该间距类型的字体。 当前不支持基于字体系列进行筛选。

*pLstFonts 外部*<br/>
[出]指向存储可用字体的[CObList 类](../../mfc/reference/coblist-class.md)对象的指针。

### <a name="remarks"></a>备注

通常，`CMFCToolBarFontComboBox`对象将可用字体列表存储在单个共享`CObList`对象中。 如果使用构造函数的第二个重载并提供指向*pLstFonts 外部*的有效指针，则该`CMFCToolBarFontComboBox`对象将改为用可用字体`CObList`填充该*pLstFonts 外部*点。

### <a name="example"></a>示例

下面的示例演示如何构造`CMFCToolBarFontComboBox`对象。 此代码片段属于 [Word Pad 示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]

## <a name="cmfctoolbarfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a>CMFCToolBarFontComboBox：：获取丰得斯克

返回指向组合框中指定`CMFCFontInfo`索引对象的指针。

```
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[在]指定组合框项的零基索引。

### <a name="return-value"></a>返回值

一个指向 `CMFCFontInfo` 对象的指针。 如果*iIndex*未指定有效的物料索引，则返回值为 NULL。

## <a name="cmfctoolbarfontcomboboxm_nfontheight"></a><a name="m_nfontheight"></a>CMFCToolBarFontComboBox：：m_nFontHeight

如果组合框具有所有者绘制样式，则指定字体组合框中字符的高度（以像素为单位）。

```
static int m_nFontHeight
```

### <a name="remarks"></a>备注

如果`m_nFontHeight`变量为 0，则根据组合框的默认字体自动计算高度。 高度包括基线上方的字符上升和基线下方字符的下降。

## <a name="cmfctoolbarfontcomboboxsetfont"></a><a name="setfont"></a>CMFCToolBarFontBox：：SetFont

根据参数中指定的字体名称和字符集选择字体组合框中的字体。

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET,
    BOOL bExact=FALSE);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
[在]指定字体名称或前缀。

*nCharSet*<br/>
[在]指定字符集。

*b精确*<br/>
[在]指定*lpszName*是否包含字体名称还是字体前缀。

### <a name="return-value"></a>返回值

如果已成功选择字体，则非零;否则 0。

### <a name="remarks"></a>备注

如果*bExact*为 TRUE，则此方法将选择与您指定为*lpszName*的名称完全匹配的字体。 如果*bExact*是 FALSE，则此方法选择以指定为*lpszName*的文本开头并使用指定为*nCharSet*的字符集的字体。 如果*nCharSet*设置为DEFAULT_CHARSET，则字符集将被忽略，并且将仅使用*lpszName*来选择字体。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFC工具栏按钮类](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton 类](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo 类](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFC工具栏：更换按钮](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)
