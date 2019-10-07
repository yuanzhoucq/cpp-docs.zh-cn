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
ms.openlocfilehash: 7628ac353d01c2a6853e35a35bd1f702d3bb041e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505864"
---
# <a name="cmfcbutton-class"></a>CMFCButton 类

`CMFCButton`类向 [CButton](../../mfc/reference/cbutton-class.md) 类添加功能，如对齐按钮文本、组合按钮文本和图像、选择光标以及指定工具提示。

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
|[CMFCButton::CleanUp](#cleanup)|重置内部变量并释放已分配的资源，如图像、位图和图标。|
|`CMFCButton::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CMFCButton::DrawItem`|当所有者描述的按钮的视觉方面发生更改时由框架调用。 （重写[CButton：:D rawitem](../../mfc/reference/cbutton-class.md#drawitem)。）|
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|指定是在大的工具提示窗口中显示工具提示的完整文本还是在小工具提示窗口中显示文本的截断版本。|
|[CMFCButton::EnableMenuFont](#enablemenufont)|指定按钮文本字体是否与应用程序菜单字体相同。|
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|指定按钮边框的样式是否对应于当前的 Windows 主题。|
|`CMFCButton::GetThisClass`|由框架用于获取指向与此类类型相关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|返回对基础工具提示控件的引用。|
|[CMFCButton::IsAutoCheck](#isautocheck)|指示复选框或单选按钮是否为 "自动" 按钮。|
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|指示按钮是否设置为自动重复模式。|
|[CMFCButton::IsCheckBox](#ischeckbox)|指示按钮是否为复选框按钮。|
|[CMFCButton::IsChecked](#ischecked)|指示是否选中当前按钮。|
|[CMFCButton::IsHighlighted](#ishighlighted)|指示是否突出显示某个按钮。|
|[CMFCButton::IsPressed](#ispressed)|指示按钮是否已按下并突出显示。|
|[CMFCButton::IsPushed](#ispushed)|指示是否推送按钮。|
|[CMFCButton::IsRadioButton](#isradiobutton)|指示按钮是否为单选按钮。|
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|指示按钮边框的样式是否对应于当前的 Windows 主题。|
|`CMFCButton::OnDrawParentBackground`|在指定区域中绘制按钮的父级的背景。 （重写[AFX_GLOBAL_DATA：:D rawparentbackground](../../mfc/reference/afx-global-data-structure.md)|
|`CMFCButton::PreTranslateMessage`|转换窗口消息，然后将其调度到[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)和[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 函数。 （重写 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。）|
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|将按钮设置为自动重复模式。|
|[CMFCButton::SetCheckedImage](#setcheckedimage)|设置选中按钮的图像。|
|[CMFCButton::SetFaceColor](#setfacecolor)|设置按钮文本的背景色。|
|[CMFCButton::SetImage](#setimage)|设置按钮的图像。|
|[CMFCButton::SetMouseCursor](#setmousecursor)|设置游标图像。|
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|将光标设置为指针的图像。|
|[CMFCButton::SetStdImage](#setstdimage)|`CMenuImages`使用对象设置按钮图像。|
|[CMFCButton::SetTextColor](#settextcolor)|为未选中的按钮设置按钮文本的颜色。|
|[CMFCButton::SetTextHotColor](#settexthotcolor)|设置所选按钮的按钮文本颜色。|
|[CMFCButton::SetTooltip](#settooltip)|将工具提示与按钮相关联。|
|[CMFCButton::SizeToContent](#sizetocontent)|调整按钮的大小以包含其按钮文本和图像。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CMFCButton::OnDraw](#ondraw)|由框架调用以绘制一个按钮。|
|[CMFCButton::OnDrawBorder](#ondrawborder)|由框架调用，用于绘制按钮的边框。|
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|由框架调用，用于绘制按钮的聚焦框。|
|[CMFCButton::OnDrawText](#ondrawtext)|由框架调用，用于绘制按钮文本。|
|[CMFCButton::OnFillBackground](#onfillbackground)|由框架调用，用于绘制按钮文本的背景。|
|[CMFCButton::SelectFont](#selectfont)|检索与指定的设备上下文关联的字体。|

### <a name="data-members"></a>数据成员

|名称|描述|
|----------|-----------------|
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|指定按钮文本的对齐方式。|
|[CMFCButton::m_bDontUseWinXPTheme](#m_bDontUseWinXPTheme)|指定是否使用 Windows XP 主题。|
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|指示是否在按钮周围绘制聚焦框。|
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|指定按钮的样式，例如无边框、平面、半平面或三维。|
|[CMFCButton::m_bGrayDisabled](#m_bGrayDisabled)|如果为 TRUE，则允许将禁用的按钮绘制为灰显。|
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|指示当光标悬停在 BS_CHECKBOX 按钮上时是否突出显示该按钮。|
|[CMFCButton::m_bResponseOnButtonDown](#m_bResponseOnButtonDown)|指示是否响应按钮按下事件。|
|[CMFCButton::m_bRightImage](#m_brightimage)|指示是否在按钮右侧显示图像。|
|[CMFCButton::m_bTopImage](#m_bTopImage)| 指示图像是否位于按钮的顶部。|
|[CMFCButton::m_bTransparent](#m_btransparent)|指示按钮是否透明。|
|[CMFCButton::m_bWasDblClk](#m_bWasDblClk)| 指示最后一个 click 事件是否是双击事件。|

## <a name="remarks"></a>备注

其他类型的按钮是从`CMFCButton`类派生的，如支持`CMFCColorButton`超链接的[CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md)类以及支持颜色选取器对话框的类。

`CMFCButton`对象的样式可以是*三维*、*平*、*半平面*或*无边框*。 按钮文本可以在按钮的左侧、顶部或中心对齐。 在运行时，您可以控制按钮是显示文本、图像、文本还是显示图像。 还可以指定在光标悬停在按钮上时显示特定的光标图像。

直接在代码中或使用 " **MFC 类向导**" 工具和对话框模板创建一个按钮控件。 如果直接创建一个按钮控件，请在应用`CMFCButton`程序中添加一个变量，然后调用该`CMFCButton`对象的`Create`构造函数和方法。 如果使用**MFC 类向导**，请向应用程序`CButton`中添加一个变量，然后将该变量的类型从`CButton`更改为`CMFCButton`。

若要在对话框应用程序中处理通知消息，请为每个通知添加消息映射项和事件处理程序。 `CMFCButton`对象发送的通知与`CButton`对象发送的通知相同。

## <a name="example"></a>示例

下面的示例演示如何使用`CMFCButton`类中的各种方法配置按钮的属性。 该示例是[新控件示例](../../overview/visual-cpp-samples.md)的一部分。

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

**标头：** afxbutton

##  <a name="cleanup"></a>CMFCButton：：清理

重置内部变量并释放已分配的资源，如图像、位图和图标。

```
virtual void CleanUp();
```

##  <a name="enablefulltexttooltip"></a>  CMFCButton::EnableFullTextTooltip

指定是在大的工具提示窗口中显示工具提示的完整文本还是在小工具提示窗口中显示文本的截断版本。

```
void EnableFullTextTooltip(BOOL bOn=TRUE);
```

### <a name="parameters"></a>参数

*bOn*<br/>
中若要显示所有文本，则为 TRUE;如果显示截断的文本，则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="enablemenufont"></a>CMFCButton::EnableMenuFont

指定按钮文本字体是否与应用程序菜单字体相同。

```
void EnableMenuFont(
    BOOL bOn=TRUE,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>参数

*bOn*<br/>
中若要使用应用程序菜单字体作为按钮文本字体，则为 TRUE;如果使用系统字体，则为 FALSE。 默认值为 TRUE。

*bRedraw*<br/>
中若要立即重绘屏幕，则为 TRUE;否则为 FALSE。 默认值为 TRUE。

### <a name="remarks"></a>备注

如果不使用此方法指定按钮文本字体，则可以使用[CWnd：： SetFont](../../mfc/reference/cwnd-class.md#setfont)方法指定字体。 如果根本不指定字体，框架将设置默认字体。

##  <a name="enablewindowstheming"></a>CMFCButton::EnableWindowsTheming

指定按钮边框的样式是否对应于当前的 Windows 主题。

```
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
中如果为 TRUE，则使用当前的 Windows 主题绘制按钮边框;如果不使用 Windows 主题，则为 FALSE。 默认值为 TRUE。

### <a name="remarks"></a>备注

此方法会影响您的应用程序中从`CMFCButton`类派生的所有按钮。

##  <a name="gettooltipctrl"></a>  CMFCButton::GetToolTipCtrl

返回对基础工具提示控件的引用。

```
CToolTipCtrl& GetToolTipCtrl();
```

### <a name="return-value"></a>返回值

对基础工具提示控件的引用。

### <a name="remarks"></a>备注

##  <a name="isautocheck"></a>CMFCButton::IsAutoCheck

指示复选框或单选按钮是否为 "自动" 按钮。

```
BOOL IsAutoCheck() const;
```

### <a name="return-value"></a>返回值

如果该按钮具有 style BS_AUTOCHECKBOX 或 BS_AUTORADIOBUTTON，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="isautorepeatcommandmode"></a>CMFCButton::IsAutorepeatCommandMode

指示按钮是否设置为自动重复模式。

```
BOOL IsAutorepeatCommandMode() const;
```

### <a name="return-value"></a>返回值

如果按钮设置为自动重复模式，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

使用[CMFCButton：： SetAutorepeatMode](#setautorepeatmode)方法可将按钮设置为自动重复模式。

##  <a name="ischeckbox"></a>CMFCButton::IsCheckBox

指示按钮是否为复选框按钮。

```
BOOL IsCheckBox() const;
```

### <a name="return-value"></a>返回值

如果该按钮具有 BS_CHECKBOX 或 BS_AUTOCHECKBOX 样式，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="ischecked"></a>CMFCButton：： IsChecked

指示是否选中当前按钮。

```
BOOL IsChecked() const;
```

### <a name="return-value"></a>返回值

如果选中 "当前" 按钮，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

框架使用不同的方法来指示检查不同种类的按钮。 例如，当单选按钮包含点时将其选中;如果复选框包含**X**，则选中复选框。

##  <a name="ishighlighted"></a>CMFCButton::IsHighlighted

指示是否突出显示某个按钮。

```
BOOL IsHighlighted() const;
```

### <a name="return-value"></a>返回值

如果按钮突出显示，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

当鼠标悬停在按钮上时，将突出显示某个按钮。

##  <a name="ispressed"></a>CMFCButton::IsPressed

指示按钮是否已按下并突出显示。

```
BOOL IsPressed() const;
```

### <a name="return-value"></a>返回值

如果按下了按钮，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="ispushed"></a>CMFCButton::IsPushed

指示是否推送按钮。

```
BOOL IsPushed() const;
```

### <a name="return-value"></a>返回值

如果按钮被推送，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="isradiobutton"></a>CMFCButton::IsRadioButton

指示按钮是否为单选按钮。

```
BOOL IsRadioButton() const;
```

### <a name="return-value"></a>返回值

如果按钮样式为 BS_RADIOBUTTON 或 BS_AUTORADIOBUTTON，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="iswindowsthemingenabled"></a>CMFCButton::IsWindowsThemingEnabled

指示按钮边框的样式是否对应于当前的 Windows 主题。

```
static BOOL IsWindowsThemingEnabled();
```

### <a name="return-value"></a>返回值

如果按钮边框的样式与当前的 Windows 主题相对应，则为 TRUE;否则为 FALSE。

## <a name="a-namem_bdontusewinxptheme-cmfcbuttonm_bdontusewinxptheme"></a><a name="m_bDontUseWinXPTheme"/>CMFCButton::m_bDontUseWinXPTheme

指定在绘制按钮时是否使用 Windows XP 主题。

```
BOOL m_bDontUseWinXPTheme;
```

##  <a name="m_bdrawfocus"></a>  CMFCButton::m_bDrawFocus

指示是否在按钮周围绘制聚焦框。

```
BOOL m_bDrawFocus;
```

### <a name="remarks"></a>备注

将 " `m_bDrawFocus`成员" 设置为 "TRUE"，以指定框架将在按钮的文本和图像周围绘制聚焦框（如果按钮接收到焦点）。

`CMFCButton`构造函数将此成员初始化为 TRUE。

##  <a name="m_bGrayDisabled"></a>CMFCButton::m_bGrayDisabled

如果为 TRUE，则允许将禁用的按钮绘制为灰显。

```
BOOL m_bGrayDisabled;
```

##  <a name="m_bhighlightchecked"></a>CMFCButton::m_bHighlightChecked

指示当光标悬停在 BS_CHECKBOX 按钮上时是否突出显示该按钮。

```
BOOL m_bHighlightChecked;
```

### <a name="remarks"></a>备注

`m_bHighlightChecked`将成员设置为 TRUE，以指定框架在鼠标悬停在 BS_CHECKBOX 按钮上时，将突出显示该按钮。

##  <a name="m_bResponseOnButtonDown"></a>CMFCButton::m_bResponseOnButtonDown

指示是否响应按钮按下事件。

```
BOOL m_bResponseOnButtonDown;
```

##  <a name="m_brightimage"></a>CMFCButton::m_bRightImage

指示是否在按钮右侧显示图像。

```
BOOL m_bRightImage;
```

##  <a name="m_bTopImage"></a>  CMFCButton::m_bTopImage](#m_bTopImage)

指示图像是否位于按钮的顶部。

```
BOOL m_bTopImage;
```

### <a name="remarks"></a>备注

`m_bRightImage`将成员设置为 TRUE，以指定框架将在按钮的文本标签右侧显示该按钮的图像。

##  <a name="m_btransparent"></a>  CMFCButton::m_bTransparent

指示按钮是否透明。

```
BOOL m_bTransparent;
```

### <a name="remarks"></a>备注

`m_bTransparent`将成员设置为 TRUE，以指定该框架将使该按钮透明。 `CMFCButton`构造函数将此成员初始化为 FALSE。

##  <a name="m_nalignstyle"></a>CMFCButton::m_nAlignStyle

指定按钮文本的对齐方式。

```
AlignStyle m_nAlignStyle;
```

### <a name="remarks"></a>备注

使用下列`CMFCButton::AlignStyle`枚举值之一来指定按钮文本的对齐方式：

|值|描述|
|-----------|-----------------|
|ALIGN_CENTER|缺省值将按钮文本与按钮中心对齐。|
|ALIGN_LEFT|将按钮文本与按钮的左侧对齐。|
|ALIGN_RIGHT|将按钮文本与按钮右侧对齐。|

`CMFCButton`构造函数将此成员初始化为 ALIGN_CENTER。

##  <a name="m_bWasDblClk"></a>CMFCButton：： m_bWasDblClk] （#m_bWasDblClk） |

指示最后一个 click 事件是否是双击。 |

```
BOOL m_bWasDblClk;
```

##  <a name="m_nflatstyle"></a>  CMFCButton::m_nFlatStyle

指定按钮的样式，例如无边框、平面、半平面或三维。

```
FlatStyle  m_nFlatStyle;
```

### <a name="remarks"></a>备注

下表列出`CMFCButton::m_nFlatStyle`了用于指定按钮外观的枚举值。

|值|描述|
|-----------|-----------------|
|BUTTONSTYLE_3D|缺省值此按钮显示为具有较高的三维边。 单击该按钮时，该按钮将显示为深缩进。|
|BUTTONSTYLE_FLAT|当鼠标不停留在按钮上时，按钮显示为二维并且不具有凸起边。 当鼠标悬停在按钮上时，按钮显示为具有低三维边。 单击该按钮时，该按钮将看上去按浅浅缩进。|
|BUTTONSTYLE_SEMIFLAT|按钮显示为具有较低的三维边。 单击该按钮时，该按钮将显示为深缩进。|
|BUTTONSTYLE_NOBORDERS|此按钮不具有凸起边并且始终显示为二维。 在单击按钮时，该按钮看起来不是缩进的。|

`CMFCButton`构造函数将此成员初始化为 BUTTONSTYLE_3D。

### <a name="example"></a>示例

下面的示例演示如何`m_nFlatStyle` `CMFCButton`在类中设置成员变量的值。 此示例是[新控件示例](../../overview/visual-cpp-samples.md)的一部分。

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

*pDC*<br/>
中指向设备上下文的指针。

*rect*<br/>
中对限定按钮的矩形的引用。

*uiState*<br/>
中当前按钮状态。 有关详细信息，请参阅`itemState` [DRAWITEMSTRUCT 结构](/windows/win32/api/winuser/ns-winuser-drawitemstruct)主题的成员。

### <a name="remarks"></a>备注

重写此方法以使用自己的代码绘制按钮。

##  <a name="ondrawborder"></a>  CMFCButton::OnDrawBorder

由框架调用，用于绘制按钮的边框。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中指向设备上下文的指针。

*rectClient*<br/>
中对限定按钮的矩形的引用。

*uiState*<br/>
中当前按钮状态。 有关详细信息，请参阅`itemState` [DRAWITEMSTRUCT 结构](/windows/win32/api/winuser/ns-winuser-drawitemstruct)主题的成员。

### <a name="remarks"></a>备注

重写此方法以使用自己的代码绘制边框。

##  <a name="ondrawfocusrect"></a>  CMFCButton::OnDrawFocusRect

由框架调用，用于绘制按钮的聚焦框。

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中指向设备上下文的指针。

*rectClient*<br/>
中对限定按钮的矩形的引用。

### <a name="remarks"></a>备注

重写此方法以使用自己的代码绘制聚焦框。

##  <a name="ondrawtext"></a>  CMFCButton::OnDrawText

由框架调用，用于绘制按钮文本。

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
中指向设备上下文的指针。

*rect*<br/>
中对限定按钮的矩形的引用。

*strText*<br/>
中要绘制的文本。

*uiDTFlags*<br/>
中指定如何设置文本格式的标志。 有关详细信息，请参阅[CDC：:D rawtext](../../mfc/reference/cdc-class.md#drawtext)方法的*nFormat*参数。

*uiState*<br/>
[in] 保留。

### <a name="remarks"></a>备注

重写此方法以使用自己的代码绘制按钮文本。

##  <a name="onfillbackground"></a>  CMFCButton::OnFillBackground

由框架调用，用于绘制按钮文本的背景。

```
virtual void OnFillBackground(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中指向设备上下文的指针。

*rectClient*<br/>
中对限定按钮的矩形的引用。

### <a name="remarks"></a>备注

重写此方法以使用自己的代码绘制按钮的背景。

##  <a name="selectfont"></a>  CMFCButton::SelectFont

检索与指定的设备上下文关联的字体。

```
virtual CFont* SelectFont(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中指向设备上下文的指针。

### <a name="return-value"></a>返回值

重写此方法以使用自己的代码来检索字体。

### <a name="remarks"></a>备注

##  <a name="setautorepeatmode"></a>CMFCButton::SetAutorepeatMode

将按钮设置为自动重复模式。

```
void SetAutorepeatMode(int nTimeDelay=500);
```

### <a name="parameters"></a>参数

*nTimeDelay*<br/>
中指定发送到父窗口的消息间间隔的非负数。 间隔以毫秒为单位，其默认值为500毫秒。 指定零以禁用自动重复消息模式。

### <a name="remarks"></a>备注

此方法会导致按钮持续向父窗口发送 WM_COMMAND 消息，直到释放该按钮，或将*nTimeDelay*参数设置为零。

##  <a name="setcheckedimage"></a>  CMFCButton::SetCheckedImage

设置选中按钮的图像。

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

*hIcon*<br/>
中包含新图像的位图和掩码的图标的句柄。

*bAutoDestroy*<br/>
中如果指定自动销毁位图资源，则为 TRUE;否则为 FALSE。 默认值为 TRUE。

*hIconHot*<br/>
中包含所选状态的图像的图标的句柄。

*hBitmap*<br/>
中包含未选中状态图像的位图的句柄。

*hBitmapHot*<br/>
中包含所选状态的图像的位图的句柄。

*bMap3dColors*<br/>
中指定按钮背景的透明颜色;即按钮的图符。 若要使用颜色值 RGB （192，192，192），则为 TRUE;若为 FALSE，则使用由`AFX_GLOBAL_DATA::clrBtnFace`定义的颜色值。

*uiBmpResId*<br/>
中未选择的映像的资源 ID。

*uiBmpHotResId*<br/>
中所选映像的资源 ID。

*hIconDisabled*<br/>
中已禁用图像的图标的句柄。

*hBitmapDisabled*<br/>
中包含已禁用图像的位图的句柄。

*uiBmpDsblResID*<br/>
中已禁用位图的资源 ID。

*bAlphaBlend*<br/>
中如果仅使用使用 alpha 通道的32位映像，则为 TRUE;FALSE，则不只使用 alpha 通道图像。 默认值为 FALSE。

### <a name="remarks"></a>备注

##  <a name="setfacecolor"></a>  CMFCButton::SetFaceColor

设置按钮文本的背景色。

```
void SetFaceColor(
    COLORREF crFace,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>参数

*crFace*<br/>
中RGB 颜色值。

*bRedraw*<br/>
中若要立即重绘屏幕，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

使用此方法可为按钮背景（面部）定义一种新的填充颜色。 请注意，当[CMFCButton：： m_bTransparent](#m_btransparent)成员变量为 TRUE 时，不填充背景。

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

*hIcon*<br/>
中包含新图像的位图和掩码的图标的句柄。

*bAutoDestroy*<br/>
中如果指定自动销毁位图资源，则为 TRUE;否则为 FALSE。 默认值为 TRUE。

*hIconHot*<br/>
中包含所选状态的图像的图标的句柄。

*hBitmap*<br/>
中包含未选中状态图像的位图的句柄。

*hBitmapHot*<br/>
中包含所选状态的图像的位图的句柄。

*uiBmpResId*<br/>
中未选择的映像的资源 ID。

*uiBmpHotResId*<br/>
中所选映像的资源 ID。

*bMap3dColors*<br/>
中指定按钮背景的透明颜色;即按钮的图符。 若要使用颜色值 RGB （192，192，192），则为 TRUE;若为 FALSE，则使用由`AFX_GLOBAL_DATA::clrBtnFace`定义的颜色值。

*hIconDisabled*<br/>
中已禁用图像的图标的句柄。

*hBitmapDisabled*<br/>
中包含已禁用图像的位图的句柄。

*uiBmpDsblResID*<br/>
中已禁用位图的资源 ID。

*bAlphaBlend*<br/>
中如果仅使用使用 alpha 通道的32位映像，则为 TRUE;FALSE，则不只使用 alpha 通道图像。 默认值为 FALSE。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

下面的示例演示如何`SetImage` `CMFCButton`在类中使用方法的各种版本。 该示例是[新控件示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]

##  <a name="setmousecursor"></a>CMFCButton::SetMouseCursor

设置游标图像。

```
void SetMouseCursor(HCURSOR hcursor);
```

### <a name="parameters"></a>参数

*hcursor*<br/>
中游标的句柄。

### <a name="remarks"></a>备注

使用此方法可将光标图像（如手形光标）与按钮相关联。 将从应用程序资源加载光标。

### <a name="example"></a>示例

下面的示例演示如何使用`SetMouseCursor` `CMFCButton`类中的方法。 示例是[新控件示例](../../overview/visual-cpp-samples.md)中的代码的一部分。

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]

##  <a name="setmousecursorhand"></a>CMFCButton::SetMouseCursorHand

将光标设置为指针的图像。

```
void SetMouseCursorHand();
```

### <a name="remarks"></a>备注

使用此方法将手的光标图像与按钮相关联。 将从应用程序资源加载光标。

##  <a name="setstdimage"></a>CMFCButton::SetStdImage

`CMenuImages`使用对象设置按钮图像。

```
void SetStdImage(
    CMenuImages::IMAGES_IDS id,
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```

### <a name="parameters"></a>参数

*id*<br/>
中`CMenuImage::IMAGES_IDS`枚举中定义的一个按钮图像标识符。 图像值指定图像，如箭头、pin 和单选按钮。

State<br/>
中`CMenuImages::IMAGE_STATE`枚举中定义的按钮图像状态标识符之一。 图像状态指定按钮颜色，如黑色、灰色、浅灰色、白色和暗灰色。 默认值为 `CMenuImages::ImageBlack`。

*idDisabled*<br/>
中`CMenuImage::IMAGES_IDS`枚举中定义的一个按钮图像标识符。 图像指示该按钮已禁用。 默认值为第一个按钮图像（ `CMenuImages::IdArrowDown`）。

### <a name="remarks"></a>备注

##  <a name="settextcolor"></a>CMFCButton::SetTextColor

为未选中的按钮设置按钮文本的颜色。

```
void SetTextColor(COLORREF clrText);
```

### <a name="parameters"></a>参数

*clrText*<br/>
中RGB 颜色值。

### <a name="remarks"></a>备注

##  <a name="settexthotcolor"></a>CMFCButton::SetTextHotColor

设置所选按钮的按钮文本颜色。

```
void SetTextHotColor(COLORREF clrTextHot);
```

### <a name="parameters"></a>参数

*clrTextHot*<br/>
中RGB 颜色值。

### <a name="remarks"></a>备注

##  <a name="settooltip"></a>CMFCButton::SetTooltip

将工具提示与按钮相关联。

```
void SetTooltip(LPCTSTR lpszToolTipText);
```

### <a name="parameters"></a>参数

*lpszToolTipText*<br/>
中指向工具提示的文本的指针。 指定 NULL 可禁用工具提示。

### <a name="remarks"></a>备注

##  <a name="sizetocontent"></a>CMFCButton：： System.windows.window.sizetocontent

调整按钮的大小以包含其按钮文本和图像。

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>参数

*bCalcOnly*<br/>
中如果计算，但不更改按钮的新大小，则为 TRUE;若要更改按钮大小，则为 FALSE。 默认值为 FALSE。

### <a name="return-value"></a>返回值

一个`CSize`对象，该对象包含按钮的新大小。

### <a name="remarks"></a>备注

默认情况下，此方法将计算新的大小，该大小包含10像素的水平边距和5像素的垂直边距。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCLinkCtrl 类](../../mfc/reference/cmfclinkctrl-class.md)<br/>
[CMFCColorButton 类](../../mfc/reference/cmfccolorbutton-class.md)<br/>
[CMFCMenuButton 类](../../mfc/reference/cmfcmenubutton-class.md)
