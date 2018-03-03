---
title: "CMFCButton 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCButton
- AFXBUTTON/CMFCButton
- AFXBUTTON/CMFCButton::CleanUp
- AFXBUTTON/CMFCButton::EnableFullTextTooltip
- AFXBUTTON/CMFCButton::EnableMenuFont
- AFXBUTTON/CMFCButton::EnableWindowsTheming
- AFXBUTTON/CMFCButton::GetToolTipCtrl
- AFXBUTTON/CMFCButton::IsAutoCheck
- AFXBUTTON/CMFCButton::IsAutorepeatCommandMode
- AFXBUTTON/CMFCButton::IsCheckBox
- AFXBUTTON/CMFCButton::IsChecked
- AFXBUTTON/CMFCButton::IsHighlighted
- AFXBUTTON/CMFCButton::IsPressed
- AFXBUTTON/CMFCButton::IsPushed
- AFXBUTTON/CMFCButton::IsRadioButton
- AFXBUTTON/CMFCButton::IsWindowsThemingEnabled
- AFXBUTTON/CMFCButton::SetAutorepeatMode
- AFXBUTTON/CMFCButton::SetCheckedImage
- AFXBUTTON/CMFCButton::SetFaceColor
- AFXBUTTON/CMFCButton::SetImage
- AFXBUTTON/CMFCButton::SetMouseCursor
- AFXBUTTON/CMFCButton::SetMouseCursorHand
- AFXBUTTON/CMFCButton::SetStdImage
- AFXBUTTON/CMFCButton::SetTextColor
- AFXBUTTON/CMFCButton::SetTextHotColor
- AFXBUTTON/CMFCButton::SetTooltip
- AFXBUTTON/CMFCButton::SizeToContent
- AFXBUTTON/CMFCButton::OnDraw
- AFXBUTTON/CMFCButton::OnDrawBorder
- AFXBUTTON/CMFCButton::OnDrawFocusRect
- AFXBUTTON/CMFCButton::OnDrawText
- AFXBUTTON/CMFCButton::OnFillBackground
- AFXBUTTON/CMFCButton::SelectFont
- AFXBUTTON/CMFCButton::m_bDrawFocus
- AFXBUTTON/CMFCButton::m_bHighlightChecked
- AFXBUTTON/CMFCButton::m_bRightImage
- AFXBUTTON/CMFCButton::m_bTransparent
- AFXBUTTON/CMFCButton::m_nAlignStyle
- AFXBUTTON/CMFCButton::m_nFlatStyle
dev_langs:
- C++
helpviewer_keywords:
- CMFCButton [MFC], CleanUp
- CMFCButton [MFC], EnableFullTextTooltip
- CMFCButton [MFC], EnableMenuFont
- CMFCButton [MFC], EnableWindowsTheming
- CMFCButton [MFC], GetToolTipCtrl
- CMFCButton [MFC], IsAutoCheck
- CMFCButton [MFC], IsAutorepeatCommandMode
- CMFCButton [MFC], IsCheckBox
- CMFCButton [MFC], IsChecked
- CMFCButton [MFC], IsHighlighted
- CMFCButton [MFC], IsPressed
- CMFCButton [MFC], IsPushed
- CMFCButton [MFC], IsRadioButton
- CMFCButton [MFC], IsWindowsThemingEnabled
- CMFCButton [MFC], SetAutorepeatMode
- CMFCButton [MFC], SetCheckedImage
- CMFCButton [MFC], SetFaceColor
- CMFCButton [MFC], SetImage
- CMFCButton [MFC], SetMouseCursor
- CMFCButton [MFC], SetMouseCursorHand
- CMFCButton [MFC], SetStdImage
- CMFCButton [MFC], SetTextColor
- CMFCButton [MFC], SetTextHotColor
- CMFCButton [MFC], SetTooltip
- CMFCButton [MFC], SizeToContent
- CMFCButton [MFC], OnDraw
- CMFCButton [MFC], OnDrawBorder
- CMFCButton [MFC], OnDrawFocusRect
- CMFCButton [MFC], OnDrawText
- CMFCButton [MFC], OnFillBackground
- CMFCButton [MFC], SelectFont
- CMFCButton [MFC], m_bDrawFocus
- CMFCButton [MFC], m_bHighlightChecked
- CMFCButton [MFC], m_bRightImage
- CMFCButton [MFC], m_bTransparent
- CMFCButton [MFC], m_nAlignStyle
- CMFCButton [MFC], m_nFlatStyle
ms.assetid: 4b32f57c-7a53-4734-afb9-d47e3359f62e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6d496cf079cd56d8260c5fd8072809bc05559ef2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcbutton-class"></a>CMFCButton 类
`CMFCButton`类添加了功能[CButton](../../mfc/reference/cbutton-class.md)如对齐按钮文本、 组合按钮文本和图像、 选择光标以及指定工具提示的类。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCButton : public CButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCButton::CMFCButton`|默认构造函数。|  
|`CMFCButton::~CMFCButton`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCButton::CleanUp](#cleanup)|重置内部变量并释放已分配的资源，例如图像、 位图和图标。|  
|`CMFCButton::CreateObject`|由框架用于创建此类类型的动态实例。|  
|`CMFCButton::DrawItem`|当所有者描述的按钮的可视方位发生更改时由框架调用。 (重写[CButton::DrawItem](../../mfc/reference/cbutton-class.md#drawitem)。)|  
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|指定是否在大工具提示窗口或小工具提示窗口中的文本的截断的版本中显示工具提示的完整文本。|  
|[CMFCButton::EnableMenuFont](#enablemenufont)|指定按钮文本字体是否是应用程序菜单字体相同。|  
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|指定按钮边框的样式是否对应于当前的 Windows 主题。|  
|`CMFCButton::GetThisClass`|由框架用于获取指向的指针[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型关联的对象。|  
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|返回到基础的工具提示控件的引用。|  
|[CMFCButton::IsAutoCheck](#isautocheck)|指示是否复选框或单选按钮为自动按钮。|  
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|指示按钮是否设置为自动重复模式。|  
|[CMFCButton::IsCheckBox](#ischeckbox)|指示按钮是否复选框按钮。|  
|[CMFCButton::IsChecked](#ischecked)|指示是否检查当前的按钮。|  
|[CMFCButton::IsHighlighted](#ishighlighted)|指示一个按钮将突出显示。|  
|[CMFCButton::IsPressed](#ispressed)|指示是否为推送并突出显示按钮。|  
|[CMFCButton::IsPushed](#ispushed)|指示是否按下按钮。|  
|[CMFCButton::IsRadioButton](#isradiobutton)|指示按钮是否是一个单选按钮。|  
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|指示按钮边框的样式是否对应于当前的 Windows 主题。|  
|`CMFCButton::OnDrawParentBackground`|指定的区域中绘制背景的按钮的父级。 (重写[AFX_GLOBAL_DATA::DrawParentBackground](../../mfc/reference/afx-global-data-structure.md)|  
|`CMFCButton::PreTranslateMessage`|翻译窗口消息之前被发送到[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函数。 （重写 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。）|  
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|将一个按钮设置为自动重复模式。|  
|[CMFCButton::SetCheckedImage](#setcheckedimage)|设置为已选中按钮的图像。|  
|[CMFCButton::SetFaceColor](#setfacecolor)|设置按钮文本的背景色。|  
|[CMFCButton::SetImage](#setimage)|设置按钮的图像。|  
|[CMFCButton::SetMouseCursor](#setmousecursor)|设置光标图像。|  
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|将光标设置为一只手的映像。|  
|[CMFCButton::SetStdImage](#setstdimage)|使用`CMenuImages`对象以设置按钮图像。|  
|[CMFCButton::SetTextColor](#settextcolor)|设置未选择一个按钮的按钮文本的颜色。|  
|[CMFCButton::SetTextHotColor](#settexthotcolor)|设置选择一个按钮的按钮文本的颜色。|  
|[CMFCButton::SetTooltip](#settooltip)|将工具提示与按钮相关联。|  
|[CMFCButton::SizeToContent](#sizetocontent)|调整大小以包含其按钮文本和图像的按钮。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCButton::OnDraw](#ondraw)|由框架调用以绘制一个按钮。|  
|[CMFCButton::OnDrawBorder](#ondrawborder)|由框架调用以绘制边框的按钮。|  
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|由框架调用以绘制聚焦框按钮。|  
|[CMFCButton::OnDrawText](#ondrawtext)|由框架调用以绘制按钮文本。|  
|[CMFCButton::OnFillBackground](#onfillbackground)|由框架调用以绘制背景的按钮文本。|  
|[CMFCButton::SelectFont](#selectfont)|检索与指定的设备上下文关联的字体。|  
  
### <a name="data-members"></a>数据成员  
  
|name|描述|  
|----------|-----------------|  
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|指示是否周围绘制聚焦框按钮。|  
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|指示是否在光标悬停在其上时突出显示 BS_CHECKBOX 样式按钮。|  
|[CMFCButton::m_bRightImage](#m_brightimage)|指示是否在右侧的按钮上显示图像。|  
|[CMFCButton::m_bTransparent](#m_btransparent)|指示按钮是否是透明的。|  
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|指定按钮文本的对齐方式。|  
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|指定此按钮时，如边框、 平整用平面或 3D 样式。|  
  
## <a name="remarks"></a>备注  
 按钮的其他类型都派生自`CMFCButton`类，如[CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md)类，该类支持超链接，与`CMFCColorButton`类，该类支持颜色选取器对话框。  
  
 样式`CMFCButton`对象可以是*三维*，*平面*，*用平面*或*无边框*。 可以在左侧、 顶部或一个按钮的中心对齐按钮文本。 在运行时，你可以控制按钮显示文本、 图像或文本和图像。 你还可以指定将光标悬停在按钮上时，会显示特定光标图像。  
  
 直接在代码中，或通过使用创建的按钮控件**MFC 类向导**工具和对话框模板。 如果直接创建的按钮控件，添加`CMFCButton`变量与你的应用程序，然后调用构造函数和`Create`方法`CMFCButton`对象。 如果你使用**MFC 类向导**，添加`CButton`变量与你的应用程序，然后将更改从变量的类型`CButton`到`CMFCButton`。  
  
 若要处理对话框框中应用程序中的通知消息，添加一个消息映射条目和每个通知事件处理程序。 发送的通知`CMFCButton`对象是由发送相同`CButton`对象。  
  
## <a name="example"></a>示例  
 下面的示例演示如何通过使用中的各种方法来配置该按钮的属性`CMFCButton`类。 此示例摘自的[新控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]  
[!code-cpp[NVC_MFC_NewControls#32](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_3.cpp)]  
[!code-cpp[NVC_MFC_NewControls#33](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_4.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
## <a name="requirements"></a>惠?  
 **标头：** afxbutton.h  
  
##  <a name="cleanup"></a>CMFCButton::CleanUp  
 重置内部变量并释放已分配的资源，例如图像、 位图和图标。  
  
```  
virtual void CleanUp();
```  
  
##  <a name="enablefulltexttooltip"></a>CMFCButton::EnableFullTextTooltip  
 指定是否在大工具提示窗口或小工具提示窗口中的文本的截断的版本中显示工具提示的完整文本。  
  
```  
void EnableFullTextTooltip(BOOL bOn=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bOn`  
 `TRUE`若要显示所有属性。`FALSE`到截断的显示文本。  
  
### <a name="remarks"></a>备注  
  
##  <a name="enablemenufont"></a>CMFCButton::EnableMenuFont  
 指定按钮文本字体是否是应用程序菜单字体相同。  
  
```  
void EnableMenuFont(
    BOOL bOn=TRUE,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bOn`  
 `TRUE`要用作按钮文本字体; 应用程序菜单字体`FALSE`用于系统字体。 默认值为 `TRUE`。  
  
 [in] `bRedraw`  
 `TRUE`若要立即重绘屏幕上。否则为`FALSE`。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 如果此方法不执行用于指定按钮文本字体，则可以指定使用的字体[CWnd::SetFont](../../mfc/reference/cwnd-class.md#setfont)方法。 如果你根本未指定一种字体，框架将设置默认字体。  
  
##  <a name="enablewindowstheming"></a>CMFCButton::EnableWindowsTheming  
 指定按钮边框的样式是否对应于当前的 Windows 主题。  
  
```  
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要使用当前的 Windows 主题来绘制按钮的边框。`FALSE`不使用 Windows 主题。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 此方法会影响你派生自的应用程序中的所有按钮`CMFCButton`类。  
  
##  <a name="gettooltipctrl"></a>CMFCButton::GetToolTipCtrl  
 返回到基础的工具提示控件的引用。  
  
```  
CToolTipCtrl& GetToolTipCtrl();
```  
  
### <a name="return-value"></a>返回值  
 对基础的工具提示控件的引用。  
  
### <a name="remarks"></a>备注  
  
##  <a name="isautocheck"></a>CMFCButton::IsAutoCheck  
 指示是否复选框或单选按钮为自动按钮。  
  
```  
BOOL IsAutoCheck() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果该按钮具有，样式 BS_AUTOCHECKBOX 或 BS_AUTORADIOBUTTON;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="isautorepeatcommandmode"></a>CMFCButton::IsAutorepeatCommandMode  
 指示按钮是否设置为自动重复模式。  
  
```  
BOOL IsAutorepeatCommandMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果按钮设置为自动重复模式，则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 使用[CMFCButton::SetAutorepeatMode](#setautorepeatmode)方法将一个按钮设置为自动重复模式。  
  
##  <a name="ischeckbox"></a>CMFCButton::IsCheckBox  
 指示按钮是否复选框按钮。  
  
```  
BOOL IsCheckBox() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果按钮有 BS_CHECKBOX 或 BS_AUTOCHECKBOX 样式; 为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
  
##  <a name="ischecked"></a>CMFCButton::IsChecked  
 指示是否检查当前的按钮。  
  
```  
BOOL IsChecked() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果已选中当前按钮;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架将使用不同的方式，以指示检查了不同类型的按钮。 例如，当它包含一个点; 时，一个单选按钮将检查包含时选中复选框**X**。  
  
##  <a name="ishighlighted"></a>CMFCButton::IsHighlighted  
 指示一个按钮将突出显示。  
  
```  
BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>返回值  
 突出显示按钮; 如果为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 当鼠标悬停在按钮上时，将突出显示按钮。  
  
##  <a name="ispressed"></a>CMFCButton::IsPressed  
 指示是否为推送并突出显示按钮。  
  
```  
BOOL IsPressed() const;  
```  
  
### <a name="return-value"></a>返回值  
 按下了按钮; 如果为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
  
##  <a name="ispushed"></a>CMFCButton::IsPushed  
 指示是否按下按钮。  
  
```  
BOOL IsPushed() const;  
```  
  
### <a name="return-value"></a>返回值  
 按下按钮; 如果为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
  
##  <a name="isradiobutton"></a>CMFCButton::IsRadioButton  
 指示按钮是否是一个单选按钮。  
  
```  
BOOL IsRadioButton() const;  
```  
  
### <a name="return-value"></a>返回值  
 按钮样式 BS_RADIOBUTTON 或 BS_AUTORADIOBUTTON; 如果为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
  
##  <a name="iswindowsthemingenabled"></a>CMFCButton::IsWindowsThemingEnabled  
 指示按钮边框的样式是否对应于当前的 Windows 主题。  
  
```  
static BOOL IsWindowsThemingEnabled();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果按钮边框的样式对应于当前的 Windows 主题;否则为`FALSE`。  
  
##  <a name="m_bdrawfocus"></a>CMFCButton::m_bDrawFocus  
 指示是否周围绘制聚焦框按钮。  
  
```  
BOOL m_bDrawFocus;  
```  
  
### <a name="remarks"></a>备注  
 设置`m_bDrawFocus`成员`TRUE`指定框架将周围绘制聚焦框按钮的文本和图像如果该按钮将接收焦点。  
  
 `CMFCButton` 构造函数将此成员初始化为 `TRUE`。  
  
##  <a name="m_bhighlightchecked"></a>CMFCButton::m_bHighlightChecked  
 指示是否在光标悬停在其上时突出显示 BS_CHECKBOX 样式按钮。  
  
```  
BOOL m_bHighlightChecked;  
```  
  
### <a name="remarks"></a>备注  
 设置`m_bHighlightChecked`成员`TRUE`指定，框架将突出显示 BS_CHECKBOX 样式按钮鼠标悬停在其上时。  
  
##  <a name="m_brightimage"></a>CMFCButton::m_bRightImage  
 指示是否在右侧的按钮上显示图像。  
  
```  
BOOL m_bRightImage;  
```  
  
### <a name="remarks"></a>备注  
 设置`m_bRightImage`成员`TRUE`以指定框架将右侧的按钮的文本标签中显示按钮的图像。  
  
##  <a name="m_btransparent"></a>CMFCButton::m_bTransparent  
 指示按钮是否是透明的。  
  
```  
BOOL m_bTransparent;  
```  
  
### <a name="remarks"></a>备注  
 设置`m_bTransparent`成员`TRUE`指定，框架将创建按钮透明。 `CMFCButton` 构造函数将此成员初始化为 `FALSE`。  
  
##  <a name="m_nalignstyle"></a>CMFCButton::m_nAlignStyle  
 指定按钮文本的对齐方式。  
  
```  
AlignStyle m_nAlignStyle;  
```  
  
### <a name="remarks"></a>备注  
 使用以下项之一`CMFCButton::AlignStyle`枚举值来指定按钮文本的对齐方式：  
  
|“值”|描述|  
|-----------|-----------------|  
|ALIGN_CENTER|（默认值）对齐到中心按钮的按钮文本。|  
|ALIGN_LEFT|对齐按钮左侧的按钮文本。|  
|ALIGN_RIGHT|对齐按钮右侧的按钮文本。|  
  
 `CMFCButton`构造函数将初始化到 ALIGN_CENTER 此成员。  
  
##  <a name="m_nflatstyle"></a>CMFCButton::m_nFlatStyle  
 指定此按钮时，如边框、 平整用平面或 3D 样式。  
  
```  
FlatStyle  m_nFlatStyle;  
```  
  
### <a name="remarks"></a>备注  
 下表列出`CMFCButton::m_nFlatStyle`指定按钮的外观的枚举值。  
  
|“值”|描述|  
|-----------|-----------------|  
|BUTTONSTYLE_3D|（默认值）按钮显示为具有高的三维边。 单击该按钮，该按钮显示为按到深层缩进。|  
|BUTTONSTYLE_FLAT|当鼠标不会暂停到按钮上方中时，按钮似乎是二维并且没有引发的边。 当鼠标停留到按钮上方时，按钮显示为具有低，三维边。 单击该按钮，该按钮显示为按到浅表缩进。|  
|BUTTONSTYLE_SEMIFLAT|按钮显示为具有低，三维边。 单击该按钮，该按钮显示为按到深层缩进。|  
|BUTTONSTYLE_NOBORDERS|该按钮不会不引发两边，并始终显示二维。 按钮似乎未单击时其到缩进按下。|  
  
 `CMFCButton` 构造函数将此成员初始化为 `BUTTONSTYLE_3D`。  
  
### <a name="example"></a>示例  
 下面的示例演示如何设置的值`m_nFlatStyle`中的成员变量`CMFCButton`类。 此示例摘自[新控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]  
  
##  <a name="ondraw"></a>CMFCButton::OnDraw  
 由框架调用以绘制一个按钮。  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    UINT uiState);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 对限定按钮的矩形的引用。  
  
 [in] `uiState`  
 当前的按钮状态。 有关详细信息，请参阅`itemState`的成员[DRAWITEMSTRUCT 结构](../../mfc/reference/drawitemstruct-structure.md)主题。  
  
### <a name="remarks"></a>备注  
 重写此方法以使用你自己的代码绘制一个按钮。  
  
##  <a name="ondrawborder"></a>CMFCButton::OnDrawBorder  
 由框架调用以绘制边框的按钮。  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect& rectClient,  
    UINT uiState);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rectClient`  
 对限定按钮的矩形的引用。  
  
 [in] `uiState`  
 当前的按钮状态。 有关详细信息，请参阅`itemState`的成员[DRAWITEMSTRUCT 结构](../../mfc/reference/drawitemstruct-structure.md)主题。  
  
### <a name="remarks"></a>备注  
 重写此方法以使用你自己的代码绘制边框。  
  
##  <a name="ondrawfocusrect"></a>CMFCButton::OnDrawFocusRect  
 由框架调用以绘制聚焦框按钮。  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rectClient`  
 对限定按钮的矩形的引用。  
  
### <a name="remarks"></a>备注  
 重写此方法以使用你自己的代码绘制聚焦框。  
  
##  <a name="ondrawtext"></a>CMFCButton::OnDrawText  
 由框架调用以绘制按钮文本。  
  
```  
virtual void OnDrawText(
    CDC* pDC,  
    const CRect& rect,  
    const CString& strText,  
    UINT uiDTFlags,  
    UINT uiState);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 对限定按钮的矩形的引用。  
  
 [in] `strText`  
 要绘制的文本。  
  
 [in] `uiDTFlags`  
 指定如何设置文本格式的标志。 有关详细信息，请参阅`nFormat`参数[CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)方法。  
  
 [in] `uiState`  
 （保留）。  
  
### <a name="remarks"></a>备注  
 重写此方法以使用你自己的代码绘制按钮文本。  
  
##  <a name="onfillbackground"></a>CMFCButton::OnFillBackground  
 由框架调用以绘制背景的按钮文本。  
  
```  
virtual void OnFillBackground(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rectClient`  
 对限定按钮的矩形的引用。  
  
### <a name="remarks"></a>备注  
 重写此方法以使用你自己的代码绘制按钮的背景。  
  
##  <a name="selectfont"></a>CMFCButton::SelectFont  
 检索与指定的设备上下文关联的字体。  
  
```  
virtual CFont* SelectFont(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
### <a name="return-value"></a>返回值  
 重写此方法以使用你自己的代码检索字体。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setautorepeatmode"></a>CMFCButton::SetAutorepeatMode  
 将一个按钮设置为自动重复模式。  
  
```  
void SetAutorepeatMode(int nTimeDelay=500);
```  
  
### <a name="parameters"></a>参数  
 [in] `nTimeDelay`  
 一个非负数字，指定的时间间隔向父窗口发送的消息。 以毫秒为单位的间隔，其默认值为 500 毫秒。 指定零以禁用自动重复消息模式。  
  
### <a name="remarks"></a>备注  
 此方法将导致不断 WM_COMMAND 消息发送到父窗口之前释放按钮时，该按钮或`nTimeDelay`参数设置为零。  
  
##  <a name="setcheckedimage"></a>CMFCButton::SetCheckedImage  
 设置为已选中按钮的图像。  
  
```  
void SetCheckedImage(
    HICON hIcon,  
    BOOL bAutoDestroy=TRUE,  
    HICON hIconHot=NULL,  
    HICON hIconDisabled=NULL,  
    BOOL bAlphaBlend=FALSE);

 
void SetCheckedImage(
    HBITMAP hBitmap,  
    BOOL bAutoDestroy=TRUE,  
    HBITMAP hBitmapHot=NULL,  
    BOOL bMap3dColors=TRUE,  
    HBITMAP hBitmapDisabled=NULL);

 
void SetCheckedImage(
    UINT uiBmpResId,  
    UINT uiBmpHotResId=0,  
    UINT uiBmpDsblResID=0);
```  
  
### <a name="parameters"></a>参数  
 [in] `hIcon`  
 包含的位图和掩码为新映像的图标的句柄。  
  
 [in] `bAutoDestroy`  
 `TRUE`指定位图的资源会自动; 销毁否则为`FALSE`。 默认值为 `TRUE`。  
  
 [in] `hIconHot`  
 包含所选状态的图像的图标的句柄。  
  
 [in] `hBitmap`  
 用于包含未选中状态的图像的位图的句柄。  
  
 [in] `hBitmapHot`  
 用于包含所选状态的图像的位图的句柄。  
  
 [in] `bMap3dColors`  
 指定按钮背景; 的透明颜色也就是说，按钮的表面。 `TRUE`若要使用的颜色值 RGB （192、 192、 192）;`FALSE`使用定义的颜色值`AFX_GLOBAL_DATA::clrBtnFace`。  
  
 [in] `uiBmpResId`  
 非选择的图像的资源 ID。  
  
 [in] `uiBmpHotResId`  
 所选映像的资源 ID。  
  
 [in] `hIconDisabled`  
 禁用的图像的图标的句柄。  
  
 [in] `hBitmapDisabled`  
 包含禁用的图像的位图的句柄。  
  
 [in] `uiBmpDsblResID`  
 已禁用的位图的资源 ID。  
  
 [in] `bAlphaBlend`  
 `TRUE`若要使用仅使用 alpha 通道; 的 32 位映像`FALSE`，若要不使用仅 alpha 通道的图像。 默认值为 `FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setfacecolor"></a>CMFCButton::SetFaceColor  
 设置按钮文本的背景色。  
  
```  
void SetFaceColor(
    COLORREF crFace,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `crFace`  
 RGB 颜色值。  
  
 [in] `bRedraw`  
 `TRUE`若要立即; 重绘屏幕否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用此方法来定义新的填充颜色按钮背景 （面朝）。 请注意，不是背景时填写[CMFCButton::m_bTransparent](#m_btransparent)成员变量是`TRUE`。  
  
##  <a name="setimage"></a>CMFCButton::SetImage  
 设置按钮的图像。  
  
```  
void SetImage(
    HICON hIcon,  
    BOOL bAutoDestroy=TRUE,  
    HICON hIconHot=NULL,  
    HICON hIconDisabled=NULL,  
    BOOL bAlphaBlend=FALSE);

 
void SetImage(
    HBITMAP hBitmap,  
    BOOL bAutoDestroy=TRUE,  
    HBITMAP hBitmapHot=NULL,  
    BOOL bMap3dColors=TRUE,  
    HBITMAP hBitmapDisabled=NULL);

 
void SetImage(
    UINT uiBmpResId,  
    UINT uiBmpHotResId=0,  
    UINT uiBmpDsblResID=0);
```  
  
### <a name="parameters"></a>参数  
 [in] `hIcon`  
 包含的位图和掩码为新映像的图标的句柄。  
  
 [in] `bAutoDestroy`  
 `TRUE`指定位图的资源会自动; 销毁否则为`FALSE`。 默认值为 `TRUE`。  
  
 [in] `hIconHot`  
 包含所选状态的图像的图标的句柄。  
  
 [in] `hBitmap`  
 用于包含未选中状态的图像的位图的句柄。  
  
 [in] `hBitmapHot`  
 用于包含所选状态的图像的位图的句柄。  
  
 [in] `uiBmpResId`  
 非选择的图像的资源 ID。  
  
 [in] `uiBmpHotResId`  
 所选映像的资源 ID。  
  
 [in] `bMap3dColors`  
 指定按钮背景; 的透明颜色也就是说，按钮的表面。 `TRUE`若要使用的颜色值 RGB （192、 192、 192）;`FALSE`使用定义的颜色值`AFX_GLOBAL_DATA::clrBtnFace`。  
  
 [in] `hIconDisabled`  
 禁用的图像的图标的句柄。  
  
 [in] `hBitmapDisabled`  
 包含禁用的图像的位图的句柄。  
  
 [in] `uiBmpDsblResID`  
 已禁用的位图的资源 ID。  
  
 [in] `bAlphaBlend`  
 `TRUE`若要使用仅使用 alpha 通道; 的 32 位映像`FALSE`，若要不使用仅 alpha 通道的图像。 默认值为 `FALSE`。  
  
### <a name="remarks"></a>备注  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用各种版本的`SetImage`中的方法`CMFCButton`类。 此示例摘自的[新控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]  
  
##  <a name="setmousecursor"></a>CMFCButton::SetMouseCursor  
 设置光标图像。  
  
```  
void SetMouseCursor(HCURSOR hcursor);
```  
  
### <a name="parameters"></a>参数  
 [in] `hcursor`  
 光标的句柄。  
  
### <a name="remarks"></a>备注  
 使用此方法将光标图像，如手形光标，与按钮相关联。 从应用程序资源加载光标。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`SetMouseCursor`中的方法`CMFCButton`类。 中的代码示例摘自[新控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]  
  
##  <a name="setmousecursorhand"></a>CMFCButton::SetMouseCursorHand  
 将光标设置为一只手的映像。  
  
```  
void SetMouseCursorHand();
```  
  
### <a name="remarks"></a>备注  
 使用此方法将手形光标图像与按钮相关联。 从应用程序资源加载光标。  
  
##  <a name="setstdimage"></a>CMFCButton::SetStdImage  
 使用`CMenuImages`对象以设置按钮图像。  
  
```  
void SetStdImage(
    CMenuImages::IMAGES_IDS id,  
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,  
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```  
  
### <a name="parameters"></a>参数  
 [in] `id`  
 其中一个按钮图像标识符中定义`CMenuImage::IMAGES_IDS`枚举。 映像值指定如箭头、 pin 和单选按钮的图像。  
  
 [in] `state`  
 其中一个按钮图像状态标识符中定义`CMenuImages::IMAGE_STATE`枚举。 映像状态指定如黑色、 灰色、 浅灰色白和暗灰色的按钮颜色。 默认值为 `CMenuImages::ImageBlack`。  
  
 [in] `idDisabled`  
 其中一个按钮图像标识符中定义`CMenuImage::IMAGES_IDS`枚举。 图指示的按钮被禁用。 默认值是第一个按钮图像 ( `CMenuImages::IdArrowDown`)。  
  
### <a name="remarks"></a>备注  
  
##  <a name="settextcolor"></a>CMFCButton::SetTextColor  
 设置未选择一个按钮的按钮文本的颜色。  
  
```  
void SetTextColor(COLORREF clrText);
```  
  
### <a name="parameters"></a>参数  
 [in] `clrText`  
 RGB 颜色值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="settexthotcolor"></a>CMFCButton::SetTextHotColor  
 设置选择一个按钮的按钮文本的颜色。  
  
```  
void SetTextHotColor(COLORREF clrTextHot);
```  
  
### <a name="parameters"></a>参数  
 [in] `clrTextHot`  
 RGB 颜色值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="settooltip"></a>CMFCButton::SetTooltip  
 将工具提示与按钮相关联。  
  
```  
void SetTooltip(LPCTSTR lpszToolTipText);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszToolTipText`  
 为工具提示的文本指针。 指定 NULL 可禁用工具提示。  
  
### <a name="remarks"></a>备注  
  
##  <a name="sizetocontent"></a>CMFCButton::SizeToContent  
 调整大小以包含其按钮文本和图像的按钮。  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bCalcOnly`  
 `TRUE`若要计算，但不是能更改按钮; 的新大小`FALSE`更改按钮的大小。 默认值为 `FALSE`。  
  
### <a name="return-value"></a>返回值  
 A`CSize`对象，其中包含按钮的新大小。  
  
### <a name="remarks"></a>备注  
 默认情况下，此方法计算新的大小，其中包括水平边距为 10 个像素和垂直边距为 5 个像素。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCLinkCtrl 类](../../mfc/reference/cmfclinkctrl-class.md)   
 [CMFCColorButton 类](../../mfc/reference/cmfccolorbutton-class.md)   
 [CMFCMenuButton 类](../../mfc/reference/cmfcmenubutton-class.md)
