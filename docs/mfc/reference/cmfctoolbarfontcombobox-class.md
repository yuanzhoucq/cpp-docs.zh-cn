---
title: CMFCToolBarFontComboBox 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::GetFontDesc
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::SetFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarFontComboBox [MFC], CMFCToolBarFontComboBox
- CMFCToolBarFontComboBox [MFC], GetFontDesc
- CMFCToolBarFontComboBox [MFC], SetFont
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3826a1a649cf4a2c3f292b660e90384edac2575e
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040085"
---
# <a name="cmfctoolbarfontcombobox-class"></a>CMFCToolBarFontComboBox 类
包含使用户能够选择从系统字体列表的字体的字体的组合框控件的工具栏按钮。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|构造 `CMFCToolBarFontComboBox` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|返回一个指向`CMFCFontInfo`组合框中指定索引的对象。|  
|[CMFCToolBarFontComboBox::SetFont](#setfont)|字体的名称或字体的前缀和字符一套根据或者字体组合框中选择的字体。|  
  
### <a name="data-members"></a>数据成员  
 [CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)  
 字体组合框中字符的高度。  
  
## <a name="remarks"></a>备注  
 若要将字体组合框按钮添加到工具栏，请按照以下步骤：  
  
1.  在父级工具栏资源中保留该按钮的虚拟资源 ID。  
  
2.  构造`CMFCToolBarFontComboBox`对象。  
  
3.  在处理 AFX_WM_RESETTOOLBAR 消息的消息处理程序，将原始按钮替换为新的组合框按钮使用[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)。  
  
4.  同步在组合框中使用选择文档中的字体使用的字体[CMFCToolBarFontComboBox::SetFont](#setfont)方法。  
  
 若要与组合框中选定的字体同步文档的字体，使用[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)方法来检索所选字体的属性并将这些属性用于创建[CFont 类](../../mfc/reference/cfont-class.md)对象。  
  
 字体组合框按钮调用 Win32 函数[EnumFontFamiliesEx](http://msdn.microsoft.com/library/windows/desktop/dd162620)以确定可用于系统的屏幕和打印机字体。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxtoolbarfontcombobox.h  
  
##  <a name="cmfctoolbarfontcombobox"></a>  CMFCToolBarFontComboBox::CMFCToolBarFontComboBox  
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
 [in]*uiID*  
 组合框命令 ID。  
  
 [in]*iImage*  
 工具栏图像的从零开始索引。 映像位于[CMFCToolBarImages 类](../../mfc/reference/cmfctoolbarimages-class.md)对象[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)类维护。  
  
 [in]*nFontType*  
 组合框中包含的字体的类型。 此参数可以是以下值的组合 (布尔 OR):  
  
 是 DEVICE_FONTTYPE  
  
 RASTER_FONTTYPE  
  
 TRUETYPE_FONTTYPE  
  
 [in]*nCharSet*  
 如果设置为 DEFAULT_CHARSET，组合框中包含所有唯一地命名所有字符集中的字体。 （如果存在具有相同名称的两种字体，组合框包含其中之一。）如果设置为有效的字符的设置值，组合框包含仅在指定的字符集中的字体。 请参阅[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)有关可能的字符的列表设置。  
  
 [in]*dwStyle*  
 组合框的样式。 (请参阅[组合框样式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))  
  
 [in]*iWidth*  
 以像素为单位的编辑控件的宽度。  
  
 [in]*nPitchAndFamily*  
 如果设置为 DEFAULT_PITCH，组合框包含无论音调的字体。 如果设置为 FIXED_PITCH 或 VARIABLE_PITCH，组合框包含仅与该音调类型的字体。 当前不支持筛选基于字体系列。  
  
 [out]*pLstFontsExternal*  
 指向[CObList 类](../../mfc/reference/coblist-class.md)对象，用于存储的可用字体。  
  
### <a name="remarks"></a>备注  
 通常情况下，`CMFCToolBarFontComboBox`对象在单个共享存储的可用字体列表`CObList`对象。 如果使用构造函数的第二个重载，并提供指向的有效指针*pLstFontsExternal*，则该`CMFCToolBarFontComboBox`对象将改为填充`CObList`， *pLstFontsExternal*指向以，可用的字体。  
  
### <a name="example"></a>示例  
 下面的示例演示如何构造`CMFCToolBarFontComboBox`对象。 此代码片段属于 [Word Pad 示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]  
  
##  <a name="getfontdesc"></a>  CMFCToolBarFontComboBox::GetFontDesc  
 返回一个指向`CMFCFontInfo`组合框中指定索引的对象。  
  
```  
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>参数  
 [in]*iIndex*  
 指定组合框项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 指向的指针`CMFCFontInfo`对象。 如果*iIndex*未指定一个有效的项的索引，则返回值是`NULL`。  
  
##  <a name="m_nfontheight"></a>  CMFCToolBarFontComboBox::m_nFontHeight  
 指定高度，以像素为单位，字体组合框中，如果组合框的所有者绘制样式中的字符。  
  
```  
static int m_nFontHeight  
```  
  
### <a name="remarks"></a>备注  
 如果`m_nFontHeight`变量为 0，则根据组合框的默认字体自动计算高度。 高度包括两个字符在基线上方的上升和基线下方的字符的下降。  
  
##  <a name="setfont"></a>  CMFCToolBarFontComboBox::SetFont  
 在参数中指定的字体名称和字符根据字体组合框中的字体设置的选择。  
  
```  
BOOL SetFont(
    LPCTSTR lpszName,  
    BYTE nCharSet=DEFAULT_CHARSET,  
    BOOL bExact=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in]*lpszName*  
 指定的字体名称或前缀。  
  
 [in]*nCharSet*  
 指定的字符集。  
  
 [in]*bExact*  
 指定是否*lpszName*包含字体名称或字体前缀。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功，则选择字体否则为 0。  
  
### <a name="remarks"></a>备注  
 如果*bExact*是`TRUE`，此方法选择与你指定为的名称完全匹配的字体*lpszName*。 如果*bExact*是`FALSE`，此方法选择指定为文本开头的字体*lpszName*并使用指定为字符集*nCharSet*. 如果*nCharSet*设置到 DEFAULT_CHARSET，字符集将被忽略，并且只*lpszName*将用于选择字体的字体。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton 类](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCFontInfo 类](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)



