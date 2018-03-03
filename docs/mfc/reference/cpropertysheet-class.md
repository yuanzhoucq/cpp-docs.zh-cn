---
title: "CPropertySheet 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 52c5d167390826578c4e3a2380c885bf1d507d19
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cpropertysheet-class"></a>CPropertySheet 类
表示属性表，也称为选项卡对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class CPropertySheet : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CPropertySheet::CPropertySheet](#cpropertysheet)|构造 `CPropertySheet` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Cpropertysheet:: Addpage](#addpage)|向属性表添加页面。|  
|[CPropertySheet::Construct](#construct)|构造 `CPropertySheet` 对象。|  
|[CPropertySheet::Create](#create)|显示无模式属性表。|  
|[CPropertySheet::DoModal](#domodal)|显示模式属性表。|  
|[Cpropertysheet:: Enablestackedtabs](#enablestackedtabs)|指示属性表是使用堆积或滚动选项卡。|  
|[CPropertySheet::EndDialog](#enddialog)|终止属性表。|  
|[CPropertySheet::GetActiveIndex](#getactiveindex)|检索的活动页面的属性表的索引。|  
|[CPropertySheet::GetActivePage](#getactivepage)|返回活动页对象。|  
|[CPropertySheet::GetPage](#getpage)|检索指向指定页。|  
|[CPropertySheet::GetPageCount](#getpagecount)|检索的属性表中的页数。|  
|[CPropertySheet::GetPageIndex](#getpageindex)|检索的属性表指定页的索引。|  
|[CPropertySheet::GetTabControl](#gettabcontrol)|检索指向选项卡控件的指针。|  
|[CPropertySheet::MapDialogRect](#mapdialogrect)|将矩形的对话框单位转换为屏幕单位。|  
|[Cpropertysheet:: Oninitdialog](#oninitdialog)|重写以增加属性表初始化。|  
|[CPropertySheet::PressButton](#pressbutton)|模拟所选的属性表中指定的按钮。|  
|[CPropertySheet::RemovePage](#removepage)|从属性表删除页。|  
|[CPropertySheet::SetActivePage](#setactivepage)|以编程方式设置活动的页对象。|  
|[CPropertySheet::SetFinishText](#setfinishtext)|设置完成按钮的文本。|  
|[CPropertySheet::SetTitle](#settitle)|设置的属性表的标题。|  
|[CPropertySheet::SetWizardButtons](#setwizardbuttons)|使向导按钮。|  
|[CPropertySheet::SetWizardMode](#setwizardmode)|使向导模式。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CPropertySheet::m_psh](#m_psh)|Windows [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546)结构。 提供对基本的属性表参数访问。|  
  
## <a name="remarks"></a>备注  
 属性表组成`CPropertySheet`对象和一个或多个[CPropertyPage](../../mfc/reference/cpropertypage-class.md)对象。 框架显示属性表作为具有一组选项卡索引和一个区域，它包含当前所选的页面的窗口。 用户导航到特定页通过使用相应的选项卡。  
  
 `CPropertySheet`提供对扩展的支持[PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546)结构在中引入[!INCLUDE[Win98](../../mfc/reference/includes/win98_md.md)]和 Windows NT 2000。 该结构包含其他标志和支持使用"水印"背景位图的成员。  
  
 若要在你的属性表对象中自动显示这些新映像，请将有效值的位图和调色板映像传递对的调用中[CPropertySheet::Construct](#construct)或[CPropertySheet::CPropertySheet](#cpropertysheet).  
  
 即使`CPropertySheet`不派生自[CDialog](../../mfc/reference/cdialog-class.md)，管理`CPropertySheet`对象就像管理`CDialog`对象。 例如，需要两个部分构成构造属性表的创建： 调用的构造函数，然后调用[DoModal](#domodal)模式属性表或[创建](#create)无模式属性表。 `CPropertySheet`有两种类型的构造函数： [CPropertySheet::Construct](#construct)和[CPropertySheet::CPropertySheet](#cpropertysheet)。  
  
 构造时`CPropertySheet`对象时，某些[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)可能会导致首次异常出现。 这将导致从系统尝试创建该工作表之前更改的属性表样式。 若要避免此异常，请确保在创建时设置以下样式你`CPropertySheet`:  
  
-   DS_3DLOOK  
  
-   DS_CONTROL  
  
-   WS_CHILD  
  
-   WS_TABSTOP  
  
 以下样式是可选的并不会导致首次异常：  
  
-   DS_SHELLFONT  
  
-   DS_LOCALEDIT  
  
-   WS_CLIPCHILDREN  
  
 任何其他`Window Styles`程序以及禁止的而应启用它们。  
  
 之间交换数据`CPropertySheet`对象和外部对象是类似于与交换数据`CDialog`对象。 重要的区别是属性表的这些设置通常是的成员变量`CPropertyPage`对象而不是`CPropertySheet`对象本身。  
  
 你可以创建一种称为向导，指导用户完成了操作，例如设置设备，或创建新闻稿的步骤的属性页中的序列与包含属性表的选项卡对话框。 在向导类型选项卡对话框中，属性页没有选项卡上，且仅一个属性页可见一次。 此外，而不是**确定**和**立即应用**按钮，向导类型选项卡对话框具有**回**按钮，**下一步**或**完成**按钮，**取消**按钮，和一个**帮助**按钮。  
  
 若要创建向导类型对话框中，按照相同步骤，你可以按照创建标准属性表，但调用[SetWizardMode](#setwizardmode)之前调用[DoModal](#domodal)。 若要启用的向导按钮，调用[SetWizardButtons](#setwizardbuttons)，使用标志自定义它们的功能和外观。 若要启用**完成**按钮，调用[SetFinishText](#setfinishtext)用户已在向导的最后一页上执行操作后。  
  
 有关如何使用`CPropertySheet`对象，请参阅文章[属性表和属性页](../../mfc/property-sheets-and-property-pages-in-mfc.md)。 此外，请参阅知识库文章 Q146916： 如何： 使用标准按钮创建无模式 CPropertySheet 和文章 Q300606： 如何： 设计可调整大小的 MFC 属性表。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPropertySheet`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxdlgs.h  
  
##  <a name="addpage"></a>Cpropertysheet:: Addpage  
 在属性表中添加与最右边的选项卡提供的页。  
  
```  
void AddPage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>参数  
 `pPage`  
 指向以页后，可以添加到属性表。 不能为**NULL**。  
  
### <a name="remarks"></a>备注  
 将页面添加到你希望它们出现的从左到右顺序属性表。  
  
 `AddPage`将添加[CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)对象传递给`CPropertySheet`对象的页的列表，但不是实际创建页窗口。 框架推迟的页的窗口的创建，直到用户选择该页面。  
  
 当你添加属性页使用`AddPage`、`CPropertySheet`父级的`CPropertyPage`。 若要从属性页中获取到属性表的访问权限，调用[CWnd::GetParent](../../mfc/reference/cwnd-class.md#getparent)。  
  
 不需要等到创建属性表窗口调用`AddPage`。 通常，你可以将调用`AddPage`之前调用[DoModal](#domodal)或[创建](#create)。  
  
 如果调用`AddPage`之后显示的属性页，选项卡行将反映新添加的页。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]  
  
##  <a name="construct"></a>CPropertySheet::Construct  
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
 `nIDCaption`  
 要用于属性表标题的 ID。  
  
 `pParentWnd`  
 到属性表的父窗口的指针。 如果**NULL**，父窗口将应用程序的主窗口。  
  
 `iSelectPage`  
 最初将成为在最前面的页的索引。 默认值为添加到表中的第一页。  
  
 `pszCaption`  
 指向包含要用于属性表的标题的字符串的指针。 不能为**NULL**。  
  
 `hbmWatermark`  
 在属性页水印位图的句柄。  
  
 `hpalWatermark`  
 水印位图和/或标头位图的调色板的句柄。  
  
 `hbmHeader`  
 属性页的标头位图的句柄。  
  
### <a name="remarks"></a>备注  
 如果类构造函数之一不已调用，则调用此成员函数。 例如，调用`Construct`声明或分配的数组时`CPropertySheet`对象。 对于数组，必须调用`Construct`数组中每个成员。  
  
 若要显示属性表，请调用[DoModal](#domodal)或[创建](#create)。 将在属性表的标题栏中放置的第一个参数中包含的字符串。  
  
 如果你使用的第三个或第四个原型，你可以自动显示水印和/或标头的图像`Construct`，列出更高版本，且您传递有效的值`hbmWatermark`， `hpalWatermark`，和/或`hbmHeader`参数。  
  
### <a name="example"></a>示例  
 下面的示例演示在什么情况下，您将调用`Construct`。  
  
 [!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]  
  
##  <a name="cpropertysheet"></a>CPropertySheet::CPropertySheet  
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
 `nIDCaption`  
 要用于属性表标题的 ID。  
  
 `pParentWnd`  
 指向属性表的父窗口。 如果**NULL**，父窗口将应用程序的主窗口。  
  
 `iSelectPage`  
 最初将成为在最前面的页的索引。 默认值为添加到表中的第一页。  
  
 `pszCaption`  
 指向包含要用于属性表的标题的字符串。 不能为**NULL**。  
  
 `hbmWatermark`  
 属性表的背景位图句柄。  
  
 `hpalWatermark`  
 水印位图和/或标头位图的调色板的句柄。  
  
 `hbmHeader`  
 属性页的标头位图句柄。  
  
### <a name="remarks"></a>备注  
 若要显示属性表，请调用[DoModal](#domodal)或[创建](#create)。 将在属性表的标题栏中放置的第一个参数中包含的字符串。  
  
 如果你有多个参数 （例如，如果你使用的数组），使用[构造](#construct)而不是`CPropertySheet`。  
  
 如果你使用的第三个或第四个原型，你可以自动显示水印和/或标头的图像`CPropertySheet`、 更高版本，并将有效的值传递`hbmWatermark`， `hpalWatermark`，和/或`hbmHeader`参数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]  
  
##  <a name="create"></a>CPropertySheet::Create  
 显示无模式属性表。  
  
```  
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);  
```  
  
### <a name="parameters"></a>参数  
 `pParentWnd`  
 指向以父窗口。 如果**NULL**，父情况是桌面。  
  
 `dwStyle`  
 属性表的窗口样式。 有关可用样式的完整列表，请参阅[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。  
  
 `dwExStyle`  
 属性表的扩展的窗口样式。 有关可用样式的完整列表，请参阅[扩展窗口样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建属性表则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 调用**创建**可以是在构造函数中，或后调用的构造函数可以调用它。  
  
 默认样式，表示通过将传递为-1 表示`dwStyle`，实际**WS_SYSMENU &#124;**`WS_POPUP` **&#124;WS_CAPTION &#124; DS_MODALFRAME &#124; DS_CONTEXTHELP &#124;WS_VISIBLE**。 默认值扩展窗口样式，表示通过将 0 作为传递`dwExStyle`，实际**WS_EX_DLGMODALFRAME**。  
  
 **创建**成员函数将在创建属性表后立即返回。 若要销毁属性表，调用[cwnd:: Destroywindow](../../mfc/reference/cwnd-class.md#destroywindow)。  
  
 无模式属性表显示通过调用**创建**没有确定、 取消，立即应用和帮助按钮，模式属性表一样。 必须由用户创建所需的按钮。  
  
 若要显示模式属性表，请调用[DoModal](#domodal)相反。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]  
  
##  <a name="domodal"></a>CPropertySheet::DoModal  
 显示模式属性表。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 `IDOK`或`IDCANCEL`如果函数是与成功; 否则为 0 或-1。 如果已建立属性表作为向导 (请参阅[SetWizardMode](#setwizardmode))，`DoModal`返回`ID_WIZFINISH`或`IDCANCEL`。  
  
### <a name="remarks"></a>备注  
 返回值对应于关闭属性表控件的 ID。 此函数返回后，将销毁 windows 对应于属性表和所有页。 对象本身仍存在。 通常情况下，将检索数据从[CPropertyPage](../../mfc/reference/cpropertypage-class.md)对象后`DoModal`返回`IDOK`。  
  
 若要显示无模式属性表，请调用[创建](#create)相反。  
  
 从其相应的对话框资源创建属性页时，它可能会导致首次异常。 这将导致从之前创建页面对话框资源的样式更改为所需的样式的属性页。 因为资源通常是只读的这将导致异常。 系统处理异常，并使已修改的资源的副本。 首次异常因此被忽略。  
  
> [!NOTE]
>  如果你正在使用异步异常处理模型进行编译，操作系统必须处理此异常。 有关异常处理模型的详细信息，请参阅[/EH （异常处理模型）](../../build/reference/eh-exception-handling-model.md)。 在这种情况下，不换行调用`CPropertySheet::DoModal`与 c + + try catch 块在其中 catch 处理所有异常，例如， `catch (...)`。 此块将处理适用于操作系统和原因不可预知的行为的异常。 但是，你可以安全地使用 c + + 异常处理与特定异常类型或结构化的异常处理的访问冲突异常通过传递到操作系统。  
  
 若要避免生成此首次异常，你可以手动保证属性表有正确[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 你需要设置一个属性表的以下样式：  
  
-   DS_3DLOOK  
  
-   DS_CONTROL  
  
-   WS_CHILD  
  
-   WS_TABSTOP  
  
 你可以使用以下可选样式，而不会导致首次异常：  
  
-   DS_SHELLFONT  
  
-   DS_LOCALEDIT  
  
-   WS_CLIPCHILDREN  
  
 禁用所有其他 Windows 样式，因为它们不是与属性表兼容。 此建议不适用于扩展样式。 适当地设置这些标准样式可以保证在属性表没有要修改和将避免生成首次异常。  
  
### <a name="example"></a>示例  
  请参阅示例[cpropertysheet:: Addpage](#addpage)。  
  
##  <a name="enablestackedtabs"></a>Cpropertysheet:: Enablestackedtabs  
 指示是否堆栈中的属性表选项卡的行。  
  
```  
void EnableStackedTabs(BOOL bStacked);
```  
  
### <a name="parameters"></a>参数  
 `bStacked`  
 指示是否属性表中启用堆积选项卡。 通过设置来禁用堆积的行标记`bStacked`到**FALSE**。  
  
### <a name="remarks"></a>备注  
 默认情况下，如果属性表具有更多选项卡而不能显示在宽度属性表的单个行中选项卡将堆积在多行。 若要使用滚动选项卡而不是堆叠选项卡，调用`EnableStackedTabs`与`bStacked`设置为**FALSE**之前调用[DoModal](#domodal)或[创建](#create)。  
  
 必须调用`EnableStackedTabs`在创建模式或无模式属性表。 将在此样式`CPropertySheet`-派生类中，消息处理程序编写为`WM_CREATE`。 中的重写版本[CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)，调用**EnableStackedTabs (FALSE)**之前调用基类实现。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]  
  
##  <a name="enddialog"></a>CPropertySheet::EndDialog  
 终止属性表。  
  
```  
void EndDialog(int nEndID);
```  
  
### <a name="parameters"></a>参数  
 *nEndID*  
 要用作返回值的属性表的标识符。  
  
### <a name="remarks"></a>备注  
 按下确定、 取消或关闭按钮时，将由框架调用此成员函数。 调用此成员函数，如果发生事件时，应关闭属性表。  
  
 此成员函数仅用于模式对话框。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertySheet::PressButton](#pressbutton)。  
  
##  <a name="getactiveindex"></a>CPropertySheet::GetActiveIndex  
 获取属性表窗口的活动页的索引号，然后与的参数中使用返回的索引号`GetPage`。  
  
```  
int GetActiveIndex() const;  
```  
  
### <a name="return-value"></a>返回值  
 活动页的索引号。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertySheet::GetActivePage](#getactivepage)。  
  
##  <a name="getactivepage"></a>CPropertySheet::GetActivePage  
 检索属性表窗口的活动页。  
  
```  
CPropertyPage* GetActivePage() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向的活动页面的指针。  
  
### <a name="remarks"></a>备注  
 使用此成员函数以活动页面上执行某些操作。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]  
  
##  <a name="getpage"></a>CPropertySheet::GetPage  
 将指针返回到此属性表中的指定页。  
  
```  
CPropertyPage* GetPage(int nPage) const;  
```  
  
### <a name="parameters"></a>参数  
 `nPage`  
 索引所需的页上，从 0 开始。 必须是介于 0 和一个小于 （含） 的属性表中的页面数之间。  
  
### <a name="return-value"></a>返回值  
 指向对应的页面的指针`nPage`参数。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish)。  
  
##  <a name="getpagecount"></a>CPropertySheet::GetPageCount  
 确定当前属性表中的页面数。  
  
```  
int GetPageCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 属性表中的页面数。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish)。  
  
##  <a name="getpageindex"></a>CPropertySheet::GetPageIndex  
 检索属性表中指定的页的索引号。  
  
```  
int GetPageIndex(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>参数  
 `pPage`  
 指向包含要查找的索引的页面。 不能为**NULL**。  
  
### <a name="return-value"></a>返回值  
 页的索引号。  
  
### <a name="remarks"></a>备注  
 例如，你将使用`GetPageIndex`来获取的页索引，以便使用[SetActivePage](#setactivepage)或[GetPage](#getpage)。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertySheet::GetActivePage](#getactivepage)。  
  
##  <a name="gettabcontrol"></a>CPropertySheet::GetTabControl  
 检索指向选项卡控件执行操作特定于选项卡控件 (即，使用中的 Api 的任何[CTabCtrl](../../mfc/reference/ctabctrl-class.md))。  
  
```  
CTabCtrl* GetTabControl() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向选项卡控件的指针。  
  
### <a name="remarks"></a>备注  
 如果你想要将位图添加到每个选项卡，在初始化期间，例如，调用此成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]  
  
##  <a name="m_psh"></a>CPropertySheet::m_psh  
 其成员存储的特征的结构[PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546)。  
  
### <a name="remarks"></a>备注  
 使用此结构来初始化属性表的外观，它构造之后，但它显示为带之前[DoModal](#domodal)成员函数。 例如，设置`dwSize`的成员`m_psh`你想要具有的属性表的大小。  
  
 此结构，包括其成员的列表的详细信息请参阅**PROPSHEETHEADER** Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]  
  
##  <a name="mapdialogrect"></a>CPropertySheet::MapDialogRect  
 将矩形的对话框单位转换为屏幕单位。  
  
```  
void MapDialogRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)包含对话框中的对象要转换的坐标。  
  
### <a name="remarks"></a>备注  
 在派生自的平均宽度和高度的用于对话框文本的字体中字符的当前对话框基本单位方面阐述对话框单位。 一个水平单元是对话框基本宽度单位 （） 的四分之一，一个垂直单元的八分之一对话框基高度单元。  
  
 [GetDialogBaseUnits](http://msdn.microsoft.com/library/windows/desktop/ms645475) Windows 函数将返回系统字体的大小信息，但你可以指定不同的字体的每个属性表，如果你使用**DS_SETFONT**设置中的样式资源定义文件。 [MapDialogRect](http://msdn.microsoft.com/library/windows/desktop/ms645502) Windows 函数，在 Windows SDK 中，将会介绍用于此对话框中的相应的字体。  
  
 `MapDialogRect`成员函数将替换中的对话框单元`lpRect`与屏幕单位 （像素），以便可以使用矩形来创建一个对话框，或将控件放在一个框内。  
  
##  <a name="oninitdialog"></a>Cpropertysheet:: Oninitdialog  
 替代来增加属性表初始化。  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>返回值  
 指定应用程序是否已将输入的焦点设置到其中一个属性表中的控件。 如果**OnInitDialog**返回非零，则 Windows 会将输入的焦点设置到属性表中的第一个控件。 只有当它已显式设置为它的一个属性表中控件的输入的焦点，则该应用程序可以返回 0。  
  
### <a name="remarks"></a>备注  
 此成员函数调用以响应**WM_INITDIALOG**消息。 此消息将发送到属性表期间[创建](#create)或[DoModal](#domodal)调用，在显示属性表之前立即发生。  
  
 如果你需要执行特殊处理，在初始化属性表时，重写该成员函数。 在重写的版本中，首先调用基类`OnInitDialog`但忽略其返回值。 通常将返回**TRUE**从你重写的成员函数。  
  
 此成员函数不需要一个消息映射条目。  
  
##  <a name="pressbutton"></a>CPropertySheet::PressButton  
 模拟所选的属性表中指定的按钮。  
  
```  
void PressButton(int nButton);
```  
  
### <a name="parameters"></a>参数  
 `nButton`  
 nButton： 标识要按下的按钮。 此参数可以是以下值之一：  
  
- **PSBTN_BACK**选择后退按钮。  
  
- **PSBTN_NEXT**选择下一步按钮。  
  
- **PSBTN_FINISH**选择完成按钮。  
  
- **PSBTN_OK**选择确定按钮。  
  
- **PSBTN_APPLYNOW**选择立即应用按钮。  
  
- **PSBTN_CANCEL**选择取消按钮。  
  
- **PSBTN_HELP**选择帮助按钮。  
  
### <a name="remarks"></a>备注  
 请参阅[PSM_PRESSBUTTON](http://msdn.microsoft.com/library/windows/desktop/bb774597) Windows SDK Pressbutton 消息有关的详细信息。  
  
 调用`PressButton`不会发送[PSN_APPLY](http://msdn.microsoft.com/library/windows/desktop/bb774552)到框架在属性页上的通知。 若要发送此通知时，调用[CPropertyPage::OnOK](../../mfc/reference/cpropertypage-class.md#onok)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]  
  
##  <a name="removepage"></a>CPropertySheet::RemovePage  
 从属性表删除页，并销毁关联的窗口。  
  
```  
void RemovePage(CPropertyPage* pPage);  
void RemovePage(int nPage);
```  
  
### <a name="parameters"></a>参数  
 `pPage`  
 指向以页后，可以从属性表中删除。 不能为 `NULL`。  
  
 `nPage`  
 要删除的页的索引。 必须是介于 0 和一个小于 （含） 的属性表中的页面数之间。  
  
### <a name="remarks"></a>备注  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)对象本身不会被销毁之前的所有者`CPropertySheet`窗口已关闭。  
  
##  <a name="setactivepage"></a>CPropertySheet::SetActivePage  
 更改的活动页面。  
  
```  
BOOL SetActivePage(int nPage);  
BOOL SetActivePage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>参数  
 `nPage`  
 要设置的页的索引。 它必须是介于 0 和一个小于 （含） 的属性表中的页面数之间。  
  
 `pPage`  
 指向要设置的属性表中的页。 它不能是**NULL**。  
  
### <a name="return-value"></a>返回值  
 如果成功，则激活属性表则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 例如，使用`SetActivePage`如果在一页上的用户的操作会导致另一个页面会在活动页面。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertySheet::GetActivePage](#getactivepage)。  
  
##  <a name="setfinishtext"></a>CPropertySheet::SetFinishText  
 设置中完成命令按钮的文本。  
  
```  
void SetFinishText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
 `lpszText`  
 指向要显示在完成命令按钮的文本。  
  
### <a name="remarks"></a>备注  
 调用`SetFinishText`以在完成命令按钮上显示文本和隐藏下一步和后退按钮后用户在完成向导的最后一页上的操作。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]  
  
##  <a name="settitle"></a>CPropertySheet::SetTitle  
 指定属性表的标题 （框架窗口的标题栏中显示的文本）。  
  
```  
void SetTitle(
    LPCTSTR lpszText,  
    UINT nStyle = 0);
```  
  
### <a name="parameters"></a>参数  
 `nStyle`  
 指定的属性表标题的样式。 必须指定的样式，0 或作为**PSH_PROPTITLE**。 如果将样式设置为**PSH_PROPTITLE**，在指定为标题文本之后显示单词"属性"。 例如，调用`SetTitle`("简单" **PSH_PROPTITLE**) 将导致在属性表标题的"简单属性。  
  
 `lpszText`  
 指向要将其用于在属性表的标题栏中标题的文本。  
  
### <a name="remarks"></a>备注  
 默认情况下，属性表的属性表构造函数中使用标题参数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]  
  
##  <a name="setwizardbuttons"></a>CPropertySheet::SetWizardButtons  
 启用或禁用向导属性表中的后退、 下一步或完成按钮。  
  
```  
void SetWizardButtons(DWORD dwFlags);
```  
  
### <a name="parameters"></a>参数  
 `dwFlags`  
 一组自定义的函数和向导按钮外观的标志。 此参数可以是以下值的组合：  
  
- **PSWIZB_BACK**后退按钮  
  
- **PSWIZB_NEXT**下一步按钮  
  
- **PSWIZB_FINISH**完成按钮  
  
- **PSWIZB_DISABLEDFINISH**已禁用完成按钮  
  
### <a name="remarks"></a>备注  
 调用`SetWizardButtons`仅对话框已打开，则后不能调用`SetWizardButtons`之前调用[DoModal](#domodal)。 通常情况下，应调用`SetWizardButtons`从[cpropertypage:: Onsetactive](../../mfc/reference/cpropertypage-class.md#onsetactive)。  
  
 如果你想要更改完成按钮上的文本或隐藏下一步和后退按钮一次该用户已完成向导中，调用[SetFinishText](#setfinishtext)。 请注意下, 一步完成以及共享相同的按钮。 你可以显示完成或下一步按钮一次，但不是两者。  
  
### <a name="example"></a>示例  
 A`CPropertySheet`有三个向导属性页： `CStylePage`， `CColorPage`，和`CShapePage`。  下面的代码片段演示如何启用和禁用**回**和**下一步**向导属性页上的按钮。  
  
 [!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]  
  
##  <a name="setwizardmode"></a>CPropertySheet::SetWizardMode  
 确定为向导的属性页。  
  
```  
void SetWizardMode();
```  
  
### <a name="remarks"></a>备注  
 向导属性页的关键特征是，在用户导航下一步使用或完成、 后退、 和取消按钮而不是选项卡。  
  
 调用`SetWizardMode`之前调用[DoModal](#domodal)。 调用后`SetWizardMode`，`DoModal`将返回**ID_WIZFINISH** （如果用户关闭与完成按钮） 或**IDCANCEL**。  
  
 `SetWizardMode`设置 PSH_WIZARD 标志。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 CMNCTRL1](../../visual-cpp-samples.md)   
 [MFC 示例 CMNCTRL2](../../visual-cpp-samples.md)   
 [MFC 示例 PROPDLG](../../visual-cpp-samples.md)   
 [MFC 示例 SNAPVW](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)



