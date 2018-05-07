---
title: CDialog 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDialog
- AFXWIN/CDialog
- AFXWIN/CDialog::CDialog
- AFXWIN/CDialog::Create
- AFXWIN/CDialog::CreateIndirect
- AFXWIN/CDialog::DoModal
- AFXWIN/CDialog::EndDialog
- AFXWIN/CDialog::GetDefID
- AFXWIN/CDialog::GotoDlgCtrl
- AFXWIN/CDialog::InitModalIndirect
- AFXWIN/CDialog::MapDialogRect
- AFXWIN/CDialog::NextDlgCtrl
- AFXWIN/CDialog::OnInitDialog
- AFXWIN/CDialog::OnSetFont
- AFXWIN/CDialog::PrevDlgCtrl
- AFXWIN/CDialog::SetDefID
- AFXWIN/CDialog::SetHelpID
- AFXWIN/CDialog::OnCancel
- AFXWIN/CDialog::OnOK
dev_langs:
- C++
helpviewer_keywords:
- CDialog [MFC], CDialog
- CDialog [MFC], Create
- CDialog [MFC], CreateIndirect
- CDialog [MFC], DoModal
- CDialog [MFC], EndDialog
- CDialog [MFC], GetDefID
- CDialog [MFC], GotoDlgCtrl
- CDialog [MFC], InitModalIndirect
- CDialog [MFC], MapDialogRect
- CDialog [MFC], NextDlgCtrl
- CDialog [MFC], OnInitDialog
- CDialog [MFC], OnSetFont
- CDialog [MFC], PrevDlgCtrl
- CDialog [MFC], SetDefID
- CDialog [MFC], SetHelpID
- CDialog [MFC], OnCancel
- CDialog [MFC], OnOK
ms.assetid: ca64b77e-2cd2-47e3-8eff-c2645ad578f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43f36dae3c383aebedf7e8340188e78961066a30
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cdialog-class"></a>CDialog 类
用于在屏幕上显示对话框的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class CDialog : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CDialog::CDialog](#cdialog)|构造 `CDialog` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDialog::Create](#create)|初始化 `CDialog` 对象。 创建无模式对话框，并将其附加到`CDialog`对象。|  
|[CDialog::CreateIndirect](#createindirect)|从内存中的对话框模板 （而不是基于资源） 来创建无模式对话框。|  
|[CDialog::DoModal](#domodal)|调用模式对话框并返回完成。|  
|[CDialog::EndDialog](#enddialog)|关闭模式对话框。|  
|[CDialog::GetDefID](#getdefid)|获取对话框中的默认按钮控件的 ID。|  
|[CDialog::GotoDlgCtrl](#gotodlgctrl)|将焦点移到指定的对话框控件在对话框中。|  
|[CDialog::InitModalIndirect](#initmodalindirect)|从内存中的对话框模板 （而不是基于资源） 来创建模式对话框。 参数存储之前函数`DoModal`调用。|  
|[CDialog::MapDialogRect](#mapdialogrect)|将矩形的对话框单位转换为屏幕单位。|  
|[CDialog::NextDlgCtrl](#nextdlgctrl)|将焦点移到下一步的对话框控件在对话框中。|  
|[CDialog::OnInitDialog](#oninitdialog)|重写以增加对话框中初始化。|  
|[CDialog::OnSetFont](#onsetfont)|重写以指定对话框控件是使用时，它可绘制文本的字体。|  
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|将焦点移至上一个对话框控件在对话框中。|  
|[CDialog::SetDefID](#setdefid)|指定按钮会变为对话框中的默认按钮控件。|  
|[CDialog::SetHelpID](#sethelpid)|设置对话框中的上下文相关帮助 ID。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDialog::OnCancel](#oncancel)|重写以执行的取消按钮或 ESC 键操作。 关闭对话框，默认值和**DoModal**返回**IDCANCEL**。|  
|[CDialog::OnOK](#onok)|重写以执行模式对话框中的确定按钮的操作。 关闭对话框，默认值和`DoModal`返回**IDOK**。|  
  
## <a name="remarks"></a>备注  
 对话框中有两种类型： 模式和无模式。 在应用程序继续之前，必须由用户关闭模式对话框。 无模式对话框允许用户以显示该对话框并返回到另一个任务而无需取消或删除对话框。  
  
 A`CDialog`对象是对话框模板的组合和`CDialog`-派生类。 使用对话框编辑器创建对话框模板并将其存储在资源中，然后使用添加类向导以创建派生自的类`CDialog`。  
  
 对话框中，与任何其他窗口一样从 Windows 中接收消息。 在对话框中，你有特别兴趣处理从对话框的控件通知消息，因为这是在用户对话框中的交互。 使用属性窗口选择哪些消息给句柄以及你想将适当的消息映射条目和消息处理程序成员函数向类添加为你。 只需编写特定于应用程序代码中处理程序成员函数。  
  
 如果你愿意，你可以在编写消息映射项和成员函数手动。  
  
 在所有但最不重要的对话框中，你将成员变量添加到派生的对话框类来存储用户在对话框的控件中输入的数据或显示的用户数据。 添加变量向导可用于创建成员变量并将其与控件关联。 同时，你选择的变量类型和允许的每个变量的值的范围。 代码向导将成员变量添加到派生的对话框类。  
  
 数据映射生成以自动处理的成员变量和对话框的控件之间的数据交换。 数据映射提供函数来初始化的控件在对话框中，使用合适的值，检索数据，并验证数据。  
  
 若要创建模式对话框，构造使用派生的对话框类的构造函数的堆栈上的对象，然后调用`DoModal`创建对话框窗口和其控件。 如果你想要创建无模式对话框，调用**创建**对话框类的构造函数中。  
  
 你还可以创建一个模板在内存中通过使用[DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394)数据结构在 Windows SDK 中所述。 在构造之后`CDialog`对象，请调用[CreateIndirect](#createindirect)创建无模式对话框中或调用[InitModalIndirect](#initmodalindirect)和[DoModal](#domodal)创建在安装结束时对话框。  
  
 重写中编写交换和验证数据映射`CWnd::DoDataExchange`，它将添加到新的对话框类。 请参阅[DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)成员函数在`CWnd`有关交换和验证功能的详细信息。  
  
 程序员和 framework 调用`DoDataExchange`间接通过调用[CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)。  
  
 框架调用`UpdateData`当用户单击确定按钮以关闭模式对话框。 （不检索数据如果单击取消按钮。）默认实现[OnInitDialog](#oninitdialog)还会调用`UpdateData`设置控件的初始值。 通常可以重写`OnInitDialog`进一步初始化控件。 `OnInitDialog` 后创建所有对话框控件和框显示对话框之前调用。  
  
 你可以调用`CWnd::UpdateData`模式或无模式对话框中的执行期间随时。  
  
 如果手动开发对话框中，你有必要将成员变量添加到派生的对话框类自己，并添加成员函数来设置或获取这些值。  
  
 当用户按确定或取消按钮，或当你的代码调用模式对话框自动关闭`EndDialog`成员函数。  
  
 当你实现无模式对话框时，始终重写`OnCancel`成员函数和调用`DestroyWindow`从在其中。 请勿调用基类`CDialog::OnCancel`，因为它调用`EndDialog`，这将使对话框中不可见，但不是会破坏。 你还应重写`PostNcDestroy`要删除的无模式对话框**这**，因为无模式对话框通常会分配有**新**。 有模式对话框通常构造在框架上，而无需`PostNcDestroy`清理。  
  
 有关详细信息`CDialog`，请参阅：  
  
- [对话框](../../mfc/dialog-boxes.md)  
  
-   知识库文章 Q262954： 如何： 创建可调整其大小的对话框中，与滚动条  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDialog`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="cdialog"></a>  CDialog::CDialog  
 若要构造的基于资源的模式对话框，请调用构造函数的任一公共形式。  
  
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
 包含是对话框模板资源的名称的以 null 结尾的字符串。  
  
 `nIDTemplate`  
 包含对话框模板资源的 ID 号。  
  
 `pParentWnd`  
 指向父或所有者窗口对象 (类型的[CWnd](../../mfc/reference/cwnd-class.md)) 对话框对象所属。 如果它是**NULL**，对话框对象的父窗口设置为应用程序主窗口。  
  
### <a name="remarks"></a>备注  
 一种形式的构造函数通过模板名称提供到对话框资源的访问权限。 另一个构造函数提供按模板 ID 号的访问通常具有**IDD_** 前缀 (例如，IDD_DIALOG1)。  
  
 若要构造一个模式对话框，可从内存中的模板，请首先调用无参数、 受保护构造函数，然后调用`InitModalIndirect`。  
  
 与上述方法之一构造模式对话框后，调用`DoModal`。  
  
 若要构造一个无模式对话框，使用受保护的形式`CDialog`构造函数。 构造函数得到保护，因为必须派生你自己对话框类，以实现无模式对话框。 无模式对话框的构造是一个两步过程。 第一次调用构造函数;然后调用**创建**成员函数来创建基于资源的对话框中，或调用`CreateIndirect`以从内存中的模板创建对话框。  
  
##  <a name="create"></a>  CDialog::Create  
 调用**创建**若要创建使用对话框模板资源从一个无模式对话框。  
  
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
 包含是对话框模板资源的名称的以 null 结尾的字符串。  
  
 `pParentWnd`  
 指向父窗口对象 (类型的[CWnd](../../mfc/reference/cwnd-class.md)) 对话框对象所属。 如果它是**NULL**，对话框对象的父窗口设置为应用程序主窗口。  
  
 `nIDTemplate`  
 包含对话框模板资源的 ID 号。  
  
### <a name="return-value"></a>返回值  
 这两种形式返回非零，如果对话框中创建和初始化已成功;否则为 0。  
  
### <a name="remarks"></a>备注  
 你可以将调用放到**创建**内的构造函数或调用其构造函数调用。  
  
 两种形式的**创建**成员函数按模板名称或模板 ID 号 (例如，IDD_DIALOG1) 提供对对话框模板资源进行访问。  
  
 对于任一窗体，将指针传递到父窗口对象。 如果`pParentWnd`是**NULL**，将使用其父窗口或所有者窗口设置为应用程序主窗口创建对话框。  
  
 **创建**成员函数将返回其创建该对话框后立即。  
  
 使用**WS_VISIBLE**如果对话框中时创建的父窗口应出现在对话框模板中的样式。 否则，必须调用`ShowWindow`。 进一步对话框样式和其应用程序，请参阅[DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394) Windows SDK 中的结构和[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)中*MFC 参考*。  
  
 使用`CWnd::DestroyWindow`函数销毁对话框中创建的**创建**函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]  
  
##  <a name="createindirect"></a>  CDialog::CreateIndirect  
 调用此成员函数以从内存中对话框模板创建无模式对话框。  
  
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
 指向包含用来创建对话框中的对话框模板的内存。 此模板是形式[DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394)结构和控制信息，如 Windows SDK 中所述。  
  
 `pParentWnd`  
 指向对话框对象的父窗口对象 (类型的[CWnd](../../mfc/reference/cwnd-class.md))。 如果它是**NULL**，对话框对象的父窗口设置为应用程序主窗口。  
  
 `lpDialogInit`  
 指向**DLGINIT**资源。  
  
 `hDialogTemplate`  
 包含全局内存包含对话框模板的句柄。 此模板是形式**DLGTEMPLATE**结构和每个控件在对话框中的数据。  
  
### <a name="return-value"></a>返回值  
 如果对话框中已创建并初始化成功，则非零否则为 0。  
  
### <a name="remarks"></a>备注  
 `CreateIndirect`成员函数将返回其创建该对话框后立即。  
  
 使用**WS_VISIBLE**如果对话框中时创建的父窗口应出现在对话框模板中的样式。 否则，必须调用`ShowWindow`以使其显示。 有关如何在模板中指定其他对话框中样式的详细信息，请参阅[DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394) Windows SDK 中的结构。  
  
 使用`CWnd::DestroyWindow`函数销毁对话框中创建的`CreateIndirect`函数。  
  
 包含 ActiveX 控件的对话框需要中提供的其他信息**DLGINIT**资源。 有关详细信息，请参阅知识库文章 Q231591，"如何： 使用对话框模板创建与 ActiveX 控件的 MFC 对话框。" 知识库文章位于[ http://support.microsoft.com ](http://support.microsoft.com/)。  
  
##  <a name="domodal"></a>  CDialog::DoModal  
 调用此成员函数以调用模式对话框并返回完成的对话框结果。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 `int`值，该值指定的值`nResult`参数传递到[CDialog::EndDialog](#enddialog)成员函数，其用于关闭对话框。 返回值为-1，如果该函数无法创建对话框中，或**IDABORT**如果发生了一些其他错误，通过这种情况下输出窗口将包含错误信息从[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>备注  
 对话框中处于活动状态时，此成员函数将处理与用户的所有交互。 正是这使得对话框模式;也就是说，用户不能交互与其他窗口中，是关闭该对话框之前。  
  
 如果用户单击其中一个在对话框中，如确定或取消，消息处理程序成员函数时，按键如[OnOK](#onok)或[OnCancel](#oncancel)，调用以尝试关闭对话框。 默认值`OnOK`成员函数将验证和更新对话框中的数据并关闭结果对话框中**IDOK**，也是默认值`OnCancel`成员函数将关闭结果的对话框中**IDCANCEL**而无需验证或更新的对话框中的数据。 你可以重写这些消息处理程序函数，以更改其行为。  
  
> [!NOTE]
> `PreTranslateMessage` 现在为模式对话框框消息处理调用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]  
  
##  <a name="enddialog"></a>  CDialog::EndDialog  
 调用此成员函数以终止模式对话框。  
  
```  
void EndDialog(int nResult);
```  
  
### <a name="parameters"></a>参数  
 `nResult`  
 包含要从对话框中返回到调用方的值`DoModal`。  
  
### <a name="remarks"></a>备注  
 此成员函数将返回`nResult`用作返回值`DoModal`。 必须使用`EndDialog`函数来完成处理每当创建模式对话框。  
  
 你可以调用`EndDialog`任何时候，即使在[OnInitDialog](#oninitdialog)，在这种情况下，你应在关闭对话框框，然后它会显示，或设置输入的焦点之前。  
  
 `EndDialog` 不会立即关闭对话框。 相反，它设置一个标志，指示当前消息处理程序返回时，就会立即关闭对话框。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]  
  
##  <a name="getdefid"></a>  CDialog::GetDefID  
 调用`GetDefID`成员函数以获取对话框中的默认按钮控件的 ID。  
  
```  
DWORD GetDefID() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个 32 位值 ( `DWORD`)。 如果默认全都具有的 ID 值，包含高序位字**DC_HASDEFID**和低序位字包含的 ID 值。 如果默认按钮不具有的 ID 值，则返回值为 0。  
  
### <a name="remarks"></a>备注  
 这通常是确定按钮。  
  
##  <a name="gotodlgctrl"></a>  CDialog::GotoDlgCtrl  
 将焦点移到指定控件在对话框中。  
  
```  
void GotoDlgCtrl(CWnd* pWndCtrl);
```  
  
### <a name="parameters"></a>参数  
 `pWndCtrl`  
 标识要接收焦点的窗口 （控件）。  
  
### <a name="remarks"></a>备注  
 若要获取的控件 （子窗口），以将作为传递指针`pWndCtrl`，调用`CWnd::GetDlgItem`成员函数，返回一个指向[CWnd](../../mfc/reference/cwnd-class.md)对象。  
  
### <a name="example"></a>示例  
  请参阅示例[CWnd::GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem)。  
  
##  <a name="initmodalindirect"></a>  CDialog::InitModalIndirect  
 调用此成员函数以初始化使用内存中构造的对话框模板的模式对话框对象。  
  
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
 指向包含用来创建对话框中的对话框模板的内存。 此模板是形式[DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394)结构和控制信息，如 Windows SDK 中所述。  
  
 `hDialogTemplate`  
 包含全局内存包含对话框模板的句柄。 此模板是形式**DLGTEMPLATE**结构和每个控件在对话框中的数据。  
  
 `pParentWnd`  
 指向父或所有者窗口对象 (类型的[CWnd](../../mfc/reference/cwnd-class.md)) 对话框对象所属。 如果它是**NULL**，对话框对象的父窗口设置为应用程序主窗口。  
  
 `lpDialogInit`  
 指向**DLGINIT**资源。  
  
### <a name="return-value"></a>返回值  
 如果创建并初始化成功，则对话框对象则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 若要间接创建模式对话框，首先分配全局内存块，并填充对话框模板。 然后调用空`CDialog`用于构造对话框对象构造函数。 接下来，调用`InitModalIndirect`存储到内存中对话框模板你句柄。 创建并显示 Windows 对话框中更高版本，在[DoModal](#domodal)调用成员函数。  
  
 包含 ActiveX 控件的对话框需要中提供的其他信息**DLGINIT**资源。 有关详细信息，请参阅知识库文章 Q231591，"如何： 使用对话框模板创建与 ActiveX 控件的 MFC 对话框。" 知识库文章位于[ http://support.microsoft.com ](http://support.microsoft.com/)。  
  
##  <a name="mapdialogrect"></a>  CDialog::MapDialogRect  
 要转换为屏幕单元的矩形的对话框单位的调用。  
  
```  
void MapDialogRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)包含对话框中的对象要转换的坐标。  
  
### <a name="remarks"></a>备注  
 在派生自的平均宽度和高度的用于对话框文本的字体中字符的当前对话框基本单位方面阐述对话框单位。 一个水平单元是对话框基本宽度单位 （） 的四分之一，一个垂直单元的八分之一对话框基高度单元。  
  
 **GetDialogBaseUnits** Windows 函数将返回系统字体的大小信息，但你可以指定不同的字体每个对话框中，如果你使用**DS_SETFONT**设置中的样式资源定义文件。 `MapDialogRect` Windows 函数将使用此对话框中的相应的字体。  
  
 `MapDialogRect`成员函数将替换中的对话框单元`lpRect`与屏幕单位 （像素），以便可以使用矩形来创建一个对话框，或将控件放在一个框内。  
  
##  <a name="nextdlgctrl"></a>  CDialog::NextDlgCtrl  
 将焦点移到下一个控件在对话框中。  
  
```  
void NextDlgCtrl() const;  
```  
  
### <a name="remarks"></a>备注  
 如果焦点位于对话框中的最后一个控件，它将移动到第一个控件。  
  
##  <a name="oncancel"></a>  CDialog::OnCancel  
 框架调用此方法，当用户单击**取消**或按 ESC 键模式或无模式对话框中的。  
  
```  
virtual void OnCancel();
```  
  
### <a name="remarks"></a>备注  
 重写此方法以执行操作 （例如还原旧数据） 当用户关闭对话框中通过单击**取消**或按 ESC 键。 默认值通过调用关闭模式对话框[EndDialog](#enddialog) ，从而导致[DoModal](#domodal)返回 IDCANCEL。  
  
 如果你实现**取消**按钮在无模式对话框，你必须重写`OnCancel`方法并且调用[DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow)其内部。 请勿调用基类方法，因为它调用`EndDialog`，这将使对话框中不可见，但不是销毁它。  
  
> [!NOTE]
>  当你使用时，不能重写此方法`CFileDialog`在 Windows XP 下编译的程序中的对象。 有关详细信息`CFileDialog`，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]  
  
##  <a name="oninitdialog"></a>  CDialog::OnInitDialog  
 此方法调用以响应`WM_INITDIALOG`消息。  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>返回值  
 指定是否应用程序的设置输入的焦点为每个控件在对话框中。 如果`OnInitDialog`返回非零，则 Windows 会将输入的焦点设置到默认位置，在对话框中的第一个控件。 只有当它已显式设置输入的焦点为每个控件在对话框中，该应用程序可以返回 0。  
  
### <a name="remarks"></a>备注  
 Windows 会将发送`WM_INITDIALOG`期间对话框中的消息[创建](#create)， [CreateIndirect](#createindirect)，或[DoModal](#domodal)调用，在对话框中之前立即发生将显示。  
  
 如果你想要执行特殊处理，在初始化对话框中时，重写此方法。 在重写的版本中，首先调用基类`OnInitDialog`但请忽略其返回值。 通常将返回`TRUE`从你重写的方法。  
  
 Windows 调用`OnInitDialog`到所有的 Microsoft 基础类库对话框使用常见的标准全局对话框过程的函数。 它不调用此函数通过消息映射，并且因此你不为此方法需要一个消息映射条目。  
  
> [!NOTE]
> 当你使用时，不能重写此方法`CFileDialog`在 Windows Vista 或更高版本操作系统下编译的程序中的对象。 有关对进行的更改的详细信息`CFileDialog`在 Windows Vista 及更高版本，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]  
  
##  <a name="onok"></a>  CDialog::OnOK  
 当用户单击时调用**确定**按钮 （带有 IDOK ID 的按钮）。  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>备注  
 重写此方法以执行操作时**确定**按钮处于激活状态。 如果该对话框包含自动的数据验证和 exchange，此方法的默认实现将验证对话框数据，并更新你的应用程序中的适当变量。  
  
 如果你实现**确定**按钮在无模式对话框，你必须重写`OnOK`方法并且调用[DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow)其内部。 请勿调用基类方法，因为它调用[EndDialog](#enddialog)它使对话框中不可见，但不会销毁它。  
  
> [!NOTE]
>  当你使用时，不能重写此方法`CFileDialog`在 Windows XP 下编译的程序中的对象。 有关详细信息`CFileDialog`，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]  
  
##  <a name="onsetfont"></a>  CDialog::OnSetFont  
 指定在绘制文本时，将使用的对话框中控件的字体。  
  
```  
Virtual void OnSetFont(CFont* pFont);
```  
  
### <a name="parameters"></a>参数  
 [in] `pFont`  
 指定指向将用作此对话框中的所有控件的默认字体的字体的指针。  
  
### <a name="remarks"></a>备注  
 对话框中将使用指定的字体作为默认值的所有控件。  
  
 对话框编辑器通常设置的对话框字体的对话框模板资源的一部分。  
  
> [!NOTE]
> 当你使用时，不能重写此方法`CFileDialog`在 Windows Vista 或更高版本操作系统下编译的程序中的对象。 有关对进行的更改的详细信息`CFileDialog`在 Windows Vista 及更高版本，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。  
  
##  <a name="prevdlgctrl"></a>  CDialog::PrevDlgCtrl  
 在对话框中将焦点设置为上一个控件。  
  
```  
void PrevDlgCtrl() const;  
```  
  
### <a name="remarks"></a>备注  
 如果焦点位于对话框中的第一个控件，它将移动到最后一个控件在框中。  
  
##  <a name="setdefid"></a>  CDialog::SetDefID  
 更改对话框中的默认按钮控件。  
  
```  
void SetDefID(UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `nID`  
 指定将成为默认的按钮控件的 ID。  
  
##  <a name="sethelpid"></a>  CDialog::SetHelpID  
 设置对话框中的上下文相关帮助 ID。  
  
```  
void SetHelpID(UINT nIDR);
```  
  
### <a name="parameters"></a>参数  
 *nIDR*  
 指定区分上下文的帮助 id。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 DLGCBR32](../../visual-cpp-samples.md)   
 [MFC 示例 DLGTEMPL](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)

