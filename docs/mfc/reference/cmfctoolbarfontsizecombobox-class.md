---
title: "CMFCToolBarFontSizeComboBox 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- CMFCToolBarFontSizeComboBox class
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 9dddb563617a708bdc8b2193fa5ee8bd10321828
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbarfontsizecombobox-class"></a>CMFCToolBarFontSizeComboBox 类
包含使用户能够选择的字体大小的组合框控件的工具栏按钮。  
  
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
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|以缇返回所选的字体大小。|  
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|用指定的字体的所有受支持的字体大小填充组合框列表。|  
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|设置字体大小，单位为缇。|  
  
## <a name="remarks"></a>备注  
 您可以使用`CMFCToolBarFontSizeComboBox`对象一起[CMFCToolBarFontComboBox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)对象以使用户能够选择字体和字体大小。  
  
 您可以将字体大小组合框按钮添加一个工具栏，就像添加字体组合框按钮。 有关详细信息，请参阅[CMFCToolBarFontComboBox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)。  
  
 当用户选择中的新字体`CMFCToolBarFontComboBox`对象时，可以通过使用支持该字体的大小来填充字体大小组合框[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)方法。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCToolBarFontSizeComboBox`用于配置类`CMFCToolBarFontSizeComboBox`对象。 该示例说明了如何从文本框中检索字体大小，单位为缇、 字体大小组合框填充给定字体的所有有效的大小，并以缇为单位指定的字号。 此代码段属于[Word 板示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad #&8;](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxtoolbarfontcombobox.h  
  
##  <a name="cmfctoolbarfontsizecombobox"></a>CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox  
 构造 `CMFCToolBarFontSizeComboBox` 对象。  
  
```  
CMFCToolBarFontSizeComboBox();
```  
  
##  <a name="gettwipsize"></a>CMFCToolBarFontSizeComboBox::GetTwipSize  
 检索字体大小，单位为缇从字体大小组合框的文本框。  
  
```  
int GetTwipSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果返回值为正，则缇中的字体大小。 如果组合框的文本框为空，则为-1。 如果发生错误，则为-2。  
  
##  <a name="rebuildfontsizes"></a>CMFCToolBarFontSizeComboBox::RebuildFontSizes  
 字体大小组合框填充所有有效的给定字体的大小。  
  
```  
void RebuildFontSizes(const CString& strFontName);
```  
  
### <a name="parameters"></a>参数  
 `[in] strFontName`  
 指定的字体名称。  
  
### <a name="remarks"></a>备注  
 调用此函数，当你想要同步之间的字体组合框中选择和字体大小组合框，如[CMFCToolBarFontComboBox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)。  
  
##  <a name="settwipsize"></a>CMFCToolBarFontSizeComboBox::SetTwipSize  
 将向上舍入指定大小 （以缇为单位） 的最接近的大小以磅为单位，然后设置对应的值组合框中选定的大小。  
  
```  
void SetTwipSize(int nSize);
```  
  
### <a name="parameters"></a>参数  
 [in] `nSize`  
 指定的字体大小 （以缇为单位） 来设置。  
  
### <a name="remarks"></a>备注  
 您可以通过调用以后检索以前的有效的字体大小[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)方法。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton 类](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCFontInfo 类](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [演练︰ 将置于工具栏上的控件](../../mfc/walkthrough-putting-controls-on-toolbars.md)




