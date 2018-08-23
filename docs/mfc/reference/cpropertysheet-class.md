---
title: CPropertySheet 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 994e9f8c48bb6d6db2a9af06613abca895b09f51
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42538228"
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
|[Cpropertysheet:: Domodal](#domodal)|显示模式属性表。|  
|[Cpropertysheet:: Enablestackedtabs](#enablestackedtabs)|指示是否在属性表使用堆积或滚动选项卡。|  
|[CPropertySheet::EndDialog](#enddialog)|终止属性表。|  
|[CPropertySheet::GetActiveIndex](#getactiveindex)|检索活动的属性表页的索引。|  
|[CPropertySheet::GetActivePage](#getactivepage)|返回活动页对象。|  
|[CPropertySheet::GetPage](#getpage)|检索指向指定的页。|  
|[CPropertySheet::GetPageCount](#getpagecount)|检索的属性表中的页数。|  
|[CPropertySheet::GetPageIndex](#getpageindex)|检索指定的属性表页的索引。|  
|[CPropertySheet::GetTabControl](#gettabcontrol)|检索指向选项卡控件。|  
|[CPropertySheet::MapDialogRect](#mapdialogrect)|将一个矩形的对话框单位转换为屏幕单位。|  
|[Cpropertysheet:: Oninitdialog](#oninitdialog)|重写以增加属性表初始化。|  
|[CPropertySheet::PressButton](#pressbutton)|模拟所选的属性表中指定的按钮。|  
|[CPropertySheet::RemovePage](#removepage)|删除从属性表页。|  
|[CPropertySheet::SetActivePage](#setactivepage)|以编程方式设置活动页对象。|  
|[CPropertySheet::SetFinishText](#setfinishtext)|设置为完成按钮的文本。|  
|[CPropertySheet::SetTitle](#settitle)|设置的属性表的标题。|  
|[CPropertySheet::SetWizardButtons](#setwizardbuttons)|使向导按钮。|  
|[CPropertySheet::SetWizardMode](#setwizardmode)|使向导模式。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CPropertySheet::m_psh](#m_psh)|Windows [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546)结构。 提供对基本属性表参数访问。|  
  
## <a name="remarks"></a>备注  
 属性表组成`CPropertySheet`对象和一个或多个[CPropertyPage](../../mfc/reference/cpropertypage-class.md)对象。 框架显示属性表为具有一组选项卡索引和区域，其中包含当前所选的页面的窗口。 用户导航到特定页通过使用相应的选项卡。  
  
 `CPropertySheet` 提供对扩展的支持[PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546) Windows 98 和 Windows NT 2000 中引入的结构。 该结构包含其他标志和支持使用"水印"背景位图的成员。  
  
 若要在属性表对象中自动显示这些新映像，对的调用中传递的位图和调色板映像的有效值[CPropertySheet::Construct](#construct)或[CPropertySheet::CPropertySheet](#cpropertysheet).  
  
 即使`CPropertySheet`不派生自[CDialog](../../mfc/reference/cdialog-class.md)，以及管理`CPropertySheet`对象是类似于管理`CDialog`对象。 例如，创建属性表的所需的两部分构造： 调用构造函数中，，然后调用[DoModal](#domodal)的模式属性表或[创建](#create)无模式属性表。 `CPropertySheet` 有两种类型的构造函数： [CPropertySheet::Construct](#construct)并[CPropertySheet::CPropertySheet](#cpropertysheet)。  
  
 当构造`CPropertySheet`对象时，某些[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)会导致首次异常发生。 这将导致从系统尝试进行更改的属性表样式，然后创建工作表。 若要避免此异常，请确保在创建时设置以下样式在`CPropertySheet`:  
  
-   DS_3DLOOK  
  
-   DS_CONTROL  
  
-   WS_CHILD  
  
-   WS_TABSTOP  
  
 以下样式是可选的并且不会导致首次异常：  
  
-   DS_SHELLFONT  
  
-   DS_LOCALEDIT  
  
-   WS_CLIPCHILDREN  
  
 任何其他`Window Styles`以及禁止的而应启用它们。  
  
 之间交换数据`CPropertySheet`对象和一个外部对象是类似于与交换数据`CDialog`对象。 重要的区别是，属性表的设置是通常的成员变量`CPropertyPage`对象而不是`CPropertySheet`对象本身。  
  
 可以创建一种称为向导，其中包含具有一系列指导用户完成操作，例如设置设备，或创建时事通讯的步骤的属性页的属性表选项卡对话框。 向导类型选项卡对话框中，在属性页无选项卡上，并一次只有一个属性页上可见。 此外，而不是让**确定**并**立即应用**按钮，向导类型选项卡对话框具有**回**按钮，**下一步**或**完成**按钮，**取消**按钮，和一个**帮助**按钮。  
  
 若要创建向导类型对话框，请按照你创建的标准属性表，但调用时要遵循的相同步骤[SetWizardMode](#setwizardmode)在调用之前[DoModal](#domodal)。 若要启用的向导按钮，调用[SetWizardButtons](#setwizardbuttons)，使用标志自定义其功能和外观。 若要启用**完成**按钮，调用[SetFinishText](#setfinishtext)用户已在向导的最后一页上执行操作之后。  
  
 有关如何使用详细信息`CPropertySheet`对象，请参阅文章[属性表和属性页](../../mfc/property-sheets-and-property-pages-in-mfc.md)。 此外，请参阅知识库文章 Q146916： 如何： 使用标准按钮创建无模式 CPropertySheet，且项目 Q300606： 如何： 设计可调整大小的 MFC 属性表。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPropertySheet`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdlgs.h  
  
##  <a name="addpage"></a>  Cpropertysheet:: Addpage  
 将提供与最右侧的选项卡页添加属性表中。  
  
```  
void AddPage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>参数  
 *pPage*  
 指向要添加到属性表页。 不能为 NULL。  
  
### <a name="remarks"></a>备注  
 将页面添加到属性表中您希望它们显示的从左到右顺序。  
  
 `AddPage` 将添加[CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)对象传递给`CPropertySheet`对象的页的列表，但不会实际创建页面的窗口。 Framework 推迟创建的窗口的页上，直到用户选择该页面。  
  
 添加属性页中使用时`AddPage`，则`CPropertySheet`父级的`CPropertyPage`。 若要从属性页中获取到属性表的访问权限，调用[CWnd::GetParent](../../mfc/reference/cwnd-class.md#getparent)。  
  
 不需要等到创建属性表窗口调用`AddPage`。 通常情况下，将调用`AddPage`之前调用[DoModal](#domodal)或[创建](#create)。  
  
 如果调用`AddPage`之后显示的属性页、 选项卡行将反映新添加的页。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]  
  
##  <a name="construct"></a>  CPropertySheet::Construct  
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
 *nIDCaption*  
 要用于属性表的标题的 ID。  
  
 *pParentWnd*  
 向属性表的父窗口的指针。 如果为 NULL，父窗口将应用程序的主窗口。  
  
 *iSelectPage*  
 最初将成为在最前面的页的索引。 默认值为添加到表中的第一页。  
  
 *pszCaption*  
 包含要用于属性表的标题的字符串指针。 不能为 NULL。  
  
 *hbmWatermark*  
 属性页的水印位图的句柄。  
  
 *hpalWatermark*  
 水印位图和/或标头位图的调色板的句柄。  
  
 *hbmHeader*  
 属性页的标头位图的句柄。  
  
### <a name="remarks"></a>备注  
 如果一个类构造函数不已调用，则调用此成员函数。 例如，调用`Construct`声明或分配的数组时`CPropertySheet`对象。 对于数组，必须调用`Construct`数组中每个成员。  
  
 若要显示属性表，请调用[DoModal](#domodal)或[创建](#create)。 第一个参数中包含的字符串将放入属性表的标题栏。  
  
 如果使用的第三个或第四个原型，您可以自动显示水印和/或标头图像`Construct`，以上所列并将有效的值传递*hbmWatermark*， *hpalWatermark*和/或*hbmHeader*参数。  
  
### <a name="example"></a>示例  
 下面的示例演示在什么情况下，您将调用`Construct`。  
  
 [!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]  
  
##  <a name="cpropertysheet"></a>  CPropertySheet::CPropertySheet  
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
 *nIDCaption*  
 要用于属性表的标题的 ID。  
  
 *pParentWnd*  
 指向属性表的父窗口。 如果为 NULL，父窗口将应用程序的主窗口。  
  
 *iSelectPage*  
 最初将成为在最前面的页的索引。 默认值为添加到表中的第一页。  
  
 *pszCaption*  
 指向包含要用于属性表的标题的字符串。 不能为 NULL。  
  
 *hbmWatermark*  
 属性表的背景位图句柄。  
  
 *hpalWatermark*  
 调色板的句柄的水印位图和/或标头位图。  
  
 *hbmHeader*  
 位图的句柄标头的属性页。  
  
### <a name="remarks"></a>备注  
 若要显示属性表，请调用[DoModal](#domodal)或[创建](#create)。 第一个参数中包含的字符串将放入属性表的标题栏。  
  
 如果你有多个参数 （例如，如果您使用的数组），使用[构造](#construct)而不是`CPropertySheet`。  
  
 如果使用的第三个或第四个原型，您可以自动显示水印和/或标头图像`CPropertySheet`、 更高版本，并将有效的值传递进行*hbmWatermark*， *hpalWatermark*，和 /或*hbmHeader*参数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]  
  
##  <a name="create"></a>  CPropertySheet::Create  
 显示无模式属性表。  
  
```  
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);  
```  
  
### <a name="parameters"></a>参数  
 *pParentWnd*  
 指向父窗口。 如果为 NULL，则父级为桌面。  
  
 *dwStyle*  
 属性表的窗口样式。 有关可用样式的完整列表，请参阅[的窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。  
  
 *dwExStyle*  
 属性表的扩展的窗口样式。 有关可用样式的完整列表，请参阅[扩展窗口样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建属性表，非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 对调用`Create`可以是在构造函数，也可以调用的构造函数后调用。  
  
 默认样式，通过传递为-1 以表示*dwStyle*，是实际 WS_SYSMENU&#124;WS_POPUP&#124;WS_CAPTION&#124;DS_MODALFRAME&#124;DS_CONTEXTHELP&#124;WS_VISIBLE。 默认值扩展窗口样式，表示通过传递 0 作为*dwExStyle*，是实际 WS_EX_DLGMODALFRAME。  
  
 `Create`成员函数创建属性表后立即返回。 若要销毁的属性表，请调用[cwnd:: Destroywindow](../../mfc/reference/cwnd-class.md#destroywindow)。  
  
 无模式属性表显示通过调用`Create`与模式属性表不具有确定、 取消，立即应用和帮助按钮。 必须由用户创建所需的按钮。  
  
 若要显示模式属性表，请调用[DoModal](#domodal)相反。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]  
  
##  <a name="domodal"></a>  Cpropertysheet:: Domodal  
 显示模式属性表。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 IDOK 或 IDCANCEL 如果函数成功，则否则为 0 或-1。 如果已建立属性表作为向导 (请参阅[SetWizardMode](#setwizardmode))，`DoModal`返回 ID_WIZFINISH 或 IDCANCEL。  
  
### <a name="remarks"></a>备注  
 返回值对应于关闭属性表控件的 ID。 此函数返回后，将销毁 windows 对应于属性表，所有页面。 对象本身仍将存在。 通常情况下，将检索数据[CPropertyPage](../../mfc/reference/cpropertypage-class.md)对象后`DoModal`返回 IDOK。  
  
 若要显示无模式属性表，请调用[创建](#create)相反。  
  
 从其相应的对话框资源创建属性页，它可能会导致首次异常。 这将导致从之前创建该页面为所需的样式更改对话框资源的样式的属性页。 因为资源通常是只读的这将导致异常。 系统处理异常，并将已修改的资源的副本。 因此可以忽略第一个可能发生的异常。  
  
> [!NOTE]
>  如果使用的异步异常处理模型进行编译，操作系统必须处理此异常。 有关异常处理模型的详细信息，请参阅[/EH （异常处理模型）](../../build/reference/eh-exception-handling-model.md)。 在这种情况下，不换行对的调用`CPropertySheet::DoModal`与 c + + try catch 块中的 catch 处理所有异常，例如， `catch (...)`。 此块会处理适用于操作系统，并导致不可预知的行为的异常。 但是，您可以安全地使用 c + + 异常处理与特定异常类型或结构化的异常处理的访问冲突异常通过传递到操作系统。  
  
 若要避免生成此第一机会异常，您可以手动保证属性表具有正确[的窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 需要设置以下样式的属性表：  
  
-   DS_3DLOOK  
  
-   DS_CONTROL  
  
-   WS_CHILD  
  
-   WS_TABSTOP  
  
 您可以使用以下可选样式，而不会导致首次异常：  
  
-   DS_SHELLFONT  
  
-   DS_LOCALEDIT  
  
-   WS_CLIPCHILDREN  
  
 禁用所有其他 Windows 样式，因为它们不是与属性表兼容。 此建议不适用于扩展样式。 适当地设置这些标准样式将保证属性表不需要进行修改，并将避免生成首次异常。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[cpropertysheet:: Addpage](#addpage)。  
  
##  <a name="enablestackedtabs"></a>  Cpropertysheet:: Enablestackedtabs  
 指示是否堆栈选项卡属性表中的行数。  
  
```  
void EnableStackedTabs(BOOL bStacked);
```  
  
### <a name="parameters"></a>参数  
 *bStacked*  
 指示是否在属性表中启用了堆积选项卡。 通过设置来禁用标记的堆积的行*bStacked*为 FALSE。  
  
### <a name="remarks"></a>备注  
 默认情况下，如果属性表具有更多选项卡以外的属性页中，在宽度单行选项卡将堆叠在多行中。 若要使用滚动选项卡而不是堆叠的选项卡，请调用`EnableStackedTabs`与*bStacked*设置为 FALSE，然后再调[DoModal](#domodal)或[创建](#create)。  
  
 必须调用`EnableStackedTabs`在创建模式或无模式属性表。 若要包含在此样式`CPropertySheet`-派生的类，编写 WM_CREATE 消息处理程序。 中的重写版本[CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)，调用`EnableStackedTabs( FALSE )`之前调用基类实现。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]  
  
##  <a name="enddialog"></a>  CPropertySheet::EndDialog  
 终止属性表。  
  
```  
void EndDialog(int nEndID);
```  
  
### <a name="parameters"></a>参数  
 *nEndID*  
 要用作返回值的属性表的标识符。  
  
### <a name="remarks"></a>备注  
 按确定、 取消或关闭按钮时，由框架调用此成员函数。 调用此成员函数，如果发生了事件，应关闭属性表。  
  
 此成员函数仅用于一个模式对话框。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CPropertySheet::PressButton](#pressbutton)。  
  
##  <a name="getactiveindex"></a>  CPropertySheet::GetActiveIndex  
 获取属性表窗口的活动页的索引号，然后使用作为的参数的返回的索引号`GetPage`。  
  
```  
int GetActiveIndex() const;  
```  
  
### <a name="return-value"></a>返回值  
 活动页的索引号。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CPropertySheet::GetActivePage](#getactivepage)。  
  
##  <a name="getactivepage"></a>  CPropertySheet::GetActivePage  
 检索属性表窗口的活动页面。  
  
```  
CPropertyPage* GetActivePage() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向活动的页面的指针。  
  
### <a name="remarks"></a>备注  
 使用此成员函数以活动页面上执行某些操作。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]  
  
##  <a name="getpage"></a>  CPropertySheet::GetPage  
 返回一个指向此属性表中指定的页。  
  
```  
CPropertyPage* GetPage(int nPage) const;  
```  
  
### <a name="parameters"></a>参数  
 *n 页面*  
 索引所需的页上，从 0 开始。 必须是介于 0 和一个小于页面在属性表中，非独占数之间。  
  
### <a name="return-value"></a>返回值  
 指向对应的页指针*n 页面*参数。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish)。  
  
##  <a name="getpagecount"></a>  CPropertySheet::GetPageCount  
 确定当前在属性表中的页数。  
  
```  
int GetPageCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 属性表中的页的数目。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish)。  
  
##  <a name="getpageindex"></a>  CPropertySheet::GetPageIndex  
 检索指定属性表中的页的索引数。  
  
```  
int GetPageIndex(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>参数  
 *pPage*  
 指向包含要查找的索引的页。 不能为 NULL。  
  
### <a name="return-value"></a>返回值  
 页的索引号。  
  
### <a name="remarks"></a>备注  
 例如，将使用`GetPageIndex`若要获得若要使用的页索引[SetActivePage](#setactivepage)或[GetPage](#getpage)。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CPropertySheet::GetActivePage](#getactivepage)。  
  
##  <a name="gettabcontrol"></a>  CPropertySheet::GetTabControl  
 检索指向选项卡控件执行操作特定于选项卡控件 (即，若要使用的 Api 中的任何[CTabCtrl](../../mfc/reference/ctabctrl-class.md))。  
  
```  
CTabCtrl* GetTabControl() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向选项卡控件的指针。  
  
### <a name="remarks"></a>备注  
 例如，如果你想要将位图添加到每个选项卡，在初始化期间调用此成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]  
  
##  <a name="m_psh"></a>  CPropertySheet::m_psh  
 其成员存储的特征的结构[PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546)。  
  
### <a name="remarks"></a>备注  
 使用此结构来构造它之后，但它显示为带之前初始化属性表的外观[DoModal](#domodal)成员函数。 例如，设置*dwSize*的成员`m_psh`你想要具有的属性表的大小。  
  
 此结构，包括其成员的列表的详细信息请参阅 Windows SDK 中的 PROPSHEETHEADER。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]  
  
##  <a name="mapdialogrect"></a>  CPropertySheet::MapDialogRect  
 将一个矩形的对话框单位转换为屏幕单位。  
  
```  
void MapDialogRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 *lpRect*  
 指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，它包含对话框中要转换的坐标。  
  
### <a name="remarks"></a>备注  
 对话框单位是派生自的平均宽度和高度用于对话框文本的字体中字符的当前对话框基本单位根据所述。 一个水平单元是一个第四个对话框基本宽度单位 （） 的一个垂直的单位的八分之一对话框基本高度单元。  
  
 [GetDialogBaseUnits](http://msdn.microsoft.com/library/windows/desktop/ms645475) Windows 函数将返回系统字体的大小信息，但如果在资源定义文件中使用 DS_SETFONT 样式，则可以指定每个属性页不同的字体。 [MapDialogRect](http://msdn.microsoft.com/library/windows/desktop/ms645502) Windows 函数，在 Windows SDK 中，将会介绍此对话框为使用合适的字体。  
  
 `MapDialogRect`成员函数将替换中的对话框单元*lpRect*与屏幕单位 （像素），使该矩形可以用于创建一个对话框，或将控件放在一个框。  
  
##  <a name="oninitdialog"></a>  Cpropertysheet:: Oninitdialog  
 重写以增加属性表初始化。  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>返回值  
 指定应用程序是否已将输入的焦点设置到其中一个属性表中的控件。 如果`OnInitDialog`返回非零值，则 Windows 会将输入的焦点设置到属性表中的第一个控件。 仅当已显式输入的焦点设置到其中一个属性表中的控件，该应用程序可以返回 0。  
  
### <a name="remarks"></a>备注  
 此成员函数调用以响应 WM_INITDIALOG 消息。 此消息发送到属性表期间[创建](#create)或[DoModal](#domodal)调用，这在显示属性表之前立即发生。  
  
 如果您需要执行特殊处理初始化属性表时，重写此成员函数。 在重写的版本中，首先调用基类`OnInitDialog`但忽略其返回值。 通常情况下将重写的成员函数返回 TRUE。  
  
 此成员函数不需要消息映射条目。  
  
##  <a name="pressbutton"></a>  CPropertySheet::PressButton  
 模拟所选的属性表中指定的按钮。  
  
```  
void PressButton(int nButton);
```  
  
### <a name="parameters"></a>参数  
 *n 按钮*  
 n 按钮： 标识按钮按下。 此参数可以是下列值之一：  
  
- PSBTN_BACK 选择后退按钮。  
  
- PSBTN_NEXT 选择下一步按钮。  
  
- PSBTN_FINISH 选择完成按钮。  
  
- PSBTN_OK 选择确定按钮。  
  
- PSBTN_APPLYNOW 选择立即应用按钮。  
  
- PSBTN_CANCEL 选择取消按钮。  
  
- PSBTN_HELP 选择帮助按钮。  
  
### <a name="remarks"></a>备注  
 请参阅[PSM_PRESSBUTTON](http://msdn.microsoft.com/library/windows/desktop/bb774597)有关 Windows SDK Pressbutton 消息详细信息。  
  
 调用`PressButton`将不会发送[PSN_APPLY](http://msdn.microsoft.com/library/windows/desktop/bb774552)框架在属性页中的通知。 若要发送此通知，请调用[CPropertyPage::OnOK](../../mfc/reference/cpropertypage-class.md#onok)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]  
  
##  <a name="removepage"></a>  CPropertySheet::RemovePage  
 从属性表中删除页，并销毁关联的窗口。  
  
```  
void RemovePage(CPropertyPage* pPage);  
void RemovePage(int nPage);
```  
  
### <a name="parameters"></a>参数  
 *pPage*  
 指向页后，可以从属性表中删除。 不能为 NULL。  
  
 *n 页面*  
 要删除的页的索引。 必须是介于 0 和一个小于页面在属性表中，非独占数之间。  
  
### <a name="remarks"></a>备注  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)对象本身不会被销毁之前的所有者`CPropertySheet`窗口处于关闭状态。  
  
##  <a name="setactivepage"></a>  CPropertySheet::SetActivePage  
 更改活动页。  
  
```  
BOOL SetActivePage(int nPage);  
BOOL SetActivePage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>参数  
 *n 页面*  
 若要设置的页的索引。 它必须介于 0 和一个小于页面在属性表中，非独占数之间。  
  
 *pPage*  
 指向要设置的属性表中的页。 它不能为 NULL。  
  
### <a name="return-value"></a>返回值  
 如果成功，则激活属性表，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 例如，使用`SetActivePage`如果在一页上的用户的操作会导致另一个页面以变为活动页。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CPropertySheet::GetActivePage](#getactivepage)。  
  
##  <a name="setfinishtext"></a>  CPropertySheet::SetFinishText  
 在完成命令按钮中设置的文本。  
  
```  
void SetFinishText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
 *lpszText*  
 指向要在完成命令按钮上显示的文本。  
  
### <a name="remarks"></a>备注  
 调用`SetFinishText`完成命令按钮上显示文本并在用户完成该向导的最后一页上的操作后隐藏下一步和后退按钮。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]  
  
##  <a name="settitle"></a>  CPropertySheet::SetTitle  
 指定属性表的标题 （框架窗口的标题栏中显示的文本）。  
  
```  
void SetTitle(
    LPCTSTR lpszText,  
    UINT nStyle = 0);
```  
  
### <a name="parameters"></a>参数  
 *nStyle*  
 指定属性表标题的样式。 0 或作为 PSH_PROPTITLE，必须指定样式。 如果样式设置为 PSH_PROPTITLE，指定为标题的文本之后显示单词"属性"。 例如，调用`SetTitle`（"简单"，PSH_PROPTITLE） 将导致"简单属性。"的属性表标题  
  
 *lpszText*  
 指向要将其用于在属性表的标题栏标题的文本。  
  
### <a name="remarks"></a>备注  
 默认情况下，属性表的属性表构造函数中使用标题参数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]  
  
##  <a name="setwizardbuttons"></a>  CPropertySheet::SetWizardButtons  
 启用或禁用向导属性表中的步、 下一步或完成按钮。  
  
```  
void SetWizardButtons(DWORD dwFlags);
```  
  
### <a name="parameters"></a>参数  
 *dwFlags*  
 一组自定义的函数和向导按钮的外观的标志。 此参数可以是以下值的组合：  
  
- PSWIZB_BACK 后退按钮  
  
- PSWIZB_NEXT 下一步按钮  
  
- PSWIZB_FINISH 完成按钮  
  
- PSWIZB_DISABLEDFINISH 禁用完成按钮  
  
### <a name="remarks"></a>备注  
 调用`SetWizardButtons`仅在对话框已打开，则后不能调用`SetWizardButtons`在调用之前[DoModal](#domodal)。 通常情况下，应调用`SetWizardButtons`从[cpropertypage:: Onsetactive](../../mfc/reference/cpropertypage-class.md#onsetactive)。  
  
 如果你想要更改完成按钮上的文本或隐藏的下一步和后退按钮一次该用户已完成向导中，调用[SetFinishText](#setfinishtext)。 请注意，完成和下一步共享相同的按钮。 您可以显示完成或下一步按钮一次但不可同时使用两者。  
  
### <a name="example"></a>示例  
 一个`CPropertySheet`有三个向导属性页： `CStylePage`， `CColorPage`，和`CShapePage`。  下面的代码片段演示如何启用和禁用**回**并**下一步**向导属性页上的按钮。  
  
 [!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]  
  
##  <a name="setwizardmode"></a>  CPropertySheet::SetWizardMode  
 建立属性页，作为一个向导。  
  
```  
void SetWizardMode();
```  
  
### <a name="remarks"></a>备注  
 向导属性页的关键特征是，在用户导航接下来使用或完成、 后退、 和取消按钮而不是选项卡。  
  
 调用`SetWizardMode`之前调用[DoModal](#domodal)。 调用后`SetWizardMode`，`DoModal`将返回 ID_WIZFINISH （如果用户使用完成按钮关闭） 或 IDCANCEL。  
  
 `SetWizardMode` 设置 PSH_WIZARD 标志。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 CMNCTRL1](../../visual-cpp-samples.md)   
 [MFC 示例 CMNCTRL2](../../visual-cpp-samples.md)   
 [MFC 示例 PROPDLG](../../visual-cpp-samples.md)   
 [MFC 示例 SNAPVW](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)



