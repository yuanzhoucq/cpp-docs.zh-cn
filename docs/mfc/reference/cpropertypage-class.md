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
ms.openlocfilehash: 9d4100037c5a6cd2eeef1a50fb2d5a46b2cb6505
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58772718"
---
# <a name="cpropertypage-class"></a>CPropertyPage 类

表示属性表的各个页，也称为选项卡对话框。

## <a name="syntax"></a>语法

```
class CPropertyPage : public CDialog
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CPropertyPage::CPropertyPage](#cpropertypage)|构造 `CPropertyPage` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CPropertyPage::CancelToClose](#canceltoclose)|更改确定按钮以阅读关闭，并禁用取消按钮，无法恢复在发生更改后的模式属性表页。|
|[CPropertyPage::Construct](#construct)|构造 `CPropertyPage` 对象。 使用`Construct`如果你想要在运行时，指定你的参数，或者如果正在使用数组。|
|[CPropertyPage::GetPSP](#getpsp)|检索 Windows [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2)与关联的结构`CPropertyPage`对象。|
|[CPropertyPage::OnApply](#onapply)|单击立即应用按钮时由框架调用。|
|[CPropertyPage::OnCancel](#oncancel)|单击取消按钮时由框架调用。|
|[CPropertyPage::OnKillActive](#onkillactive)|当前页不再是活动的页面时由框架调用。 执行数据验证。|
|[CPropertyPage::OnOK](#onok)|单击确定，立即应用，或关闭按钮时由框架调用。|
|[CPropertyPage::OnQueryCancel](#onquerycancel)|单击取消按钮，并在取消发生之前，由框架调用。|
|[CPropertyPage::OnReset](#onreset)|单击取消按钮时由框架调用。|
|[CPropertyPage::OnSetActive](#onsetactive)|当该页成为活动页时由框架调用。|
|[CPropertyPage::OnWizardBack](#onwizardback)|使用向导类型的属性表时单击后退按钮时由框架调用。|
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|使用向导类型的属性表时单击完成按钮时由框架调用。|
|[CPropertyPage::OnWizardNext](#onwizardnext)|使用向导类型的属性表时单击下一步按钮时由框架调用。|
|[CPropertyPage::QuerySiblings](#querysiblings)|将消息转发到属性表的每一页。|
|[CPropertyPage::SetModified](#setmodified)|调用以激活或停用的立即应用按钮。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CPropertyPage::m_psp](#m_psp)|Windows [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2)结构。 提供对基本属性页参数的访问。|

## <a name="remarks"></a>备注

如与标准对话框，您从派生类`CPropertyPage`属性表中每一页。 若要使用`CPropertyPage`-派生的对象，首先创建[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)对象，然后创建属性表中每个页的对象。 调用[cpropertysheet:: Addpage](../../mfc/reference/cpropertysheet-class.md#addpage)每个工作表，在页上，并通过调用显示属性表[cpropertysheet:: Domodal](../../mfc/reference/cpropertysheet-class.md#domodal)模式属性表，或[CPropertySheet::创建](../../mfc/reference/cpropertysheet-class.md#create)无模式属性表。

可以创建一种称为向导，其中包含具有一系列指导用户完成操作，例如设置设备，或创建时事通讯的步骤的属性页的属性表选项卡对话框。 向导类型选项卡对话框中，在属性页无选项卡上，并一次只有一个属性页上可见。 此外，而不是让确定和立即应用按钮，向导类型选项卡对话框具有后退按钮、 一个下一步或完成按钮和取消按钮。

建立属性表作为向导的详细信息，请参阅[CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。 有关使用的详细信息`CPropertyPage`对象，请参阅文章[属性表和属性页](../../mfc/property-sheets-and-property-pages-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CPropertyPage`

## <a name="requirements"></a>要求

**标头：** afxdlgs.h

##  <a name="canceltoclose"></a>  CPropertyPage::CancelToClose

发生了不可恢复的更改建立到的模式属性表页中的数据之后，请调用此函数。

```
void CancelToClose();
```

### <a name="remarks"></a>备注

此函数将更改为关闭的确定按钮并禁用取消按钮。 此更改不能取消更改是永久的所做的修改用户的警报。

`CancelToClose`成员函数中不起作用的无模式属性表，因为无模式属性表不具有默认情况下的取消按钮。

### <a name="example"></a>示例

  有关示例，请参阅[CPropertyPage::QuerySiblings](#querysiblings)。

##  <a name="construct"></a>  CPropertyPage::Construct

调用此成员函数来构造`CPropertyPage`对象。

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

### <a name="parameters"></a>参数

*nIDTemplate*<br/>
使用此页的模板的 ID。

*nIDCaption*<br/>
要放置在此页的选项卡名称的 ID。 如果为 0，名称将来自此页的对话框模板。

*lpszTemplateName*<br/>
包含的模板资源名称的以 null 结尾的字符串。

*nIDHeaderTitle*<br/>
若要将放置在属性页标题的标题位置的名称的 ID。 默认情况下，0。

*nIDHeaderSubTitle*<br/>
若要将放置在属性页标头的副标题位置名称的 ID。 默认情况下，0。

### <a name="remarks"></a>备注

满足所有以下条件时才显示该对象：

- 页已添加到属性表使用[cpropertysheet:: Addpage](../../mfc/reference/cpropertysheet-class.md#addpage)。

- 属性表的[DoModal](../../mfc/reference/cpropertysheet-class.md#domodal)或[创建](../../mfc/reference/cpropertysheet-class.md#create)调用函数。

- 用户已经选择了 （选项到卡式） 此页。

调用`Construct`如果尚未调用的其他类构造函数之一。 `Construct`成员函数很灵活，因为可以保留参数语句为空，然后在代码中指定多个参数和任何时候构造。

必须使用`Construct`当使用数组、 和必须调用`Construct`数组的每个成员，以便数据成员分配适当的值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]

##  <a name="cpropertypage"></a>  CPropertyPage::CPropertyPage

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
使用此页的模板的 ID。

*nIDCaption*<br/>
要放置在此页的选项卡名称的 ID。 如果为 0，名称将来自此页的对话框模板。

*dwSize*<br/>
*lpszTemplateName*指向包含有关此页的模板的名称的字符串。 不能为 NULL。

*nIDHeaderTitle*<br/>
若要将放置在属性页标题的标题位置的名称的 ID。

*nIDHeaderSubTitle*<br/>
若要将放置在属性页标头的副标题位置名称的 ID。

### <a name="remarks"></a>备注

满足所有以下条件时才显示该对象：

- 页已添加到属性表使用[cpropertysheet:: Addpage](../../mfc/reference/cpropertysheet-class.md#addpage)。

- 属性表的[DoModal](../../mfc/reference/cpropertysheet-class.md#domodal)或[创建](../../mfc/reference/cpropertysheet-class.md#create)调用函数。

- 用户已经选择了 （选项到卡式） 此页。

如果你有多个参数 （例如，如果您使用的数组），使用[CPropertySheet::Construct](../../mfc/reference/cpropertysheet-class.md#construct)而不是`CPropertyPage`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]

##  <a name="getpsp"></a>  CPropertyPage::GetPSP

检索 Windows [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2)与关联的结构`CPropertyPage`对象。

```
const PROPSHEETPAGE& GetPSP() const;

PROPSHEETPAGE& GetPSP();
```

### <a name="return-value"></a>返回值

对引用`PROPSHEETPAGE`结构。

##  <a name="m_psp"></a>  CPropertyPage::m_psp

`m_psp` 是一种结构的成员将存储的特征[PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2)。

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>备注

使用此结构在构造之后初始化的属性页的外观。

此结构，包括其成员的列表的详细信息请参阅`PROPSHEETPAGE`Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]

##  <a name="onapply"></a>  CPropertyPage::OnApply

当用户选择确定或立即应用按钮，由框架调用此成员函数。

```
virtual BOOL OnApply();
```

### <a name="return-value"></a>返回值

如果接受所做的更改; 非零值否则为 0。

### <a name="remarks"></a>备注

当框架调用此函数时，接受属性表中的所有属性页上所做的更改，但属性表保留焦点，和`OnApply`，则返回 TRUE （值 1）。 之前`OnApply`可以调用由框架，您必须调用[SetModified](#setmodified)并将其参数设置为 TRUE。 只要用户的属性页上进行了更改，这将激活的立即应用按钮。

重写此成员函数以指定程序在用户单击立即应用按钮时采取什么操作。 重写时，该函数应返回以接受更改的 TRUE 和 FALSE 可阻止更改未生效。

默认实现`OnApply`调用`OnOK`。

当用户按属性表中的立即应用或确定按钮时发送通知消息的详细信息，请参阅[PSN_APPLY](/windows/desktop/Controls/psn-apply) Windows SDK 中。

### <a name="example"></a>示例

  有关示例，请参阅[CPropertyPage::OnOK](#onok)。

##  <a name="oncancel"></a>  CPropertyPage::OnCancel

当选择取消按钮时，由框架调用此成员函数。

```
virtual void OnCancel();
```

### <a name="remarks"></a>备注

重写此成员函数以执行取消按钮操作。 默认值求反所做的任何更改。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]

##  <a name="onkillactive"></a>  CPropertyPage::OnKillActive

当该页不再是活动页时，由框架调用此成员函数。

```
virtual BOOL OnKillActive();
```

### <a name="return-value"></a>返回值

非零，如果数据已更新成功，否则为 0。

### <a name="remarks"></a>备注

重写此成员函数以执行特殊的数据验证任务。

此成员函数的默认实现将从控件的属性页中设置复制到的属性页的成员变量。 如果由于对话框数据验证 (DDV) 错误未成功更新数据，页面将保留焦点。

此成员函数返回成功后，框架将调用的页[OnOK](#onok)函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]

##  <a name="onok"></a>  CPropertyPage::OnOK

由框架调用此成员函数，当用户选择确定或立即应用按钮，框架将调用后立即[OnKillActive](#onkillactive)。

```
virtual void OnOK();
```

### <a name="remarks"></a>备注

当用户选择确定或立即应用按钮时，该框架接收[PSN_APPLY](/windows/desktop/Controls/psn-apply)属性页的通知。 在调用`OnOK`如果调用不会进行[CPropertySheet::PressButton](../../mfc/reference/cpropertysheet-class.md#pressbutton)因为属性页不会在这种情况下发送通知。

重写此成员函数以实现特定于当前处于活动状态的页的其他行为，当用户关闭整个属性表。

此成员函数的默认实现将标记为"清除"以反映数据已在更新页`OnKillActive`函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]

##  <a name="onquerycancel"></a>  CPropertyPage::OnQueryCancel

当用户单击取消按钮和取消之前操作发生时，由框架调用此成员函数。

```
virtual BOOL OnQueryCancel();
```

### <a name="return-value"></a>返回值

返回 FALSE，以避免取消操作或允许它，则返回 TRUE。

### <a name="remarks"></a>备注

重写此成员函数以指定当用户单击取消按钮时，程序采用的操作。

默认实现`OnQueryCancel`，则返回 TRUE。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]

##  <a name="onreset"></a>  CPropertyPage::OnReset

当用户选择取消按钮，由框架调用此成员函数。

```
virtual void OnReset();
```

### <a name="remarks"></a>备注

当框架调用此函数时，到之前选择立即应用按钮用户所做的所有属性页的更改将被丢弃，并在属性表保留焦点。

重写此成员函数以指定当用户单击取消按钮时，程序采用什么操作。

默认实现`OnReset`不执行任何操作。

### <a name="example"></a>示例

  有关示例，请参阅[CPropertyPage::OnCancel](#oncancel)。

##  <a name="onsetactive"></a>  CPropertyPage::OnSetActive

用户选择和成为活动页的页时，由框架调用此成员函数。

```
virtual BOOL OnSetActive();
```

### <a name="return-value"></a>返回值

如果页已成功设置活动状态，则非零值否则为 0。

### <a name="remarks"></a>备注

重写此成员函数以激活页面时执行任务。 此成员函数的重写通常会在更新数据成员，以使其能够使用新数据更新页面控件后调用的默认版本。

默认实现创建的窗口页上，如果不是之前创建，并使其活动页。

### <a name="example"></a>示例

  有关示例，请参阅[CPropertySheet::SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext)。

##  <a name="onwizardback"></a>  CPropertyPage::OnWizardBack

当用户单击向导中后退按钮时，由框架调用此成员函数。

```
virtual LRESULT OnWizardBack();
```

### <a name="return-value"></a>返回值

若要自动前进到下一页，则为 0为-1 以避免页面更改。 若要跳转到下一个以外的页面，返回要显示的对话框的标识符。

### <a name="remarks"></a>备注

重写此成员函数以指定在按下后退按钮时，用户必须执行一些操作。

有关如何使向导类型的属性表的详细信息，请参阅[CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]

##  <a name="onwizardfinish"></a>  CPropertyPage::OnWizardFinish

当用户单击完成按钮在向导中，由框架调用此成员函数。

```
virtual BOOL OnWizardFinish();
```

### <a name="return-value"></a>返回值

属性表被销毁时在向导完成; 如果非零值否则为零。

### <a name="remarks"></a>备注

当用户单击**完成**向导，该框架中的按钮将调用此函数; 当`OnWizardFinish`返回 TRUE （非零值），属性表可以被销毁 （但实际不销毁）。 调用`DestroyWindow`要销毁的属性表。 不要调用`DestroyWindow`从`OnWizardFinish`; 这样做会导致堆损坏或出现其他错误。

您可以重写此成员函数以指定在按下完成按钮时，用户必须执行一些操作。 当重写此函数，返回 FALSE 可阻止属性表被销毁。

当用户在向导属性表中按完成按钮时发送通知消息的详细信息，请参阅[PSN_WIZFINISH](/windows/desktop/Controls/psn-wizfinish) Windows SDK 中。

有关如何使向导类型的属性表的详细信息，请参阅[CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]

[!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]

[!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]

[!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]

##  <a name="onwizardnext"></a>  CPropertyPage::OnWizardNext

当用户单击下一步按钮在向导中，由框架调用此成员函数。

```
virtual LRESULT OnWizardNext();
```

### <a name="return-value"></a>返回值

若要自动前进到下一页，则为 0为-1 以避免页面更改。 若要跳转到下一个以外的页面，返回要显示的对话框的标识符。

### <a name="remarks"></a>备注

重写此成员函数以指定在按下的下一步按钮时，用户必须执行一些操作。

有关如何使向导类型的属性表的详细信息，请参阅[CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]

##  <a name="querysiblings"></a>  CPropertyPage::QuerySiblings

调用此成员函数以将消息转发到属性表中每一页。

```
LRESULT QuerySiblings(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>参数

*wParam*<br/>
指定消息相关的其他信息。

*lParam*<br/>
指定消息相关的其他信息

### <a name="return-value"></a>返回值

从属性表中或 0 中的页的非零值的所有页面都返回的值为 0。

### <a name="remarks"></a>备注

如果页时返回非零值，则属性表不到后续页面发送消息。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]

[!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]

##  <a name="setmodified"></a>  CPropertyPage::SetModified

调用此成员函数可启用或禁用立即应用按钮，根据是否属性页中的设置应该应用到相应的外部对象。

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>参数

*bChanged*<br/>
若要指示自上次应用;，已修改的属性页设置如果为 FALSE，以指示已应用，或应忽略的属性页设置。

### <a name="remarks"></a>备注

该框架使页的"更新"，它是跟踪，请为其调用了的属性页`SetModified( TRUE )`。 将始终启用立即应用按钮，如果调用`SetModified( TRUE )`的页面之一。 在调用时，将禁用立即应用按钮`SetModified( FALSE )`一个页面，但如果没有任何其他页是"更新。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CPropertySheet 类](../../mfc/reference/cpropertysheet-class.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)
