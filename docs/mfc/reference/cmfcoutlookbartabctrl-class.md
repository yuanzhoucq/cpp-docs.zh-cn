---
title: CMFCOutlookBarTabCtrl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::AddControl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::Create
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableInPlaceEdit
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableScrollButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetVisiblePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsMode2003
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowOptions
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetActiveTab
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetPageButtonTextAlign
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetToolbarImageList
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetVisiblePageButtons
dev_langs:
- C++
helpviewer_keywords:
- CMFCOutlookBarTabCtrl [MFC], AddControl
- CMFCOutlookBarTabCtrl [MFC], CanShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], CanShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], Create
- CMFCOutlookBarTabCtrl [MFC], EnableAnimation
- CMFCOutlookBarTabCtrl [MFC], EnableInPlaceEdit
- CMFCOutlookBarTabCtrl [MFC], EnableScrollButtons
- CMFCOutlookBarTabCtrl [MFC], GetBorderSize
- CMFCOutlookBarTabCtrl [MFC], GetVisiblePageButtons
- CMFCOutlookBarTabCtrl [MFC], IsAnimation
- CMFCOutlookBarTabCtrl [MFC], IsMode2003
- CMFCOutlookBarTabCtrl [MFC], OnShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowOptions
- CMFCOutlookBarTabCtrl [MFC], SetActiveTab
- CMFCOutlookBarTabCtrl [MFC], SetBorderSize
- CMFCOutlookBarTabCtrl [MFC], SetPageButtonTextAlign
- CMFCOutlookBarTabCtrl [MFC], SetToolbarImageList
- CMFCOutlookBarTabCtrl [MFC], SetVisiblePageButtons
ms.assetid: b1f2b3f7-cc59-49a3-99d8-7ff9b37c044b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e677879079eaab3dd36481fec76ca53da92ef87d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373298"
---
# <a name="cmfcoutlookbartabctrl-class"></a>CMFCOutlookBarTabCtrl Class
在 Microsoft Outlook 中具有 **“导航窗格”** 可视外观的选项卡控件。  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
## <a name="syntax"></a>语法  
  
```  
class CMFCOutlookBarTabCtrl : public CMFCBaseTabCtrl  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCOutlookBarTabCtrl::CMFCOutlookBarTabCtrl`|默认构造函数。|  
|`CMFCOutlookBarTabCtrl::~CMFCOutlookBarTabCtrl`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCOutlookBarTabCtrl::AddControl](#addcontrol)|将 Windows 控件添加为 Outlook 栏中的新选项卡。|  
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|由框架调用以确定将显示当用户编辑框的尺寸将重命名选项卡。（重写 `CMFCBaseTabCtrl::CalcRectEdit`。）|  
|[CMFCOutlookBarTabCtrl::CanShowFewerPageButtons](#canshowfewerpagebuttons)|由框架调用以确定如果不是当前可见，则可以显示较少的 Outlook 栏选项卡页按钮的大小调整操作期间。|  
|[CMFCOutlookBarTabCtrl::CanShowMorePageButtons](#canshowmorepagebuttons)|由框架调用以确定是否可以显示多个 Outlook 栏选项卡页按钮，不是当前可见的大小调整操作期间。|  
|[CMFCOutlookBarTabCtrl::Create](#create)|创建 Outlook 栏选项卡控件。|  
|`CMFCOutlookBarTabCtrl::CreateObject`|由框架用于创建此类类型的动态实例。|  
|[CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)|指定是否启用活动选项卡之间进行切换过程中发生的动画。|  
|[CMFCOutlookBarTabCtrl::EnableInPlaceEdit](#enableinplaceedit)|指定用户是否可以修改选项卡按钮的 Outlook 栏上的文本标签。 (重写[CMFCBaseTabCtrl::EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit)。)|  
|[CMFCOutlookBarTabCtrl::EnableScrollButtons](#enablescrollbuttons)|由框架调用以启用允许用户滚动 Outlook 栏窗格上的按钮的按钮。|  
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|标识包含指定的点的窗格。 (重写[CMFCBaseTabCtrl::FindTargetWnd](../../mfc/reference/cmfcbasetabctrl-class.md#findtargetwnd)。)|  
|[CMFCOutlookBarTabCtrl::GetBorderSize](#getbordersize)|返回 Outlook 选项卡控件的边框大小。|  
|`CMFCOutlookBarTabCtrl::GetTabArea`|检索的大小和选项卡控件的选项卡区域的位置。 (重写[CMFCBaseTabCtrl::GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea)。)|  
|`CMFCOutlookBarTabCtrl::GetThisClass`|由框架用于获取指向的指针[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型关联的对象。|  
|[CMFCOutlookBarTabCtrl::GetVisiblePageButtons](#getvisiblepagebuttons)||  
|[CMFCOutlookBarTabCtrl::IsAnimation](#isanimation)|确定是否启用活动选项卡之间进行切换过程中发生的动画。|  
|[CMFCOutlookBarTabCtrl::IsMode2003](#ismode2003)|确定 Outlook 栏选项卡控件是否在模拟 Microsoft Outlook 2003 模式下。|  
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|确定点是否在选项卡区域内。 (重写[CMFCBaseTabCtrl::IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea)。)|  
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|确定选项卡是否可拆分。 (重写[CMFCBaseTabCtrl::IsTabDetachable](../../mfc/reference/cmfcbasetabctrl-class.md#istabdetachable)。)|  
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|插入或删除选项卡时，由框架调用。 （重写 `CMFCBaseTabCtrl::OnChangeTabs`。）|  
|[CMFCOutlookBarTabCtrl::OnShowFewerPageButtons](#onshowfewerpagebuttons)|由框架调用以减少可见的选项卡页按钮的数目。|  
|[CMFCOutlookBarTabCtrl::OnShowMorePageButtons](#onshowmorepagebuttons)|由框架调用以增加可见的选项卡页按钮的数目。|  
|[CMFCOutlookBarTabCtrl::OnShowOptions](#onshowoptions)|显示**导航窗格选项**对话框。|  
|`CMFCOutlookBarTabCtrl::RecalcLayout`|重新计算选项卡控件的内部布局。 (重写[CMFCBaseTabCtrl::RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout)。)|  
|[CMFCOutlookBarTabCtrl::SetActiveTab](#setactivetab)|设置活动选项卡。(重写[CMFCBaseTabCtrl::SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab)。)|  
|[CMFCOutlookBarTabCtrl::SetBorderSize](#setbordersize)|设置 Outlook 选项卡控件的边框大小。|  
|[CMFCOutlookBarTabCtrl::SetPageButtonTextAlign](#setpagebuttontextalign)|在 Outlook 栏的选项卡按钮上设置的对齐方式的文本标签。|  
|[CMFCOutlookBarTabCtrl::SetToolbarImageList](#settoolbarimagelist)|设置包含在 Outlook 2003 模式下的 Outlook 栏底部显示的图标的位图 (请参阅[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md))。|  
|[CMFCOutlookBarTabCtrl::SetVisiblePageButtons](#setvisiblepagebuttons)||  
  
## <a name="remarks"></a>备注  
 若要创建具有提供停靠支持 Outlook 栏，使用`CMFCOutlookBar`对象以承载栏选项卡控件的 Outlook。 有关详细信息，请参阅[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何初始化`CMFCOutlookBarTabCtrl`对象，并使用中的各种方法`CMFCOutlookBarTabCtrl`类。 该示例演示如何启用 Outlook 栏选项卡页按钮上的文本标签就地编辑、 启用动画、 启用滚动句柄，使用户能够滚动 Outlook 栏窗格上的按钮、 设置 Outlook 选项卡上下文的边框大小角色，并设置上的 Outlook 栏的选项卡按钮的文本标签的对齐方式。 此代码片段属于[Outlook 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_OutlookDemo#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_1.cpp)]  
[!code-cpp[NVC_MFC_OutlookDemo#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)  
  
 [CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxoutlookbartabctrl.h  
  
##  <a name="addcontrol"></a>  CMFCOutlookBarTabCtrl::AddControl  
 将 Windows 控件添加为 Outlook 栏中的新选项卡。  
  
```  
void AddControl(
    CWnd* pWndCtrl,  
    LPCTSTR lpszName,  
    int nImageID=-1,  
    BOOL bDetachable=TRUE,  
    DWORD dwControlBarStyle=AFX_CBRS_FLOAT |  AFX_CBRS_CLOSE | AFX_CBRS_RESIZE |  CBRS_AFX_AUTOHIDE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndCtrl`  
 指向要添加的控件的指针。  
  
 [in] `lpszName`  
 指定的选项卡的名称。  
  
 [in] `bDetachable`  
 如果`TRUE`，页面将创建为可拆分。  
  
 [in] `nImageID`  
 在新选项卡中显示的图像的内部图像列表中的映像索引。  
  
 [in] `dwControlBarStyle`  
 指定 AFX_ `CBRS_`* 样式已包装的停靠窗格。  
  
### <a name="remarks"></a>备注  
 使用此函数以作为新的 outlook 栏页添加控件。  
  
 在内部调用此函数[cmfcbasetabctrl:: Addtab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)。  
  
 如果你设置`bDetachable`到`TRUE`，`AddControl`会在内部创建`CDockablePaneAdapter`对象，并将包装添加的控件。 它自动设置选项卡式窗口的运行时类的运行时类`CMFCOutlookBar`和在浮点帧的运行时类`CMultiPaneFrameWnd`。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`AddControl`中的方法`CMFCOutlookBarTabCtrl`类。 此代码片段属于[Outlook 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_OutlookDemo#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_3.cpp)]  
  
##  <a name="canshowfewerpagebuttons"></a>  CMFCOutlookBarTabCtrl::CanShowFewerPageButtons  
 由框架调用在调整大小时操作，以确定是否可以不是当前可见显示较少的 Outlook 栏选项卡页按钮。  
  
```  
virtual BOOL CanShowFewerPageButtons() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果存在多个按钮;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 Outlook 栏选项卡控件动态添加或移除根据可用空间量是显示的选项卡。 此方法由框架用于帮助完成该过程。  
  
##  <a name="canshowmorepagebuttons"></a>  CMFCOutlookBarTabCtrl::CanShowMorePageButtons  
 由框架调用在调整大小时操作，以确定是否不是当前可见，也可以显示多个 Outlook 栏选项卡页按钮。  
  
```  
virtual BOOL CanShowMorePageButtons() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果不是当前可见; 的按钮否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 Outlook 栏选项卡控件动态添加或删除从显示，具体取决于空间量是可用的选项卡。 此方法由框架用于帮助完成该过程。  
  
##  <a name="create"></a>  CMFCOutlookBarTabCtrl::Create  
 创建 Outlook 栏选项卡控件。  
  
```  
virtual BOOL Create(
    const CRect& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 [in] `rect`  
 指定的初始大小和位置，以像素为单位。  
  
 [in] `pParentWnd`  
 向父窗口的点。 不得为 `NULL`。  
  
 [in] `nID`  
 控件 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则已创建控件则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 通常情况下，outlook 栏选项卡控件时，会创建[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)控件`WM_CREATE`过程的消息。  
  
##  <a name="enableanimation"></a>  CMFCOutlookBarTabCtrl::EnableAnimation  
 指定是否启用活动选项卡之间进行切换过程中发生的动画。  
  
```  
static void EnableAnimation(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 指定是否应启用或禁用动画。  
  
### <a name="remarks"></a>备注  
 调用此函数可启用和禁用动画。 当用户打开选项卡页时，该页的标题将滑向上或向下如果启用动画。 如果禁用了动画，页面将立即变为活动状态。  
  
 默认情况下，启用动画。  
  
##  <a name="enableinplaceedit"></a>  CMFCOutlookBarTabCtrl::EnableInPlaceEdit  
 指定用户是否可以修改选项卡页按钮的 Outlook 栏上的文本标签。  
  
```  
virtual void EnableInPlaceEdit(BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 `bEnable`  
 如果`TRUE`，启用的文本标签就地编辑。 如果`FALSE`，禁用就地编辑。  
  
### <a name="remarks"></a>备注  
 调用此函数可启用或禁用在就地编辑选项卡页按钮上的文本标签。 默认情况下在就地编辑功能被禁用。  
  
##  <a name="enablescrollbuttons"></a>  CMFCOutlookBarTabCtrl::EnableScrollButtons  
 由框架调用以启用允许用户滚动 Outlook 栏窗格上的按钮的滚动句柄。  
  
```  
void EnableScrollButtons(
    BOOL bEnable = TRUE,  
    BOOL bIsUp = TRUE,  
    BOOL bIsDown = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 确定是否显示的滚动按钮。  
  
 [in] `bIsUp`  
 确定是否显示顶部的滚动条。  
  
 [in] `bIsDown`  
 确定是否显示底部滚动条。  
  
### <a name="remarks"></a>备注  
 允许滚动按钮时显示。 活动选项卡更改要还原的滚动按钮时，将由框架调用此方法。  
  
##  <a name="getbordersize"></a>  CMFCOutlookBarTabCtrl::GetBorderSize  
 返回 Outlook 选项卡控件的边框大小。  
  
```  
int GetBorderSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 边框的大小，以像素为单位。  
  
##  <a name="getvisiblepagebuttons"></a>  CMFCOutlookBarTabCtrl::GetVisiblePageButtons  

  
```  
int GetVisiblePageButtons() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="isanimation"></a>  CMFCOutlookBarTabCtrl::IsAnimation  
 指定是否启用活动选项卡之间进行切换过程中发生的动画。  
  
```  
static BOOL IsAnimation();
```  
  
### <a name="return-value"></a>返回值  
 如果已启用动画; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 调用[CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)函数以启用或禁用动画。  
  
##  <a name="ismode2003"></a>  CMFCOutlookBarTabCtrl::IsMode2003  
 确定 Outlook 栏选项卡控件是否处于模拟 Microsoft Outlook 2003 模式。  
  
```  
BOOL IsMode2003() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果 Outlook 栏选项卡控件处于 Outlook 2003 模式;否则为`FALSE`;  
  
### <a name="remarks"></a>备注  
 此值将由[CMFCOutlookBar::SetMode2003](../../mfc/reference/cmfcoutlookbar-class.md#setmode2003)。  
  
##  <a name="onshowfewerpagebuttons"></a>  CMFCOutlookBarTabCtrl::OnShowFewerPageButtons  
 由框架调用以减少可见的选项卡页按钮的数目。  
  
```  
virtual void OnShowFewerPageButtons();
```  
  
### <a name="remarks"></a>备注  
 当调整控件的大小，此方法将调整显示页面选项卡按钮的数目。  
  
##  <a name="onshowmorepagebuttons"></a>  CMFCOutlookBarTabCtrl::OnShowMorePageButtons  
 由框架调用以增加可见的选项卡页按钮的数目。  
  
```  
virtual void OnShowMorePageButtons();
```  
  
### <a name="remarks"></a>备注  
 此方法调整时调整控件的大小可见的选项卡页按钮的数目。  
  
##  <a name="onshowoptions"></a>  CMFCOutlookBarTabCtrl::OnShowOptions  
 显示**导航窗格选项**对话框。  
  
```  
virtual void OnShowOptions();
```  
  
### <a name="remarks"></a>备注  
 **导航窗格选项**对话框允许用户选择的选项卡页按钮若要显示和它们的显示顺序。  
  
 由框架调用此方法，当用户选择**导航窗格选项**从控件的自定义菜单的菜单项。  
  
##  <a name="setactivetab"></a>  CMFCOutlookBarTabCtrl::SetActiveTab  
 设置活动选项卡。活动选项卡是处于打开状态，其可见的内容。  
  
```  
virtual BOOL SetActiveTab(int iTab);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 若要打开选项卡的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 非零，如果已成功，则打开指定的选项卡否则为 0。  
  
### <a name="remarks"></a>备注  
 设置活动选项卡上的视觉效果取决于您是否已启用动画。 有关详细信息，请参阅[CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)。  
  
##  <a name="setbordersize"></a>  CMFCOutlookBarTabCtrl::SetBorderSize  
 设置 Outlook 选项卡控件的边框大小。  
  
```  
void SetBorderSize(int nBorderSize);
```  
  
### <a name="parameters"></a>参数  
 [in] `nBorderSize`  
 以像素为单位指定新的边框大小。  
  
### <a name="remarks"></a>备注  
 设置新的边框大小并重新计算的 outlook 窗口布局。  
  
##  <a name="setpagebuttontextalign"></a>  CMFCOutlookBarTabCtrl::SetPageButtonTextAlign  
 在 Outlook 栏的选项卡按钮上设置的对齐方式的文本标签。  
  
```  
void SetPageButtonTextAlign(
    UINT uiAlign,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiAlign`  
 指定的文本对齐方式。  
  
 [in] `bRedraw`  
 如果`TRUE`，outlook 窗口将重绘。  
  
### <a name="remarks"></a>备注  
 此函数用于更改页按钮文本对齐方式。  
  
 `uiAlign` 可以是以下值之一：  
  
|返回的常量|含义|  
|--------------|-------------|  
|TA_LEFT|左的对齐|  
|TA_CENTER|居中对齐|  
|TA_RIGHT|右对齐|  
  
 默认值为 TA_CENTER。  
  
##  <a name="settoolbarimagelist"></a>  CMFCOutlookBarTabCtrl::SetToolbarImageList  
 设置包含在 Outlook 2003 模式下的 Outlook 栏底部显示的图标的位图。  
  
```  
BOOL SetToolbarImageList(
    UINT uiID,  
    int cx,  
    COLORREF clrTransp=RGB(255, 0, 255));
```  
  
### <a name="parameters"></a>参数  
 [in] `uiID`  
 指定要加载图像的资源 ID。  
  
 [in] `cx`  
 在映像列表中，以像素为单位指定图像的宽度。  
  
 [in] `clrTransp`  
 一个指定的透明颜色的 RGB 值。  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`如果成功; 否则返回`FALSE`。  
  
### <a name="remarks"></a>备注  
 此函数用于将附加图像列表将在 Microsoft Office 2003 模式下的工具栏按钮显示其映像。 映像索引应对应于页索引。  
  
 如果未在 Microsoft Office 2003 模式下，不应调用此方法。 有关详细信息，请参阅[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
##  <a name="setvisiblepagebuttons"></a>  CMFCOutlookBarTabCtrl::SetVisiblePageButtons  

  
```  
void SetVisiblePageButtons(int nVisiblePageButtons);
```  
  
### <a name="parameters"></a>参数  
 [in] `nVisiblePageButtons`  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)   
 [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CMFCOutlookBarPane 类](../../mfc/reference/cmfcoutlookbarpane-class.md)
