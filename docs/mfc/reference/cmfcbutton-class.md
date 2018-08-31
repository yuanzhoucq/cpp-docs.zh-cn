---
title: CMFCButton 类 |Microsoft Docs
ms.custom: ''
ms.date: 08/28/2018
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8385320b51efedd214424385babc5f03d5559873
ms.sourcegitcommit: 220fd4fda829f810e15fc1a1d98ab43c46201b47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2018
ms.locfileid: "43352711"
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
|[CMFCButton::CleanUp](#cleanup)|重置内部变量，并释放已分配的资源，例如图像、 位图和图标。|  
|`CMFCButton::CreateObject`|由框架用于创建此类类型的动态实例。|  
|`CMFCButton::DrawItem`|所有者描述的按钮的可视特征发生更改时由框架调用。 (重写[CButton::DrawItem](../../mfc/reference/cbutton-class.md#drawitem)。)|  
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|指定是否在大型的工具提示窗口或小工具提示窗口中的文本的截断的版本中显示完整的工具提示文本。|  
|[CMFCButton::EnableMenuFont](#enablemenufont)|指定按钮的文本字体是否是应用程序菜单字体相同。|  
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|指定按钮边框的样式是否对应于当前 Windows 主题。|  
|`CMFCButton::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型相关联的对象。|  
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|返回到基础的工具提示控件的引用。|  
|[CMFCButton::IsAutoCheck](#isautocheck)|指示复选框或单选按钮是一个自动按钮。|  
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|指示是否将一个按钮设置为自动重复模式。|  
|[CMFCButton::IsCheckBox](#ischeckbox)|指示 button 是否是复选框按钮。|  
|[CMFCButton::IsChecked](#ischecked)|指示是否检查当前的按钮。|  
|[CMFCButton::IsHighlighted](#ishighlighted)|指示是否突出显示一个按钮。|  
|[CMFCButton::IsPressed](#ispressed)|指示按钮是否被推送和突出显示。|  
|[CMFCButton::IsPushed](#ispushed)|指示是否按下按钮。|  
|[CMFCButton::IsRadioButton](#isradiobutton)|指示 button 是否是单选按钮。|  
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|指示按钮边框的样式是否对应于当前 Windows 主题。|  
|`CMFCButton::OnDrawParentBackground`|在指定区域中绘制按钮的父项的背景。 (重写[AFX_GLOBAL_DATA::DrawParentBackground](../../mfc/reference/afx-global-data-structure.md)|  
|`CMFCButton::PreTranslateMessage`|将窗口消息调度到之前[TranslateMessage](https://msdn.microsoft.com/library/windows/desktop/ms644955)并[DispatchMessage](https://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函数。 （重写 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。）|  
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|将一个按钮设置为自动重复模式。|  
|[CMFCButton::SetCheckedImage](#setcheckedimage)|设置选中的按钮的图像。|  
|[CMFCButton::SetFaceColor](#setfacecolor)|设置按钮文本的背景色。|  
|[CMFCButton::SetImage](#setimage)|设置按钮的图像。|  
|[CMFCButton::SetMouseCursor](#setmousecursor)|设置光标图像。|  
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|将光标设置到手的形状的图像。|  
|[CMFCButton::SetStdImage](#setstdimage)|使用`CMenuImages`对象来设置按钮的图像。|  
|[CMFCButton::SetTextColor](#settextcolor)|设置未选择的按钮的按钮文本的颜色。|  
|[CMFCButton::SetTextHotColor](#settexthotcolor)|设置处于选中状态的按钮的按钮文本的颜色。|  
|[CMFCButton::SetTooltip](#settooltip)|将工具提示与按钮相关联。|  
|[CMFCButton::SizeToContent](#sizetocontent)|调整大小以包含其按钮文本和图像的按钮。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCButton::OnDraw](#ondraw)|由框架调用以绘制一个按钮。|  
|[CMFCButton::OnDrawBorder](#ondrawborder)|由框架调用以绘制边框的按钮。|  
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|由框架调用以绘制聚焦框的按钮。|  
|[CMFCButton::OnDrawText](#ondrawtext)|由框架调用以绘制按钮文本。|  
|[CMFCButton::OnFillBackground](#onfillbackground)|由框架调用以绘制控件背景的按钮文本。|  
|[CMFCButton::SelectFont](#selectfont)|检索与指定的设备上下文关联的字体。|  
  
### <a name="data-members"></a>数据成员  
  
|name|描述|  
|----------|-----------------|  
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|指定按钮文本的对齐方式。|  
|[CMFCButton::m_bDontUseWinXPTheme](#m_bDontUseWinXPTheme)|指定是否使用 Windows XP 主题。|
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|指示是否绘制一个聚焦框按钮周围。| 
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|指定的按钮，如无边距、 平面的以平面或 3D 样式。|  
|[CMFCButton::m_bGrayDisabled](#m_bGrayDisabled)|为 TRUE 时，启用已禁用的按钮绘制为灰显。|
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|指示是否在光标悬停时突出显示 BS_CHECKBOX 样式的按钮。|  
|[CMFCButton::m_bResponseOnButtonDown](#m_bResponseOnButtonDown)|指示是否对按钮按下事件做出响应。|
|[CMFCButton::m_bRightImage](#m_brightimage)|指示是否在按钮的右侧显示的图像。|
|[CMFCButton::m_bTopImage](#m_bTopImage)| 指示图像是否为该按钮上。|
|[CMFCButton::m_bTransparent](#m_btransparent)|指示按钮是否是透明的。|  
|[CMFCButton::m_bWasDblClk](#m_bWasDblClk)| 指示最后一个单击事件是一次双击。|
  
## <a name="remarks"></a>备注  
 其他类型的按钮派生自`CMFCButton`类，如[CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md)类，该类支持超链接，并`CMFCColorButton`类，该类支持颜色选取器对话框。  
  
 样式`CMFCButton`对象可以是*3D*，*平面*，*半平面*或*没有边框*。 可以在左侧、 顶部或一个按钮的中心对齐按钮文本。 在运行时，可以控制该按钮显示的文本、 图像或文本和图像。 此外可以指定将光标悬停在按钮上时，显示特定光标图像。  
  
 在代码中直接或通过使用创建的按钮控件**MFC 类向导**工具和对话框模板。 如果直接创建一个按钮控件，请添加`CMFCButton`应用程序，然后调用构造函数与变量和`Create`方法的`CMFCButton`对象。 如果您使用**MFC 类向导**，添加`CButton`变量到应用程序，然后将更改从变量的类型`CButton`到`CMFCButton`。  
  
 若要处理对话框 box 应用程序中的通知消息，添加消息映射条目和每个通知的事件处理程序。 由发送的通知`CMFCButton`对象将与发送的那些相同`CButton`对象。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法中的配置按钮属性`CMFCButton`类。 此示例摘自[新的控件示例](../../visual-cpp-samples.md)。  
  
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
  
## <a name="requirements"></a>要求  
 **标头：** afxbutton.h  
  
##  <a name="cleanup"></a>  CMFCButton::CleanUp  
 重置内部变量，并释放已分配的资源，例如图像、 位图和图标。  
  
```  
virtual void CleanUp();
```  
  
##  <a name="enablefulltexttooltip"></a>  CMFCButton::EnableFullTextTooltip  
 指定是否在大型的工具提示窗口或小工具提示窗口中的文本的截断的版本中显示完整的工具提示文本。  
  
```  
void EnableFullTextTooltip(BOOL bOn=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in]*bOn*  
 为 TRUE，则显示所有属性。FALSE 截断的显示文本。  
  
### <a name="remarks"></a>备注  
  
##  <a name="enablemenufont"></a>  CMFCButton::EnableMenuFont  
 指定按钮的文本字体是否是应用程序菜单字体相同。  
  
```  
void EnableMenuFont(
    BOOL bOn=TRUE,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in]*bOn*  
 若要为按钮文本字体; 使用的应用程序菜单字体，则返回 TRUE为 FALSE，则使用系统字体。 默认值为 TRUE。  
  
 [in]*bRedraw*  
 为 TRUE，则立即重绘屏幕上。否则为 FALSE。 默认值为 TRUE。  
  
### <a name="remarks"></a>备注  
 如果此方法不执行用于指定按钮文本字体，则可以指定与字体[CWnd::SetFont](../../mfc/reference/cwnd-class.md#setfont)方法。 如果您根本不指定一种字体，框架将设置默认字体。  
  
##  <a name="enablewindowstheming"></a>  CMFCButton::EnableWindowsTheming  
 指定按钮边框的样式是否对应于当前 Windows 主题。  
  
```  
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in]*bEnable*  
 为 TRUE，则使用当前 Windows 主题来绘制按钮边框。为 FALSE，则不使用 Windows 主题。 默认值为 TRUE。  
  
### <a name="remarks"></a>备注  
 此方法会影响派生自应用程序中的所有按钮`CMFCButton`类。  
  
##  <a name="gettooltipctrl"></a>  CMFCButton::GetToolTipCtrl  
 返回到基础的工具提示控件的引用。  
  
```  
CToolTipCtrl& GetToolTipCtrl();
```  
  
### <a name="return-value"></a>返回值  
 对基础的工具提示控件的引用。  
  
### <a name="remarks"></a>备注  
  
##  <a name="isautocheck"></a>  CMFCButton::IsAutoCheck  
 指示复选框或单选按钮是一个自动按钮。  
  
```  
BOOL IsAutoCheck() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果该按钮具有样式为 BS_AUTOCHECKBOX 或 BS_AUTORADIOBUTTON;否则为 FALSE。  
  
### <a name="remarks"></a>备注  
  
##  <a name="isautorepeatcommandmode"></a>  CMFCButton::IsAutorepeatCommandMode  
 指示是否将一个按钮设置为自动重复模式。  
  
```  
BOOL IsAutorepeatCommandMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果该按钮设置为自动重复模式，则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 使用[CMFCButton::SetAutorepeatMode](#setautorepeatmode)方法将一个按钮设置为自动重复模式。  
  
##  <a name="ischeckbox"></a>  CMFCButton::IsCheckBox  
 指示 button 是否是复选框按钮。  
  
```  
BOOL IsCheckBox() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果该按钮具有 BS_CHECKBOX 或 BS_AUTOCHECKBOX 样式; 则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
  
##  <a name="ischecked"></a>  CMFCButton::IsChecked  
 指示是否检查当前的按钮。  
  
```  
BOOL IsChecked() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果当前按钮被选中; 则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 框架将使用不同的方式，以指示检查了不同类型的按钮。 当它包含一个句点; 例如，选中单选按钮包含时选中复选框**X**。  
  
##  <a name="ishighlighted"></a>  CMFCButton::IsHighlighted  
 指示是否突出显示一个按钮。  
  
```  
BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果该按钮将突出显示; 则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 当鼠标悬停在按钮上时，将突出显示一个按钮。  
  
##  <a name="ispressed"></a>  CMFCButton::IsPressed  
 指示按钮是否被推送和突出显示。  
  
```  
BOOL IsPressed() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果按下按钮; 则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
  
##  <a name="ispushed"></a>  CMFCButton::IsPushed  
 指示是否按下按钮。  
  
```  
BOOL IsPushed() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果按钮; 则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
  
##  <a name="isradiobutton"></a>  CMFCButton::IsRadioButton  
 指示 button 是否是单选按钮。  
  
```  
BOOL IsRadioButton() const;  
```  
  
### <a name="return-value"></a>返回值  
 按钮样式 BS_RADIOBUTTON 或 BS_AUTORADIOBUTTON; 如果为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
  
##  <a name="iswindowsthemingenabled"></a>  CMFCButton::IsWindowsThemingEnabled  
 指示按钮边框的样式是否对应于当前 Windows 主题。  
  
```  
static BOOL IsWindowsThemingEnabled();
```  
  
### <a name="return-value"></a>返回值  
 如果按钮边框的样式对应于当前的 Windows 主题; 则为 TRUE否则为 FALSE。  



## <a name="a-namembdontusewinxptheme-cmfcbuttonmbdontusewinxptheme"></a><a name="m_bDontUseWinXPTheme"/> CMFCButton::m_bDontUseWinXPTheme
指定是否在绘制按钮时使用 Windows XP 主题。

```  
BOOL m_bDontUseWinXPTheme;  
```

##  <a name="m_bdrawfocus"></a>  CMFCButton::m_bDrawFocus  
 指示是否绘制一个聚焦框按钮周围。  
  
```  
BOOL m_bDrawFocus;  
```  
  
### <a name="remarks"></a>备注  
 设置`m_bDrawFocus`为 TRUE 的成员才能指定该框架将周围绘制聚焦框按钮的文本和图像，如果该按钮将接收焦点。  
  
 `CMFCButton`构造函数初始化此成员为 TRUE。  

##  <a name="m_bGrayDisabled"></a>  CMFCButton::m_bGrayDisabled
为 TRUE 时，启用已禁用的按钮绘制为灰显。


```  
BOOL m_bGrayDisabled;  
```

##  <a name="m_bhighlightchecked"></a>  CMFCButton::m_bHighlightChecked  
 指示是否在光标悬停时突出显示 BS_CHECKBOX 样式的按钮。  
  
```  
BOOL m_bHighlightChecked;  
```  
  
### <a name="remarks"></a>备注  
 设置`m_bHighlightChecked`为 TRUE，框架将时突出显示 BS_CHECKBOX 样式的按钮的鼠标悬停在其上指定的成员。  

##  <a name="m_bResponseOnButtonDown"></a> CMFCButton::m_bResponseOnButtonDown
指示是否对按钮按下事件做出响应。

```  
BOOL m_bResponseOnButtonDown;  
```  

##  <a name="m_brightimage"></a>  CMFCButton::m_bRightImage  
 指示是否在按钮的右侧显示的图像。  
  
```  
BOOL m_bRightImage;  
```  


##  <a name="m_bTopImage"></a>  CMFCButton::m_bTopImage](#m_bTopImage)
指示图像是否为该按钮上。

```  
BOOL m_bTopImage;  
```

### <a name="remarks"></a>备注  
 设置`m_bRightImage`为 TRUE 来指定该框架将右侧的按钮的文本标签中显示按钮的图像的成员。  
  
##  <a name="m_btransparent"></a>  CMFCButton::m_bTransparent  
 指示按钮是否是透明的。  
  
```  
BOOL m_bTransparent;  
```  
  
### <a name="remarks"></a>备注  
 设置`m_bTransparent`为 TRUE 来指定，该框架将使按钮透明的成员。 `CMFCButton`构造函数初始化此成员为 FALSE。  
  
##  <a name="m_nalignstyle"></a>  CMFCButton::m_nAlignStyle  
 指定按钮文本的对齐方式。  
  
```  
AlignStyle m_nAlignStyle;  
```  
  
### <a name="remarks"></a>备注  
 使用下列任一`CMFCButton::AlignStyle`枚举值，以指定按钮文本的对齐方式：  
  
|“值”|描述|  
|-----------|-----------------|  
|ALIGN_CENTER|（默认值）对齐到按钮的中心的按钮文本。|  
|ALIGN_LEFT|对齐到左侧和右侧的按钮的按钮文本。|  
|ALIGN_RIGHT|对齐到右侧的按钮的按钮文本。|  
  
 `CMFCButton`构造函数初始化到 ALIGN_CENTER 此成员。  

##  <a name="m_bWasDblClk"></a>  CMFCButton::m_bWasDblClk](#m_bWasDblClk) | 
指示最后一个单击事件是一次双击。 |

```  
BOOL m_bWasDblClk;  
```  

##  <a name="m_nflatstyle"></a>  CMFCButton::m_nFlatStyle  
 指定的按钮，如无边距、 平面的以平面或 3D 样式。  
  
```  
FlatStyle  m_nFlatStyle;  
```  
  
### <a name="remarks"></a>备注  
 下表列出了`CMFCButton::m_nFlatStyle`指定按钮的外观的枚举值。  
  
|“值”|描述|  
|-----------|-----------------|  
|BUTTONSTYLE_3D|（默认值）该按钮显示为具有高的三维边。 单击该按钮，该按钮显示到有深度的缩进按下。|  
|BUTTONSTYLE_FLAT|当鼠标置于按钮上，但不暂停时，按钮将显示为二维，且不具有凸起的边。 当鼠标悬停在按钮上时，按钮将显示具有较低的三维边。 单击该按钮，该按钮显示为浅表缩进按下。|  
|BUTTONSTYLE_SEMIFLAT|该按钮显示为具有较低的三维边。 单击该按钮，该按钮显示到有深度的缩进按下。|  
|BUTTONSTYLE_NOBORDERS|该按钮不会不引发边，并始终显示二维。 该按钮不会显示单击时到缩进按下。|  
  
 `CMFCButton`构造函数初始化到 BUTTONSTYLE_3D 此成员。  
  
### <a name="example"></a>示例  
 下面的示例演示如何设置的值`m_nFlatStyle`中的成员变量`CMFCButton`类。 此示例摘自[新的控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]  
  
##  <a name="ondraw"></a>  CMFCButton::OnDraw  
 由框架调用以绘制一个按钮。  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    UINT uiState);
```  
  
### <a name="parameters"></a>参数  
 [in]*pDC*  
 一个指向设备上下文的指针。  
  
 [in]*rect*  
 对限定按钮的矩形的引用。  
  
 [in]*uiState*  
 当前的按钮状态。 有关详细信息，请参阅`itemState`的成员[DRAWITEMSTRUCT 结构](../../mfc/reference/drawitemstruct-structure.md)主题。  
  
### <a name="remarks"></a>备注  
 重写此方法以使用你自己的代码来绘制一个按钮。  
  
##  <a name="ondrawborder"></a>  CMFCButton::OnDrawBorder  
 由框架调用以绘制边框的按钮。  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect& rectClient,  
    UINT uiState);
```  
  
### <a name="parameters"></a>参数  
 [in]*pDC*  
 一个指向设备上下文的指针。  
  
 [in]*rectClient*  
 对限定按钮的矩形的引用。  
  
 [in]*uiState*  
 当前的按钮状态。 有关详细信息，请参阅`itemState`的成员[DRAWITEMSTRUCT 结构](../../mfc/reference/drawitemstruct-structure.md)主题。  
  
### <a name="remarks"></a>备注  
 重写此方法以使用你自己的代码来绘制边框。  
  
##  <a name="ondrawfocusrect"></a>  CMFCButton::OnDrawFocusRect  
 由框架调用以绘制聚焦框的按钮。  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>参数  
 [in]*pDC*  
 一个指向设备上下文的指针。  
  
 [in]*rectClient*  
 对限定按钮的矩形的引用。  
  
### <a name="remarks"></a>备注  
 重写此方法以使用你自己的代码来绘制聚焦框。  
  
##  <a name="ondrawtext"></a>  CMFCButton::OnDrawText  
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
 [in]*pDC*  
 一个指向设备上下文的指针。  
  
 [in]*rect*  
 对限定按钮的矩形的引用。  
  
 [in]*strText*  
 要绘制的文本。  
  
 [in]*uiDTFlags*  
 指定如何设置文本格式的标志。 有关详细信息，请参阅*nFormat*的参数[CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)方法。  
  
 [in]*uiState*  
 （保留）。  
  
### <a name="remarks"></a>备注  
 重写此方法以使用你自己的代码来绘制按钮文本。  
  
##  <a name="onfillbackground"></a>  CMFCButton::OnFillBackground  
 由框架调用以绘制控件背景的按钮文本。  
  
```  
virtual void OnFillBackground(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>参数  
 [in]*pDC*  
 一个指向设备上下文的指针。  
  
 [in]*rectClient*  
 对限定按钮的矩形的引用。  
  
### <a name="remarks"></a>备注  
 重写此方法以使用你自己的代码用于绘制背景的按钮。  
  
##  <a name="selectfont"></a>  CMFCButton::SelectFont  
 检索与指定的设备上下文关联的字体。  
  
```  
virtual CFont* SelectFont(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in]*pDC*  
 一个指向设备上下文的指针。  
  
### <a name="return-value"></a>返回值  
 重写此方法以使用你自己的代码来检索字体的字体。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setautorepeatmode"></a>  CMFCButton::SetAutorepeatMode  
 将一个按钮设置为自动重复模式。  
  
```  
void SetAutorepeatMode(int nTimeDelay=500);
```  
  
### <a name="parameters"></a>参数  
 [in]*nTimeDelay*  
 一个非负数字，指定发送到父窗口的消息之间的间隔。 以毫秒为单位的时间间隔，其默认值为 500 毫秒。 指定零以禁用自动重复消息模式。  
  
### <a name="remarks"></a>备注  
 此方法会导致该按钮以不断向父窗口发送 WM_COMMAND 消息，直到释放按钮，或*nTimeDelay*参数设置为零。  
  
##  <a name="setcheckedimage"></a>  CMFCButton::SetCheckedImage  
 设置选中的按钮的图像。  
  
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
 [in]*hIcon*  
 包含位图和掩码为新映像的图标的句柄。  
  
 [in]*bAutoDestroy*  
 为 TRUE，则指定位图资源被销毁自动保存功能。否则为 FALSE。 默认值为 TRUE。  
  
 [in]*hIconHot*  
 包含此图像可查看所选状态的图标的句柄。  
  
 [in]*hBitmap*  
 包含未选定状态的图像的位图的句柄。  
  
 [in]*hBitmapHot*  
 包含所选状态的图像的位图的句柄。  
  
 [in]*bMap3dColors*  
 指定按钮背景; 透明的颜色也就是说，该按钮的人脸。 若要使用的颜色值 RGB （192，192，192）;如果为 FALSE，使用定义的颜色值`AFX_GLOBAL_DATA::clrBtnFace`。  
  
 [in]*uiBmpResId*  
 非选择图像的资源 ID。  
  
 [in]*uiBmpHotResId*  
 所选图像的资源 ID。  
  
 [in]*hIconDisabled*  
 禁用图像的图标的句柄。  
  
 [in]*hBitmapDisabled*  
 包含已禁用的图像的位图的句柄。  
  
 [in]*uiBmpDsblResID*  
 已禁用的位图的资源 ID。  
  
 [in]*bAlphaBlend*  
 为 true，则使用 alpha 通道; 的使用仅 32 位映像如果为 FALSE，不使用仅 alpha 通道的图像。 默认值为 FALSE。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setfacecolor"></a>  CMFCButton::SetFaceColor  
 设置按钮文本的背景色。  
  
```  
void SetFaceColor(
    COLORREF crFace,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in]*crFace*  
 RGB 颜色值。  
  
 [in]*bRedraw*  
 为 TRUE，则立即; 重绘屏幕否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 此方法用于定义新的填充颜色按钮背景 （人脸）。 请注意，在后台不填充何时[CMFCButton::m_bTransparent](#m_btransparent)成员变量为 TRUE。  
  
##  <a name="setimage"></a>  CMFCButton::SetImage  
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
 [in]*hIcon*  
 包含位图和掩码为新映像的图标的句柄。  
  
 [in]*bAutoDestroy*  
 为 TRUE，则指定位图资源被销毁自动保存功能。否则为 FALSE。 默认值为 TRUE。  
  
 [in]*hIconHot*  
 包含此图像可查看所选状态的图标的句柄。  
  
 [in]*hBitmap*  
 包含未选定状态的图像的位图的句柄。  
  
 [in]*hBitmapHot*  
 包含所选状态的图像的位图的句柄。  
  
 [in]*uiBmpResId*  
 非选择图像的资源 ID。  
  
 [in]*uiBmpHotResId*  
 所选图像的资源 ID。  
  
 [in]*bMap3dColors*  
 指定按钮背景; 透明的颜色也就是说，该按钮的人脸。 若要使用的颜色值 RGB （192，192，192）;如果为 FALSE，使用定义的颜色值`AFX_GLOBAL_DATA::clrBtnFace`。  
  
 [in]*hIconDisabled*  
 禁用图像的图标的句柄。  
  
 [in]*hBitmapDisabled*  
 包含已禁用的图像的位图的句柄。  
  
 [in]*uiBmpDsblResID*  
 已禁用的位图的资源 ID。  
  
 [in]*bAlphaBlend*  
 为 true，则使用 alpha 通道; 的使用仅 32 位映像如果为 FALSE，不使用仅 alpha 通道的图像。 默认值为 FALSE。  
  
### <a name="remarks"></a>备注  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用各种版本的`SetImage`中的方法`CMFCButton`类。 此示例摘自[新的控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]  
  
##  <a name="setmousecursor"></a>  CMFCButton::SetMouseCursor  
 设置光标图像。  
  
```  
void SetMouseCursor(HCURSOR hcursor);
```  
  
### <a name="parameters"></a>参数  
 [in]*hcursor*  
 光标的句柄。  
  
### <a name="remarks"></a>备注  
 使用此方法将光标图像，如手形光标与按钮相关联。 从应用程序资源加载光标。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`SetMouseCursor`中的方法`CMFCButton`类。 中的代码示例摘自[新的控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]  
  
##  <a name="setmousecursorhand"></a>  CMFCButton::SetMouseCursorHand  
 将光标设置到手的形状的图像。  
  
```  
void SetMouseCursorHand();
```  
  
### <a name="remarks"></a>备注  
 使用此方法将手形光标图像与按钮相关联。 从应用程序资源加载光标。  
  
##  <a name="setstdimage"></a>  CMFCButton::SetStdImage  
 使用`CMenuImages`对象来设置按钮的图像。  
  
```  
void SetStdImage(
    CMenuImages::IMAGES_IDS id,  
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,  
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```  
  
### <a name="parameters"></a>参数  
 [in]*id*  
 一个按钮的图像标识符中定义的`CMenuImage::IMAGES_IDS`枚举。 Image 值指定如箭头、 pin 和单选按钮的图像。  
  
 [in]*状态*  
 在中定义的按钮图像状态标识符之一`CMenuImages::IMAGE_STATE`枚举。 映像状态指定按钮的颜色，例如黑色、 灰色、 浅灰色，白色和暗灰色。 默认值为 `CMenuImages::ImageBlack`。  
  
 [in]*idDisabled*  
 一个按钮的图像标识符中定义的`CMenuImage::IMAGES_IDS`枚举。 图指示了该按钮被禁用。 默认值是第一个按钮图像 ( `CMenuImages::IdArrowDown`)。  
  
### <a name="remarks"></a>备注  
  
##  <a name="settextcolor"></a>  CMFCButton::SetTextColor  
 设置未选择的按钮的按钮文本的颜色。  
  
```  
void SetTextColor(COLORREF clrText);
```  
  
### <a name="parameters"></a>参数  
 [in]*clrText*  
 RGB 颜色值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="settexthotcolor"></a>  CMFCButton::SetTextHotColor  
 设置处于选中状态的按钮的按钮文本的颜色。  
  
```  
void SetTextHotColor(COLORREF clrTextHot);
```  
  
### <a name="parameters"></a>参数  
 [in]*clrTextHot*  
 RGB 颜色值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="settooltip"></a>  CMFCButton::SetTooltip  
 将工具提示与按钮相关联。  
  
```  
void SetTooltip(LPCTSTR lpszToolTipText);
```  
  
### <a name="parameters"></a>参数  
 [in]*lpszToolTipText*  
 为工具提示的文本指针。 指定 NULL 可禁用工具提示。  
  
### <a name="remarks"></a>备注  
  
##  <a name="sizetocontent"></a>  CMFCButton::SizeToContent  
 调整大小以包含其按钮文本和图像的按钮。  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in]*bCalcOnly*  
 若要计算，但不是更改按钮; 的新大小，则返回 TRUE如果为 FALSE，则若要更改按钮的大小。 默认值为 FALSE。  
  
### <a name="return-value"></a>返回值  
 一个`CSize`对象，其中包含新按钮的大小。  
  
### <a name="remarks"></a>备注  
 默认情况下，此方法计算新的大小，其中包括的水平边距为 10 个像素和 5 个像素的垂直边距。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCLinkCtrl 类](../../mfc/reference/cmfclinkctrl-class.md)   
 [CMFCColorButton 类](../../mfc/reference/cmfccolorbutton-class.md)   
 [CMFCMenuButton 类](../../mfc/reference/cmfcmenubutton-class.md)
