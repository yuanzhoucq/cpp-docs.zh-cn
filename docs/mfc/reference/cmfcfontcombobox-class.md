---
title: "CMFCFontComboBox 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::GetSelFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::SelectFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::Setup
- AFXFONTCOMBOBOX/CMFCFontComboBox::m_bDrawUsingFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCFontComboBox::DrawItem method
- CMFCFontComboBox::PreTranslateMessage method
- CMFCFontComboBox::MeasureItem method
- CMFCFontComboBox class
- CMFCFontComboBox::CompareItem method
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
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
ms.openlocfilehash: 1252f5ca102637e70cc384afd723464aec4144b4
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcfontcombobox-class"></a>CMFCFontComboBox 类
`CMFCFontComboBox`类创建包含字体列表的一个组合框控件。  
  
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
  
|名称|说明|  
|----------|-----------------|  
|`CMFCFontComboBox::CompareItem`|由框架来确定新项的当前字体组合框控件的已排序的列表框中的相对位置调用。 (重写[CComboBox::CompareItem](../../mfc/reference/ccombobox-class.md#compareitem)。)|  
|`CMFCFontComboBox::DrawItem`|由当前的字体组合框控件中绘制指定的项的框架调用。 (重写[CComboBox::DrawItem](../../mfc/reference/ccombobox-class.md#drawitem)。)|  
|[CMFCFontComboBox::GetSelFont](#getselfont)|检索有关当前所选字体信息。|  
|`CMFCFontComboBox::MeasureItem`|由框架来通知 Windows 列表框中当前的字体组合框控件中的维度的调用。 (重写[CComboBox::MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem)。)|  
|`CMFCFontComboBox::PreTranslateMessage`|翻译窗口消息之前被发送到[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函数。 (重写[cwnd:: Pretranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|  
|[CMFCFontComboBox::SelectFont](#selectfont)|选择符合指定的条件后从字体组合框中的字体。|  
|[CMFCFontComboBox::Setup](#setup)|初始化字体组合框中项的列表。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|框架中，指示哪种字体用于绘制当前字体组合框中的项标签。|  
  
## <a name="remarks"></a>备注  
 若要使用`CMFCFontComboBox`对象在对话框中，将添加`CMFCFontComboBox`到对话框类变量。 然后在`OnInitDialog`方法的对话框类，调用[CMFCFontComboBox::Setup](#setup)方法以初始化组合框控件中项的列表。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CComboBox](../../mfc/reference/ccombobox-class.md)  
  
 [CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxfontcombobox.h  
  
##  <a name="cmfcfontcombobox"></a>CMFCFontComboBox::CMFCFontComboBox  
 构造 `CMFCFontComboBox` 对象。  
  
```  
CMFCFontComboBox();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getselfont"></a>CMFCFontComboBox::GetSelFont  
 检索有关当前所选字体信息。  
  
```  
CMFCFontInfo* GetSelFont() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CMFCFontInfo 类](../../mfc/reference/cmfcfontinfo-class.md)对象，它描述一种字体。 它可以是`NULL`如果在组合框中选择的字体。  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_bdrawusingfont"></a>CMFCFontComboBox::m_bDrawUsingFont  
 框架中，指示哪种字体用于绘制当前字体组合框中的项标签。  
  
```  
static BOOL m_bDrawUsingFont;  
```  
  
### <a name="remarks"></a>备注  
 将此成员设置为`TRUE`来指示要使用相同的字体绘制每个项目标签的框架。 将此成员设置为`FALSE`来指示要绘制用其名称是标签相同字体每个项目标签的框架。 此成员的默认值是`FALSE`。  
  
##  <a name="selectfont"></a>CMFCFontComboBox::SelectFont  
 选择符合指定的条件后从字体组合框中的字体。  
  
```  
BOOL SelectFont(CMFCFontInfo* pDesc);

 
BOOL SelectFont(
    LPCTSTR lpszName,  
    BYTE nCharSet=DEFAULT_CHARSET);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDesc`  
 指向字体描述对象。  
  
 [in] `lpszName`  
 指定的字体名称。  
  
 [in] `nCharSet`  
 指定的字符集。 默认值为 DEFAULT_CHARSET。 有关详细信息，请参阅`lfCharSet`的成员[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)结构。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果字体组合框中的某项匹配的描述对象，指定的字体或字体名称和字符集;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用此方法来选择并滚动到对应于指定的字体的字体组合框中的项。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`SelectFont`中的方法`CMFCFontComboBox`类。 此示例摘自[新控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&34;](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls #&35;](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]  
  
##  <a name="setup"></a>CMFCFontComboBox::Setup  
 初始化字体组合框中项的列表。  
  
```  
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,  
    BYTE nCharSet=DEFAULT_CHARSET,  
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```  
  
### <a name="parameters"></a>参数  
 [in] `nFontType`  
 指定字体类型。 默认值为 DEVICE_FONTTYPE、 RASTER_FONTTYPE 和 TRUETYPE_FONTTYPE 的按位组合 (OR)。  
  
 [in] `nCharSet`  
 指定字体字符组。 默认值为 DEFAULT_CHARSET。  
  
 [in] `nPitchAndFamily`  
 指定的字体间距和系列。 默认值为 DEFAULT_PITCH。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则初始化字体组合框否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法通过枚举与指定的参数匹配的当前已安装的字体和字体组合框中插入这些字体名称初始化字体组合框。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`Setup`中的方法`CMFCFontComboBox`类。 此示例摘自[新控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&34;](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls #&36;](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarFontComboBox 类](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [CMFCFontInfo 类](../../mfc/reference/cmfcfontinfo-class.md)

