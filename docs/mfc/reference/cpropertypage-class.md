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
ms.openlocfilehash: f46566eb562f1515e98aedf938ca68b225ee1b67
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751100"
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
|[C属性页：C属性页](#cpropertypage)|构造 `CPropertyPage` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C属性页：：取消关闭](#canceltoclose)|在模态属性表页面发生不可恢复更改后，将"确定"按钮更改为"关闭"，并禁用"取消"按钮。|
|[C属性页：构造](#construct)|构造 `CPropertyPage` 对象。 `Construct`如果要在运行时指定参数，或者使用数组，请使用。|
|[C属性页：获取PSP](#getpsp)|检索与`CPropertyPage`对象关联的 Windows [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2)结构。|
|[C属性页：：在申请上](#onapply)|单击"立即应用"按钮时由框架调用。|
|[C属性页：打开取消](#oncancel)|单击"取消"按钮时由框架调用。|
|[C属性页：在活动](#onkillactive)|当当前页面不再是活动页时，由框架调用。 在此处执行数据验证。|
|[C属性页：ONOK](#onok)|单击"确定"""立即应用"或"关闭"按钮时，由框架调用。|
|[C属性页：在查询取消](#onquerycancel)|单击"取消"按钮时和取消发生之前，由框架调用。|
|[C属性页：打开重置](#onreset)|单击"取消"按钮时由框架调用。|
|[C属性页：打开活动](#onsetactive)|当页面成为活动页时，由框架调用。|
|[C属性页：：在向导背面](#onwizardback)|使用向导类型属性表单击"后退"按钮时，由框架调用。|
|[C属性页：在向导完成](#onwizardfinish)|使用向导类型属性表单击"完成"按钮时，由框架调用。|
|[C属性页：：在向导下一页](#onwizardnext)|使用向导类型属性表单击"下一步"按钮时，由框架调用。|
|[C属性页：查询同级](#querysiblings)|将消息转发到属性表的每个页面。|
|[C属性页：：已修改](#setmodified)|调用以激活或停用"立即应用"按钮。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[C属性页：m_psp](#m_psp)|Windows [PROPPAGE 结构](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2)。 提供对基本属性页参数的访问。|

## <a name="remarks"></a>备注

与标准对话框一样，从属性表中的每个页面`CPropertyPage`派生一个类。 要使用`CPropertyPage`派生对象，请先创建[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)对象，然后为属性表中的每个页面创建一个对象。 调用[CPropertySheet：：为工作表中的每个页面添加Page，](../../mfc/reference/cpropertysheet-class.md#addpage)然后通过调用模式属性表的[CPropertySheet：:DoModal）](../../mfc/reference/cpropertysheet-class.md#domodal)或[CPropertySheet：：为](../../mfc/reference/cpropertysheet-class.md#create)无模式属性表创建来显示属性表。

您可以创建称为向导的选项卡对话框类型，该对话框由包含一系列属性页的属性表组成，该属性页指导用户完成操作的步骤，例如设置设备或创建新闻稿。 在向导类型选项卡对话框中，属性页没有选项卡，并且一次只能看到一个属性页。 此外，向导类型选项卡对话框没有"确定"和"立即应用"按钮，而是具有"后退"按钮、"下一步"或"完成"按钮以及"取消"按钮。

有关将属性表设置为向导的详细信息，请参阅[CPropertySheet：setWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。 有关使用`CPropertyPage`对象的详细信息，请参阅文章["属性表"和"属性页](../../mfc/property-sheets-and-property-pages-in-mfc.md)"。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CPropertyPage`

## <a name="requirements"></a>要求

**标题：** afxdlgs.h

## <a name="cpropertypagecanceltoclose"></a><a name="canceltoclose"></a>C属性页：：取消关闭

对模态属性表页面中的数据进行了不可恢复的更改后，请调用此函数。

```cpp
void CancelToClose();
```

### <a name="remarks"></a>备注

此功能将"确定"按钮更改为"关闭"并禁用"取消"按钮。 此更改提醒用户更改是永久性的，并且无法取消修改。

成员`CancelToClose`函数在无模式属性表中不执行任何操作，因为默认情况下，无模式属性表没有"取消"按钮。

### <a name="example"></a>示例

  请参阅[CPropertyPage：查询同级的示例](#querysiblings)。

## <a name="cpropertypageconstruct"></a><a name="construct"></a>C属性页：构造

调用此成员函数以构造对象`CPropertyPage`。

```cpp
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

### <a name="parameters"></a>参数

*nIDTemplate*<br/>
用于此页面的模板的 ID。

*nIDCaption*<br/>
要放置在此页选项卡中的名称的 ID。 如果为 0，则名称将从此页面的对话框模板中获取。

*lpszTemplate 名称*<br/>
包含一个 null 端接字符串，该字符串是模板资源的名称。

*nIDHeader标题*<br/>
要放置在属性页页页页标题的标题位置的名称的 ID。 默认情况下，0。

*nIDHeader 子标题*<br/>
要放置在属性页页标题的字幕位置的名称的 ID。 默认情况下，0。

### <a name="remarks"></a>备注

满足以下所有条件后，将显示该对象：

- 该页已使用[CPropertySheet：：AddPage](../../mfc/reference/cpropertysheet-class.md#addpage)添加到属性表。

- 属性表的["DoModal"](../../mfc/reference/cpropertysheet-class.md#domodal)或["创建"](../../mfc/reference/cpropertysheet-class.md#create)函数已调用。

- 用户已选择（选项卡到）此页面。

如果`Construct`尚未调用其他类构造函数之一，则调用。 `Construct`成员函数是灵活的，因为您可以将参数语句留空，然后在代码中的任何点指定多个参数和构造。

在使用数组`Construct`时必须使用，并且必须调用`Construct`数组的每个成员，以便为数据成员分配正确的值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]

## <a name="cpropertypagecpropertypage"></a><a name="cpropertypage"></a>C属性页：C属性页

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

### <a name="parameters"></a>参数

*nIDTemplate*<br/>
用于此页面的模板的 ID。

*nIDCaption*<br/>
要放置在此页选项卡中的名称的 ID。 如果为 0，则名称将从此页面的对话框模板中获取。

*dwSize*<br/>
*lpszTemplate 名称*指向包含此页面模板名称的字符串。 不能为 NULL。

*nIDHeader标题*<br/>
要放置在属性页页页页标题的标题位置的名称的 ID。

*nIDHeader 子标题*<br/>
要放置在属性页页标题的字幕位置的名称的 ID。

### <a name="remarks"></a>备注

满足以下所有条件后，将显示该对象：

- 该页已使用[CPropertySheet：：AddPage](../../mfc/reference/cpropertysheet-class.md#addpage)添加到属性表。

- 属性表的["DoModal"](../../mfc/reference/cpropertysheet-class.md#domodal)或["创建"](../../mfc/reference/cpropertysheet-class.md#create)函数已调用。

- 用户已选择（选项卡到）此页面。

如果有多个参数（例如，如果您正在使用数组），请使用[CPropertySheet：：构造](../../mfc/reference/cpropertysheet-class.md#construct)而不是`CPropertyPage`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]

## <a name="cpropertypagegetpsp"></a><a name="getpsp"></a>C属性页：获取PSP

检索与`CPropertyPage`对象关联的 Windows [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2)结构。

```
const PROPSHEETPAGE& GetPSP() const;

PROPSHEETPAGE& GetPSP();
```

### <a name="return-value"></a>返回值

对结构的`PROPSHEETPAGE`引用。

## <a name="cpropertypagem_psp"></a><a name="m_psp"></a>C属性页：m_psp

`m_psp`是一个结构，其成员存储[PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2)的特征。

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>备注

使用此结构在构造属性页后初始化属性页的外观。

有关此结构的详细信息（包括其成员的列表），请参阅`PROPSHEETPAGE`Windows SDK。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]

## <a name="cpropertypageonapply"></a><a name="onapply"></a>C属性页：：在申请上

当用户选择"确定"或"立即应用"按钮时，框架将调用此成员函数。

```
virtual BOOL OnApply();
```

### <a name="return-value"></a>返回值

如果接受更改，则非零;否则 0。

### <a name="remarks"></a>备注

当框架调用此函数时，接受在属性表中的所有属性页上所做的更改，属性表将保留焦点，并`OnApply`返回 TRUE（值 1）。 在`OnApply`框架可以调用之前，必须调用[Set修改](#setmodified)并将其参数设置为 TRUE。 当用户在属性页上进行更改时，这将激活"立即应用"按钮。

覆盖此成员函数，以指定当用户单击"立即应用"按钮时程序执行的操作。 重写时，函数应返回 TRUE 以接受更改和 FALSE，以防止更改生效。

调用`OnApply``OnOK`的默认实现。

有关用户在属性表中按下"立即应用"或"确定"按钮时发送的通知消息的详细信息，请参阅 Windows SDK 中的[PSN_APPLY。](/windows/win32/Controls/psn-apply)

### <a name="example"></a>示例

  请参阅[CPropertyPage 示例：：OnOK](#onok)。

## <a name="cpropertypageoncancel"></a><a name="oncancel"></a>C属性页：打开取消

选择"取消"按钮时，框架将调用此成员函数。

```
virtual void OnCancel();
```

### <a name="remarks"></a>备注

覆盖此成员函数以执行"取消"按钮操作。 默认值将否定已进行的任何更改。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]

## <a name="cpropertypageonkillactive"></a><a name="onkillactive"></a>C属性页：在活动

当页面不再是活动页时，框架将调用此成员函数。

```
virtual BOOL OnKillActive();
```

### <a name="return-value"></a>返回值

如果数据已成功更新，则非零，否则为 0。

### <a name="remarks"></a>备注

重写此成员函数以执行特殊的数据验证任务。

此成员函数的默认实现将设置从属性页的控件复制到属性页的成员变量。 如果由于对话框数据验证 （DDV） 错误而未成功更新数据，则页面将保留焦点。

此成员函数成功返回后，框架将调用页面的[OnOK](#onok)函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]

## <a name="cpropertypageonok"></a><a name="onok"></a>C属性页：ONOK

当用户选择"确定"或"立即申请"按钮时，在框架调用[OnKillActive](#onkillactive)之后，框架会调用此成员函数。

```
virtual void OnOK();
```

### <a name="remarks"></a>备注

当用户选择"确定"或"立即应用"按钮时，框架将从属性页收到[PSN_APPLY](/windows/win32/Controls/psn-apply)通知。 如果您调用`OnOK`[CPropertySheet：:PresButton，](../../mfc/reference/cpropertysheet-class.md#pressbutton)则不会调用 to，因为在这种情况下，属性页不会发送通知。

重写此成员函数，在用户关闭整个属性表时实现特定于当前活动页的其他行为。

此成员函数的默认实现将页面标记为"干净"，以反映数据在`OnKillActive`函数中已更新。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]

## <a name="cpropertypageonquerycancel"></a><a name="onquerycancel"></a>C属性页：在查询取消

当用户单击"取消"按钮并在执行取消操作之前，框架将调用此成员函数。

```
virtual BOOL OnQueryCancel();
```

### <a name="return-value"></a>返回值

返回 FALSE 以防止取消操作或 TRUE 以允许它。

### <a name="remarks"></a>备注

覆盖此成员函数以指定程序在用户单击"取消"按钮时执行的操作。

默认实现`OnQueryCancel`返回 TRUE。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]

## <a name="cpropertypageonreset"></a><a name="onreset"></a>C属性页：打开重置

当用户选择"取消"按钮时，框架将调用此成员函数。

```
virtual void OnReset();
```

### <a name="remarks"></a>备注

当框架调用此函数时，将放弃用户以前选择"立即应用"按钮所做的所有属性页的更改，并且属性表将保留焦点。

覆盖此成员函数以指定当用户单击"取消"按钮时程序执行的操作。

的`OnReset`默认实现不执行任何操作。

### <a name="example"></a>示例

  请参阅[CPropertyPage 示例：：打开取消](#oncancel)。

## <a name="cpropertypageonsetactive"></a><a name="onsetactive"></a>C属性页：打开活动

当用户选择页面并成为活动页时，框架将调用此成员函数。

```
virtual BOOL OnSetActive();
```

### <a name="return-value"></a>返回值

如果页面已成功设置为活动，则非零;否则 0。

### <a name="remarks"></a>备注

覆盖此成员函数，以在激活页面时执行任务。 重写此成员函数通常会在更新数据成员后调用默认版本，以允许它使用新数据更新页面控件。

默认实现为页面创建窗口（如果不是以前创建）并使其成为活动页。

### <a name="example"></a>示例

  请参阅[CPropertySheet 的示例：setFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext)。

## <a name="cpropertypageonwizardback"></a><a name="onwizardback"></a>C属性页：：在向导背面

当用户单击向导中的"后退"按钮时，框架将调用此成员函数。

```
virtual LRESULT OnWizardBack();
```

### <a name="return-value"></a>返回值

0 自动前进到下一页;-1 以防止页面更改。 要跳转到下一个页面以外的页面，返回要显示的对话框的标识符。

### <a name="remarks"></a>备注

重写此成员函数以指定按下"后退"按钮时用户必须执行的操作。

有关如何创建向导类型属性表的详细信息，请参阅[CPropertySheet：setWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]

## <a name="cpropertypageonwizardfinish"></a><a name="onwizardfinish"></a>C属性页：在向导完成

当用户单击向导中的"完成"按钮时，框架将调用此成员函数。

```
virtual BOOL OnWizardFinish();
```

### <a name="return-value"></a>返回值

如果属性表在向导完成时销毁，则非零;否则为零。

### <a name="remarks"></a>备注

当用户单击向导中的"完成"按钮时，框架将调用此函数;当用户单击向导中的 **"完成"** 按钮时，框架将调用此函数。当`OnWizardFinish`返回 TRUE（非零值）时，属性表可以销毁（但实际上不会销毁）。 调用`DestroyWindow`以销毁属性表。 不要从`OnWizardFinish``DestroyWindow`拨打 。这样做将导致堆损坏或其他错误。

您可以重写此成员函数，以指定用户在按下"完成"按钮时必须执行的操作。 重写此函数时，返回 FALSE 以防止属性表被销毁。

有关用户在向导属性表中按下"完成"按钮时发送的通知消息的详细信息，请参阅 Windows SDK 中的[PSN_WIZFINISH。](/windows/win32/Controls/psn-wizfinish)

有关如何创建向导类型属性表的详细信息，请参阅[CPropertySheet：setWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]

[!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]

[!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]

[!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]

## <a name="cpropertypageonwizardnext"></a><a name="onwizardnext"></a>C属性页：：在向导下一页

当用户单击向导中的"下一步"按钮时，框架将调用此成员函数。

```
virtual LRESULT OnWizardNext();
```

### <a name="return-value"></a>返回值

0 自动前进到下一页;-1 以防止页面更改。 要跳转到下一个页面以外的页面，返回要显示的对话框的标识符。

### <a name="remarks"></a>备注

重写此成员函数以指定按下"下一步"按钮时用户必须执行的操作。

有关如何创建向导类型属性表的详细信息，请参阅[CPropertySheet：setWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]

## <a name="cpropertypagequerysiblings"></a><a name="querysiblings"></a>C属性页：查询同级

调用此成员函数将消息转发到属性表中的每个页面。

```
LRESULT QuerySiblings(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>参数

*wParam*<br/>
指定其他与消息相关的信息。

*lParam*<br/>
指定其他与消息相关的信息

### <a name="return-value"></a>返回值

属性表中的页面中的非零值;如果所有页面返回值 0，则为 0。

### <a name="remarks"></a>备注

如果页面返回非零值，则属性表不会将消息发送到后续页面。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]

[!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]

## <a name="cpropertypagesetmodified"></a><a name="setmodified"></a>C属性页：：已修改

调用此成员函数以启用或禁用"立即应用"按钮，具体取决于属性页中的设置是否应应用于相应的外部对象。

```cpp
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>参数

*b 已更改*<br/>
TRUE 以指示自上次应用属性页设置以来已修改属性页设置;FALSE 以指示已应用属性页设置，或应忽略。

### <a name="remarks"></a>备注

框架跟踪哪些页面是"脏"的，即您为其调用`SetModified( TRUE )`的属性页。 如果调用`SetModified( TRUE )`其中一个页面，则始终启用"立即应用"按钮。 当您调用`SetModified( FALSE )`其中一个页面时，将禁用"立即应用"按钮，但前提是其他页面均未"脏"。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[C属性表类](../../mfc/reference/cpropertysheet-class.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)
