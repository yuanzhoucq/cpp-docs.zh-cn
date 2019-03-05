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
ms.openlocfilehash: a1dd85ed7bf80f5307bf0bd07ef5ef74875c8562
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258939"
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>CMFCToolBarFontSizeComboBox 类

包含使用户能够选择字体大小的组合框控件的工具栏按钮。

## <a name="syntax"></a>语法

```
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|描述|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox](#cmfctoolbarfontsizecombobox)|构造 `CMFCToolBarFontSizeComboBox` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|返回以缇为单位的所选的字体大小。|
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|用指定的字体的所有受支持的字体大小填充组合框列表。|
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|设置字体大小，单位为缇。|

## <a name="remarks"></a>备注

可以使用`CMFCToolBarFontSizeComboBox`对象一起[CMFCToolBarFontComboBox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)对象以使用户能够选择字体和字体大小。

可以将字体大小组合框按钮添加到工具栏，就像添加字体组合框按钮。 有关详细信息，请参阅[CMFCToolBarFontComboBox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)。

当用户选择中的新字体`CMFCToolBarFontComboBox`对象，可以通过使用该字体的受支持的大小来填充字体大小组合框[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)方法。

## <a name="example"></a>示例

下面的示例演示如何使用中的各种方法`CMFCToolBarFontSizeComboBox`类，以配置`CMFCToolBarFontSizeComboBox`对象。 该示例演示了如何从文本框中检索的字体大小，以缇为单位、 字体大小组合框填充所有有效大小的给定字体，并以缇为单位指定字体大小。 此代码片段属于 [Word Pad 示例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)

## <a name="requirements"></a>要求

**标头：** afxtoolbarfontcombobox.h

##  <a name="cmfctoolbarfontsizecombobox"></a>  CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox

构造 `CMFCToolBarFontSizeComboBox` 对象。

```
CMFCToolBarFontSizeComboBox();
```

##  <a name="gettwipsize"></a>  CMFCToolBarFontSizeComboBox::GetTwipSize

检索从字体大小组合框的文本框字体大小，单位为缇。

```
int GetTwipSize() const;
```

### <a name="return-value"></a>返回值

如果返回值为正，则以缇为单位的字号。 如果组合框的文本框为空，则为-1。 如果发生错误，它为-2。

##  <a name="rebuildfontsizes"></a>  CMFCToolBarFontSizeComboBox::RebuildFontSizes

填充所有有效大小的给定字体的字体大小组合框。

```
void RebuildFontSizes(const CString& strFontName);
```

### <a name="parameters"></a>参数

*strFontName*<br/>
[in]指定的字体名称。

### <a name="remarks"></a>备注

调用此函数，当你想要同步之间字体组合框中的选择和字体大小的组合框中，如[CMFCToolBarFontComboBox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)。

##  <a name="settwipsize"></a>  CMFCToolBarFontSizeComboBox::SetTwipSize

将向上舍入指定大小 （以缇为单位） 到最接近大小以磅为单位，并设置为该值在组合框中的所选的大小。

```
void SetTwipSize(int nSize);
```

### <a name="parameters"></a>参数

*nSize*<br/>
[in]指定的字体大小 （以缇为单位） 设置。

### <a name="remarks"></a>备注

您可以通过调用稍后检索上一个有效的字体大小[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)方法。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton 类](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo 类](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)
