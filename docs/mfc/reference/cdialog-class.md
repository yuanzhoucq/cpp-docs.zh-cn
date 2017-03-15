---
title: "CDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDialog
dev_langs:
- C++
helpviewer_keywords:
- modal dialog boxes, creating
- MFC dialog boxes, base class
- modeless dialog boxes, creating
- modeless dialog boxes, displaying
- CDialog class
ms.assetid: ca64b77e-2cd2-47e3-8eff-c2645ad578f9
caps.latest.revision: 23
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
ms.openlocfilehash: 0944d815e8aca591f2a09c09af60fa591a9b1a6d
ms.lasthandoff: 02/24/2017

---
# <a name="cdialog-class"></a>CDialog 类
用于在屏幕上显示对话框的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class CDialog : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CDialog::CDialog](#cdialog)|构造 `CDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CDialog::Create](#create)|初始化`CDialog`对象。 创建无模式对话框，并将其附加到`CDialog`对象。|  
|[CDialog::CreateIndirect](#createindirect)|从内存中的对话框模板 （而不是基于资源） 来创建无模式对话框。|  
|[CDialog::DoModal](#domodal)|调用模式对话框并返回完成。|  
|[CDialog::EndDialog](#enddialog)|关闭一个模式对话框。|  
|[CDialog::GetDefID](#getdefid)|获取对话框中的默认按钮控件的 ID。|  
|[CDialog::GotoDlgCtrl](#gotodlgctrl)|将焦点移到指定的对话框控件在对话框中。|  
|[CDialog::InitModalIndirect](#initmodalindirect)|（而不是基于资源） 从内存中的对话框模板创建模式对话框。 参数存储该函数之前`DoModal`调用。|  
|[CDialog::MapDialogRect](#mapdialogrect)|将矩形的对话框单位转换为屏幕单位。|  
|[CDialog::NextDlgCtrl](#nextdlgctrl)|将焦点移到下一个对话框中控件在对话框中。|  
|[CDialog::OnInitDialog](#oninitdialog)|重写以增加对话框中初始化。|  
|[CDialog::OnSetFont](#onsetfont)|重写以指定对话框的控件是用于绘制文本的字体。|  
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|将焦点移至上一个对话框中控件在对话框中。|  
|[CDialog::SetDefID](#setdefid)|更改为指定按钮的对话框中的默认按钮控件。|  
|[CDialog::SetHelpID](#sethelpid)|设置对话框中的上下文相关帮助 ID。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CDialog::OnCancel](#oncancel)|重写以执行取消按钮或 ESC 键操作。 关闭对话框，默认值和**DoModal**返回**IDCANCEL**。|  
|[CDialog::OnOK](#onok)|重写以执行在模式对话框中的确定按钮的操作。 关闭对话框，默认值和`DoModal`返回**IDOK**。|  
  
## <a name="remarks"></a>备注  
 对话框有两种类型︰ 模式和无模式。 在应用程序继续之前，用户必须关闭一个模式对话框。 无模式对话框允许用户以显示该对话框并返回到另一项任务而无需取消或删除对话框。  
  
 一个`CDialog`对象是对话框模板的组合和`CDialog`的派生类。 使用对话框编辑器来创建对话框模板，并将其存储在一个资源，然后添加类向导用于创建派生自的类`CDialog`。  
  
 对话框中，与任何其他窗口一样接收来自 Windows 消息。 在对话框中，您特别感兴趣，因为它是用户与您的对话框交互的方式处理来自对话框的控件的通知消息。 使用属性窗口句柄，而且它需要哪些消息将适当的消息映射条目和消息处理程序成员函数向类添加为您的选择。 只需编写特定于应用程序代码中处理成员函数。  
  
 如果您愿意，您总是可以编写消息映射项和成员函数手动。  
  
 中除最普通的对话框中的所有，您将成员变量添加到派生的对话框类来存储用户在对话框的控件中输入的数据或显示的用户数据。 可以使用添加变量向导创建成员变量并将它们与控件关联。 一次选择变量类型和允许的每个变量的值的范围。 代码向导将成员变量添加到您在派生的对话框类。  
  
 数据映射生成以自动处理的成员变量和对话框的控件之间的数据交换。 数据映射提供函数来初始化具有适当的值的对话框中的控件，检索数据，并验证数据。  
  
 若要创建模式对话框中，构造使用派生的对话框类的构造函数的堆栈上的对象，然后调用`DoModal`来创建对话框窗口，其控件。 如果你想要创建无模式对话框，则调用**创建**自己的对话框类的构造函数中。  
  
 您还可以创建一个模板在内存中使用[DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394)数据结构中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 在构造之后`CDialog`对象，请调用[CreateIndirect](#createindirect)若要创建无模式对话框中，或者调用[InitModalIndirect](#initmodalindirect)和[DoModal](#domodal)创建模式对话框。  
  
 中的重写编写交换和验证数据映射`CWnd::DoDataExchange`，它将添加到新的对话框类。 请参阅[DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)成员函数在`CWnd`有关的交换和验证功能的详细信息。  
  
 程序员和框架调用`DoDataExchange`间接通过调用[CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)。  
  
 框架将调用`UpdateData`当用户单击确定按钮以关闭一个模式对话框。 （不会检索数据如果单击取消按钮。）默认实现[OnInitDialog](#oninitdialog)还会调用`UpdateData`来设置控件的初始值。 您通常可重写`OnInitDialog`来进一步初始化控件。 `OnInitDialog`创建所有对话框控件并只是对话框框中显示之前之后调用。  
  
 您可以调用`CWnd::UpdateData`随时模式或无模式对话框执行的过程。  
  
 如果您手动开发一个对话框，您需要将成员变量添加到派生的对话框类自己，并添加成员函数来设置或获取这些值。  
  
 当用户按确定或取消按钮，或当您的代码调用模式对话框自动关闭`EndDialog`成员函数。  
  
 当实现无模式对话框时，始终重写`OnCancel`成员函数，并调用`DestroyWindow`从在其中。 不调用基类`CDialog::OnCancel`，这是因为它调用`EndDialog`，这将使对话框中不可见，但不是会破坏。 您还应该重写`PostNcDestroy`为要删除的无模式对话框**这**，原因是无模式对话框通常会分配与**新**。 有模式对话框通常在框架上构造，但不需要`PostNcDestroy`清理。  
  
 有关详细信息`CDialog`，请参阅︰  
  
- [对话框](../../mfc/dialog-boxes.md)  
  
-   知识库文章 Q262954︰ 如何︰ 使用滚动条创建可调整其大小的对话框  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDialog`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="a-namecdialoga--cdialogcdialog"></a><a name="cdialog"></a>CDialog::CDialog  
 若要构造的基于资源的模式对话框中，请调用任一公共形式的构造函数。  
  
```  
explicit CDialog(
    LPCTSTR lpszTemplateName,  
    CWnd* pParentWnd = NULL);

 
explicit CDialog(
    UINT nIDTemplate,  
    CWnd* pParentWnd = NULL);  
  
CDialog();
```  
  
### <a name="parameters"></a>参数  
 `lpszTemplateName`  
 包含以 null 结尾的字符串，对话框模板资源的名称。  
  
 `nIDTemplate`  
 包含对话框模板资源的 ID 号。  
  
 `pParentWnd`  
 指向父或所有者窗口对象 (类型的[CWnd](../../mfc/reference/cwnd-class.md)) 对话框对象所属。 如果它是**NULL**，对话框对象的父窗口设置为主应用程序窗口中。  
  
### <a name="remarks"></a>备注  
 一种形式的构造函数由模板名称提供到对话框资源的访问。 另一个构造函数提供的模板 ID 号的访问通常具有**IDD_**前缀 (例如，IDD_DIALOG1)。  
  
 若要构造一个模式对话框，可从内存中的模板，首先调用无参数的、 受保护的构造函数，然后调用`InitModalIndirect`。  
  
 与上述方法之一，构造一个模式对话框后，调用`DoModal`。  
  
 若要构造的无模式对话框，请使用受保护的形式的`CDialog`构造函数。 构造函数得到保护，因为必须派生您自己的对话框类来实现无模式对话框。 无模式对话框的构造是一个两步过程。 第一次调用构造函数;然后，调用**创建**成员函数来创建基于资源的对话框中，或调用`CreateIndirect`以从内存中的模板创建对话框。  
  
##  <a name="a-namecreatea--cdialogcreate"></a><a name="create"></a>CDialog::Create  
 调用**创建**若要创建无模式对话框中使用对话框模板资源。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszTemplateName,  
    CWnd* pParentWnd = NULL);

 
virtual BOOL Create(
    UINT nIDTemplate,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszTemplateName`  
 包含以 null 结尾的字符串，对话框模板资源的名称。  
  
 `pParentWnd`  
 指向父窗口对象 (类型的[CWnd](../../mfc/reference/cwnd-class.md)) 对话框对象所属。 如果它是**NULL**，对话框对象的父窗口设置为主应用程序窗口中。  
  
 `nIDTemplate`  
 包含对话框模板资源的 ID 号。  
  
### <a name="return-value"></a>返回值  
 这两种形式返回非零，如果成功，则对话框中创建和初始化否则为 0。  
  
### <a name="remarks"></a>备注  
 你可以放置到调用**创建**的构造函数或调用内部调用此构造函数之后。  
  
 两种形式的**创建**按模板名称或模板 ID 号 (例如，IDD_DIALOG1) 为到对话框模板资源的访问而提供成员函数。  
  
 对于任一窗体，将指针传递到父窗口对象。 如果`pParentWnd`是**NULL**，对话框中将使用其父窗口或所有者窗口设置为主应用程序窗口中创建。  
  
 **创建**成员函数将创建该对话框后立即返回。  
  
 使用**WS_VISIBLE**如对话框中创建的父窗口时应显示在对话框模板中的样式。 否则，必须调用`ShowWindow`。 进一步对话框框样式和他们的应用程序，请参阅[DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]和[窗口样式](../../mfc/reference/window-styles.md)中*MFC 参考*。  
  
 使用`CWnd::DestroyWindow`函数来销毁对话框中创建的**创建**函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog #&62;](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]  
  
##  <a name="a-namecreateindirecta--cdialogcreateindirect"></a><a name="createindirect"></a>CDialog::CreateIndirect  
 调用该成员函数以从内存中对话框模板创建无模式对话框。  
  
```  
virtual BOOL CreateIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,  
    CWnd* pParentWnd = NULL,  
    void* lpDialogInit = NULL);

 
virtual BOOL CreateIndirect(
    HGLOBAL hDialogTemplate,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpDialogTemplate`  
 指向内存中包含用于创建对话框的对话框模板。 此模板的窗体中是[DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394)结构和控制信息，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `pParentWnd`  
 指向对话框对象的父窗口对象 (类型的[CWnd](../../mfc/reference/cwnd-class.md))。 如果它是**NULL**，对话框对象的父窗口设置为主应用程序窗口中。  
  
 `lpDialogInit`  
 指向**DLGINIT**资源。  
  
 `hDialogTemplate`  
 包含指向包含的对话框模板的全局内存的句柄。 此模板的窗体中是**DLGTEMPLATE**结构和每个控件在对话框中的数据。  
  
### <a name="return-value"></a>返回值  
 如果对话框中已创建并初始化成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 `CreateIndirect`成员函数将创建该对话框后立即返回。  
  
 使用**WS_VISIBLE**如对话框中创建的父窗口时应显示在对话框模板中的样式。 否则，必须调用`ShowWindow`以让其显示。 有关如何在模板中指定其他对话框中样式的详细信息，请参阅[DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 使用`CWnd::DestroyWindow`函数来销毁对话框中创建的`CreateIndirect`函数。  
  
 包含 ActiveX 控件的对话框需要中提供的其他信息**DLGINIT**资源。 有关详细信息，请参阅知识库文章 Q231591，"如何︰ 使用对话框模板来创建与 ActiveX 控件的 MFC 对话框。" 知识库文章可在 MSDN 库的 Visual Studio 文档中或在[http://support.microsoft.com](http://support.microsoft.com/)。  
  
##  <a name="a-namedomodala--cdialogdomodal"></a><a name="domodal"></a>CDialog::DoModal  
 调用此成员函数来调用模式对话框并返回对话框中的结果完成。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 `int`值，该值指定的值`nResult`参数传递给[CDialog::EndDialog](#enddialog)成员函数，用来关闭该对话框。 返回值为 –&1;，如果该函数无法创建该对话框中，或**IDABORT**如果出现了其他错误，通过这种情况下输出窗口将包含错误信息从[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>备注  
 对话框中处于活动状态时，此成员函数将处理与用户的所有交互。 这是新增功能使得对话框成为模式;也就是说，用户不能进行交互与其他窗口对话框中关闭之前。  
  
 如果用户单击一个按钮在对话框中，如确定或取消，消息处理程序成员函数，如[OnOK](#onok)或[OnCancel](#oncancel)，调用以尝试关闭该对话框。 默认值`OnOK`成员函数将验证和更新对话框中的数据并关闭结果对话框**IDOK**，并且将默认`OnCancel`成员函数将关闭该对话框与结果**IDCANCEL**而无需验证或更新对话框中的数据。 您可以重写这些消息处理程序函数来更改其行为。  
  
> [!NOTE]
> `PreTranslateMessage`现在称为为模式对话框框中消息处理。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog #&63;](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]  
  
##  <a name="a-nameenddialoga--cdialogenddialog"></a><a name="enddialog"></a>CDialog::EndDialog  
 调用该成员函数以终止有模式对话框。  
  
```  
void EndDialog(int nResult);
```  
  
### <a name="parameters"></a>参数  
 `nResult`  
 包含要从对话框中返回给调用方的值`DoModal`。  
  
### <a name="remarks"></a>备注  
 此成员函数将返回`nResult`的返回值作为`DoModal`。 必须使用`EndDialog`函数以完成创建模式对话框时的处理。  
  
 您可以调用`EndDialog`在任何时候，即使是在[OnInitDialog](#oninitdialog)、 中才将其对话框中显示这种情况下，应该将其关闭，或设置输入的焦点之前。  
  
 `EndDialog`不会立即关闭该对话框。 相反，它设置一个标志，指示以关闭只要返回当前消息处理程序对话框。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog #&64;](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCControlLadenDialog #&65;](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]  
  
##  <a name="a-namegetdefida--cdialoggetdefid"></a><a name="getdefid"></a>CDialog::GetDefID  
 调用`GetDefID`成员函数以获取对话框中的默认按钮控件的 ID。  
  
```  
DWORD GetDefID() const;  
```  
  
### <a name="return-value"></a>返回值  
 32 位值 ( `DWORD`)。 如果默认按钮具有的 ID 值，包含高序位字**DC_HASDEFID**和低序位字包含的 ID 值。 如果默认按钮不具有的 ID 值，则返回值为 0。  
  
### <a name="remarks"></a>备注  
 这通常是确定按钮。  
  
##  <a name="a-namegotodlgctrla--cdialoggotodlgctrl"></a><a name="gotodlgctrl"></a>CDialog::GotoDlgCtrl  
 将焦点移到指定控件在对话框中。  
  
```  
void GotoDlgCtrl(CWnd* pWndCtrl);
```  
  
### <a name="parameters"></a>参数  
 `pWndCtrl`  
 标识要接收焦点的窗口 （控件）。  
  
### <a name="remarks"></a>备注  
 若要获取的控件 （子窗口） 将作为传递一个指针， `pWndCtrl`，调用`CWnd::GetDlgItem`成员函数，它将返回一个指向[CWnd](../../mfc/reference/cwnd-class.md)对象。  
  
### <a name="example"></a>示例  
  请参阅示例[CWnd::GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem)。  
  
##  <a name="a-nameinitmodalindirecta--cdialoginitmodalindirect"></a><a name="initmodalindirect"></a>CDialog::InitModalIndirect  
 调用此成员函数来初始化模式对话框对象使用内存中构造的对话框模板。  
  
```  
BOOL InitModalIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,  
    CWnd* pParentWnd = NULL,  
    void* lpDialogInit = NULL);

 
    BOOL InitModalIndirect(
    HGLOBAL hDialogTemplate,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpDialogTemplate`  
 指向内存中包含用于创建对话框的对话框模板。 此模板的窗体中是[DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394)结构和控制信息，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `hDialogTemplate`  
 包含指向包含的对话框模板的全局内存的句柄。 此模板的窗体中是**DLGTEMPLATE**结构和每个控件在对话框中的数据。  
  
 `pParentWnd`  
 指向父或所有者窗口对象 (类型的[CWnd](../../mfc/reference/cwnd-class.md)) 对话框对象所属。 如果它是**NULL**，对话框对象的父窗口设置为主应用程序窗口中。  
  
 `lpDialogInit`  
 指向**DLGINIT**资源。  
  
### <a name="return-value"></a>返回值  
 如果对话框对象已创建并初始化成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 若要间接创建模式对话框中，首先分配全局内存块，并使用对话框模板的填充。 然后，调用空`CDialog`构造函数来构造对话框对象。 接下来，调用`InitModalIndirect`以存储到内存中对话框模板您句柄。 创建并显示 Windows 对话框中更高版本，当[DoModal](#domodal)调用成员函数。  
  
 包含 ActiveX 控件的对话框需要中提供的其他信息**DLGINIT**资源。 有关详细信息，请参阅知识库文章 Q231591，"如何︰ 使用对话框模板来创建与 ActiveX 控件的 MFC 对话框。" 知识库文章可在 MSDN 库的 Visual Studio 文档中或在[http://support.microsoft.com](http://support.microsoft.com/)。  
  
##  <a name="a-namemapdialogrecta--cdialogmapdialogrect"></a><a name="mapdialogrect"></a>CDialog::MapDialogRect  
 若要将一个矩形的对话框单位转换为屏幕单位的调用。  
  
```  
void MapDialogRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，它包含对话框中要转换的坐标。  
  
### <a name="remarks"></a>备注  
 在派生自的平均宽度和高度用于对话框中的文本的字体中字符的当前对话框基本单位方面阐述对话框单位。 一个水平度量对话框基本宽度单位 （） 的四分之一，一个垂直的单位是对话框底高单位的&1; /&8;。  
  
 **GetDialogBaseUnits** Windows 函数返回系统字体的大小信息，但您可以指定不同的字体，每个对话框中，如果您使用**DS_SETFONT**资源定义文件中的样式。 `MapDialogRect` Windows 函数将使用此对话框中的合适的字体。  
  
 `MapDialogRect`成员函数将替换为对话框单位`lpRect`与屏幕单位 （像素），以便可以使用矩形来创建一个对话框，或将控件放在一个框中。  
  
##  <a name="a-namenextdlgctrla--cdialognextdlgctrl"></a><a name="nextdlgctrl"></a>CDialog::NextDlgCtrl  
 将焦点移到下一个控件在对话框中。  
  
```  
void NextDlgCtrl() const;  
```  
  
### <a name="remarks"></a>备注  
 如果焦点位于对话框中的最后一个控件，它将移到第一个控件。  
  
##  <a name="a-nameoncancela--cdialogoncancel"></a><a name="oncancel"></a>CDialog::OnCancel  
 框架将调用此方法，当用户单击**取消**或按 ESC 键在模式对话框或无模式对话框中。  
  
```  
virtual void OnCancel();
```  
  
### <a name="remarks"></a>备注  
 重写此方法以执行操作 （例如还原旧数据） 当用户关闭对话框中通过单击**取消**或按 ESC 键。 默认值通过调用关闭一个模式对话框[EndDialog](#enddialog) ，从而导致[DoModal](#domodal)返回 IDCANCEL。  
  
 如果实现**取消**按钮在无模式对话框，你必须重写`OnCancel`方法并且调用[DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow)其内部。 请勿调用基类方法，因为它调用`EndDialog`，这将使对话框中不可见，但不是销毁它。  
  
> [!NOTE]
>  不能重写此方法，当您使用`CFileDialog`在 Windows XP 下编译的程序中的对象。 有关详细信息`CFileDialog`，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog #&66;](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]  
  
##  <a name="a-nameoninitdialoga--cdialogoninitdialog"></a><a name="oninitdialog"></a>CDialog::OnInitDialog  
 此方法调用以响应`WM_INITDIALOG`消息。  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>返回值  
 指定是否应用程序具有输入的焦点设置到其中一个控件在对话框中。 如果`OnInitDialog`返回非零，则 Windows 会将输入的焦点设置到默认位置，在对话框中的第一个控件。 只有当它已显式设置输入的焦点为其中一个控件在对话框中，应用程序可以返回 0。  
  
### <a name="remarks"></a>备注  
 Windows 将发送`WM_INITDIALOG`期间对话框中的消息[创建](#create)， [CreateIndirect](#createindirect)，或[DoModal](#domodal)调用，对话框中显示之前立即发生这种情况。  
  
 如果你想要执行特殊处理，对话框中初始化时，重写此方法。 在重写版本中，首先调用基类`OnInitDialog`但会忽略其返回值。 通常会返回`TRUE`从被重写方法。  
  
 Windows 调用`OnInitDialog`到所有 Microsoft 基础类库对话框使用常见的标准全球对话框的过程的函数。 不会调用此函数通过消息映射，并因此不需要消息映射条目为此方法。  
  
> [!NOTE]
>  不能重写此方法，当您使用`CFileDialog`下编译的程序中的对象[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。 有关更改的详细信息`CFileDialog`下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog #&67;](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]  
  
##  <a name="a-nameonoka--cdialogonok"></a><a name="onok"></a>CDialog::OnOK  
 当用户单击时，调用**确定**按钮 （带有 IDOK ID 的按钮）。  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>备注  
 重写此方法以执行操作时**确定**按钮处于激活状态。 如果自动数据验证和交换中包含对话框中，此方法的默认实现验证对话框数据并更新您的应用程序中的适当变量。  
  
 如果实现**确定**按钮在无模式对话框，你必须重写`OnOK`方法并且调用[DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow)其内部。 请勿调用基类方法，因为它调用[EndDialog](#enddialog)这将使对话框中不可见，但不会销毁它。  
  
> [!NOTE]
>  不能重写此方法，当您使用`CFileDialog`在 Windows XP 下编译的程序中的对象。 有关详细信息`CFileDialog`，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog #&68;](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]  
  
##  <a name="a-nameonsetfonta--cdialogonsetfont"></a><a name="onsetfont"></a>CDialog::OnSetFont  
 指定在绘制文本时，将使用的对话框中控件的字体。  
  
```  
Virtual void OnSetFont(CFont* pFont);
```  
  
### <a name="parameters"></a>参数  
 [in] `pFont`  
 指定一个指向将用作在此对话框中的所有控件的默认字体的字体。  
  
### <a name="remarks"></a>备注  
 对话框中将使用指定的字体作为默认值为所有控件。  
  
 对话框编辑器通常属于对话框模板资源设置对话框的字体。  
  
> [!NOTE]
>  不能重写此方法，当您使用`CFileDialog`下编译的程序中的对象[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。 有关更改的详细信息`CFileDialog`下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。  
  
##  <a name="a-nameprevdlgctrla--cdialogprevdlgctrl"></a><a name="prevdlgctrl"></a>CDialog::PrevDlgCtrl  
 在对话框中将焦点设置为上一个控件。  
  
```  
void PrevDlgCtrl() const;  
```  
  
### <a name="remarks"></a>备注  
 如果焦点位于对话框中的第一个控件，它将移到最后一个控件在框中。  
  
##  <a name="a-namesetdefida--cdialogsetdefid"></a><a name="setdefid"></a>CDialog::SetDefID  
 更改对话框中的默认按钮控件。  
  
```  
void SetDefID(UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 指定将成为默认的按钮控件的 ID。  
  
##  <a name="a-namesethelpida--cdialogsethelpid"></a><a name="sethelpid"></a>CDialog::SetHelpID  
 设置对话框中的上下文相关帮助 ID。  
  
```  
void SetHelpID(UINT nIDR);
```  
  
### <a name="parameters"></a>参数  
 *nIDR*  
 指定区分上下文的帮助 id。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 DLGCBR32](../../visual-cpp-samples.md)   
 [MFC 示例 DLGTEMPL](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)


