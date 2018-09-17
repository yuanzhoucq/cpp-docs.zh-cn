---
title: CDialog 类 |Microsoft Docs
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
ms.openlocfilehash: c18a9b1e4a35a1089b8a7fb441161552bb3a3909
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724303"
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
|[CDialog::CreateIndirect](#createindirect)|创建无模式对话框从内存中的对话框模板 （而不是基于资源）。|  
|[CDialog::DoModal](#domodal)|调用模式对话框并返回完成。|  
|[CDialog::EndDialog](#enddialog)|关闭模式对话框。|  
|[CDialog::GetDefID](#getdefid)|获取对话框中的默认按钮控件的 ID。|  
|[CDialog::GotoDlgCtrl](#gotodlgctrl)|将焦点移到指定的对话框控件在对话框中。|  
|[CDialog::InitModalIndirect](#initmodalindirect)|创建模式对话框从内存中的对话框模板 （而不是基于资源）。 参数存储到该函数`DoModal`调用。|  
|[CDialog::MapDialogRect](#mapdialogrect)|将一个矩形的对话框单位转换为屏幕单位。|  
|[CDialog::NextDlgCtrl](#nextdlgctrl)|将焦点移到下一个对话框控件在对话框中。|  
|[CDialog::OnInitDialog](#oninitdialog)|重写以增加对话框初始化。|  
|[CDialog::OnSetFont](#onsetfont)|重写以指定对话框控件将绘制文本时使用的字体。|  
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|将焦点移到上一个对话框控件在对话框中。|  
|[CDialog::SetDefID](#setdefid)|更改为指定可通过按钮的对话框中的默认按钮控件。|  
|[CDialog::SetHelpID](#sethelpid)|设置对话框的的上下文相关帮助 ID。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDialog::OnCancel](#oncancel)|重写以执行取消按钮或 ESC 键操作。 默认关闭对话框和`DoModal`返回 IDCANCEL。|  
|[CDialog::OnOK](#onok)|重写以执行在模式对话框中的确定按钮的操作。 默认关闭对话框和`DoModal`返回 IDOK。|  
  
## <a name="remarks"></a>备注  
 对话框有两种类型： 模式和无模式。 应用程序继续运行之前，用户必须关闭模式对话框。 无模式对话框允许用户以显示该对话框并返回到另一项任务而无需取消或删除对话框的。  
  
 一个`CDialog`对象是对话框模板的组合和`CDialog`-派生的类。 使用对话框编辑器创建对话框模板，并将其存储在资源中，然后添加类向导用于创建派生自的类`CDialog`。  
  
 对话框中，与任何其他窗口一样接收来自 Windows 消息。 在对话框中，您特别感兴趣，因为它是用户与您的对话框的交互方式处理来自对话框的控件的通知消息。 使用属性窗口句柄和它需要哪些消息将适当的消息映射条目和消息处理程序成员函数向类添加为你的选择。 只需在处理程序成员函数中编写特定于应用程序的代码。  
  
 如果您愿意，您可以始终消息映射项和成员函数手动编写。  
  
 除最普通的对话框中，你将成员变量添加到派生的对话框类来存储用户在对话框的控件中输入的数据或显示该用户的数据。 可以使用添加变量向导创建成员变量并将其与控件关联。 一次，选择一个变量类型和每个变量的值的允许范围。 代码向导将成员变量添加到自己的派生的对话框类。  
  
 生成数据映射，以自动处理成员变量和对话框的控件之间的数据交换。 数据映射提供函数来初始化具有适当的值的对话框中的控件，检索数据，并验证数据。  
  
 若要创建模式对话框中，构造使用派生的对话框类的构造函数在堆栈上的对象，然后调用`DoModal`创建对话框窗口和其控件。 如果你想要创建无模式对话框，则调用`Create`对话框类的构造函数中。  
  
 您还可以创建一个模板在内存中使用[DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate)数据结构，如 Windows SDK 中所述。 在构造之后`CDialog`对象，请调用[CreateIndirect](#createindirect)若要创建无模式对话框中或调用[InitModalIndirect](#initmodalindirect)并[DoModal](#domodal)创建在安装结束时对话框。  
  
 在交换和验证数据映射写入中的重写`CWnd::DoDataExchange`添加到新的对话框类。 请参阅[DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)成员函数在`CWnd`有关交换和验证功能的详细信息。  
  
 程序员和 framework 调用`DoDataExchange`间接通过调用[CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)。  
  
 框架将调用`UpdateData`当用户单击确定按钮以关闭模式对话框。 （不会检索数据如果单击取消按钮。）默认实现[OnInitDialog](#oninitdialog)还会调用`UpdateData`来设置控件的初始值。 通常可以重写`OnInitDialog`进一步初始化控件。 `OnInitDialog` 创建所有对话框控件和框显示在对话框后调用。  
  
 您可以调用`CWnd::UpdateData`模式或无模式对话框的执行期间任何时候。  
  
 如果手动开发一个对话框，您需要将成员变量添加到派生的对话框类自己，并添加成员函数来设置或获取这些值。  
  
 当用户按确定或取消按钮，或当你的代码调用模式对话框会自动关闭`EndDialog`成员函数。  
  
 当实现无模式对话框时，始终重写`OnCancel`成员函数，并调用`DestroyWindow`从在其中。 不调用基类`CDialog::OnCancel`，因为它会调用`EndDialog`，这将以对话框中不可见，但不是会销毁它。 您还应该重写`PostNcDestroy`为要删除的无模式对话框**这**，因为无模式对话框通常分配带有**新**。 模式对话框通常构造帧上，而无需`PostNcDestroy`清理。  
  
 有关详细信息`CDialog`，请参阅：  
  
- [对话框](../../mfc/dialog-boxes.md)  
  
-   知识库文章 Q262954： 如何： 创建具有滚动条可调整其大小的对话框  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDialog`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="cdialog"></a>  CDialog::CDialog  
 若要构造基于资源的模式对话框中，调用构造函数的任一公共窗体。  
  
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
 *lpszTemplateName*  
 包含以 null 结尾的字符串，表示对话框模板资源的名称。  
  
 *nIDTemplate*  
 包含对话框模板资源的 ID 号。  
  
 *pParentWnd*  
 指向父或所有者窗口对象 (类型的[CWnd](../../mfc/reference/cwnd-class.md)) 对话框对象属于的。 如果它为 NULL，对话框对象的父窗口设置为应用程序主窗口。  
  
### <a name="remarks"></a>备注  
 一种形式的构造函数提供的模板名称对话框资源的访问权限。 另一个构造函数提供的模板 ID 号，访问通常**IDD_** 前缀 (例如，IDD_DIALOG1)。  
  
 若要构造内存中的模板从一个模式对话框，请首先调用无参数、 受保护构造函数，然后调用`InitModalIndirect`。  
  
 使用上述方法之一构造模式对话框后，调用`DoModal`。  
  
 若要构造一个无模式对话框，使用的受保护的形式`CDialog`构造函数。 构造函数得到保护，因为必须派生自己对话框类，以实现无模式对话框。 无模式对话框的构造是一个两步过程。 第一次调用构造函数;然后调用`Create`成员函数来创建基于资源的对话框中，或调用`CreateIndirect`从内存中的模板创建的对话框。  
  
##  <a name="create"></a>  CDialog::Create  
 调用`Create`若要创建一个无模式对话框，使用资源中的对话框模板。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszTemplateName,  
    CWnd* pParentWnd = NULL);

 
virtual BOOL Create(
    UINT nIDTemplate,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 *lpszTemplateName*  
 包含以 null 结尾的字符串，表示对话框模板资源的名称。  
  
 *pParentWnd*  
 指向父窗口对象 (类型的[CWnd](../../mfc/reference/cwnd-class.md)) 对话框对象属于的。 如果它为 NULL，对话框对象的父窗口设置为应用程序主窗口。  
  
 *nIDTemplate*  
 包含对话框模板资源的 ID 号。  
  
### <a name="return-value"></a>返回值  
 这两种形式返回对话框创建和初始化已成功完成; 如果非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 可以将对调用`Create`内部构造函数或调用它的构造函数后调用。  
  
 两种形式的`Create`成员函数由模板名称或模板 ID 号 (例如，IDD_DIALOG1) 提供的对话框模板资源的访问权限。  
  
 对于任一窗体，将指针传递到父窗口对象。 如果*pParentWnd*为 NULL，将使用其父窗口或所有者窗口设置为应用程序主窗口创建对话框。  
  
 `Create`成员函数将创建该对话框后立即返回。  
  
 如果创建父窗口时，应显示该对话框，请使用对话框模板中的 WS_VISIBLE 样式。 否则，必须调用`ShowWindow`。 有关进一步的对话框样式和其应用程序，请参阅[DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate) Windows SDK 中的结构和[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)中*MFC 参考*。  
  
 使用`CWnd::DestroyWindow`函数来销毁对话框中创建的`Create`函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]  
  
##  <a name="createindirect"></a>  CDialog::CreateIndirect  
 调用此成员函数以从内存中的对话框模板创建无模式对话框。  
  
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
 *lpDialogTemplate*  
 指向包含用于创建对话框中的对话框模板的内存。 此模板是中的窗体[DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate)结构和控制信息，如 Windows SDK 中所述。  
  
 *pParentWnd*  
 指向对话框对象的父窗口对象 (类型的[CWnd](../../mfc/reference/cwnd-class.md))。 如果它为 NULL，对话框对象的父窗口设置为应用程序主窗口。  
  
 *lpDialogInit*  
 指向 DLGINIT 资源。  
  
 *hDialogTemplate*  
 包含指向包含对话框模板的全局内存句柄。 此模板中的窗体是`DLGTEMPLATE`结构和每个控件在对话框中的数据。  
  
### <a name="return-value"></a>返回值  
 如果对话框的已创建并初始化成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 `CreateIndirect`成员函数将创建该对话框后立即返回。  
  
 如果创建父窗口时，应显示该对话框，请使用对话框模板中的 WS_VISIBLE 样式。 否则，必须调用`ShowWindow`以使其显示。 有关如何在模板中指定其他对话框样式的详细信息，请参阅[DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate) Windows SDK 中的结构。  
  
 使用`CWnd::DestroyWindow`函数来销毁对话框中创建的`CreateIndirect`函数。  
  
 包含 ActiveX 控件的对话框需要 DLGINIT 资源中提供的其他信息。 有关详细信息，请参阅知识库文章 Q231591，"如何： 使用对话框模板创建一个 MFC 对话框使用 ActiveX 控件。" 知识库文章位于[ http://support.microsoft.com ](http://support.microsoft.com/)。  
  
##  <a name="domodal"></a>  CDialog::DoModal  
 调用此成员函数以调用模式对话框并返回完成的对话框结果。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 **Int**值，该值指定的值*n 结果*参数传递给[CDialog::EndDialog](#enddialog)成员函数，用于关闭对话框。 返回值为-1，如果发生某些其他错误，在这种情况下，输出窗口将包含错误信息从函数无法创建对话框中或 IDABORT [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>备注  
 对话框中处于活动状态时，此成员函数将处理与用户的所有交互。 这是什么工作使得对话框成为模式;也就是说，用户不能前进行交互与其他窗口对话框的已关闭。  
  
 如果用户单击其中一个在对话框中，例如确定或取消，消息处理程序成员函数时，按键如[OnOK](#onok)或[OnCancel](#oncancel)，调用以尝试关闭该对话框。 默认值`OnOK`成员函数将验证和更新对话框中的数据并关闭对话框与结果 IDOK 和默认`OnCancel`成员函数将关闭该对话框与结果 IDCANCEL 而无需验证或更新对话框中的数据。 您可以重写这些消息处理程序函数来更改其行为。  
  
> [!NOTE]
> `PreTranslateMessage` 现在调用模式对话框框中消息处理。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]  
  
##  <a name="enddialog"></a>  CDialog::EndDialog  
 调用此成员函数以终止模式对话框。  
  
```  
void EndDialog(int nResult);
```  
  
### <a name="parameters"></a>参数  
 *n 结果*  
 包含要从对话框返回给调用方的值`DoModal`。  
  
### <a name="remarks"></a>备注  
 此成员函数将返回*n 结果*的返回值作为`DoModal`。 必须使用`EndDialog`函数来完成处理每当创建模式对话框。  
  
 您可以调用`EndDialog`在任何时候，即使是在[OnInitDialog](#oninitdialog)，在这种情况下，应关闭对话框前的所示，或设置输入的焦点之前。  
  
 `EndDialog` 不会立即关闭对话框。 相反，它设置一个标志，指示当前消息处理程序返回后立即关闭对话框。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]  
  
##  <a name="getdefid"></a>  CDialog::GetDefID  
 调用`GetDefID`成员函数以获取的对话框中的默认按钮控件的 ID。  
  
```  
DWORD GetDefID() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个 32 位值 ( `DWORD`)。 如果默认 pushbutton 具有的 ID 值，高序位字包含 DC_HASDEFID，低序位字包含的 ID 值。 如果默认 pushbutton 不具有的 ID 值，则返回值为 0。  
  
### <a name="remarks"></a>备注  
 这通常是确定按钮。  
  
##  <a name="gotodlgctrl"></a>  CDialog::GotoDlgCtrl  
 将焦点移到指定控件在对话框中。  
  
```  
void GotoDlgCtrl(CWnd* pWndCtrl);
```  
  
### <a name="parameters"></a>参数  
 *pWndCtrl*  
 标识要接收焦点的窗口 （控制）。  
  
### <a name="remarks"></a>备注  
 若要获取的控件 （子窗口） 将作为传递指向*pWndCtrl*，调用`CWnd::GetDlgItem`成员函数，返回一个指向[CWnd](../../mfc/reference/cwnd-class.md)对象。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CWnd::GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem)。  
  
##  <a name="initmodalindirect"></a>  CDialog::InitModalIndirect  
 调用此成员函数以初始化使用构造内存中的对话框模板的模式对话框对象。  
  
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
 *lpDialogTemplate*  
 指向包含用于创建对话框中的对话框模板的内存。 此模板是中的窗体[DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate)结构和控制信息，如 Windows SDK 中所述。  
  
 *hDialogTemplate*  
 包含指向包含对话框模板的全局内存句柄。 此模板中的窗体是`DLGTEMPLATE`结构和每个控件在对话框中的数据。  
  
 *pParentWnd*  
 指向父或所有者窗口对象 (类型的[CWnd](../../mfc/reference/cwnd-class.md)) 对话框对象属于的。 如果它为 NULL，对话框对象的父窗口设置为应用程序主窗口。  
  
 *lpDialogInit*  
 指向 DLGINIT 资源。  
  
### <a name="return-value"></a>返回值  
 如果对话框对象已创建并初始化成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 若要间接创建模式对话框，请首先分配全局内存块，并填充对话框模板。 然后，调用空`CDialog`构造对话框对象的构造函数。 接下来，调用`InitModalIndirect`存储到内存中对话框模板在句柄。 创建并显示 Windows 对话框中更高版本，当[DoModal](#domodal)调用成员函数。  
  
 包含 ActiveX 控件的对话框需要 DLGINIT 资源中提供的其他信息。 有关详细信息，请参阅知识库文章 Q231591，"如何： 使用对话框模板创建一个 MFC 对话框使用 ActiveX 控件。" 知识库文章位于[ http://support.microsoft.com ](http://support.microsoft.com/)。  
  
##  <a name="mapdialogrect"></a>  CDialog::MapDialogRect  
 若要将一个矩形的对话框单位转换为屏幕单位的调用。  
  
```  
void MapDialogRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 *lpRect*  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，它包含对话框中要转换的坐标。  
  
### <a name="remarks"></a>备注  
 对话框单位是派生自的平均宽度和高度用于对话框文本的字体中字符的当前对话框基本单位根据所述。 一个水平单元是一个第四个对话框基本宽度单位 （） 的一个垂直的单位的八分之一对话框基本高度单元。  
  
 `GetDialogBaseUnits` Windows 函数将返回系统字体的大小信息，但如果在资源定义文件中使用 DS_SETFONT 样式，则可以指定每个对话框不同的字体。 `MapDialogRect` Windows 函数将使用此对话框中的合适的字体。  
  
 `MapDialogRect`成员函数将替换中的对话框单元*lpRect*与屏幕单位 （像素），使该矩形可以用于创建一个对话框，或将控件放在一个框。  
  
##  <a name="nextdlgctrl"></a>  CDialog::NextDlgCtrl  
 将焦点移到下一个控件在对话框中。  
  
```  
void NextDlgCtrl() const;  
```  
  
### <a name="remarks"></a>备注  
 如果焦点位于对话框中的最后一个控件，它会移动到第一个控件。  
  
##  <a name="oncancel"></a>  CDialog::OnCancel  
 当用户单击，框架将调用此方法**取消**或按 ESC 键模式或无模式对话框中的。  
  
```  
virtual void OnCancel();
```  
  
### <a name="remarks"></a>备注  
 重写此方法以执行操作 （如还原旧数据） 当用户关闭对话框中单击**取消**或按 ESC 键。 默认值通过调用关闭模式对话框[EndDialog](#enddialog) ，从而导致[DoModal](#domodal)返回 IDCANCEL。  
  
 如果你实现了**取消**按钮在无模式对话框中，您必须重写`OnCancel`方法并调用[DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow)其内部。 不要调用基类方法，因为它调用`EndDialog`，这将使对话框中不可见，但不是销毁它。  
  
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
 指定是否应用程序已将输入的焦点设置到其中一个控件在对话框中。 如果`OnInitDialog`返回非零值，则 Windows 会将输入的焦点设置到默认位置，在对话框中的第一个控件。 仅当已显式设置输入的焦点到其中一个控件在对话框中，应用程序可以返回 0。  
  
### <a name="remarks"></a>备注  
 Windows 将发送`WM_INITDIALOG`到期间对话框的消息[创建](#create)， [CreateIndirect](#createindirect)，或[DoModal](#domodal)对话框的之前立即发生的调用随即出现。  
  
 如果你想要执行特殊处理对话框的初始化时，重写此方法。 在重写的版本中，首先调用基类`OnInitDialog`但忽略其返回值。 通常会返回`TRUE`从重写的方法。  
  
 Windows 调用`OnInitDialog`到所有 Microsoft 基础类库对话框使用常见的标准全局对话框过程的函数。 它未调用此函数通过消息映射，并因此不需要消息映射条目为此方法。  
  
> [!NOTE]
> 当你使用时，不能重写此方法`CFileDialog`下 Windows Vista 或更高版本操作系统编译的程序中的对象。 有关更改的详细信息`CFileDialog`Windows vista 及更高版本，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]  
  
##  <a name="onok"></a>  CDialog::OnOK  
 当用户单击时调用**确定**按钮 （带有 IDOK ID 的按钮）。  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>备注  
 重写此方法以执行操作时**确定**按钮会被激活。 如果对话框包含自动数据验证和 exchange，此方法的默认实现验证对话框数据并更新你的应用程序中的相应变量。  
  
 如果你实现了**确定**按钮在无模式对话框中，您必须重写`OnOK`方法并调用[DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow)其内部。 不要调用基类方法，因为它调用[EndDialog](#enddialog)这将使对话框中不可见，但不会销毁它。  
  
> [!NOTE]
>  当你使用时，不能重写此方法`CFileDialog`在 Windows XP 下编译的程序中的对象。 有关详细信息`CFileDialog`，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]  
  
##  <a name="onsetfont"></a>  CDialog::OnSetFont  
 指定的字体绘制文本时，将使用对话框控件。  
  
```  
Virtual void OnSetFont(CFont* pFont);
```  
  
### <a name="parameters"></a>参数  
*pFont*<br/>
[in]指定指向将用作此对话框中的所有控件的默认字体的字体。  
  
### <a name="remarks"></a>备注  
 对话框中将使用指定的字体作为默认值的所有控件。  
  
 通常，对话框编辑器的对话框模板资源的一部分设置对话框字体。  
  
> [!NOTE]
> 当你使用时，不能重写此方法`CFileDialog`下 Windows Vista 或更高版本操作系统编译的程序中的对象。 有关更改的详细信息`CFileDialog`Windows vista 及更高版本，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。  
  
##  <a name="prevdlgctrl"></a>  CDialog::PrevDlgCtrl  
 在对话框中，将焦点设置到上一个控件。  
  
```  
void PrevDlgCtrl() const;  
```  
  
### <a name="remarks"></a>备注  
 如果焦点位于对话框中的第一个控件，它会移动到最后一个控件在框中。  
  
##  <a name="setdefid"></a>  CDialog::SetDefID  
 更改对话框中的默认按钮控件。  
  
```  
void SetDefID(UINT nID);
```  
  
### <a name="parameters"></a>参数  
 *nID*  
 指定将成为默认的按钮控件的 ID。  
  
##  <a name="sethelpid"></a>  CDialog::SetHelpID  
 设置对话框的的上下文相关帮助 ID。  
  
```  
void SetHelpID(UINT nIDR);
```  
  
### <a name="parameters"></a>参数  
 *nIDR*  
 指定的上下文相关帮助 id。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 DLGCBR32](../../visual-cpp-samples.md)   
 [MFC 示例 DLGTEMPL](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)

