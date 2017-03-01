---
title: "CMFCPropertyGridCtrl Class |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPropertyGridCtrl
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridCtrl::get_accValue method
- CMFCPropertyGridCtrl::accHitTest method
- CMFCPropertyGridCtrl::get_accState method
- CMFCPropertyGridCtrl::accLocation method
- CMFCPropertyGridCtrl::get_accChild method
- CMFCPropertyGridCtrl::get_accName method
- CMFCPropertyGridCtrl::PreTranslateMessage method
- CMFCPropertyGridCtrl::get_accRole method
- CMFCPropertyGridCtrl::get_accDefaultAction method
- CMFCPropertyGridCtrl class
- CMFCPropertyGridCtrl::get_accDescription method
ms.assetid: 95877cae-2311-4a2a-9031-0c8c3cf0a5f9
caps.latest.revision: 35
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
ms.openlocfilehash: 93611d1b52d6372a81b91f08c5a5c7b215b584e3
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcpropertygridctrl-class"></a>CMFCPropertyGridCtrl Class
[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 支持可以按字母或分层顺序显示属性的可编辑属性网格控件。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCPropertyGridCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCPropertyGridCtrl::CMFCPropertyGridCtrl](#cmfcpropertygridctrl)|构造 `CMFCPropertyGridCtrl` 对象。|  
|`CMFCPropertyGridCtrl::~CMFCPropertyGridCtrl`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|`CMFCPropertyGridCtrl::accHitTest`|由框架调用以检索屏幕上给定点处的子元素或子对象。 (重写[CWnd::accHitTest](../../mfc/reference/cwnd-class.md#acchittest)。)|  
|`CMFCPropertyGridCtrl::accLocation`|由框架调用以检索指定对象的当前屏幕位置。 (重写[CWnd::accLocation](../../mfc/reference/cwnd-class.md#acclocation)。)|  
|[CMFCPropertyGridCtrl::accSelect](#accselect)|由框架调用以修改选定内容或移动指定对象的键盘焦点。 (重写[CWnd::accSelect](../../mfc/reference/cwnd-class.md#accselect)。)|  
|[CMFCPropertyGridCtrl::AddProperty](#addproperty)|将新属性添加到属性网格控件。|  
|[CMFCPropertyGridCtrl::AlwaysShowUserToolTip](#alwaysshowusertooltip)||  
|[CMFCPropertyGridCtrl::CloseColorPopup](#closecolorpopup)|关闭颜色选择对话框。|  
|[CMFCPropertyGridCtrl::Create](#create)|创建属性网格控件，并将其附加到属性网格控件对象。|  
|[CMFCPropertyGridCtrl::DeleteProperty](#deleteproperty)|从属性网格控件中删除指定的属性。|  
|[CMFCPropertyGridCtrl::DrawControlBarColors](#drawcontrolbarcolors)||  
|[CMFCPropertyGridCtrl::EnableDescriptionArea](#enabledescriptionarea)|启用或禁用的属性列表下显示的说明区域。|  
|[CMFCPropertyGridCtrl::EnableHeaderCtrl](#enableheaderctrl)|启用或禁用在属性网格控件顶部标头控件。|  
|[CMFCPropertyGridCtrl::EnsureVisible](#ensurevisible)|执行滚动操作使得在属性网格控件，并扩展属性项，直到指定的属性可见。|  
|[CMFCPropertyGridCtrl::ExpandAll](#expandall)|展开或折叠属性网格控件的所有节点。|  
|[CMFCPropertyGridCtrl::FindItemByData](#finditembydata)|检索与用户定义相关联的属性`DWORD`值。|  
|`CMFCPropertyGridCtrl::get_accChild`|由框架调用以检索指定子级的 `IDispatch` 接口地址。 (重写[CWnd::get_accChild](../../mfc/reference/cwnd-class.md#get_accchild)。)|  
|[CMFCPropertyGridCtrl::get_accChildCount](#get_accchildcount)|由框架调用调用以检索属于该对象的子级的个数。 (重写[CWnd::get_accChildCount](../../mfc/reference/cwnd-class.md#get_accchildcount)。)|  
|`CMFCPropertyGridCtrl::get_accDefaultAction`|由框架调用以检索描述对象默认操作的字符串。 (重写[CWnd::get_accDefaultAction](../../mfc/reference/cwnd-class.md#get_accdefaultaction)。)|  
|`CMFCPropertyGridCtrl::get_accDescription`|由框架调用以检索描述指定对象的可视外观的字符串。 (重写[CWnd::get_accDescription](../../mfc/reference/cwnd-class.md#get_accdescription)。)|  
|[CMFCPropertyGridCtrl::get_accFocus](#get_accfocus)|由框架调用以检索具有键盘焦点的对象。 (重写[CWnd::get_accFocus](../../mfc/reference/cwnd-class.md#get_accfocus)。)|  
|[CMFCPropertyGridCtrl::get_accHelp](#get_acchelp)|由框架调用以检索对象的`Help`属性字符串。 (重写[CWnd::get_accHelp](../../mfc/reference/cwnd-class.md#get_acchelp)。)|  
|[CMFCPropertyGridCtrl::get_accHelpTopic](#get_acchelptopic)|由框架调用以检索的完整路径`WinHelp`与指定的对象和该文件内的相应主题的标识符关联的文件。 (重写[CWnd::get_accHelpTopic](../../mfc/reference/cwnd-class.md#get_acchelptopic)。)|  
|[CMFCPropertyGridCtrl::get_accKeyboardShortcut](#get_acckeyboardshortcut)|由框架调用以检索指定对象的快捷键或访问键。 (重写[CWnd::get_accKeyboardShortcut](../../mfc/reference/cwnd-class.md#get_acckeyboardshortcut)。)|  
|`CMFCPropertyGridCtrl::get_accName`|由框架调用以检索指定对象的名称。 (重写[CWnd::get_accName](../../mfc/reference/cwnd-class.md#get_accname)。)|  
|`CMFCPropertyGridCtrl::get_accRole`|由框架调用以检索描述指定对象的角色的信息。 (重写[CWnd::get_accRole](../../mfc/reference/cwnd-class.md#get_accrole)。)|  
|[CMFCPropertyGridCtrl::get_accSelection](#get_accselection)|由框架调用以检索该对象的选定子级。 (重写[CWnd::get_accSelection](../../mfc/reference/cwnd-class.md#get_accselection)。)|  
|`CMFCPropertyGridCtrl::get_accState`|由框架调用以检索指定对象的当前状态。 (重写[CWnd::get_accState](../../mfc/reference/cwnd-class.md#get_accstate)。)|  
|`CMFCPropertyGridCtrl::get_accValue`|由框架调用以检索指定对象的值。 (重写[CWnd::get_accValue](../../mfc/reference/cwnd-class.md#get_accvalue)。)|  
|[CMFCPropertyGridCtrl::GetBkColor](#getbkcolor)|检索当前的属性网格控件的背景色。|  
|[CMFCPropertyGridCtrl::GetBoldFont](#getboldfont)|检索 Windows 字体，在当前的属性网格中的文本控件中显示为粗体样式。|  
|[CMFCPropertyGridCtrl::GetCurSel](#getcursel)|检索当前所选的属性。|  
|[CMFCPropertyGridCtrl::GetCustomColors](#getcustomcolors)|检索当前为属性网格控件元素定义的自定义颜色。|  
|[CMFCPropertyGridCtrl::GetDescriptionHeight](#getdescriptionheight)|检索位于属性网格控件底部的说明区域的高度。|  
|[CMFCPropertyGridCtrl::GetDescriptionRows](#getdescriptionrows)|检索在说明区域中的当前属性网格控件的行数。|  
|[CMFCPropertyGridCtrl::GetHeaderCtrl](#getheaderctrl)|检索内部[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)对象框架使用，以显示当前的属性网格控件。|  
|[CMFCPropertyGridCtrl::GetHeaderHeight](#getheaderheight)|检索属性网格控件标题的高度。|  
|[CMFCPropertyGridCtrl::GetLeftColumnWidth](#getleftcolumnwidth)|检索包含每个属性的名称的当前属性网格控件左侧的列的宽度。|  
|[CMFCPropertyGridCtrl::GetListRect](#getlistrect)|检索的属性网格控件的边框。|  
|[CMFCPropertyGridCtrl::GetProperty](#getproperty)|检索指向对应的属性网格控件项的指定索引的属性对象的指针。|  
|[CMFCPropertyGridCtrl::GetPropertyColumnWidth](#getpropertycolumnwidth)|检索包含属性值的列的当前宽度。|  
|[CMFCPropertyGridCtrl::GetPropertyCount](#getpropertycount)|检索在属性网格控件的属性的数目。|  
|[CMFCPropertyGridCtrl::GetRowHeight](#getrowheight)|检索的属性网格控件中的某行的高度。|  
|[CMFCPropertyGridCtrl::GetScrollBarCtrl](#getscrollbarctrl)|检索指向属性网格控件中滚动条控件的指针。 (重写[CWnd::GetScrollBarCtrl](../../mfc/reference/cwnd-class.md#getscrollbarctrl)。)|  
|[CMFCPropertyGridCtrl::GetTextColor](#gettextcolor)|检索当前的属性网格控件中的属性项的文本的颜色。|  
|`CMFCPropertyGridCtrl::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)程序与此类类型的对象。|  
|[CMFCPropertyGridCtrl::HitTest](#hittest)|检索指向项中指定的点是否与属性网格控件项相对应的属性对象的指针。 此方法还指示在属性网格控件中包含点的区域。|  
|[CMFCPropertyGridCtrl::InitHeader](#initheader)|初始化内部[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)对象框架使用，以显示当前的属性网格控件。|  
|[CMFCPropertyGridCtrl::IsAlphabeticMode](#isalphabeticmode)|指示在属性网格控件是否处于按字母顺序模式。|  
|[CMFCPropertyGridCtrl::IsAlwaysShowUserToolTip](#isalwaysshowusertooltip)||  
|[CMFCPropertyGridCtrl::IsDescriptionArea](#isdescriptionarea)|指示是否显示在属性网格控件的描述区域。|  
|[CMFCPropertyGridCtrl::IsGroupNameFullWidth](#isgroupnamefullwidth)|指示是否在当前的属性网格控件的宽度范围内显示每个属性组名称。|  
|[CMFCPropertyGridCtrl::IsHeaderCtrl](#isheaderctrl)|指示是否显示标头控件。|  
|[CMFCPropertyGridCtrl::IsMarkModifiedProperties](#ismarkmodifiedproperties)|指示在属性网格控件显示修改后的属性的方式。|  
|[CMFCPropertyGridCtrl::IsShowDragContext](#isshowdragcontext)|指示是否框架重绘的当前属性网格控件的名称和值列在用户调整列的大小。|  
|[CMFCPropertyGridCtrl::IsVSDotNetLook](#isvsdotnetlook)|指示是否正在 VS.NET 使用的样式属性网格控件的外观。|  
|[CMFCPropertyGridCtrl::MarkModifiedProperties](#markmodifiedproperties)|指定如何显示修改后的属性。|  
|`CMFCPropertyGridCtrl::PreTranslateMessage`|类使用[CWinApp](../../mfc/reference/cwinapp-class.md)将窗口消息转换之前调度到[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函数。 (重写[cwnd:: Pretranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|  
|[CMFCPropertyGridCtrl::RemoveAll](#removeall)|从属性网格控件中删除所有属性对象。|  
|[CMFCPropertyGridCtrl::ResetOriginalValues](#resetoriginalvalues)|还原所有属性的原始值。|  
|[CMFCPropertyGridCtrl::SetAlphabeticMode](#setalphabeticmode)|设置或重置按字母顺序排列的模式。|  
|[CMFCPropertyGridCtrl::SetBoolLabels](#setboollabels)|指定的布尔值的标签的文本。|  
|[CMFCPropertyGridCtrl::SetCurSel](#setcursel)|在属性网格控件中选择一个属性。|  
|[CMFCPropertyGridCtrl::SetCustomColors](#setcustomcolors)|指定自定义颜色的各种属性网格控件元素。|  
|[CMFCPropertyGridCtrl::SetDescriptionRows](#setdescriptionrows)|指定要在当前的属性网格控件的描述部分中显示行的数。|  
|[CMFCPropertyGridCtrl::SetGroupNameFullWidth](#setgroupnamefullwidth)|指定是否在当前的属性网格控件中显示一组属性的类别名称的整个宽度。|  
|[CMFCPropertyGridCtrl::SetListDelimiter](#setlistdelimiter)|定义将用作分隔符的属性值列表中的字符。|  
|[CMFCPropertyGridCtrl::SetShowDragContext](#setshowdragcontext)|指定是否在 framework 重绘的当前属性网格控件的名称和值列时用户调整列的大小。|  
|[CMFCPropertyGridCtrl::SetVSDotNetLook](#setvsdotnetlook)|在 VS.NET 中使用的样式设置的属性网格控件的外观。|  
|[CMFCPropertyGridCtrl::UpdateColor](#updatecolor)|设置当前选定的颜色属性的颜色值。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCPropertyGridCtrl::AdjustLayout](#adjustlayout)|重绘属性网格控件并将其属性。|  
|[CMFCPropertyGridCtrl::CompareProps](#compareprops)|由对属性排序的属性网格控件调用。|  
|[CMFCPropertyGridCtrl::EditItem](#edititem)|由框架调用，当用户开始修改属性。|  
|[CMFCPropertyGridCtrl::EndEditItem](#endedititem)|由框架调用，当用户停止修改的属性。|  
|[CMFCPropertyGridCtrl::Init](#init)|由框架来初始化属性网格控件调用。|  
|[CMFCPropertyGridCtrl::OnChangeSelection](#onchangeselection)|当前所选内容更改时由框架调用。|  
|[CMFCPropertyGridCtrl::OnClickButton](#onclickbutton)|单击属性按钮时由框架调用。|  
|[CMFCPropertyGridCtrl::OnDrawBorder](#ondrawborder)|由要绘制在属性网格控件周围的边框的框架调用。|  
|[CMFCPropertyGridCtrl::OnDrawDescription](#ondrawdescription)|由框架来绘制说明区域和显示的说明文本调用。|  
|[CMFCPropertyGridCtrl::OnDrawList](#ondrawlist)|由框架在属性网格控件中显示的属性列表调用。|  
|[CMFCPropertyGridCtrl::OnDrawProperty](#ondrawproperty)|由框架，以显示属性的调用。|  
|[CMFCPropertyGridCtrl::OnPropertyChanged](#onpropertychanged)|属性的值发生更改时由框架调用。|  
|[CMFCPropertyGridCtrl::OnSelectCombo](#onselectcombo)|选择一个属性，它包含一个组合框控件时由框架调用。|  
|[CMFCPropertyGridCtrl::ValidateItemData](#validateitemdata)|由该框架能验证属性数据调用。|  
  
## <a name="remarks"></a>备注  
 `CMFCPropertyGridCtrl`类显示在属性网格控件，其中包含派生自的可编辑属性[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)类。 每个属性可以表示一种类型，并且它可以包含的子项。 属性网格控件支持可调整大小区域底部可以显示所选属性的说明。  
  
 若要使用属性网格控件，构造`CMFCPropertyGridCtrl`对象，然后调用[CMFCPropertyGridCtrl::Create](#create)方法。 使用[CMFCPropertyGridCtrl::AddProperty](#addproperty)方法将属性添加到列表。  
  
## <a name="selection-properties"></a>选择属性  
 而不是表示一个值，属性项可以启动一个对话框，使用户能够选择颜色、 文件或字体。  
  
 下表列出四种选择属性类型︰  
  
|类|描述|  
|-----------|-----------------|  
|[CMFCPropertyGridProperty 类](../../mfc/reference/cmfcpropertygridproperty-class.md)|一个一般用途的属性，用于指定的字符串、 布尔值，日期值，等等。|  
|[CMFCPropertyGridColorProperty 类](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)|一个属性，用于选择一个颜色值。|  
|[CMFCPropertyGridFileProperty 类](../../mfc/reference/cmfcpropertygridfileproperty-class.md)|一个属性，用于选择一个文件。|  
|[CMFCPropertyGridFontProperty 类](../../mfc/reference/cmfcpropertygridfontproperty-class.md)|一个属性，用于选择一种字体。|  
  
## <a name="illustrations"></a>图示  
 下图描述了两种方式显示属性在属性网格控件。 第一张图显示的属性层次结构，第二个按字母顺序显示属性。  
  
 ![属性列表与属性表](../../mfc/reference/media/proplist.png "proplist")  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法来配置的属性网格控件对象`CMFCPropertyGridCtrl`类。 该示例演示如何启用标头控件、 启用说明区域中，并设置属性网格控件的外观。 该示例还演示如何设置控件对进行排序，由此控件的按字母顺序模式有各自的属性名称，它包含的所有属性以及如何都设置各种元素的属性网格控件的自定义颜色。 此示例摘自[新控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&14;](../../mfc/reference/codesnippet/cpp/cmfcpropertygridctrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls #&16;](../../mfc/reference/codesnippet/cpp/cmfcpropertygridctrl-class_2.cpp)]  
[!code-cpp[NVC_MFC_NewControls #&20;](../../mfc/reference/codesnippet/cpp/cmfcpropertygridctrl-class_3.cpp)]  
[!code-cpp[NVC_MFC_NewControls #&21;](../../mfc/reference/codesnippet/cpp/cmfcpropertygridctrl-class_4.cpp)]  
[!code-cpp[NVC_MFC_NewControls #&24;](../../mfc/reference/codesnippet/cpp/cmfcpropertygridctrl-class_5.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxpropertygridctrl.h  
  
##  <a name="a-nameaccselecta--cmfcpropertygridctrlaccselect"></a><a name="accselect"></a>CMFCPropertyGridCtrl::accSelect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual HRESULT accSelect(
    long flagsSelect,  
    VARIANT varChild);
```  
  
### <a name="parameters"></a>参数  
 [in] `flagsSelect`  
 [in] `varChild`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameaddpropertya--cmfcpropertygridctrladdproperty"></a><a name="addproperty"></a>CMFCPropertyGridCtrl::AddProperty  
 将新属性添加到属性网格控件。  
  
```  
int AddProperty(
    CMFCPropertyGridProperty* pProp,  
    BOOL bRedraw=TRUE,  
    BOOL bAdjustLayout=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pProp`  
 指向属性。  
  
 [in] `bRedraw`  
 `TRUE`若要立即; 重绘属性否则为`FALSE`。 默认值为 `TRUE`。  
  
 [in] `bAdjustLayout`  
 `TRUE`若要重新计算如何绘制的文本和值的属性，然后绘制您的属性。`FALSE`用现有计算来绘制该属性。 默认值为 `TRUE`。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，其中添加属性; 在属性网格控件的位置的从零开始索引否则为-1。  
  
### <a name="remarks"></a>备注  
 此方法将添加到属性网格控件中的属性列表的末尾的指定属性的指针。 不要破坏属性或允许它们超出范围，网格控件被销毁之前。 完成此操作与属性网格控件，调用[CMFCPropertyGridCtrl::RemoveAll](#removeall)若要删除所有添加的属性。 如果指定的属性已添加到列表 AddProperty 方法失败。  
  
##  <a name="a-nameadjustlayouta--cmfcpropertygridctrladjustlayout"></a><a name="adjustlayout"></a>CMFCPropertyGridCtrl::AdjustLayout  
 重绘属性网格控件并将其属性。  
  
```  
virtual void AdjustLayout();
```  
  
### <a name="remarks"></a>备注  
 此方法将重新计算如何绘制整个属性网格控件和属性，包括图像、 字体和控件。  
  
##  <a name="a-namealwaysshowusertooltipa--cmfcpropertygridctrlalwaysshowusertooltip"></a><a name="alwaysshowusertooltip"></a>CMFCPropertyGridCtrl::AlwaysShowUserToolTip  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void AlwaysShowUserToolTip(BOOL bShow = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bShow`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameclosecolorpopupa--cmfcpropertygridctrlclosecolorpopup"></a><a name="closecolorpopup"></a>CMFCPropertyGridCtrl::CloseColorPopup  
 关闭颜色选择对话框。  
  
```  
virtual void CloseColorPopup();
```  
  
### <a name="remarks"></a>备注  
 有关颜色选择对话框的详细信息，请参阅[CMFCPropertyGridColorProperty 类](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)。  
  
##  <a name="a-namecmfcpropertygridctrla--cmfcpropertygridctrlcmfcpropertygridctrl"></a><a name="cmfcpropertygridctrl"></a>CMFCPropertyGridCtrl::CMFCPropertyGridCtrl  
 构造 `CMFCPropertyGridCtrl` 对象。  
  
```  
CMFCPropertyGridCtrl();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namecomparepropsa--cmfcpropertygridctrlcompareprops"></a><a name="compareprops"></a>CMFCPropertyGridCtrl::CompareProps  
 由对属性排序的属性网格控件调用。  
  
```  
virtual int CompareProps(
    const CMFCPropertyGridProperty* pProp1,  
    const CMFCPropertyGridProperty* pProp2) const;  
```  
  
### <a name="parameters"></a>参数  
 `pProp1`  
 属性指向的指针。  
  
 `pProp2`  
 属性指向的指针。  
  
### <a name="return-value"></a>返回值  
  
|返回值|描述|  
|------------------|-----------------|  
|< 0|名称`pProp1`参数小于的名称`pProp2`参数。|  
|0|名称`pProp1`参数是否等于的名称`pProp2`参数。|  
|> 0|名称`pProp1`对象是否大于名称`pProp2`参数。|  
  
### <a name="remarks"></a>备注  
 默认情况下，此方法使用[CString::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare)方法来比较`CMFCPropertyGridProperty::m_strName`指定参数的成员。  
  
##  <a name="a-namecreatea--cmfcpropertygridctrlcreate"></a><a name="create"></a>CMFCPropertyGridCtrl::Create  
 创建属性网格控件，并将其附加到属性网格控件对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwStyle`  
 按位组合 (OR)[窗口样式](../../mfc/reference/window-styles.md)。  
  
 [in] `rect`  
 指定的大小和位置的窗口中，在客户端的绑定矩形坐标`pParentWnd`。  
  
 [in] `pParentWnd`  
 向父窗口的指针。 不得为 `NULL`。  
  
 [in] `nID`  
 子窗口 ID。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则已创建窗口否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 若要创建属性网格控件，第一次调用[CMFCPropertyGridCtrl::CMFCPropertyGridCtrl](#cmfcpropertygridctrl)构造属性网格对象。 然后，调用`CMFCPropertyGridCtrl::Create`。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`Create`中的方法`CMFCPropertyGridCtrl`类。 此示例摘自[新控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&15;](../../mfc/reference/codesnippet/cpp/cmfcpropertygridctrl-class_6.cpp)]  
  
##  <a name="a-namedeletepropertya--cmfcpropertygridctrldeleteproperty"></a><a name="deleteproperty"></a>CMFCPropertyGridCtrl::DeleteProperty  
 从属性网格控件中删除指定的属性。  
  
```  
BOOL DeleteProperty(
    CMFCPropertyGridProperty*& pProp,  
    BOOL bRedraw=TRUE,  
    BOOL bAdjustLayout=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pProp`  
 指向属性。  
  
 [in] `bRedraw`  
 `TRUE`若要重绘属性网格控件;否则为`FALSE`。 默认值为 `TRUE`。  
  
 [in] `bAdjustLayout`  
 `TRUE`若要重新计算如何在属性网格控件中，绘制所有文本、 图像和项，然后都绘制控件;否则为`FALSE`。 默认值为 `TRUE`。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `TRUE`；否则为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法用于从属性网格控件中删除某个属性和任何子项目。  
  
##  <a name="a-namedrawcontrolbarcolorsa--cmfcpropertygridctrldrawcontrolbarcolors"></a><a name="drawcontrolbarcolors"></a>CMFCPropertyGridCtrl::DrawControlBarColors  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL DrawControlBarColors() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameedititema--cmfcpropertygridctrledititem"></a><a name="edititem"></a>CMFCPropertyGridCtrl::EditItem  
 由框架调用，当用户开始修改属性。  
  
```  
virtual BOOL EditItem(
    CMFCPropertyGridProperty* pProp,  
    LPPOINT lptClick=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `pProp`  
 指向属性。  
  
 [in] `lptClick`  
 用户单击以开始编辑操作的属性网格控件上的点。 关键在于该控件的工作区坐标中。 默认值为 `NULL`。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果方法成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameenabledescriptionareaa--cmfcpropertygridctrlenabledescriptionarea"></a><a name="enabledescriptionarea"></a>CMFCPropertyGridCtrl::EnableDescriptionArea  
 启用或禁用在属性网格控件的属性列表下显示的说明区域。  
  
```  
void EnableDescriptionArea(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要启用说明区域;`FALSE`若要禁用的说明区域。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 说明区域显示在属性网格控件的底部。 默认情况下，说明区域为已禁用，从而不可见。  
  
##  <a name="a-nameenableheaderctrla--cmfcpropertygridctrlenableheaderctrl"></a><a name="enableheaderctrl"></a>CMFCPropertyGridCtrl::EnableHeaderCtrl  
 启用或禁用在属性网格控件顶部标头控件。  
  
```  
void EnableHeaderCtrl(
    BOOL bEnable=TRUE,  
    LPCTSTR lpszLeftColumn=_T("Property"),  
    LPCTSTR lpszRightColumn=_T("Value"));
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要启用标头控件中;`FALSE`禁用标头控件。 默认值为 `TRUE`。  
  
 [in] `lpszLeftColumn`  
 标头控件的左侧的列的标题。 默认值是**属性**。  
  
 [in] `lpszRightColumn`  
 标头控件的右侧列的标题。 默认值是**值**。  
  
##  <a name="a-nameendedititema--cmfcpropertygridctrlendedititem"></a><a name="endedititem"></a>CMFCPropertyGridCtrl::EndEditItem  
 由框架调用，当用户完成修改的属性。  
  
```  
virtual BOOL EndEditItem(BOOL bUpdateData=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bUpdateData`  
 `TRUE`若要指定在编辑操作已完成; 时，必须验证已修改的属性数据否则为`FALSE`。 默认值为 `TRUE`。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则结束编辑操作，`FALSE`如果已修改的属性数据无效，或者如果编辑操作应继续。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameensurevisiblea--cmfcpropertygridctrlensurevisible"></a><a name="ensurevisible"></a>CMFCPropertyGridCtrl::EnsureVisible  
 执行滚动操作使得在属性网格控件，并扩展属性项，直到指定的属性可见。  
  
```  
void EnsureVisible(
    CMFCPropertyGridProperty* pProp,  
    BOOL bExpandParents=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pProp`  
 指向属性。  
  
 [in] `bExpandParents`  
 `TRUE`若要展开父项，以使指定的属性可见，则否则为`FALSE`。 默认值为 `FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameexpandalla--cmfcpropertygridctrlexpandall"></a><a name="expandall"></a>CMFCPropertyGridCtrl::ExpandAll  
 展开或折叠属性网格控件的所有节点。  
  
```  
void ExpandAll(BOOL bExpand=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bExpand`  
 `TRUE`若要展开所有节点;`FALSE`可折叠所有节点。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namefinditembydataa--cmfcpropertygridctrlfinditembydata"></a><a name="finditembydata"></a>CMFCPropertyGridCtrl::FindItemByData  
 检索与用户定义相关联的属性`DWORD`值。  
  
```  
CMFCPropertyGridProperty* FindItemByData(
    DWORD_PTR dwData,  
    BOOL bSearchSubItems=TRUE) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `dwData`  
 一个 `DWORD` 值。  
  
 [in] `bSearchSubItems`  
 `TRUE`若要搜索属性的子项目;否则为`FALSE`。 默认值为 `TRUE`。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则该关联的属性对象指向的指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 使用[CMFCPropertyGridCtrl::CMFCPropertyGridCtrl](#cmfcpropertygridctrl)构造函数或[CMFCPropertyGridProperty::SetData](../../mfc/reference/cmfcpropertygridproperty-class.md#setdata)方法将关联起来`DWORD`具有属性。  
  
##  <a name="a-namegetaccchildcounta--cmfcpropertygridctrlgetaccchildcount"></a><a name="get_accchildcount"></a>CMFCPropertyGridCtrl::get_accChildCount  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual HRESULT get_accChildCount(long* pcountChildren);
```  
  
### <a name="parameters"></a>参数  
 [in] `pcountChildren`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetaccfocusa--cmfcpropertygridctrlgetaccfocus"></a><a name="get_accfocus"></a>CMFCPropertyGridCtrl::get_accFocus  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual HRESULT get_accFocus(VARIANT* pvarChild);
```  
  
### <a name="parameters"></a>参数  
 [in] `pvarChild`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetacchelpa--cmfcpropertygridctrlgetacchelp"></a><a name="get_acchelp"></a>CMFCPropertyGridCtrl::get_accHelp  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual HRESULT get_accHelp(
    VARIANT varChild,  
    BSTR* pszHelp);
```  
  
### <a name="parameters"></a>参数  
 [in] `varChild`  
 [in] `pszHelp`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetacchelptopica--cmfcpropertygridctrlgetacchelptopic"></a><a name="get_acchelptopic"></a>CMFCPropertyGridCtrl::get_accHelpTopic  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual HRESULT get_accHelpTopic(
    BSTR* pszHelpFile,  
    VARIANT varChild,  
    long* pidTopic);
```  
  
### <a name="parameters"></a>参数  
 [in] `pszHelpFile`  
 [in] `varChild`  
 [in] `pidTopic`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetacckeyboardshortcuta--cmfcpropertygridctrlgetacckeyboardshortcut"></a><a name="get_acckeyboardshortcut"></a>CMFCPropertyGridCtrl::get_accKeyboardShortcut  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual HRESULT get_accKeyboardShortcut(
    VARIANT varChild,  
    BSTR* pszKeyboardShortcut);
```  
  
### <a name="parameters"></a>参数  
 [in] `varChild`  
 [in] `pszKeyboardShortcut`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetaccselectiona--cmfcpropertygridctrlgetaccselection"></a><a name="get_accselection"></a>CMFCPropertyGridCtrl::get_accSelection  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual HRESULT get_accSelection(VARIANT* pvarChildren);
```  
  
### <a name="parameters"></a>参数  
 [in] `pvarChildren`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetbkcolora--cmfcpropertygridctrlgetbkcolor"></a><a name="getbkcolor"></a>CMFCPropertyGridCtrl::GetBkColor  
 检索当前的属性网格控件的背景色。  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 RGB 颜色值。  
  
### <a name="remarks"></a>备注  
 此方法检索框架使用用于绘制当前属性网格控件的背景的颜色。 [CMFCPropertyGridCtrl::GetTextColor](#gettextcolor)方法检索的前景色。  
  
##  <a name="a-namegetboldfonta--cmfcpropertygridctrlgetboldfont"></a><a name="getboldfont"></a>CMFCPropertyGridCtrl::GetBoldFont  
 检索用于在粗体样式中的当前属性网格控件中绘制文本的 Windows 字体。  
  
```  
CFont& GetBoldFont();
```  
  
### <a name="return-value"></a>返回值  
 对引用[CFont](../../mfc/reference/cfont-class.md)描述加粗字体的特征的对象。  
  
##  <a name="a-namegetcursela--cmfcpropertygridctrlgetcursel"></a><a name="getcursel"></a>CMFCPropertyGridCtrl::GetCurSel  
 检索当前所选的属性。  
  
```  
CMFCPropertyGridProperty* GetCurSel() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向对应于在属性网格控件的选定项的属性对象的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetcustomcolorsa--cmfcpropertygridctrlgetcustomcolors"></a><a name="getcustomcolors"></a>CMFCPropertyGridCtrl::GetCustomColors  
 检索当前为属性网格控件元素定义的自定义颜色。  
  
```  
void GetCustomColors(
    COLORREF& clrBackground,  
    COLORREF& clrText,  
    COLORREF& clrGroupBackground,  
    COLORREF& clrGroupText,  
    COLORREF& clrDescriptionBackground,  
    COLORREF& clrDescriptionText,  
    COLORREF& clrLine);
```  
  
### <a name="parameters"></a>参数  
 [out] `clrBackground`  
 属性值的背景色。  
  
 [out] `clrText`  
 属性名称和属性值文本的颜色。  
  
 [out] `clrGroupBackground`  
 属性组的背景色。  
  
 [out] `clrGroupText`  
 在属性组中的文本的颜色。  
  
 [out] `clrDescriptionBackground`  
 说明区域的背景色。  
  
 [out] `clrDescriptionText`  
 在说明区域中的文本的颜色。  
  
 [out] `clrLine`  
 属性之间绘制的线条的颜色。  
  
### <a name="remarks"></a>备注  
 使用[CMFCPropertyGridCtrl::SetCustomColors](#setcustomcolors)方法设置自定义颜色。  
  
##  <a name="a-namegetdescriptionheighta--cmfcpropertygridctrlgetdescriptionheight"></a><a name="getdescriptionheight"></a>CMFCPropertyGridCtrl::GetDescriptionHeight  
 检索位于属性网格控件底部的描述区域的高度。  
  
```  
int GetDescriptionHeight() const;  
```  
  
### <a name="return-value"></a>返回值  
 说明区域，以像素为单位的高度。  
  
### <a name="remarks"></a>备注  
 说明区域的高度由系统自动计算并设置为 1/4 属性网格控件的高度。  
  
 使用[CMFCPropertyGridCtrl::EnableDescriptionArea](#enabledescriptionarea)方法，以显示或隐藏说明区域。 使用[CMFCPropertyGridCtrl::IsDescriptionArea](#isdescriptionarea)方法，以确定是否描述区域是显示还是隐藏。  
  
##  <a name="a-namegetdescriptionrowsa--cmfcpropertygridctrlgetdescriptionrows"></a><a name="getdescriptionrows"></a>CMFCPropertyGridCtrl::GetDescriptionRows  
 检索在说明区域中的当前属性网格控件的行数。  
  
```  
int GetDescriptionRows() const;  
```  
  
### <a name="return-value"></a>返回值  
 在说明区域中的当前属性网格控件的行数。  
  
### <a name="remarks"></a>备注  
 [CMFCPropertyGridCtrl::CMFCPropertyGridCtrl](#cmfcpropertygridctrl)构造函数将初始化为 3 行说明区域。  
  
##  <a name="a-namegetheaderctrla--cmfcpropertygridctrlgetheaderctrl"></a><a name="getheaderctrl"></a>CMFCPropertyGridCtrl::GetHeaderCtrl  
 检索内部[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)对象框架使用，以显示当前的属性网格控件。  
  
```  
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```  
  
### <a name="return-value"></a>返回值  
 对 `CMFCHeaderCtrl` 对象的引用。  
  
##  <a name="a-namegetheaderheighta--cmfcpropertygridctrlgetheaderheight"></a><a name="getheaderheight"></a>CMFCPropertyGridCtrl::GetHeaderHeight  
 检索在属性网格控件的标头的高度。  
  
```  
int GetHeaderHeight() const;  
```  
  
### <a name="return-value"></a>返回值  
 标头，以像素为单位的高度。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetleftcolumnwidtha--cmfcpropertygridctrlgetleftcolumnwidth"></a><a name="getleftcolumnwidth"></a>CMFCPropertyGridCtrl::GetLeftColumnWidth  
 检索包含每个属性的名称的当前属性网格控件左侧的列的宽度。  
  
```  
int GetLeftColumnWidth() const;  
```  
  
### <a name="return-value"></a>返回值  
 名称列的宽度。  
  
### <a name="remarks"></a>备注  
 在属性网格控件的右列中包含的每个属性的值。  
  
##  <a name="a-namegetlistrecta--cmfcpropertygridctrlgetlistrect"></a><a name="getlistrect"></a>CMFCPropertyGridCtrl::GetListRect  
 检索的属性网格控件的边框。  
  
```  
CRect GetListRect() const;  
```  
  
### <a name="return-value"></a>返回值  
 属性网格控件的边框。 此 rectange 不包括说明区域和标头。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetpropertya--cmfcpropertygridctrlgetproperty"></a><a name="getproperty"></a>CMFCPropertyGridCtrl::GetProperty  
 检索指向对应于在属性网格控件中的项的指定索引的属性对象的指针。  
  
```  
CMFCPropertyGridProperty* GetProperty(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 属性网格控件项的从零开始的索引。  
  
 如果此方法会断言`nIndex`参数小于零或大于或等于属性的数目。  
  
### <a name="return-value"></a>返回值  
 指向对应于指定的索引，如果此方法成功，则属性对象的指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetpropertycolumnwidtha--cmfcpropertygridctrlgetpropertycolumnwidth"></a><a name="getpropertycolumnwidth"></a>CMFCPropertyGridCtrl::GetPropertyColumnWidth  
 检索包含属性值的列的当前宽度。  
  
```  
int GetPropertyColumnWidth() const;  
```  
  
### <a name="return-value"></a>返回值  
 包含属性值的列的当前宽度。  
  
### <a name="remarks"></a>备注  
 在属性网格控件右侧列包含的属性值。 客户可以使用属性网格控件的拆分框更改值列的宽度。  
  
##  <a name="a-namegetpropertycounta--cmfcpropertygridctrlgetpropertycount"></a><a name="getpropertycount"></a>CMFCPropertyGridCtrl::GetPropertyCount  
 检索在属性网格控件的属性的数目。  
  
```  
int GetPropertyCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 属性的数目。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetrowheighta--cmfcpropertygridctrlgetrowheight"></a><a name="getrowheight"></a>CMFCPropertyGridCtrl::GetRowHeight  
 检索的属性网格控件中的某行的高度。  
  
```  
int GetRowHeight() const;  
```  
  
### <a name="return-value"></a>返回值  
 行的高度。  
  
### <a name="remarks"></a>备注  
 行的高度等于当前的字体高度加 4 个像素。  
  
##  <a name="a-namegetscrollbarctrla--cmfcpropertygridctrlgetscrollbarctrl"></a><a name="getscrollbarctrl"></a>CMFCPropertyGridCtrl::GetScrollBarCtrl  
 检索指向属性网格控件中滚动条控件的指针。  
  
```  
virtual CScrollBar* GetScrollBarCtrl(int nBar) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `nBar`  
 滚动条，它必须是方向`SB_VERT`。  
  
### <a name="return-value"></a>返回值  
 指向滚动栏对象，或`NULL`如果没有任何滚动条或滚动条方向为`SB_HORZ`。  
  
### <a name="remarks"></a>备注  
 使用此方法来获取到垂直滚动条控件的直接访问。  
  
##  <a name="a-namegettextcolora--cmfcpropertygridctrlgettextcolor"></a><a name="gettextcolor"></a>CMFCPropertyGridCtrl::GetTextColor  
 检索用于在当前的属性网格控件中绘制属性项的文本的颜色。  
  
```  
COLORREF GetTextColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 RGB 颜色值。  
  
### <a name="remarks"></a>备注  
 此方法检索框架将绘制前景色的当前属性网格控件使用的颜色。 [CMFCPropertyGridCtrl::GetBkColor](#getbkcolor)方法检索的背景色。  
  
##  <a name="a-namehittesta--cmfcpropertygridctrlhittest"></a><a name="hittest"></a>CMFCPropertyGridCtrl::HitTest  
 检索指向项中指定的点是否与属性网格控件项相对应的属性对象的指针。 此方法还指示在属性网格控件中包含点的区域。  
  
```  
CMFCPropertyGridProperty* HitTest(
    CPoint pt,  
    CMFCPropertyGridProperty::ClickArea* pnArea=NULL,  
    BOOL bPropsOnly=FALSE) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `pt`  
 工作区坐标中的点。  
  
 [in, out] `pnArea`  
 一个指向`ClickArea`变量。 当此方法返回时，该变量指示*属性区域*，其中包含指定的点。 有关属性区域的详细信息，请参阅备注。  
  
 [in] `bPropsOnly`  
 `TRUE`若要测试仅属性区域;`FALSE`测试*说明区*如果指定的点不在的属性区域。 默认值为 `FALSE`。 说明区域的详细信息，请参阅备注。  
  
### <a name="return-value"></a>返回值  
 如果`bPropsOnly`参数是`TRUE`和指定的点是在属性区域中，返回值是指向相应的属性对象的指针。 此外，`pnArea`参数设置为包含指定的点的特定区域。 否则，返回值是`NULL`和`pnArea`不修改参数。  
  
 如果`bPropsOnly`参数是`FALSE`，返回值也始终`NULL`。 但是，如果指定的点在描述区域中，`pnArea`参数设置为`CMFCPropertyGridProperty::ClickDescription`。  
  
### <a name="remarks"></a>备注  
 术语*属性区域*指的是任何一个的名称，值，或展开框区域的属性网格控件项。 *说明区*是在属性网格控件底部的区域。 当单击属性网格控件项时，说明区域将显示相应属性的说明。  
  
 此方法设置的变量的值`pnArea`参数指向。 下表列出可能的值以及相应的区域。  
  
|值|区域|  
|-----------|----------|  
|`ClickArea::ClickExpandBox`|属性展开框控件。|  
|`ClickArea::ClickName`|属性名称。|  
|`ClickArea::ClickValue`|属性值。|  
|`CMFCPropertyGridProperty::ClickDescription`|属性网格控件说明区域。|  
  
##  <a name="a-nameinita--cmfcpropertygridctrlinit"></a><a name="init"></a>CMFCPropertyGridCtrl::Init  
 由框架来初始化属性网格控件调用。  
  
```  
virtual void Init();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameinitheadera--cmfcpropertygridctrlinitheader"></a><a name="initheader"></a>CMFCPropertyGridCtrl::InitHeader  
 初始化内部[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)对象框架使用，以显示当前的属性网格控件。  
  
```  
virtual void InitHeader();
```  
  
##  <a name="a-nameisalphabeticmodea--cmfcpropertygridctrlisalphabeticmode"></a><a name="isalphabeticmode"></a>CMFCPropertyGridCtrl::IsAlphabeticMode  
 指示在属性网格控件是否处于按字母顺序模式。  
  
```  
BOOL IsAlphabeticMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果属性网格控件是否处于按字母顺序模式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 按字母顺序模式的属性网格控件时，它们的名称按字母顺序排序的所有属性。 否则，它们的父节点下分组属性。  
  
 使用[CMFCPropertyGridCtrl::SetAlphabeticMode](#setalphabeticmode)方法来启用或禁用按字母顺序模式。  
  
##  <a name="a-nameisalwaysshowusertooltipa--cmfcpropertygridctrlisalwaysshowusertooltip"></a><a name="isalwaysshowusertooltip"></a>CMFCPropertyGridCtrl::IsAlwaysShowUserToolTip  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsAlwaysShowUserToolTip() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameisdescriptionareaa--cmfcpropertygridctrlisdescriptionarea"></a><a name="isdescriptionarea"></a>CMFCPropertyGridCtrl::IsDescriptionArea  
 指示是否显示在属性网格控件的描述区域。  
  
```  
BOOL IsDescriptionArea() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果显示说明区域;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用[CMFCPropertyGridCtrl::EnableDescriptionArea](#enabledescriptionarea)方法来隐藏或显示的说明区域。  
  
##  <a name="a-nameisgroupnamefullwidtha--cmfcpropertygridctrlisgroupnamefullwidth"></a><a name="isgroupnamefullwidth"></a>CMFCPropertyGridCtrl::IsGroupNameFullWidth  
 指示是否在当前的属性网格控件的宽度范围内显示每个属性组名称。  
  
```  
BOOL IsGroupNameFullWidth() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果在属性网格控件; 的宽度范围内显示组的名称`FALSE`如果组名截断该控件的右侧 （值） 列。  
  
### <a name="remarks"></a>备注  
 一个*组*是相关属性在属性网格控件的集合。 如果层次结构方式显示控件*组名*显示为组上方的行中类别标题。  
  
##  <a name="a-nameisheaderctrla--cmfcpropertygridctrlisheaderctrl"></a><a name="isheaderctrl"></a>CMFCPropertyGridCtrl::IsHeaderCtrl  
 指示是否显示标头控件。  
  
```  
BOOL IsHeaderCtrl() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果标头控件会显示出来;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用[CMFCPropertyGridCtrl::EnableHeaderCtrl](#enableheaderctrl)隐藏或显示标头控件的方法。  
  
##  <a name="a-nameismarkmodifiedpropertiesa--cmfcpropertygridctrlismarkmodifiedproperties"></a><a name="ismarkmodifiedproperties"></a>CMFCPropertyGridCtrl::IsMarkModifiedProperties  
 指示在属性网格控件显示修改后的属性的方式。  
  
```  
BOOL IsMarkModifiedProperties() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果粗体样式用于显示，修改的属性;`FALSE`如果常规样式用于显示修改的属性。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameisshowdragcontexta--cmfcpropertygridctrlisshowdragcontext"></a><a name="isshowdragcontext"></a>CMFCPropertyGridCtrl::IsShowDragContext  
 指示是否框架重绘的当前属性网格控件的名称和值列在用户调整列的大小。  
  
```  
BOOL IsShowDragContext() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果框架在调整大小操作; 期间重绘的名称和值的列，`FALSE`如果拖放操作完成后，该框架重绘列。  
  
### <a name="remarks"></a>备注  
 用户可以通过拖动列之间的拆分条来调整在属性网格控件的名称和值列。 如果显示的拖动上下文，则只要用户拖动拆分栏将调整大小的名称和值的列。 否则为在拆分栏移动，但这些列拖放操作完成之前不重新绘制。  
  
##  <a name="a-nameisvsdotnetlooka--cmfcpropertygridctrlisvsdotnetlook"></a><a name="isvsdotnetlook"></a>CMFCPropertyGridCtrl::IsVSDotNetLook  
 指示是否在 Visual Studio.NET 中的样式属性网格控件的外观。  
  
```  
BOOL IsVSDotNetLook() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果在样式中的 Visual Studio.NET; 是属性网格控件否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用[CMFCPropertyGridCtrl::SetVSDotNetLook](#setvsdotnetlook)方法来为 Visual Studio.NET 中的样式设置的属性网格控件。  
  
##  <a name="a-namemarkmodifiedpropertiesa--cmfcpropertygridctrlmarkmodifiedproperties"></a><a name="markmodifiedproperties"></a>CMFCPropertyGridCtrl::MarkModifiedProperties  
 指定如何显示修改后的属性。  
  
```  
void MarkModifiedProperties(
    BOOL bMark=TRUE,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bMark`  
 `TRUE`显示已修改的粗体样式; 中的属性`FALSE`在常规样式中显示已修改的属性。 默认值为 `TRUE`。  
  
 [in] `bRedraw`  
 `TRUE`若要立即; 重绘属性网格控件否则为`FALSE`。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameonchangeselectiona--cmfcpropertygridctrlonchangeselection"></a><a name="onchangeselection"></a>CMFCPropertyGridCtrl::OnChangeSelection  
 当前所选内容更改时由框架调用。  
  
```  
virtual void OnChangeSelection(
    CMFCPropertyGridProperty* pNewSel,   
    CMFCPropertyGridProperty* pOldSel);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `pNewSel`|指针，指向新选定的属性。|  
|[in] `pOldSel`|指针，指向先前选定的属性。|  
  
### <a name="remarks"></a>备注  
 此方法的默认实现没有任何影响。  
  
##  <a name="a-nameonclickbuttona--cmfcpropertygridctrlonclickbutton"></a><a name="onclickbutton"></a>CMFCPropertyGridCtrl::OnClickButton  
 单击属性按钮时由框架调用。  
  
```  
virtual void OnClickButton(CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 工作区坐标中的点。  
  
### <a name="remarks"></a>备注  
 默认情况下，此方法更新当前属性值。  
  
##  <a name="a-nameondrawbordera--cmfcpropertygridctrlondrawborder"></a><a name="ondrawborder"></a>CMFCPropertyGridCtrl::OnDrawBorder  
 由要绘制在属性网格控件周围的边框的框架调用。  
  
```  
virtual void OnDrawBorder(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameondrawdescriptiona--cmfcpropertygridctrlondrawdescription"></a><a name="ondrawdescription"></a>CMFCPropertyGridCtrl::OnDrawDescription  
 由框架来绘制说明区域和显示的说明文本调用。  
  
```  
virtual void OnDrawDescription(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 指定要绘制的说明区域的位置矩形。  
  
### <a name="remarks"></a>备注  
 使用[CMFCPropertyGridCtrl::EnableDescriptionArea](#enabledescriptionarea)方法以显示说明区域。  
  
##  <a name="a-nameondrawlista--cmfcpropertygridctrlondrawlist"></a><a name="ondrawlist"></a>CMFCPropertyGridCtrl::OnDrawList  
 由框架在属性网格控件中显示的属性列表调用。  
  
```  
virtual void OnDrawList(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameondrawpropertya--cmfcpropertygridctrlondrawproperty"></a><a name="ondrawproperty"></a>CMFCPropertyGridCtrl::OnDrawProperty  
 由框架，以显示属性的调用。  
  
```  
virtual int OnDrawProperty(
    CDC* pDC,  
    CMFCPropertyGridProperty* pProp) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `pProp`  
 指向属性对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `TRUE`；否则为 `FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameonpropertychangeda--cmfcpropertygridctrlonpropertychanged"></a><a name="onpropertychanged"></a>CMFCPropertyGridCtrl::OnPropertyChanged  
 属性的值发生更改时由框架调用。  
  
```  
virtual void OnPropertyChanged(CMFCPropertyGridProperty* pProp) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `pProp`  
 指向其值已更改的属性对象的指针。  
  
### <a name="remarks"></a>备注  
 默认情况下，此方法可发送[AFX_WM_PROPERTY_CHANGED](../../mfc/reference/afx-messages.md)属性网格控件的所有者的消息。  
  
##  <a name="a-nameonselectcomboa--cmfcpropertygridctrlonselectcombo"></a><a name="onselectcombo"></a>CMFCPropertyGridCtrl::OnSelectCombo  
 选择一个属性，它包含一个组合框控件时由框架调用。  
  
```  
void OnSelectCombo();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameremovealla--cmfcpropertygridctrlremoveall"></a><a name="removeall"></a>CMFCPropertyGridCtrl::RemoveAll  
 从属性网格控件中删除所有属性对象。  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameresetoriginalvaluesa--cmfcpropertygridctrlresetoriginalvalues"></a><a name="resetoriginalvalues"></a>CMFCPropertyGridCtrl::ResetOriginalValues  
 还原所有属性的原始值。  
  
```  
void ResetOriginalValues(BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bRedraw`  
 `TRUE`若要重绘的属性列表中;否则为`FALSE`。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetalphabeticmodea--cmfcpropertygridctrlsetalphabeticmode"></a><a name="setalphabeticmode"></a>CMFCPropertyGridCtrl::SetAlphabeticMode  
 设置或重置字母的模式。  
  
```  
void SetAlphabeticMode(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bSet`  
 `TRUE`若要设置按字母顺序模式;`FALSE`重置按字母顺序模式。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 按字母顺序模式的属性网格控件时，该控件对它包含由其属性名称的所有属性进行都排序。  
  
##  <a name="a-namesetboollabelsa--cmfcpropertygridctrlsetboollabels"></a><a name="setboollabels"></a>CMFCPropertyGridCtrl::SetBoolLabels  
 指定的布尔值的标签的文本。  
  
```  
void SetBoolLabels(
    LPCTSTR lpszTrue,  
    LPCTSTR lpszFalse);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszTrue`  
 要显示的布尔值为 true 的文本字符串。  
  
 [in] `lpszFalse`  
 要为 false 的布尔值显示的文本字符串。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetcursela--cmfcpropertygridctrlsetcursel"></a><a name="setcursel"></a>CMFCPropertyGridCtrl::SetCurSel  
 在属性网格控件中选择一个属性。  
  
```  
void SetCurSel(
    CMFCPropertyGridProperty* pProp,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pProp`  
 指向属性对象的指针。  
  
 [in] `bRedraw`  
 `TRUE`若要立即; 重绘属性网格控件否则为`FALSE`。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 使用此方法以取消在属性网格控件中当前项的选择，然后选择对应于指定的属性的项。  
  
##  <a name="a-namesetcustomcolorsa--cmfcpropertygridctrlsetcustomcolors"></a><a name="setcustomcolors"></a>CMFCPropertyGridCtrl::SetCustomColors  
 指定属性网格控件的各种元素的自定义的颜色。  
  
```  
void SetCustomColors(
    COLORREF clrBackground,  
    COLORREF clrText,  
    COLORREF clrGroupBackground,  
    COLORREF clrGroupText,  
    COLORREF clrDescriptionBackground,  
    COLORREF clrDescriptionText,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>参数  
 [in] `clrBackground`  
 属性值的背景色。  
  
 [in] `clrText`  
 属性名称和属性值文本的颜色。  
  
 [in] `clrGroupBackground`  
 属性组的背景色。  
  
 [in] `clrGroupText`  
 属性组的新的文本颜色。  
  
 [in] `clrDescriptionBackground`  
 说明区域的背景色。  
  
 [in] `clrDescriptionText`  
 在说明区域中的文本的颜色。  
  
 [in] `clrLine`  
 属性之间绘制的线条的颜色。  
  
### <a name="remarks"></a>备注  
 对于任何参数，指定`((COLORREF)-1)`颜色值要用于该元素的属性网格控件的默认颜色。  
  
 若要自定义的特定属性的外观，请从派生类[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)类，然后重写[CMFCPropertyGridProperty::OnDrawName](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawname)， [CMFCPropertyGridProperty::OnDrawValue](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue)， [CMFCPropertyGridProperty::OnDrawExpandBox](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawexpandbox)，和[CMFCPropertyGridProperty::OnDrawButton](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawbutton)方法。  
  
##  <a name="a-namesetdescriptionrowsa--cmfcpropertygridctrlsetdescriptionrows"></a><a name="setdescriptionrows"></a>CMFCPropertyGridCtrl::SetDescriptionRows  
 指定要在当前的属性网格控件的描述部分中显示行的数。  
  
```  
void SetDescriptionRows(int nDescRows);
```  
  
### <a name="parameters"></a>参数  
 [in] `nDescRows`  
 要在属性说明中显示的行数。  
  
##  <a name="a-namesetgroupnamefullwidtha--cmfcpropertygridctrlsetgroupnamefullwidth"></a><a name="setgroupnamefullwidth"></a>CMFCPropertyGridCtrl::SetGroupNameFullWidth  
 指定是否在当前的属性网格控件中显示一组属性的类别名称的整个宽度。  
  
```  
void SetGroupNameFullWidth(
    BOOL bGroupNameFullWidth = TRUE,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bGroupNameFullWidth`  
 `TRUE`若要显示的类别名称，而不考虑属性名称列的宽度的完整宽度。 `FALSE`若要限制的类别名称为属性名称列的宽度的宽度。 默认值为 `TRUE`。  
  
 [in] `bRedraw`  
 `TRUE`若要立即; 更新的属性网格控件`FALSE`来更新控件，在下一个重绘事件时出现。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 属性网格控件组成可调整大小*属性名称*列和一个*属性值*列。 名称列的末尾也是值列开始。 若要调整列的大小，拖动列之间的边框。  
  
 这些条款*组名*和*类别名称*此方法中互换使用。 类别名称将显示在注意一组相关的属性和值的行。 此方法指定属性名称列的宽度是否还指定显示的类别名称的宽度。  
  
##  <a name="a-namesetlistdelimitera--cmfcpropertygridctrlsetlistdelimiter"></a><a name="setlistdelimiter"></a>CMFCPropertyGridCtrl::SetListDelimiter  
 定义用作分隔符的属性值列表中的字符。  
  
```  
void SetListDelimiter(TCHAR c);
```  
  
### <a name="parameters"></a>参数  
 [in] `c`  
 要用作分隔符的字符。  
  
### <a name="remarks"></a>备注  
 使用此方法中使用的属性值的列表中定义分隔符字符[CMFCPropertyGridProperty::CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#cmfcpropertygridproperty)构造函数。 在该构造函数中设置`bIsValueList`参数`TRUE`。  
  
 默认情况下， [CMFCPropertyGridCtrl::CMFCPropertyGridCtrl](#cmfcpropertygridctrl)构造函数将分隔符字符设置为以逗号 （，）。  
  
##  <a name="a-namesetshowdragcontexta--cmfcpropertygridctrlsetshowdragcontext"></a><a name="setshowdragcontext"></a>CMFCPropertyGridCtrl::SetShowDragContext  
 指定是否在 framework 重绘的当前属性网格控件的名称和值列时用户调整列的大小。  
  
```  
void SetShowDragContext(BOOL bShowDragContext = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bShowDragContext`  
 `TRUE`若要执行大小调整操作; 在重绘的名称和值的列`FALSE`拖放操作完成后重绘列。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 用户可以通过拖动列之间的拆分条来调整在属性网格控件的名称和值列。 如果显示的拖动上下文，则只要用户拖动拆分栏将调整大小的名称和值的列。 否则为在拆分栏移动，但这些列拖放操作完成之前不重新绘制。  
  
##  <a name="a-namesetvsdotnetlooka--cmfcpropertygridctrlsetvsdotnetlook"></a><a name="setvsdotnetlook"></a>CMFCPropertyGridCtrl::SetVSDotNetLook  
 在 Visual Studio.NET 中使用的样式设置的属性网格控件的外观。  
  
```  
void SetVSDotNetLook(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bSet`  
 `TRUE`若要设置使用 Visual Studio.NET; 中的样式属性网格控件否则为`FALSE`。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameupdatecolora--cmfcpropertygridctrlupdatecolor"></a><a name="updatecolor"></a>CMFCPropertyGridCtrl::UpdateColor  
 设置当前选定的颜色属性的颜色值。  
  
```  
virtual void UpdateColor(COLORREF color);
```  
  
### <a name="parameters"></a>参数  
 [in] `color`  
 RGB 颜色值。  
  
### <a name="remarks"></a>备注  
 此方法断言在调试模式下，如果属性网格控件的当前选定的属性不是一个颜色属性。  
  
##  <a name="a-namevalidateitemdataa--cmfcpropertygridctrlvalidateitemdata"></a><a name="validateitemdata"></a>CMFCPropertyGridCtrl::ValidateItemData  
 由该框架能验证属性数据调用。  
  
```  
virtual BOOL ValidateItemData(CMFCPropertyGridProperty* pProp);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `pProp`|指向属性。 未使用此参数。|  
  
### <a name="return-value"></a>返回值  
 总是为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 [CMFCPropertyGridCtrl::EndEditItem](#endedititem)方法调用此方法来验证数据。 默认情况下，此方法不使用其`pProp`参数和其返回值始终是`TRUE`。  
  
 如果重写此方法时，返回`TRUE`指定的属性数据是否有效。 否则，返回`FALSE`，在这种情况下该框架不会更新该属性。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)

