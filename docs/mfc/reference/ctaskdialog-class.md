---
title: CTaskDialog Class
ms.date: 11/19/2018
f1_keywords:
- CTaskDialog
- AFXTASKDIALOG/CTaskDialog
- AFXTASKDIALOG/CTaskDialog::CTaskDialog
- AFXTASKDIALOG/CTaskDialog::AddCommandControl
- AFXTASKDIALOG/CTaskDialog::AddRadioButton
- AFXTASKDIALOG/CTaskDialog::ClickCommandControl
- AFXTASKDIALOG/CTaskDialog::ClickRadioButton
- AFXTASKDIALOG/CTaskDialog::DoModal
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonCount
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonFlag
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonId
- AFXTASKDIALOG/CTaskDialog::GetOptions
- AFXTASKDIALOG/CTaskDialog::GetSelectedCommandControlID
- AFXTASKDIALOG/CTaskDialog::GetSelectedRadioButtonID
- AFXTASKDIALOG/CTaskDialog::GetVerificationCheckboxState
- AFXTASKDIALOG/CTaskDialog::IsCommandControlEnabled
- AFXTASKDIALOG/CTaskDialog::IsRadioButtonEnabled
- AFXTASKDIALOG/CTaskDialog::IsSupported
- AFXTASKDIALOG/CTaskDialog::LoadCommandControls
- AFXTASKDIALOG/CTaskDialog::LoadRadioButtons
- AFXTASKDIALOG/CTaskDialog::NavigateTo
- AFXTASKDIALOG/CTaskDialog::OnCommandControlClick
- AFXTASKDIALOG/CTaskDialog::OnCreate
- AFXTASKDIALOG/CTaskDialog::OnDestroy
- AFXTASKDIALOG/CTaskDialog::OnExpandButtonClick
- AFXTASKDIALOG/CTaskDialog::OnHelp
- AFXTASKDIALOG/CTaskDialog::OnHyperlinkClick
- AFXTASKDIALOG/CTaskDialog::OnInit
- AFXTASKDIALOG/CTaskDialog::OnNavigatePage
- AFXTASKDIALOG/CTaskDialog::OnRadioButtonClick
- AFXTASKDIALOG/CTaskDialog::OnTimer
- AFXTASKDIALOG/CTaskDialog::OnVerificationCheckboxClick
- AFXTASKDIALOG/CTaskDialog::RemoveAllCommandControls
- AFXTASKDIALOG/CTaskDialog::RemoveAllRadioButtons
- AFXTASKDIALOG/CTaskDialog::SetCommandControlOptions
- AFXTASKDIALOG/CTaskDialog::SetCommonButtonOptions
- AFXTASKDIALOG/CTaskDialog::SetCommonButtons
- AFXTASKDIALOG/CTaskDialog::SetContent
- AFXTASKDIALOG/CTaskDialog::SetDefaultCommandControl
- AFXTASKDIALOG/CTaskDialog::SetDefaultRadioButton
- AFXTASKDIALOG/CTaskDialog::SetDialogWidth
- AFXTASKDIALOG/CTaskDialog::SetExpansionArea
- AFXTASKDIALOG/CTaskDialog::SetFooterIcon
- AFXTASKDIALOG/CTaskDialog::SetFooterText
- AFXTASKDIALOG/CTaskDialog::SetMainIcon
- AFXTASKDIALOG/CTaskDialog::SetMainInstruction
- AFXTASKDIALOG/CTaskDialog::SetOptions
- AFXTASKDIALOG/CTaskDialog::SetProgressBarMarquee
- AFXTASKDIALOG/CTaskDialog::SetProgressBarPosition
- AFXTASKDIALOG/CTaskDialog::SetProgressBarRange
- AFXTASKDIALOG/CTaskDialog::SetProgressBarState
- AFXTASKDIALOG/CTaskDialog::SetRadioButtonOptions
- AFXTASKDIALOG/CTaskDialog::SetVerificationCheckbox
- AFXTASKDIALOG/CTaskDialog::SetVerificationCheckboxText
- AFXTASKDIALOG/CTaskDialog::SetWindowTitle
- AFXTASKDIALOG/CTaskDialog::ShowDialog
- AFXTASKDIALOG/CTaskDialog::TaskDialogCallback
helpviewer_keywords:
- CTaskDialog [MFC], CTaskDialog
- CTaskDialog [MFC], AddCommandControl
- CTaskDialog [MFC], AddRadioButton
- CTaskDialog [MFC], ClickCommandControl
- CTaskDialog [MFC], ClickRadioButton
- CTaskDialog [MFC], DoModal
- CTaskDialog [MFC], GetCommonButtonCount
- CTaskDialog [MFC], GetCommonButtonFlag
- CTaskDialog [MFC], GetCommonButtonId
- CTaskDialog [MFC], GetOptions
- CTaskDialog [MFC], GetSelectedCommandControlID
- CTaskDialog [MFC], GetSelectedRadioButtonID
- CTaskDialog [MFC], GetVerificationCheckboxState
- CTaskDialog [MFC], IsCommandControlEnabled
- CTaskDialog [MFC], IsRadioButtonEnabled
- CTaskDialog [MFC], IsSupported
- CTaskDialog [MFC], LoadCommandControls
- CTaskDialog [MFC], LoadRadioButtons
- CTaskDialog [MFC], NavigateTo
- CTaskDialog [MFC], OnCommandControlClick
- CTaskDialog [MFC], OnCreate
- CTaskDialog [MFC], OnDestroy
- CTaskDialog [MFC], OnExpandButtonClick
- CTaskDialog [MFC], OnHelp
- CTaskDialog [MFC], OnHyperlinkClick
- CTaskDialog [MFC], OnInit
- CTaskDialog [MFC], OnNavigatePage
- CTaskDialog [MFC], OnRadioButtonClick
- CTaskDialog [MFC], OnTimer
- CTaskDialog [MFC], OnVerificationCheckboxClick
- CTaskDialog [MFC], RemoveAllCommandControls
- CTaskDialog [MFC], RemoveAllRadioButtons
- CTaskDialog [MFC], SetCommandControlOptions
- CTaskDialog [MFC], SetCommonButtonOptions
- CTaskDialog [MFC], SetCommonButtons
- CTaskDialog [MFC], SetContent
- CTaskDialog [MFC], SetDefaultCommandControl
- CTaskDialog [MFC], SetDefaultRadioButton
- CTaskDialog [MFC], SetDialogWidth
- CTaskDialog [MFC], SetExpansionArea
- CTaskDialog [MFC], SetFooterIcon
- CTaskDialog [MFC], SetFooterText
- CTaskDialog [MFC], SetMainIcon
- CTaskDialog [MFC], SetMainInstruction
- CTaskDialog [MFC], SetOptions
- CTaskDialog [MFC], SetProgressBarMarquee
- CTaskDialog [MFC], SetProgressBarPosition
- CTaskDialog [MFC], SetProgressBarRange
- CTaskDialog [MFC], SetProgressBarState
- CTaskDialog [MFC], SetRadioButtonOptions
- CTaskDialog [MFC], SetVerificationCheckbox
- CTaskDialog [MFC], SetVerificationCheckboxText
- CTaskDialog [MFC], SetWindowTitle
- CTaskDialog [MFC], ShowDialog
- CTaskDialog [MFC], TaskDialogCallback
ms.assetid: 1991ec98-ae56-4483-958b-233809c8c559
ms.openlocfilehash: e2f77a2eda4397ed368e477165e876f9b8fbf936
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502347"
---
# <a name="ctaskdialog-class"></a>CTaskDialog Class

功能类似于消息框，但可向用户显示额外信息的弹出对话框。 `CTaskDialog` 还包括从用户那里收集信息的功能。

## <a name="syntax"></a>语法

```
class CTaskDialog : public CObject
```

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|||
|-|-|
|[CTaskDialog:: CTaskDialog](#ctaskdialog)|构造 `CTaskDialog` 对象。|

### <a name="methods"></a>方法

|||
|-|-|
|[CTaskDialog::AddCommandControl](#addcommandcontrol)|向添加一个命令按钮控件`CTaskDialog`。|
|[CTaskDialog::AddRadioButton](#addradiobutton)|向添加一个单选按钮`CTaskDialog`。|
|[CTaskDialog::ClickCommandControl](#clickcommandcontrol)|以编程方式单击命令按钮控件或常用按钮。|
|[CTaskDialog::ClickRadioButton](#clickradiobutton)|以编程方式单击单选按钮。|
|[CTaskDialog::DoModal](#domodal)|显示`CTaskDialog`。|
|[CTaskDialog::GetCommonButtonCount](#getcommonbuttoncount)|检索可用的常用按钮数。|
|[CTaskDialog::GetCommonButtonFlag](#getcommonbuttonflag)|将标准 Windows 按钮转换为与`CTaskDialog`类关联的通用按钮类型。|
|[CTaskDialog::GetCommonButtonId](#getcommonbuttonid)|将与`CTaskDialog`类关联的通用按钮类型之一转换为标准 Windows 按钮。|
|[CTaskDialog::GetOptions](#getoptions)|返回此`CTaskDialog`的选项标志。|
|[CTaskDialog::GetSelectedCommandControlID](#getselectedcommandcontrolid)|返回所选命令按钮控件。|
|[CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid)|返回选定的单选按钮。|
|[CTaskDialog::GetVerificationCheckboxState](#getverificationcheckboxstate)|检索验证复选框的状态。|
|[CTaskDialog::IsCommandControlEnabled](#iscommandcontrolenabled)|确定命令按钮控件或通用按钮是否已启用。|
|[CTaskDialog::IsRadioButtonEnabled](#isradiobuttonenabled)|确定是否启用单选按钮。|
|[CTaskDialog:: IsSupported](#issupported)|确定运行应用程序的计算机是否支持`CTaskDialog`。|
|[CTaskDialog::LoadCommandControls](#loadcommandcontrols)|使用字符串表中的数据添加命令按钮控件。|
|[CTaskDialog::LoadRadioButtons](#loadradiobuttons)|使用字符串表中的数据添加单选按钮。|
|[CTaskDialog::NavigateTo](#navigateto)|将焦点转移到另`CTaskDialog`一个。|
|[CTaskDialog::OnCommandControlClick](#oncommandcontrolclick)|当用户单击命令按钮控件时, 框架会调用此方法。|
|[CTaskDialog::OnCreate](#oncreate)|框架在创建`CTaskDialog`后将调用此方法。|
|[CTaskDialog::OnDestroy](#ondestroy)|框架在销毁`CTaskDialog`之前立即调用此方法。|
|[CTaskDialog::OnExpandButtonClick](#onexpandbuttonclick)|当用户单击展开按钮时, 框架会调用此方法。|
|[CTaskDialog::OnHelp](#onhelp)|当用户请求帮助时, 框架会调用此方法。|
|[CTaskDialog::OnHyperlinkClick](#onhyperlinkclick)|用户单击某个超链接时, 框架会调用此方法。|
|[CTaskDialog::OnInit](#oninit)|初始化时`CTaskDialog` , 框架会调用此方法。|
|[CTaskDialog::OnNavigatePage](#onnavigatepage)|当用户将焦点移动到上`CTaskDialog`的控件时, 框架会调用此方法。|
|[CTaskDialog::OnRadioButtonClick](#onradiobuttonclick)|当用户选择单选按钮控件时, 框架会调用此方法。|
|[CTaskDialog::OnTimer](#ontimer)|当计时器过期时, 框架会调用此方法。|
|[CTaskDialog::OnVerificationCheckboxClick](#onverificationcheckboxclick)|当用户单击 "验证" 复选框时, 框架会调用此方法。|
|[CTaskDialog::RemoveAllCommandControls](#removeallcommandcontrols)|从中`CTaskDialog`移除所有命令控件。|
|[CTaskDialog::RemoveAllRadioButtons](#removeallradiobuttons)|从中`CTaskDialog`移除所有单选按钮。|
|[CTaskDialog::SetCommandControlOptions](#setcommandcontroloptions)|更新上`CTaskDialog`的命令按钮控件。|
|[CTaskDialog::SetCommonButtonOptions](#setcommonbuttonoptions)|更新要启用的常用按钮子集, 并要求 UAC 提升。|
|[CTaskDialog::SetCommonButtons](#setcommonbuttons)|将常见按钮添加到`CTaskDialog`中。|
|[CTaskDialog::SetContent](#setcontent)|更新的内容`CTaskDialog`。|
|[CTaskDialog::SetDefaultCommandControl](#setdefaultcommandcontrol)|指定默认命令按钮控件。|
|[CTaskDialog::SetDefaultRadioButton](#setdefaultradiobutton)|指定默认的单选按钮。|
|[CTaskDialog::SetDialogWidth](#setdialogwidth)|调整的宽度`CTaskDialog`。|
|[CTaskDialog::SetExpansionArea](#setexpansionarea)|更新的扩展区域`CTaskDialog`。|
|[CTaskDialog::SetFooterIcon](#setfootericon)|更新的页脚图标`CTaskDialog`。|
|[CTaskDialog::SetFooterText](#setfootertext)|更新脚注`CTaskDialog`中的文本。|
|[CTaskDialog::SetMainIcon](#setmainicon)|更新的主图标`CTaskDialog`。|
|[CTaskDialog::SetMainInstruction](#setmaininstruction)|更新的主指令`CTaskDialog`。|
|[CTaskDialog::SetOptions](#setoptions)|配置的选项`CTaskDialog`。|
|[CTaskDialog::SetProgressBarMarquee](#setprogressbarmarquee)|为配置滚动条`CTaskDialog` , 并将其添加到对话框中。|
|[CTaskDialog::SetProgressBarPosition](#setprogressbarposition)|调整进度栏的位置。|
|[CTaskDialog::SetProgressBarRange](#setprogressbarrange)|调整进度栏的范围。|
|[CTaskDialog::SetProgressBarState](#setprogressbarstate)|设置进度栏的状态, 并将其显示在上`CTaskDialog`。|
|[CTaskDialog::SetRadioButtonOptions](#setradiobuttonoptions)|启用或禁用单选按钮。|
|[CTaskDialog::SetVerificationCheckbox](#setverificationcheckbox)|设置 "验证" 复选框的选中状态。|
|[CTaskDialog::SetVerificationCheckboxText](#setverificationcheckboxtext)|设置 "验证" 复选框右侧的文本。|
|[CTaskDialog::SetWindowTitle](#setwindowtitle)|设置的标题`CTaskDialog`。|
|[CTaskDialog::ShowDialog](#showdialog)|创建并显示`CTaskDialog`。|
|[CTaskDialog::TaskDialogCallback](#taskdialogcallback)|框架将调用此来响应各种 Windows 消息。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|`m_aButtons`|的命令按钮控件`CTaskDialog`数组。|
|`m_aRadioButtons`|的单选按钮控件`CTaskDialog`数组。|
|`m_bVerified`|`TRUE`指示选中 "验证" 复选框。`FALSE`指示它不是。|
|`m_footerIcon`|页脚中的图标`CTaskDialog`。|
|`m_hWnd`|的窗口`CTaskDialog`的句柄。|
|`m_mainIcon`|的主图标`CTaskDialog`。|
|`m_nButtonDisabled`|指示禁用了哪些常用按钮的掩码。|
|`m_nButtonElevation`|指示哪些常见按钮需要 UAC 提升的掩码。|
|`m_nButtonId`|所选命令按钮控件的 ID。|
|`m_nCommonButton`|指示哪些常见按钮显示在上`CTaskDialog`的掩码。|
|`m_nDefaultCommandControl`|显示时`CTaskDialog`所选择的命令按钮控件的 ID。|
|`m_nDefaultRadioButton`|显示时`CTaskDialog`选定的单选按钮控件的 ID。|
|`m_nFlags`|指示的选项`CTaskDialog`的掩码。|
|`m_nProgressPos`|进度栏的当前位置。  该值必须介于 `m_nProgressRangeMin` 和 `m_nProgressRangeMax` 之间。|
|`m_nProgressRangeMax`|进度栏的最大值。|
|`m_nProgressRangeMin`|进度栏的最小值。|
|`m_nProgressState`|进度栏的状态。 有关详细信息, 请参阅[CTaskDialog:: SetProgressBarState](#setprogressbarstate)。|
|`m_nRadioId`|所选单选按钮控件的 ID。|
|`m_nWidth`|的`CTaskDialog`宽度 (以像素为单位)。|
|`m_strCollapse`|隐藏展开后`CTaskDialog`的信息时, 在扩展框右侧显示的字符串。|
|`m_strContent`|的内容字符串`CTaskDialog`。|
|`m_strExpand`|显示展开的`CTaskDialog`信息时, 展开框右侧显示的字符串。|
|`m_strFooter`|的脚注`CTaskDialog`。|
|`m_strInformation`|的展开信息`CTaskDialog`。|
|`m_strMainInstruction`|的主要说明`CTaskDialog`。|
|`m_strTitle`|的标题`CTaskDialog`。|
|`m_strVerification`|在`CTaskDialog`验证复选框右侧显示的字符串。|

## <a name="remarks"></a>备注

`CTaskDialog`类将替换标准 Windows 消息框, 并具有其他功能, 例如用于从用户收集信息的新控件。 此类位于 Visual Studio 2010 和更高版本的 MFC 库中。 `CTaskDialog`从 Windows Vista 开始提供。 较早版本的 Windows 无法显示`CTaskDialog`该对象。 用于`CTaskDialog::IsSupported`在运行时确定当前用户是否可以显示 "任务" 对话框。 仍支持标准 Windows 消息框。

`CTaskDialog`仅当使用 Unicode 库生成应用程序时, 才可用。

具有`CTaskDialog`两个不同的构造函数。 一个构造函数使你能够指定两个命令按钮和最多六个常规按钮控件。 您可以在创建`CTaskDialog`后添加更多命令按钮。 第二个构造函数不支持任何命令按钮, 但您可以添加不限数量的常规按钮控件。 有关构造函数的详细信息, 请参阅[CTaskDialog:: CTaskDialog](#ctaskdialog)。

下图显示了一个示例`CTaskDialog` , 用于说明某些控件的位置。

![CTaskDialog 的示例](../../mfc/reference/media/ctaskdialogsample.png "CTaskDialog 的示例") <br/>
CTaskDialog 示例

## <a name="requirements"></a>要求

**所需的最低操作系统:** Windows Vista

**标头:** afxtaskdialog

##  <a name="addcommandcontrol"></a>CTaskDialog:: AddCommandControl

向添加一个新的`CTaskDialog`命令按钮控件。

```
void AddCommandControl(
    int nCommandControlID,
    const CString& strCaption,
    BOOL bEnabled = TRUE,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>参数

*nCommandControlID*<br/>
中命令控件标识号。

*strCaption*<br/>
中向用户`CTaskDialog`显示的字符串。 使用此字符串说明命令的用途。

*bEnabled*<br/>
中一个布尔参数, 用于指示是启用还是禁用新按钮。

*bRequiresElevation*<br/>
中布尔型参数, 指示命令是否需要提升。

### <a name="remarks"></a>备注

`CTaskDialog Class`可以显示不限数量的命令按钮控件。 但是, 如果`CTaskDialog`显示任何命令按钮控件, 它最多可以显示六个按钮。 `CTaskDialog`如果没有命令按钮控件, 它可以显示不受限制的按钮数。

当用户选择一个命令按钮控件时, 将`CTaskDialog`关闭。 如果你的应用程序使用[CTaskDialog::D omodal](#domodal)显示对话框, `DoModal`则将返回所选命令按钮控件的*nCommandControlID* 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="addradiobutton"></a>CTaskDialog:: AddRadioButton

向添加一个单选按钮`CTaskDialog`。

```
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,
    const CString& strCaption,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>参数

*nRadioButtonID*<br/>
中单选按钮的标识号。

*strCaption*<br/>
中单选按钮旁`CTaskDialog`显示的字符串。

*bEnabled*<br/>
中布尔型参数, 指示是否启用单选按钮。

### <a name="remarks"></a>备注

使用[CTaskDialog 类](../../mfc/reference/ctaskdialog-class.md)的单选按钮, 可以从用户收集信息。 使用函数[CTaskDialog:: GetSelectedRadioButtonID](#getselectedradiobuttonid)确定所选的单选按钮。

不要求 nRadioButtonID 参数对于每个单选按钮都是唯一的。 `CTaskDialog` 但是, 如果不为每个单选按钮使用不同的标识符, 则可能会遇到意外的行为。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="clickcommandcontrol"></a>CTaskDialog:: ClickCommandControl

以编程方式单击命令按钮控件或常用按钮。

```
protected:
void ClickCommandControl(int nCommandControlID) const;
```

### <a name="parameters"></a>参数

*nCommandControlID*<br/>
中要单击的控件的命令 ID。

### <a name="remarks"></a>备注

此方法生成 windows 消息 TDM_CLICK_BUTTON。

##  <a name="clickradiobutton"></a>CTaskDialog:: ClickRadioButton

以编程方式单击单选按钮。

```
protected:
void ClickRadioButton(int nRadioButtonID) const;
```

### <a name="parameters"></a>参数

*nRadioButtonID*<br/>
中要单击的单选按钮的 ID。

### <a name="remarks"></a>备注

此方法生成 windows 消息 TDM_CLICK_RADIO_BUTTON。

##  <a name="ctaskdialog"></a>CTaskDialog:: CTaskDialog

创建[CTaskDialog 类](../../mfc/reference/ctaskdialog-class.md)的实例。

```
CTaskDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nCommonButtons = TDCBF_OK_BUTTON | TDCBF_CANCEL_BUTTON,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));

CTaskDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast,
    int nCommonButtons,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));
```

### <a name="parameters"></a>参数

*strContent*<br/>
中要用于的内容`CTaskDialog`的字符串。

*strMainInstruction*<br/>
中的主要说明`CTaskDialog`。

*strTitle*<br/>
中的标题`CTaskDialog`。

*nCommonButtons*<br/>
中要添加到`CTaskDialog`中的常用按钮的掩码。

*nTaskDialogOptions*<br/>
中要用于的`CTaskDialog`选项集。

*strFooter*<br/>
中要用作脚注的字符串。

*nIDCommandControlsFirst*<br/>
中第一个命令的字符串 ID。

*nIDCommandControlsLast*<br/>
中最后一个命令的字符串 ID。

### <a name="remarks"></a>备注

可以通过两种方式将添加`CTaskDialog`到应用程序。 第一种方法是使用其中一个构造函数创建`CTaskDialog`并使用[CTaskDialog::D omodal](#domodal)显示它。 第二种方法是使用静态函数[CTaskDialog:: ShowDialog](#showdialog), 这样就可以在`CTaskDialog` `CTaskDialog`不显式创建对象的情况下显示。

第二个构造函数通过使用应用程序的资源文件中的数据来创建命令按钮控件。 资源文件中的字符串表包含多个具有关联的字符串 Id 的字符串。 此方法为*nIDCommandControlsFirst*和*nCommandControlsLast*之间的字符串表中的每个有效条目添加一个命令按钮控件。 对于这些命令按钮控件, 字符串表中的字符串是控件的标题, 而字符串 ID 是控件的 ID。

有关有效选项的列表, 请参阅[CTaskDialog:: SetOptions](#setoptions) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="domodal"></a>CTaskDialog::D oModal

`CTaskDialog`显示, 并使其模式化。

```
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```

### <a name="parameters"></a>参数

*hParent*<br/>
中的父窗口`CTaskDialog`。

### <a name="return-value"></a>返回值

与用户所做的选择相对应的整数。

### <a name="remarks"></a>备注

显示[CTaskDialog](../../mfc/reference/ctaskdialog-class.md)的此实例。 然后, 应用程序会等待用户关闭对话框。

当`CTaskDialog`用户选择通用按钮、命令链接控件或`CTaskDialog`关闭时, 将关闭。 返回值是指示用户如何关闭对话框的标识符。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="getcommonbuttoncount"></a>CTaskDialog:: GetCommonButtonCount

检索常用按钮的数目。

```
int GetCommonButtonCount() const;
```

### <a name="return-value"></a>返回值

可用的常用按钮数。

### <a name="remarks"></a>备注

常见按钮是提供给[CTaskDialog:: CTaskDialog](#ctaskdialog)的默认按钮。 [CTaskDialog 类](../../mfc/reference/ctaskdialog-class.md)显示对话框底部的按钮。

CommCtrl 中提供了按钮的枚举列表。

##  <a name="getcommonbuttonflag"></a>CTaskDialog:: GetCommonButtonFlag

将标准 Windows 按钮转换为与[CTaskDialog 类](../../mfc/reference/ctaskdialog-class.md)关联的通用按钮类型。

```
int GetCommonButtonFlag(int nButtonId) const;
```

### <a name="parameters"></a>参数

*nButtonId*<br/>
中标准 Windows 按钮值。

### <a name="return-value"></a>返回值

对应`CTaskDialog`的通用按钮的值。 如果没有对应的通用按钮, 此方法将返回0。

##  <a name="getcommonbuttonid"></a>CTaskDialog:: GetCommonButtonId

将与[CTaskDialog 类](../../mfc/reference/ctaskdialog-class.md)关联的通用按钮类型之一转换为标准 Windows 按钮。

```
int GetCommonButtonId(int nFlag);
```

### <a name="parameters"></a>参数

*nFlag*<br/>
中与`CTaskDialog`类关联的通用按钮类型。

### <a name="return-value"></a>返回值

对应的标准 Windows 按钮的值。 如果没有对应的 Windows 按钮, 则该方法返回0。

##  <a name="getoptions"></a>CTaskDialog:: GetOptions

返回此`CTaskDialog`的选项标志。

```
int GetOptions() const;
```

### <a name="return-value"></a>返回值

的标志`CTaskDialog`。

### <a name="remarks"></a>备注

有关可用于[CTaskDialog 类](../../mfc/reference/ctaskdialog-class.md)的选项的详细信息, 请参阅[CTaskDialog:: SetOptions](#setoptions)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="getselectedcommandcontrolid"></a>CTaskDialog:: GetSelectedCommandControlID

返回所选命令按钮控件。

```
int GetSelectedCommandControlID() const;
```

### <a name="return-value"></a>返回值

当前所选命令按钮控件的 ID。

### <a name="remarks"></a>备注

您不必使用此方法来检索用户选择的命令按钮的 ID。 该 ID 由[CTaskDialog::D omodal](#domodal)或[CTaskDialog:: ShowDialog](#showdialog)返回。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="getselectedradiobuttonid"></a>CTaskDialog:: GetSelectedRadioButtonID

返回选定的单选按钮。

```
int GetSelectedRadioButtonID() const;
```

### <a name="return-value"></a>返回值

所选单选按钮的 ID。

### <a name="remarks"></a>备注

用户关闭对话框后, 可以使用此方法来检索所选单选按钮。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="getverificationcheckboxstate"></a>CTaskDialog:: GetVerificationCheckboxState

检索验证复选框的状态。

```
BOOL GetVerificationCheckboxState() const;
```

### <a name="return-value"></a>返回值

如果选中此复选框, 则为 TRUE; 否则为 FALSE。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="iscommandcontrolenabled"></a>CTaskDialog:: IsCommandControlEnabled

确定命令按钮控件或按钮是否已启用。

```
BOOL IsCommandControlEnabled(int nCommandControlID) const;
```

### <a name="parameters"></a>参数

*nCommandControlID*<br/>
中要测试的命令按钮控件或按钮的 ID。

### <a name="return-value"></a>返回值

如果启用控件, 则为 TRUE; 否则为 FALSE。

### <a name="remarks"></a>备注

您可以使用此方法来确定两个命令按钮控件和`CTaskDialog`类的常用按钮的可用性。

如果*nCommandControlID*不是通用`CTaskDialog`按钮控件或命令按钮控件的有效标识符, 则此方法将引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="isradiobuttonenabled"></a>CTaskDialog:: IsRadioButtonEnabled

确定是否启用单选按钮。

```
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;
```

### <a name="parameters"></a>参数

*nRadioButtonID*<br/>
中要测试的单选按钮的 ID。

### <a name="return-value"></a>返回值

如果启用单选按钮, 则为 TRUE; 否则为 FALSE。

### <a name="remarks"></a>备注

如果*nRadioButtonID*不是单选按钮的有效标识符, 则此方法将引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="issupported"></a>CTaskDialog:: IsSupported

确定运行应用程序的计算机是否支持`CTaskDialog`。

```
static BOOL IsSupported();
```

### <a name="return-value"></a>返回值

如果计算机支持, `CTaskDialog`则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果运行应用程序的计算机支持`CTaskDialog`类, 请使用此函数在运行时确定。 如果计算机不支持`CTaskDialog`, 则应提供另一种向用户传达信息的方法。 如果应用程序尝试`CTaskDialog`在不`CTaskDialog`支持类的计算机上使用, 则该应用程序会崩溃。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

##  <a name="loadcommandcontrols"></a>CTaskDialog:: LoadCommandControls

使用字符串表中的数据添加命令按钮控件。

```
void LoadCommandControls(
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast);
```

### <a name="parameters"></a>参数

*nIDCommandControlsFirst*<br/>
中第一个命令的字符串 ID。

*nIDCommandControlsLast*<br/>
中最后一个命令的字符串 ID。

### <a name="remarks"></a>备注

此方法使用应用程序的资源文件中的数据创建命令按钮控件。 资源文件中的字符串表包含多个具有关联的字符串 Id 的字符串。 使用此方法添加的新命令按钮控件使用控件标题的字符串和控件 ID 的字符串 ID。 所选字符串的范围由*nIDCommandControlsFirst*和*nCommandControlsLast*(含) 提供。 如果范围中存在空项, 则此方法不会为该项添加命令按钮控件。

默认情况下, 新的命令按钮控件是启用的, 不需要提升。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="loadradiobuttons"></a>CTaskDialog:: LoadRadioButtons

使用字符串表中的数据添加单选按钮控件。

```
void LoadRadioButtons(
    int nIDRadioButtonsFirst,
    int nIDRadioButtonsLast);
```

### <a name="parameters"></a>参数

*nIDRadioButtonsFirst*<br/>
中第一个单选按钮的字符串 ID。

*nIDRadioButtonsLast*<br/>
中最后一个单选按钮的字符串 ID。

### <a name="remarks"></a>备注

此方法通过使用应用程序的资源文件中的数据创建单选按钮。 资源文件中的字符串表包含多个具有关联的字符串 Id 的字符串。 使用此方法添加的新单选按钮使用该单选按钮的标题的字符串以及单选按钮 ID 的字符串 ID。 所选字符串的范围由*nIDRadioButtonsFirst*和*nRadioButtonsLast*(含) 提供。 如果范围中存在空项, 则此方法不会为该项添加单选按钮。

默认情况下, 启用新的单选按钮。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="navigateto"></a>CTaskDialog:: NavigateTo

将焦点转移到另`CTaskDialog`一个。

```
protected:
void NavigateTo(CTaskDialog& oTaskDialog) const;
```

### <a name="parameters"></a>参数

*oTaskDialog*<br/>
中接收`CTaskDialog`焦点的。

### <a name="remarks"></a>备注

此方法在显示`CTaskDialog` *oTaskDialog*时隐藏当前的。 *OTaskDialog*显示在与当前`CTaskDialog`相同的位置。

##  <a name="oncommandcontrolclick"></a>CTaskDialog:: OnCommandControlClick

当用户单击命令按钮控件时, 框架会调用此方法。

```
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```

### <a name="parameters"></a>参数

*nCommandControlID*<br/>
中用户选择的命令按钮控件的 ID。

### <a name="return-value"></a>返回值

默认实现返回 S_OK。

### <a name="remarks"></a>备注

在派生类中重写此方法以实现自定义行为。

##  <a name="oncreate"></a>CTaskDialog:: OnCreate

框架在创建`CTaskDialog`后将调用此方法。

```
virtual HRESULT OnCreate();
```

### <a name="return-value"></a>返回值

默认实现返回 S_OK。

### <a name="remarks"></a>备注

在派生类中重写此方法以实现自定义行为。

##  <a name="ondestroy"></a>CTaskDialog:: OnDestroy

框架在销毁`CTaskDialog`之前立即调用此方法。

```
virtual HRESULT OnDestroy();
```

### <a name="return-value"></a>返回值

默认实现返回 S_OK。

### <a name="remarks"></a>备注

在派生类中重写此方法以实现自定义行为。

##  <a name="onexpandbuttonclick"></a>CTaskDialog:: OnExpandButtonClick

当用户单击展开按钮时, 框架会调用此方法。

```
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```

### <a name="parameters"></a>参数

*bExpanded*<br/>
中非零值表示显示额外的信息;0指示隐藏了额外的信息。

### <a name="return-value"></a>返回值

默认实现返回 S_OK。

### <a name="remarks"></a>备注

在派生类中重写此方法以实现自定义行为。

##  <a name="onhelp"></a>CTaskDialog:: OnHelp

当用户请求帮助时, 框架会调用此方法。

```
virtual HRESULT OnHelp();
```

### <a name="return-value"></a>返回值

默认实现返回 S_OK。

### <a name="remarks"></a>备注

在派生类中重写此方法以实现自定义行为。

##  <a name="onhyperlinkclick"></a>CTaskDialog:: OnHyperlinkClick

用户单击某个超链接时, 框架会调用此方法。

```
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```

### <a name="parameters"></a>参数

*strHref*<br/>
中表示超链接的字符串。

### <a name="return-value"></a>返回值

默认实现返回 S_OK。

### <a name="remarks"></a>备注

此方法在返回 S_OK 之前调用[ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) 。

在派生类中重写此方法以实现自定义行为。

##  <a name="oninit"></a>CTaskDialog:: OnInit

初始化时`CTaskDialog` , 框架会调用此方法。

```
virtual HRESULT OnInit();
```

### <a name="return-value"></a>返回值

默认实现返回 S_OK。

### <a name="remarks"></a>备注

在派生类中重写此方法以实现自定义行为。

##  <a name="onnavigatepage"></a>CTaskDialog:: OnNavigatePage

框架调用此方法来响应[CTaskDialog:: NavigateTo](#navigateto)方法。

```
virtual HRESULT OnNavigatePage();
```

### <a name="return-value"></a>返回值

默认实现返回 S_OK。

### <a name="remarks"></a>备注

在派生类中重写此方法以实现自定义行为。

##  <a name="onradiobuttonclick"></a>CTaskDialog:: OnRadioButtonClick

当用户选择单选按钮控件时, 框架会调用此方法。

```
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```

### <a name="parameters"></a>参数

*nRadioButtonID*<br/>
中用户单击的单选按钮控件的 ID。

### <a name="return-value"></a>返回值

默认实现返回 S_OK。

### <a name="remarks"></a>备注

在派生类中重写此方法以实现自定义行为。

##  <a name="ontimer"></a>CTaskDialog:: OnTimer

当计时器过期时, 框架会调用此方法。

```
virtual HRESULT OnTimer(long lTime);
```

### <a name="parameters"></a>参数

*lTime*<br/>
中创建或计时器重置`CTaskDialog`后的时间 (以毫秒为单位)。

### <a name="return-value"></a>返回值

默认实现返回 S_OK。

### <a name="remarks"></a>备注

在派生类中重写此方法以实现自定义行为。

##  <a name="onverificationcheckboxclick"></a>CTaskDialog:: OnVerificationCheckboxClick

当用户单击 "验证" 复选框时, 框架会调用此方法。

```
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```

### <a name="parameters"></a>参数

*bChecked*<br/>
中如果为 TRUE, 则表示已选中 "验证" 复选框;FALSE 指示它不是。

### <a name="return-value"></a>返回值

默认实现返回 S_OK。

### <a name="remarks"></a>备注

在派生类中重写此方法以实现自定义行为。

##  <a name="removeallcommandcontrols"></a>CTaskDialog:: RemoveAllCommandControls

从中`CTaskDialog`移除所有命令按钮控件。

```
void RemoveAllCommandControls();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="removeallradiobuttons"></a>CTaskDialog:: RemoveAllRadioButtons

从中`CTaskDialog`移除所有单选按钮。

```
void RemoveAllRadioButtons();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setcommandcontroloptions"></a>CTaskDialog:: SetCommandControlOptions

更新上`CTaskDialog`的命令按钮控件。

```
void SetCommandControlOptions(
    int nCommandControlID,
    BOOL bEnabled,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>参数

*nCommandControlID*<br/>
中要更新的命令控件的 ID。

*bEnabled*<br/>
中一个布尔参数, 用于指示指定的命令按钮控件是已启用还是已禁用。

*bRequiresElevation*<br/>
中一个布尔参数, 用于指示指定的命令按钮控件是否需要提升。

### <a name="remarks"></a>备注

使用此方法可更改命令按钮控件是否已启用, 或者是否在将其添加到`CTaskDialog`类后需要提升。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="setcommonbuttonoptions"></a>CTaskDialog:: SetCommonButtonOptions

更新要启用的常用按钮子集并要求 UAC 提升。

```
void SetCommonButtonOptions(
    int nDisabledButtonMask,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>参数

*nDisabledButtonMask*<br/>
中要禁用的常用按钮的掩码。

*nElevationButtonMask*<br/>
中需要提升的常用按钮的掩码。

### <a name="remarks"></a>备注

可以使用构造函数[CTaskDialog:: CTaskDialog](#ctaskdialog)和方法[CTaskDialog:: SetCommonButtons](#setcommonbuttons)将可用的通用按钮设置为[CTaskDialog 类](../../mfc/reference/ctaskdialog-class.md)的实例。 `CTaskDialog::SetCommonButtonOptions`不支持添加新的常用按钮。

如果使用此方法来禁用或提升此`CTaskDialog`功能不可用的通用按钮, 此方法将通过使用 "[确保](diagnostic-services.md#ensure)宏" 引发异常。

此方法启用可用于但不在*nDisabledButtonMask*中`CTaskDialog`的任何按钮, 即使之前已禁用。 此方法以类似的方式对待提升: 当通用按钮可用但未包含在*nElevationButtonMask*中时, 它会将常见按钮记录为不需要提升。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

##  <a name="setcommonbuttons"></a>CTaskDialog:: SetCommonButtons

将常见按钮添加到`CTaskDialog`中。

```
void SetCommonButtons(
    int nButtonMask,
    int nDisabledButtonMask = 0,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>参数

*nButtonMask*<br/>
中要添加到`CTaskDialog`中的按钮的掩码。

*nDisabledButtonMask*<br/>
中要禁用的按钮的掩码。

*nElevationButtonMask*<br/>
中需要提升的按钮的掩码。

### <a name="remarks"></a>备注

创建`CTaskDialog`类的此实例的显示窗口后, 无法调用此方法。 如果执行此操作, 则此方法将引发异常。

*NButtonMask*指示的按钮会重写以前添加到中的`CTaskDialog`所有常用按钮。 只有*nButtonMask*中指示的按钮可用。

如果*nDisabledButtonMask*或*nElevationButtonMask*包含不在*nButtonMask*中的按钮, 则此方法将使用[确保](diagnostic-services.md#ensure)宏引发异常。

默认情况下, 所有常用按钮都处于启用状态, 并且不需要提升权限。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

##  <a name="setcontent"></a>CTaskDialog:: SetContent

更新的内容`CTaskDialog`。

```
void SetContent(const CString& strContent);
```

### <a name="parameters"></a>参数

*strContent*<br/>
中要向用户显示的字符串。

### <a name="remarks"></a>备注

`CTaskDialog`类的内容是在对话框的主要部分中向用户显示的文本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setdefaultcommandcontrol"></a>CTaskDialog:: SetDefaultCommandControl

指定默认命令按钮控件。

```
void SetDefaultCommandControl(int nCommandControlID);
```

### <a name="parameters"></a>参数

*nCommandControlID*<br/>
中要作为默认值的命令按钮控件的 ID。

### <a name="remarks"></a>备注

默认命令按钮控件是第一次向用户显示时`CTaskDialog`选择的控件。

如果它找不到由*nCommandControlID*指定的命令按钮控件, 则此方法将引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

##  <a name="setdefaultradiobutton"></a>CTaskDialog:: SetDefaultRadioButton

指定默认的单选按钮。

```
void SetDefaultRadioButton(int nRadioButtonID);
```

### <a name="parameters"></a>参数

*nRadioButtonID*<br/>
中要作为默认值的单选按钮的 ID。

### <a name="remarks"></a>备注

默认的单选按钮是第一次向用户显示时`CTaskDialog`选择的按钮。

如果它找不到由*nRadioButtonID*指定的单选按钮, 则此方法将引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setdialogwidth"></a>CTaskDialog:: SetDialogWidth

调整的宽度`CTaskDialog`。

```
void SetDialogWidth(int nWidth = 0);
```

### <a name="parameters"></a>参数

*nWidth*<br/>
中对话框的宽度 (以像素为单位)。

### <a name="remarks"></a>备注

参数*nWidth*必须大于或等于0。 否则, 此方法将引发异常。

如果将*nWidth*设置为 0, 则此方法会将该对话框设置为默认大小。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setexpansionarea"></a>CTaskDialog:: SetExpansionArea

更新的扩展区域`CTaskDialog`。

```
void SetExpansionArea(
    const CString& strExpandedInformation,
    const CString& strCollapsedLabel = _T(""),
    const CString& strExpandedLabel = _T(""));
```

### <a name="parameters"></a>参数

*strExpandedInformation*<br/>
中当用户单击展开`CTaskDialog`按钮时, 在对话框的主体中显示的字符串。

*strCollapsedLabel*<br/>
中折叠展开区域时`CTaskDialog` , 展开按钮旁显示的字符串。

*strExpandedLabel*<br/>
中显示展开区域时`CTaskDialog`展开按钮旁显示的字符串。

### <a name="remarks"></a>备注

`CTaskDialog`类的扩展区域使您能够向用户提供附加信息。 扩展区域位于的`CTaskDialog`主要部分, 位于标题和内容字符串的紧下方。

第一次显示时, 它不会显示展开的信息并将`strCollapsedLabel`其放在展开按钮旁边。 `CTaskDialog` 当用户单击展开按钮时, 将显示`CTaskDialog` " *strExpandedInformation* ", 并将标签更改为 " *strExpandedLabel*"。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setfootericon"></a>CTaskDialog:: SetFooterIcon

更新的页脚图标`CTaskDialog`。

```
void SetFooterIcon(HICON hFooterIcon);
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```

### <a name="parameters"></a>参数

*hFooterIcon*<br/>
中的新图标`CTaskDialog`。

*lpszFooterIcon*<br/>
中的新图标`CTaskDialog`。

### <a name="remarks"></a>备注

页脚图标显示在[CTaskDialog 类](../../mfc/reference/ctaskdialog-class.md)的底部。 它可以有关联的页脚文本。 可以用[CTaskDialog:: SetFooterText](#setfootertext)更改页脚文本。

如果`CTaskDialog`显示了, 或输入参数为 NULL, 则此方法将引发异常, 并显示 "[确保](diagnostic-services.md#ensure)宏"。

`CTaskDialog`只能接受或`LPCWSTR`作为页脚图标。 `HICON` 这是通过在构造函数或[CTaskDialog:: SetOptions](#setoptions)中设置选项 TDF_USE_HICON_FOOTER 来配置的。 默认情况下, `CTaskDialog`配置为使用`LPCWSTR`作为页脚图标的输入类型。 如果尝试使用不合适的类型设置图标, 则此方法将生成异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setfootertext"></a>CTaskDialog:: SetFooterText

更新脚注`CTaskDialog`中的文本。

```
void SetFooterText(const CString& strFooterText);
```

### <a name="parameters"></a>参数

*strFooterText*<br/>
中页脚的新文本。

### <a name="remarks"></a>备注

页脚图标会显示在底部`CTaskDialog`的页脚文本旁边。 可以更改[CTaskDialog:: SetFooterIcon](#setfootericon)的页脚图标。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setmainicon"></a>CTaskDialog:: SetMainIcon

更新的主图标`CTaskDialog`。

```
void SetMainIcon(HICON hMainIcon);
void SetMainIcon(LPCWSTR lpszMainIcon);
```

### <a name="parameters"></a>参数

*hMainIcon*<br/>
中新图标。

*lpszMainIcon*<br/>
中新图标。

### <a name="remarks"></a>备注

如果`CTaskDialog`显示了, 或输入参数为 NULL, 则此方法将引发异常, 并显示 "[确保](diagnostic-services.md#ensure)宏"。

`CTaskDialog`只能接受或`LPCWSTR`作为主图标。 `HICON` 可以通过在构造函数中或在[CTaskDialog:: SetOptions](#setoptions)方法中设置 TDF_USE_HICON_MAIN 选项来对此进行配置。 默认情况下, `CTaskDialog`配置为使用`LPCWSTR`作为主图标的输入类型。 如果尝试使用不合适的类型设置图标, 则此方法将生成异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setmaininstruction"></a>CTaskDialog:: SetMainInstruction

更新的主指令`CTaskDialog`。

```
void SetMainInstruction(const CString& strInstructions);
```

### <a name="parameters"></a>参数

*strInstructions*<br/>
中新的主指令。

### <a name="remarks"></a>备注

`CTaskDialog`类的主要说明是用大粗体字体向用户显示的文本。 它位于标题栏下的对话框中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setoptions"></a>CTaskDialog:: SetOptions

配置的选项`CTaskDialog`。

```
void SetOptions(int nOptionFlag);
```

### <a name="parameters"></a>参数

*nOptionFlag*<br/>
中要用于的标志集`CTaskDialog`。

### <a name="remarks"></a>备注

此方法清除的所有当前选项`CTaskDialog`。 若要保留当前的选项, 必须先用[CTaskDialog:: GetOptions](#getoptions)检索它们, 并将它们与要设置的选项组合在一起。

下表列出了所有有效选项。

|||
|-|-|
|TDF_ENABLE_HYPERLINKS|启用中的`CTaskDialog`超链接。|
|TDF_USE_HICON_MAIN|`HICON`将配置`CTaskDialog`为对主图标使用。 替代方法是使用`LPCWSTR`。|
|TDF_USE_HICON_FOOTER|将配置`HICON`为使用作为页脚图标的。 `CTaskDialog` 替代方法是使用`LPCWSTR`。|
|TDF_ALLOW_DIALOG_CANCELLATION|使用户能够`CTaskDialog`通过使用键盘或使用对话框右上角的图标来关闭, 即使未启用 "**取消**" 按钮也是如此。 如果未设置此标志, 并且未启用 "**取消**" 按钮, 则用户无法通过使用 Alt + F4、转义键或标题栏的 "关闭" 按钮来关闭对话框。|
|TDF_USE_COMMAND_LINKS|将配置`CTaskDialog`为使用命令按钮控件。|
|TDF_USE_COMMAND_LINKS_NO_ICON|将配置`CTaskDialog`为使用命令按钮控件, 而不在控件旁边显示一个图标。 TDF_USE_COMMAND_LINKS 重写 TDF_USE_COMMAND_LINKS_NO_ICON。|
|TDF_EXPAND_FOOTER_AREA|指示扩展区域当前已展开。|
|TDF_EXPANDED_BY_DEFAULT|确定默认情况下是否展开展开区域。|
|TDF_VERIFICATION_FLAG_CHECKED|指示当前已选中 "验证" 复选框。|
|TDF_SHOW_PROGRESS_BAR|将配置`CTaskDialog`为显示进度栏。|
|TDF_SHOW_MARQUEE_PROGRESS_BAR|将进度栏配置为天棚式进度栏。 如果启用此选项, 则必须将 TDF_SHOW_PROGRESS_BAR 设置为具有预期的行为。|
|TDF_CALLBACK_TIMER|`CTaskDialog`指示回拨时间间隔设置为大约200毫秒。|
|TDF_POSITION_RELATIVE_TO_WINDOW|将配置`CTaskDialog`为相对于父窗口居中。 如果未启用此标志, `CTaskDialog`则相对于监视器居中。|
|TDF_RTL_LAYOUT|将配置`CTaskDialog`为从右到左的读取布局。|
|TDF_NO_DEFAULT_RADIO_BUTTON|指示当`CTaskDialog`显示时, 不选择任何单选按钮。|
|TDF_CAN_BE_MINIMIZED|允许用户最小化`CTaskDialog`。 若要支持此选项, `CTaskDialog`则不能是模式的。 MFC 不支持此选项, 因为 MFC 不支持无模式`CTaskDialog`。|

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="setprogressbarmarquee"></a>CTaskDialog:: SetProgressBarMarquee

为配置滚动条`CTaskDialog` , 并将其添加到对话框中。

```
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,
    int nMarqueeSpeed = 0);
```

### <a name="parameters"></a>参数

*bEnabled*<br/>
中若要启用滚动条, 则为 TRUE;若要禁用选框栏并将`CTaskDialog`其从中移除, 则为 FALSE。

*nMarqueeSpeed*<br/>
中一个整数, 指示滚动条的速度。

### <a name="remarks"></a>备注

滚动条显示在`CTaskDialog`类的主文本下方。

使用*nMarqueeSpeed*设置滚动条的速度;值越大, 表示速度越慢。 如果将*nMarqueeSpeed*的值设置为 0, 则会使选框栏在 Windows 的默认速度下移动。

如果*nMarqueeSpeed*小于 0, 此方法将引发异常, 并将 "[确保](diagnostic-services.md#ensure)宏"。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarposition"></a>CTaskDialog:: SetProgressBarPosition

调整进度栏的位置。

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>参数

*nProgressPos*<br/>
中进度栏的位置。

### <a name="remarks"></a>备注

如果*nProgressPos*不在进度栏范围内, 此方法将引发异常, 并将 "[确保](diagnostic-services.md#ensure)宏"。 可以用[CTaskDialog:: SetProgressBarRange](#setprogressbarrange)更改进度栏范围。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarrange"></a>CTaskDialog:: SetProgressBarRange

调整进度栏的范围。

```
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>参数

*nRangeMin*<br/>
中进度栏的下限。

*nRangeMax*<br/>
中进度栏的上限。

### <a name="remarks"></a>备注

进度栏相对于*nRangeMin*和*nRangeMax*的位置。 例如, 如果*nRangeMin*为 50, *nRangeMax*为 100, 则位置为75为进度栏的一半。 使用[CTaskDialog:: SetProgressBarPosition](#setprogressbarposition)设置进度栏的位置。

若要显示进度栏, 必须启用选项 "TDF_SHOW_PROGRESS_BAR", 并且 TDF_SHOW_MARQUEE_PROGRESS_BAR 不能启用。 此方法自动设置 TDF_SHOW_PROGRESS_BAR 并清除 TDF_SHOW_MARQUEE_PROGRESS_BAR。 使用[CTaskDialog:: SetOptions](#setoptions)手动更改[CTaskDialog 类](../../mfc/reference/ctaskdialog-class.md)的此实例的选项。

此方法引发异常, 并在*nRangeMin*不小于*nRangeMax*时[确保](diagnostic-services.md#ensure)宏。 如果已显示并且具有天棚式进度`CTaskDialog`栏, 此方法也会引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setprogressbarstate"></a>CTaskDialog:: SetProgressBarState

设置进度栏的状态, 并将其显示在上`CTaskDialog`。

```
void SetProgressBarState(int nState = PBST_NORMAL);
```

### <a name="parameters"></a>参数

*nState*<br/>
中进度栏的状态。 有关可能的值, 请参阅备注部分。

### <a name="remarks"></a>备注

此方法引发异常, 如果`CTaskDialog`已显示并且具有天棚式进度栏, 则使用[确保](diagnostic-services.md#ensure)宏。

下表列出了*nState*的可能值。 在所有这些情况下, 进度栏将用常规颜色填充, 直到到达指定的停止位置。 此时, 将根据状态更改颜色。

|||
|-|-|
|PBST_NORMAL|填充进度栏后, `CTaskDialog`不会更改栏的颜色。 默认情况下, 常规颜色为绿色。|
|PBST_ERROR|填充进度栏后, `CTaskDialog`会将该条形的颜色更改为错误颜色。 默认情况下, 此值为红色。|
|PBST_PAUSED|填充进度栏后, `CTaskDialog`会将该条形的颜色更改为暂停的颜色。 默认情况下, 此值为黄色。|

可以设置进度栏在[CTaskDialog:: SetProgressBarPosition](#setprogressbarposition)处停止的位置。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

##  <a name="setradiobuttonoptions"></a>CTaskDialog:: SetRadioButtonOptions

启用或禁用单选按钮。

```
void SetRadioButtonOptions(
    int nRadioButtonID,
    BOOL bEnabled);
```

### <a name="parameters"></a>参数

*nRadioButtonID*<br/>
中单选按钮控件的 ID。

*bEnabled*<br/>
中若要启用单选按钮, 则为 TRUE;若要禁用单选按钮, 则为 FALSE。

### <a name="remarks"></a>备注

如果*nRadioButtonID*不是单选按钮的有效 ID, 此方法将引发异常, 并将 "[确保](diagnostic-services.md#ensure)宏"。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

##  <a name="setverificationcheckbox"></a>CTaskDialog:: SetVerificationCheckbox

设置 "验证" 复选框的选中状态。

```
void SetVerificationCheckbox(BOOL bChecked);
```

### <a name="parameters"></a>参数

*bChecked*<br/>
中如果在显示时`CTaskDialog`选中验证复选框, 则为 TRUE;如果为 FALSE, 则在显示时`CTaskDialog` , 将取消选中验证复选框。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="setverificationcheckboxtext"></a>CTaskDialog:: SetVerificationCheckboxText

设置在 "验证" 复选框右侧显示的文本。

```
void SetVerificationCheckboxText(CString& strVerificationText);
```

### <a name="parameters"></a>参数

*strVerificationText*<br/>
中此方法在 "验证" 复选框旁边显示的文本。

### <a name="remarks"></a>备注

如果已显示`CTaskDialog`类的此实例, 则此方法将引发异常, 并显示 "[确保](diagnostic-services.md#ensure)宏"。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

##  <a name="setwindowtitle"></a>CTaskDialog:: SetWindowTitle

设置的标题`CTaskDialog`。

```
void SetWindowTitle(CString& strWindowTitle);
```

### <a name="parameters"></a>参数

*strWindowTitle*<br/>
中的新标题`CTaskDialog`。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

##  <a name="showdialog"></a>CTaskDialog:: ShowDialog

创建并显示`CTaskDialog`。

```
static INT_PTR ShowDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast,
    int nCommonButtons = TDCBF_YES_BUTTON | TDCBF_NO_BUTTON,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));
```

### <a name="parameters"></a>参数

*strContent*<br/>
中要用于的内容`CTaskDialog`的字符串。

*strMainInstruction*<br/>
中的主要说明`CTaskDialog`。

*strTitle*<br/>
中的标题`CTaskDialog`。

*nIDCommandControlsFirst*<br/>
中第一个命令的字符串 ID。

*nIDCommandControlsLast*<br/>
中最后一个命令的字符串 ID。

*nCommonButtons*<br/>
中要添加到`CTaskDialog`中的按钮的掩码。

*nTaskDialogOptions*<br/>
中要用于的`CTaskDialog`选项集。

*strFooter*<br/>
中要用作脚注的字符串。

### <a name="return-value"></a>返回值

与用户所做的选择相对应的整数。

### <a name="remarks"></a>备注

使用此静态方法, 可以创建`CTaskDialog`类的实例, 而无需在代码中显式`CTaskDialog`创建对象。 由于没有`CTaskDialog` `CTaskDialog`对象, 因此如果使用此方法向用户显示, 则不能调用的任何其他方法。 `CTaskDialog`

此方法使用应用程序的资源文件中的数据创建命令按钮控件。 资源文件中的字符串表包含多个具有关联的字符串 Id 的字符串。 此方法为*nIDCommandControlsFirst*和*nCommandControlsLast*之间的字符串表中的每个有效条目添加一个命令按钮控件。 对于这些命令按钮控件, 字符串表中的字符串是控件的标题, 而字符串 ID 是控件的 ID。

有关有效选项的列表, 请参阅[CTaskDialog:: SetOptions](#setoptions) 。

当`CTaskDialog`用户选择通用按钮、命令链接控件或`CTaskDialog`关闭时, 将关闭。 返回值是指示用户如何关闭对话框的标识符。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

##  <a name="taskdialogcallback"></a>CTaskDialog:: TaskDialogCallback

框架将调用此方法以响应各种 Windows 消息。

```
friend:
HRESULT TaskDialogCallback(
    HWND hWnd,
    UINT uNotification,
    WPARAM wParam,
    LPARAM lParam,
    LONG_PTR dwRefData);
```

### <a name="parameters"></a>参数

*hwnd*<br/>
中的`m_hWnd` 结构`CTaskDialog`的句柄。

*uNotification*<br/>
中指定生成的消息的通知代码。

*wParam*<br/>
中有关消息的详细信息。

*lParam*<br/>
中有关消息的详细信息。

*dwRefData*<br/>
中指向回调消息所`CTaskDialog`应用到的对象的指针。

### <a name="return-value"></a>返回值

取决于特定的通知代码。 有关详细信息，请参阅备注部分。

### <a name="remarks"></a>备注

的`TaskDialogCallback`默认实现将处理特定消息, 然后调用[CTaskDialog 类](../../mfc/reference/ctaskdialog-class.md)的相应 On 方法。 例如, 为了响应 TDN_BUTTON_CLICKED 消息, `TaskDialogCallback`调用[CTaskDialog:: OnCommandControlClick](#oncommandcontrolclick)。

*WParam*和*lParam*的值取决于生成的特定消息。 这两个值中的一个或两个值都为空。 下表列出了支持的默认通知以及*wParam*和*lParam*的值的含义。 如果在派生类中重写此方法, 则应为下表中的每条消息实现回调代码。

|通知消息|*wParam*负值|*lParam*负值|
|--------------------------|--------------------|--------------------|
|TDN_CREATED|未使用。|未使用。|
|TDN_NAVIGATED|未使用。|未使用。|
|TDN_BUTTON_CLICKED|命令按钮控件 ID。|未使用。|
|TDN_HYPERLINK_CLICKED|未使用。|一个包含链接的[LPCWSTR](/windows/win32/WinProg/windows-data-types)结构。|
|TDN_TIMER|创建或计时器重置`CTaskDialog`后的时间 (以毫秒为单位)。|未使用。|
|TDN_DESTROYED|未使用。|未使用。|
|TDN_RADIO_BUTTON_CLICKED|单选按钮 ID。|未使用。|
|TDN_DIALOG_CONSTRUCTED|未使用。|未使用。|
|TDN_VERIFICATION_CLICKED|如果选中此复选框, 则为 1; 否则为0。|未使用。|
|TDN_HELP|未使用。|未使用。|
|TDN_EXPANDO_BUTTON_CLICKED|如果扩展区域处于折叠状态, 则为 0;如果显示展开文本, 则为非零值。|未使用。|

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[演练：将 CTaskDialog 添加到应用程序](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)
