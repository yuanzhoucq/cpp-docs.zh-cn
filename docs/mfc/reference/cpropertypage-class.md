---
title: "CPropertyPage 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPropertyPage
dev_langs:
- C++
helpviewer_keywords:
- property pages, CPropertyPage class
- dialog boxes, tabs
- CPropertyPage class
- tab dialog boxes
ms.assetid: d9000a21-aa81-4530-85d9-f43432afb4dc
caps.latest.revision: 25
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 13fb9befb6d1549493afa6cbed53ec4d41443c3a
ms.lasthandoff: 02/24/2017

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
|[CPropertyPage::CPropertyPage](#cpropertypage)|构造 `CPropertyPage` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CPropertyPage::CancelToClose](#canceltoclose)|更改确定按钮以阅读关闭，并禁用模式属性表的页中无法恢复更改后的取消按钮。|  
|[CPropertyPage::Construct](#construct)|构造 `CPropertyPage` 对象。 使用`Construct`你想要在运行时，来指定参数是否使用数组。|  
|[CPropertyPage::GetPSP](#getpsp)|检索 Windows [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548)的关联结构`CPropertyPage`对象。|  
|[CPropertyPage::OnApply](#onapply)|单击立即应用按钮时，由框架调用。|  
|[CPropertyPage::OnCancel](#oncancel)|单击取消按钮时，由框架调用。|  
|[Cpropertypage:: Onkillactive](#onkillactive)|在当前页不再是活动的页面时由框架调用。 此执行数据验证。|  
|[CPropertyPage::OnOK](#onok)|单击确定、 立即应用，或关闭按钮时由框架调用。|  
|[CPropertyPage::OnQueryCancel](#onquerycancel)|单击取消按钮时，并在取消已经发生之前，由框架调用。|  
|[CPropertyPage::OnReset](#onreset)|单击取消按钮时，由框架调用。|  
|[Cpropertypage:: Onsetactive](#onsetactive)|页上进行的活动页面时由框架调用。|  
|[CPropertyPage::OnWizardBack](#onwizardback)|使用向导类型的属性表时单击后退按钮时由框架调用。|  
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|使用向导类型的属性表时单击完成按钮时由框架调用。|  
|[CPropertyPage::OnWizardNext](#onwizardnext)|使用向导类型的属性表时单击下一步按钮时由框架调用。|  
|[CPropertyPage::QuerySiblings](#querysiblings)|将消息转发到属性表的每一页。|  
|[Cpropertypage:: Setmodified](#setmodified)|调用以激活或停用立即应用按钮。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CPropertyPage::m_psp](#m_psp)|Windows [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548)结构。 提供对基本的属性页上参数的访问。|  
  
## <a name="remarks"></a>备注  
 如与标准对话框，您从派生类`CPropertyPage`为在属性表中每个页。 若要使用`CPropertyPage`-派生的对象，首先创建[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)对象，然后创建一个对象，用于将属性表中每一页。 调用[cpropertysheet:: Addpage](../../mfc/reference/cpropertysheet-class.md#addpage)为每个页的表中，然后通过调用中显示的属性表[cpropertysheet:: Domodal](../../mfc/reference/cpropertysheet-class.md#domodal)模式属性表，或[CPropertySheet::Create](../../mfc/reference/cpropertysheet-class.md#create)为无模式属性表。  
  
 您可以创建一种称为向导，其中包含的属性表具有一系列指导用户完成操作，例如设置设备，或创建时事通讯的步骤的属性页选项卡对话框。 在向导类型选项卡对话框中，属性页没有选项卡上，并且一次只有一个属性页上可见。 而且，而不是让确定和立即应用按钮，向导类型选项卡对话框中具有后退按钮、 一个下一步或完成按钮和取消按钮。  
  
 建立属性表作为向导的详细信息，请参阅[CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。 有关详细信息使用`CPropertyPage`对象，请参阅文章[属性表和属性页](../../mfc/property-sheets-and-property-pages-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `CPropertyPage`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdlgs.h  
  
##  <a name="a-namecanceltoclosea--cpropertypagecanceltoclose"></a><a name="canceltoclose"></a>CPropertyPage::CancelToClose  
 调用此函数后对模式属性表的页中的数据进行了不可恢复的更改。  
  
```  
void CancelToClose();
```  
  
### <a name="remarks"></a>备注  
 此函数会将确定按钮更改为关闭并禁用取消按钮。 此更改不能取消更改是永久的所做的修改用户的警报。  
  
 `CancelToClose`成员函数不会在无模式属性表中，执行任何操作，因为无模式属性表不具有默认情况下的取消按钮。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertyPage::QuerySiblings](#querysiblings)。  
  
##  <a name="a-nameconstructa--cpropertypageconstruct"></a><a name="construct"></a>CPropertyPage::Construct  
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
 使用此页的模板的 ID。  
  
 `nIDCaption`  
 要放置在此页的选项卡名称的 ID。 如果为 0，名称将来自此页的对话框模板。  
  
 `lpszTemplateName`  
 包含以 null 结尾的字符串，表示模板资源的名称。  
  
 `nIDHeaderTitle`  
 要放置在属性页标题的标题位置名称的 ID。 默认情况下，0。  
  
 `nIDHeaderSubTitle`  
 要放置在属性页页眉的副标题位置名称的 ID。 默认情况下，0。  
  
### <a name="remarks"></a>备注  
 在满足所有以下条件时，将显示的对象︰  
  
-   网页已添加到属性表使用[cpropertysheet:: Addpage](../../mfc/reference/cpropertysheet-class.md#addpage)。  
  
-   属性表的[DoModal](../../mfc/reference/cpropertysheet-class.md#domodal)或[创建](../../mfc/reference/cpropertysheet-class.md#create)调用函数。  
  
-   在用户已经选择 （选项为卡式） 此页。  
  
 调用**构造**如果尚未调用其他类构造函数之一。 `Construct`成员函数是灵活，因为您可以将参数语句保留为空，然后在代码中指定多个参数和任何时候构造。  
  
 必须使用`Construct`时使用数组、，必须调用**构造**数组的每个成员，以便数据成员分配适当的值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&112;](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]  
  
##  <a name="a-namecpropertypagea--cpropertypagecpropertypage"></a><a name="cpropertypage"></a>CPropertyPage::CPropertyPage  
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
 使用此页的模板的 ID。  
  
 `nIDCaption`  
 要放置在此页的选项卡名称的 ID。 如果为 0，名称将来自此页的对话框模板。  
  
 `dwSize`  
 `lpszTemplateName`  
 指向一个包含此页的模板的名称的字符串。 不能为**NULL**。  
  
 `nIDHeaderTitle`  
 要放置在属性页标题的标题位置名称的 ID。  
  
 `nIDHeaderSubTitle`  
 要放置在属性页页眉的副标题位置名称的 ID。  
  
### <a name="remarks"></a>备注  
 在满足所有以下条件时，将显示的对象︰  
  
-   网页已添加到属性表使用[cpropertysheet:: Addpage](../../mfc/reference/cpropertysheet-class.md#addpage)。  
  
-   属性表的[DoModal](../../mfc/reference/cpropertysheet-class.md#domodal)或[创建](../../mfc/reference/cpropertysheet-class.md#create)调用函数。  
  
-   在用户已经选择 （选项为卡式） 此页。  
  
 如果您具有多个参数 （例如，如果您使用的一个数组），使用[CPropertySheet::Construct](../../mfc/reference/cpropertysheet-class.md#construct)而不是`CPropertyPage`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&113;](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]  
  
##  <a name="a-namegetpspa--cpropertypagegetpsp"></a><a name="getpsp"></a>CPropertyPage::GetPSP  
 检索 Windows [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548)的关联结构`CPropertyPage`对象。  
  
```  
const PROPSHEETPAGE& GetPSP() const;  
  
PROPSHEETPAGE& GetPSP();
```  
  
### <a name="return-value"></a>返回值  
 对引用**PROPSHEETPAGE**结构。  
  
##  <a name="a-namempspa--cpropertypagempsp"></a><a name="m_psp"></a>CPropertyPage::m_psp  
 `m_psp`是一种结构的成员将存储的特征[PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548)。  
  
```  
PROPSHEETPAGE m_psp;  
```  
  
### <a name="remarks"></a>备注  
 使用此结构在构造之后初始化属性页的外观。  
  
 此结构，包括其成员的列表的详细信息请参阅**PROPSHEETPAGE**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&128;](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]  
  
##  <a name="a-nameonapplya--cpropertypageonapply"></a><a name="onapply"></a>CPropertyPage::OnApply  
 在用户选择确定或立即应用按钮时，将由框架调用此成员函数。  
  
```  
virtual BOOL OnApply();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果接受所做的更改;否则为 0。  
  
### <a name="remarks"></a>备注  
 当框架调用此函数时，接受在属性表中的所有属性页上所做的更改，但属性表保留焦点，和`OnApply`返回**TRUE** （值 1）。 之前`OnApply`可以调用由框架，您必须调用[SetModified](#setmodified)并将其参数设置为**TRUE**。 一旦用户进行了更改的属性页上，这将激活立即应用按钮。  
  
 重写该成员函数以指定在用户单击立即应用按钮时，考虑您的程序的操作。 重写时，该函数应返回**TRUE**以接受更改和**FALSE**防止更改生效。  
  
 默认实现`OnApply`调用`OnOK`。  
  
 当用户按下立即应用或确定按钮在属性表中发送通知消息的详细信息，请参阅[PSN_APPLY](http://msdn.microsoft.com/library/windows/desktop/bb774552)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertyPage::OnOK](#onok)。  
  
##  <a name="a-nameoncancela--cpropertypageoncancel"></a><a name="oncancel"></a>CPropertyPage::OnCancel  
 当选择取消按钮时，将由框架调用此成员函数。  
  
```  
virtual void OnCancel();
```  
  
### <a name="remarks"></a>备注  
 重写该成员函数以执行取消按钮操作。 默认值求反所做的任何更改。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&114;](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]  
  
##  <a name="a-nameonkillactivea--cpropertypageonkillactive"></a><a name="onkillactive"></a>Cpropertypage:: Onkillactive  
 在页上不再是活动的页面时，将由框架调用此成员函数。  
  
```  
virtual BOOL OnKillActive();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果数据更新成功，否则为 0。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以执行特殊的数据验证任务。  
  
 此成员函数的默认实现将设置从属性页中的控件复制到属性页上的成员变量。 如果由于对话框数据验证 (DDV) 错误未成功更新数据，页上将保留焦点。  
  
 此成员函数将返回成功后，框架将调用该页面的[OnOK](#onok)函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&115;](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]  
  
##  <a name="a-nameonoka--cpropertypageonok"></a><a name="onok"></a>CPropertyPage::OnOK  
 由框架调用此成员函数，当用户选择确定或立即应用按钮，框架将调用后立即[OnKillActive](#onkillactive)。  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>备注  
 当用户选择确定或立即应用按钮时，框架会收到[PSN_APPLY](http://msdn.microsoft.com/library/windows/desktop/bb774552)从属性页上的通知。 对调用`OnOK`如果调用不会进行[CPropertySheet::PressButton](../../mfc/reference/cpropertysheet-class.md#pressbutton)因为属性页上没有这种情况下发送通知。  
  
 重写该成员函数以实现特定于当前处于活动状态的页的其他行为，当用户关闭整个属性表。  
  
 此成员函数的默认实现将标记为"clean"表示反映在已更新的数据页`OnKillActive`函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView 排行榜的 #&116;](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]  
  
##  <a name="a-nameonquerycancela--cpropertypageonquerycancel"></a><a name="onquerycancel"></a>CPropertyPage::OnQueryCancel  
 当用户单击取消按钮，在取消之前采取任何措施的位置，将由框架调用此成员函数。  
  
```  
virtual BOOL OnQueryCancel();
```  
  
### <a name="return-value"></a>返回值  
 返回**FALSE**以避免取消操作或 TRUE 将允许它。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以指定该程序将在用户单击取消按钮时的操作。  
  
 默认实现`OnQueryCancel`返回**TRUE**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&117;](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]  
  
##  <a name="a-nameonreseta--cpropertypageonreset"></a><a name="onreset"></a>CPropertyPage::OnReset  
 在用户选择取消按钮时，将由框架调用此成员函数。  
  
```  
virtual void OnReset();
```  
  
### <a name="remarks"></a>备注  
 当框架调用此函数时，对之前选择立即应用按钮的用户所做的所有属性页的更改将被放弃，且属性表中保留了焦点。  
  
 重写该成员函数以指定该程序将在用户单击取消按钮时的操作。  
  
 默认实现`OnReset`不执行任何操作。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertyPage::OnCancel](#oncancel)。  
  
##  <a name="a-nameonsetactivea--cpropertypageonsetactive"></a><a name="onsetactive"></a>Cpropertypage:: Onsetactive  
 由用户选择和成为活动页面页时，将由框架调用此成员函数。  
  
```  
virtual BOOL OnSetActive();
```  
  
### <a name="return-value"></a>返回值  
 如果页已成功设置活动状态，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以激活页面时执行的任务。 重写该成员函数通常会在更新数据的成员，以允许应用程序使用最新数据更新页面控件后调用的默认版本。  
  
 默认实现创建窗口中的页上，如果不是以前创建的并将其当前页。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertySheet::SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext)。  
  
##  <a name="a-nameonwizardbacka--cpropertypageonwizardback"></a><a name="onwizardback"></a>CPropertyPage::OnWizardBack  
 当用户单击后退按钮在向导中，将由框架调用此成员函数。  
  
```  
virtual LRESULT OnWizardBack();
```  
  
### <a name="return-value"></a>返回值  
 0，则自动前进到下一个页面;为-1，使页面无法更改。 若要跳转到下一个以外的页面，请返回对话框中显示的标识符。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以指定在按下后退按钮时，用户必须执行一些操作。  
  
 有关如何使向导类型的属性表的详细信息，请参阅[CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&118;](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]  
  
##  <a name="a-nameonwizardfinisha--cpropertypageonwizardfinish"></a><a name="onwizardfinish"></a>CPropertyPage::OnWizardFinish  
 当用户单击完成按钮在向导中，将由框架调用此成员函数。  
  
```  
virtual BOOL OnWizardFinish();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果属性表被销毁时在向导完成;否则为零。  
  
### <a name="remarks"></a>备注  
 当用户单击**完成**按钮在向导中，框架将调用此函数; 当`OnWizardFinish`返回**TRUE** （非零值） 属性表可以将其销毁 （但实际上不销毁）。 调用`DestroyWindow`要销毁的属性表。 不要调用`DestroyWindow`从`OnWizardFinish`; 这样做将导致堆损坏或出现其他错误。  
  
 您可以重写该成员函数以指定在按下完成按钮时，用户必须执行一些操作。 当重写此函数，返回**FALSE**以防止属性表被销毁。  
  
 当用户在向导属性表中按完成按钮时，发送的通知消息的详细信息，请参阅[PSN_WIZFINISH](http://msdn.microsoft.com/library/windows/desktop/bb774571)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 有关如何使向导类型的属性表的详细信息，请参阅[CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&119;](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&120;](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&121;](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&122;](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]  
  
##  <a name="a-nameonwizardnexta--cpropertypageonwizardnext"></a><a name="onwizardnext"></a>CPropertyPage::OnWizardNext  
 当用户单击下一步按钮在向导中，将由框架调用此成员函数。  
  
```  
virtual LRESULT OnWizardNext();
```  
  
### <a name="return-value"></a>返回值  
 0，则自动前进到下一个页面;为-1，使页面无法更改。 若要跳转到下一个以外的页面，请返回对话框中显示的标识符。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以指定在按下下一步按钮时，用户必须执行一些操作。  
  
 有关如何使向导类型的属性表的详细信息，请参阅[CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&123;](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]  
  
##  <a name="a-namequerysiblingsa--cpropertypagequerysiblings"></a><a name="querysiblings"></a>CPropertyPage::QuerySiblings  
 调用该成员函数以将消息转发到属性表中的每一页。  
  
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
 从页中的属性表中，或者，如果非零值的所有页面都返回值为 0。  
  
### <a name="remarks"></a>备注  
 如果页面返回非零值，属性表不向后续页发送消息。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&124;](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&125;](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&126;](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]  
  
##  <a name="a-namesetmodifieda--cpropertypagesetmodified"></a><a name="setmodified"></a>Cpropertypage:: Setmodified  
 调用该成员函数以启用或禁用立即应用按钮，根据是否在属性页中的设置应该应用于相应的外部对象。  
  
```  
void SetModified(BOOL bChanged = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bChanged`  
 **TRUE**以指示是否尚未应用了这些; 的上次修改的属性页设置**FALSE**以指示属性页设置尚未应用，还是应忽略。  
  
### <a name="remarks"></a>备注  
 该框架使所属页的"脏"，它是跟踪、 为其调用了属性页**SetModified (TRUE)**。 如果调用将始终启用立即应用按钮**SetModified (TRUE)**的页面之一。 将禁用立即应用按钮，当您调用**SetModified (FALSE)**之一的页面，但是仅当无其他两个页面"脏"。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&127;](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 CMNCTRL1](../../visual-cpp-samples.md)   
 [MFC 示例 CMNCTRL2](../../visual-cpp-samples.md)   
 [MFC 示例 PROPDLG](../../visual-cpp-samples.md)   
 [MFC 示例 SNAPVW](../../visual-cpp-samples.md)   
 [CDialog 类](../../mfc/reference/cdialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPropertySheet 类](../../mfc/reference/cpropertysheet-class.md)   
 [CDialog 类](../../mfc/reference/cdialog-class.md)

