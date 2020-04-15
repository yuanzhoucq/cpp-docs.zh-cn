---
title: C属性表类
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
ms.openlocfilehash: 167c99f734e4538ff2704e032a6ca98fb1d82004
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363951"
---
# <a name="cpropertysheet-class"></a>C属性表类

表示属性表，也称为选项卡对话框。

## <a name="syntax"></a>语法

```
class CPropertySheet : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C属性表：C属性表](#cpropertysheet)|构造 `CPropertySheet` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C属性表：：添加页](#addpage)|向属性表添加页面。|
|[C属性表：构造](#construct)|构造 `CPropertySheet` 对象。|
|[C属性表：创建](#create)|显示无模式属性表。|
|[C属性表：:Do 模态](#domodal)|显示模态属性表。|
|[C属性表：：启用堆叠选项卡](#enablestackedtabs)|指示属性表是使用堆叠选项卡还是滚动选项卡。|
|[C属性表：结束对话](#enddialog)|终止属性表。|
|[C属性表：获取活动索引](#getactiveindex)|检索属性表的活动页的索引。|
|[C属性表：获取活动页面](#getactivepage)|返回活动页对象。|
|[C属性表：获取页面](#getpage)|检索指向指定页面的指针。|
|[C属性表：获取页面计数](#getpagecount)|检索属性表中的页数。|
|[C属性表：获取页面索引](#getpageindex)|检索属性表指定页的索引。|
|[C属性表：获取Tab控制](#gettabcontrol)|检索指向选项卡控件的指针。|
|[C属性表：mapDialogrect](#mapdialogrect)|将矩形的对话框单位转换为屏幕单位。|
|[C属性表：onInitDialog](#oninitdialog)|重写以增强属性表初始化。|
|[C属性表：:PresButton](#pressbutton)|模拟属性表中指定按钮的选择。|
|[C属性表：删除页](#removepage)|从属性工作表中删除页面。|
|[C属性表：：设置活动页](#setactivepage)|以编程方式设置活动页面对象。|
|[C属性表：：设置完成文本](#setfinishtext)|设置"完成"按钮的文本。|
|[C属性表：：设置标题](#settitle)|设置属性表的标题。|
|[C属性表：：设置向导按钮](#setwizardbuttons)|启用向导按钮。|
|[C属性表：：设置向导模式](#setwizardmode)|启用向导模式。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[C属性表：m_psh](#m_psh)|Windows [PROPSHEETHEADER 结构](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)。 提供对基本属性表参数的访问。|

## <a name="remarks"></a>备注

属性表由对象`CPropertySheet`和一个或多个[CPropertyPage](../../mfc/reference/cpropertypage-class.md)对象组成。 框架将属性表显示为一个窗口，其中包含一组选项卡索引和包含当前所选页面的区域。 用户使用相应的选项卡导航到特定页面。

`CPropertySheet`支持 Windows 98 和 Windows NT 2000 中引入的扩展[PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)结构。 该结构包含支持使用"水印"背景位图的其他标志和成员。

要在属性表对象中自动显示这些新图像，请将调用[CPropertySheet：：构造](#construct)或[CPropertySheet：CPropertySheet](#cpropertysheet)中的位图和调色板图像的有效值传递给 。

即使`CPropertySheet`不是从[CDialog](../../mfc/reference/cdialog-class.md)派生的`CPropertySheet`，管理对象就像管理对象一`CDialog`样。 例如，创建属性表需要两个部分构造：调用构造函数，然后调用模态属性表[DoModal](#domodal)或为无模式属性表[创建](#create)。 `CPropertySheet`有两种类型的构造函数[：C属性表：构造](#construct)和 C[属性表：：C属性表](#cpropertysheet)。

构造`CPropertySheet`对象时，某些[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)可能会导致发生第一次异常。 这是系统尝试在创建工作表之前更改属性表样式的结果。 为了避免此异常，请确保在创建 时`CPropertySheet`设置以下样式：

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

以下样式是可选的，不会导致第一次机会异常：

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

任何其他`Window Styles`是被禁止的，你不应该启用他们。

在`CPropertySheet`对象和外部对象之间交换数据类似于与`CDialog`对象交换数据。 重要的区别是属性表的设置通常是对象的成员变量，`CPropertyPage`而不是对象本身的成员`CPropertySheet`变量。

您可以创建称为向导的选项卡对话框类型，该对话框由包含一系列属性页的属性表组成，该属性页指导用户完成操作的步骤，例如设置设备或创建新闻稿。 在向导类型选项卡对话框中，属性页没有选项卡，并且一次只能看到一个属性页。 此外，向导类型选项卡对话框没有 **"确定**"和 **"立即应用"** 按钮，而是具有 **"后退"** 按钮 **、"下一步**"或 **"完成"** 按钮 **、"取消"** 按钮和 **"帮助**"按钮。

要创建向导类型对话框，请按照创建标准属性表的步骤执行相同的步骤，但在调用[DoModal](#domodal)之前调用[SetWizardMode。](#setwizardmode) 要启用向导按钮，请使用标志调用[SetWizardButtons](#setwizardbuttons)来自定义其功能和外观。 要启用 **"完成"** 按钮，请用户在向导的最后一页上执行操作后调用[SetFinishText。](#setfinishtext)

有关如何使用`CPropertySheet`对象的详细信息，请参阅文章["属性表"和"属性页](../../mfc/property-sheets-and-property-pages-in-mfc.md)"。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>要求

**标题：** afxdlgs.h

## <a name="cpropertysheetaddpage"></a><a name="addpage"></a>C属性表：：添加页

在属性表中添加提供的最右侧选项卡的页面。

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>参数

*pPage*<br/>
指向要添加到属性表的页面。 不能为 NULL。

### <a name="remarks"></a>备注

按从左到右的顺序将页面添加到属性工作表，您希望它们显示。

`AddPage`将[CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)对象添加到`CPropertySheet`对象的页面列表中，但实际上不会为页面创建窗口。 框架将推迟创建页面的窗口，直到用户选择该页面。

使用`AddPage`添加 属性页时，`CPropertySheet`是 的`CPropertyPage`父页。 要从属性页访问属性表，请致电[CWnd：：getParent](../../mfc/reference/cwnd-class.md#getparent)。

不必等到创建属性表窗口才能调用`AddPage`。 通常，您将在调用`AddPage` [DoModal](#domodal)或[创建](#create)之前调用 。

如果在显示属性`AddPage`页后调用，选项卡行将反映新添加的页面。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]

## <a name="cpropertysheetconstruct"></a><a name="construct"></a>C属性表：构造

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

### <a name="parameters"></a>参数

*nIDCaption*<br/>
用于属性表的标题的 ID。

*pparentwnd*<br/>
指向属性表的父窗口。 如果为 NULL，则父窗口将是应用程序的主窗口。

*iSelectPage*<br/>
最初位于顶部的页面索引。 默认值是添加到工作表的第一页。

*pszCaption*<br/>
指向包含要用于属性表的标题的字符串的指针。 不能为 NULL。

*hbm沃特马克*<br/>
处理属性页的水印位图。

*赫帕尔沃特马克*<br/>
处理水印位图和/或标题位图的调色板。

*hbmHeader*<br/>
处理属性页的头位图。

### <a name="remarks"></a>备注

如果尚未调用一个类构造函数，请调用此成员函数。 例如，在声明`Construct`或分配`CPropertySheet`对象数组时调用。 对于数组，必须调用`Construct`数组中的每个成员。

要显示属性工作表，请调用["使用模式"](#domodal)或["创建](#create)"。 第一个参数中包含的字符串将放置在属性表的标题栏中。

如果使用上面列出的 第三个或第四`Construct`个原型，并且传递*hbmWatermark、hpalWatermark*和/或*hbmHeader*参数的有效值*hpalWatermark*，则可以自动显示水印和/或标题图像。

### <a name="example"></a>示例

下面的示例演示了在什么情况下调用`Construct`。

[!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]

## <a name="cpropertysheetcpropertysheet"></a><a name="cpropertysheet"></a>C属性表：C属性表

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

### <a name="parameters"></a>参数

*nIDCaption*<br/>
用于属性表的标题的 ID。

*pparentwnd*<br/>
指向属性表的父窗口。 如果为 NULL，则父窗口将是应用程序的主窗口。

*iSelectPage*<br/>
最初位于顶部的页面索引。 默认值是添加到工作表的第一页。

*pszCaption*<br/>
指向包含要用于属性表的标题的字符串。 不能为 NULL。

*hbm沃特马克*<br/>
属性表的背景位图的句柄。

*赫帕尔沃特马克*<br/>
水印位图和/或头位图调色板的句柄。

*hbmHeader*<br/>
属性页头位图的句柄。

### <a name="remarks"></a>备注

要显示属性工作表，请调用["使用模式"](#domodal)或["创建](#create)"。 第一个参数中包含的字符串将放置在属性表的标题栏中。

如果有多个参数（例如，如果使用数组），请使用[构造](#construct)而不是`CPropertySheet`。

如果您使用上面的第三个或第四`CPropertySheet`个原型，并且传递*hbmWatermark、hpalWatermark*和/或*hbmHeader*参数的有效值*hpalWatermark*，则可以自动显示水印和/或标题图像。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]

## <a name="cpropertysheetcreate"></a><a name="create"></a>C属性表：创建

显示无模式属性表。

```
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
指向父窗口。 如果为 NULL，则父级是桌面。

*dwStyle*<br/>
属性表的窗口样式。 有关可用样式的完整列表，请参阅[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*dwExStyle*<br/>
属性表的扩展窗口样式。 有关可用样式的完整列表，请参阅[扩展窗口样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

### <a name="return-value"></a>返回值

成功创建属性表时为非零;否则 0。

### <a name="remarks"></a>备注

调用`Create`可以位于构造函数内部，也可以在调用构造函数后调用它。

默认样式，通过传递 -1 表示为*dwStyle，* 实际上是WS_SYSMENU&#124;&#124;WS_POPUP&#124;&#124;WS_CAPTION&#124;DS_MODALFRAME&#124;DS_CONTEXTHELP&#124;WS_VISIBLE。 默认扩展窗口样式（通过将 0 表示为*dwExStyle）* 表示，实际上是WS_EX_DLGMODALFRAME。

成员`Create`函数在创建属性表后立即返回。 要销毁属性表，请致电[CWnd：:DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow)。

与模式属性表一样，显示的`Create`未模属性表具有"确定"、"取消"、"立即应用"和"帮助"按钮。 所需的按钮必须由用户创建。

要显示模态属性表，请改为调用[DoModal。](#domodal)

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]

[!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]

## <a name="cpropertysheetdomodal"></a><a name="domodal"></a>C属性表：:Do 模态

显示模态属性表。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>返回值

IDOK 或 IDCANCEL（如果函数成功）;否则为 0 或 -1。 如果属性表已设置为向导（请参阅[SetWizardMode），](#setwizardmode)`DoModal`则返回ID_WIZFINISH或 IDCANCEL。

### <a name="remarks"></a>备注

返回值对应于关闭属性表的控件的 ID。 返回此函数后，与属性表和所有页面对应的窗口将被销毁。 对象本身将仍然存在。 通常，您将在返回 IDOK 后`DoModal`从[CPropertyPage](../../mfc/reference/cpropertypage-class.md)对象检索数据。

要显示无模式属性表，请改为"[创建](#create)"。

当从相应的对话框资源创建属性页时，可能会导致第一次异常。 这源于属性页在创建页面之前将对话框资源的样式更改为所需的样式。 由于资源通常是只读的，因此会导致异常。 系统处理异常，并创建修改后的资源的副本。 因此，可以忽略第一个异常。

> [!NOTE]
> 如果要使用异步异常处理模型进行编译，操作系统必须处理此异常。 有关异常处理模型的详细信息，请参阅[/EH（异常处理模型）。](../../build/reference/eh-exception-handling-model.md) 在这种情况下，不要`CPropertySheet::DoModal`用C++尝试 catch 块对 调用进行包装，`catch (...)`其中 catch 处理所有异常，例如 。 此块将处理用于操作系统的异常，并导致不可预知的行为。 但是，在访问冲突异常传递到操作系统时，可以使用具有特定异常类型或结构化异常处理C++异常处理。

为了避免生成此第一个异常，您可以手动保证属性表具有正确的[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 您需要为属性表设置以下样式：

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

您可以使用以下可选样式，而不会造成第一次异常：

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

禁用所有其他 Windows 样式，因为它们与属性表不兼容。 此建议不适用于扩展样式。 适当地设置这些标准样式将保证属性表不必修改，并且将避免生成第一个异常。

### <a name="example"></a>示例

请参阅[CPropertySheet 的示例：：添加页](#addpage)。

## <a name="cpropertysheetenablestackedtabs"></a><a name="enablestackedtabs"></a>C属性表：：启用堆叠选项卡

指示是否将选项卡行堆叠在属性工作表中。

```
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>参数

*b堆叠*<br/>
指示在属性表中是否启用了堆叠选项卡。 通过将*bStacked*设置为 FALSE 来禁用堆叠的标记行。

### <a name="remarks"></a>备注

默认情况下，如果属性工作表的选项卡数多于属性工作表宽度中的一行，则选项卡将堆叠在多行中。 要使用滚动选项卡而不是堆叠选项卡，请`EnableStackedTabs`调用*bStacked*设置为 FALSE，然后再调用[DoModal](#domodal)或[创建](#create)。

创建模态`EnableStackedTabs`或无模式属性表时必须调用。 要将此样式合并到`CPropertySheet`派生类中，请为WM_CREATE编写消息处理程序。 在重写版本的[CWnd：：onCreate](../../mfc/reference/cwnd-class.md#oncreate)中，调用`EnableStackedTabs( FALSE )`基类实现之前调用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]

## <a name="cpropertysheetenddialog"></a><a name="enddialog"></a>C属性表：结束对话

终止属性表。

```
void EndDialog(int nEndID);
```

### <a name="parameters"></a>参数

*nEndID*<br/>
用作属性表的返回值的标识符。

### <a name="remarks"></a>备注

按下"确定"、"取消"或"关闭"按钮时，框架将调用此成员函数。 如果发生应关闭属性表的事件，请调用此成员函数。

此成员函数仅与模式对话框一起使用。

### <a name="example"></a>示例

请参阅[CPropertySheet：:PresButton](#pressbutton)"的示例。

## <a name="cpropertysheetgetactiveindex"></a><a name="getactiveindex"></a>C属性表：获取活动索引

获取属性工作表窗口的活动页的索引号，然后使用返回的索引号作为`GetPage`的参数。

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>返回值

活动页的索引号。

### <a name="example"></a>示例

请参阅[CPropertySheet 的示例：获取活动页](#getactivepage)。

## <a name="cpropertysheetgetactivepage"></a><a name="getactivepage"></a>C属性表：获取活动页面

检索属性工作表窗口的活动页。

```
CPropertyPage* GetActivePage() const;
```

### <a name="return-value"></a>返回值

指向活动页的指针。

### <a name="remarks"></a>备注

使用此成员函数在活动页上执行某些操作。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]

## <a name="cpropertysheetgetpage"></a><a name="getpage"></a>C属性表：获取页面

返回指向此属性表中指定页面的指针。

```
CPropertyPage* GetPage(int nPage) const;
```

### <a name="parameters"></a>参数

*nPage*<br/>
所需页面的索引，从 0 开始。 必须小于属性表中的页数 0 和 1（包括）。

### <a name="return-value"></a>返回值

指向与*nPage*参数对应的页面的指针。

### <a name="example"></a>示例

请参阅[CPropertyPage 的示例：：在向导完成](../../mfc/reference/cpropertypage-class.md#onwizardfinish)。

## <a name="cpropertysheetgetpagecount"></a><a name="getpagecount"></a>C属性表：获取页面计数

确定属性表中当前页数。

```
int GetPageCount() const;
```

### <a name="return-value"></a>返回值

属性表中的页数。

### <a name="example"></a>示例

请参阅[CPropertyPage 的示例：：在向导完成](../../mfc/reference/cpropertypage-class.md#onwizardfinish)。

## <a name="cpropertysheetgetpageindex"></a><a name="getpageindex"></a>C属性表：获取页面索引

检索属性表中指定页面的索引号。

```
int GetPageIndex(CPropertyPage* pPage);
```

### <a name="parameters"></a>参数

*pPage*<br/>
指向要找到的索引的页面。 不能为 NULL。

### <a name="return-value"></a>返回值

页面的索引编号。

### <a name="remarks"></a>备注

例如，您可以使用`GetPageIndex`获取页面索引，以便使用[SetActivePage](#setactivepage)或[GetPage](#getpage)。

### <a name="example"></a>示例

请参阅[CPropertySheet 的示例：获取活动页](#getactivepage)。

## <a name="cpropertysheetgettabcontrol"></a><a name="gettabcontrol"></a>C属性表：获取Tab控制

检索指向选项卡控件的指针，以执行特定于选项卡控件（即使用[CTabCtrl](../../mfc/reference/ctabctrl-class.md)中的任何 API）

```
CTabCtrl* GetTabControl() const;
```

### <a name="return-value"></a>返回值

指向选项卡控件的指针。

### <a name="remarks"></a>备注

例如，如果要在初始化期间向每个选项卡添加位图，请调用此成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]

## <a name="cpropertysheetm_psh"></a><a name="m_psh"></a>C属性表：m_psh

其成员存储[PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)特征的结构。

### <a name="remarks"></a>备注

使用此结构在构造属性表后，但在使用[DoModal](#domodal)成员函数显示属性表之前初始化它的外观。 例如，将 的`m_psh` *dwSize*成员设置为您希望属性表具有的大小。

有关此结构的详细信息（包括其成员的列表），请参阅 Windows SDK 中的 PROPSHEETHEADER。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

## <a name="cpropertysheetmapdialogrect"></a><a name="mapdialogrect"></a>C属性表：mapDialogrect

将矩形的对话框单位转换为屏幕单位。

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*lpRect*<br/>
指向包含要转换的对话框坐标的[RECT](/previous-versions/dd162897\(v=vs.85\))结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象。

### <a name="remarks"></a>备注

对话框单位根据当前对话框基本单位表示，该单位派生自对话框文本字体中字符的平均宽度和高度。 一个水平单位是对话框基宽单位的四分之一，一个垂直单位是对话框基本高度单位的八分之一。

[GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) Windows 函数返回系统字体的大小信息，但如果在资源定义文件中使用DS_SETFONT样式，则可以为每个属性表指定不同的字体。 Windows SDK 中描述的[MapDialogRect](/windows/win32/api/winuser/nf-winuser-mapdialogrect) Windows 功能为此对话框使用相应的字体。

成员`MapDialogRect`函数将*lpRect*中的对话框单元替换为屏幕单位（像素），以便矩形可用于创建对话框或在框中放置控件。

## <a name="cpropertysheetoninitdialog"></a><a name="oninitdialog"></a>C属性表：onInitDialog

用于增强属性表初始化的重写。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>返回值

指定应用程序是否已将输入焦点设置为属性表中的一个控件。 如果`OnInitDialog`返回非零，Windows 会将输入焦点设置到属性表中的第一个控件。 仅当应用程序显式将输入焦点设置为属性表中的一个控件时，应用程序才能返回 0。

### <a name="remarks"></a>备注

调用此成员函数以响应WM_INITDIALOG消息。 此消息在[创建](#create)或[DoModal](#domodal)调用期间发送到属性表，这些调用在显示属性表之前发生。

如果在初始化属性表时需要执行特殊处理，则重写此成员函数。 在重写版本中，首先调用基类`OnInitDialog`，但忽略其返回值。 您通常会从重写的成员函数返回 TRUE。

不需要此成员函数的消息映射条目。

## <a name="cpropertysheetpressbutton"></a><a name="pressbutton"></a>C属性表：:PresButton

模拟属性表中指定按钮的选择。

```
void PressButton(int nButton);
```

### <a name="parameters"></a>参数

*nButton*<br/>
nButton ：标识要按下的按钮。 此参数可以是以下值之一：

- PSBTN_BACK选择"后退"按钮。

- PSBTN_NEXT选择"下一步"按钮。

- PSBTN_FINISH 选择"完成"按钮。

- PSBTN_OK 选择"确定"按钮。

- PSBTN_APPLYNOW选择"立即应用"按钮。

- PSBTN_CANCEL选择"取消"按钮。

- PSBTN_HELP 选择"帮助"按钮。

### <a name="remarks"></a>备注

有关 Windows SDK 按下按钮消息的详细信息，请参阅[PSM_PRESSBUTTON。](/windows/win32/Controls/psm-pressbutton)

调用`PressButton`不会将[PSN_APPLY](/windows/win32/Controls/psn-apply)通知从属性页发送到框架。 要发送此通知，请致电[CPropertyPage：：OnOK](../../mfc/reference/cpropertypage-class.md#onok)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]

## <a name="cpropertysheetremovepage"></a><a name="removepage"></a>C属性表：删除页

从属性工作表中删除页面并销毁关联的窗口。

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>参数

*pPage*<br/>
指向要从属性表中删除的页面。 不能为 NULL。

*nPage*<br/>
要删除的页面的索引。 必须小于属性表中的页数 0 和 1（包括）。

### <a name="remarks"></a>备注

在`CPropertySheet`关闭窗口的所有者之前，不会销毁[CPropertyPage](../../mfc/reference/cpropertypage-class.md)对象本身。

## <a name="cpropertysheetsetactivepage"></a><a name="setactivepage"></a>C属性表：：设置活动页

更改活动页。

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>参数

*nPage*<br/>
要设置的页面的索引。 它必须小于属性表中的页数 0 和 1（包括）。

*pPage*<br/>
指向要在属性表中设置的页面。 不可为 NULL。

### <a name="return-value"></a>返回值

如果成功激活属性表，则非零;否则 0。

### <a name="remarks"></a>备注

例如，如果用户在`SetActivePage`一页上的操作应导致另一个页面成为活动页，请使用。

### <a name="example"></a>示例

请参阅[CPropertySheet 的示例：获取活动页](#getactivepage)。

## <a name="cpropertysheetsetfinishtext"></a><a name="setfinishtext"></a>C属性表：：设置完成文本

在"完成"命令按钮中设置文本。

```
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

*lpszText*<br/>
指向要显示在"完成"命令按钮上的文本。

### <a name="remarks"></a>备注

调用`SetFinishText`以在"完成"命令按钮上显示文本，并在用户完成向导最后一页上的操作后隐藏"下一步"和"后退"按钮。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

## <a name="cpropertysheetsettitle"></a><a name="settitle"></a>C属性表：：设置标题

指定属性表的标题（框架窗口的标题栏中显示的文本）。

```
void SetTitle(
    LPCTSTR lpszText,
    UINT nStyle = 0);
```

### <a name="parameters"></a>参数

*nStyle*<br/>
指定属性工作表标题的样式。 样式必须在 0 或 PSH_PROPTITLE时指定。 如果样式设置为PSH_PROPTITLE，则单词"属性"将显示在指定为标题的文本之后。 例如，调用`SetTitle`（"简单"，PSH_PROPTITLE）将导致"简单属性"的属性表标题。

*lpszText*<br/>
指向要用作属性表标题栏中标题的文本。

### <a name="remarks"></a>备注

默认情况下，属性表在属性表构造函数中使用标题参数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

## <a name="cpropertysheetsetwizardbuttons"></a><a name="setwizardbuttons"></a>C属性表：：设置向导按钮

启用或禁用向导属性表中的"后退"、"下一步"或"完成"按钮。

```
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>参数

dwFlags**<br/>
一组标志，用于自定义向导按钮的功能和外观。 此参数可以是以下值的组合：

- PSWIZB_BACK"后退"按钮

- PSWIZB_NEXT 下一个按钮

- PSWIZB_FINISH完成按钮

- PSWIZB_DISABLEDFINISH禁用完成按钮

### <a name="remarks"></a>备注

仅在`SetWizardButtons`对话框打开后调用;在致电[DoModal](#domodal)之前`SetWizardButtons`，你不能打电话。 通常，您应该从`SetWizardButtons`[CPropertyPage 调用：打开活动](../../mfc/reference/cpropertypage-class.md#onsetactive)。

如果要更改"完成"按钮上的文本，或在用户完成向导后隐藏"下一步"和"后退"按钮，请调用[SetFinishText](#setfinishtext)。 请注意，为"完成"和"下一步"共享同一按钮。 可以一次显示"完成"或"下一步"按钮，但不能同时显示两者。

### <a name="example"></a>示例

A`CPropertySheet`有三个向导属性`CStylePage`页`CColorPage`：`CShapePage`和 。  下面的代码片段演示如何启用和禁用向导属性页上的 **"后退**"和 **"下一步**"按钮。

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

## <a name="cpropertysheetsetwizardmode"></a><a name="setwizardmode"></a>C属性表：：设置向导模式

将属性页建立为向导。

```
void SetWizardMode();
```

### <a name="remarks"></a>备注

向导属性页的一个关键特征是用户使用"下一步"或"完成"、"后退"和"取消"按钮而不是选项卡进行导航。

呼叫`SetWizardMode` [DoModal](#domodal)之前呼叫 。 调用`SetWizardMode`后，`DoModal`将返回ID_WIZFINISH（如果用户关闭"完成"按钮）或 IDCANCEL。

`SetWizardMode`设置PSH_WIZARD标志。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
