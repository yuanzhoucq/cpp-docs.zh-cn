---
title: CToolBar 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CToolBar
- AFXEXT/CToolBar
- AFXEXT/CToolBar::CToolBar
- AFXEXT/CToolBar::CommandToIndex
- AFXEXT/CToolBar::Create
- AFXEXT/CToolBar::CreateEx
- AFXEXT/CToolBar::GetButtonInfo
- AFXEXT/CToolBar::GetButtonStyle
- AFXEXT/CToolBar::GetButtonText
- AFXEXT/CToolBar::GetItemID
- AFXEXT/CToolBar::GetItemRect
- AFXEXT/CToolBar::GetToolBarCtrl
- AFXEXT/CToolBar::LoadBitmap
- AFXEXT/CToolBar::LoadToolBar
- AFXEXT/CToolBar::SetBitmap
- AFXEXT/CToolBar::SetButtonInfo
- AFXEXT/CToolBar::SetButtons
- AFXEXT/CToolBar::SetButtonStyle
- AFXEXT/CToolBar::SetButtonText
- AFXEXT/CToolBar::SetHeight
- AFXEXT/CToolBar::SetSizes
dev_langs:
- C++
helpviewer_keywords:
- CToolBar [MFC], CToolBar
- CToolBar [MFC], CommandToIndex
- CToolBar [MFC], Create
- CToolBar [MFC], CreateEx
- CToolBar [MFC], GetButtonInfo
- CToolBar [MFC], GetButtonStyle
- CToolBar [MFC], GetButtonText
- CToolBar [MFC], GetItemID
- CToolBar [MFC], GetItemRect
- CToolBar [MFC], GetToolBarCtrl
- CToolBar [MFC], LoadBitmap
- CToolBar [MFC], LoadToolBar
- CToolBar [MFC], SetBitmap
- CToolBar [MFC], SetButtonInfo
- CToolBar [MFC], SetButtons
- CToolBar [MFC], SetButtonStyle
- CToolBar [MFC], SetButtonText
- CToolBar [MFC], SetHeight
- CToolBar [MFC], SetSizes
ms.assetid: e868da26-5e07-4607-9651-e2f863ad9059
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2a80ea4cb188d879b9af0a7901ffbe89b8673df6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="ctoolbar-class"></a>CToolBar 类
具有一行位图化按钮和可选分隔符的控件条。  
  
## <a name="syntax"></a>语法  
  
```  
class CToolBar : public CControlBar  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CToolBar::CToolBar](#ctoolbar)|构造 `CToolBar` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CToolBar::CommandToIndex](#commandtoindex)|返回一个具有给定的命令 id。 按钮的索引|  
|[CToolBar::Create](#create)|创建 Windows 工具栏并将其附加到`CToolBar`对象。|  
|[CToolBar::CreateEx](#createex)|创建`CToolBar`有其他样式的嵌入对象`CToolBarCtrl`对象。|  
|[CToolBar::GetButtonInfo](#getbuttoninfo)|检索 ID、 样式和一个按钮的图像数。|  
|[CToolBar::GetButtonStyle](#getbuttonstyle)|检索一个按钮的样式。|  
|[CToolBar::GetButtonText](#getbuttontext)|检索将显示在按钮的文本。|  
|[CToolBar::GetItemID](#getitemid)|返回的命令 ID 的按钮或给定索引处的分隔符。|  
|[CToolBar::GetItemRect](#getitemrect)|检索给定索引处的项的显示矩形。|  
|[CToolBar::GetToolBarCtrl](#gettoolbarctrl)|允许直接访问基础的公共控件。|  
|[CToolBar::LoadBitmap](#loadbitmap)|加载包含位图按钮图像的位图。|  
|[CToolBar::LoadToolBar](#loadtoolbar)|加载使用资源编辑器创建工具栏资源。|  
|[CToolBar::SetBitmap](#setbitmap)|设置一个位图图像。|  
|[CToolBar::SetButtonInfo](#setbuttoninfo)|设置 ID、 样式和一个按钮的图像数。|  
|[CToolBar::SetButtons](#setbuttons)|设置按钮样式和的按钮图像位图中的索引。|  
|[CToolBar::SetButtonStyle](#setbuttonstyle)|设置按钮样式。|  
|[CToolBar::SetButtonText](#setbuttontext)|设置在按钮上将显示的文本。|  
|[CToolBar::SetHeight](#setheight)|设置工具栏的高度。|  
|[CToolBar::SetSizes](#setsizes)|设置按钮和其位图的大小。|  
  
## <a name="remarks"></a>备注  
 按钮可以像普通按钮、 复选框按钮、 或单选按钮。 `CToolBar` 对象是从类派生的框架窗口对象的通常嵌入的成员[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)。  
  
 [CToolBar::GetToolBarCtrl](#gettoolbarctrl)，成员函数新到 MFC 4.0，使您可以充分利用自定义工具栏和其他功能的 Windows 公共控件的支持。 `CToolBar` 成员函数为您提供的大多数 Windows 公共控件; 功能但是，当调用`GetToolBarCtrl`，你可让您的工具栏甚至多个 Windows 95/98 工具栏的特征。 当调用`GetToolBarCtrl`，它将返回到引用`CToolBarCtrl`对象。 请参阅[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)有关设计使用 Windows 公共控件的工具栏的详细信息。 公共控件有关的更多常规信息，请参阅[公共控件](http://msdn.microsoft.com/library/windows/desktop/bb775493)Windows SDK 中。  
  
 Visual c + + 为你提供了两种方法，以创建工具栏。 若要创建工具栏资源使用资源编辑器，请按照下列步骤：  
  
1.  创建工具栏资源。  
  
2.  构造 `CToolBar` 对象。  
  
3.  调用[创建](#create)(或[CreateEx](#createex)) 函数来创建 Windows 工具栏和将其附加到`CToolBar`对象。  
  
4.  调用[LoadToolBar](#loadtoolbar)加载工具栏资源。  
  
 否则，请按照下列步骤：  
  
1.  构造 `CToolBar` 对象。  
  
2.  调用[创建](#create)(或[CreateEx](#createex)) 函数来创建 Windows 工具栏和将其附加到`CToolBar`对象。  
  
3.  调用[LoadBitmap](#loadbitmap)加载用于包含工具栏按钮图像的位图。  
  
4.  调用[SetButtons](#setbuttons)用于设置按钮样式并在位图中图像关联的每个按钮。  
  
 在工具栏中的所有按钮图像，都将从一个位图，这必须包含每个按钮的一个映像。 所有映像必须都是相同的大小;默认值为 16 像素宽和 15 像素高。 映像必须在位图中的并排放置。  
  
 `SetButtons`函数将指针传递到的控件 Id 和一个整数，数组中指定的元素数的数组。 该函数将每个按钮 ID 设置为该数组的相应元素的值，并将每个按钮分配图像索引，它指定在位图中的按钮的图像的位置。 如果数组元素具有值**ID_SEPARATOR**，不分配任何映像索引。  
  
 在位图中图像的顺序通常是在其中绘制它们在屏幕上，但你可以使用的顺序[SetButtonInfo](#setbuttoninfo)函数来更改图像顺序和绘制顺序之间的关系。  
  
 在工具栏中的所有按钮都都相同的大小。 默认值为 24 x 22 像素，根据*软件设计的 Windows 界面指南*。 图像和按钮尺寸之间的任何额外的空间用于构成该图像的周围边框。  
  
 每个按钮有一个映像。 各种按钮状态，然后从该一个映像生成样式 （按下，列表中，已禁用、 关闭、 禁用和中间状态）。 尽管位图可能是任意颜色，可以获得最佳结果的黑色和阴影的灰色图像。  
  
> [!WARNING]
> `CToolBar` 支持最多为 16 种颜色的位图。 当在工具栏编辑器中加载图像时，Visual Studio 将自动将图像转换为 16 颜色位图，如有必要，并显示一条警告消息，如果映像已转换。 如果具有多个 16 种颜色 （使用外部编辑器编辑图像） 使用的映像，应用程序可能出现意外行为。  
  
 默认情况下，工具栏按钮模仿按键。 但是，复选框按钮或单选按钮，还可以模拟工具栏按钮。 复选框按钮有三种状态： 已选中、 已清除，和中间状态。 单选按钮具有只有两种状态： 选中和清除。  
  
 若要设置的单个按钮或分隔符样式不指向数组的情况下，调用[GetButtonStyle](#getbuttonstyle)以检索该样式，然后调用[SetButtonStyle](#setbuttonstyle)而不是`SetButtons`。 `SetButtonStyle` 当你想要在运行时更改按钮的样式，则将最为有用。  
  
 若要将分配要在按钮上显示的文本，调用[GetButtonText](#getbuttontext)以检索要显示在的按钮，然后调用的文本[SetButtonText](#setbuttontext)以设置的文本。  
  
 若要创建复选框按钮，将其分配样式**TBBS_CHECKBOX**或使用`CCmdUI`对象的`SetCheck`成员函数在`ON_UPDATE_COMMAND_UI`处理程序。 调用`SetCheck`变为复选框按钮的按钮。 传递`SetCheck`参数为 0 的未选中，1 选中，或 2 的不确定。  
  
 若要创建的单选按钮，调用[CCmdUI](../../mfc/reference/ccmdui-class.md)对象的[SetRadio](../../mfc/reference/ccmdui-class.md#setradio)从成员函数`ON_UPDATE_COMMAND_UI`处理程序。 传递`SetRadio`取消选中或签入的非零的自变量为 0。 若要提供单选按钮组的互斥行为，您必须`ON_UPDATE_COMMAND_UI`针对所有组中的按钮处理程序。  
  
 有关详细信息使用`CToolBar`，请参阅文章[MFC 工具栏实现](../../mfc/mfc-toolbar-implementation.md)和[技术说明 31： 控件条](../../mfc/tn031-control-bars.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CToolBar`  
  
## <a name="requirements"></a>要求  
 **标头：** afxext.h  
  
##  <a name="commandtoindex"></a>  CToolBar::CommandToIndex  
 此成员函数返回的第一个工具栏按钮，开始位置 0，其命令 ID 匹配的索引`nIDFind`。  
  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIDFind`  
 工具栏按钮的命令 ID。  
  
### <a name="return-value"></a>返回值  
 索引的按钮，则为-1 如果按钮没有给定的命令 id。  
  
##  <a name="create"></a>  CToolBar::Create  
 此成员函数将创建一个 Windows 工具栏 （子窗口），并将其与关联`CToolBar`对象。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,  
    UINT nID = AFX_IDW_TOOLBAR);
```  
  
### <a name="parameters"></a>参数  
 `pParentWnd`  
 指向将工具栏的父窗口的指针。  
  
 `dwStyle`  
 工具栏样式中。 支持的其他工具栏样式包括：  
  
- `CBRS_TOP` 控件条是在框架窗口的顶部。  
  
- `CBRS_BOTTOM` 控件条是在框架窗口的底部。  
  
- `CBRS_NOALIGN` 父级调整大小时，将不会重新定位控件条。  
  
- `CBRS_TOOLTIPS` 控件栏会显示工具提示。  
  
- **CBRS_SIZE_DYNAMIC**控件条是动态的。  
  
- **CBRS_SIZE_FIXED**固定的控件条。  
  
- **CBRS_FLOATING**浮点控件条。  
  
- `CBRS_FLYBY` 状态栏会显示有关该按钮的信息。  
  
- **CBRS_HIDE_INPLACE**控件条不向用户显示。  
  
 `nID`  
 工具栏的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 它还将工具栏高度设置为默认值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]  
  
##  <a name="createex"></a>  CToolBar::CreateEx  
 调用此函数可创建一个 Windows 工具栏 （子窗口），并将其与关联`CToolBar`对象。  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = TBSTYLE_FLAT,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_ALIGN_TOP,  
    CRect rcBorders = CRect(
    0, 
    0, 
    0, 
    0), 
    UINT nID = AFX_IDW_TOOLBAR);
```  
  
### <a name="parameters"></a>参数  
 `pParentWnd`  
 指向将工具栏的父窗口的指针。  
  
 `dwCtrlStyle`  
 为创建的嵌入其他样式[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)对象。 默认情况下，此值设置为**TBSTYLE_FLAT**。 工具栏样式的完整列表，请参阅`dwStyle`。  
  
 `dwStyle`  
 工具栏样式中。 请参阅[工具栏控件和按钮样式](http://msdn.microsoft.com/library/windows/desktop/bb760439)Windows SDK for 相应样式的列表中。  
  
 *rcBorders*  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md)对象，用于定义工具栏窗口边框的宽度。 这些边框设置为 0,0,0,0 默认情况下，从而导致在工具栏窗口中并无边框。  
  
 `nID`  
 工具栏的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 它还将工具栏高度设置为默认值。  
  
 使用`CreateEx`，而不是[创建](#create)，当需要在嵌入式的工具栏控件的创建过程的某些样式。 例如，设置`dwCtrlStyle`到**TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT**创建类似于 Internet 资源管理器 4 工具栏的工具栏。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]  
  
##  <a name="ctoolbar"></a>  CToolBar::CToolBar  
 此成员函数构造`CToolBar`对象和设置的默认大小。  
  
```  
CToolBar();
```  
  
### <a name="remarks"></a>备注  
 调用[创建](#create)成员函数来创建工具栏窗口。  
  
##  <a name="getbuttoninfo"></a>  CToolBar::GetButtonInfo  
 此成员函数将检索控件 ID、 样式和工具栏按钮或通过指定的位置处的分隔符图像索引*nIndex。*  
  
```  
void GetButtonInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& iImage) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 工具栏按钮或获取其信息是要检索的分隔符的索引。  
  
 `nID`  
 引用**UINT**是否设置为按钮的命令 ID。  
  
 `nStyle`  
 引用**UINT**是否设置为按钮的样式。  
  
 `iImage`  
 对一个整数，它设置为位图中的按钮的图像的索引引用。  
  
### <a name="remarks"></a>备注  
 这些值将赋给引用的变量`nID`， `nStyle`，和`iImage`。 映像索引是包含的所有工具栏按钮的图像位图中图像的位置。 第一个图像位于位置 0。  
  
 如果`nIndex`指定一个分隔符，`iImage`设为以像素为单位的分隔符宽度。  
  
##  <a name="getbuttonstyle"></a>  CToolBar::GetButtonStyle  
 调用此成员函数可检索的按钮或在工具栏上的分隔符的样式。  
  
```  
UINT GetButtonStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要检索的工具栏按钮或分隔符样式的索引。  
  
### <a name="return-value"></a>返回值  
 按钮或由指定的分隔符的样式`nIndex`。  
  
### <a name="remarks"></a>备注  
 按钮样式确定如何该按钮显示和对用户输入的响应方式。 请参阅[SetButtonStyle](#setbuttonstyle)有关按钮样式的示例。  
  
##  <a name="getbuttontext"></a>  CToolBar::GetButtonText  
 调用此成员函数以检索在按钮显示的文本。  
  
```  
CString GetButtonText(int nIndex) const;  
  
void GetButtonText(
    int nIndex,  
    CString& rString) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要检索的文本索引。  
  
 `rString`  
 对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)将包含要检索的文本的对象。  
  
### <a name="return-value"></a>返回值  
 A`CString`对象，其中包含按钮文本。  
  
### <a name="remarks"></a>备注  
 此成员的第二种形式函数填充`CString`具有字符串文本对象。  
  
##  <a name="getitemid"></a>  CToolBar::GetItemID  
 此成员函数返回的命令 ID 的按钮或由指定的分隔符`nIndex`。  
  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要检索其 ID 的项的索引。  
  
### <a name="return-value"></a>返回值  
 按钮或由指定的分隔符的命令 ID `nIndex`。  
  
### <a name="remarks"></a>备注  
 分隔符返回**ID_SEPARATOR**。  
  
##  <a name="getitemrect"></a>  CToolBar::GetItemRect  
 此成员函数填充`RECT`结构中包含其地址`lpRect`按钮或由指定的分隔符的坐标`nIndex`。  
  
```  
virtual void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 矩形坐标是要检索的项 （按钮或分隔符） 的索引。  
  
 `lpRect`  
 地址[RECT](../../mfc/reference/rect-structure1.md)结构，它将包含该项的坐标。  
  
### <a name="remarks"></a>备注  
 坐标是以相对于工具栏的左上角的像素为单位。  
  
 使用`GetItemRect`若要获取你想要将替换为组合框或其他控件的分隔符坐标。  
  
### <a name="example"></a>示例  
  请参阅示例[CToolBar::SetSizes](#setsizes)。  
  
##  <a name="gettoolbarctrl"></a>  CToolBar::GetToolBarCtrl  
 此成员函数允许直接访问基础的公共控件。  
  
```  
CToolBarCtrl& GetToolBarCtrl() const;  
```  
  
### <a name="return-value"></a>返回值  
 对 `CToolBarCtrl` 对象的引用。  
  
### <a name="remarks"></a>备注  
 使用`GetToolBarCtrl`若要利用 Windows 工具栏公共控件的功能并利用支持[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)提供用于自定义工具栏。  
  
 有关使用公共控件的详细信息，请参阅文章[控件](../../mfc/controls-mfc.md)和[公共控件](http://msdn.microsoft.com/library/windows/desktop/bb775493)Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]  
  
##  <a name="loadbitmap"></a>  CToolBar::LoadBitmap  
 调用此成员函数可加载由指定的位图`lpszResourceName`或`nIDResource`。  
  
```  
BOOL LoadBitmap(LPCTSTR lpszResourceName);  
BOOL LoadBitmap(UINT nIDResource);
```  
  
### <a name="parameters"></a>参数  
 `lpszResourceName`  
 指向要加载的位图的资源名称。  
  
 `nIDResource`  
 资源 ID 加载位图。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 位图应包含一个图像可查看每个工具栏按钮。 如果图像不标准大小 （16 像素宽和高 15 像素） 的调用[SetSizes](#setsizes)设置按钮大小和其图像。  
  
> [!WARNING]
> `CToolBar` 支持最多为 16 种颜色的位图。 当在工具栏编辑器中加载图像时，Visual Studio 将自动将图像转换为 16 颜色位图，如有必要，并显示一条警告消息，如果映像已转换。 如果具有多个 16 种颜色 （使用外部编辑器编辑图像） 使用的映像，应用程序可能出现意外行为。  
  
##  <a name="loadtoolbar"></a>  CToolBar::LoadToolBar  
 调用此成员函数可加载由指定的工具栏`lpszResourceName`或`nIDResource`。  
  
```  
BOOL LoadToolBar(LPCTSTR lpszResourceName);  
BOOL LoadToolBar(UINT nIDResource);
```  
  
### <a name="parameters"></a>参数  
 `lpszResourceName`  
 指向要加载的工具栏资源名称。  
  
 `nIDResource`  
 资源 ID 工具栏的加载。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 请参阅[工具栏编辑器](../../windows/toolbar-editor.md)中有关创建工具栏资源的详细信息。  
  
### <a name="example"></a>示例  
  请参阅示例[CToolBar::CreateEx](#createex)。  
  
##  <a name="setbitmap"></a>  CToolBar::SetBitmap  
 调用此成员函数可设置工具栏的位图图像。  
  
```  
BOOL SetBitmap(HBITMAP hbmImageWell);
```  
  
### <a name="parameters"></a>参数  
 *hbmImageWell*  
 位图图像与工具栏关联的句柄。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 例如，调用`SetBitmap`用户对更改按钮的操作的文档执行操作后更改位图图像。  
  
##  <a name="setbuttoninfo"></a>  CToolBar::SetButtonInfo  
 调用此成员函数可设置按钮的命令 ID、 样式和映像数量。  
  
```  
void SetButtonInfo(
    int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int iImage);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 按钮或分隔符为设置信息的从零开始索引。  
  
 `nID`  
 为其设置按钮的命令 ID 的值。  
  
 `nStyle`  
 新的按钮样式。 支持以下按钮样式：  
  
- **TBBS_BUTTON**标准按键 （默认值）  
  
- **TBBS_SEPARATOR**分隔符  
  
- **TBBS_CHECKBOX**自动复选框按钮  
  
- **TBBS_GROUP**标记的一组按钮开始位置  
  
- **TBBS_CHECKGROUP**标记的一组复选框按钮开始位置  
  
- **TBBS_DROPDOWN**创建下拉列表按钮。  
  
- **TBBS_AUTOSIZE**按钮的宽度将计算基于上按钮的文本，而非图像的大小。  
  
- **TBBS_NOPREFIX**按钮文本将不具有与之关联的快捷键前缀。  
  
 `iImage`  
 位图中的按钮的图像的新索引。  
  
### <a name="remarks"></a>备注  
 分隔符，都样式**TBBS_SEPARATOR**，此函数以像素为单位到中存储的值设置的分隔符的宽度`iImage`。  
  
> [!NOTE]
>  你还可以设置使用的按钮状态`nStyle`参数; 但是，因为由控制按钮状态[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui)处理程序中，任何状态使用设置`SetButtonInfo`下一步将会丢失空闲处理。 请参阅[如何更新用户界面对象](../../mfc/how-to-update-user-interface-objects.md)和[TN031： 控件条](../../mfc/tn031-control-bars.md)有关详细信息。  
  
 位图图像和按钮上的信息，请参阅[CToolBar](../../mfc/reference/ctoolbar-class.md)概述和[CToolBar::LoadBitmap](#loadbitmap)。  
  
##  <a name="setbuttons"></a>  CToolBar::SetButtons  
 此成员函数将每个工具栏按钮的命令 ID 设置为指定数组的相应元素的值`lpIDArray`。  
  
```  
BOOL SetButtons(
    const UINT* lpIDArray,  
    int nIDCount);
```  
  
### <a name="parameters"></a>参数  
 `lpIDArray`  
 指向命令 Id 的数组的指针。 它可以是**NULL**分配空按钮。  
  
 `nIDCount`  
 指向数组中的元素数目`lpIDArray`。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果数组的元素具有值**ID_SEPARATOR**，在工具栏上的相应位置中创建一个分隔符。 此函数还将每个按钮的样式设置为**TBBS_BUTTON**和每个分隔符样式应用到**TBBS_SEPARATOR**，并将一个图像索引分配给每个按钮。 映像索引指定位图中的按钮的图像的位置。  
  
 不需要考虑的位图中的分隔符，因为此函数不会分配为分隔符的映像索引。 如果你工具栏按钮在位置 0，1，和 3 和在位置 2，分别位于位置 0、 1 和 2 中你位图图像的分隔符为的按钮位于位置 0、 1 和 3，分别分配。  
  
 如果`lpIDArray`是**NULL**，此函数为指定的项的数目分配空间`nIDCount`。 使用[SetButtonInfo](#setbuttoninfo)设置每个项的特性。  
  
##  <a name="setbuttonstyle"></a>  CToolBar::SetButtonStyle  
 调用此成员函数可设置的样式的按钮或分隔符，或组按钮。  
  
```  
void SetButtonStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 索引的按钮或获取其信息是要设置的分隔符。  
  
 `nStyle`  
 按钮样式中。 支持以下按钮样式：  
  
- **TBBS_BUTTON**标准按键 （默认值）  
  
- **TBBS_SEPARATOR**分隔符  
  
- **TBBS_CHECKBOX**自动复选框按钮  
  
- **TBBS_GROUP**标记的一组按钮开始位置  
  
- **TBBS_CHECKGROUP**标记的一组复选框按钮开始位置  
  
- **TBBS_DROPDOWN**创建下拉列表按钮  
  
- **TBBS_AUTOSIZE**按钮的宽度将计算基于上按钮的文本，而非图像的大小  
  
- **TBBS_NOPREFIX**按钮文本将不具有与之关联的快捷键前缀  
  
### <a name="remarks"></a>备注  
 按钮样式确定如何该按钮显示和对用户输入的响应方式。  
  
 之前调用`SetButtonStyle`，调用[GetButtonStyle](#getbuttonstyle)成员函数来检索按钮或分隔符样式。  
  
> [!NOTE]
>  你还可以设置使用的按钮状态`nStyle`参数; 但是，因为由控制按钮状态[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui)处理程序中，任何状态使用设置`SetButtonStyle`下一步将会丢失空闲处理。 请参阅[如何更新用户界面对象](../../mfc/how-to-update-user-interface-objects.md)和[TN031： 控件条](../../mfc/tn031-control-bars.md)有关详细信息。  
  
##  <a name="setbuttontext"></a>  CToolBar::SetButtonText  
 调用此函数可设置上一个按钮的文本。  
  
```  
BOOL SetButtonText(
    int nIndex,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 其中的文本是设置按钮的索引。  
  
 `lpszText`  
 指向要设置在按钮上的文本。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
  请参阅示例[CToolBar::GetToolBarCtrl](#gettoolbarctrl)。  
  
##  <a name="setheight"></a>  CToolBar::SetHeight  
 此成员函数设置的值，以像素为单位，指定在工具栏的高度`cyHeight`。  
  
```  
void SetHeight(int cyHeight);
```  
  
### <a name="parameters"></a>参数  
 `cyHeight`  
 以像素为单位工具栏的高度。  
  
### <a name="remarks"></a>备注  
 在调用[SetSizes](#setsizes)，此成员函数用于重写的标准工具栏高度。 如果高度太小，则将在底部剪辑按钮。  
  
 如果未调用此函数，框架将使用按钮的大小来确定工具栏高度。  
  
##  <a name="setsizes"></a>  CToolBar::SetSizes  
 调用此成员函数可设置为的大小，以像素为单位中, 指定的工具栏按钮*sizeButton*。  
  
```  
void SetSizes(
    SIZE sizeButton,  
    SIZE sizeImage);
```  
  
### <a name="parameters"></a>参数  
 *sizeButton*  
 以像素为单位，每个按钮的大小。  
  
 `sizeImage`  
 以像素为单位的每个图像大小。  
  
### <a name="remarks"></a>备注  
 `sizeImage`参数必须包含大小，以像素为单位，工具栏的位图中图像的大小。 中的维度*sizeButton*必须足以容纳图像加 7 像素额外的宽度和高度额外 6 个像素。 此函数还将设置工具栏的高度以适应按钮。  
  
 调用此成员函数仅对工具栏不遵循*软件设计的 Windows 界面指南*按钮和图像的大小的建议。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 CTRLBARS](../../visual-cpp-samples.md)   
 [MFC 示例 DLGCBR32](../../visual-cpp-samples.md)   
 [MFC 示例 DOCKTOOL](../../visual-cpp-samples.md)   
 [CControlBar 类](../../mfc/reference/ccontrolbar-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CToolBarCtrl 类](../../mfc/reference/ctoolbarctrl-class.md)   
 [CControlBar 类](../../mfc/reference/ccontrolbar-class.md)
