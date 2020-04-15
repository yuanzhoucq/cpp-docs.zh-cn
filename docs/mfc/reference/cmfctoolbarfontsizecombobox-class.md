---
title: CMFCToolBarFontSizeComboBox 类
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::GetTwipSize
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::RebuildFontSizes
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::SetTwipSize
helpviewer_keywords:
- CMFCToolBarFontSizeComboBox [MFC], CMFCToolBarFontSizeComboBox
- CMFCToolBarFontSizeComboBox [MFC], GetTwipSize
- CMFCToolBarFontSizeComboBox [MFC], RebuildFontSizes
- CMFCToolBarFontSizeComboBox [MFC], SetTwipSize
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
ms.openlocfilehash: 09811b14ed805b1965015a32a25c0b67c947ff4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358310"
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>CMFCToolBarFontSizeComboBox 类

包含组合框控件的工具栏按钮，使用户能够选择字体大小。

## <a name="syntax"></a>语法

```
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[CMFCToolBarFontSsCombox：CMFCToolBarFontSscombox](#cmfctoolbarfontsizecombobox)|构造 `CMFCToolBarFontSizeComboBox` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCToolBarFontSsSsBox：：获取Twipsize](#gettwipsize)|以 twips 返回所选字体大小。|
|[CMFCToolBarFontSsBox：：重建字体](#rebuildfontsizes)|使用指定字体的所有支持字体大小填充组合框列表。|
|[CMFCToolBarFontSsSsBox：：SetTwipSize](#settwipsize)|以 twips 设置字体大小。|

## <a name="remarks"></a>备注

您可以将`CMFCToolBarFontSizeComboBox`对象与[CMFCToolBarFontComboBox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)对象一起使用，以使用户能够选择字体和字体大小。

您可以添加字体大小组合框按钮到工具栏，就像添加字体组合框按钮一样。 有关详细信息，请参阅[CMFCToolBarFontCombox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)。

当用户在`CMFCToolBarFontComboBox`对象中选择新字体时，可以使用[CMFCToolBoxSizeComboBox：："重建字体"](#rebuildfontsizes)方法，使用该字体支持的大小填充字体大小组合框。

## <a name="example"></a>示例

下面的示例演示如何在`CMFCToolBarFontSizeComboBox`类中使用各种方法来配置`CMFCToolBarFontSizeComboBox`对象。 该示例演示如何从文本框中检索字体大小（以 twips 形式），使用给定字体的所有有效大小填充字体大小组合框，并在 twips 中指定字体大小。 此代码片段属于 [Word Pad 示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComBox按钮](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontSsComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)

## <a name="requirements"></a>要求

**标题：** afxtoolbarfontcombox.h

## <a name="cmfctoolbarfontsizecomboboxcmfctoolbarfontsizecombobox"></a><a name="cmfctoolbarfontsizecombobox"></a>CMFCToolBarFontSsCombox：CMFCToolBarFontSscombox

构造 `CMFCToolBarFontSizeComboBox` 对象。

```
CMFCToolBarFontSizeComboBox();
```

## <a name="cmfctoolbarfontsizecomboboxgettwipsize"></a><a name="gettwipsize"></a>CMFCToolBarFontSsSsBox：：获取Twipsize

从字体大小组合框的文本框中检索字体大小（以 twips 形式显示）。

```
int GetTwipSize() const;
```

### <a name="return-value"></a>返回值

如果返回值为正，则为 twips 中的字体大小。 如果组合框的文本框为空，则为 -1。 如果发生错误，为 -2。

## <a name="cmfctoolbarfontsizecomboboxrebuildfontsizes"></a><a name="rebuildfontsizes"></a>CMFCToolBarFontSsBox：：重建字体

使用给定字体的所有有效大小填充字体大小组合框。

```
void RebuildFontSizes(const CString& strFontName);
```

### <a name="parameters"></a>参数

*串放大缩小字体功能 放大缩小字体功能*<br/>
[在]指定字体名称。

### <a name="remarks"></a>备注

如果要在字体组合框中的选择与字体大小组合框（如[CMFCToolBarFontCombox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)）之间进行同步，请调用此功能。

## <a name="cmfctoolbarfontsizecomboboxsettwipsize"></a><a name="settwipsize"></a>CMFCToolBarFontSsSsBox：：SetTwipSize

将指定大小（以 twips 为单位）舍入到最近的大小（以磅为单位），然后将组合框中的选定大小设置为该值。

```
void SetTwipSize(int nSize);
```

### <a name="parameters"></a>参数

*nSize*<br/>
[在]指定要设置的字体大小（以 twips 表示）。

### <a name="remarks"></a>备注

稍后，您可以通过调用[CMFCToolBarFontSizeComboBox：：GetTwipSize](#gettwipsize)方法来检索以前的有效字体大小。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFC工具栏按钮类](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton 类](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo 类](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFC工具栏：更换按钮](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)
