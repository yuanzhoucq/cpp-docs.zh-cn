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
ms.openlocfilehash: b07190c70fb11950b25aff45fb10e850c0e81b24
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865103"
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
|[CDialog：： CDialog](#cdialog)|构造 `CDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDialog：： Create](#create)|初始化 `CDialog` 对象。 创建无模式对话框，并将其附加到 `CDialog` 对象上。|
|[CDialog：： CreateIndirect](#createindirect)|从内存中的对话框模板创建无模式对话框（不是基于资源的）。|
|[CDialog：:D oModal](#domodal)|调用模式对话框并在完成时返回。|
|[CDialog：： EndDialog](#enddialog)|关闭模式对话框。|
|[CDialog：： GetDefID](#getdefid)|获取对话框的默认按钮控件的 ID。|
|[CDialog：： GotoDlgCtrl](#gotodlgctrl)|将焦点移到对话框中的指定对话框控件。|
|[CDialog：： InitModalIndirect](#initmodalindirect)|从内存中的对话框模板创建模式对话框（不是基于资源的）。 参数会一直存储，直到调用函数 `DoModal`。|
|[CDialog：： MapDialogRect](#mapdialogrect)|将矩形的对话框单位转换为屏幕单位。|
|[CDialog：： NextDlgCtrl](#nextdlgctrl)|将焦点移到对话框中的下一个对话框控件。|
|[CDialog：： OnInitDialog](#oninitdialog)|重写以增加对话框初始化。|
|[CDialog：： OnSetFont](#onsetfont)|重写以指定对话框控件在绘制文本时使用的字体。|
|[CDialog：:P revDlgCtrl](#prevdlgctrl)|将焦点移到对话框中的上一个对话框控件。|
|[CDialog：： SetDefID](#setdefid)|将对话框的默认按钮控件更改为指定的按钮。|
|[CDialog：： SetHelpID](#sethelpid)|为对话框设置区分上下文的帮助 ID。|

### <a name="protected-methods"></a>受保护方法

|名称|说明|
|----------|-----------------|
|[CDialog：： OnCancel](#oncancel)|重写以执行 "取消" 按钮或 ESC 键操作。 默认关闭对话框并 `DoModal` 返回 IDCANCEL。|
|[CDialog：： OnOK](#onok)|重写以在模式对话框中执行 "确定" 按钮操作。 默认关闭对话框并 `DoModal` 返回 IDOK。|

## <a name="remarks"></a>备注

对话框分为两种类型：模式和无模式。 在应用程序继续之前，用户必须关闭模式对话框。 无模式对话框允许用户在不取消或删除对话框的情况下显示对话框并返回到其他任务。

`CDialog` 对象是对话框模板和 `CDialog`派生类的组合。 使用对话框编辑器创建对话框模板并将其存储在资源中，然后使用添加类向导创建派生自 `CDialog`的类。

对话框与任何其他窗口一样，接收来自 Windows 的消息。 在对话框中，您特别希望处理来自对话框的控件发出的通知消息，因为这是用户与您的对话框进行交互的方式。 使用[类向导](mfc-class-wizard.md)可以选择要处理的消息，并将相应的消息映射项和消息处理程序成员函数添加到类。 只需在处理程序成员函数中编写特定于应用程序的代码即可。

如果您愿意，您始终可以手动编写消息映射项和成员函数。

在除最普通对话框以外的所有对话框中，您可以向派生对话框类添加成员变量，以存储用户在对话框控件中输入的数据或显示用户的数据。 您可以使用 "添加变量向导" 创建成员变量并将其与控件相关联。 同时，为每个变量选择变量类型和允许的值范围。 代码向导将成员变量添加到您的派生对话框类。

系统将生成数据映射，以自动处理成员变量与对话框控件之间的数据交换。 数据映射提供了一些函数，这些函数用适当的值初始化对话框中的控件，检索数据并验证数据。

若要创建模式对话框，请使用派生对话框类的构造函数在堆栈上构造对象，然后调用 `DoModal` 创建对话框窗口及其控件。 若要创建无模式对话框，请调用对话框类的构造函数中的 `Create`。

还可以使用[DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate)数据结构在内存中创建模板，如 Windows SDK 中所述。 构造 `CDialog` 对象后，调用[CreateIndirect](#createindirect)创建无模式对话框，或调用[InitModalIndirect](#initmodalindirect)和[DoModal](#domodal)创建模式对话框。

交换和验证数据映射以添加到新对话框类的 `CWnd::DoDataExchange` 的替代来编写。 有关 exchange 和验证功能的详细信息，请参阅 `CWnd` 中的[DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)成员函数。

程序员和 framework 都通过调用[CWnd：： UpdateData](../../mfc/reference/cwnd-class.md#updatedata)间接调用 `DoDataExchange`。

当用户单击 "确定" 按钮关闭模式对话框时，框架会调用 `UpdateData`。 （如果单击 "取消" 按钮，则不会检索数据。）[OnInitDialog](#oninitdialog)的默认实现还调用 `UpdateData` 以设置控件的初始值。 通常会重写 `OnInitDialog` 以便进一步初始化控件。 在创建所有对话框控件之后，在对话框显示之前调用 `OnInitDialog`。

在执行模式对话框或无模式对话框的过程中，您可以随时调用 `CWnd::UpdateData`。

如果手动开发一个对话框，则需要自行向派生对话框类添加必要的成员变量，并添加成员函数以设置或获取这些值。

当用户按 "确定" 或 "取消" 按钮时，或者当你的代码调用 `EndDialog` 成员函数时，模式对话框将自动关闭。

实现无模式对话框时，请始终重写 `OnCancel` 成员函数并从中调用 `DestroyWindow`。 请勿调用基类 `CDialog::OnCancel`，因为它调用了 `EndDialog`，这会使对话框不可见，但不会将其销毁。 还应覆盖无模式对话框的 `PostNcDestroy`，以便删除**该**对话框，因为无模式对话框通常是用**new**分配的。 模式对话框通常在帧上构造，无需 `PostNcDestroy` 清理。

有关 `CDialog`的详细信息，请参阅[对话框](../../mfc/dialog-boxes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDialog`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cdialog"></a>CDialog：： CDialog

若要构造基于资源的模式对话框，请调用构造函数的公共形式。

```
explicit CDialog(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd = NULL);

explicit CDialog(
    UINT nIDTemplate,
    CWnd* pParentWnd = NULL);

CDialog();
```

### <a name="parameters"></a>parameters

*lpszTemplateName*<br/>
包含一个以 null 结尾的字符串，它是对话框模板资源的名称。

*nIDTemplate*<br/>
包含对话框模板资源的 ID 号。

*pParentWnd*<br/>
指向对话框对象所属的父对象或所有者窗口对象（类型为[CWnd](../../mfc/reference/cwnd-class.md)）。 如果为 NULL，则对话框对象的父窗口将设置为主应用程序窗口。

### <a name="remarks"></a>备注

构造函数的一种形式提供按模板名称对对话框资源的访问。 其他构造函数提供按模板 ID 号进行访问，通常使用**IDD_** 前缀（例如，IDD_DIALOG1）。

若要从内存中的模板构造模式对话框，请首先调用无参数的、受保护的构造函数，然后调用 `InitModalIndirect`。

使用上述方法之一构造模式对话框后，调用 `DoModal`。

若要构造无模式对话框，请使用受保护的 `CDialog` 构造函数形式。 此构造函数是受保护的，因为必须派生自己的对话框类来实现无模式对话框。 无模式对话框的构造是一个两步过程。 首先调用构造函数;然后调用 `Create` 成员函数以创建基于资源的对话框，或调用 `CreateIndirect` 以从内存中的模板创建对话框。

##  <a name="create"></a>CDialog：： Create

调用 `Create`，使用资源的对话框模板创建无模式对话框。

```
virtual BOOL Create(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd = NULL);

virtual BOOL Create(
    UINT nIDTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>parameters

*lpszTemplateName*<br/>
包含一个以 null 结尾的字符串，它是对话框模板资源的名称。

*pParentWnd*<br/>
指向对话框对象所属的父窗口对象（类型为[CWnd](../../mfc/reference/cwnd-class.md)）。 如果为 NULL，则对话框对象的父窗口将设置为主应用程序窗口。

*nIDTemplate*<br/>
包含对话框模板资源的 ID 号。

### <a name="return-value"></a>返回值

如果对话框创建和初始化成功，两个窗体都将返回非零值;否则为0。

### <a name="remarks"></a>备注

可以在构造函数中调用 `Create`，或在调用构造函数后调用它。

提供了两种形式的 `Create` 成员函数以便按模板名称或模板 ID 号（例如 IDD_DIALOG1）访问对话框模板资源。

对于任一窗体，传递指向父窗口对象的指针。 如果*pParentWnd*为 NULL，则将创建对话框，并将其父窗口或所有者窗口设置为主应用程序窗口。

`Create` 成员函数在创建该对话框后立即返回。

如果在创建父窗口时显示对话框，则在对话框模板中使用 WS_VISIBLE 样式。 否则，必须调用 `ShowWindow`。 若要进一步了解对话框样式及其应用程序，请参阅*MFC 参考*中的 Windows SDK 和[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)中的[DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate)结构。

使用 `CWnd::DestroyWindow` 函数可销毁由 `Create` 函数创建的对话框。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]

##  <a name="createindirect"></a>CDialog：： CreateIndirect

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

### <a name="parameters"></a>parameters

*lpDialogTemplate*<br/>
指向包含用于创建对话框的对话框模板的内存。 此模板的形式为[DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate)结构和控制信息，如 Windows SDK 中所述。

*pParentWnd*<br/>
指向对话框对象的父窗口对象（类型为[CWnd](../../mfc/reference/cwnd-class.md)）。 如果为 NULL，则对话框对象的父窗口将设置为主应用程序窗口。

*lpDialogInit*<br/>
指向 DLGINIT 资源。

*hDialogTemplate*<br/>
包含包含对话框模板的全局内存的句柄。 此模板的形式为对话框中每个控件的 `DLGTEMPLATE` 结构和数据。

### <a name="return-value"></a>返回值

如果已成功创建并初始化了对话框，则为非零值;否则为0。

### <a name="remarks"></a>备注

`CreateIndirect` 成员函数在创建该对话框后立即返回。

如果在创建父窗口时显示对话框，则在对话框模板中使用 WS_VISIBLE 样式。 否则，必须调用 `ShowWindow` 以使其显示。 有关如何在模板中指定其他对话框样式的详细信息，请参阅 Windows SDK 中的[DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate)结构。

使用 `CWnd::DestroyWindow` 函数可销毁由 `CreateIndirect` 函数创建的对话框。

包含 ActiveX 控件的对话框需要在 DLGINIT 资源中提供其他信息。

##  <a name="domodal"></a>CDialog：:D oModal

调用此成员函数以调用模式对话框并在完成后返回对话框结果。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

一个**整数**值，该值指定传递给[CDialog：： EndDialog](#enddialog)成员函数的*n 结果*参数的值，该参数用于关闭对话框。 如果函数无法创建对话框，则返回值为-1; 如果发生其他错误，则返回值为 IDABORT，在这种情况下，"输出" 窗口将包含来自[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)的错误信息。

### <a name="remarks"></a>备注

当对话框处于活动状态时，此成员函数将处理与用户的所有交互。 这就是使对话框模式的：也就是说，在关闭该对话框之前，用户无法与其他窗口交互。

如果用户在对话框中单击其中一个按钮（如 "确定" 或 "取消"），则会调用消息处理程序成员函数（如[OnOK](#onok)或[OnCancel](#oncancel)），尝试关闭对话框。 默认 `OnOK` 成员函数将验证和更新对话框数据，并关闭带有 result IDOK 的对话框，并且默认的 `OnCancel` 成员函数将关闭带有 result IDCANCEL 的对话框，而不验证或更新对话框数据。 你可以重写这些消息处理函数来更改它们的行为。

> [!NOTE]
> 现在为模式对话框消息处理调用 `PreTranslateMessage`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]

##  <a name="enddialog"></a>CDialog：： EndDialog

调用此成员函数以终止模式对话框。

```
void EndDialog(int nResult);
```

### <a name="parameters"></a>parameters

*N 结果*<br/>
包含要从对话框返回 `DoModal`的调用方的值。

### <a name="remarks"></a>备注

此成员函数返回*n 结果*作为 `DoModal`的返回值。 每当创建模式对话框时，都必须使用 `EndDialog` 函数完成处理。

即使是在[OnInitDialog](#oninitdialog)中，也可以在任何时候调用 `EndDialog`，在这种情况下，应在显示对话框之前或在设置输入焦点之前关闭对话框。

`EndDialog` 不会立即关闭对话框。 相反，它将设置一个标志，该标志指示对话框在当前消息处理程序返回后立即关闭。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]

[!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]

##  <a name="getdefid"></a>CDialog：： GetDefID

调用 `GetDefID` 成员函数以获取对话框默认按钮控件的 ID。

```
DWORD GetDefID() const;
```

### <a name="return-value"></a>返回值

32位值（`DWORD`）。 如果默认按键有一个 ID 值，则高序位字包含 DC_HASDEFID 并且低序位字包含 ID 值。 如果默认按键没有 ID 值，则返回值为0。

### <a name="remarks"></a>备注

这通常是 "确定" 按钮。

##  <a name="gotodlgctrl"></a>CDialog：： GotoDlgCtrl

将焦点移动到对话框中的指定控件。

```
void GotoDlgCtrl(CWnd* pWndCtrl);
```

### <a name="parameters"></a>parameters

*pWndCtrl*<br/>
标识要接收焦点的窗口（控件）。

### <a name="remarks"></a>备注

若要获取指向控件的指针（子窗口）以作为*pWndCtrl*传递，请调用 `CWnd::GetDlgItem` 成员函数，该函数返回指向[CWnd](../../mfc/reference/cwnd-class.md)对象的指针。

### <a name="example"></a>示例

  请参阅[CWnd：： GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem)的示例。

##  <a name="initmodalindirect"></a>CDialog：： InitModalIndirect

使用在内存中构造的对话框模板调用此成员函数来初始化模式对话框对象。

```
BOOL InitModalIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,
    CWnd* pParentWnd = NULL,
    void* lpDialogInit = NULL);

    BOOL InitModalIndirect(
    HGLOBAL hDialogTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>parameters

*lpDialogTemplate*<br/>
指向包含用于创建对话框的对话框模板的内存。 此模板的形式为[DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate)结构和控制信息，如 Windows SDK 中所述。

*hDialogTemplate*<br/>
包含包含对话框模板的全局内存的句柄。 此模板的形式为对话框中每个控件的 `DLGTEMPLATE` 结构和数据。

*pParentWnd*<br/>
指向对话框对象所属的父对象或所有者窗口对象（类型为[CWnd](../../mfc/reference/cwnd-class.md)）。 如果为 NULL，则对话框对象的父窗口将设置为主应用程序窗口。

*lpDialogInit*<br/>
指向 DLGINIT 资源。

### <a name="return-value"></a>返回值

如果成功创建并初始化对话框对象，则为非零值;否则为0。

### <a name="remarks"></a>备注

若要间接创建模式对话框，请首先分配全局内存块并使用对话框模板填充它。 然后调用空的 `CDialog` 构造函数来构造对话框对象。 接下来，调用 `InitModalIndirect` 将句柄存储在 "内存中" 对话框模板中。 当调用[DoModal](#domodal)成员函数时，将创建并显示 Windows 对话框。

包含 ActiveX 控件的对话框需要在 DLGINIT 资源中提供其他信息。

##  <a name="mapdialogrect"></a>CDialog：： MapDialogRect

调用以将矩形的对话框单位转换为屏幕单位。

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>parameters

*lpRect*<br/>
指向一个[RECT](/windows/win32/api/windef/ns-windef-rect)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，其中包含要转换的对话框坐标。

### <a name="remarks"></a>备注

对话框单位根据当前的对话框基本单位进行说明，该基本单位是从用于对话框文本的字体中的字符的平均宽度和高度派生的。 一个水平单位是对话框基数宽度单位的第四个，而一个垂直单位是对话框基准高度单位的八分之一。

`GetDialogBaseUnits` Windows 函数返回系统字体的大小信息，但如果在资源定义文件中使用 DS_SETFONT 样式，则可以为每个对话框指定不同的字体。 `MapDialogRect` Windows 函数为此对话框使用适当的字体。

`MapDialogRect` 成员函数将*lpRect*中的对话框单位替换为屏幕单位（像素），以便可以使用该矩形来创建对话框或将控件放置在一个框中。

##  <a name="nextdlgctrl"></a>CDialog：： NextDlgCtrl

将焦点移至对话框中的下一个控件。

```
void NextDlgCtrl() const;
```

### <a name="remarks"></a>备注

如果焦点位于对话框中的最后一个控件上，则它会移动到第一个控件。

##  <a name="oncancel"></a>CDialog：： OnCancel

当用户在模式对话框或无模式对话框中单击 "**取消**" 或按 ESC 键时，框架会调用此方法。

```
virtual void OnCancel();
```

### <a name="remarks"></a>备注

重写此方法以在用户关闭对话框时通过单击 "**取消**" 或按 ESC 键来执行操作（如还原旧数据）。 默认情况下，通过调用[EndDialog](#enddialog)并导致[DoModal](#domodal)返回 IDCANCEL 来关闭模式对话框。

如果在无模式对话框中实现 "**取消**" 按钮，则必须重写 `OnCancel` 方法，并在其中调用[DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) 。 请勿调用基类方法，因为它调用 `EndDialog`，这会使对话框不可见，但不会将其销毁。

> [!NOTE]
>  在 Windows XP 下编译的程序中使用 `CFileDialog` 对象时，不能重写此方法。 有关 `CFileDialog`的详细信息，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]

##  <a name="oninitdialog"></a>CDialog：： OnInitDialog

调用此方法是为了响应 `WM_INITDIALOG` 消息。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>返回值

指定应用程序是否已将输入焦点设置到对话框中的某个控件。 如果 `OnInitDialog` 返回非零值，则 Windows 将输入焦点设置到对话框中的第一个控件。 仅当应用程序已将输入焦点显式设置到对话框中的某个控件时，应用程序才能返回0。

### <a name="remarks"></a>备注

在[创建](#create)、 [CreateIndirect](#createindirect)或[DoModal](#domodal)调用期间，Windows 会将 `WM_INITDIALOG` 消息发送到对话框，这会在对话框显示之前立即发生。

如果要在初始化对话框时执行特殊处理，请重写此方法。 在重写的版本中，首先调用基类 `OnInitDialog` 但忽略其返回值。 通常会从重写的方法返回 `TRUE`。

Windows 通过使用所有 Microsoft 基础类库对话框通用的标准全局对话框过程来调用 `OnInitDialog` 函数。 它不会通过消息映射调用此函数，因此，不需要为此方法使用消息映射项。

> [!NOTE]
> 如果在 Windows Vista 或更高版本的操作系统下编译的程序中使用 `CFileDialog` 对象，则不能重写此方法。 有关 Windows Vista 和更高版本下 `CFileDialog` 更改的详细信息，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]

##  <a name="onok"></a>CDialog：： OnOK

当用户单击 **"确定"** 按钮（ID 为 IDOK 的按钮）时调用。

```
virtual void OnOK();
```

### <a name="remarks"></a>备注

重写此方法以在激活 **"确定"** 按钮时执行操作。 如果此对话框包含自动数据验证和交换，此方法的默认实现将验证对话框数据并更新应用程序中的相应变量。

如果在无模式对话框中实现 **"确定"** 按钮，则必须重写 `OnOK` 方法，并在其中调用[DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) 。 请勿调用基类方法，因为它会调用[EndDialog](#enddialog) ，这会使对话框不可见，但不会将其销毁。

> [!NOTE]
>  在 Windows XP 下编译的程序中使用 `CFileDialog` 对象时，不能重写此方法。 有关 `CFileDialog`的详细信息，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]

##  <a name="onsetfont"></a>CDialog：： OnSetFont

指定在绘制文本时对话框控件将使用的字体。

```
Virtual void OnSetFont(CFont* pFont);
```

### <a name="parameters"></a>parameters

*pFont*<br/>
中指定一个指针，该指针指向将用作此对话框中所有控件的默认字体的字体。

### <a name="remarks"></a>备注

此对话框将使用指定的字体作为其所有控件的默认字体。

对话框编辑器通常将对话框字体设置为对话框模板资源的一部分。

> [!NOTE]
> 如果在 Windows Vista 或更高版本的操作系统下编译的程序中使用 `CFileDialog` 对象，则不能重写此方法。 有关 Windows Vista 和更高版本下 `CFileDialog` 更改的详细信息，请参阅[CFileDialog 类](../../mfc/reference/cfiledialog-class.md)。

##  <a name="prevdlgctrl"></a>CDialog：:P revDlgCtrl

将焦点设置到对话框中的上一个控件。

```
void PrevDlgCtrl() const;
```

### <a name="remarks"></a>备注

如果焦点位于对话框中的第一个控件上，则移动到框中的最后一个控件。

##  <a name="setdefid"></a>CDialog：： SetDefID

更改对话框的默认按钮控件。

```
void SetDefID(UINT nID);
```

### <a name="parameters"></a>parameters

*nID*<br/>
指定将成为默认值的按钮控件的 ID。

##  <a name="sethelpid"></a>CDialog：： SetHelpID

为对话框设置区分上下文的帮助 ID。

```
void SetHelpID(UINT nIDR);
```

### <a name="parameters"></a>parameters

*nIDR*<br/>
指定区分上下文的帮助 ID。

## <a name="see-also"></a>另请参阅

[MFC 示例 DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 DLGTEMPL](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
