---
title: "CToolBar 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- Windows toolbar common controls [C++]
- control bars [C++], CToolBar class
- toolbars [C++], CToolBar class
- buttons [C++], MFC toolbars
- bitmaps [C++], button controls
- CToolBar class
- Windows common controls [C++], CToolBar class
ms.assetid: e868da26-5e07-4607-9651-e2f863ad9059
caps.latest.revision: 26
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
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: d7fea85426eef09f3694bd26e037acaaccc63f01
ms.lasthandoff: 02/24/2017

---
# <a name="ctoolbar-class"></a>CToolBar 类
具有一行位图化按钮和可选分隔符的控件条。  
  
## <a name="syntax"></a>语法  
  
```  
class CToolBar : public CControlBar  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CToolBar::CToolBar](#ctoolbar)|构造 `CToolBar` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CToolBar::CommandToIndex](#commandtoindex)|返回与给定的命令 ID 的按钮的索引|  
|[CToolBar::Create](#create)|创建 Windows 工具栏并将其附加到`CToolBar`对象。|  
|[CToolBar::CreateEx](#createex)|创建`CToolBar`具有其他样式为嵌入对象`CToolBarCtrl`对象。|  
|[CToolBar::GetButtonInfo](#getbuttoninfo)|检索 ID、 样式和一个按钮的图像数。|  
|[CToolBar::GetButtonStyle](#getbuttonstyle)|检索一个按钮的样式。|  
|[CToolBar::GetButtonText](#getbuttontext)|检索将显示在按钮的文本。|  
|[CToolBar::GetItemID](#getitemid)|返回的命令 ID 的按钮或从给定索引处的分隔符。|  
|[CToolBar::GetItemRect](#getitemrect)|检索给定索引处的项的显示矩形。|  
|[CToolBar::GetToolBarCtrl](#gettoolbarctrl)|允许直接访问基础的公共控件。|  
|[CToolBar::LoadBitmap](#loadbitmap)|加载包含位图按钮图像的位图。|  
|[CToolBar::LoadToolBar](#loadtoolbar)|加载使用资源编辑器创建工具栏资源。|  
|[CToolBar::SetBitmap](#setbitmap)|设置一个位图化图像。|  
|[CToolBar::SetButtonInfo](#setbuttoninfo)|设置 ID、 样式和一个按钮的图像数。|  
|[CToolBar::SetButtons](#setbuttons)|设置按钮样式和的位图中的按钮图像的索引。|  
|[CToolBar::SetButtonStyle](#setbuttonstyle)|将按钮样式设置。|  
|[CToolBar::SetButtonText](#setbuttontext)|在按钮上设置将显示的文本。|  
|[CToolBar::SetHeight](#setheight)|设置工具栏的高度。|  
|[CToolBar::SetSizes](#setsizes)|设置按钮和其位图的大小。|  
  
## <a name="remarks"></a>备注  
 这些按钮可以像普通按钮、 复选框按钮、 或单选按钮。 `CToolBar`对象是从类派生的框架窗口对象的通常嵌入的成员[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)。  
  
 [CToolBar::GetToolBarCtrl](#gettoolbarctrl)，成员函数新增到 MFC 4.0，让您充分利用自定义工具栏和其他功能的 Windows 公共控件的支持。 `CToolBar`成员函数为您提供的大多数 Windows 公共控件; 功能但是，当您调用`GetToolBarCtrl`，您可以为您的工具栏更多 Windows 95/98 工具栏的特征。 当您调用`GetToolBarCtrl`，它将返回到引用`CToolBarCtrl`对象。 请参阅[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)有关设计使用 Windows 公共控件的工具栏的详细信息。 关于公共控件的详细信息，请参阅[公共控件](http://msdn.microsoft.com/library/windows/desktop/bb775493)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 Visual c + + 提供了两个方法，以创建工具栏。 若要创建工具栏资源使用资源编辑器，请按照下列步骤︰  
  
1.  创建工具栏上的资源。  
  
2.  构造 `CToolBar` 对象。  
  
3.  调用[创建](#create)(或[CreateEx](#createex)) 函数来创建 Windows 工具栏并将其附加到`CToolBar`对象。  
  
4.  调用[LoadToolBar](#loadtoolbar)加载工具栏资源。  
  
 否则，请按照下列步骤︰  
  
1.  构造 `CToolBar` 对象。  
  
2.  调用[创建](#create)(或[CreateEx](#createex)) 函数来创建 Windows 工具栏并将其附加到`CToolBar`对象。  
  
3.  调用[LoadBitmap](#loadbitmap)加载包含工具栏按钮图像的位图。  
  
4.  调用[SetButtons](#setbuttons)设置按钮样式并将每个按钮与在位图中图像相关联。  
  
 在工具栏中的所有按钮图像均都来自一个位图，其中必须包含一个图像可查看每个按钮。 所有映像必须都是相同的大小;默认值为 16 像素宽、 高 15 像素。 映像必须在位图中的并排放置。  
  
 `SetButtons`函数采用指向的控件 Id 和一个整数，指定数组中的元素数的数组的指针。 该函数将每个按钮的 ID 设置为该数组的对应元素的值，并将每个按钮分配图像索引，指定位图中的按钮的图像的位置。 如果数组元素具有值**ID_SEPARATOR**，分配没有图像索引。  
  
 在位图中图像的顺序通常是在其中绘制它们在屏幕上，但您可以使用的顺序[SetButtonInfo](#setbuttoninfo)函数来更改图像订单和绘制顺序之间的关系。  
  
 在工具栏中的所有按钮都都大小相同。 默认值为 24 x 22 像素，根据所使用*软件设计的 Windows 界面指南*。 图像和按钮尺寸之间的任何额外空间用于构成图像周围的边框。  
  
 每个按钮有一个映像。 各种按钮状态，然后从该一个映像生成样式 （按下向上、 下，已禁用、 已关闭、 禁用和中间状态）。 尽管位图可以是任何颜色，您可以获得最佳结果与黑色和灰色阴影中的图像。  
  
> [!WARNING]
> `CToolBar`支持最多为 16 种颜色的位图。 当图像加载到工具栏编辑器中时，Visual Studio 会自动将图像转换为 16 色位图，如有必要，并显示一条警告消息，如果映像已转换。 如果具有多个 16 种颜色 （使用外部编辑器编辑映像） 使用的映像，该应用程序可能会出现意外行为。  
  
 工具栏按钮默认情况下模拟按键。 但是，复选框按钮或单选按钮，还可以模拟工具栏按钮。 复选框按钮有三种状态︰ 选中、 已清除，和不确定。 单选按钮都有只有两种状态︰ 检查并清除。  
  
 若要设置的单个按钮或分隔符样式，而不指向一个数组，调用[GetButtonStyle](#getbuttonstyle)检索并将该样式，然后调用[SetButtonStyle](#setbuttonstyle)而不是`SetButtons`。 `SetButtonStyle`如果想要在运行时更改按钮的样式，则将最为有用。  
  
 若要将分配要在按钮上显示的文本，请调用[GetButtonText](#getbuttontext)来检索要显示在的按钮，然后调用的文本[SetButtonText](#setbuttontext)设置的文本。  
  
 若要创建一个复选框按钮，将其分配样式**TBBS_CHECKBOX**或使用`CCmdUI`对象的`SetCheck`成员函数在`ON_UPDATE_COMMAND_UI`处理程序。 调用`SetCheck`按钮将变成复选框按钮。 传递`SetCheck`参数为 0 代表取消选中后，1 代表选中，或 2 为不确定。  
  
 若要创建的单选按钮，调用[CCmdUI](../../mfc/reference/ccmdui-class.md)对象的[SetRadio](../../mfc/reference/ccmdui-class.md#setradio)成员函数从`ON_UPDATE_COMMAND_UI`处理程序。 传递`SetRadio`为未选中或签入的非零参数为 0。 为了提供单选按钮组的相互排斥行为，您必须具有`ON_UPDATE_COMMAND_UI`针对所有组中的按钮处理程序。  
  
 有关详细信息使用`CToolBar`，请参阅文章[MFC 工具栏实现](../../mfc/mfc-toolbar-implementation.md)和[技术说明 31︰ 控件条](../../mfc/tn031-control-bars.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CToolBar`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxext.h  
  
##  <a name="commandtoindex"></a>CToolBar::CommandToIndex  
 此成员函数返回第一个工具栏按钮，开始位置 0，其命令 ID 匹配的索引`nIDFind`。  
  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIDFind`  
 工具栏按钮的命令 ID。  
  
### <a name="return-value"></a>返回值  
 索引按钮，则为-1 如果按钮没有给定的命令 id。  
  
##  <a name="create"></a>CToolBar::Create  
 此成员函数将创建一个 Windows 工具栏 （子窗口），并将其与关联`CToolBar`对象。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,  
    UINT nID = AFX_IDW_TOOLBAR);
```  
  
### <a name="parameters"></a>参数  
 `pParentWnd`  
 指向作为工具栏上的父级的窗口。  
  
 `dwStyle`  
 工具栏上的样式。 支持的其他工具栏样式包括︰  
  
- `CBRS_TOP`控件条是在框架窗口的顶部。  
  
- `CBRS_BOTTOM`控件条是在框架窗口的底部。  
  
- `CBRS_NOALIGN`父级调整大小时，则不会重新定位控件条。  
  
- `CBRS_TOOLTIPS`控件条显示工具提示。  
  
- **CBRS_SIZE_DYNAMIC**控件条是动态的。  
  
- **CBRS_SIZE_FIXED**固定的控件条。  
  
- **CBRS_FLOATING**浮动的控件条。  
  
- `CBRS_FLYBY`状态栏显示有关该按钮的信息。  
  
- **CBRS_HIDE_INPLACE**控件条不向用户显示。  
  
 `nID`  
 工具栏上的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 它还将工具栏高度设置为默认值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&179;](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]  
  
##  <a name="createex"></a>CToolBar::CreateEx  
 调用此函数可创建一个 Windows 工具栏 （子窗口） 并将其与关联`CToolBar`对象。  
  
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
 指向作为工具栏上的父级的窗口。  
  
 `dwCtrlStyle`  
 适用于创建嵌入其他样式[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)对象。 默认情况下，此值设置为**TBSTYLE_FLAT**。 工具栏样式的完整列表，请参阅`dwStyle`。  
  
 `dwStyle`  
 工具栏上的样式。 请参阅[工具栏控件和按钮样式](http://msdn.microsoft.com/library/windows/desktop/bb760439)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关相应的样式的列表。  
  
 *rcBorders*  
 一个[CRect](../../atl-mfc-shared/reference/crect-class.md)工具栏窗口边框的宽度定义的对象。 默认情况下，从而导致与无边框工具栏窗口将这些边框设 0,0,0,0。  
  
 `nID`  
 工具栏上的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 它还将工具栏高度设置为默认值。  
  
 使用`CreateEx`，而不是[创建](#create)，当某些样式需要在嵌入式的工具栏控件的创建过程。 例如，设置`dwCtrlStyle`到**TBSTYLE_FLAT |TBSTYLE_TRANSPARENT**以创建工具栏类似于 Internet Explorer 4 工具栏。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&180;](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]  
  
##  <a name="ctoolbar"></a>CToolBar::CToolBar  
 此成员函数所构造`CToolBar`对象并设置默认大小。  
  
```  
CToolBar();
```  
  
### <a name="remarks"></a>备注  
 调用[创建](#create)成员函数来创建工具栏窗口中。  
  
##  <a name="getbuttoninfo"></a>CToolBar::GetButtonInfo  
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
 工具栏按钮或分隔符将为要检索其信息的索引。  
  
 `nID`  
 引用**UINT**已设置为按钮的命令 ID。  
  
 `nStyle`  
 引用**UINT**它被设置为按钮的样式。  
  
 `iImage`  
 对一个整数，它设置为位图中的按钮的图像的索引的引用。  
  
### <a name="remarks"></a>备注  
 这些值分配给引用的变量`nID`， `nStyle`，和`iImage`。 映像索引是包含的所有工具栏按钮的图像位图中图像的位置。 第一幅图像位于位置 0。  
  
 如果`nIndex`指定分隔符，`iImage`设为以像素为单位的分隔符宽度。  
  
##  <a name="getbuttonstyle"></a>CToolBar::GetButtonStyle  
 调用此成员函数以检索按钮或在工具栏上的分隔符的样式。  
  
```  
UINT GetButtonStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要检索的工具栏按钮或分隔符样式的索引。  
  
### <a name="return-value"></a>返回值  
 按钮或由指定的分隔符的样式`nIndex`。  
  
### <a name="remarks"></a>备注  
 按钮样式确定按钮的显示方式和对用户输入的响应方式。 请参阅[SetButtonStyle](#setbuttonstyle)有关按钮样式的示例。  
  
##  <a name="getbuttontext"></a>CToolBar::GetButtonText  
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
 对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)将包含文本要检索的对象。  
  
### <a name="return-value"></a>返回值  
 一个`CString`对象，其中包含该按钮的文本。  
  
### <a name="remarks"></a>备注  
 此成员的第二种形式函数填充`CString`具有字符串文本对象。  
  
##  <a name="getitemid"></a>CToolBar::GetItemID  
 此成员函数返回的按钮或由指定的分隔符的命令 ID `nIndex`。  
  
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
  
##  <a name="getitemrect"></a>CToolBar::GetItemRect  
 此成员函数将填充`RECT`结构中包含其地址`lpRect`使用的按钮或由指定的分隔符的坐标`nIndex`。  
  
```  
virtual void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要从中检索其矩形坐标的项 （按钮或分隔符） 的索引。  
  
 `lpRect`  
 地址的指针[RECT](../../mfc/reference/rect-structure1.md)结构，它将包含项目的坐标。  
  
### <a name="remarks"></a>备注  
 坐标是以相对于窗口左上角的工具栏上的像素为单位。  
  
 使用`GetItemRect`若要获取你想要将替换为组合框或其他控件的分隔符坐标。  
  
### <a name="example"></a>示例  
  请参阅示例[CToolBar::SetSizes](#setsizes)。  
  
##  <a name="gettoolbarctrl"></a>CToolBar::GetToolBarCtrl  
 此成员函数允许直接访问基础的公共控件。  
  
```  
CToolBarCtrl& GetToolBarCtrl() const;  
```  
  
### <a name="return-value"></a>返回值  
 对 `CToolBarCtrl` 对象的引用。  
  
### <a name="remarks"></a>备注  
 使用`GetToolBarCtrl`为了充分利用 Windows 工具栏公共控件的功能并且为了充分利用支持[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)提供用于自定义工具栏。  
  
 有关使用公共控件的详细信息，请参阅文章[控件](../../mfc/controls-mfc.md)和[公共控件](http://msdn.microsoft.com/library/windows/desktop/bb775493)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocViewSDI #&15;](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]  
  
##  <a name="loadbitmap"></a>CToolBar::LoadBitmap  
 调用此成员函数可加载由指定的位图`lpszResourceName`或`nIDResource`。  
  
```  
BOOL LoadBitmap(LPCTSTR lpszResourceName);  
BOOL LoadBitmap(UINT nIDResource);
```  
  
### <a name="parameters"></a>参数  
 `lpszResourceName`  
 指针，指向要加载的位图的资源名称。  
  
 `nIDResource`  
 资源 ID 加载位图。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 位图应包含一个图像可查看每个工具栏按钮。 如果图像不是标准的大小 （宽为 16 像素和高 15 像素） 的调用[SetSizes](#setsizes)设置按钮大小和其映像。  
  
> [!WARNING]
> `CToolBar`支持最多为 16 种颜色的位图。 当图像加载到工具栏编辑器中时，Visual Studio 会自动将图像转换为 16 色位图，如有必要，并显示一条警告消息，如果映像已转换。 如果具有多个 16 种颜色 （使用外部编辑器编辑映像） 使用的映像，该应用程序可能会出现意外行为。  
  
##  <a name="loadtoolbar"></a>CToolBar::LoadToolBar  
 调用此成员函数以加载所指定的工具栏`lpszResourceName`或`nIDResource`。  
  
```  
BOOL LoadToolBar(LPCTSTR lpszResourceName);  
BOOL LoadToolBar(UINT nIDResource);
```  
  
### <a name="parameters"></a>参数  
 `lpszResourceName`  
 指针，指向要加载工具栏上的资源名称。  
  
 `nIDResource`  
 资源 ID 加载工具栏。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 请参阅[工具栏编辑器](../../windows/toolbar-editor.md)中有关创建工具栏资源的详细信息。  
  
### <a name="example"></a>示例  
  请参阅示例[CToolBar::CreateEx](#createex)。  
  
##  <a name="setbitmap"></a>CToolBar::SetBitmap  
 调用此成员函数可设置工具栏的位图图像。  
  
```  
BOOL SetBitmap(HBITMAP hbmImageWell);
```  
  
### <a name="parameters"></a>参数  
 *hbmImageWell*  
 与工具栏相关联的位图图像的句柄。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 例如，调用`SetBitmap`用户更改按钮的操作的文档上执行的操作后更改位图图像。  
  
##  <a name="setbuttoninfo"></a>CToolBar::SetButtonInfo  
 调用该成员函数以设置按钮的命令 ID、 样式和映像数。  
  
```  
void SetButtonInfo(
    int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int iImage);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 按钮或分隔符的信息要为其设置的从零开始索引。  
  
 `nID`  
 为其设置按钮的命令 ID 的值。  
  
 `nStyle`  
 新的按钮样式。 支持以下按钮样式︰  
  
- **TBBS_BUTTON**标准按键 （默认值）  
  
- **TBBS_SEPARATOR**分隔符  
  
- **TBBS_CHECKBOX**自动复选框按钮  
  
- **TBBS_GROUP**标记开始的一组按钮  
  
- **TBBS_CHECKGROUP**标记开始的一组复选框按钮  
  
- **TBBS_DROPDOWN**创建了一个下拉列表按钮。  
  
- **TBBS_AUTOSIZE**将基于按钮的文本，而非图像的大小计算按钮的宽度。  
  
- **TBBS_NOPREFIX**按钮文本不会与之关联的加速器前缀。  
  
 `iImage`  
 位图中的按钮的图像的新索引。  
  
### <a name="remarks"></a>备注  
 为分隔符，它具有样式**TBBS_SEPARATOR**，此函数设置分隔符的宽度以像素为单位中存储的值为`iImage`。  
  
> [!NOTE]
>  您还可以设置使用的按钮状态`nStyle`参数; 但是，因为由控制按钮状态[ON_UPDATE_COMMAND_UI](http://msdn.microsoft.com/library/c4de3c21-2d2e-4b89-a4ce-d0c0e2d9edc4)处理程序中，任何状态使用设置`SetButtonInfo`在下一步的空闲处理期间都将丢失。 请参阅[如何更新用户界面对象](../../mfc/how-to-update-user-interface-objects.md)和[TN031︰ 控件条](../../mfc/tn031-control-bars.md)有关详细信息。  
  
 有关位图图像和按钮的信息，请参阅[CToolBar](../../mfc/reference/ctoolbar-class.md)概述和[CToolBar::LoadBitmap](#loadbitmap)。  
  
##  <a name="setbuttons"></a>CToolBar::SetButtons  
 此成员函数将每个工具栏按钮的命令 ID 设置为指定数组的对应元素的值`lpIDArray`。  
  
```  
BOOL SetButtons(
    const UINT* lpIDArray,  
    int nIDCount);
```  
  
### <a name="parameters"></a>参数  
 `lpIDArray`  
 指向数组的命令 Id 的指针。 它可以是**NULL**分配空按钮。  
  
 `nIDCount`  
 指向数组中的元素数目`lpIDArray`。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果数组的元素具有值**ID_SEPARATOR**，在工具栏上的对应位置中创建一个分隔符。 此函数还将每个按钮的样式设置为**TBBS_BUTTON**和每个分隔符样式应用到**TBBS_SEPARATOR**，并将图像索引分配给每个按钮。 映像索引指定位图中的按钮的图像的位置。  
  
 不需要考虑的位图中的分隔符，因为此函数不会分配为分隔符的图像索引。 如果您的工具栏按钮位置 0，1 和 3，而在位置 2，分别位于位置 0、 1 和 2 在位图中图像的分隔符被分配给位于位置 0、 1 和 3，按钮分别。  
  
 如果`lpIDArray`是**NULL**，此函数为指定的项目数分配空间`nIDCount`。 使用[SetButtonInfo](#setbuttoninfo)以设置每个项目的属性。  
  
##  <a name="setbuttonstyle"></a>CToolBar::SetButtonStyle  
 调用此成员函数以设置样式的按钮或分隔符，或分组按钮。  
  
```  
void SetButtonStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 按钮或分隔符的信息是要设置的索引。  
  
 `nStyle`  
 按钮样式。 支持以下按钮样式︰  
  
- **TBBS_BUTTON**标准按键 （默认值）  
  
- **TBBS_SEPARATOR**分隔符  
  
- **TBBS_CHECKBOX**自动复选框按钮  
  
- **TBBS_GROUP**标记开始的一组按钮  
  
- **TBBS_CHECKGROUP**标记开始的一组复选框按钮  
  
- **TBBS_DROPDOWN**创建了一个下拉列表按钮  
  
- **TBBS_AUTOSIZE**按钮的宽度将基于按钮的文本，而非图像的大小计算  
  
- **TBBS_NOPREFIX**按钮文本不会与之关联的快捷键对应前缀  
  
### <a name="remarks"></a>备注  
 按钮样式确定按钮的显示方式和对用户输入的响应方式。  
  
 之前，先调用`SetButtonStyle`，调用[GetButtonStyle](#getbuttonstyle)成员函数以检索按钮或分隔符样式。  
  
> [!NOTE]
>  您还可以设置使用的按钮状态`nStyle`参数; 但是，因为由控制按钮状态[ON_UPDATE_COMMAND_UI](http://msdn.microsoft.com/library/c4de3c21-2d2e-4b89-a4ce-d0c0e2d9edc4)处理程序中，任何状态使用设置`SetButtonStyle`在下一步的空闲处理期间都将丢失。 请参阅[如何更新用户界面对象](../../mfc/how-to-update-user-interface-objects.md)和[TN031︰ 控件条](../../mfc/tn031-control-bars.md)有关详细信息。  
  
##  <a name="setbuttontext"></a>CToolBar::SetButtonText  
 调用此函数可设置上一个按钮的文本。  
  
```  
BOOL SetButtonText(
    int nIndex,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 按钮的文本是要设置的索引。  
  
 `lpszText`  
 指向要在按钮上设置的文本。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
  请参阅示例[CToolBar::GetToolBarCtrl](#gettoolbarctrl)。  
  
##  <a name="setheight"></a>CToolBar::SetHeight  
 此成员函数设置的值，以像素为单位，在指定工具栏的高度`cyHeight`。  
  
```  
void SetHeight(int cyHeight);
```  
  
### <a name="parameters"></a>参数  
 `cyHeight`  
 以像素为单位的工具栏的高度。  
  
### <a name="remarks"></a>备注  
 在调用[SetSizes](#setsizes)，使用此成员函数来覆盖的标准工具栏的高度。 如果高度太小，这些按钮将裁剪在底部。  
  
 如果未调用此函数，框架将使用该按钮的大小来确定工具栏高度。  
  
##  <a name="setsizes"></a>CToolBar::SetSizes  
 调用此成员函数以设置工具栏的按钮的大小，以像素为单位，指定在*sizeButton*。  
  
```  
void SetSizes(
    SIZE sizeButton,  
    SIZE sizeImage);
```  
  
### <a name="parameters"></a>参数  
 *sizeButton*  
 以像素为单位，每个按钮的大小。  
  
 `sizeImage`  
 以像素为单位，每个图像的大小。  
  
### <a name="remarks"></a>备注  
 `sizeImage`参数必须包含以像素为单位的工具栏位图中图像的大小。 中的维度*sizeButton*必须足以容纳图像加 7 个像素多余的宽度和高度额外 6 个像素。 此函数还将设置工具栏的高度以适应这些按钮。  
  
 调用此成员函数仅对不符合的工具栏*软件设计的 Windows 界面指南*为按钮和图像大小的建议。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCListView #&8;](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 CTRLBARS](../../visual-cpp-samples.md)   
 [MFC 示例 DLGCBR32](../../visual-cpp-samples.md)   
 [MFC 示例 DOCKTOOL](../../visual-cpp-samples.md)   
 [CControlBar 类](../../mfc/reference/ccontrolbar-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CToolBarCtrl 类](../../mfc/reference/ctoolbarctrl-class.md)   
 [CControlBar 类](../../mfc/reference/ccontrolbar-class.md)

