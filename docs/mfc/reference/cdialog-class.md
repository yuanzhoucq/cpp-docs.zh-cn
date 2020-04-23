---
title: CDialog 类
ms.date: 09/07/2019
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
ms.openlocfilehash: 36913cfdd8beda31136176c966890a90077c1b30
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753366"
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
|[CDialog：CDialog](#cdialog)|构造 `CDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDialog：创建](#create)|初始化 `CDialog` 对象。 创建无模式对话框并将其附加到`CDialog`对象。|
|[CDialog：创建间接](#createindirect)|从内存中的对话框模板创建无模式对话框（不基于资源）。|
|[CDialog：:Do模态](#domodal)|调用模态对话框，并在完成后返回。|
|[CDialog：结束对话](#enddialog)|关闭模式对话框。|
|[CDialog：GetDefID](#getdefid)|获取对话框的默认按钮控件的 ID。|
|[CDialog：GotoDlgCtrl](#gotodlgctrl)|将焦点移动到对话框中的指定对话框控件。|
|[CDialog：in模态间接](#initmodalindirect)|从内存中的对话框模板创建模式对话框（不基于资源）。 参数将一直存储到调用函数`DoModal`为止。|
|[C对话：：映射对话](#mapdialogrect)|将矩形的对话框单位转换为屏幕单位。|
|[CDialog：：下一个DlgCtrl](#nextdlgctrl)|将焦点移动到对话框中的下一个对话框控件。|
|[CDialog：onInitDialog](#oninitdialog)|覆盖以增强对话框初始化。|
|[CDialog：：放大缩小字体功能 放大缩小字体功能](#onsetfont)|覆盖以指定对话框控件在绘制文本时要使用的字体。|
|[CDialog：:PrevDlgCtrl](#prevdlgctrl)|将焦点移动到对话框中的上一个对话框控件。|
|[CDialog：setDefID](#setdefid)|将对话框的默认按钮控件更改为指定的按钮。|
|[CDialog：设置帮助ID](#sethelpid)|为对话框设置上下文相关的帮助 ID。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CDialog：打开取消](#oncancel)|覆盖以执行"取消"按钮或 ESC 键操作。 默认值关闭对话框并`DoModal`返回 IDCANCEL。|
|[CDialog：：OnOK](#onok)|覆盖以在模式对话框中执行"确定"按钮操作。 默认值关闭对话框并`DoModal`返回 IDOK。|

## <a name="remarks"></a>备注

对话框有两种类型：模态和无模式。 在应用程序继续之前，用户必须关闭模式对话框。 无模式对话框允许用户显示对话框并返回到其他任务，而无需取消或删除对话框。

对象`CDialog`是对话框模板和`CDialog`派生类的组合。 使用对话框编辑器创建对话框模板并将其存储在资源中，然后使用"添加类"向导创建派生自 的`CDialog`类。

与任何其他窗口一样，对话框接收来自 Windows 的消息。 在对话框中，您特别有兴趣处理来自对话框控件的通知消息，因为这是用户与对话框交互的方式。 使用[类向导](mfc-class-wizard.md)选择要处理的邮件，它将为您向类添加适当的消息映射条目和消息处理程序成员函数。 您只需在处理程序成员函数中编写特定于应用程序的代码。

如果您愿意，您可以随时手动编写消息映射条目和成员函数。

在除了最琐碎的对话框外的所有对话框中，您将成员变量添加到派生对话框类中，以存储用户在对话框控件中输入的数据或显示用户的数据。 可以使用"添加变量"向导创建成员变量并将其与控件关联。 同时，为每个变量选择变量类型和允许的值范围。 代码向导将成员变量添加到派生对话框类。

生成数据映射以自动处理成员变量和对话框控件之间的数据交换。 数据映射提供函数，用于用正确的值初始化对话框中的控件、检索数据并验证数据。

要创建模态对话框，请使用派生对话框类的构造函数在堆栈上构造对象，然后调用`DoModal`以创建对话框窗口及其控件。 如果要创建无模式对话框，请调用`Create`对话框类的构造函数。

您还可以使用 Windows SDK 中描述的[DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate)数据结构在内存中创建模板。 构造`CDialog`对象后，调用[CreateIndirect](#createindirect)以创建无模式对话框，或调用[InitModal 间接](#initmodalindirect)和[DoModal](#domodal)以创建模式对话框。

交换和验证数据映射以添加到新对话框类的`CWnd::DoDataExchange`重写形式编写。 有关交换和验证功能的更多，请参阅`CWnd`中的[DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)成员函数。

程序员和框架都通过调用`DoDataExchange`[CWnd：：updateData](../../mfc/reference/cwnd-class.md#updatedata)间接调用。

当用户单击"`UpdateData`确定"按钮以关闭模式对话框时，框架将调用。 （如果单击"取消"按钮，则不会检索数据。[OnInitDialog](#oninitdialog)的默认实现还调用`UpdateData`设置控件的初始值。 通常重写`OnInitDialog`以进一步初始化控件。 `OnInitDialog`在创建所有对话框控件后并在显示对话框之前调用。

在执行模式或`CWnd::UpdateData`无模式对话框期间，您可以随时调用。

如果手动开发一个对话框，则自己向派生的对话框类添加必要的成员变量，并添加成员函数来设置或获取这些值。

当用户按下"确定"或"取消"按钮或代码调用`EndDialog`成员函数时，模式对话框将自动关闭。

实现无模式对话框时，始终覆盖`OnCancel`成员函数并从其中调用。 `DestroyWindow` 不要调用基类`CDialog::OnCancel`，因为它调用`EndDialog`，这将使对话框不可见，但不会破坏它。 您还应重写`PostNcDestroy`无模式对话框，以便删除**此**，因为无模式对话框通常使用**new**分配。 模态对话框通常构建在框架上，不需要`PostNcDestroy`清理。

有关 的详细信息`CDialog`，请参阅[对话框](../../mfc/dialog-boxes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDialog`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cdialogcdialog"></a><a name="cdialog"></a>CDialog：CDialog

要构造基于资源的模式对话框，请调用构造函数的两种公共形式。

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

*lpszTemplate 名称*<br/>
包含一个 null 端接字符串，该字符串是对话框模板资源的名称。

*nIDTemplate*<br/>
包含对话框模板资源的 ID 号。

*pparentwnd*<br/>
指向对话框对象所属的父窗口或所有者窗口对象[（CWnd](../../mfc/reference/cwnd-class.md)类型）。 如果为 NULL，则对话框对象的父窗口将设置为主应用程序窗口。

### <a name="remarks"></a>备注

构造函数的一种形式按模板名称提供对对话框资源的访问。 另一个构造函数按模板 ID 号提供访问，通常带有**IDD_** 前缀（例如，IDD_DIALOG1）。

要从内存中的模板构造模态对话框，请先调用无参数、受保护的构造函数，然后调用`InitModalIndirect`。

使用上述方法之一构造模式对话框后，调用`DoModal`。

要构造无模式对话框，请使用`CDialog`构造函数的受保护形式。 构造函数受到保护，因为必须派生自己的对话框类才能实现无模式对话框。 构建无模式对话框是一个两步过程。 首先调用构造函数;然后调用`Create`成员函数以创建基于资源的对话框，或调用`CreateIndirect`从内存中的模板创建对话框。

## <a name="cdialogcreate"></a><a name="create"></a>CDialog：创建

调用`Create`使用来自资源的对话框模板创建无模式对话框。

```
virtual BOOL Create(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd = NULL);

virtual BOOL Create(
    UINT nIDTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>参数

*lpszTemplate 名称*<br/>
包含一个 null 端接字符串，该字符串是对话框模板资源的名称。

*pparentwnd*<br/>
指向对话框对象所属的父窗口对象[（CWnd](../../mfc/reference/cwnd-class.md)类型）。 如果为 NULL，则对话框对象的父窗口将设置为主应用程序窗口。

*nIDTemplate*<br/>
包含对话框模板资源的 ID 号。

### <a name="return-value"></a>返回值

如果对话框创建和初始化成功，则两种窗体都返回非零;否则 0。

### <a name="remarks"></a>备注

可以将调用放在`Create`构造函数内部，或在调用构造函数后调用它。

`Create`提供了两种形式的成员函数，以便通过模板名称或模板 ID 号（例如，IDD_DIALOG1）访问对话框模板资源。

对于任一窗体，将指针传递给父窗口对象。 如果*pParentWnd*为 NULL，则对话框将创建其父窗口或所有者窗口设置为主应用程序窗口。

成员`Create`函数在创建对话框后立即返回。

如果在创建父窗口时应显示对话框，则在对话框模板中使用WS_VISIBLE样式。 否则，您必须调用`ShowWindow`。 有关进一步的对话框样式及其应用程序，请参阅*MFC 参考*中的 Windows SDK 和[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)中的[DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate)结构。

使用`CWnd::DestroyWindow`函数销毁由`Create`该函数创建的对话框。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]

## <a name="cdialogcreateindirect"></a><a name="createindirect"></a>CDialog：创建间接

调用此成员函数从内存中的对话框模板创建无模式对话框。

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

*lpDialog模板*<br/>
包含用于创建对话框的对话框模板的内存点。 此模板以[DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate)结构和控制信息的形式出现，如 Windows SDK 中所述。

*pparentwnd*<br/>
指向对话框对象的父窗口对象[（CWnd](../../mfc/reference/cwnd-class.md)类型）。 如果为 NULL，则对话框对象的父窗口将设置为主应用程序窗口。

*lpDialogInit*<br/>
指向 DLGINIT 资源。

*h对话模板*<br/>
包含包含对话框模板的全局内存的句柄。 此模板以对话框中每个控件的`DLGTEMPLATE`结构和数据的形式出现。

### <a name="return-value"></a>返回值

如果对话框已成功创建并初始化，则非零;否则 0。

### <a name="remarks"></a>备注

成员`CreateIndirect`函数在创建对话框后立即返回。

如果在创建父窗口时应显示对话框，则在对话框模板中使用WS_VISIBLE样式。 否则，必须调用`ShowWindow`以使其显示。 有关如何在模板中指定其他对话框样式的详细信息，请参阅 Windows SDK 中的[DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate)结构。

使用`CWnd::DestroyWindow`函数销毁由`CreateIndirect`该函数创建的对话框。

包含 ActiveX 控件的对话框需要 DLGINIT 资源中提供的其他信息。

## <a name="cdialogdomodal"></a><a name="domodal"></a>CDialog：:Do模态

调用此成员函数以调用模态对话框，并在完成后返回对话框结果。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

指定传递给[CDialog：endDialog](#enddialog)成员函数的*nResult*参数的值的**int**值，用于关闭对话框。 如果函数无法创建对话框，则返回值为 -1;如果发生其他错误，则返回值为 -1，如果发生其他错误，则返回值为 -1，在这种情况下，输出窗口将包含[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)中的错误信息。

### <a name="remarks"></a>备注

此成员函数处理与用户的所有交互，当对话框处于活动状态时。 这就是使对话框模态的原因;也就是说，在关闭对话框之前，用户无法与其他窗互。

如果用户单击对话框中的一个按钮（如"确定"或"取消"），则会调用消息处理程序成员函数（如[OnOK](#onok)或[OnCancel）](#oncancel)以尝试关闭该对话框。 默认`OnOK`成员函数将验证和更新对话框数据，并关闭具有结果 IDOK 的对话框，默认`OnCancel`成员函数将关闭具有结果 IDCANCEL 的对话框，而无需验证或更新对话框数据。 您可以重写这些消息处理程序函数来更改其行为。

> [!NOTE]
> `PreTranslateMessage`现在调用模态对话框消息处理。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]

## <a name="cdialogenddialog"></a><a name="enddialog"></a>CDialog：结束对话

调用此成员函数以终止模式对话框。

```cpp
void EndDialog(int nResult);
```

### <a name="parameters"></a>参数

*nResult*<br/>
包含要从对话框返回到 的调用方的值`DoModal`。

### <a name="remarks"></a>备注

此成员函数返回*nResult*作为 的`DoModal`返回值。 每当创建模式对话框`EndDialog`时，都必须使用 函数完成处理。

您可以随时调用`EndDialog`，即使在[OnInitDialog](#oninitdialog)中，在显示对话框之前或设置输入焦点之前，也应关闭该对话框。

`EndDialog`不会立即关闭该对话框。 相反，它会设置一个标志，指示对话框在当前消息处理程序返回后立即关闭。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]

[!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]

## <a name="cdialoggetdefid"></a><a name="getdefid"></a>CDialog：GetDefID

调用`GetDefID`成员函数获取对话框的默认按钮控件的 ID。

```
DWORD GetDefID() const;
```

### <a name="return-value"></a>返回值

32 位值 （ `DWORD`。 如果默认按钮具有 ID 值，则高阶单词包含DC_HASDEFID，低阶单词包含 ID 值。 如果默认按钮没有 ID 值，则返回值为 0。

### <a name="remarks"></a>备注

这通常是一个确定按钮。

## <a name="cdialoggotodlgctrl"></a><a name="gotodlgctrl"></a>CDialog：GotoDlgCtrl

将焦点移动到对话框中的指定控件。

```cpp
void GotoDlgCtrl(CWnd* pWndCtrl);
```

### <a name="parameters"></a>参数

*pWndCtrl*<br/>
标识接收焦点的窗口（控件）。

### <a name="remarks"></a>备注

要获取指向控件（子窗口）的指针以*pWndCtrl*身份传递，请`CWnd::GetDlgItem`调用成员函数，该函数返回指向[CWnd](../../mfc/reference/cwnd-class.md)对象的指针。

### <a name="example"></a>示例

  请参阅[CWnd 的示例：GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem)。

## <a name="cdialoginitmodalindirect"></a><a name="initmodalindirect"></a>CDialog：in模态间接

调用此成员函数，使用您在内存中构造的对话框模板初始化模式对话框对象。

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

*lpDialog模板*<br/>
包含用于创建对话框的对话框模板的内存点。 此模板以[DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate)结构和控制信息的形式出现，如 Windows SDK 中所述。

*h对话模板*<br/>
包含包含对话框模板的全局内存的句柄。 此模板以对话框中每个控件的`DLGTEMPLATE`结构和数据的形式出现。

*pparentwnd*<br/>
指向对话框对象所属的父窗口或所有者窗口对象[（CWnd](../../mfc/reference/cwnd-class.md)类型）。 如果为 NULL，则对话框对象的父窗口将设置为主应用程序窗口。

*lpDialogInit*<br/>
指向 DLGINIT 资源。

### <a name="return-value"></a>返回值

如果对话框对象已成功创建并初始化，则非零;否则 0。

### <a name="remarks"></a>备注

要间接创建模式对话框，请先分配全局内存块，然后用对话框模板填充它。 然后调用空`CDialog`构造函数来构造对话框对象。 接下来，调用`InitModalIndirect`将句柄存储到内存中对话框模板。 稍后调用[DoModal](#domodal)成员函数时，将创建并显示 Windows 对话框。

包含 ActiveX 控件的对话框需要 DLGINIT 资源中提供的其他信息。

## <a name="cdialogmapdialogrect"></a><a name="mapdialogrect"></a>C对话：：映射对话

调用以将矩形的对话框单位转换为屏幕单位。

```cpp
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向包含要转换的对话框坐标的[RECT](/windows/win32/api/windef/ns-windef-rect)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象。

### <a name="remarks"></a>备注

对话框单位根据当前对话框基本单位表示，该单位派生自对话框文本字体中字符的平均宽度和高度。 一个水平单位是对话框基宽单位的四分之一，一个垂直单位是对话框基本高度单位的八分之一。

Windows`GetDialogBaseUnits`函数返回系统字体的大小信息，但如果在资源定义文件中使用DS_SETFONT样式，则可以为每个对话框指定不同的字体。 Windows`MapDialogRect`函数为此对话框使用相应的字体。

成员`MapDialogRect`函数将*lpRect*中的对话框单元替换为屏幕单位（像素），以便矩形可用于创建对话框或在框中放置控件。

## <a name="cdialognextdlgctrl"></a><a name="nextdlgctrl"></a>CDialog：：下一个DlgCtrl

将焦点移到对话框中的下一个控件。

```cpp
void NextDlgCtrl() const;
```

### <a name="remarks"></a>备注

如果焦点位于对话框中的最后一个控件，则它移动到第一个控件。

## <a name="cdialogoncancel"></a><a name="oncancel"></a>CDialog：打开取消

当用户单击 **"取消"** 或在模态或无模式对话框中按 ESC 键时，框架将调用此方法。

```
virtual void OnCancel();
```

### <a name="remarks"></a>备注

在用户通过单击 **"取消"** 或单击 ESC 键关闭对话框时，重写此方法以执行操作（如还原旧数据）。 默认值通过调用[EndDialog](#enddialog)并导致[DoModal](#domodal)返回 IDCANCEL 来关闭模式对话框。

如果在无模式对话框中实现 **"取消"** 按钮，则必须重写`OnCancel`该方法并在其中调用["销毁窗口](../../mfc/reference/cwnd-class.md#destroywindow)"。 不要调用基类方法，因为它调用`EndDialog`，这将使对话框不可见，但不会破坏它。

> [!NOTE]
> 在 Windows XP 下编译的程序`CFileDialog`中使用对象时，无法重写此方法。 有关 的详细信息`CFileDialog`，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]

## <a name="cdialogoninitdialog"></a><a name="oninitdialog"></a>CDialog：onInitDialog

调用此方法以响应消息`WM_INITDIALOG`。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>返回值

指定应用程序是否已将输入焦点设置为对话框中的一个控件。 如果`OnInitDialog`返回非零，Windows 会将输入焦点设置到默认位置，即对话框中的第一个控件。 仅当应用程序显式将输入焦点设置为对话框中的一个控件时，应用程序才能返回 0。

### <a name="remarks"></a>备注

Windows 在`WM_INITDIALOG`["创建](#create)、[创建间接](#createindirect)"或["DoModal"](#domodal)调用期间将消息发送到对话框，这些调用在显示对话框之前发生。

如果要在初始化对话框时执行特殊处理，则重写此方法。 在重写版本中，首先调用基类`OnInitDialog`，但忽略其返回值。 您通常会从重写`TRUE`的方法返回。

Windows 使用`OnInitDialog`所有 Microsoft 基础类库对话框共有的标准全局对话框过程调用该函数。 它不通过消息映射调用此函数，因此不需要此方法的消息映射条目。

> [!NOTE]
> 在 Windows Vista 或更高版本的`CFileDialog`操作系统下编译的程序中使用对象时，无法重写此方法。 有关 Windows Vista`CFileDialog`下和更高版本更改的详细信息，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]

## <a name="cdialogonok"></a><a name="onok"></a>CDialog：：OnOK

当用户单击 **"确定"** 按钮（IDOK IDOK 的按钮）时调用。

```
virtual void OnOK();
```

### <a name="remarks"></a>备注

重写此方法，在激活 **"确定"** 按钮时执行操作。 如果对话框包括自动数据验证和交换，则此方法的默认实现将验证对话框数据并更新应用程序中的相应变量。

如果在无模式对话框中实现 **"确定"** 按钮，则必须重写`OnOK`该方法并在其中调用["销毁窗口](../../mfc/reference/cwnd-class.md#destroywindow)"。 不要调用基类方法，因为它调用[EndDialog，](#enddialog)它使对话框不可见，但不会破坏它。

> [!NOTE]
> 在 Windows XP 下编译的程序`CFileDialog`中使用对象时，无法重写此方法。 有关 的详细信息`CFileDialog`，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]

## <a name="cdialogonsetfont"></a><a name="onsetfont"></a>CDialog：：放大缩小字体功能 放大缩小字体功能

指定绘制文本时对话框控件将使用的字体。

```
Virtual void OnSetFont(CFont* pFont);
```

### <a name="parameters"></a>参数

*pFont*<br/>
[在]指定指向字体的指针，该指针将用作此对话框中所有控件的默认字体。

### <a name="remarks"></a>备注

该对话框将使用指定的字体作为其所有控件的默认值。

对话框编辑器通常将对话框字体设置为对话框模板资源的一部分。

> [!NOTE]
> 在 Windows Vista 或更高版本的`CFileDialog`操作系统下编译的程序中使用对象时，无法重写此方法。 有关 Windows Vista`CFileDialog`下和更高版本更改的详细信息，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。

## <a name="cdialogprevdlgctrl"></a><a name="prevdlgctrl"></a>CDialog：:PrevDlgCtrl

将焦点设置到对话框中以前的控件。

```cpp
void PrevDlgCtrl() const;
```

### <a name="remarks"></a>备注

如果焦点位于对话框中的第一个控件处，它将移动到框中的最后一个控件。

## <a name="cdialogsetdefid"></a><a name="setdefid"></a>CDialog：setDefID

更改对话框的默认按钮控件。

```cpp
void SetDefID(UINT nID);
```

### <a name="parameters"></a>参数

*nID*<br/>
指定将成为默认值的按钮控件的 ID。

## <a name="cdialogsethelpid"></a><a name="sethelpid"></a>CDialog：设置帮助ID

为对话框设置上下文相关的帮助 ID。

```cpp
void SetHelpID(UINT nIDR);
```

### <a name="parameters"></a>参数

*尼德*<br/>
指定上下文相关的帮助 ID。

## <a name="see-also"></a>请参阅

[MFC 样品 DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 DLGTEMPL](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
