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
ms.openlocfilehash: e9aeee31d2952d5362c983934ce85f0332f553fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366638"
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
|[C任务对话：：C任务对话](#ctaskdialog)|构造 `CTaskDialog` 对象。|

### <a name="methods"></a>方法

|||
|-|-|
|[CTask对话：：添加命令控制](#addcommandcontrol)|向 添加命令按钮控件到`CTaskDialog`。|
|[CTask对话：：添加无线按钮](#addradiobutton)|向 添加单选按钮`CTaskDialog`。|
|[CTask对话：：单击命令控制](#clickcommandcontrol)|以编程方式单击命令按钮控件或常用按钮。|
|[CTask对话：：点击收音机按钮](#clickradiobutton)|以编程方式单击单选按钮。|
|[CTask对话：:Do模态](#domodal)|显示`CTaskDialog`。|
|[CTask对话：：获取公共按钮计数](#getcommonbuttoncount)|检索可用公共按钮的数量。|
|[CTask对话：：获取公共按钮标志](#getcommonbuttonflag)|将标准 Windows 按钮转换为与`CTaskDialog`类关联的通用按钮类型。|
|[CTask对话：：获取公共按钮Id](#getcommonbuttonid)|将与`CTaskDialog`类关联的常见按钮类型之一转换为标准 Windows 按钮。|
|[CTask对话：获取选项](#getoptions)|返回此`CTaskDialog`的选项标志。|
|[CTask对话：获取选定的命令控制 ID](#getselectedcommandcontrolid)|返回所选命令按钮控件。|
|[CTask对话：：获取选定的无线电按钮ID](#getselectedradiobuttonid)|返回选定的单选按钮。|
|[CTask对话：：获取验证复选框状态](#getverificationcheckboxstate)|检索验证复选框的状态。|
|[CTask对话：：启用命令控制](#iscommandcontrolenabled)|确定是否启用命令按钮控件或通用按钮。|
|[CTask对话：：启用无线电按钮](#isradiobuttonenabled)|确定是否启用了单选按钮。|
|[CTask对话：：支持](#issupported)|确定运行应用程序的计算机是否支持`CTaskDialog`。|
|[C任务对话：：加载命令控制](#loadcommandcontrols)|使用字符串表中的数据添加命令按钮控件。|
|[CTask对话：：加载无线按钮](#loadradiobuttons)|使用字符串表中的数据添加单选按钮。|
|[CTask对话：：导航到](#navigateto)|将焦点转移到另一`CTaskDialog`个 。|
|[CTask对话：：命令控制单击](#oncommandcontrolclick)|当用户单击命令按钮控件时，框架将调用此方法。|
|[CTask对话：：打开创建](#oncreate)|框架在创建 后调用此方法`CTaskDialog`。|
|[C任务对话：：在销毁](#ondestroy)|框架在销毁 之前立即调用此方法`CTaskDialog`。|
|[CTask对话：：打开按钮点击](#onexpandbuttonclick)|当用户单击扩展按钮时，框架将调用此方法。|
|[CTask对话：：上帮助](#onhelp)|当用户请求帮助时，框架调用此方法。|
|[CTask对话：：在超链接点击](#onhyperlinkclick)|当用户单击超链接时，框架将调用此方法。|
|[CTask对话：：Oninit](#oninit)|初始化 时，`CTaskDialog`框架调用此方法。|
|[CTask对话：：上导航页](#onnavigatepage)|当用户将焦点移动到 上的控件时，框架将调用此方法`CTaskDialog`。|
|[CTask对话：：在电台点击](#onradiobuttonclick)|当用户选择单选按钮控件时，框架将调用此方法。|
|[CTask对话：在计时器上](#ontimer)|当计时器过期时，框架调用此方法。|
|[CTask对话：：打开验证复选框单击](#onverificationcheckboxclick)|当用户单击验证复选框时，框架将调用此方法。|
|[CTask对话：：删除所有命令控制](#removeallcommandcontrols)|从 中删除 的所有命令控件`CTaskDialog`。|
|[CTask对话：：删除所有无线按钮](#removeallradiobuttons)|从 中删除 的所有单选按钮`CTaskDialog`。|
|[CTask对话：：设置命令控制选项](#setcommandcontroloptions)|更新 上的命令按钮控件`CTaskDialog`。|
|[CTask对话：：设置公共按钮选项](#setcommonbuttonoptions)|更新要启用的常见按钮的子集，并要求 UAC 提升。|
|[CTask对话：：设置公共按钮](#setcommonbuttons)|将通用按钮添加到 。 `CTaskDialog`|
|[C任务对话：：设置内容](#setcontent)|更新 的内容`CTaskDialog`。|
|[CTask对话：：设置默认命令控制](#setdefaultcommandcontrol)|指定默认命令按钮控件。|
|[CTask对话：：设置默认的无线电按钮](#setdefaultradiobutton)|指定默认单选按钮。|
|[C任务对话：：设置对话宽度](#setdialogwidth)|调整 的`CTaskDialog`宽度。|
|[C任务对话：：设置扩展区域](#setexpansionarea)|更新 的`CTaskDialog`扩展区域。|
|[CTask对话：：SetFooterIcon](#setfootericon)|更新 的`CTaskDialog`页脚图标。|
|[CTask对话：：设置文本](#setfootertext)|更新 脚上的文本`CTaskDialog`。|
|[CTask对话：：设置主图标](#setmainicon)|更新 的主`CTaskDialog`图标。|
|[CTask对话：：设置主指令](#setmaininstruction)|更新 的主要`CTaskDialog`指令。|
|[C任务对话：：设置选项](#setoptions)|配置 的选项`CTaskDialog`。|
|[CTask对话：：设置进度栏](#setprogressbarmarquee)|为 配置 选`CTaskDialog`框栏并将其添加到对话框中。|
|[C任务对话：：设置进度栏位置](#setprogressbarposition)|调整进度条的位置。|
|[CTask对话：：设置进度栏范围](#setprogressbarrange)|调整进度条的范围。|
|[C任务对话：：设置进度栏](#setprogressbarstate)|设置进度条的状态并将其显示在 上`CTaskDialog`。|
|[CTask对话：：设置无线按钮选项](#setradiobuttonoptions)|启用或禁用单选按钮。|
|[C任务对话：：设置验证复选框](#setverificationcheckbox)|设置验证复选框的选中状态。|
|[CTask对话：：设置验证复选框文本](#setverificationcheckboxtext)|设置验证复选框右侧的文本。|
|[C任务对话：：设置窗口标题](#setwindowtitle)|设置 的标题`CTaskDialog`。|
|[C任务对话：：显示对话](#showdialog)|创建并显示`CTaskDialog`。|
|[C任务对话：：任务对话回调](#taskdialogcallback)|框架调用此以响应各种 Windows 消息。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|`m_aButtons`|命令按钮控件的数组`CTaskDialog`。|
|`m_aRadioButtons`|的单选按钮控件的数组`CTaskDialog`。|
|`m_bVerified`|`TRUE`指示已选中验证复选框;`FALSE`表示它不是。|
|`m_footerIcon`|中脚的图标`CTaskDialog`。|
|`m_hWnd`|窗口的句柄`CTaskDialog`。|
|`m_mainIcon`|的主图标`CTaskDialog`。|
|`m_nButtonDisabled`|指示禁用哪些常见按钮的蒙版。|
|`m_nButtonElevation`|指示哪些常见按钮需要 UAC 提升的蒙版。|
|`m_nButtonId`|所选命令按钮控件的 ID。|
|`m_nCommonButton`|指示 在 上显示哪些常见按钮的`CTaskDialog`蒙版。|
|`m_nDefaultCommandControl`|显示 时选择的命令按钮控件`CTaskDialog`的 ID。|
|`m_nDefaultRadioButton`|显示 时选择的单选按钮控件`CTaskDialog`的 ID。|
|`m_nFlags`|指示 的选项的`CTaskDialog`蒙版。|
|`m_nProgressPos`|进度条的当前位置。  该值必须介于 `m_nProgressRangeMin` 和 `m_nProgressRangeMax` 之间。|
|`m_nProgressRangeMax`|进度条的最大值。|
|`m_nProgressRangeMin`|进度条的最小值。|
|`m_nProgressState`|进度条的状态。 有关详细信息，请参阅[CTaskDialog：设置进度栏](#setprogressbarstate)。|
|`m_nRadioId`|所选单选按钮控件的 ID。|
|`m_nWidth`|`CTaskDialog` 的宽度（以像素为单位）。|
|`m_strCollapse`|隐藏展开信息`CTaskDialog`时，将显示的字符串显示在扩展框的右侧。|
|`m_strContent`|的内容字符串`CTaskDialog`。|
|`m_strExpand`|显示展开信息`CTaskDialog`时，在扩展框右侧显示的字符串。|
|`m_strFooter`|页脚`CTaskDialog`。|
|`m_strInformation`|的扩展信息`CTaskDialog`。|
|`m_strMainInstruction`|的主要指令`CTaskDialog`。|
|`m_strTitle`|`CTaskDialog` 的标题。|
|`m_strVerification`|在验证复选框右侧`CTaskDialog`显示的字符串。|

## <a name="remarks"></a>备注

该`CTaskDialog`类替换标准 Windows 消息框，并具有其他功能，如从用户收集信息的新控件。 此类位于 Visual Studio 2010 及更高版本中的 MFC 库中。 从`CTaskDialog`Windows Vista 开始，提供 。 早期版本的 Windows 无法显示`CTaskDialog`该对象。 用于`CTaskDialog::IsSupported`确定当前用户是否可以显示任务对话框。 仍然支持标准 Windows 消息框。

仅当`CTaskDialog`使用 Unicode 库生成应用程序时，才可用。

有`CTaskDialog`两个不同的构造函数。 一个构造函数允许您指定两个命令按钮和最多六个常规按钮控件。 创建 后可以添加更多命令按钮`CTaskDialog`。 第二个构造函数不支持任何命令按钮，但您可以添加无限数量的常规按钮控件。 有关构造函数的详细信息，请参阅[CTaskDialog：：CTaskDialog](#ctaskdialog)。

下图显示了一个示例`CTaskDialog`，用于说明某些控件的位置。

![CTaskDialog 示例](../../mfc/reference/media/ctaskdialogsample.png "CTaskDialog 示例") <br/>
C任务对话示例

## <a name="requirements"></a>要求

**最低要求操作系统：** 视窗Vista

**标题：** afxtaskdialog.h

## <a name="ctaskdialogaddcommandcontrol"></a><a name="addcommandcontrol"></a>CTask对话：：添加命令控制

向 添加新的命令按钮控件。 `CTaskDialog`

```
void AddCommandControl(
    int nCommandControlID,
    const CString& strCaption,
    BOOL bEnabled = TRUE,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>参数

*n命令控制ID*<br/>
[在]命令控制标识号。

*串标题*<br/>
[在]向用户显示的`CTaskDialog`字符串。 使用此字符串来解释命令的用途。

*b 启用*<br/>
[在]指示新按钮是启用还是禁用的布尔参数。

*b 要求提升*<br/>
[在]指示命令是否需要高程的布尔参数。

### <a name="remarks"></a>备注

`CTaskDialog Class`可以显示无限数量的命令按钮控件。 但是，如果`CTaskDialog`显示任何命令按钮控件，它最多可以显示六个按钮。 `CTaskDialog`如果没有命令按钮控件，它可以显示无限数量的按钮。

当用户选择命令按钮控件时，将关闭`CTaskDialog`。 如果应用程序使用[CTaskDialog：:DoModal](#domodal)显示对话框，`DoModal`则返回所选命令按钮控件的*nCommandControlID。*

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogaddradiobutton"></a><a name="addradiobutton"></a>CTask对话：：添加无线按钮

向 添加单选按钮`CTaskDialog`。

```
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,
    const CString& strCaption,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>参数

*nRadioButtonID*<br/>
[在]单选按钮的标识号。

*串标题*<br/>
[在]在单选按钮`CTaskDialog`旁边显示的字符串。

*b 启用*<br/>
[在]指示是否启用单选按钮的布尔参数。

### <a name="remarks"></a>备注

[CTaskDialog 类](../../mfc/reference/ctaskdialog-class.md)的单选按钮使您能够从用户那里收集信息。 使用函数[CTaskDialog：获取选择无线电按钮ID](#getselectedradiobuttonid)来确定选择了哪个单选按钮。

不`CTaskDialog`要求*nRadioButtonID*参数对于每个单选按钮是唯一的。 但是，如果不为每个单选按钮使用不同的标识符，则可能会遇到意外行为。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogclickcommandcontrol"></a><a name="clickcommandcontrol"></a>CTask对话：：单击命令控制

以编程方式单击命令按钮控件或常用按钮。

```
protected:
void ClickCommandControl(int nCommandControlID) const;
```

### <a name="parameters"></a>参数

*n命令控制ID*<br/>
[在]要单击的控件的命令 ID。

### <a name="remarks"></a>备注

此方法生成窗口消息TDM_CLICK_BUTTON。

## <a name="ctaskdialogclickradiobutton"></a><a name="clickradiobutton"></a>CTask对话：：点击收音机按钮

以编程方式单击单选按钮。

```
protected:
void ClickRadioButton(int nRadioButtonID) const;
```

### <a name="parameters"></a>参数

*nRadioButtonID*<br/>
[在]要单击的单选按钮的 ID。

### <a name="remarks"></a>备注

此方法生成窗口消息TDM_CLICK_RADIO_BUTTON。

## <a name="ctaskdialogctaskdialog"></a><a name="ctaskdialog"></a>C任务对话：：C任务对话

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

*str内容*<br/>
[在]用于 的内容`CTaskDialog`的字符串。

*斯特曼指令*<br/>
[在]的主要指令`CTaskDialog`。

*斯特标题*<br/>
[在]的标题`CTaskDialog`。

*n 通用按钮*<br/>
[在]要添加到 的常用按钮的掩码`CTaskDialog`。

*n任务对话选项*<br/>
[在]用于 的选项`CTaskDialog`集。

*斯特福特*<br/>
[在]要用作页脚的字符串。

*nID命令控制优先*<br/>
[在]第一个命令的字符串 ID。

*nID命令控制上次*<br/>
[在]最后一个命令的字符串 ID。

### <a name="remarks"></a>备注

有两种方法可以向应用程序添加 。 `CTaskDialog` 第一种方法是使用其中一个构造函数创建 ，`CTaskDialog`并使用[CTaskDialog：:DoModal](#domodal)显示它。 第二种方法是使用静态函数[CTaskDialog：：showDialog](#showdialog)，它使您能够在不显式创建`CTaskDialog``CTaskDialog`对象的情况下显示 。

第二个构造函数使用来自应用程序的资源文件的数据创建命令按钮控件。 资源文件中的字符串表具有多个字符串与关联的字符串指示。 此方法为*nIDCommandControlsFirst*和*nCommandControlsLast*之间的字符串表中的每个有效条目添加命令按钮控件，包括。 对于这些命令按钮控件，字符串表中的字符串是控件的标题，字符串 ID 是控件的 ID。

有关有效选项的列表，请参阅[CTaskDialog：设置选项](#setoptions)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogdomodal"></a><a name="domodal"></a>CTask对话：:Do模态

显示`CTaskDialog`和 使其模态。

```
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```

### <a name="parameters"></a>参数

*h 家长*<br/>
[在]的`CTaskDialog`父窗口。

### <a name="return-value"></a>返回值

与用户所做的选择对应的整数。

### <a name="remarks"></a>备注

显示[CTaskDialog](../../mfc/reference/ctaskdialog-class.md)的此实例。 然后，应用程序等待用户关闭对话框。

当用户`CTaskDialog`选择公共按钮、命令链接控件或关闭 时`CTaskDialog`关闭 。 返回值是指示用户如何关闭对话框的标识符。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetcommonbuttoncount"></a><a name="getcommonbuttoncount"></a>CTask对话：：获取公共按钮计数

检索常用按钮的数量。

```
int GetCommonButtonCount() const;
```

### <a name="return-value"></a>返回值

可用的常用按钮数。

### <a name="remarks"></a>备注

常见按钮是提供给[CTaskDialog：：CTaskDialog](#ctaskdialog)的默认按钮。 [CTaskDialog 类](../../mfc/reference/ctaskdialog-class.md)显示对话框底部的按钮。

枚举的按钮列表在 CommCtrl.h 中提供。

## <a name="ctaskdialoggetcommonbuttonflag"></a><a name="getcommonbuttonflag"></a>CTask对话：：获取公共按钮标志

将标准 Windows 按钮转换为与[CTaskDialog 类](../../mfc/reference/ctaskdialog-class.md)关联的常见按钮类型。

```
int GetCommonButtonFlag(int nButtonId) const;
```

### <a name="parameters"></a>参数

*nButtonId*<br/>
[在]标准 Windows 按钮值。

### <a name="return-value"></a>返回值

相应的`CTaskDialog`公用按钮的值。 如果没有相应的通用按钮，此方法返回 0。

## <a name="ctaskdialoggetcommonbuttonid"></a><a name="getcommonbuttonid"></a>CTask对话：：获取公共按钮Id

将与[CTaskDialog 类](../../mfc/reference/ctaskdialog-class.md)关联的常见按钮类型之一转换为标准 Windows 按钮。

```
int GetCommonButtonId(int nFlag);
```

### <a name="parameters"></a>参数

*nFlag*<br/>
[在]与`CTaskDialog`类关联的通用按钮类型。

### <a name="return-value"></a>返回值

相应的标准 Windows 按钮的值。 如果没有相应的 Windows 按钮，该方法将返回 0。

## <a name="ctaskdialoggetoptions"></a><a name="getoptions"></a>CTask对话：获取选项

返回此`CTaskDialog`的选项标志。

```
int GetOptions() const;
```

### <a name="return-value"></a>返回值

中区的标志`CTaskDialog`。

### <a name="remarks"></a>备注

有关[CTaskDialog 类](../../mfc/reference/ctaskdialog-class.md)可用的选项的详细信息，请参阅[CTaskDialog：：setOptions](#setoptions)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetselectedcommandcontrolid"></a><a name="getselectedcommandcontrolid"></a>CTask对话：获取选定的命令控制 ID

返回所选命令按钮控件。

```
int GetSelectedCommandControlID() const;
```

### <a name="return-value"></a>返回值

当前选定的命令按钮控件的 ID。

### <a name="remarks"></a>备注

不必使用此方法检索用户选择的命令按钮的 ID。 该 ID 由[CTaskDialog：:Do 模式或](#domodal) [CTaskDialog：：显示对话](#showdialog)返回。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialoggetselectedradiobuttonid"></a><a name="getselectedradiobuttonid"></a>CTask对话：：获取选定的无线电按钮ID

返回选定的单选按钮。

```
int GetSelectedRadioButtonID() const;
```

### <a name="return-value"></a>返回值

所选单选按钮的 ID。

### <a name="remarks"></a>备注

用户可以在用户关闭对话框后使用此方法来检索选定的单选按钮。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialoggetverificationcheckboxstate"></a><a name="getverificationcheckboxstate"></a>CTask对话：：获取验证复选框状态

检索验证复选框的状态。

```
BOOL GetVerificationCheckboxState() const;
```

### <a name="return-value"></a>返回值

如果选中该复选框，则为 TRUE，如果没有，则 FALSE。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogiscommandcontrolenabled"></a><a name="iscommandcontrolenabled"></a>CTask对话：：启用命令控制

确定是否启用命令按钮控件或按钮。

```
BOOL IsCommandControlEnabled(int nCommandControlID) const;
```

### <a name="parameters"></a>参数

*n命令控制ID*<br/>
[在]要测试的命令按钮控件或按钮的 ID。

### <a name="return-value"></a>返回值

如果启用了控件，则为 TRUE，如果未启用，则为 FALSE。

### <a name="remarks"></a>备注

可以使用此方法确定命令按钮控件和`CTaskDialog`Class* 的常见按钮的可用性。

如果*nCommandControlID*不是常见`CTaskDialog`按钮或命令按钮控件的有效标识符，则此方法将引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogisradiobuttonenabled"></a><a name="isradiobuttonenabled"></a>CTask对话：：启用无线电按钮

确定是否启用了单选按钮。

```
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;
```

### <a name="parameters"></a>参数

*nRadioButtonID*<br/>
[在]要测试的单选按钮的 ID。

### <a name="return-value"></a>返回值

如果启用了单选按钮，则为 TRUE，如果没有，则 FALSE。

### <a name="remarks"></a>备注

如果*nRadioButtonID*不是单选按钮的有效标识符，则此方法将引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogissupported"></a><a name="issupported"></a>CTask对话：：支持

确定运行应用程序的计算机是否支持`CTaskDialog`。

```
static BOOL IsSupported();
```

### <a name="return-value"></a>返回值

如果计算机支持，`CTaskDialog`则为 TRUE。否则。

### <a name="remarks"></a>备注

使用此函数在运行时确定运行应用程序的计算机是否支持该`CTaskDialog`类。 如果计算机不支持 ，`CTaskDialog`应提供另一种方法将信息传达给用户。 如果应用程序尝试在不支持该`CTaskDialog``CTaskDialog`类的计算机上使用 ， 则应用程序将崩溃。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogloadcommandcontrols"></a><a name="loadcommandcontrols"></a>C任务对话：：加载命令控制

使用字符串表中的数据添加命令按钮控件。

```
void LoadCommandControls(
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast);
```

### <a name="parameters"></a>参数

*nID命令控制优先*<br/>
[在]第一个命令的字符串 ID。

*nID命令控制上次*<br/>
[在]最后一个命令的字符串 ID。

### <a name="remarks"></a>备注

此方法通过使用来自应用程序的资源文件的数据创建命令按钮控件。 资源文件中的字符串表具有多个字符串与关联的字符串指示。 使用此方法添加的新命令按钮控件使用字符串作为控件的标题和控件 ID 的字符串 ID。 所选字符串的范围由*nIDCommandControlsFirst*和*nCommandControlsLast*提供，包括。 如果区域中有空条目，则 该方法不会为该条目添加命令按钮控件。

默认情况下，启用新的命令按钮控件，不需要提升。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogloadradiobuttons"></a><a name="loadradiobuttons"></a>CTask对话：：加载无线按钮

使用字符串表中的数据添加单选按钮控件。

```
void LoadRadioButtons(
    int nIDRadioButtonsFirst,
    int nIDRadioButtonsLast);
```

### <a name="parameters"></a>参数

*nIDRadioButtons首先*<br/>
[在]第一个单选按钮的字符串 ID。

*nIDRadioButtonSLast*<br/>
[在]最后一个单选按钮的字符串 ID。

### <a name="remarks"></a>备注

此方法使用应用程序的资源文件中的数据创建单选按钮。 资源文件中的字符串表具有多个字符串与关联的字符串指示。 使用此方法添加的新单选按钮使用单选按钮的字幕字符串和单选按钮 ID 的字符串 ID。 所选字符串的范围由*nIDRadioButtonsFirst*和*nRadioButtonSLast*提供，包括。 如果范围内有空条目，则 该方法不会为该条目添加单选按钮。

默认情况下，启用新的单选按钮。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialognavigateto"></a><a name="navigateto"></a>CTask对话：：导航到

将焦点转移到另一`CTaskDialog`个 。

```
protected:
void NavigateTo(CTaskDialog& oTaskDialog) const;
```

### <a name="parameters"></a>参数

*o任务对话*<br/>
[在]接收`CTaskDialog`焦点的 。

### <a name="remarks"></a>备注

此方法在显示`CTaskDialog`*oTaskDialog*时隐藏电流。 *oTaskDialog*与 当前`CTaskDialog`的位置相同。

## <a name="ctaskdialogoncommandcontrolclick"></a><a name="oncommandcontrolclick"></a>CTask对话：：命令控制单击

当用户单击命令按钮控件时，框架将调用此方法。

```
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```

### <a name="parameters"></a>参数

*n命令控制ID*<br/>
[在]用户选择的命令按钮控件的 ID。

### <a name="return-value"></a>返回值

默认实现返回S_OK。

### <a name="remarks"></a>备注

重写派生类中的此方法以实现自定义行为。

## <a name="ctaskdialogoncreate"></a><a name="oncreate"></a>CTask对话：：打开创建

框架在创建 后调用此方法`CTaskDialog`。

```
virtual HRESULT OnCreate();
```

### <a name="return-value"></a>返回值

默认实现返回S_OK。

### <a name="remarks"></a>备注

重写派生类中的此方法以实现自定义行为。

## <a name="ctaskdialogondestroy"></a><a name="ondestroy"></a>C任务对话：：在销毁

框架在销毁 之前立即调用此方法`CTaskDialog`。

```
virtual HRESULT OnDestroy();
```

### <a name="return-value"></a>返回值

默认实现返回S_OK。

### <a name="remarks"></a>备注

重写派生类中的此方法以实现自定义行为。

## <a name="ctaskdialogonexpandbuttonclick"></a><a name="onexpandbuttonclick"></a>CTask对话：：打开按钮点击

当用户单击扩展按钮时，框架将调用此方法。

```
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```

### <a name="parameters"></a>参数

*b 扩展*<br/>
[在]非零值表示显示额外信息;使用 "非零"值，表示显示额外信息。0 表示附加信息已隐藏。

### <a name="return-value"></a>返回值

默认实现返回S_OK。

### <a name="remarks"></a>备注

重写派生类中的此方法以实现自定义行为。

## <a name="ctaskdialogonhelp"></a><a name="onhelp"></a>CTask对话：：上帮助

当用户请求帮助时，框架调用此方法。

```
virtual HRESULT OnHelp();
```

### <a name="return-value"></a>返回值

默认实现返回S_OK。

### <a name="remarks"></a>备注

重写派生类中的此方法以实现自定义行为。

## <a name="ctaskdialogonhyperlinkclick"></a><a name="onhyperlinkclick"></a>CTask对话：：在超链接点击

当用户单击超链接时，框架将调用此方法。

```
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```

### <a name="parameters"></a>参数

*斯特雷赫*<br/>
[在]表示超链接的字符串。

### <a name="return-value"></a>返回值

默认实现返回S_OK。

### <a name="remarks"></a>备注

此方法在返回S_OK之前调用[ShellExecute。](/windows/win32/api/shellapi/nf-shellapi-shellexecutew)

重写派生类中的此方法以实现自定义行为。

## <a name="ctaskdialogoninit"></a><a name="oninit"></a>CTask对话：：Oninit

初始化 时，`CTaskDialog`框架调用此方法。

```
virtual HRESULT OnInit();
```

### <a name="return-value"></a>返回值

默认实现返回S_OK。

### <a name="remarks"></a>备注

重写派生类中的此方法以实现自定义行为。

## <a name="ctaskdialogonnavigatepage"></a><a name="onnavigatepage"></a>CTask对话：：上导航页

框架调用此方法以响应[CTaskDialog：：Navigateto](#navigateto)方法。

```
virtual HRESULT OnNavigatePage();
```

### <a name="return-value"></a>返回值

默认实现返回S_OK。

### <a name="remarks"></a>备注

重写派生类中的此方法以实现自定义行为。

## <a name="ctaskdialogonradiobuttonclick"></a><a name="onradiobuttonclick"></a>CTask对话：：在电台点击

当用户选择单选按钮控件时，框架将调用此方法。

```
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```

### <a name="parameters"></a>参数

*nRadioButtonID*<br/>
[在]用户单击的单选按钮控件的 ID。

### <a name="return-value"></a>返回值

默认实现返回S_OK。

### <a name="remarks"></a>备注

重写派生类中的此方法以实现自定义行为。

## <a name="ctaskdialogontimer"></a><a name="ontimer"></a>CTask对话：在计时器上

当计时器过期时，框架调用此方法。

```
virtual HRESULT OnTimer(long lTime);
```

### <a name="parameters"></a>参数

*lTime*<br/>
[在]创建 或重置计时器以来`CTaskDialog`的时间（以毫秒为单位）。

### <a name="return-value"></a>返回值

默认实现返回S_OK。

### <a name="remarks"></a>备注

重写派生类中的此方法以实现自定义行为。

## <a name="ctaskdialogonverificationcheckboxclick"></a><a name="onverificationcheckboxclick"></a>CTask对话：：打开验证复选框单击

当用户单击验证复选框时，框架将调用此方法。

```
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```

### <a name="parameters"></a>参数

*bChecked*<br/>
[在]TRUE 表示选择了验证复选框;FALSE 表示它不是。

### <a name="return-value"></a>返回值

默认实现返回S_OK。

### <a name="remarks"></a>备注

重写派生类中的此方法以实现自定义行为。

## <a name="ctaskdialogremoveallcommandcontrols"></a><a name="removeallcommandcontrols"></a>CTask对话：：删除所有命令控制

从 中删除 的所有命令按钮控件`CTaskDialog`。

```
void RemoveAllCommandControls();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogremoveallradiobuttons"></a><a name="removeallradiobuttons"></a>CTask对话：：删除所有无线按钮

从 中删除 的所有单选按钮`CTaskDialog`。

```
void RemoveAllRadioButtons();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetcommandcontroloptions"></a><a name="setcommandcontroloptions"></a>CTask对话：：设置命令控制选项

更新 上的命令按钮控件`CTaskDialog`。

```
void SetCommandControlOptions(
    int nCommandControlID,
    BOOL bEnabled,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>参数

*n命令控制ID*<br/>
[在]要更新的命令控件的 ID。

*b 启用*<br/>
[在]布尔参数，指示指定的命令按钮控件是启用还是禁用。

*b 要求提升*<br/>
[在]布尔参数，指示指定的命令按钮控件是否需要高程。

### <a name="remarks"></a>备注

使用此方法可以更改命令按钮控件是否已启用或在添加到`CTaskDialog`类后是否需要提升。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetcommonbuttonoptions"></a><a name="setcommonbuttonoptions"></a>CTask对话：：设置公共按钮选项

更新要启用的常用按钮的子集，并要求 UAC 提升。

```
void SetCommonButtonOptions(
    int nDisabledButtonMask,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>参数

*n 禁用按钮蒙版*<br/>
[在]要禁用的常见按钮的掩码。

*n 海拔按钮蒙版*<br/>
[在]需要高程的常见按钮的蒙版。

### <a name="remarks"></a>备注

可以使用构造函数[CTaskDialog：：CTaskDialog](#ctaskdialog)和方法[CTaskDialog：：setCommonButton，](#setcommonbuttons)设置[CTaskDialog 类](../../mfc/reference/ctaskdialog-class.md)实例可用的通用按钮。 `CTaskDialog::SetCommonButtonOptions`不支持添加新的通用按钮。

如果使用此方法禁用或提升对此不可用的通用按钮`CTaskDialog`，则此方法通过使用["确保"](diagnostic-services.md#ensure)宏引发异常。

此方法启用任何可用于`CTaskDialog`但不在 n*残疾人按钮掩码中的*按钮，即使它以前已禁用也是如此。 此方法以类似的方式对待高程：如果通用按钮可用但不包括在*nElevationButton 掩码*中，则将通用按钮记录为不需要高程。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcommonbuttons"></a><a name="setcommonbuttons"></a>CTask对话：：设置公共按钮

将通用按钮添加到 。 `CTaskDialog`

```
void SetCommonButtons(
    int nButtonMask,
    int nDisabledButtonMask = 0,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>参数

*nButton 掩码*<br/>
[在]要添加到 的`CTaskDialog`按钮的掩码。

*n 禁用按钮蒙版*<br/>
[在]要禁用的按钮的掩码。

*n 海拔按钮蒙版*<br/>
[在]需要高程的按钮的蒙版。

### <a name="remarks"></a>备注

创建类的此实例的显示窗口后，`CTaskDialog`不能调用此方法。 如果这样做，此方法将引发异常。

*nButtonMask*指示的按钮将覆盖以前添加到 的任何`CTaskDialog`常见按钮。 只有*nButton Mask*中指示的按钮可用。

如果*n 禁用 Button Mask*或*nElevationButton Mask*包含的按钮不在*nButton Mask*中，则此方法通过使用["确保"](diagnostic-services.md#ensure)宏引发异常。

默认情况下，所有常见按钮都已启用，不需要提升。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcontent"></a><a name="setcontent"></a>C任务对话：：设置内容

更新 的内容`CTaskDialog`。

```
void SetContent(const CString& strContent);
```

### <a name="parameters"></a>参数

*str内容*<br/>
[在]要向用户显示的字符串。

### <a name="remarks"></a>备注

`CTaskDialog`类的内容是在对话框的主部分向用户显示的文本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetdefaultcommandcontrol"></a><a name="setdefaultcommandcontrol"></a>CTask对话：：设置默认命令控制

指定默认命令按钮控件。

```
void SetDefaultCommandControl(int nCommandControlID);
```

### <a name="parameters"></a>参数

*n命令控制ID*<br/>
[在]命令按钮控件的 ID 为默认值。

### <a name="remarks"></a>备注

默认命令按钮控件是首次向用户显示 时`CTaskDialog`选择的控件。

如果找不到*nCommandControlID*指定的命令按钮控件，此方法将引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetdefaultradiobutton"></a><a name="setdefaultradiobutton"></a>CTask对话：：设置默认的无线电按钮

指定默认单选按钮。

```
void SetDefaultRadioButton(int nRadioButtonID);
```

### <a name="parameters"></a>参数

*nRadioButtonID*<br/>
[在]作为默认值的单选按钮的 ID。

### <a name="remarks"></a>备注

默认单选按钮是首次向用户显示 时`CTaskDialog`选择的按钮。

如果找不到*nRadioButtonID*指定的单选按钮，此方法将引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetdialogwidth"></a><a name="setdialogwidth"></a>C任务对话：：设置对话宽度

调整 的`CTaskDialog`宽度。

```
void SetDialogWidth(int nWidth = 0);
```

### <a name="parameters"></a>参数

*n 宽度*<br/>
[在]对话框的宽度（以像素为单位）。

### <a name="remarks"></a>备注

参数*nWidth*必须大于或等于 0。 否则，此方法将引发异常。

如果*nWidth*设置为 0，则此方法将对话框设置为默认大小。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetexpansionarea"></a><a name="setexpansionarea"></a>C任务对话：：设置扩展区域

更新 的`CTaskDialog`扩展区域。

```
void SetExpansionArea(
    const CString& strExpandedInformation,
    const CString& strCollapsedLabel = _T(""),
    const CString& strExpandedLabel = _T(""));
```

### <a name="parameters"></a>参数

*放大缩小字体功能 放大缩小字体功能*<br/>
[在]当用户单击扩展按钮`CTaskDialog`时，对话框正文中显示的字符串。

*str 折叠标签*<br/>
[在]扩展区域折叠时`CTaskDialog`显示在扩展按钮旁边的字符串。

*str 扩展标签*<br/>
[在]显示展开区域时`CTaskDialog`，在扩展按钮旁边显示的字符串。

### <a name="remarks"></a>备注

类的`CTaskDialog`扩展区域使您能够向用户提供其他信息。 扩展区域位于 的`CTaskDialog`，位于标题和内容字符串的正下方。

首次显示`CTaskDialog`时，它不显示展开的信息，并放在`strCollapsedLabel`扩展按钮旁边。 当用户单击扩展按钮时，`CTaskDialog`将显示*str"扩展信息*"并将标签更改为*str"扩展标签*"。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootericon"></a><a name="setfootericon"></a>CTask对话：：SetFooterIcon

更新 页`CTaskDialog`脚图标。

```
void SetFooterIcon(HICON hFooterIcon);
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```

### <a name="parameters"></a>参数

*hFooterIcon*<br/>
[在]的新图标`CTaskDialog`。

*lpszFooterIcon*<br/>
[在]的新图标`CTaskDialog`。

### <a name="remarks"></a>备注

页脚图标显示在[CTaskDialog 类](../../mfc/reference/ctaskdialog-class.md)的底部。 它可以具有关联的页脚文本。 您可以使用[CTaskDialog 更改页脚文本：setFooterText](#setfootertext)。

如果显示 或输入参数为 NULL，`CTaskDialog`则此方法会向["确保"](diagnostic-services.md#ensure)宏引发异常。

只能`CTaskDialog`接受`HICON`或`LPCWSTR`作为页脚图标。 这是通过在构造函数或 CTaskDialog 中设置选项[TDF_USE_HICON_FOOTER：：setOption](#setoptions)进行配置的。 默认情况下，`CTaskDialog`配置为用作`LPCWSTR`页脚图标的输入类型。 如果尝试使用不适当的类型设置图标，此方法将生成异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootertext"></a><a name="setfootertext"></a>CTask对话：：设置文本

更新 脚上的文本`CTaskDialog`。

```
void SetFooterText(const CString& strFooterText);
```

### <a name="parameters"></a>参数

*斯特福特文本*<br/>
[在]页脚的新文本。

### <a name="remarks"></a>备注

页脚图标显示在 的页脚文本旁边`CTaskDialog`。 您可以使用[CTaskDialog 更改页脚图标：：SetFooterIcon](#setfootericon)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmainicon"></a><a name="setmainicon"></a>CTask对话：：设置主图标

更新 的主`CTaskDialog`图标。

```
void SetMainIcon(HICON hMainIcon);
void SetMainIcon(LPCWSTR lpszMainIcon);
```

### <a name="parameters"></a>参数

*hMainIcon*<br/>
[在]新图标。

*lpszMainIcon*<br/>
[在]新图标。

### <a name="remarks"></a>备注

如果显示 或输入参数为 NULL，`CTaskDialog`则此方法会向["确保"](diagnostic-services.md#ensure)宏引发异常。

只能`CTaskDialog`接受 或`HICON``LPCWSTR`作为主图标。 您可以通过在构造函数中或[CTaskDialog：setOption](#setoptions)方法中设置TDF_USE_HICON_MAIN选项来配置此选项。 默认情况下，`CTaskDialog`配置为用作`LPCWSTR`主图标的输入类型。 如果尝试使用不适当的类型设置图标，此方法将生成异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmaininstruction"></a><a name="setmaininstruction"></a>CTask对话：：设置主指令

更新 的主要`CTaskDialog`指令。

```
void SetMainInstruction(const CString& strInstructions);
```

### <a name="parameters"></a>参数

*串指令*<br/>
[在]新的主指令。

### <a name="remarks"></a>备注

`CTaskDialog`类的主要指令是以大粗体显示给用户的文本。 它位于标题栏下方的对话框中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetoptions"></a><a name="setoptions"></a>C任务对话：：设置选项

配置 的选项`CTaskDialog`。

```
void SetOptions(int nOptionFlag);
```

### <a name="parameters"></a>参数

*nOptionFlag*<br/>
[在]用于 的标记集`CTaskDialog`。

### <a name="remarks"></a>备注

此方法清除 的所有当前选项`CTaskDialog`。 若要保留当前选项，必须先使用[CTaskDialog：：GetOptions](#getoptions)检索它们，并将它们与要设置的选项合并。

下表列出了所有有效的选项。

|||
|-|-|
|TDF_ENABLE_HYPERLINKS|启用 中的`CTaskDialog`超链接。|
|TDF_USE_HICON_MAIN|将 配置为`CTaskDialog`对主`HICON`图标使用 。 另一种方法是使用`LPCWSTR`。|
|TDF_USE_HICON_FOOTER|将 配置为`CTaskDialog`使用 页`HICON`脚图标 的 。 另一种方法是使用`LPCWSTR`。|
|TDF_ALLOW_DIALOG_CANCELLATION|允许用户`CTaskDialog`使用键盘或使用对话框右上角的图标关闭 ，即使未启用 **"取消"** 按钮也是如此。 如果未设置此标志，并且未启用 **"取消"** 按钮，则用户无法使用 Alt_F4、Escape 键或标题栏的关闭按钮关闭对话框。|
|TDF_USE_COMMAND_LINKS|配置 要`CTaskDialog`使用的命令按钮控件。|
|TDF_USE_COMMAND_LINKS_NO_ICON|配置`CTaskDialog`要使用的命令按钮控件，而不显示控件旁边的图标。 TDF_USE_COMMAND_LINKS覆盖TDF_USE_COMMAND_LINKS_NO_ICON。|
|TDF_EXPAND_FOOTER_AREA|指示扩展区域当前已展开。|
|TDF_EXPANDED_BY_DEFAULT|确定默认情况下是否扩展扩展区域。|
|TDF_VERIFICATION_FLAG_CHECKED|指示当前已选择验证复选框。|
|TDF_SHOW_PROGRESS_BAR|配置为`CTaskDialog`显示进度条。|
|TDF_SHOW_MARQUEE_PROGRESS_BAR|将进度栏配置为选框进度条。 如果启用此选项，则必须将TDF_SHOW_PROGRESS_BAR设置为具有预期行为。|
|TDF_CALLBACK_TIMER|指示`CTaskDialog`回调间隔设置为大约 200 毫秒。|
|TDF_POSITION_RELATIVE_TO_WINDOW|配置`CTaskDialog`相对于父窗口要居中。 如果未启用此标志，则`CTaskDialog`相对于监视器，居中。|
|TDF_RTL_LAYOUT|配置`CTaskDialog`从右到左读取布局的 。|
|TDF_NO_DEFAULT_RADIO_BUTTON|指示`CTaskDialog`出现时未选择单选按钮。|
|TDF_CAN_BE_MINIMIZED|使用户能够最小化 。 `CTaskDialog` 要支持此选项，`CTaskDialog`不能是模态的。 MFC 不支持此选项，因为 MFC 不支持无`CTaskDialog`模式 。|

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetprogressbarmarquee"></a><a name="setprogressbarmarquee"></a>CTask对话：：设置进度栏

为 配置 选`CTaskDialog`框栏并将其添加到对话框中。

```
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,
    int nMarqueeSpeed = 0);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]TRUE 启用选取框栏;FALSE 以禁用选取框栏并从 中删除`CTaskDialog`它。

*nMarqueeSpeed*<br/>
[在]指示选框条速度的整数。

### <a name="remarks"></a>备注

选框栏显示在`CTaskDialog`类的主文本下方。

使用*nMarqueeSpeed*设置选框栏的速度;值越大表示速度较慢。 *nMarqueeSpeed*的值为 0 使选取框条以 Windows 的默认速度移动。

如果*nMarqueeSpeed*小于 0，此方法会向["确保"](diagnostic-services.md#ensure)宏引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarposition"></a><a name="setprogressbarposition"></a>C任务对话：：设置进度栏位置

调整进度条的位置。

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>参数

*n 进步Pos*<br/>
[在]进度条的位置。

### <a name="remarks"></a>备注

如果*nProgressPos*不在进度栏范围内，则此方法会向["确保"](diagnostic-services.md#ensure)宏引发异常。 您可以使用[CTaskDialog 更改进度栏范围：：设置进度栏范围](#setprogressbarrange)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarrange"></a><a name="setprogressbarrange"></a>CTask对话：：设置进度栏范围

调整进度条的范围。

```
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>参数

*恩朗明*<br/>
[在]进度条的下限。

*nRangeMax*<br/>
[在]进度条的上限。

### <a name="remarks"></a>备注

进度条的位置相对于*nRangeMin*和*nRangeMax*。 例如，如果*nRangeMin*为*50，nRangeMax*为 100，则位置为 75 的位置位于进度条的一半。 使用[CTaskDialog：设置进度栏位置](#setprogressbarposition)以设置进度栏的位置。

要显示进度条，必须启用选项TDF_SHOW_PROGRESS_BAR，并且不能启用TDF_SHOW_MARQUEE_PROGRESS_BAR。 此方法会自动设置TDF_SHOW_PROGRESS_BAR并清除TDF_SHOW_MARQUEE_PROGRESS_BAR。 使用[CTaskDialog：：设置选项](#setoptions)以手动更改[CTaskDialog 类](../../mfc/reference/ctaskdialog-class.md)的此实例的选项。

如果*nRangeMin*不小于*nRangeMax，* 则此方法会向["确保"](diagnostic-services.md#ensure)宏引发异常。 如果已显示 ，并且具有选`CTaskDialog`框进度栏，则此方法还会引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarstate"></a><a name="setprogressbarstate"></a>C任务对话：：设置进度栏

设置进度条的状态并将其显示在 上`CTaskDialog`。

```
void SetProgressBarState(int nState = PBST_NORMAL);
```

### <a name="parameters"></a>参数

*n州*<br/>
[在]进度条的状态。 有关可能的值，请参阅备注部分。

### <a name="remarks"></a>备注

如果已显示 ，并且具有选框进度栏`CTaskDialog`，则此方法会向["确保"](diagnostic-services.md#ensure)宏引发异常。

下表列出了*nState*的可能值。 在所有这些情况下，进度条将填充常规颜色，直到它到达指定的停止位置。 此时，它将根据状态更改颜色。

|||
|-|-|
|PBST_NORMAL|进度条填充后，`CTaskDialog`不会更改条形的颜色。 默认情况下，常规颜色为绿色。|
|PBST_ERROR|进度条填充后，`CTaskDialog`将条形的颜色更改为错误颜色。 默认情况下，这是红色的。|
|PBST_PAUSED|进度条填充后，`CTaskDialog`将条形的颜色更改为已暂停的颜色。 默认情况下，这是黄色的。|

您可以使用 CTaskDialog 设置进度栏停止的位置[：：设置进度栏位置](#setprogressbarposition)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetradiobuttonoptions"></a><a name="setradiobuttonoptions"></a>CTask对话：：设置无线按钮选项

启用或禁用单选按钮。

```
void SetRadioButtonOptions(
    int nRadioButtonID,
    BOOL bEnabled);
```

### <a name="parameters"></a>参数

*nRadioButtonID*<br/>
[在]单选按钮控件的 ID。

*b 启用*<br/>
[在]TRUE 启用单选按钮;FALSE 以禁用单选按钮。

### <a name="remarks"></a>备注

如果*nRadioButtonID*不是单选按钮的有效 ID，则此方法会向["确保"](diagnostic-services.md#ensure)宏引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetverificationcheckbox"></a><a name="setverificationcheckbox"></a>C任务对话：：设置验证复选框

设置验证复选框的选中状态。

```
void SetVerificationCheckbox(BOOL bChecked);
```

### <a name="parameters"></a>参数

*bChecked*<br/>
[在]TRUE 以在 显示 时选择`CTaskDialog`验证复选框;FALSE 在 显示 时未选中`CTaskDialog`验证复选框。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetverificationcheckboxtext"></a><a name="setverificationcheckboxtext"></a>CTask对话：：设置验证复选框文本

设置显示在验证复选框右侧的文本。

```
void SetVerificationCheckboxText(CString& strVerificationText);
```

### <a name="parameters"></a>参数

*str验证文本*<br/>
[在]此方法显示在验证复选框旁边的文本。

### <a name="remarks"></a>备注

如果已显示类的此实例，`CTaskDialog`此方法会向["确保"](diagnostic-services.md#ensure)宏引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetwindowtitle"></a><a name="setwindowtitle"></a>C任务对话：：设置窗口标题

设置 的标题`CTaskDialog`。

```
void SetWindowTitle(CString& strWindowTitle);
```

### <a name="parameters"></a>参数

*strWindow 标题*<br/>
[在]的新标题`CTaskDialog`。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogshowdialog"></a><a name="showdialog"></a>C任务对话：：显示对话

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

*str内容*<br/>
[在]用于 的内容`CTaskDialog`的字符串。

*斯特曼指令*<br/>
[在]的主要指令`CTaskDialog`。

*斯特标题*<br/>
[在]的标题`CTaskDialog`。

*nID命令控制优先*<br/>
[在]第一个命令的字符串 ID。

*nID命令控制上次*<br/>
[在]最后一个命令的字符串 ID。

*n 通用按钮*<br/>
[在]要添加到 的`CTaskDialog`按钮的掩码。

*n任务对话选项*<br/>
[在]用于 的选项`CTaskDialog`集。

*斯特福特*<br/>
[在]要用作页脚的字符串。

### <a name="return-value"></a>返回值

与用户所做的选择对应的整数。

### <a name="remarks"></a>备注

此静态方法使您能够创建类的实例，`CTaskDialog`而无需在代码中显式创建`CTaskDialog`对象。 由于没有`CTaskDialog`对象，`CTaskDialog`因此，如果使用此方法向用户显示 ，`CTaskDialog`则无法调用 的任何其他方法。

此方法通过使用来自应用程序的资源文件的数据创建命令按钮控件。 资源文件中的字符串表具有多个字符串与关联的字符串指示。 此方法为*nIDCommandControlsFirst*和*nCommandControlsLast*之间的字符串表中的每个有效条目添加命令按钮控件，包括。 对于这些命令按钮控件，字符串表中的字符串是控件的标题，字符串 ID 是控件的 ID。

有关有效选项的列表，请参阅[CTaskDialog：设置选项](#setoptions)。

当用户`CTaskDialog`选择公共按钮、命令链接控件或关闭 时`CTaskDialog`关闭 。 返回值是指示用户如何关闭对话框的标识符。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogtaskdialogcallback"></a><a name="taskdialogcallback"></a>C任务对话：：任务对话回调

框架调用此方法以响应各种 Windows 消息。

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

*霍恩德*<br/>
[在]对 的结构`m_hWnd``CTaskDialog`的句柄。

*u 通知*<br/>
[在]指定生成的消息的通知代码。

*wParam*<br/>
[在]有关该消息的详细信息。

*lParam*<br/>
[在]有关该消息的详细信息。

*dwRefData*<br/>
[在]指向回调消息应用于`CTaskDialog`的对象的指针。

### <a name="return-value"></a>返回值

取决于特定的通知代码。 有关详细信息，请参阅“备注”部分。

### <a name="remarks"></a>备注

的`TaskDialogCallback`默认实现处理特定消息，然后调用[CTaskDialog 类](../../mfc/reference/ctaskdialog-class.md)的适当的 On 方法。 例如，为了响应TDN_BUTTON_CLICKED消息，`TaskDialogCallback`调用[CTaskDialog：：OnCommandControl 单击](#oncommandcontrolclick)。

*wParam*和*lParam*的值取决于特定生成的消息。 这些值或两个值都可能是空的。 下表列出了支持的默认通知以及*wParam*和*lParam*的值表示的内容。 如果在派生类中重写此方法，则应为下表中的每条消息实现回调代码。

|通知消息|*wParam*价值|*lParam*价值|
|--------------------------|--------------------|--------------------|
|TDN_CREATED|未使用。|未使用。|
|TDN_NAVIGATED|未使用。|未使用。|
|TDN_BUTTON_CLICKED|命令按钮控制 ID。|未使用。|
|TDN_HYPERLINK_CLICKED|未使用。|包含链接的[LPCWSTR](/windows/win32/WinProg/windows-data-types)结构。|
|TDN_TIMER|创建 或重置计时器以来`CTaskDialog`的时间（以毫秒为单位）。|未使用。|
|TDN_DESTROYED|未使用。|未使用。|
|TDN_RADIO_BUTTON_CLICKED|单选按钮 ID。|未使用。|
|TDN_DIALOG_CONSTRUCTED|未使用。|未使用。|
|TDN_VERIFICATION_CLICKED|如果选中该复选框，为 1，则为 0（如果不是）。|未使用。|
|TDN_HELP|未使用。|未使用。|
|TDN_EXPANDO_BUTTON_CLICKED|如果扩展区域折叠，0;如果显示扩展文本，则非零。|未使用。|

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[演练：向应用程序添加 CTaskDialog](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)
