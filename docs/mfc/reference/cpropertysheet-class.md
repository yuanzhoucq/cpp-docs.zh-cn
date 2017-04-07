---
title: "CPropertySheet 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
- dialog boxes, tabs
- CPropertySheet class
- property sheets, CPropertySheet class
- tab dialog boxes
ms.assetid: 8461ccff-d14f-46e0-a746-42ad642ef94e
caps.latest.revision: 30
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
ms.openlocfilehash: 41ad7b598016b1fa04aa7ca63575f853195b5359
ms.lasthandoff: 02/24/2017

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
|[Cpropertysheet:: Enablestackedtabs](#enablestackedtabs)|指示属性表是使用堆积或滚动选项卡。|  
|[CPropertySheet::EndDialog](#enddialog)|终止属性表。|  
|[CPropertySheet::GetActiveIndex](#getactiveindex)|检索的属性表的活动页面的索引。|  
|[CPropertySheet::GetActivePage](#getactivepage)|返回活动的 page 对象。|  
|[CPropertySheet::GetPage](#getpage)|检索指向指定的页。|  
|[CPropertySheet::GetPageCount](#getpagecount)|检索的属性表中的页数。|  
|[CPropertySheet::GetPageIndex](#getpageindex)|检索指定的页的属性表的索引。|  
|[CPropertySheet::GetTabControl](#gettabcontrol)|检索指向选项卡控件。|  
|[CPropertySheet::MapDialogRect](#mapdialogrect)|将矩形的对话框单位转换为屏幕单位。|  
|[Cpropertysheet:: Oninitdialog](#oninitdialog)|重写以增加属性工作表初始化。|  
|[CPropertySheet::PressButton](#pressbutton)|模拟所选的属性表中的指定按钮。|  
|[CPropertySheet::RemovePage](#removepage)|从属性表中移除一个页面。|  
|[CPropertySheet::SetActivePage](#setactivepage)|以编程方式设置活动的 page 对象。|  
|[CPropertySheet::SetFinishText](#setfinishtext)|设置完成按钮的文本。|  
|[CPropertySheet::SetTitle](#settitle)|设置的属性表的标题。|  
|[CPropertySheet::SetWizardButtons](#setwizardbuttons)|使向导按钮。|  
|[CPropertySheet::SetWizardMode](#setwizardmode)|启用向导模式。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CPropertySheet::m_psh](#m_psh)|Windows [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546)结构。 提供对基本的属性表参数的访问。|  
  
## <a name="remarks"></a>备注  
 属性表包含`CPropertySheet`对象和一个或多个[CPropertyPage](../../mfc/reference/cpropertypage-class.md)对象。 框架显示属性表为具有一组选项卡索引和包含当前所选的页面的区域的窗口。 用户导航到特定页通过使用相应的选项卡。  
  
 `CPropertySheet`为扩展提供了支持[PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546)结构中引入[!INCLUDE[Win98](../../mfc/reference/includes/win98_md.md)]和 Windows NT 2000。 该结构包含其他标志和支持使用"水印"背景位图的成员。  
  
 在您的属性表对象中自动显示这些新映像，到调用中传递的有效值的位图和调色板映像[CPropertySheet::Construct](#construct)或[CPropertySheet::CPropertySheet](#cpropertysheet)。  
  
 即使`CPropertySheet`不源自[CDialog](../../mfc/reference/cdialog-class.md)，以及管理`CPropertySheet`对象是类似于管理`CDialog`对象。 例如，属性表的创建所需的两部分构造︰ 调用构造函数中，，然后调用[DoModal](#domodal)为模式属性表或[创建](#create)为无模式属性表。 `CPropertySheet`有两种类型的构造函数︰ [CPropertySheet::Construct](#construct)和[CPropertySheet::CPropertySheet](#cpropertysheet)。  
  
 当构造`CPropertySheet`对象时，某些[窗口样式](../../mfc/reference/window-styles.md)可能会导致发生首次异常。 这将导致从尝试更改的属性表样式，在创建工作表之前的系统。 若要避免此异常，请确保在创建时设置以下样式您`CPropertySheet`:  
  
-   DS_3DLOOK  
  
-   DS_CONTROL  
  
-   WS_CHILD  
  
-   WS_TABSTOP  
  
 下面的样式是可选的并且不会导致首次异常︰  
  
-   DS_SHELLFONT  
  
-   DS_LOCALEDIT  
  
-   WS_CLIPCHILDREN  
  
 任何其他`Window Styles`禁止，并且不应启用它们。  
  
 之间交换数据`CPropertySheet`对象和外部的对象是类似于与交换数据`CDialog`对象。 重要的区别在于属性表的设置通常是成员变量的`CPropertyPage`对象而不是`CPropertySheet`对象本身。  
  
 您可以创建一种称为向导，其中包含的属性表具有一系列指导用户完成操作，例如设置设备，或创建时事通讯的步骤的属性页选项卡对话框。 在向导类型选项卡对话框中，属性页没有选项卡上，并且一次只有一个属性页上可见。 此外，而不是**确定**和**立即应用**按钮、 向导类型选项卡对话框有**回**按钮，**下一步**或**完成**按钮，**取消**按钮，和一个**帮助**按钮。  
  
 若要创建向导类型的对话框，请按照您创建的标准属性表中，但调用时要遵循的相同步骤[SetWizardMode](#setwizardmode)之前调用[DoModal](#domodal)。 若要启用的向导按钮，调用[SetWizardButtons](#setwizardbuttons)，使用标志自定义它们的功能和外观。 若要启用**完成**按钮，请调用[SetFinishText](#setfinishtext)用户已在该向导的最后一页上执行操作之后。  
  
 有关如何使用`CPropertySheet`对象，请参阅文章[属性表和属性页](../../mfc/property-sheets-and-property-pages-in-mfc.md)。 此外，请参阅知识库文章 Q146916︰ 如何︰ 使用标准按钮创建无模式 CPropertySheet 和文章 Q300606︰ 如何︰ 设计可调整大小的 MFC 属性表。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPropertySheet`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdlgs.h  
  
##  <a name="addpage"></a>Cpropertysheet:: Addpage  
 在属性表中添加与最右侧的选项卡提供页。  
  
```  
void AddPage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>参数  
 `pPage`  
 指向以页后，可以添加到属性表。 不能为**NULL**。  
  
### <a name="remarks"></a>备注  
 将页添加到的属性表中您希望它们出现的从左到右顺序。  
  
 `AddPage`添加[CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)对象传递给`CPropertySheet`对象的页的列表，但不会实际创建页窗口。 框架将推迟页上的窗口的创建，直到用户选择该页面。  
  
 当您将添加属性页使用`AddPage`、`CPropertySheet`是父级的`CPropertyPage`。 若要从属性页上获取到属性表的访问权限，调用[CWnd::GetParent](../../mfc/reference/cwnd-class.md#getparent)。  
  
 不需要等到创建属性表窗口后再调用`AddPage`。 通常，将调用`AddPage`之前调用[DoModal](#domodal)或[创建](#create)。  
  
 如果调用`AddPage`后显示属性页上，选项卡行将反映新添加的页。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&129;](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]  
  
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
 若要使用的属性表标题的 ID。  
  
 `pParentWnd`  
 属性表的父窗口的指针。 如果**NULL**，父窗口将在应用程序的主窗口。  
  
 `iSelectPage`  
 最初将成为在最前面的页的索引。 默认值为添加到表中的第一页。  
  
 `pszCaption`  
 包含要使用的属性表的标题的字符串的指针。 不能为**NULL**。  
  
 `hbmWatermark`  
 属性页上的水印位图的句柄。  
  
 `hpalWatermark`  
 水印位图和/或标头位图的调色板的句柄。  
  
 `hbmHeader`  
 属性页上的标头位图的句柄。  
  
### <a name="remarks"></a>备注  
 如果类构造函数之一不已被调用，则调用此成员函数。 例如，调用`Construct`您声明或分配的数组`CPropertySheet`对象。 对于数组，则必须调用`Construct`对于数组中每个成员。  
  
 若要显示属性表，请调用[DoModal](#domodal)或[创建](#create)。 将在属性表的标题栏中放置在第一个参数中包含的字符串。  
  
 如果您使用的第三个或第四个原型，您可以自动显示水印和/或标头的图像`Construct`、 以上所列并将有效的值传递`hbmWatermark`， `hpalWatermark`，和/或`hbmHeader`参数。  
  
### <a name="example"></a>示例  
 下面的示例演示在什么情况下，您就可以调用`Construct`。  
  
 [!code-cpp[NVC_MFCDocView #&130;](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]  
  
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
 若要使用的属性表标题的 ID。  
  
 `pParentWnd`  
 指向父窗口的属性表。 如果**NULL**，父窗口将在应用程序的主窗口。  
  
 `iSelectPage`  
 最初将成为在最前面的页的索引。 默认值为添加到表中的第一页。  
  
 `pszCaption`  
 指向包含要使用的属性表的标题的字符串。 不能为**NULL**。  
  
 `hbmWatermark`  
 属性表的背景位图句柄。  
  
 `hpalWatermark`  
 指向水印位图和/或标头位图的调色板的句柄。  
  
 `hbmHeader`  
 属性页上的标头位图句柄。  
  
### <a name="remarks"></a>备注  
 若要显示属性表，请调用[DoModal](#domodal)或[创建](#create)。 将在属性表的标题栏中放置在第一个参数中包含的字符串。  
  
 如果您具有多个参数 （例如，如果您使用的一个数组），使用[构造](#construct)而不是`CPropertySheet`。  
  
 如果您使用的第三个或第四个原型，您可以自动显示水印和/或标头的图像`CPropertySheet`、 更高版本，并将有效的值传递`hbmWatermark`， `hpalWatermark`，和/或`hbmHeader`参数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&131;](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]  
  
##  <a name="create"></a>CPropertySheet::Create  
 显示无模式属性表。  
  
```  
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)–1,
    DWORD dwExStyle = 0);  
```  
  
### <a name="parameters"></a>参数  
 `pParentWnd`  
 指向父窗口。 如果**NULL**，父级是桌面。  
  
 `dwStyle`  
 属性表的窗口样式。 有关可用样式的完整列表，请参阅[窗口样式](../../mfc/reference/window-styles.md)。  
  
 `dwExStyle`  
 属性表的扩展的窗口样式。 有关可用样式的完整列表，请参阅[扩展窗口样式](../../mfc/reference/extended-window-styles.md)  
  
### <a name="return-value"></a>返回值  
 非零，如果成功，则创建属性表否则为 0。  
  
### <a name="remarks"></a>备注  
 对调用**创建**可以是在构造函数，或对其进行调用后调用的构造函数。  
  
 默认样式，通过传递为 –&1; 表示`dwStyle`，实际上是**WS_SYSMENU |**`WS_POPUP`**|WS_CAPTION |DS_MODALFRAME |DS_CONTEXTHELP |WS_VISIBLE**。 默认值扩展窗口样式，通过传递 0 作为表示`dwExStyle`，实际上是**WS_EX_DLGMODALFRAME**。  
  
 **创建**成员函数将在创建属性表后立即返回。 若要销毁的属性表，请调用[cwnd:: Destroywindow](../../mfc/reference/cwnd-class.md#destroywindow)。  
  
 无模式属性表显示通过调用**创建**模式属性表一样不具有确定、 取消，立即应用和帮助按钮。 必须由用户创建所需的按钮。  
  
 若要显示模式属性表，请调用[DoModal](#domodal)相反。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&132;](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&133;](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]  
  
##  <a name="domodal"></a>Cpropertysheet:: Domodal  
 显示模式属性表。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>返回值  
 `IDOK`或`IDCANCEL`函数是否成功; 否则为 0 或-1。 如果已建立属性表作为向导 (请参阅[SetWizardMode](#setwizardmode))，`DoModal`返回`ID_WIZFINISH`或`IDCANCEL`。  
  
### <a name="remarks"></a>备注  
 返回值对应于关闭属性表控件的 ID。 此函数返回后，将销毁 windows 分别对应于属性表和所有的页面。 为对象本身仍将存在。 通常情况下，您将从中检索数据[CPropertyPage](../../mfc/reference/cpropertypage-class.md)对象后`DoModal`返回`IDOK`。  
  
 若要显示无模式属性表，请调用[创建](#create)相反。  
  
 属性页创建时从其相应的对话框资源，则可能导致首次异常。 这将导致从对话框资源的样式更改为所需的样式之前创建页面, 的属性页。 因为资源通常是只读的所以这会导致引发异常。 系统处理异常，并创建已修改的资源的副本。 首次异常因此被忽略。  
  
> [!NOTE]
>  如果使用的异步异常处理模型进行编译，操作系统必须处理此异常。 有关异常处理模型的详细信息，请参阅[/EH （异常处理模型）](../../build/reference/eh-exception-handling-model.md)。 在这种情况下，不换行对的调用`CPropertySheet::DoModal`与 c + + 的 try-catch 块顺序在 catch 处理所有异常，例如， `catch (...)`。 此块将处理针对的操作系统，以及导致不可预知的行为异常。 但是，您可以安全地使用 c + + 异常处理与特定的异常类型或结构化的异常处理的访问冲突异常通过传递给操作系统。  
  
 为了避免生成此第一机会异常，则可以手动保证属性表具有正确[窗口样式](../../mfc/reference/window-styles.md)。 您需要设置属性表的以下样式︰  
  
-   DS_3DLOOK  
  
-   DS_CONTROL  
  
-   WS_CHILD  
  
-   WS_TABSTOP  
  
 您可以使用以下可选样式，而不会导致首次异常︰  
  
-   DS_SHELLFONT  
  
-   DS_LOCALEDIT  
  
-   WS_CLIPCHILDREN  
  
 禁用所有其他 Windows 样式，因为它们不是与属性表兼容。 此建议不适用于扩展样式。 适当地设置这些标准样式可以保证在属性表不需要进行修改，和将避免生成首次异常。  
  
### <a name="example"></a>示例  
  请参阅示例[cpropertysheet:: Addpage](#addpage)。  
  
##  <a name="enablestackedtabs"></a>Cpropertysheet:: Enablestackedtabs  
 指示是否堆栈中的属性表选项卡的行。  
  
```  
void EnableStackedTabs(BOOL bStacked);
```  
  
### <a name="parameters"></a>参数  
 `bStacked`  
 指示是否在属性表中启用堆积选项卡。 通过设置来禁用堆积的行标记`bStacked`到**FALSE**。  
  
### <a name="remarks"></a>备注  
 默认情况下，如果属性表具有更多选项卡的属性表中，在宽度单个行中放不下选项卡会堆叠在多个行中。 若要使用滚动选项卡而不是堆栈的选项卡，调用`EnableStackedTabs`与`bStacked`设置为**FALSE**之前调用[DoModal](#domodal)或[创建](#create)。  
  
 必须调用`EnableStackedTabs`当您创建在安装结束时或无模式属性表。 若要将合并在这种样式`CPropertySheet`-派生类中，编写消息处理程序为`WM_CREATE`。 中的重写版本[CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)，调用**EnableStackedTabs (FALSE)**之前调用基类实现。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&134;](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]  
  
##  <a name="enddialog"></a>CPropertySheet::EndDialog  
 终止属性表。  
  
```  
void EndDialog(int nEndID);
```  
  
### <a name="parameters"></a>参数  
 *nEndID*  
 要用作返回值的属性表的标识符。  
  
### <a name="remarks"></a>备注  
 按确定、 取消或关闭按钮时，将由框架调用此成员函数。 调用此成员函数，如果发生事件时，应关闭属性表。  
  
 此成员函数只能与一个模式对话框使用。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertySheet::PressButton](#pressbutton)。  
  
##  <a name="getactiveindex"></a>CPropertySheet::GetActiveIndex  
 获取属性表窗口的活动页的索引号，然后使用作为的参数的返回的索引号`GetPage`。  
  
```  
int GetActiveIndex() const;  
```  
  
### <a name="return-value"></a>返回值  
 活动页的索引号。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertySheet::GetActivePage](#getactivepage)。  
  
##  <a name="getactivepage"></a>CPropertySheet::GetActivePage  
 检索属性表窗口的活动页面。  
  
```  
CPropertyPage* GetActivePage() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向活动页的指针。  
  
### <a name="remarks"></a>备注  
 使用此成员函数以在活动页中执行某些操作。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&135;](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]  
  
##  <a name="getpage"></a>CPropertySheet::GetPage  
 为此属性表中指定的页中返回的指针。  
  
```  
CPropertyPage* GetPage(int nPage) const;  
```  
  
### <a name="parameters"></a>参数  
 `nPage`  
 索引所需的页上，从 0 开始。 必须是介于 0 和一个小于总页数在属性表 （含） 之间。  
  
### <a name="return-value"></a>返回值  
 将指针与对应的页面`nPage`参数。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish)。  
  
##  <a name="getpagecount"></a>CPropertySheet::GetPageCount  
 确定当前在属性表中的页数。  
  
```  
int GetPageCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 在属性表中的页的数目。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish)。  
  
##  <a name="getpageindex"></a>CPropertySheet::GetPageIndex  
 检索的属性表中指定的页的编号。  
  
```  
int GetPageIndex(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>参数  
 `pPage`  
 指向包含要查找的索引的页面。 不能为**NULL**。  
  
### <a name="return-value"></a>返回值  
 页的索引号。  
  
### <a name="remarks"></a>备注  
 例如，您将使用`GetPageIndex`来获取页索引，以便使用[SetActivePage](#setactivepage)或[GetPage](#getpage)。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertySheet::GetActivePage](#getactivepage)。  
  
##  <a name="gettabcontrol"></a>CPropertySheet::GetTabControl  
 检索指向选项卡控件来执行某些特定选项卡控件的指针 (也就是说，若要使用的任何 Api 中[CTabCtrl](../../mfc/reference/ctabctrl-class.md))。  
  
```  
CTabCtrl* GetTabControl() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向选项卡控件的指针。  
  
### <a name="remarks"></a>备注  
 例如，如果您想要将位图添加到每个选项卡，在初始化期间调用该成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&136;](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]  
  
##  <a name="m_psh"></a>CPropertySheet::m_psh  
 其成员存储的特征的结构[PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546)。  
  
### <a name="remarks"></a>备注  
 使用此结构可以构造它之后，但它显示为带之前初始化属性表的外观[DoModal](#domodal)成员函数。 例如，设置`dwSize`的成员`m_psh`想要具有的属性表的大小。  
  
 此结构，包括其成员的列表的详细信息请参阅**PROPSHEETHEADER**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&143;](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]  
  
##  <a name="mapdialogrect"></a>CPropertySheet::MapDialogRect  
 将矩形的对话框单位转换为屏幕单位。  
  
```  
void MapDialogRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，它包含对话框中要转换的坐标。  
  
### <a name="remarks"></a>备注  
 在派生自的平均宽度和高度用于对话框中的文本的字体中字符的当前对话框基本单位方面阐述对话框单位。 一个水平度量对话框基本宽度单位 （） 的四分之一，一个垂直的单位是对话框底高单位的&1; /&8;。  
  
 [GetDialogBaseUnits](http://msdn.microsoft.com/library/windows/desktop/ms645475) Windows 函数返回系统字体的大小信息，但您可以指定每个属性页不同的字体，如果您使用**DS_SETFONT**资源定义文件中的样式。 [MapDialogRect](http://msdn.microsoft.com/library/windows/desktop/ms645502)中所述的 Windows 函数[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]，对于此对话框使用合适的字体。  
  
 `MapDialogRect`成员函数将替换为对话框单位`lpRect`与屏幕单位 （像素），以便可以使用矩形来创建一个对话框，或将控件放在一个框中。  
  
##  <a name="oninitdialog"></a>Cpropertysheet:: Oninitdialog  
 重写来扩充属性工作表初始化。  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>返回值  
 指定应用程序是否已将输入的焦点设置到其中一个属性表中的控件。 如果**OnInitDialog**返回非零，则 Windows 会将输入的焦点设置到属性表中的第一个控件。 只有当它已显式设置为其中一个属性表中的控件的输入的焦点，则该应用程序可以返回 0。  
  
### <a name="remarks"></a>备注  
 此成员函数调用以响应**WM_INITDIALOG**消息。 此消息发送到的属性表期间[创建](#create)或[DoModal](#domodal)调用，在显示属性表之前立即发生这种情况。  
  
 如果您需要执行特殊处理，在初始化属性表时，重写该成员函数。 在重写版本中，首先调用基类`OnInitDialog`但忽略其返回值。 正常情况下将返回**TRUE**从重写的成员函数。  
  
 此成员函数不需要的消息映射条目。  
  
##  <a name="pressbutton"></a>CPropertySheet::PressButton  
 模拟所选的属性表中的指定按钮。  
  
```  
void PressButton(int nButton);
```  
  
### <a name="parameters"></a>参数  
 `nButton`  
 nButton︰ 标识要按下此按钮。 此参数可以是下列值之一︰  
  
- **PSBTN_BACK**选择后退按钮。  
  
- **PSBTN_NEXT**选择下一步按钮。  
  
- **PSBTN_FINISH**选择完成按钮。  
  
- **PSBTN_OK**选择确定按钮。  
  
- **PSBTN_APPLYNOW**选择立即应用按钮。  
  
- **PSBTN_CANCEL**选择取消按钮。  
  
- **PSBTN_HELP**选择帮助按钮。  
  
### <a name="remarks"></a>备注  
 请参阅[PSM_PRESSBUTTON](http://msdn.microsoft.com/library/windows/desktop/bb774597)有关 Windows SDK Pressbutton 消息的详细信息。  
  
 调用`PressButton`将不会发送[PSN_APPLY](http://msdn.microsoft.com/library/windows/desktop/bb774552)向框架通知在属性页中。 若要发送此通知，请调用[CPropertyPage::OnOK](../../mfc/reference/cpropertypage-class.md#onok)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&137;](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]  
  
##  <a name="removepage"></a>CPropertySheet::RemovePage  
 从属性表中移除一个页面，并销毁关联的窗口。  
  
```  
void RemovePage(CPropertyPage* pPage);  
void RemovePage(int nPage);
```  
  
### <a name="parameters"></a>参数  
 `pPage`  
 指向以页后，可以从属性表中删除。 不能为`NULL`。  
  
 `nPage`  
 要删除的页的索引。 必须是介于 0 和一个小于总页数在属性表 （含） 之间。  
  
### <a name="remarks"></a>备注  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)对象本身不会被破坏之前的所有者`CPropertySheet`窗口处于关闭状态。  
  
##  <a name="setactivepage"></a>CPropertySheet::SetActivePage  
 更改的活动页面。  
  
```  
BOOL SetActivePage(int nPage);  
BOOL SetActivePage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>参数  
 `nPage`  
 若要设置的页的索引。 它必须是介于 0 和一个小于总页数在属性表 （含） 之间。  
  
 `pPage`  
 指向要设置的属性表中的页。 它不能是**NULL**。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功，则激活属性表否则为 0。  
  
### <a name="remarks"></a>备注  
 例如，使用`SetActivePage`如果在一页上的用户的操作应该会导致另一个页面以成为活动的页。  
  
### <a name="example"></a>示例  
  请参阅示例[CPropertySheet::GetActivePage](#getactivepage)。  
  
##  <a name="setfinishtext"></a>CPropertySheet::SetFinishText  
 设置在完成命令按钮的文本。  
  
```  
void SetFinishText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
 `lpszText`  
 指向要在完成命令按钮上显示的文本。  
  
### <a name="remarks"></a>备注  
 调用`SetFinishText`若要在完成命令按钮上显示文本并在用户完成该向导的最后一页上的操作后隐藏下一步和后退按钮。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&138;](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]  
  
##  <a name="settitle"></a>CPropertySheet::SetTitle  
 指定属性表的标题 （框架窗口的标题栏中显示的文本）。  
  
```  
void SetTitle(
    LPCTSTR lpszText,  
    UINT nStyle = 0);
```  
  
### <a name="parameters"></a>参数  
 `nStyle`  
 指定的属性表标题的样式。 必须指定的样式，0 或作为**PSH_PROPTITLE**。 如果该样式设置为**PSH_PROPTITLE**，指定为标题的文本之后将显示"属性"一词。 例如，调用`SetTitle`("简单" **PSH_PROPTITLE**)，则会在属性表标题中的"简单属性。  
  
 `lpszText`  
 指向要将其用于标题的属性表的标题栏中的文本。  
  
### <a name="remarks"></a>备注  
 默认情况下，属性表的属性表构造函数中使用标题参数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&139;](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]  
  
##  <a name="setwizardbuttons"></a>CPropertySheet::SetWizardButtons  
 启用或禁用向导属性表中的后退、 下一步，或完成按钮。  
  
```  
void SetWizardButtons(DWORD dwFlags);
```  
  
### <a name="parameters"></a>参数  
 `dwFlags`  
 一组自定义的函数和向导按钮的外观的标志。 此参数可以是以下值的组合︰  
  
- **PSWIZB_BACK**后退按钮  
  
- **PSWIZB_NEXT**下一步按钮  
  
- **PSWIZB_FINISH**完成按钮  
  
- **PSWIZB_DISABLEDFINISH**已禁用完成按钮  
  
### <a name="remarks"></a>备注  
 调用`SetWizardButtons`对话框已打开，则仅后不能调用`SetWizardButtons`之前调用[DoModal](#domodal)。 通常情况下，应调用`SetWizardButtons`从[cpropertypage:: Onsetactive](../../mfc/reference/cpropertypage-class.md#onsetactive)。  
  
 如果您想要更改完成按钮上的文本或隐藏下一步和后退按钮一次该用户已完成向导中，调用[SetFinishText](#setfinishtext)。 请注意，完成和下一步为共享相同的按钮。 您可以显示完成或下一步按钮一次但不要同时使用两者。  
  
### <a name="example"></a>示例  
 一个`CPropertySheet`有三个向导属性页︰ `CStylePage`， `CColorPage`，和`CShapePage`。  下面的代码段演示如何启用和禁用**回**和**下一步**向导属性页上的按钮。  
  
 [!code-cpp[NVC_MFCDocView #&140;](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&141;](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&138;](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]  
  
##  <a name="setwizardmode"></a>CPropertySheet::SetWizardMode  
 用作向导建立的属性页。  
  
```  
void SetWizardMode();
```  
  
### <a name="remarks"></a>备注  
 向导属性页的关键特征是，在用户导航接下来使用或完成、 后退、 和取消按钮而不是选项卡。  
  
 调用`SetWizardMode`之前调用[DoModal](#domodal)。 在您调用之后`SetWizardMode`，`DoModal`将返回**ID_WIZFINISH** （如果用户关闭使用完成按钮） 或**IDCANCEL**。  
  
 `SetWizardMode`设置 PSH_WIZARD 标志。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&142;](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 CMNCTRL1](../../visual-cpp-samples.md)   
 [MFC 示例 CMNCTRL2](../../visual-cpp-samples.md)   
 [MFC 示例 PROPDLG](../../visual-cpp-samples.md)   
 [MFC 示例 SNAPVW](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)




