---
title: CPropertySheet 类
ms.date: 11/04/2016
f1_keywords:
- CPropertySheet
- AFXDLGS/CPropertySheet
- AFXDLGS/CPropertySheet::CPropertySheet
- AFXDLGS/CPropertySheet::AddPage
- AFXDLGS/CPropertySheet::Construct
- AFXDLGS/CPropertySheet::Create
- AFXDLGS/CPropertySheet::DoModal
- AFXDLGS/CPropertySheet::EnableStackedTabs
- AFXDLGS/CPropertySheet::EndDialog
- AFXDLGS/CPropertySheet::GetActiveIndex
- AFXDLGS/CPropertySheet::GetActivePage
- AFXDLGS/CPropertySheet::GetPage
- AFXDLGS/CPropertySheet::GetPageCount
- AFXDLGS/CPropertySheet::GetPageIndex
- AFXDLGS/CPropertySheet::GetTabControl
- AFXDLGS/CPropertySheet::MapDialogRect
- AFXDLGS/CPropertySheet::OnInitDialog
- AFXDLGS/CPropertySheet::PressButton
- AFXDLGS/CPropertySheet::RemovePage
- AFXDLGS/CPropertySheet::SetActivePage
- AFXDLGS/CPropertySheet::SetFinishText
- AFXDLGS/CPropertySheet::SetTitle
- AFXDLGS/CPropertySheet::SetWizardButtons
- AFXDLGS/CPropertySheet::SetWizardMode
- AFXDLGS/CPropertySheet::m_psh
helpviewer_keywords:
- CPropertySheet [MFC], CPropertySheet
- CPropertySheet [MFC], AddPage
- CPropertySheet [MFC], Construct
- CPropertySheet [MFC], Create
- CPropertySheet [MFC], DoModal
- CPropertySheet [MFC], EnableStackedTabs
- CPropertySheet [MFC], EndDialog
- CPropertySheet [MFC], GetActiveIndex
- CPropertySheet [MFC], GetActivePage
- CPropertySheet [MFC], GetPage
- CPropertySheet [MFC], GetPageCount
- CPropertySheet [MFC], GetPageIndex
- CPropertySheet [MFC], GetTabControl
- CPropertySheet [MFC], MapDialogRect
- CPropertySheet [MFC], OnInitDialog
- CPropertySheet [MFC], PressButton
- CPropertySheet [MFC], RemovePage
- CPropertySheet [MFC], SetActivePage
- CPropertySheet [MFC], SetFinishText
- CPropertySheet [MFC], SetTitle
- CPropertySheet [MFC], SetWizardButtons
- CPropertySheet [MFC], SetWizardMode
- CPropertySheet [MFC], m_psh
ms.assetid: 8461ccff-d14f-46e0-a746-42ad642ef94e
ms.openlocfilehash: 23d17aee2aacbc1484c0f3e181bc824546ab49a2
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426413"
---
# <a name="cpropertysheet-class"></a>CPropertySheet 类

表示属性表，也称为选项卡对话框。

## <a name="syntax"></a>语法

```
class CPropertySheet : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CPropertySheet：： CPropertySheet](#cpropertysheet)|构造 `CPropertySheet` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CPropertySheet：： AddPage](#addpage)|向属性表添加页面。|
|[CPropertySheet：：构造](#construct)|构造 `CPropertySheet` 对象。|
|[CPropertySheet：： Create](#create)|显示无模式属性表。|
|[CPropertySheet：:D oModal](#domodal)|显示模式属性表。|
|[CPropertySheet：： EnableStackedTabs](#enablestackedtabs)|指示属性表是使用堆积选项卡还是滚动选项卡。|
|[CPropertySheet：： EndDialog](#enddialog)|终止属性表。|
|[CPropertySheet：： GetActiveIndex](#getactiveindex)|检索属性表的活动页的索引。|
|[CPropertySheet：： GetActivePage](#getactivepage)|返回活动页对象。|
|[CPropertySheet：： GetPage](#getpage)|检索指向指定页的指针。|
|[CPropertySheet：： GetPageCount](#getpagecount)|检索属性表中的页数。|
|[CPropertySheet：： GetPageIndex](#getpageindex)|检索属性表的指定页的索引。|
|[CPropertySheet：： GetTabControl](#gettabcontrol)|检索指向选项卡控件的指针。|
|[CPropertySheet：： MapDialogRect](#mapdialogrect)|将矩形的对话框单位转换为屏幕单位。|
|[CPropertySheet：： OnInitDialog](#oninitdialog)|重写以增加属性表初始化。|
|[CPropertySheet：:P ressButton](#pressbutton)|模拟在属性表中选择的指定按钮。|
|[CPropertySheet：： RemovePage](#removepage)|从属性表中删除页。|
|[CPropertySheet：： SetActivePage](#setactivepage)|以编程方式设置活动页对象。|
|[CPropertySheet：： SetFinishText](#setfinishtext)|设置 "完成" 按钮的文本。|
|[CPropertySheet：： SetTitle](#settitle)|设置属性表的标题。|
|[CPropertySheet：： SetWizardButtons](#setwizardbuttons)|启用向导按钮。|
|[CPropertySheet：： SetWizardMode](#setwizardmode)|启用向导模式。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CPropertySheet：： m_psh](#m_psh)|Windows [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)结构。 提供对基本属性表参数的访问。|

## <a name="remarks"></a>备注

属性表包含一个 `CPropertySheet` 对象和一个或多个[CPropertyPage](../../mfc/reference/cpropertypage-class.md)对象。 框架将属性表显示为一个窗口，其中包含一组选项卡索引和一个包含当前所选页面的区域。 用户使用相应的选项卡定位到特定页。

`CPropertySheet` 提供对 Windows 98 和 Windows NT 2000 中引入的扩展[PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)结构的支持。 结构包含其他标志和支持使用 "水印" 背景位图的成员。

若要在属性表对象中自动显示这些新图像，请在调用[CPropertySheet：：构造](#construct)或[CPropertySheet：： CPropertySheet](#cpropertysheet)时传递位图和调色板图像的有效值。

即使 `CPropertySheet` 不是派生自[CDialog](../../mfc/reference/cdialog-class.md)，管理 `CPropertySheet` 对象也像管理 `CDialog` 对象。 例如，创建属性表需要两部分构造：调用构造函数，然后为模式属性表调用[DoModal](#domodal)或为无模式属性表[创建](#create)。 `CPropertySheet` 具有两种类型的构造函数： [CPropertySheet：：构造](#construct)和[CPropertySheet：： CPropertySheet](#cpropertysheet)。

构造 `CPropertySheet` 对象时，某些[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)可能会导致出现首次异常。 这会导致系统在创建工作表之前尝试更改属性表的样式。 若要避免此异常，请确保在创建 `CPropertySheet`时设置以下样式：

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

以下样式是可选的，将不会导致首次出现异常：

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

禁止任何其他 `Window Styles`，不应启用它们。

在 `CPropertySheet` 对象和外部对象之间交换数据与与 `CDialog` 对象交换数据类似。 重要的区别在于，属性表的设置通常是 `CPropertyPage` 对象的成员变量，而不是 `CPropertySheet` 对象本身的成员变量。

您可以创建一个名为 "向导" 的 "选项卡" 对话框，其中包含一系列属性页，用于引导用户完成操作的步骤，如设置设备或创建新闻稿。 在向导类型的 "选项卡" 对话框中，属性页没有选项卡，一次只能显示一个属性页。 此外，"向导-类型选项卡" 对话框中有 "**后退**" 按钮、"**下一步**" 或 "**完成**" 按钮、"**取消**" 按钮和 "**帮助**" 按钮，而不是使用 **"确定" 和 "** **立即应用**" 按钮。

若要创建向导类型对话框，请按照创建标准属性表时遵循的相同步骤进行操作，但在调用[DoModal](#domodal)之前调用[SetWizardMode](#setwizardmode) 。 若要启用向导按钮，请调用[SetWizardButtons](#setwizardbuttons)，使用 flags 自定义其功能和外观。 若要启用 "**完成**" 按钮，请在用户在向导的最后一页上执行操作后调用[SetFinishText](#setfinishtext) 。

有关如何使用 `CPropertySheet` 对象的详细信息，请参阅文章[属性表和属性页](../../mfc/property-sheets-and-property-pages-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>要求

**标头：** afxdlgs

##  <a name="addpage"></a>CPropertySheet：： AddPage

添加提供的页面，其中包含属性表中最右边的选项卡。

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>parameters

*pPage*<br/>
指向要添加到属性表的页面。 不能为 NULL。

### <a name="remarks"></a>备注

按要显示的从左到右的顺序向属性表添加页。

`AddPage` 将[CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)对象添加到 `CPropertySheet` 对象的页列表中，但并不实际为该页创建窗口。 框架推迟在用户选择该页之前为该页创建窗口。

使用 `AddPage`添加属性页时，`CPropertySheet` 是 `CPropertyPage`的父级。 若要从属性页访问属性表，请调用[CWnd：： GetParent](../../mfc/reference/cwnd-class.md#getparent)。

无需等待，直到创建属性表窗口才能调用 `AddPage`。 通常，在调用[DoModal](#domodal)或[Create](#create)之前，将调用 `AddPage`。

如果在显示 "属性" 页后调用 `AddPage`，则选项卡行将反映新添加的页面。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]

##  <a name="construct"></a>CPropertySheet：：构造

构造 `CPropertySheet` 对象。

```
void Construct(
    UINT nIDCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

void Construct(
    LPCTSTR pszCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

void Construct(
    UINT nIDCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);

void Construct(
    LPCTSTR pszCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);
```

### <a name="parameters"></a>parameters

*nIDCaption*<br/>
要用于属性表的标题的 ID。

*pParentWnd*<br/>
指向属性表的父窗口的指针。 如果为 NULL，则父窗口将是应用程序的主窗口。

*iSelectPage*<br/>
最初将位于顶层的页的索引。 默认值是添加到工作表中的第一页。

*pszCaption*<br/>
指向字符串的指针，该字符串包含要用于属性表的标题。 不能为 NULL。

*hbmWatermark*<br/>
属性页的水印位图的句柄。

*hpalWatermark*<br/>
水印位图和/或标头位图的调色板的句柄。

*hbmHeader*<br/>
属性页的标头位图的句柄。

### <a name="remarks"></a>备注

如果尚未调用某个类构造函数，则调用此成员函数。 例如，在声明或分配 `CPropertySheet` 对象的数组时，请调用 `Construct`。 对于数组，必须为数组中的每个成员调用 `Construct`。

若要显示属性表，请调用[DoModal](#domodal)或[Create](#create)。 第一个参数中包含的字符串将放在属性表的标题栏中。

如果使用上面列出的 `Construct`的第三个或第四个原型，并为*hbmWatermark*、 *hpalWatermark*和/或*hbmHeader*参数传递有效值，则可以自动显示水印和/或标题图像。

### <a name="example"></a>示例

下面的示例演示在什么情况下 `Construct`调用。

[!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]

##  <a name="cpropertysheet"></a>CPropertySheet：： CPropertySheet

构造 `CPropertySheet` 对象。

```
CPropertySheet();

explicit CPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

explicit CPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

CPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);

CPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);
```

### <a name="parameters"></a>parameters

*nIDCaption*<br/>
要用于属性表的标题的 ID。

*pParentWnd*<br/>
指向属性表的父窗口。 如果为 NULL，则父窗口将是应用程序的主窗口。

*iSelectPage*<br/>
最初将位于顶层的页的索引。 默认值是添加到工作表中的第一页。

*pszCaption*<br/>
指向包含要用于属性表的标题的字符串。 不能为 NULL。

*hbmWatermark*<br/>
属性表的背景位图的句柄。

*hpalWatermark*<br/>
水印位图和/或标头位图的调色板的句柄。

*hbmHeader*<br/>
属性页的标头位图的句柄。

### <a name="remarks"></a>备注

若要显示属性表，请调用[DoModal](#domodal)或[Create](#create)。 第一个参数中包含的字符串将放在属性表的标题栏中。

如果有多个参数（例如，使用数组），请使用[构造](#construct)而不是 `CPropertySheet`。

如果使用上面 `CPropertySheet`的第三个或第四个原型，并为*hbmWatermark*、 *hpalWatermark*和/或*hbmHeader*参数传递有效值，则可以自动显示水印和/或标题图像。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]

##  <a name="create"></a>CPropertySheet：： Create

显示无模式属性表。

```
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);
```

### <a name="parameters"></a>parameters

*pParentWnd*<br/>
指向父窗口。 如果为 NULL，则父项是桌面。

*dwStyle*<br/>
属性表的窗口样式。 有关可用样式的完整列表，请参阅[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*dwExStyle*<br/>
属性表的扩展窗口样式。 有关可用样式的完整列表，请参阅[扩展的窗口样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

### <a name="return-value"></a>返回值

如果成功创建属性表，则为非零值;否则为0。

### <a name="remarks"></a>备注

对 `Create` 的调用可以在构造函数中，也可以在调用构造函数后调用。

默认样式（通过将-1 作为*dwStyle*传递）&#124;实际上 WS_SYSMENU WS_POPUP&#124;WS_CAPTION&#124;DS_MODALFRAME&#124;DS_CONTEXTHELP&#124;WS_VISIBLE。 默认的扩展窗口样式（由0作为*dwExStyle*表示）实际上 WS_EX_DLGMODALFRAME。

`Create` 成员函数将在创建属性表后立即返回。 若要销毁属性表，请调用[CWnd：:D estroywindow](../../mfc/reference/cwnd-class.md#destroywindow)。

通过调用 `Create` 显示的无模式属性表没有 "确定"、"取消"、"立即应用" 和 "帮助" 按钮作为模式属性表。 用户必须创建所需的按钮。

若要显示模式属性表，请改为调用[DoModal](#domodal) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]

[!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]

##  <a name="domodal"></a>CPropertySheet：:D oModal

显示模式属性表。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

如果函数成功，则为 IDOK 或 IDCANCEL;否则为0或-1。 如果已将属性表建立为向导（请参阅[SetWizardMode](#setwizardmode)），`DoModal` 将返回 ID_WIZFINISH 或 IDCANCEL。

### <a name="remarks"></a>备注

返回值对应于关闭属性表的控件的 ID。 此函数返回后，对应于属性表和所有页面的窗口将被销毁。 对象本身将仍然存在。 通常，在 `DoModal` 返回 IDOK 后，你将从[CPropertyPage](../../mfc/reference/cpropertypage-class.md)对象中检索数据。

若要显示无模式属性表，请改为调用[Create](#create) 。

从其相应的对话框资源创建属性页时，可能会导致首次异常。 在创建页面之前，属性页会将对话框资源的样式更改为所需的样式。 因为资源通常是只读的，所以这会导致异常。 系统处理异常，并创建已修改资源的副本。 因此，可能会忽略第一次异常。

> [!NOTE]
>  如果正在使用异步异常处理模型进行编译，则必须由操作系统处理此异常。 有关异常处理模型的详细信息，请参阅[/EH （异常处理模型）](../../build/reference/eh-exception-handling-model.md)。 在这种情况下，不要使用C++ catch 块包装对 `CPropertySheet::DoModal` 的调用，其中 catch 处理所有异常，例如 `catch (...)`。 此块将处理适用于操作系统的异常，并导致不可预知的行为。 但是，您可以安全地C++将异常处理用于特定异常类型或结构化异常处理，在这种情况下，将访问冲突异常传递到操作系统。

若要避免产生这种第一次异常，可以手动保证属性表具有正确的[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 需要为属性表设置以下样式：

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

您可以使用以下可选样式，而不会导致首次出现异常：

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

禁用所有其他 Windows 样式，因为它们与属性表不兼容。 此建议不适用于扩展样式。 适当地设置这些标准样式将保证无需修改属性表，并且将避免生成首次异常。

### <a name="example"></a>示例

请参阅[CPropertySheet：： AddPage](#addpage)的示例。

##  <a name="enablestackedtabs"></a>CPropertySheet：： EnableStackedTabs

指示是否对属性表中的选项卡行进行堆栈。

```
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>parameters

*bStacked*<br/>
指示是否在属性表中启用了堆积选项卡。 通过将*bStacked*设置为 FALSE，禁用堆积标记行。

### <a name="remarks"></a>备注

默认情况下，如果属性表具有的选项卡数多于在属性表宽度的单个行中容纳的选项卡，则选项卡将在多个行中堆叠。 若要使用滚动选项卡而不是堆叠选项卡，请在调用[DoModal](#domodal)或[Create](#create)之前调用*bStacked*设置为 FALSE 的 `EnableStackedTabs`。

创建模式或无模式属性表时，必须调用 `EnableStackedTabs`。 若要将此样式合并到 `CPropertySheet`派生类中，请编写 WM_CREATE 的消息处理程序。 在[CWnd：： OnCreate](../../mfc/reference/cwnd-class.md#oncreate)的重写版本中，在调用基类实现之前调用 `EnableStackedTabs( FALSE )`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]

##  <a name="enddialog"></a>CPropertySheet：： EndDialog

终止属性表。

```
void EndDialog(int nEndID);
```

### <a name="parameters"></a>parameters

*nEndID*<br/>
要用作属性表的返回值的标识符。

### <a name="remarks"></a>备注

当按 "确定"、"取消" 或 "关闭" 按钮时，框架会调用此成员函数。 如果发生了应关闭属性表的事件，请调用此成员函数。

此成员函数仅用于模式对话框。

### <a name="example"></a>示例

请参阅[CPropertySheet：:P ressbutton](#pressbutton)的示例。

##  <a name="getactiveindex"></a>CPropertySheet：： GetActiveIndex

获取属性表窗口的活动页的索引号，然后使用返回的索引号作为 `GetPage`的参数。

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>返回值

活动页的索引号。

### <a name="example"></a>示例

请参阅[CPropertySheet：： GetActivePage](#getactivepage)的示例。

##  <a name="getactivepage"></a>CPropertySheet：： GetActivePage

检索属性表窗口的活动页。

```
CPropertyPage* GetActivePage() const;
```

### <a name="return-value"></a>返回值

指向活动页的指针。

### <a name="remarks"></a>备注

使用此成员函数在活动页上执行某种操作。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]

##  <a name="getpage"></a>CPropertySheet：： GetPage

返回指向此属性表中指定页面的指针。

```
CPropertyPage* GetPage(int nPage) const;
```

### <a name="parameters"></a>parameters

*nPage*<br/>
所需页面的索引（从0开始）。 值必须介于0和1之间，小于属性表中的页数（含）。

### <a name="return-value"></a>返回值

指向与*nPage*参数相对应的页面的指针。

### <a name="example"></a>示例

请参阅[CPropertyPage：： OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish)的示例。

##  <a name="getpagecount"></a>CPropertySheet：： GetPageCount

确定属性表中当前的页数。

```
int GetPageCount() const;
```

### <a name="return-value"></a>返回值

属性表中的页数。

### <a name="example"></a>示例

请参阅[CPropertyPage：： OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish)的示例。

##  <a name="getpageindex"></a>CPropertySheet：： GetPageIndex

检索属性表中指定页的索引号。

```
int GetPageIndex(CPropertyPage* pPage);
```

### <a name="parameters"></a>parameters

*pPage*<br/>
指向包含要查找的索引的页面。 不能为 NULL。

### <a name="return-value"></a>返回值

页的索引号。

### <a name="remarks"></a>备注

例如，你可以使用 `GetPageIndex` 获取页面索引，以便使用[SetActivePage](#setactivepage)或[GetPage](#getpage)。

### <a name="example"></a>示例

请参阅[CPropertySheet：： GetActivePage](#getactivepage)的示例。

##  <a name="gettabcontrol"></a>CPropertySheet：： GetTabControl

检索指向选项卡控件的指针，以执行特定于选项卡控件的操作（即，使用[CTabCtrl](../../mfc/reference/ctabctrl-class.md)中的任何 api）。

```
CTabCtrl* GetTabControl() const;
```

### <a name="return-value"></a>返回值

指向选项卡控件的指针。

### <a name="remarks"></a>备注

例如，如果想要在初始化期间将位图添加到每个选项卡，请调用此成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]

##  <a name="m_psh"></a>CPropertySheet：： m_psh

一个结构，其成员存储[PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)的特性。

### <a name="remarks"></a>备注

使用此结构可以在构造后，初始化属性表的外观，但在使用[DoModal](#domodal)成员函数显示它之前。 例如，将 `m_psh` 的*dwSize*成员设置为要使用的属性表的大小。

有关此结构的详细信息（包括其成员的列表），请参阅 Windows SDK 中的 PROPSHEETHEADER。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

##  <a name="mapdialogrect"></a>CPropertySheet：： MapDialogRect

将矩形的对话框单位转换为屏幕单位。

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>parameters

*lpRect*<br/>
指向一个[RECT](/previous-versions/dd162897\(v=vs.85\))结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，其中包含要转换的对话框坐标。

### <a name="remarks"></a>备注

对话框单位根据当前的对话框基本单位进行说明，该基本单位是从用于对话框文本的字体中的字符的平均宽度和高度派生的。 一个水平单位是对话框基数宽度单位的第四个，而一个垂直单位是对话框基准高度单位的八分之一。

[GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) Windows 函数返回系统字体的大小信息，但如果在资源定义文件中使用 DS_SETFONT 样式，则可以为每个属性表指定不同的字体。 Windows SDK 中描述的[MapDialogRect](/windows/win32/api/winuser/nf-winuser-mapdialogrect) Windows 函数为此对话框使用适当的字体。

`MapDialogRect` 成员函数将*lpRect*中的对话框单位替换为屏幕单位（像素），以便可以使用该矩形来创建对话框或将控件放置在一个框中。

##  <a name="oninitdialog"></a>CPropertySheet：： OnInitDialog

重写以增加属性表初始化。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>返回值

指定应用程序是否已将输入焦点设置为属性表中的某个控件。 如果 `OnInitDialog` 返回非零值，则 Windows 将输入焦点设置为属性表中的第一个控件。 仅当应用程序已将输入焦点显式设置为属性表中的某个控件时，应用程序才能返回0。

### <a name="remarks"></a>备注

调用此成员函数是为了响应 WM_INITDIALOG 消息。 此消息将在[Create](#create)或[DoModal](#domodal)调用过程中发送到属性表，这会在显示属性表之前立即发生。

如果在初始化属性表时需要执行特殊处理，请重写此成员函数。 在重写的版本中，首先调用基类 `OnInitDialog` 但忽略其返回值。 通常会从重写的成员函数返回 TRUE。

此成员函数不需要消息映射项。

##  <a name="pressbutton"></a>CPropertySheet：:P ressButton

模拟在属性表中选择的指定按钮。

```
void PressButton(int nButton);
```

### <a name="parameters"></a>parameters

*nButton*<br/>
nButton：标识要按下的按钮。 此参数可以是下列值之一：

- PSBTN_BACK 选择 "后退" 按钮。

- PSBTN_NEXT 选择 "下一步" 按钮。

- PSBTN_FINISH 选择 "完成" 按钮。

- PSBTN_OK 选择 "确定" 按钮。

- PSBTN_APPLYNOW 选择 "立即应用" 按钮。

- PSBTN_CANCEL 选择 "取消" 按钮。

- PSBTN_HELP 选择 "帮助" 按钮。

### <a name="remarks"></a>备注

有关 Windows SDK Pressbutton 消息的详细信息，请参阅[PSM_PRESSBUTTON](/windows/win32/Controls/psm-pressbutton) 。

对 `PressButton` 的调用不会将[PSN_APPLY](/windows/win32/Controls/psn-apply)通知从属性页发送到框架。 若要发送此通知，请调用[CPropertyPage：： OnOK](../../mfc/reference/cpropertypage-class.md#onok)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]

##  <a name="removepage"></a>CPropertySheet：： RemovePage

从属性表中删除页面并销毁关联的窗口。

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>parameters

*pPage*<br/>
指向要从属性表中删除的页面。 不能为 NULL。

*nPage*<br/>
要删除的页的索引。 值必须介于0和1之间，小于属性表中的页数（含）。

### <a name="remarks"></a>备注

在关闭 `CPropertySheet` 窗口的所有者之前，不会销毁[CPropertyPage](../../mfc/reference/cpropertypage-class.md)对象本身。

##  <a name="setactivepage"></a>CPropertySheet：： SetActivePage

更改活动页。

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>parameters

*nPage*<br/>
要设置的页的索引。 该值必须介于0和小于属性表中的页数（含）之间。

*pPage*<br/>
指向要在属性表中设置的页面。 不可为 NULL。

### <a name="return-value"></a>返回值

如果成功激活属性表，则为非零值;否则为0。

### <a name="remarks"></a>备注

例如，如果用户在一页上执行的操作应导致另一页成为活动页，请使用 `SetActivePage`。

### <a name="example"></a>示例

请参阅[CPropertySheet：： GetActivePage](#getactivepage)的示例。

##  <a name="setfinishtext"></a>CPropertySheet：： SetFinishText

设置 "完成" 命令按钮中的文本。

```
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>parameters

*lpszText*<br/>
指向 "完成" 命令按钮上显示的文本。

### <a name="remarks"></a>备注

调用 `SetFinishText` 以显示 "完成" 命令按钮上的文本，并隐藏用户在向导的最后一页上完成操作后的 "下一步" 和 "后退" 按钮。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="settitle"></a>CPropertySheet：： SetTitle

指定属性表的标题（框架窗口的标题栏中显示的文本）。

```
void SetTitle(
    LPCTSTR lpszText,
    UINT nStyle = 0);
```

### <a name="parameters"></a>parameters

*nStyle*<br/>
指定属性表标题的样式。 样式必须指定为0或 PSH_PROPTITLE。 如果样式设置为 "PSH_PROPTITLE"，则在指定为标题的文本后将显示 "属性" 一词。 例如，调用 `SetTitle`（"Simple"，PSH_PROPTITLE）将导致 "简单属性" 的属性表标题。

*lpszText*<br/>
指向要用作属性表标题栏中的标题的文本。

### <a name="remarks"></a>备注

默认情况下，属性表使用属性表构造函数中的 caption 参数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

##  <a name="setwizardbuttons"></a>CPropertySheet：： SetWizardButtons

启用或禁用向导属性表中的 "后退"、"下一步" 或 "完成" 按钮。

```
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>parameters

dwFlags<br/>
一组用于自定义向导按钮的功能和外观的标志。 此参数可以是下列值的组合：

- PSWIZB_BACK 后退 "按钮

- PSWIZB_NEXT "下一步" 按钮

- PSWIZB_FINISH 完成 "按钮

- PSWIZB_DISABLEDFINISH 禁用 "完成" 按钮

### <a name="remarks"></a>备注

仅在对话框打开后调用 `SetWizardButtons`;在调用[DoModal](#domodal)之前，无法调用 `SetWizardButtons`。 通常，应从[CPropertyPage：： OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive)调用 `SetWizardButtons`。

如果要更改 "完成" 按钮上的文本，或在用户完成向导后隐藏 "下一步" 和 "后退" 按钮，请调用[SetFinishText](#setfinishtext)。 请注意，"完成" 和 "下一步" 按钮是共享的。 你可以一次显示 "完成" 或 "下一步" 按钮，但不能同时显示两者。

### <a name="example"></a>示例

`CPropertySheet` 有三个向导属性页： `CStylePage`、`CColorPage`和 `CShapePage`。  下面的代码段演示如何启用和禁用向导属性页上的 "**后退**" 和 "**下一步**" 按钮。

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="setwizardmode"></a>CPropertySheet：： SetWizardMode

将属性页建立为向导。

```
void SetWizardMode();
```

### <a name="remarks"></a>备注

向导属性页的关键特性是用户使用 "下一步" 或 "完成"、"后退" 和 "取消" 按钮而不是选项卡导航。

调用[DoModal](#domodal)之前调用 `SetWizardMode`。 调用 `SetWizardMode`后，`DoModal` 将返回 ID_WIZFINISH （如果用户以 "完成" 按钮关闭）或 IDCANCEL。

`SetWizardMode` 设置 PSH_WIZARD 标志。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 示例 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
