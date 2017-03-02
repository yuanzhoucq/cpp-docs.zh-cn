---
title: "CMFCToolBarFontComboBox 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarFontComboBox
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarFontComboBox class
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
caps.latest.revision: 29
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 50b22e19cab4f434ec53383c8a170344e89cbab0
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbarfontcombobox-class"></a>CMFCToolBarFontComboBox 类
包含使用户能够从系统字体的列表中选择一种字体组合框控件的工具栏按钮。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|构造 `CMFCToolBarFontComboBox` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|返回一个指向`CMFCFontInfo`为组合框中指定的索引的对象。|  
|[CMFCToolBarFontComboBox::SetFont](#setfont)|该字体的名称或字体的前缀和字符一套根据任何一个字体组合框中选择一种字体。|  
  
### <a name="data-members"></a>数据成员  
 [CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)  
 字体组合框中字符的高度。  
  
## <a name="remarks"></a>备注  
 若要将字体组合框按钮添加到工具栏，请按照下列步骤︰  
  
1.  在父级工具栏资源中保留该按钮的虚拟资源 ID。  
  
2.  构造`CMFCToolBarFontComboBox`对象。  
  
3.  在处理该消息处理程序`AFX_WM_RESETTOOLBAR`消息，将原始按钮替换为新的组合框按钮通过使用[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)。  
  
4.  同步是组合框中选定文档的字体使用的字体[CMFCToolBarFontComboBox::SetFont](#setfont)方法。  
  
 若要同步与字体组合框中选定文档的字体，请使用[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)方法来检索所选字体属性并使用这些属性来创建[CFont 类](../../mfc/reference/cfont-class.md)对象。  
  
 字体组合框按钮调用 Win32 函数[EnumFontFamiliesEx](http://msdn.microsoft.com/library/windows/desktop/dd162620)来确定可用于系统的屏幕和打印机字体。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxtoolbarfontcombobox.h  
  
##  <a name="a-namecmfctoolbarfontcomboboxa--cmfctoolbarfontcomboboxcmfctoolbarfontcombobox"></a><a name="cmfctoolbarfontcombobox"></a>CMFCToolBarFontComboBox::CMFCToolBarFontComboBox  
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
 [in] `uiID`  
 组合框的命令 ID。  
  
 [in] `iImage`  
 工具栏图像的从零开始索引。 图像位于[CMFCToolBarImages 类](../../mfc/reference/cmfctoolbarimages-class.md)对象[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)类维护。  
  
 [in] `nFontType`  
 组合框中包含的字体的类型。 此参数可以是以下值的组合 (布尔 OR):  
  
 DEVICE_FONTTYPE  
  
 RASTER_FONTTYPE  
  
 TRUETYPE_FONTTYPE  
  
 [in] `nCharSet`  
 如果设置为 DEFAULT_CHARSET，组合框中包含所有唯一地命名所有字符集中的字体。 （如果有一个同名的两种字体，组合框包含其中之一。）如果设置为有效的字符的设置值，组合框包含仅在指定的字符集中的字体。 请参阅[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)有关的可能的字符列表设置。  
  
 [in] `dwStyle`  
 组合框的样式。 (请参阅[组合框样式](../../mfc/reference/combo-box-styles.md))  
  
 [in] `iWidth`  
 以像素为单位的编辑控件的宽度。  
  
 [in] `nPitchAndFamily`  
 如果设置为 DEFAULT_PITCH，组合框中包含字体而不考虑音调。 如果设置为 FIXED_PITCH 或 VARIABLE_PITCH，组合框包含仅与该音调类型的字体。 当前不支持基于字体系列的筛选。  
  
 [out] `pLstFontsExternal`  
 指向[CObList 类](../../mfc/reference/coblist-class.md)对象，它存储可用的字体。  
  
### <a name="remarks"></a>备注  
 通常情况下，`CMFCToolBarFontComboBox`对象存储在单个共享的可用字体列表`CObList`对象。 如果使用构造函数的第二个重载，并提供指向的有效指针`pLstFontsExternal`，则该`CMFCToolBarFontComboBox`对象将改为填满`CObList`，`pLstFontsExternal`指向具有可用的字体。  
  
### <a name="example"></a>示例  
 下面的示例演示如何构造`CMFCToolBarFontComboBox`对象。 此代码段属于[Word 板示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad #&7;](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]  
  
##  <a name="a-namegetfontdesca--cmfctoolbarfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a>CMFCToolBarFontComboBox::GetFontDesc  
 返回一个指向`CMFCFontInfo`为组合框中指定的索引的对象。  
  
```  
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iIndex`  
 指定组合框项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 一个指向`CMFCFontInfo`对象。 如果`iIndex`未指定一个有效的项的索引，则返回值是`NULL`。  
  
##  <a name="a-namemnfontheighta--cmfctoolbarfontcomboboxmnfontheight"></a><a name="m_nfontheight"></a>CMFCToolBarFontComboBox::m_nFontHeight  
 指定高度，以像素为单位，如果组合框中有所有者绘制样式的字体组合框中的字符。  
  
```  
static int m_nFontHeight  
```  
  
### <a name="remarks"></a>备注  
 如果`m_nFontHeight`变量为 0，则根据默认字体组合框的自动计算的高度。 高度包括两个字符在基线上方的上升和字符基线下方的下降。  
  
##  <a name="a-namesetfonta--cmfctoolbarfontcomboboxsetfont"></a><a name="setfont"></a>CMFCToolBarFontComboBox::SetFont  
 在参数中指定的选择根据字体名称和字符的字体组合框中的字体设置。  
  
```  
BOOL SetFont(
    LPCTSTR lpszName,  
    BYTE nCharSet=DEFAULT_CHARSET,  
    BOOL bExact=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszName`  
 指定字体名称的前缀。  
  
 [in] `nCharSet`  
 指定的字符集。  
  
 [in] `bExact`  
 指定是否`lpszName`包含字体名称或字体前缀。  
  
### <a name="return-value"></a>返回值  
 如果成功，则选择该字体，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 如果`bExact`是`TRUE`，此方法将选择与您指定为的名称完全匹配一字体`lpszName`。 如果`bExact`是`FALSE`，此方法选择开头为指定的文本的字体`lpszName`，并使用指定为字符集`nCharSet`。 如果`nCharSet`设置到 DEFAULT_CHARSET，字符集将被忽略，并且只`lpszName`将用于选择一种字体。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton 类](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCFontInfo 类](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [演练︰ 将置于工具栏上的控件](../../mfc/walkthrough-putting-controls-on-toolbars.md)




