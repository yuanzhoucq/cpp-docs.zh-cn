---
title: CMFCToolBarFontSizeComboBox 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::GetTwipSize
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::RebuildFontSizes
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::SetTwipSize
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarFontSizeComboBox [MFC], CMFCToolBarFontSizeComboBox
- CMFCToolBarFontSizeComboBox [MFC], GetTwipSize
- CMFCToolBarFontSizeComboBox [MFC], RebuildFontSizes
- CMFCToolBarFontSizeComboBox [MFC], SetTwipSize
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 53f87dd55373599f8ab8394284a6271930b9fcd6
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037504"
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
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|设置字体大小单位为缇。|  
  
## <a name="remarks"></a>备注  
 你可以使用`CMFCToolBarFontSizeComboBox`对象连同[CMFCToolBarFontComboBox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)对象，使用户能够选择字体和字号。  
  
 就像添加字体组合框按钮，你可以将字体大小组合框按钮添加到工具栏。 有关详细信息，请参阅[CMFCToolBarFontComboBox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)。  
  
 当用户选择中的新字体`CMFCToolBarFontComboBox`对象，可以通过使用支持该字体的大小来填充字体大小组合框[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)方法。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCToolBarFontSizeComboBox`用于配置类`CMFCToolBarFontSizeComboBox`对象。 该示例说明如何从文本框中检索的字体大小，单位为缇、 填充所有有效大小为给定字体的字体大小组合框和以缇为单位指定字体大小。 此代码片段属于 [Word Pad 示例](../../visual-cpp-samples.md)。  
  
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
 从的字体大小组合框的文本框中检索的字体大小，单位为缇。  
  
```  
int GetTwipSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果返回值为正，它是以缇为单位的字体大小。 如果组合框的文本框为空，则为-1。 如果错误发生，则为-2。  
  
##  <a name="rebuildfontsizes"></a>  CMFCToolBarFontSizeComboBox::RebuildFontSizes  
 填充所有有效大小为给定字体的字体大小组合框。  
  
```  
void RebuildFontSizes(const CString& strFontName);
```  
  
### <a name="parameters"></a>参数  
 [in]*strFontName*  
 指定的字体名称。  
  
### <a name="remarks"></a>备注  
 调用此函数，当你想要同步之间的字体组合框中选定和字体大小组合框，如[CMFCToolBarFontComboBox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)。  
  
##  <a name="settwipsize"></a>  CMFCToolBarFontSizeComboBox::SetTwipSize  
 将向上舍入指定大小 （以缇为单位） 的最接近的大小以点，然后设置与此值组合框中的所选的大小。  
  
```  
void SetTwipSize(int nSize);
```  
  
### <a name="parameters"></a>参数  
 [in]*nSize*  
 指定的字体大小 （以缇为单位） 设置。  
  
### <a name="remarks"></a>备注  
 你可以通过调用更高版本检索以前的有效字号[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)方法。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton 类](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCFontInfo 类](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)



