---
title: CPropertyPage 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 434a0b428199b7c2298815523517097aeee2ab47
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
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
|[CPropertyPage::CancelToClose](#canceltoclose)|更改读取关闭，确定按钮并不可恢复模式属性表的页中更改后禁用取消按钮。|  
|[CPropertyPage::Construct](#construct)|构造 `CPropertyPage` 对象。 使用`Construct`如果你想要在运行时，指定你的参数，或如果你使用的数组。|  
|[CPropertyPage::GetPSP](#getpsp)|检索 Windows [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548)与相关的结构`CPropertyPage`对象。|  
|[CPropertyPage::OnApply](#onapply)|单击立即应用按钮时，由框架调用。|  
|[CPropertyPage::OnCancel](#oncancel)|单击取消按钮时，由框架调用。|  
|[Cpropertypage:: Onkillactive](#onkillactive)|当前页不再是活动的页面时，由框架调用。 执行数据验证此处。|  
|[CPropertyPage::OnOK](#onok)|单击确定，立即应用，或关闭按钮时，由框架调用。|  
|[CPropertyPage::OnQueryCancel](#onquerycancel)|单击取消按钮后，并在取消发生之前，由框架调用。|  
|[CPropertyPage::OnReset](#onreset)|单击取消按钮时，由框架调用。|  
|[Cpropertypage:: Onsetactive](#onsetactive)|页进行的活动页面时，由框架调用。|  
|[CPropertyPage::OnWizardBack](#onwizardback)|使用向导类型的属性表时单击后退按钮时，由框架调用。|  
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|使用向导类型的属性表时单击完成按钮时，由框架调用。|  
|[CPropertyPage::OnWizardNext](#onwizardnext)|使用向导类型的属性表时单击下一步按钮时，由框架调用。|  
|[CPropertyPage::QuerySiblings](#querysiblings)|将转发到属性表的每个页面的消息。|  
|[Cpropertypage:: Setmodified](#setmodified)|调用以激活或停用立即应用按钮。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CPropertyPage::m_psp](#m_psp)|Windows [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548)结构。 提供对基本的属性页参数访问。|  
  
## <a name="remarks"></a>备注  
 如与标准对话框框中，你从派生类`CPropertyPage`属性表中每一页。 若要使用`CPropertyPage`-派生的对象，首先创建[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)对象，然后创建出现在属性表中每个页的对象。 调用[cpropertysheet:: Addpage](../../mfc/reference/cpropertysheet-class.md#addpage)每个工作表，在页上，然后通过调用显示属性表[CPropertySheet::DoModal](../../mfc/reference/cpropertysheet-class.md#domodal)模式属性表，或[CPropertySheet::创建](../../mfc/reference/cpropertysheet-class.md#create)无模式属性表。  
  
 你可以创建一种称为向导，指导用户完成了操作，例如设置设备，或创建新闻稿的步骤的属性页中的序列与包含属性表的选项卡对话框。 在向导类型选项卡对话框中，属性页没有选项卡上，且仅一个属性页可见一次。 此外，而不是有确定和立即应用按钮，向导类型选项卡对话框具有后退按钮、 下一步或完成按钮和取消按钮。  
  
 建立属性表作为向导的详细信息，请参阅[CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。 有关详细信息使用`CPropertyPage`对象，请参阅文章[属性表和属性页](../../mfc/property-sheets-and-property-pages-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `CPropertyPage`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdlgs.h  
  
##  <a name="canceltoclose"></a>  CPropertyPage::CancelToClose  
 对模式属性表的页面中的数据进行了不可恢复的更改后调用此函数。  
  
```  
void CancelToClose();
```  
  
### <a name="remarks"></a>备注  
 此函数将会将确定按钮更改为关闭并禁用取消按钮。 此更改不能取消更改是永久的修改用户的警报。  
  
 `CancelToClose`成员函数不会在无模式属性表中，执行任何操作，因为无模式属性表在默认情况下没有取消按钮。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertyPage::QuerySiblings](#querysiblings)。  
  
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
 `nIDTemplate`  
 为此页使用的模板的 ID。  
  
 `nIDCaption`  
 要放入此页的选项卡名称的 ID。 如果为 0，名称将取自对话框模板的此页。  
  
 `lpszTemplateName`  
 包含一个以 null 结尾的字符串，它的模板资源名称。  
  
 `nIDHeaderTitle`  
 要放入的属性页标题的标题位置名称的 ID。 默认情况下，0。  
  
 `nIDHeaderSubTitle`  
 要放入的属性页页眉的副标题位置名称的 ID。 默认情况下，0。  
  
### <a name="remarks"></a>备注  
 在满足所有以下条件时，将显示的对象：  
  
-   页已添加到属性表使用[cpropertysheet:: Addpage](../../mfc/reference/cpropertysheet-class.md#addpage)。  
  
-   属性表的[DoModal](../../mfc/reference/cpropertysheet-class.md#domodal)或[创建](../../mfc/reference/cpropertysheet-class.md#create)调用函数。  
  
-   用户已选定 （选项到卡式） 此页。  
  
 调用**构造**如果尚未调用的其他类构造函数之一。 `Construct`成员函数是灵活，因为您可以将参数语句留空，然后在代码中指定多个参数和任何时候的构造。  
  
 必须使用`Construct`当处理数组，并且你必须调用**构造**数组的每个成员，以便数据成员分配适当的值。  
  
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
 `nIDTemplate`  
 为此页使用的模板的 ID。  
  
 `nIDCaption`  
 要放入此页的选项卡名称的 ID。 如果为 0，名称将取自对话框模板的此页。  
  
 `dwSize`  
 `lpszTemplateName`  
 指向包含模板的此页的名称的字符串。 不能为**NULL**。  
  
 `nIDHeaderTitle`  
 要放入的属性页标题的标题位置名称的 ID。  
  
 `nIDHeaderSubTitle`  
 要放入的属性页页眉的副标题位置名称的 ID。  
  
### <a name="remarks"></a>备注  
 在满足所有以下条件时，将显示的对象：  
  
-   页已添加到属性表使用[cpropertysheet:: Addpage](../../mfc/reference/cpropertysheet-class.md#addpage)。  
  
-   属性表的[DoModal](../../mfc/reference/cpropertysheet-class.md#domodal)或[创建](../../mfc/reference/cpropertysheet-class.md#create)调用函数。  
  
-   用户已选定 （选项到卡式） 此页。  
  
 如果你有多个参数 （例如，如果你使用的数组），使用[CPropertySheet::Construct](../../mfc/reference/cpropertysheet-class.md#construct)而不是`CPropertyPage`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]  
  
##  <a name="getpsp"></a>  CPropertyPage::GetPSP  
 检索 Windows [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548)与相关的结构`CPropertyPage`对象。  
  
```  
const PROPSHEETPAGE& GetPSP() const;  
  
PROPSHEETPAGE& GetPSP();
```  
  
### <a name="return-value"></a>返回值  
 对引用**PROPSHEETPAGE**结构。  
  
##  <a name="m_psp"></a>  CPropertyPage::m_psp  
 `m_psp` 是其成员存储的特征的结构[PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548)。  
  
```  
PROPSHEETPAGE m_psp;  
```  
  
### <a name="remarks"></a>备注  
 使用此结构在构造之后初始化属性页的外观。  
  
 此结构，包括其成员的列表的详细信息请参阅**PROPSHEETPAGE** Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]  
  
##  <a name="onapply"></a>  CPropertyPage::OnApply  
 当用户选择确定或立即应用按钮，将由框架调用此成员函数。  
  
```  
virtual BOOL OnApply();
```  
  
### <a name="return-value"></a>返回值  
 如果接受所做的更改; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 当框架调用此函数时，接受属性表中的所有属性页上所做的更改，但属性表保留焦点，和`OnApply`返回**TRUE** (value 1)。 之前`OnApply`可以调用由框架，你必须已调用[SetModified](#setmodified)并将其参数设置为**TRUE**。 只要用户的属性页上进行了更改，这将激活立即应用按钮。  
  
 重写该成员函数以指定你的程序将在用户单击立即应用按钮时的操作。 重写时，该函数应返回**TRUE**接受更改和**FALSE**以防止更改生效。  
  
 默认实现`OnApply`调用`OnOK`。  
  
 有关在用户按属性表中的立即应用或确定按钮时发送的通知消息的详细信息，请参阅[PSN_APPLY](http://msdn.microsoft.com/library/windows/desktop/bb774552) Windows SDK 中。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertyPage::OnOK](#onok)。  
  
##  <a name="oncancel"></a>  CPropertyPage::OnCancel  
 当选择取消按钮时，将由框架调用此成员函数。  
  
```  
virtual void OnCancel();
```  
  
### <a name="remarks"></a>备注  
 重写该成员函数以执行取消按钮操作。 默认值对已进行了任何更改求反。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]  
  
##  <a name="onkillactive"></a>  Cpropertypage:: Onkillactive  
 当该页不再是活动的页时，将由框架调用此成员函数。  
  
```  
virtual BOOL OnKillActive();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果数据已更新成功，否则为 0。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以执行特殊的数据验证任务。  
  
 此成员函数的默认实现将设置复制到成员变量的属性页中的属性页的控件。 如果由于对话框数据验证 (DDV) 错误未成功更新数据，页面将保留焦点。  
  
 此成员函数将返回成功后，框架将调用该页面的[OnOK](#onok)函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]  
  
##  <a name="onok"></a>  CPropertyPage::OnOK  
 由框架调用此成员函数，当用户选择确定或立即应用按钮，框架调用后立即[OnKillActive](#onkillactive)。  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>备注  
 当用户选择确定或立即应用按钮时，框架会收到[PSN_APPLY](http://msdn.microsoft.com/library/windows/desktop/bb774552)在属性页上的通知。 调用`OnOK`如果调用不会进行[CPropertySheet::PressButton](../../mfc/reference/cpropertysheet-class.md#pressbutton)因为属性页不会在这种情况下发送通知。  
  
 重写该成员函数以实现特定于当前活动页的其他行为，当用户关闭整个属性表。  
  
 此成员函数的默认实现将标记为"清除"以反映中已更新的数据页`OnKillActive`函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]  
  
##  <a name="onquerycancel"></a>  CPropertyPage::OnQueryCancel  
 当用户单击取消按钮和之前取消操作发生时，将由框架调用此成员函数。  
  
```  
virtual BOOL OnQueryCancel();
```  
  
### <a name="return-value"></a>返回值  
 返回**FALSE**以避免取消操作或 TRUE 将允许它。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以指定程序采用当用户单击取消按钮的操作。  
  
 默认实现`OnQueryCancel`返回**TRUE**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]  
  
##  <a name="onreset"></a>  CPropertyPage::OnReset  
 当用户选择取消按钮，将由框架调用此成员函数。  
  
```  
virtual void OnReset();
```  
  
### <a name="remarks"></a>备注  
 当框架调用此函数时，到之前选择立即应用按钮用户所做的所有属性页面的更改将被丢弃，且属性表保留焦点。  
  
 重写该成员函数以指定程序采用当用户单击取消按钮的操作。  
  
 默认实现`OnReset`不执行任何操作。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertyPage::OnCancel](#oncancel)。  
  
##  <a name="onsetactive"></a>  Cpropertypage:: Onsetactive  
 由用户选择和成为活动页面页时，将由框架调用此成员函数。  
  
```  
virtual BOOL OnSetActive();
```  
  
### <a name="return-value"></a>返回值  
 如果页已成功设置活动状态，则非零否则为 0。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以激活页时执行任务。 通常，此成员函数的重写将在更新数据成员，以允许应用程序使用的新数据更新页面控件后调用的默认版本。  
  
 默认实现创建的窗口页上，如果不是以前创建了，并使其活动页面。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertySheet::SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext)。  
  
##  <a name="onwizardback"></a>  CPropertyPage::OnWizardBack  
 当用户单击向导中后退按钮时，将由框架调用此成员函数。  
  
```  
virtual LRESULT OnWizardBack();
```  
  
### <a name="return-value"></a>返回值  
 若要自动前进到下一页，则为 0-1 以使页面无法更改。 若要跳转到下一步以外的页，请返回对话框中要显示的标识符。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以指定按下后退按钮时，用户必须执行一些操作。  
  
 有关如何使向导类型的属性表的详细信息，请参阅[CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]  
  
##  <a name="onwizardfinish"></a>  CPropertyPage::OnWizardFinish  
 当用户单击向导中完成按钮时，将由框架调用此成员函数。  
  
```  
virtual BOOL OnWizardFinish();
```  
  
### <a name="return-value"></a>返回值  
 如果在向导完成后; 销毁属性表则不为否则为零。  
  
### <a name="remarks"></a>备注  
 当用户单击**完成**按钮在向导中，框架会调用此函数; 当`OnWizardFinish`返回**TRUE** （非零值），属性表可以将其销毁 （但不实际销毁）。 调用`DestroyWindow`销毁属性表。 不要调用`DestroyWindow`从`OnWizardFinish`; 这样做将导致堆损坏或出现其他错误。  
  
 你可以重写该成员函数以指定按下完成按钮时，用户必须执行一些操作。 当重写此函数，返回**FALSE**以防止属性表被销毁。  
  
 有关用户向导属性表中按完成按钮时发送的通知消息的详细信息，请参阅[PSN_WIZFINISH](http://msdn.microsoft.com/library/windows/desktop/bb774571) Windows SDK 中。  
  
 有关如何使向导类型的属性表的详细信息，请参阅[CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]  
  
##  <a name="onwizardnext"></a>  CPropertyPage::OnWizardNext  
 当用户单击向导中的下一步按钮时，将由框架调用此成员函数。  
  
```  
virtual LRESULT OnWizardNext();
```  
  
### <a name="return-value"></a>返回值  
 若要自动前进到下一页，则为 0-1 以使页面无法更改。 若要跳转到下一步以外的页，请返回对话框中要显示的标识符。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以指定按下的下一步按钮时，用户必须执行一些操作。  
  
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
 `wParam`  
 指定消息相关的其他信息。  
  
 `lParam`  
 指定消息相关的其他信息  
  
### <a name="return-value"></a>返回值  
 从属性表中或 0 中的页的非零值的所有页面都返回值为 0。  
  
### <a name="remarks"></a>备注  
 如果页面返回非零值，属性表不后续页中发送消息。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]  
  
##  <a name="setmodified"></a>  Cpropertypage:: Setmodified  
 调用此成员函数以启用或禁用立即应用按钮，基于是否属性页中的设置应该应用于相应的外部对象。  
  
```  
void SetModified(BOOL bChanged = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bChanged`  
 **TRUE**以指示是否尚未中应用; 的上次修改的属性页设置**FALSE**以指示已应用，或应忽略的属性页设置。  
  
### <a name="remarks"></a>备注  
 框架将的跟踪该页面的"脏"，它是、 属性页，为其调用了**SetModified (TRUE)**。 将始终启用立即应用按钮，如果调用**SetModified (TRUE)** 页面之一。 在调用时，将禁用立即应用按钮**SetModified (FALSE)** 之一的页面，但只有无其他页面"脏"。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 CMNCTRL1](../../visual-cpp-samples.md)   
 [MFC 示例 CMNCTRL2](../../visual-cpp-samples.md)   
 [MFC 示例 PROPDLG](../../visual-cpp-samples.md)   
 [MFC 示例 SNAPVW](../../visual-cpp-samples.md)   
 [CDialog 类](../../mfc/reference/cdialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPropertySheet 类](../../mfc/reference/cpropertysheet-class.md)   
 [CDialog 类](../../mfc/reference/cdialog-class.md)
