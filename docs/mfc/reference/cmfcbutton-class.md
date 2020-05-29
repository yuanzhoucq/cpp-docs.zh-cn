---
title: CMFCButton 类
ms.date: 08/28/2018
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
ms.openlocfilehash: e949feaaac3570e1518cfb488cc1c42a471a1c46
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754870"
---
# <a name="cmfcbutton-class"></a>CMFCButton 类

该`CMFCButton`类向[CButton](../../mfc/reference/cbutton-class.md)类添加功能，例如对齐按钮文本、组合按钮文本和图像、选择光标以及指定工具提示。

## <a name="syntax"></a>语法

```
class CMFCButton : public CButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CMFCButton::CMFCButton`|默认构造函数。|
|`CMFCButton::~CMFCButton`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC按钮：：清理](#cleanup)|重置内部变量并释放分配的资源，如图像、位图和图标。|
|`CMFCButton::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CMFCButton::DrawItem`|当所有者绘制按钮的可视方面已更改时，由框架调用。 （覆盖[CButton：:D原始项目](../../mfc/reference/cbutton-class.md#drawitem)））|
|[CMFC按钮：：启用全文本工具提示](#enablefulltexttooltip)|指定是在大型工具提示窗口中显示工具提示的全文，还是在小型工具提示窗口中显示文本的截断版本。|
|[CMFC按钮：：启用菜单字体](#enablemenufont)|指定按钮文本字体是否与应用程序菜单字体相同。|
|[CMFC按钮：：启用WindowsTheming](#enablewindowstheming)|指定按钮边框的样式是否与当前 Windows 主题相对应。|
|`CMFCButton::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFC按钮：：获取工具提示](#gettooltipctrl)|返回对基础工具提示控件的引用。|
|[CMFC按钮：：自动检查](#isautocheck)|指示复选框或单选按钮是自动按钮。|
|[CMFC按钮：：自动重复命令模式](#isautorepeatcommandmode)|指示按钮是否已设置为自动重复模式。|
|[CMFC按钮：：是支票盒](#ischeckbox)|指示按钮是否为复选框按钮。|
|[CMFC按钮：：已选中](#ischecked)|指示是否选中当前按钮。|
|[CMFC按钮：：已突出显示](#ishighlighted)|指示按钮是否突出显示。|
|[CMFC按钮：：按压](#ispressed)|指示是否按下并突出显示按钮。|
|[CMFC按钮：按压](#ispushed)|指示是否按下按钮。|
|[CMFC按钮：：是无线按钮](#isradiobutton)|指示按钮是否为单选按钮。|
|[CMFC按钮：Windows启用](#iswindowsthemingenabled)|指示按钮边框的样式是否与当前 Windows 主题相对应。|
|`CMFCButton::OnDrawParentBackground`|在指定区域中绘制按钮父级的背景。 （覆盖[AFX_GLOBAL_DATA：:D原始父背景](../../mfc/reference/afx-global-data-structure.md)|
|`CMFCButton::PreTranslateMessage`|在窗口消息发送到[翻译消息](/windows/win32/api/winuser/nf-winuser-translatemessage)和[调度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)窗口功能之前进行翻译。 （重写 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。）|
|[CMFC按钮：：设置自动重复模式](#setautorepeatmode)|将按钮设置为自动重复模式。|
|[CMFC按钮：：设置已检查图像](#setcheckedimage)|设置选中按钮的图像。|
|[CMFC按钮：：设置脸彩](#setfacecolor)|设置按钮文本的背景颜色。|
|[CMFC按钮：：设置图像](#setimage)|设置按钮的图像。|
|[CMFC按钮：：设置鼠标光标](#setmousecursor)|设置光标图像。|
|[CMFC按钮：：设置鼠标光标手](#setmousecursorhand)|将光标设置到手的图像。|
|[CMFC按钮：：设置StdImage](#setstdimage)|使用对象`CMenuImages`设置按钮图像。|
|[CMFC按钮：：设置文本颜色](#settextcolor)|设置未选择的按钮的按钮文本的颜色。|
|[CMFC按钮：：设置文本热色](#settexthotcolor)|设置所选按钮的按钮文本的颜色。|
|[CMFC按钮：：设置工具提示](#settooltip)|将工具提示与按钮关联。|
|[CMFC按钮：：大小到内容](#sizetocontent)|调整按钮的大小以包含其按钮文本和图像。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CMFC按钮：在画上](#ondraw)|由框架调用以绘制一个按钮。|
|[CMFC按钮：：在绘制边框](#ondrawborder)|由框架调用以绘制按钮的边框。|
|[CMFC按钮：：在Draw焦点上](#ondrawfocusrect)|框架调用以绘制按钮的焦点矩形。|
|[CMFC按钮：：画中文本](#ondrawtext)|由框架调用以绘制按钮文本。|
|[CMFC按钮：：打开填充背景](#onfillbackground)|由框架调用以绘制按钮文本的背景。|
|[CMFC按钮：：选择字体](#selectfont)|检索与指定设备上下文关联的字体。|

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[CMFC按钮：：m_nAlignStyle](#m_nalignstyle)|指定按钮文本的对齐方式。|
|[CMFC按钮：m_bDontUseWinXPTheme](#m_bDontUseWinXPTheme)|指定是否使用 Windows XP 主题。|
|[CMFC按钮：m_bDrawFocus](#m_bdrawfocus)|指示是否围绕按钮绘制焦点矩形。|
|[CMFC按钮：：m_nFlatStyle](#m_nflatstyle)|指定按钮的样式，如无边框、平面、半平面或 3D。|
|[CMFC按钮：：m_bGrayDisabled](#m_bGrayDisabled)|当 TRUE 时，使禁用的按钮绘制为灰显。|
|[CMFC按钮：m_bHighlightChecked](#m_bhighlightchecked)|指示光标悬停在按钮上时是否突出显示BS_CHECKBOX式按钮。|
|[CMFC按钮：m_bResponseOnButtonDown](#m_bResponseOnButtonDown)|指示是否响应按钮向下事件。|
|[CMFC按钮：m_bRightImage](#m_brightimage)|指示是否在按钮右侧显示图像。|
|[CMFC按钮：m_bTopImage](#m_bTopImage)| 指示图像是否位于按钮顶部。|
|[CMFC按钮：：m_bTransparent](#m_btransparent)|指示按钮是否透明。|
|[CMFC按钮：m_bWasDblClk](#m_bWasDblClk)| 指示最后一次单击事件是否为双击。|

## <a name="remarks"></a>备注

其他类型的按钮派生自`CMFCButton`类，例如支持超链接的[CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md)类和支持颜色选取器对话框的`CMFCColorButton`类。

`CMFCButton`对象的样式可以是*3D、**平面*、*半平面*或*无边框*。 按钮文本可以在按钮的左侧、顶部或中心对齐。 在运行时，您可以控制按钮是显示文本、图像还是文本和图像。 还可以指定在光标悬停在按钮上时显示特定的光标图像。

直接在代码中创建按钮控件，或使用**MFC 类向导**工具和对话框模板创建按钮控件。 如果直接创建按钮控件，请向应用程序添加`CMFCButton`变量，然后调用`Create``CMFCButton`对象的构造函数和方法。 如果使用**MFC 类向导**，请向应用程序`CButton`添加变量，然后将变量的类型从`CButton`更改为 。 `CMFCButton`

要处理对话框应用程序中的通知消息，请为每个通知添加消息映射条目和事件处理程序。 `CMFCButton`对象发送的通知与`CButton`对象发送的通知相同。

## <a name="example"></a>示例

下面的示例演示如何使用`CMFCButton`类中的各种方法配置按钮的属性。 该示例是["新控件"示例](../../overview/visual-cpp-samples.md)的一部分。

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

**标题：** afx按钮.h

## <a name="cmfcbuttoncleanup"></a><a name="cleanup"></a>CMFC按钮：：清理

重置内部变量并释放分配的资源，如图像、位图和图标。

```
virtual void CleanUp();
```

## <a name="cmfcbuttonenablefulltexttooltip"></a><a name="enablefulltexttooltip"></a>CMFC按钮：：启用全文本工具提示

指定是在大型工具提示窗口中显示工具提示的全文，还是在小型工具提示窗口中显示文本的截断版本。

```cpp
void EnableFullTextTooltip(BOOL bOn=TRUE);
```

### <a name="parameters"></a>参数

*邦*<br/>
[在]TRUE 以显示所有文本;FALSE 以显示截断的文本。

### <a name="remarks"></a>备注

## <a name="cmfcbuttonenablemenufont"></a><a name="enablemenufont"></a>CMFC按钮：：启用菜单字体

指定按钮文本字体是否与应用程序菜单字体相同。

```cpp
void EnableMenuFont(
    BOOL bOn=TRUE,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>参数

*邦*<br/>
[在]TRUE 使用应用程序菜单字体作为按钮文本字体;FALSE 以使用系统字体。 默认值为 TRUE。

*bredraw*<br/>
[在]TRUE 可立即重绘屏幕;否则，FALSE。 默认值为 TRUE。

### <a name="remarks"></a>备注

如果不使用此方法指定按钮文本字体，则可以使用[CWnd：：SetFont](../../mfc/reference/cwnd-class.md#setfont)方法指定字体。 如果根本不指定字体，则框架将设置默认字体。

## <a name="cmfcbuttonenablewindowstheming"></a><a name="enablewindowstheming"></a>CMFC按钮：：启用WindowsTheming

指定按钮边框的样式是否与当前 Windows 主题相对应。

```
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]TRUE 使用当前 Windows 主题绘制按钮边框;FALSE 不使用 Windows 主题。 默认值为 TRUE。

### <a name="remarks"></a>备注

此方法会影响应用程序中派生自`CMFCButton`类的所有按钮。

## <a name="cmfcbuttongettooltipctrl"></a><a name="gettooltipctrl"></a>CMFC按钮：：获取工具提示

返回对基础工具提示控件的引用。

```
CToolTipCtrl& GetToolTipCtrl();
```

### <a name="return-value"></a>返回值

对基础工具提示控件的引用。

### <a name="remarks"></a>备注

## <a name="cmfcbuttonisautocheck"></a><a name="isautocheck"></a>CMFC按钮：：自动检查

指示复选框或单选按钮是自动按钮。

```
BOOL IsAutoCheck() const;
```

### <a name="return-value"></a>返回值

如果按钮具有样式BS_AUTOCHECKBOX或BS_AUTORADIOBUTTON，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcbuttonisautorepeatcommandmode"></a><a name="isautorepeatcommandmode"></a>CMFC按钮：：自动重复命令模式

指示按钮是否已设置为自动重复模式。

```
BOOL IsAutorepeatCommandMode() const;
```

### <a name="return-value"></a>返回值

如果按钮设置为自动重复模式，则为 TRUE;如果按钮设置为自动重复模式，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

使用[CMFCButton：：设置自动重复模式](#setautorepeatmode)方法将按钮设置为自动重复模式。

## <a name="cmfcbuttonischeckbox"></a><a name="ischeckbox"></a>CMFC按钮：：是支票盒

指示按钮是否为复选框按钮。

```
BOOL IsCheckBox() const;
```

### <a name="return-value"></a>返回值

如果按钮具有BS_CHECKBOX或BS_AUTOCHECKBOX样式，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcbuttonischecked"></a><a name="ischecked"></a>CMFC按钮：：已选中

指示是否选中当前按钮。

```
BOOL IsChecked() const;
```

### <a name="return-value"></a>返回值

如果选中当前按钮，则为 TRUE;如果选中当前按钮，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

框架使用不同的方法来指示检查不同类型的按钮。 例如，当单选按钮包含点时，将选中它;当复选框包含**X**时，将选中它。

## <a name="cmfcbuttonishighlighted"></a><a name="ishighlighted"></a>CMFC按钮：：已突出显示

指示按钮是否突出显示。

```
BOOL IsHighlighted() const;
```

### <a name="return-value"></a>返回值

如果按钮突出显示，则为 TRUE;如果按钮突出显示，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

当鼠标悬停在按钮上时，按钮将突出显示。

## <a name="cmfcbuttonispressed"></a><a name="ispressed"></a>CMFC按钮：：按压

指示是否按下并突出显示按钮。

```
BOOL IsPressed() const;
```

### <a name="return-value"></a>返回值

如果按下按钮，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcbuttonispushed"></a><a name="ispushed"></a>CMFC按钮：按压

指示是否按下按钮。

```
BOOL IsPushed() const;
```

### <a name="return-value"></a>返回值

如果按下按钮，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcbuttonisradiobutton"></a><a name="isradiobutton"></a>CMFC按钮：：是无线按钮

指示按钮是否为单选按钮。

```
BOOL IsRadioButton() const;
```

### <a name="return-value"></a>返回值

如果按钮样式为BS_RADIOBUTTON或BS_AUTORADIOBUTTON，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcbuttoniswindowsthemingenabled"></a><a name="iswindowsthemingenabled"></a>CMFC按钮：Windows启用

指示按钮边框的样式是否与当前 Windows 主题相对应。

```
static BOOL IsWindowsThemingEnabled();
```

### <a name="return-value"></a>返回值

如果按钮边框的样式对应于当前 Windows 主题，则为 TRUE;否则，FALSE。

## <a name="cmfcbuttonm_bdontusewinxptheme"></a><a name="m_bDontUseWinXPTheme"/>CMFC按钮：m_bDontUseWinXPTheme

指定在绘制按钮时是否使用 Windows XP 主题。

```
BOOL m_bDontUseWinXPTheme;
```

## <a name="cmfcbuttonm_bdrawfocus"></a><a name="m_bdrawfocus"></a>CMFC按钮：m_bDrawFocus

指示是否围绕按钮绘制焦点矩形。

```
BOOL m_bDrawFocus;
```

### <a name="remarks"></a>备注

将`m_bDrawFocus`成员设置为 TRUE 以指定如果按钮接收焦点，框架将在按钮的文本和图像周围绘制焦点矩形。

构造`CMFCButton`函数将此成员初始化为 TRUE。

## <a name="cmfcbuttonm_bgraydisabled"></a><a name="m_bGrayDisabled"></a>CMFC按钮：：m_bGrayDisabled

当 TRUE 时，使禁用的按钮绘制为灰显。

```
BOOL m_bGrayDisabled;
```

## <a name="cmfcbuttonm_bhighlightchecked"></a><a name="m_bhighlightchecked"></a>CMFC按钮：m_bHighlightChecked

指示光标悬停在按钮上时是否突出显示BS_CHECKBOX式按钮。

```
BOOL m_bHighlightChecked;
```

### <a name="remarks"></a>备注

将`m_bHighlightChecked`成员设置为 TRUE 以指定当鼠标悬停在按钮上时，框架将突出显示BS_CHECKBOX式按钮。

## <a name="cmfcbuttonm_bresponseonbuttondown"></a><a name="m_bResponseOnButtonDown"></a>CMFC按钮：m_bResponseOnButtonDown

指示是否响应按钮向下事件。

```
BOOL m_bResponseOnButtonDown;
```

## <a name="cmfcbuttonm_brightimage"></a><a name="m_brightimage"></a>CMFC按钮：m_bRightImage

指示是否在按钮右侧显示图像。

```
BOOL m_bRightImage;
```

## <a name="cmfcbuttonm_btopimagem_btopimage"></a><a name="m_bTopImage"></a>CMFC按钮：：m_bTopImage*（#m_bTopImage）

指示图像是否位于按钮顶部。

```
BOOL m_bTopImage;
```

### <a name="remarks"></a>备注

将`m_bRightImage`成员设置为 TRUE 以指定框架将在按钮的文本标签右侧显示按钮的图像。

## <a name="cmfcbuttonm_btransparent"></a><a name="m_btransparent"></a>CMFC按钮：：m_bTransparent

指示按钮是否透明。

```
BOOL m_bTransparent;
```

### <a name="remarks"></a>备注

将`m_bTransparent`成员设置为 TRUE 以指定框架将使按钮透明。 构造`CMFCButton`函数将此成员初始化到 FALSE。

## <a name="cmfcbuttonm_nalignstyle"></a><a name="m_nalignstyle"></a>CMFC按钮：：m_nAlignStyle

指定按钮文本的对齐方式。

```
AlignStyle m_nAlignStyle;
```

### <a name="remarks"></a>备注

使用以下`CMFCButton::AlignStyle`枚举值之一指定按钮文本的对齐方式：

|“值”|说明|
|-----------|-----------------|
|ALIGN_CENTER|（默认）将按钮文本对齐到按钮的中心。|
|ALIGN_LEFT|将按钮文本对齐到按钮的左侧。|
|ALIGN_RIGHT|将按钮文本对齐到按钮的右侧。|

构造`CMFCButton`函数将此成员初始化到ALIGN_CENTER。

## <a name="cmfcbuttonm_bwasdblclkm_bwasdblclk"></a><a name="m_bWasDblClk"></a>CMFC按钮：：m_bWasDblClk*（#m_bWasDblClk）*

指示上次单击事件是否为双击。

```
BOOL m_bWasDblClk;
```

## <a name="cmfcbuttonm_nflatstyle"></a><a name="m_nflatstyle"></a>CMFC按钮：：m_nFlatStyle

指定按钮的样式，如无边框、平面、半平面或 3D。

```
FlatStyle  m_nFlatStyle;
```

### <a name="remarks"></a>备注

下表列出了`CMFCButton::m_nFlatStyle`指定按钮外观的枚举值。

|“值”|说明|
|-----------|-----------------|
|BUTTONSTYLE_3D|（默认）按钮似乎有高的三维边。 单击该按钮时，该按钮似乎被压入深缩进。|
|BUTTONSTYLE_FLAT|当鼠标未在按钮上暂停时，该按钮显示为二维，并且没有凸起的边。 当鼠标悬停在按钮上时，按钮似乎有低的三维边。 单击该按钮时，该按钮似乎被压入浅缩进。|
|BUTTONSTYLE_SEMIFLAT|按钮似乎有低的三维边。 单击该按钮时，该按钮似乎被压入深缩进。|
|BUTTONSTYLE_NOBORDERS|按钮没有凸起的边，并且始终显示为二维。 单击按钮时，按钮似乎不会按入缩进。|

构造`CMFCButton`函数将此成员初始化到BUTTONSTYLE_3D。

### <a name="example"></a>示例

下面的示例演示如何在`m_nFlatStyle``CMFCButton`类中设置成员变量的值。 此示例是["新控件"示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]

## <a name="cmfcbuttonondraw"></a><a name="ondraw"></a>CMFC按钮：在画上

由框架调用以绘制一个按钮。

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*矩形*<br/>
[在]对绑定按钮的矩形的引用。

*uiState*<br/>
[在]当前按钮状态。 有关详细信息，请参阅`itemState`[DRAWITEMSTRUCT 结构](/windows/win32/api/winuser/ns-winuser-drawitemstruct)主题的成员。

### <a name="remarks"></a>备注

重写此方法以使用您自己的代码绘制按钮。

## <a name="cmfcbuttonondrawborder"></a><a name="ondrawborder"></a>CMFC按钮：：在绘制边框

由框架调用以绘制按钮的边框。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*rectClient*<br/>
[在]对绑定按钮的矩形的引用。

*uiState*<br/>
[在]当前按钮状态。 有关详细信息，请参阅`itemState`[DRAWITEMSTRUCT 结构](/windows/win32/api/winuser/ns-winuser-drawitemstruct)主题的成员。

### <a name="remarks"></a>备注

重写此方法以使用您自己的代码绘制边框。

## <a name="cmfcbuttonondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFC按钮：：在Draw焦点上

框架调用以绘制按钮的焦点矩形。

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*rectClient*<br/>
[在]对绑定按钮的矩形的引用。

### <a name="remarks"></a>备注

重写此方法以使用自己的代码绘制焦点矩形。

## <a name="cmfcbuttonondrawtext"></a><a name="ondrawtext"></a>CMFC按钮：：画中文本

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

*pDC*<br/>
[在]指向设备上下文的指针。

*矩形*<br/>
[在]对绑定按钮的矩形的引用。

*斯特文本*<br/>
[在]要绘制的文本。

*uiDTFlags*<br/>
[在]指定如何设置文本格式的标志。 有关详细信息，请参阅[CDC：:DrawText](../../mfc/reference/cdc-class.md#drawtext)方法的*nFormat*参数。

*uiState*<br/>
[in] 保留。

### <a name="remarks"></a>备注

重写此方法以使用您自己的代码绘制按钮文本。

## <a name="cmfcbuttononfillbackground"></a><a name="onfillbackground"></a>CMFC按钮：：打开填充背景

由框架调用以绘制按钮文本的背景。

```
virtual void OnFillBackground(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

*rectClient*<br/>
[在]对绑定按钮的矩形的引用。

### <a name="remarks"></a>备注

重写此方法以使用您自己的代码绘制按钮的背景。

## <a name="cmfcbuttonselectfont"></a><a name="selectfont"></a>CMFC按钮：：选择字体

检索与指定设备上下文关联的字体。

```
virtual CFont* SelectFont(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

### <a name="return-value"></a>返回值

重写此方法以使用您自己的代码来检索字体。

### <a name="remarks"></a>备注

## <a name="cmfcbuttonsetautorepeatmode"></a><a name="setautorepeatmode"></a>CMFC按钮：：设置自动重复模式

将按钮设置为自动重复模式。

```cpp
void SetAutorepeatMode(int nTimeDelay=500);
```

### <a name="parameters"></a>参数

*n时间延迟*<br/>
[在]指定发送到父窗口的消息之间的间隔的非负数。 间隔以毫秒为单位测量，其默认值为 500 毫秒。 指定零以禁用自动重复消息模式。

### <a name="remarks"></a>备注

此方法使按钮不断向父窗口发送WM_COMMAND消息，直到释放按钮或*nTimeDelay*参数设置为零。

## <a name="cmfcbuttonsetcheckedimage"></a><a name="setcheckedimage"></a>CMFC按钮：：设置已检查图像

设置选中按钮的图像。

```cpp
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

*hIcon*<br/>
[在]处理包含新图像的位图和蒙版的图标。

*bAuto销毁*<br/>
[在]TRUE 指定自动销毁位图资源;否则，FALSE。 默认值为 TRUE。

*hIconHot*<br/>
[在]处理包含所选状态的图像的图标。

*hBitmap*<br/>
[在]处理包含非选定状态图像的位图。

*hBitmapHot*<br/>
[在]处理包含所选状态的图像的位图。

*bMap3d颜色*<br/>
[在]为按钮背景指定透明颜色;就是按钮的脸。 TRUE 使用颜色值 RGB（192、192、192）;FALSE 使用 定义`AFX_GLOBAL_DATA::clrBtnFace`的颜色值。

*乌布布雷西德*<br/>
[在]未选择图像的资源 ID。

*乌布霍特雷西德*<br/>
[在]所选图像的资源 ID。

*hIcon 已禁用*<br/>
[在]处理禁用图像的图标。

*hBitmap 已禁用*<br/>
[在]处理包含禁用图像的位图。

*uiBmpDsblResID*<br/>
[在]已禁用位图的资源 ID。

*b阿尔法布林*<br/>
[在]TRUE 仅使用使用 alpha 通道的 32 位图像;FALSE，不要只使用 Alpha 通道图像。 默认值为 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcbuttonsetfacecolor"></a><a name="setfacecolor"></a>CMFC按钮：：设置脸彩

设置按钮文本的背景颜色。

```cpp
void SetFaceColor(
    COLORREF crFace,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>参数

*crFace*<br/>
[在]RGB 颜色值。

*bredraw*<br/>
[在]TRUE 立即重绘屏幕;否则，FALSE。

### <a name="remarks"></a>备注

使用此方法为按钮背景（面）定义新的填充颜色。 请注意，当[CMFCButton：：m_bTransparent](#m_btransparent)成员变量为 TRUE 时，不会填充背景。

## <a name="cmfcbuttonsetimage"></a><a name="setimage"></a>CMFC按钮：：设置图像

设置按钮的图像。

```cpp
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

*hIcon*<br/>
[在]处理包含新图像的位图和蒙版的图标。

*bAuto销毁*<br/>
[在]TRUE 指定自动销毁位图资源;否则，FALSE。 默认值为 TRUE。

*hIconHot*<br/>
[在]处理包含所选状态的图像的图标。

*hBitmap*<br/>
[在]处理包含非选定状态图像的位图。

*hBitmapHot*<br/>
[在]处理包含所选状态的图像的位图。

*乌布布雷西德*<br/>
[在]未选择图像的资源 ID。

*乌布霍特雷西德*<br/>
[在]所选图像的资源 ID。

*bMap3d颜色*<br/>
[在]为按钮背景指定透明颜色;就是按钮的脸。 TRUE 使用颜色值 RGB（192、192、192）;FALSE 使用 定义`AFX_GLOBAL_DATA::clrBtnFace`的颜色值。

*hIcon 已禁用*<br/>
[在]处理禁用图像的图标。

*hBitmap 已禁用*<br/>
[在]处理包含禁用图像的位图。

*uiBmpDsblResID*<br/>
[在]已禁用位图的资源 ID。

*b阿尔法布林*<br/>
[在]TRUE 仅使用使用 alpha 通道的 32 位图像;FALSE，不要只使用 Alpha 通道图像。 默认值为 FALSE。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

下面的示例演示如何在`SetImage``CMFCButton`类中使用 方法的各种版本。 该示例是["新控件"示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]

## <a name="cmfcbuttonsetmousecursor"></a><a name="setmousecursor"></a>CMFC按钮：：设置鼠标光标

设置光标图像。

```cpp
void SetMouseCursor(HCURSOR hcursor);
```

### <a name="parameters"></a>参数

*赫光标*<br/>
[在]光标的句柄。

### <a name="remarks"></a>备注

使用此方法将光标图像（如手光标）与按钮相关联。 光标从应用程序资源加载。

### <a name="example"></a>示例

下面的示例演示如何在`SetMouseCursor``CMFCButton`类中使用 方法。 该示例是["新建控件"示例中](../../overview/visual-cpp-samples.md)的代码的一部分。

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]

## <a name="cmfcbuttonsetmousecursorhand"></a><a name="setmousecursorhand"></a>CMFC按钮：：设置鼠标光标手

将光标设置到手的图像。

```cpp
void SetMouseCursorHand();
```

### <a name="remarks"></a>备注

使用此方法将手的光标图像与按钮相关联。 光标从应用程序资源加载。

## <a name="cmfcbuttonsetstdimage"></a><a name="setstdimage"></a>CMFC按钮：：设置StdImage

使用对象`CMenuImages`设置按钮图像。

```cpp
void SetStdImage(
    CMenuImages::IMAGES_IDS id,
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```

### <a name="parameters"></a>参数

*id*<br/>
[在]枚举中定义的按钮图像标识符之一`CMenuImage::IMAGES_IDS`。 图像值指定图像，如箭头、引脚和单选按钮。

State <br/>
[在]枚举中定义的按钮图像状态标识符之一`CMenuImages::IMAGE_STATE`。 图像状态指定按钮颜色，如黑色、灰色、浅灰色、白色和深灰色。 默认值为 `CMenuImages::ImageBlack`。

*ID 已禁用*<br/>
[在]枚举中定义的按钮图像标识符之一`CMenuImage::IMAGES_IDS`。 该图像指示按钮已禁用。 默认值是第一个按钮图像 （ `CMenuImages::IdArrowDown`。

### <a name="remarks"></a>备注

## <a name="cmfcbuttonsettextcolor"></a><a name="settextcolor"></a>CMFC按钮：：设置文本颜色

设置未选择的按钮的按钮文本的颜色。

```cpp
void SetTextColor(COLORREF clrText);
```

### <a name="parameters"></a>参数

*clrText*<br/>
[在]RGB 颜色值。

### <a name="remarks"></a>备注

## <a name="cmfcbuttonsettexthotcolor"></a><a name="settexthotcolor"></a>CMFC按钮：：设置文本热色

设置所选按钮的按钮文本的颜色。

```cpp
void SetTextHotColor(COLORREF clrTextHot);
```

### <a name="parameters"></a>参数

*clrTextHot*<br/>
[在]RGB 颜色值。

### <a name="remarks"></a>备注

## <a name="cmfcbuttonsettooltip"></a><a name="settooltip"></a>CMFC按钮：：设置工具提示

将工具提示与按钮关联。

```cpp
void SetTooltip(LPCTSTR lpszToolTipText);
```

### <a name="parameters"></a>参数

*lpszTool提示文本*<br/>
[在]指向工具提示的文本。 指定 NULL 以禁用工具提示。

### <a name="remarks"></a>备注

## <a name="cmfcbuttonsizetocontent"></a><a name="sizetocontent"></a>CMFC按钮：：大小到内容

调整按钮的大小以包含其按钮文本和图像。

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>参数

*bCalcOnly*<br/>
[在]真实计算，但不改变，按钮的新大小;FALSE 以更改按钮的大小。 默认值为 FALSE。

### <a name="return-value"></a>返回值

包含`CSize`按钮的新大小的对象。

### <a name="remarks"></a>备注

默认情况下，此方法计算一个新大小，该大小包括 10 像素的水平边距和 5 像素的垂直边距。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCLinkCtrl 类](../../mfc/reference/cmfclinkctrl-class.md)<br/>
[CMFCColorButton 类](../../mfc/reference/cmfccolorbutton-class.md)<br/>
[CMFCMenuButton 类](../../mfc/reference/cmfcmenubutton-class.md)
