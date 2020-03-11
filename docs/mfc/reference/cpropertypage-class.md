---
title: CPropertyPage 类
ms.date: 11/04/2016
f1_keywords:
- CPropertyPage
- AFXDLGS/CPropertyPage
- AFXDLGS/CPropertyPage::CPropertyPage
- AFXDLGS/CPropertyPage::CancelToClose
- AFXDLGS/CPropertyPage::Construct
- AFXDLGS/CPropertyPage::GetPSP
- AFXDLGS/CPropertyPage::OnApply
- AFXDLGS/CPropertyPage::OnCancel
- AFXDLGS/CPropertyPage::OnKillActive
- AFXDLGS/CPropertyPage::OnOK
- AFXDLGS/CPropertyPage::OnQueryCancel
- AFXDLGS/CPropertyPage::OnReset
- AFXDLGS/CPropertyPage::OnSetActive
- AFXDLGS/CPropertyPage::OnWizardBack
- AFXDLGS/CPropertyPage::OnWizardFinish
- AFXDLGS/CPropertyPage::OnWizardNext
- AFXDLGS/CPropertyPage::QuerySiblings
- AFXDLGS/CPropertyPage::SetModified
- AFXDLGS/CPropertyPage::m_psp
helpviewer_keywords:
- CPropertyPage [MFC], CPropertyPage
- CPropertyPage [MFC], CancelToClose
- CPropertyPage [MFC], Construct
- CPropertyPage [MFC], GetPSP
- CPropertyPage [MFC], OnApply
- CPropertyPage [MFC], OnCancel
- CPropertyPage [MFC], OnKillActive
- CPropertyPage [MFC], OnOK
- CPropertyPage [MFC], OnQueryCancel
- CPropertyPage [MFC], OnReset
- CPropertyPage [MFC], OnSetActive
- CPropertyPage [MFC], OnWizardBack
- CPropertyPage [MFC], OnWizardFinish
- CPropertyPage [MFC], OnWizardNext
- CPropertyPage [MFC], QuerySiblings
- CPropertyPage [MFC], SetModified
- CPropertyPage [MFC], m_psp
ms.assetid: d9000a21-aa81-4530-85d9-f43432afb4dc
ms.openlocfilehash: 6a6223708c83f7a5b3e6532a2016660d558f8270
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865426"
---
# <a name="cpropertypage-class"></a>CPropertyPage 类

表示属性表的各个页，也称为选项卡对话框。

## <a name="syntax"></a>语法

```
class CPropertyPage : public CDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CPropertyPage：： CPropertyPage](#cpropertypage)|构造 `CPropertyPage` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CPropertyPage：： CancelToClose](#canceltoclose)|将 "确定" 按钮更改为 "关闭"，并在模式属性表的页中发生不可恢复的更改后禁用 "取消" 按钮。|
|[CPropertyPage：：构造](#construct)|构造 `CPropertyPage` 对象。 如果要在运行时指定参数，或者使用数组，请使用 `Construct`。|
|[CPropertyPage：： GetPSP](#getpsp)|检索与 `CPropertyPage` 对象关联的 Windows [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2)结构。|
|[CPropertyPage：： OnApply](#onapply)|当单击 "立即应用" 按钮时，由框架调用。|
|[CPropertyPage：： OnCancel](#oncancel)|当单击 "取消" 按钮时由框架调用。|
|[CPropertyPage：： OnKillActive](#onkillactive)|当当前页不再是活动页时由框架调用。 在此处执行数据验证。|
|[CPropertyPage：： OnOK](#onok)|当单击 "确定"、"立即应用" 或 "关闭" 按钮时由框架调用。|
|[CPropertyPage：： OnQueryCancel](#onquerycancel)|当单击 "取消" 按钮时，由框架调用，并在取消之前发生。|
|[CPropertyPage：： OnReset](#onreset)|当单击 "取消" 按钮时由框架调用。|
|[CPropertyPage：： OnSetActive](#onsetactive)|当该页成为活动页时由框架调用。|
|[CPropertyPage：： OnWizardBack](#onwizardback)|当使用向导类型的属性表时单击 "后退" 按钮时，由框架调用。|
|[CPropertyPage：： OnWizardFinish](#onwizardfinish)|当使用向导类型的属性表时单击 "完成" 按钮时，由框架调用。|
|[CPropertyPage：： OnWizardNext](#onwizardnext)|当使用向导类型的属性表时，单击 "下一步" 按钮时由框架调用。|
|[CPropertyPage：： QuerySiblings](#querysiblings)|将消息转发到属性表的每一页。|
|[CPropertyPage：： SetModified](#setmodified)|调用以激活或停用 "立即应用" 按钮。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CPropertyPage：： m_psp](#m_psp)|Windows [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2)结构。 提供对基本属性页参数的访问。|

## <a name="remarks"></a>备注

与标准对话框一样，您可以从属性表中的每一页的 `CPropertyPage` 派生类。 若要使用 `CPropertyPage`派生对象，请首先创建一个[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)对象，然后为属性表中的每一页创建一个对象。 对工作表中的每一页调用[CPropertySheet：： AddPage](../../mfc/reference/cpropertysheet-class.md#addpage) ，然后通过对模式属性表调用[CPropertySheet：:D omodal](../../mfc/reference/cpropertysheet-class.md#domodal) ，或为无模式属性表调用[CPropertySheet：： Create](../../mfc/reference/cpropertysheet-class.md#create)来显示属性表。

您可以创建一个名为 "向导" 的 "选项卡" 对话框，其中包含一系列属性页，用于引导用户完成操作的步骤，如设置设备或创建新闻稿。 在向导类型的 "选项卡" 对话框中，属性页没有选项卡，一次只能显示一个属性页。 此外，"向导类型" 选项卡对话框中包含 "后退" 按钮、"下一步" 或 "完成" 按钮和 "取消" 按钮，而不是 "立即确定" 和 "立即应用" 按钮。

有关将属性表作为向导建立的详细信息，请参阅[CPropertySheet：： SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。 有关使用 `CPropertyPage` 对象的详细信息，请参阅文章[属性表和属性页](../../mfc/property-sheets-and-property-pages-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CPropertyPage`

## <a name="requirements"></a>要求

**标头：** afxdlgs

##  <a name="canceltoclose"></a>CPropertyPage：： CancelToClose

对模式属性表的页中的数据进行了无法恢复的更改后，调用此函数。

```
void CancelToClose();
```

### <a name="remarks"></a>备注

此函数将更改 "确定" 按钮以关闭并禁用 "取消" 按钮。 此更改提醒用户，更改是永久性的，无法取消修改。

`CancelToClose` 成员函数在无模式属性表中不执行任何操作，因为无模式属性表默认情况下没有 "取消" 按钮。

### <a name="example"></a>示例

  请参阅[CPropertyPage：： QuerySiblings](#querysiblings)的示例。

##  <a name="construct"></a>CPropertyPage：：构造

调用此成员函数以构造一个 `CPropertyPage` 对象。

```
void Construct(
    UINT nIDTemplate,
    UINT nIDCaption = 0);

void Construct(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption = 0);

void Construct(
    UINT nIDTemplate,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0);

void Construct(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0);
```

### <a name="parameters"></a>parameters

*nIDTemplate*<br/>
用于此页的模板的 ID。

*nIDCaption*<br/>
要放置在此页的选项卡中的名称的 ID。 如果为0，则将从此页的对话框模板获取名称。

*lpszTemplateName*<br/>
包含以 null 结尾的字符串，它是模板资源的名称。

*nIDHeaderTitle*<br/>
要放置在属性页标题的标题位置的名称的 ID。 默认值为0。

*nIDHeaderSubTitle*<br/>
要放置在属性页标题的副标题位置的名称的 ID。 默认值为0。

### <a name="remarks"></a>备注

满足下列所有条件后，将显示该对象：

- 该页已添加到使用[CPropertySheet：： AddPage](../../mfc/reference/cpropertysheet-class.md#addpage)的属性表中。

- 已调用属性表的[DoModal](../../mfc/reference/cpropertysheet-class.md#domodal)或[Create](../../mfc/reference/cpropertysheet-class.md#create)函数。

- 用户已选择（选项卡到）此页。

如果未调用某个其他类构造函数，则调用 `Construct`。 `Construct` 成员函数是灵活的，因为可以将 parameter 语句留空，然后在代码中的任意位置指定多个参数和构造。

当使用数组时，必须使用 `Construct`，并且必须为数组的每个成员调用 `Construct`，以便为数据成员分配正确的值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]

##  <a name="cpropertypage"></a>CPropertyPage：： CPropertyPage

构造 `CPropertyPage` 对象。

```
CPropertyPage();

explicit CPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));

explicit CPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));

CPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));

CPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));
```

### <a name="parameters"></a>parameters

*nIDTemplate*<br/>
用于此页的模板的 ID。

*nIDCaption*<br/>
要放置在此页的选项卡中的名称的 ID。 如果为0，则将从此页的对话框模板获取名称。

*dwSize*<br/>
*lpszTemplateName*指向一个字符串，该字符串包含此页的模板的名称。 不能为 NULL。

*nIDHeaderTitle*<br/>
要放置在属性页标题的标题位置的名称的 ID。

*nIDHeaderSubTitle*<br/>
要放置在属性页标题的副标题位置的名称的 ID。

### <a name="remarks"></a>备注

满足下列所有条件后，将显示该对象：

- 该页已添加到使用[CPropertySheet：： AddPage](../../mfc/reference/cpropertysheet-class.md#addpage)的属性表中。

- 已调用属性表的[DoModal](../../mfc/reference/cpropertysheet-class.md#domodal)或[Create](../../mfc/reference/cpropertysheet-class.md#create)函数。

- 用户已选择（选项卡到）此页。

如果有多个参数（例如，使用数组），请使用[CPropertySheet：：构造](../../mfc/reference/cpropertysheet-class.md#construct)而不是 `CPropertyPage`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]

##  <a name="getpsp"></a>CPropertyPage：： GetPSP

检索与 `CPropertyPage` 对象关联的 Windows [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2)结构。

```
const PROPSHEETPAGE& GetPSP() const;

PROPSHEETPAGE& GetPSP();
```

### <a name="return-value"></a>返回值

对 `PROPSHEETPAGE` 结构的引用。

##  <a name="m_psp"></a>CPropertyPage：： m_psp

`m_psp` 是一种结构，其成员存储[PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2)的特性。

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>备注

使用此结构可以在构造后初始化属性页的外观。

有关此结构的详细信息（包括其成员的列表），请参阅 Windows SDK 中的 `PROPSHEETPAGE`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]

##  <a name="onapply"></a>CPropertyPage：： OnApply

当用户选择 "确定" 或 "立即应用" 按钮时，框架会调用此成员函数。

```
virtual BOOL OnApply();
```

### <a name="return-value"></a>返回值

如果接受更改，则为非零值;否则为0。

### <a name="remarks"></a>备注

当框架调用此函数时，将接受对属性表中的所有属性页所做的更改，属性表将保留焦点，`OnApply` 返回 TRUE （值为1）。 必须先调用[SetModified](#setmodified) ，并将其参数设置为 TRUE，然后才能由框架调用 `OnApply`。 这将在用户在属性页上进行更改后立即激活 "立即应用" 按钮。

重写此成员函数以指定用户单击 "立即应用" 按钮时程序采取的操作。 重写时，函数应返回 TRUE 以接受更改，并返回 FALSE 以防止更改生效。

`OnApply` 的默认实现 `OnOK`调用。

有关用户按属性表中的 "立即应用" 或 "确定" 按钮时发送的通知消息的详细信息，请参阅 Windows SDK 中的[PSN_APPLY](/windows/win32/Controls/psn-apply) 。

### <a name="example"></a>示例

  请参阅[CPropertyPage：： OnOK](#onok)的示例。

##  <a name="oncancel"></a>CPropertyPage：： OnCancel

选择 "取消" 按钮后，框架将调用此成员函数。

```
virtual void OnCancel();
```

### <a name="remarks"></a>备注

重写此成员函数以执行 "取消" 按钮操作。 默认值将对所做的任何更改取消。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]

##  <a name="onkillactive"></a>CPropertyPage：： OnKillActive

当页不再是活动页时，框架会调用此成员函数。

```
virtual BOOL OnKillActive();
```

### <a name="return-value"></a>返回值

如果成功更新了数据，则为非零; 否则为0。

### <a name="remarks"></a>备注

重写此成员函数以执行特殊的数据验证任务。

此成员函数的默认实现将设置从属性页的控件复制到属性页的成员变量。 如果由于对话框数据验证（DDV）错误而未成功更新数据，则页面将保持焦点。

此成员函数成功返回后，框架将调用页面的[OnOK](#onok)函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]

##  <a name="onok"></a>CPropertyPage：： OnOK

此成员函数在用户选择 "确定" 或 "立即应用" 按钮时由框架调用，紧跟在框架调用[OnKillActive](#onkillactive)后。

```
virtual void OnOK();
```

### <a name="remarks"></a>备注

当用户选择 "确定" 或 "立即应用" 按钮时，框架会从属性页接收[PSN_APPLY](/windows/win32/Controls/psn-apply)通知。 如果调用[CPropertySheet：:P ressbutton](../../mfc/reference/cpropertysheet-class.md#pressbutton) ，则不会调用 `OnOK`，因为在这种情况下，属性页不会发送通知。

重写此成员函数可在用户关闭整个属性表时，实现特定于当前活动页的其他行为。

此成员函数的默认实现将该页标记为 "clean"，以反映已在 `OnKillActive` 函数中更新数据。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]

##  <a name="onquerycancel"></a>CPropertyPage：： OnQueryCancel

当用户单击 "取消" 按钮时，或在发生取消操作之前，框架将调用此成员函数。

```
virtual BOOL OnQueryCancel();
```

### <a name="return-value"></a>返回值

返回 FALSE 以防止取消操作或设置为 TRUE。

### <a name="remarks"></a>备注

重写此成员函数以指定用户单击 "取消" 按钮时程序采取的操作。

`OnQueryCancel` 的默认实现将返回 TRUE。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]

##  <a name="onreset"></a>CPropertyPage：： OnReset

当用户选择 "取消" 按钮时，框架会调用此成员函数。

```
virtual void OnReset();
```

### <a name="remarks"></a>备注

当框架调用此函数时，将丢弃用户之前选择 "立即应用" 按钮所做的所有属性页的更改，并且属性表将保留焦点。

重写此成员函数以指定用户单击 "取消" 按钮时程序采取的操作。

`OnReset` 的默认实现不执行任何操作。

### <a name="example"></a>示例

  请参阅[CPropertyPage：： OnCancel](#oncancel)的示例。

##  <a name="onsetactive"></a>CPropertyPage：： OnSetActive

当用户选择页面并成为活动页面时，框架会调用此成员函数。

```
virtual BOOL OnSetActive();
```

### <a name="return-value"></a>返回值

如果成功设置了页面，则为非零值;否则为0。

### <a name="remarks"></a>备注

当激活某个页面时，重写此成员函数以执行任务。 此成员函数的重写通常会在更新数据成员后调用默认版本，以允许它用新数据更新页面控件。

默认实现会创建页的窗口（如果以前未创建），并使其成为活动页。

### <a name="example"></a>示例

  请参阅[CPropertySheet：： SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext)的示例。

##  <a name="onwizardback"></a>CPropertyPage：： OnWizardBack

当用户单击向导中的 "后退" 按钮时，框架会调用此成员函数。

```
virtual LRESULT OnWizardBack();
```

### <a name="return-value"></a>返回值

0会自动前进到下一页;-1，以防页面发生变化。 若要跳转到下一个页面，请返回要显示的对话框的标识符。

### <a name="remarks"></a>备注

重写此成员函数以指定在按下 "后退" 按钮时用户必须执行的某些操作。

有关如何创建向导类型属性表的详细信息，请参阅[CPropertySheet：： SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]

##  <a name="onwizardfinish"></a>CPropertyPage：： OnWizardFinish

当用户单击向导中的 "完成" 按钮时，框架会调用此成员函数。

```
virtual BOOL OnWizardFinish();
```

### <a name="return-value"></a>返回值

如果向导完成时属性表被销毁，则为非零值;否则为零。

### <a name="remarks"></a>备注

当用户在向导中单击 "**完成**" 按钮时，框架会调用此函数;当 `OnWizardFinish` 返回 TRUE （非零值）时，可以销毁属性表（但实际上不会销毁）。 调用 `DestroyWindow` 以销毁属性表。 不要从 `OnWizardFinish`调用 `DestroyWindow`;这样做将导致堆损坏或其他错误。

您可以重写此成员函数，以指定在按 "完成" 按钮时用户必须执行的某些操作。 重写此函数时，将返回 FALSE 以防止对属性表进行销毁。

有关用户按向导属性表中的 "完成" 按钮时发送的通知消息的详细信息，请参阅 Windows SDK 中的[PSN_WIZFINISH](/windows/win32/Controls/psn-wizfinish) 。

有关如何创建向导类型属性表的详细信息，请参阅[CPropertySheet：： SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]

[!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]

[!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]

[!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]

##  <a name="onwizardnext"></a>CPropertyPage：： OnWizardNext

当用户单击向导中的 "下一步" 按钮时，框架会调用此成员函数。

```
virtual LRESULT OnWizardNext();
```

### <a name="return-value"></a>返回值

0会自动前进到下一页;-1，以防页面发生变化。 若要跳转到下一个页面，请返回要显示的对话框的标识符。

### <a name="remarks"></a>备注

重写此成员函数以指定在按下 "下一步" 按钮时用户必须执行的某些操作。

有关如何创建向导类型属性表的详细信息，请参阅[CPropertySheet：： SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]

##  <a name="querysiblings"></a>CPropertyPage：： QuerySiblings

调用此成员函数将消息转发到属性表中的每一页。

```
LRESULT QuerySiblings(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>parameters

*wParam*<br/>
指定其他消息相关的信息。

*lParam*<br/>
指定其他消息相关信息

### <a name="return-value"></a>返回值

属性表中页的非零值，如果所有页返回值0，则为0。

### <a name="remarks"></a>备注

如果页面返回一个非零值，则该属性表不会将该消息发送到后续页面。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]

[!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]

##  <a name="setmodified"></a>CPropertyPage：： SetModified

调用此成员函数以启用或禁用 "立即应用" 按钮，具体取决于是否应将 "属性" 页中的设置应用于相应的外部对象。

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>parameters

*bChanged*<br/>
如果为 TRUE，则指示自上次应用后修改了属性页设置;若为 FALSE，则指示属性页设置已应用，或应忽略。

### <a name="remarks"></a>备注

框架跟踪哪些页是 "脏的"，即您为其调用 `SetModified( TRUE )`的属性页。 如果为某个页面调用 `SetModified( TRUE )`，将始终启用 "立即应用" 按钮。 当你为某个页面调用 `SetModified( FALSE )` 时，"立即应用" 按钮将被禁用，但前提是没有其他页面为 "脏"。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 示例 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CPropertySheet 类](../../mfc/reference/cpropertysheet-class.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)
