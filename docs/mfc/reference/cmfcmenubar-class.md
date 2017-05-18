---
title: "CMFCMenuBar 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCMenuBar
- AFXMENUBAR/CMFCMenuBar
- AFXMENUBAR/CMFCMenuBar::AdjustLocations
- AFXMENUBAR/CMFCMenuBar::AllowChangeTextLabels
- AFXMENUBAR/CMFCMenuBar::AllowShowOnPaneMenu
- AFXMENUBAR/CMFCMenuBar::CalcFixedLayout
- AFXMENUBAR/CMFCMenuBar::CalcLayout
- AFXMENUBAR/CMFCMenuBar::CalcMaxButtonHeight
- AFXMENUBAR/CMFCMenuBar::CanBeClosed
- AFXMENUBAR/CMFCMenuBar::CanBeRestored
- AFXMENUBAR/CMFCMenuBar::Create
- AFXMENUBAR/CMFCMenuBar::CreateEx
- AFXMENUBAR/CMFCMenuBar::CreateFromMenu
- AFXMENUBAR/CMFCMenuBar::EnableHelpCombobox
- AFXMENUBAR/CMFCMenuBar::EnableMenuShadows
- AFXMENUBAR/CMFCMenuBar::GetAvailableExpandSize
- AFXMENUBAR/CMFCMenuBar::GetColumnWidth
- AFXMENUBAR/CMFCMenuBar::GetDefaultMenu
- AFXMENUBAR/CMFCMenuBar::GetDefaultMenuResId
- AFXMENUBAR/CMFCMenuBar::GetFloatPopupDirection
- AFXMENUBAR/CMFCMenuBar::GetForceDownArrows
- AFXMENUBAR/CMFCMenuBar::GetHelpCombobox
- AFXMENUBAR/CMFCMenuBar::GetHMenu
- AFXMENUBAR/CMFCMenuBar::GetMenuFont
- AFXMENUBAR/CMFCMenuBar::GetMenuItem
- AFXMENUBAR/CMFCMenuBar::GetRowHeight
- AFXMENUBAR/CMFCMenuBar::GetSystemButton
- AFXMENUBAR/CMFCMenuBar::GetSystemButtonsCount
- AFXMENUBAR/CMFCMenuBar::GetSystemMenu
- AFXMENUBAR/CMFCMenuBar::HighlightDisabledItems
- AFXMENUBAR/CMFCMenuBar::IsButtonExtraSizeAvailable
- AFXMENUBAR/CMFCMenuBar::IsHighlightDisabledItems
- AFXMENUBAR/CMFCMenuBar::IsMenuShadows
- AFXMENUBAR/CMFCMenuBar::IsRecentlyUsedMenus
- AFXMENUBAR/CMFCMenuBar::IsShowAllCommands
- AFXMENUBAR/CMFCMenuBar::IsShowAllCommandsDelay
- AFXMENUBAR/CMFCMenuBar::LoadState
- AFXMENUBAR/CMFCMenuBar::OnChangeHot
- AFXMENUBAR/CMFCMenuBar::OnDefaultMenuLoaded
- AFXMENUBAR/CMFCMenuBar::OnSendCommand
- AFXMENUBAR/CMFCMenuBar::OnSetDefaultButtonText
- AFXMENUBAR/CMFCMenuBar::OnToolHitTest
- AFXMENUBAR/CMFCMenuBar::PreTranslateMessage
- AFXMENUBAR/CMFCMenuBar::RestoreOriginalstate
- AFXMENUBAR/CMFCMenuBar::SaveState
- AFXMENUBAR/CMFCMenuBar::SetDefaultMenuResId
- AFXMENUBAR/CMFCMenuBar::SetForceDownArrows
- AFXMENUBAR/CMFCMenuBar::SetMaximizeMode
- AFXMENUBAR/CMFCMenuBar::SetMenuButtonRTC
- AFXMENUBAR/CMFCMenuBar::SetMenuFont
- AFXMENUBAR/CMFCMenuBar::SetRecentlyUsedMenus
- AFXMENUBAR/CMFCMenuBar::SetShowAllCommands
dev_langs:
- C++
helpviewer_keywords:
- CMFCMenuBar class
ms.assetid: 8a3ce4c7-b012-4dc0-b4f8-53c10b4b86b8
caps.latest.revision: 36
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: ab2896f5ebab0df894f70e5ddb85bae3a5e1d5af
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcmenubar-class"></a>CMFCMenuBar 类
实现停靠的菜单栏。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCMenuBar : public CMFCToolbar  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCMenuBar::AdjustLocations](#adjustlocations)|（重写 `CMFCToolBar::AdjustLocations`。）|  
|[CMFCMenuBar::AllowChangeTextLabels](#allowchangetextlabels)|指定是否可以在工具栏按钮上的图像下，显示的文本标签。 (重写[CMFCToolBar::AllowChangeTextLabels](../../mfc/reference/cmfctoolbar-class.md#allowchangetextlabels)。)|  
|[CMFCMenuBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|（重写 `CPane::AllowShowOnPaneMenu`。）|  
|[CMFCMenuBar::CalcFixedLayout](#calcfixedlayout)|计算工具栏的水平大小。 (重写[CMFCToolBar::CalcFixedLayout](../../mfc/reference/cmfctoolbar-class.md#calcfixedlayout)。)|  
|[CMFCMenuBar::CalcLayout](#calclayout)|（重写 `CMFCToolBar::CalcLayout`。）|  
|[CMFCMenuBar::CalcMaxButtonHeight](#calcmaxbuttonheight)|计算按钮在工具栏中的最大高度。 (重写[CMFCToolBar::CalcMaxButtonHeight](../../mfc/reference/cmfctoolbar-class.md#calcmaxbuttonheight)。)|  
|[CMFCMenuBar::CanBeClosed](#canbeclosed)|指定用户是否可以关闭工具栏。 (重写[CMFCToolBar::CanBeClosed](../../mfc/reference/cmfctoolbar-class.md#canbeclosed)。)|  
|[CMFCMenuBar::CanBeRestored](#canberestored)|确定是否系统可以将工具栏恢复到其原始状态在自定义之后。 (重写[CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored)。)|  
|[CMFCMenuBar::Create](#create)|创建菜单控件，并将其附加到`CMFCMenuBar`对象。|  
|[CMFCMenuBar::CreateEx](#createex)|创建`CMFCMenuBar`具有其他样式选项对象。|  
|[CMFCMenuBar::CreateFromMenu](#createfrommenu)|初始化`CMFCMenuBar`对象。 接受`HMENU`参数，它就像一个模板，用于填充`CMFCMenuBar`。|  
|[CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox)|使**帮助**位于菜单栏右侧的组合框。|  
|[CMFCMenuBar::EnableMenuShadows](#enablemenushadows)|指定是否显示阴影对于弹出菜单。|  
|[CMFCMenuBar::GetAvailableExpandSize](#getavailableexpandsize)|(重写[CPane::GetAvailableExpandSize](../../mfc/reference/cpane-class.md#getavailableexpandsize)。)|  
|[CMFCMenuBar::GetColumnWidth](#getcolumnwidth)|返回工具栏按钮的宽度。 (重写[CMFCToolBar::GetColumnWidth](../../mfc/reference/cmfctoolbar-class.md#getcolumnwidth)。)|  
|[CMFCMenuBar::GetDefaultMenu](#getdefaultmenu)|资源文件中的原始菜单中返回的句柄。|  
|[CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid)|返回资源文件中的原始菜单上的资源标识符。|  
|[CMFCMenuBar::GetFloatPopupDirection](#getfloatpopupdirection)||  
|[CMFCMenuBar::GetForceDownArrows](#getforcedownarrows)||  
|[CMFCMenuBar::GetHelpCombobox](#gethelpcombobox)|返回一个指向**帮助**组合框。|  
|[CMFCMenuBar::GetHMenu](#gethmenu)|返回到附加到菜单的句柄`CMFCMenuBar`对象。|  
|[CMFCMenuBar::GetMenuFont](#getmenufont)|返回菜单对象的当前全局字体。|  
|[CMFCMenuBar::GetMenuItem](#getmenuitem)|返回与提供的项索引关联的工具栏按钮。|  
|[CMFCMenuBar::GetRowHeight](#getrowheight)|返回工具栏按钮的高度。 (重写[CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight)。)|  
|[CMFCMenuBar::GetSystemButton](#getsystembutton)||  
|[CMFCMenuBar::GetSystemButtonsCount](#getsystembuttonscount)||  
|[CMFCMenuBar::GetSystemMenu](#getsystemmenu)||  
|[CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems)|指示是否禁用的菜单项被突出显示。|  
|[CMFCMenuBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|确定工具栏上是否可以显示已扩展边框的按钮。 (重写[CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable)。)|  
|[CMFCMenuBar::IsHighlightDisabledItems](#ishighlightdisableditems)|指示是否突出显示已禁用的项。|  
|[CMFCMenuBar::IsMenuShadows](#ismenushadows)|指示绘制阴影时是否对于弹出菜单。|  
|[CMFCMenuBar::IsRecentlyUsedMenus](#isrecentlyusedmenus)|指示是否在菜单栏上显示最近使用的菜单命令。|  
|[CMFCMenuBar::IsShowAllCommands](#isshowallcommands)|指示弹出菜单显示的所有命令。|  
|[CMFCMenuBar::IsShowAllCommandsDelay](#isshowallcommandsdelay)|指示菜单一小段延迟后显示的所有命令。|  
|[CMFCMenuBar::LoadState](#loadstate)|加载的状态`CMFCMenuBar`注册表中的对象。|  
|[CMFCMenuBar::OnChangeHot](#onchangehot)|在用户选择工具栏上的按钮时由框架调用。 (重写[CMFCToolBar::OnChangeHot](../../mfc/reference/cmfctoolbar-class.md#onchangehot)。)|  
|[CMFCMenuBar::OnDefaultMenuLoaded](#ondefaultmenuloaded)|框架窗口从资源文件加载默认菜单时由框架调用。|  
|[CMFCMenuBar::OnSendCommand](#onsendcommand)|（重写 `CMFCToolBar::OnSendCommand`。）|  
|[CMFCMenuBar::OnSetDefaultButtonText](#onsetdefaultbuttontext)|如果菜单是自定义模式，并且在用户更改菜单项的文本由框架调用。|  
|[CMFCMenuBar::OnToolHitTest](#ontoolhittest)|（重写 `CMFCToolBar::OnToolHitTest`。）|  
|[CMFCMenuBar::PreTranslateMessage](#pretranslatemessage)|（重写 `CMFCToolBar::PreTranslateMessage`。）|  
|[CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate)|如果菜单是自定义模式，并且用户选择由框架调用**重置**菜单栏。|  
|[CMFCMenuBar::SaveState](#savestate)|保存的状态`CMFCMenuBar`对注册表的对象。|  
|[CMFCMenuBar::SetDefaultMenuResId](#setdefaultmenuresid)|将原始菜单上设置的资源文件中。|  
|[CMFCMenuBar::SetForceDownArrows](#setforcedownarrows)||  
|[CMFCMenuBar::SetMaximizeMode](#setmaximizemode)|当 MDI 子窗口更改其显示模式时，由框架调用。 如果 MDI 子窗口新最大化或不再最大化，此方法将更新菜单栏。|  
|[CMFCMenuBar::SetMenuButtonRTC](#setmenubuttonrtc)|设置用户动态创建菜单按钮时，将生成的运行时类信息。|  
|[CMFCMenuBar::SetMenuFont](#setmenufont)|设置应用程序中的所有菜单的字体。|  
|[CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus)|指定是否显示最近使用的菜单命令时的菜单栏。|  
|[CMFCMenuBar::SetShowAllCommands](#setshowallcommands)|指定是否在菜单栏显示所有命令。|  
  
## <a name="remarks"></a>备注  
 `CMFCMenuBar`类是实现停靠的功能的菜单栏。 它类似于一个工具栏，尽管它不能关闭-始终显示。  
  
 `CMFCMenuBar`支持显示最近使用的菜单项对象的选项。 如果启用此选项，`CMFCMenuBar`上第一次查看显示可用命令的一个子集。 此后，最近使用的命令会显示以及原始命令子集。 此外，用户始终可以展开要查看所有可用命令的菜单。 因此，不断，显示或显示仅当最近所选配置每个可用命令。  
  
 若要使用`CMFCMenuBar`对象，请将其嵌入在主窗口框架对象中。 在处理时`WM_CREATE`消息，请调用`CMFCMenuBar::Create`或`CMFCMenuBar::CreateEx`。 而不考虑其来创建函数，您使用，在一个指针将传递给主框架窗口。 然后，启用通过调用停靠[cframewndex:: Enabledocking](../../mfc/reference/cframewndex-class.md#enabledocking)。 通过调用停靠此菜单[CFrameWndEx::DockPane](../../mfc/reference/cframewndex-class.md#dockpane)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCMenuBar`类。 该示例演示如何将窗格中的样式设置，启用自定义按钮启用帮助框、 弹出菜单的阴影和更新菜单栏。 此代码段属于[IE 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_IEDemo #&1;](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo #&3;](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 `CMFCMenuBar`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxmenubar.h  
  
##  <a name="adjustlocations"></a>CMFCMenuBar::AdjustLocations  
 调整在菜单栏上的菜单项的位置。  
  
```  
virtual void AdjustLocations();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="allowchangetextlabels"></a>CMFCMenuBar::AllowChangeTextLabels  
 确定是否在菜单栏中的图像下，允许文本标签。  
  
```  
virtual BOOL AllowChangeTextLabels() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`如果用户可以选择显示在图像下的文本标签。  
  
### <a name="remarks"></a>备注  
  
##  <a name="allowshowonpanemenu"></a>CMFCMenuBar::AllowShowOnPaneMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="calcfixedlayout"></a>CMFCMenuBar::CalcFixedLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>参数  
 [in] `bStretch`  
 [in] `bHorz`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="calclayout"></a>CMFCMenuBar::CalcLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize CalcLayout(
    DWORD dwMode,  
    int nLength = -1);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwMode`  
 [in] `nLength`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="calcmaxbuttonheight"></a>CMFCMenuBar::CalcMaxButtonHeight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int CalcMaxButtonHeight();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="canbeclosed"></a>CMFCMenuBar::CanBeClosed  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanBeClosed() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="canberestored"></a>CMFCMenuBar::CanBeRestored  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanBeRestored() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="create"></a>CMFCMenuBar::Create  
 创建菜单控件，并将其附加到[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,  
    UINT nID = AFX_IDW_MENUBAR);
```  
  
### <a name="parameters"></a>参数  
 [in] `pParentWnd`  
 指向新的父窗口`CMFCMenuBar`对象。  
  
 [in] `dwStyle`  
 新的菜单栏的样式。  
  
 [in] `nID`  
 菜单栏的子窗口 ID。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 `TRUE`；否则为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 在构造之后`CMFCMenuBar`对象时，必须调用`Create`。 此方法创建`CMFCMenuBar`控件并将其附加到`CMFCMenuBar`对象。  
  
 关于工具栏样式的详细信息，请参阅[CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle)。  
  
##  <a name="createex"></a>CMFCMenuBar::CreateEx  
 创建[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)具有指定的扩展样式对象。  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = TBSTYLE_FLAT,  
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,  
    CRect rcBorders = CRect(1,
    1,
    1,
    1),  
    UINT nID =AFX_IDW_MENUBAR);
```  
  
### <a name="parameters"></a>参数  
 [in] `pParentWnd`  
 指向新的父窗口`CMFCMenuBar`对象。  
  
 [in] `dwCtrlStyle`  
 新的菜单栏的的其他样式。  
  
 [in] `dwStyle`  
 新的菜单栏主样式。  
  
 [in] `rcBorders`  
 一个`CRect`参数指定的边框的大小`CMFCMenuBar`对象。  
  
 [in] `nID`  
 菜单栏的子窗口 ID。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 应使用此函数，而不是[CMFCMenuBar::Create](#create)如果想要指定除了工具栏样式的样式。 有些常用的其他样式并`TBSTYLE_TRANSPARENT`和`CBRS_TOP`。  
  
 有关其他样式的列表，请参阅[工具栏控件和按钮样式](http://msdn.microsoft.com/library/windows/desktop/bb760439)，[常见控件样式](http://msdn.microsoft.com/library/windows/desktop/bb775498)，和[常见的窗口样式](http://msdn.microsoft.com/library/windows/desktop/ms632600)。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`CreateEx`方法`CMFCMenuBar`类。 此代码段属于[IE 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_IEDemo #&1;](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo #&2;](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_3.cpp)]  
  
##  <a name="createfrommenu"></a>CMFCMenuBar::CreateFromMenu  
 初始化[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象。 此方法模型`CMFCMenuBar`对象后`HMENU`参数。  
  
```  
virtual void CreateFromMenu(
    HMENU hMenu,  
    BOOL bDefaultMenu = FALSE,  
    BOOL bForceUpdate = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `hMenu`  
 菜单资源的句柄。 `CreateFromMenu`使用此资源的模板作为`CMFCMenuBar`。  
  
 [in] `bDefaultMenu`  
 一个布尔值，该值指示新菜单是否为默认菜单。  
  
 [in] `bForceUpdate`  
 一个布尔值，该值指示是否强制菜单更新，此方法。  
  
### <a name="remarks"></a>备注  
 如果您希望能够为菜单资源的同一个菜单项的菜单控件，请使用此方法。 在调用任何一个后调用此方法[CMFCMenuBar::Create](#create)或[CMFCMenuBar::CreateEx](#createex)。  
  
##  <a name="enablehelpcombobox"></a>CMFCMenuBar::EnableHelpCombobox  
 使**帮助**位于菜单栏右侧的组合框。  
  
```  
void EnableHelpCombobox(
    UINT uiID,  
    LPCTSTR lpszPrompt = NULL,  
    int nComboBoxWidth = 150);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiID`  
 的按钮的命令 ID**帮助**组合框。  
  
 [in] `lpszPrompt`  
 一个字符串，包含框架是否为空且未处于活动状态的组合框中显示的文本。 例如，"输入文本在此处"。  
  
 [in] `nComboBoxWidth`  
 以像素为单位组合框按钮的宽度。  
  
### <a name="remarks"></a>备注  
 **帮助**组合框类似于**帮助**组合框中的菜单栏[!INCLUDE[ofprword](../../mfc/reference/includes/ofprword_md.md)]。  
  
 当您调用此方法与`uiID`设置为 0，此方法会隐藏组合框。 否则，此方法的组合框自动显示在菜单栏的右侧。 调用此方法后，调用[CMFCMenuBar::GetHelpCombobox](#gethelpcombobox)以获取指向插入[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)对象。  
  
##  <a name="enablemenushadows"></a>CMFCMenuBar::EnableMenuShadows  
 使弹出菜单的阴影。  
  
```  
static void EnableMenuShadows(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 一个布尔型参数，该值指示阴影是否应启用弹出菜单。  
  
### <a name="remarks"></a>备注  
 此方法使用的算法很复杂，可能会降低速度较慢的系统上的应用程序的性能。  
  
##  <a name="getavailableexpandsize"></a>CMFCMenuBar::GetAvailableExpandSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetAvailableExpandSize() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcolumnwidth"></a>CMFCMenuBar::GetColumnWidth  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetColumnWidth() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getdefaultmenu"></a>CMFCMenuBar::GetDefaultMenu  
 检索原始菜单上的句柄。 框架将从资源文件加载原始菜单。  
  
```  
HMENU GetDefaultMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
 菜单资源的句柄。  
  
### <a name="remarks"></a>备注  
 如果您的应用程序自定义了一个菜单，您可以使用此方法来检索原始菜单上的句柄。  
  
##  <a name="getdefaultmenuresid"></a>CMFCMenuBar::GetDefaultMenuResId  
 检索默认菜单上的资源标识符。  
  
```  
UINT GetDefaultMenuResId() const;  
```  
  
### <a name="return-value"></a>返回值  
 菜单资源标识符。  
  
### <a name="remarks"></a>备注  
 框架将加载的默认菜单`CMFCMenuBar`资源文件中的对象。  
  
##  <a name="getfloatpopupdirection"></a>CMFCMenuBar::GetFloatPopupDirection  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetFloatPopupDirection(CMFCToolBarMenuButton* pButton);
```  
  
### <a name="parameters"></a>参数  
 [in] `pButton`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getforcedownarrows"></a>CMFCMenuBar::GetForceDownArrows  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL GetForceDownArrows();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="gethelpcombobox"></a>CMFCMenuBar::GetHelpCombobox  
 返回一个指向**帮助**组合框。  
  
```  
CMFCToolBarComboBoxButton* GetHelpCombobox();
```  
  
### <a name="return-value"></a>返回值  
 一个指向**帮助**组合框。 `NULL`如果**帮助**组合框中处于隐藏或未启用。  
  
### <a name="remarks"></a>备注  
 **帮助**组合框位于菜单栏的右侧。 调用方法[CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox)若要启用此组合框。  
  
##  <a name="gethmenu"></a>CMFCMenuBar::GetHMenu  
 检索到附加到菜单的句柄[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象。  
  
```  
HMENU GetHMenu() const;  
```  
  
##  <a name="getmenufont"></a>CMFCMenuBar::GetMenuFont  
 检索当前的菜单字体。  
  
```  
static const CFont& GetMenuFont(BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bHorz`  
 一个布尔型参数，用于指定是否返回水平或垂直字体。 `TRUE`指示水平字体。  
  
### <a name="return-value"></a>返回值  
 一个指向[CFont](../../mfc/reference/cfont-class.md)参数，其中包含当前的菜单栏字体。  
  
### <a name="remarks"></a>备注  
 返回的字体是应用程序的全局参数。 两种全局字体针对所有维护`CMFCMenuBar`对象。 这些单独的字体用于水平和垂直菜单栏。  
  
##  <a name="getmenuitem"></a>CMFCMenuBar::GetMenuItem  
 检索[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)根据项索引在菜单栏上的对象。  
  
```  
CMFCToolBarButton* GetMenuItem(int iItem) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iItem`  
 要返回的菜单项的索引。  
  
### <a name="return-value"></a>返回值  
 一个指向`CMFCToolBarButton`匹配由指定的索引对象`iItem`。 `NULL`如果索引无效。  
  
##  <a name="getrowheight"></a>CMFCMenuBar::GetRowHeight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetRowHeight() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getsystembutton"></a>CMFCMenuBar::GetSystemButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCToolBarMenuButtonsButton* GetSystemButton(
    UINT uiBtn,  
    BOOL bByCommand = TRUE) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `uiBtn`  
 [in] `bByCommand`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getsystembuttonscount"></a>CMFCMenuBar::GetSystemButtonsCount  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetSystemButtonsCount() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getsystemmenu"></a>CMFCMenuBar::GetSystemMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCToolBarSystemMenuButton* GetSystemMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="highlightdisableditems"></a>CMFCMenuBar::HighlightDisabledItems  
 控制是否将框架突出显示禁用的菜单项。  
  
```  
static void HighlightDisabledItems(BOOL bHighlight = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bHighlight`  
 一个布尔型参数，该值指示是否将框架突出显示不可用的菜单项。  
  
### <a name="remarks"></a>备注  
 默认情况下，框架不突出显示不可用的菜单项时用户将鼠标指针定位在其上。  
  
##  <a name="isbuttonextrasizeavailable"></a>CMFCMenuBar::IsButtonExtraSizeAvailable  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsButtonExtraSizeAvailable() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="ishighlightdisableditems"></a>CMFCMenuBar::IsHighlightDisabledItems  
 指示是否将框架突出显示不可用的菜单项。  
  
```  
static BOOL IsHighlightDisabledItems();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果不可用的菜单项突出显示;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 默认情况下，框架不突出显示不可用的菜单项时用户将鼠标指针定位在其上。 使用[CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems)方法，以启用此功能。  
  
##  <a name="ismenushadows"></a>CMFCMenuBar::IsMenuShadows  
 指示框架是否绘制阴影的弹出菜单。  
  
```  
static BOOL IsMenuShadows();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果框架绘制菜单阴影;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用[CMFCMenuBar::EnableMenuShadows](#enablemenushadows)方法来启用或禁用此功能。  
  
##  <a name="isrecentlyusedmenus"></a>CMFCMenuBar::IsRecentlyUsedMenus  
 指示是否在菜单栏上显示最近使用的菜单命令。  
  
```  
static BOOL IsRecentlyUsedMenus();
```  
  
### <a name="return-value"></a>返回值  
 如果非零`CMFCMenuBar`对象会显示最近使用菜单命令; 否则为 0。  
  
### <a name="remarks"></a>备注  
 使用函数[CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus)来控制菜单栏显示最近使用过的菜单命令。  
  
##  <a name="isshowallcommands"></a>CMFCMenuBar::IsShowAllCommands  
 指示菜单显示的所有命令。  
  
```  
static BOOL IsShowAllCommands();
```  
  
### <a name="return-value"></a>返回值  
 如果非零`CMFCMenuBar`显示所有命令; 否则为 0。  
  
### <a name="remarks"></a>备注  
 一个`CMFCMenuBar`对象可以进行配置以显示所有命令或仅都显示一部分的命令。 有关此功能的详细信息，请参阅[CMFCMenuBar 类](../../mfc/reference/cmfcmenubar-class.md)。  
  
 `IsShowAllCommands`将告诉您如何将此功能配置为`CMFCMenuBar`对象。 若要控制显示的菜单命令，请使用方法[CMFCMenuBar::SetShowAllCommands](#setshowallcommands)和[CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus)。  
  
##  <a name="isshowallcommandsdelay"></a>CMFCMenuBar::IsShowAllCommandsDelay  
 指示是否[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象在一小段延迟后显示的所有命令。  
  
```  
static BOOL IsShowAllCommandsDelay();
```  
  
### <a name="return-value"></a>返回值  
 如果菜单栏中显示整个菜单在短暂的延迟; 之后，非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 在配置给显示最近使用过的项的菜单栏时，菜单栏中显示完整菜单中两种方式之一︰  
  
-   当用户悬停在菜单底部的箭头光标从编程的延迟后会显示完整的菜单。  
  
-   在用户单击菜单底部的箭头后会显示完整的菜单。  
  
 默认情况下，所有`CMFCMenuBar`对象使用的选项可一小段延迟后显示完整菜单。 此选项不能以编程方式在更改`CMFCMenuBar`类。 但是，用户可以通过更改行为工具栏自定义期间使用**自定义**对话框...  
  
##  <a name="loadstate"></a>CMFCMenuBar::LoadState  
 从 Windows 注册表加载的菜单栏的状态。  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT)-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszProfileName`  
 一个字符串，包含 Windows 注册表项的路径。  
  
 [in] `nIndex`  
 菜单栏控件 ID。  
  
 [in] `uiID`  
 保留的值。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法已成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用[CMFCMenuBar::SaveState](#savestate)方法将菜单栏的状态保存到注册表。 已保存的信息包括菜单项、 停靠状态和菜单栏的位置。  
  
 在大多数情况下您的应用程序不会调用`LoadState`。 在初始化工作区时，框架将调用此方法。  
  
##  <a name="onchangehot"></a>CMFCMenuBar::OnChangeHot  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnChangeHot(int iHot);
```  
  
### <a name="parameters"></a>参数  
 [in] `iHot`  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondefaultmenuloaded"></a>CMFCMenuBar::OnDefaultMenuLoaded  
 从资源文件加载的菜单资源时，框架将调用此方法。  
  
```  
virtual void OnDefaultMenuLoaded(HMENU hMenu);
```  
  
### <a name="parameters"></a>参数  
 [in] `hMenu`  
 菜单上的句柄附加到`CMFCMenuBar`对象。  
  
### <a name="remarks"></a>备注  
 此函数的默认实现不执行任何操作。 重写此函数后要执行自定义代码框架从资源文件加载的菜单资源。  
  
##  <a name="onsendcommand"></a>CMFCMenuBar::OnSendCommand  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>参数  
 [in] `pButton`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="onsetdefaultbuttontext"></a>CMFCMenuBar::OnSetDefaultButtonText  
 在用户更改某一项在菜单栏上的文本时，框架将调用此方法。  
  
```  
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>参数  
 [in] `pButton`  
 一个指向[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)用户想要自定义的对象。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果该框架将用户更改应用于菜单栏中。否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法的默认实现为用户提供的文本更改按钮的文本。  
  
##  <a name="ontoolhittest"></a>CMFCMenuBar::OnToolHitTest  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual INT_PTR OnToolHitTest(
    CPoint point,  
    TOOLINFO* pTI) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 [in] `pTI`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="pretranslatemessage"></a>CMFCMenuBar::PreTranslateMessage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>参数  
 [in] `pMsg`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="restoreoriginalstate"></a>CMFCMenuBar::RestoreOriginalstate  
 当用户选择由框架调用**重置**从**自定义**对话框。  
  
```  
virtual BOOL RestoreOriginalstate();
```  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 当用户选择调用此方法**重置**从自定义菜单。 您可以手动调用此方法以编程方式重置菜单栏的状态。 此方法从资源文件加载的原始状态。  
  
 重写此方法，如果您想要执行任何处理，当用户选择**重置**选项。  
  
##  <a name="savestate"></a>CMFCMenuBar::SaveState  
 保存的状态[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象传递给 Windows 注册表。  
  
```  
virtual BOOL SaveState (
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT)-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszProfileName`  
 一个字符串，包含 Windows 注册表项的路径。  
  
 [in] `nIndex`  
 菜单栏控件 ID。  
  
 [in] `uiID`  
 保留的值。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则，否则为`FALSE`;  
  
### <a name="remarks"></a>备注  
 通常情况下，您的应用程序不会调用`SaveState`。 工作区进行序列化时，框架将调用此方法。 有关详细信息，请参阅[CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate)。  
  
 已保存的信息包括菜单项、 停靠状态和菜单栏的位置。  
  
##  <a name="setdefaultmenuresid"></a>CMFCMenuBar::SetDefaultMenuResId  
 设置的默认菜单[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)对象根据资源 id。  
  
```  
void SetDefaultMenuResId(UINT uiResId);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiResId`  
 新的默认菜单资源 ID。  
  
### <a name="remarks"></a>备注  
 [CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate)方法从资源文件中还原默认的菜单。  
  
 使用[CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid)方法来检索默认菜单，而不将其还原。  
  
##  <a name="setforcedownarrows"></a>CMFCMenuBar::SetForceDownArrows  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetForceDownArrows(BOOL bValue);
```  
  
### <a name="parameters"></a>参数  
 [in] `bValue`  
  
### <a name="remarks"></a>备注  
  
##  <a name="setmaximizemode"></a>CMFCMenuBar::SetMaximizeMode  
 当 MDI 更改其显示模式，并且必须更新菜单栏时，框架将调用此方法。  
  
```  
void SetMaximizeMode(
    BOOL bMax,  
    CWnd* pWnd = NULL,  
    BOOL bRecalcLayout = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bMax`  
 一个布尔值，指定的模式。 有关详细信息，请参阅备注部分。  
  
 [in] `pWnd`  
 指向要更改的 MDI 子窗口的指针。  
  
 [in] `bRecalcLayout`  
 一个布尔值，指定是否应立即计算菜单栏的布局。  
  
### <a name="remarks"></a>备注  
 当 MDI 子窗口最大化窗口时、 附加到 MDI 主框架窗口的菜单栏显示系统菜单和**最小化**，**最大化**和**关闭**按钮。 如果`bMax`是`TRUE`和`pWnd`不是`NULL`、 最大化 MDI 子窗口和菜单栏中必须加入额外的控件。 否则，菜单栏返回到其正常状态。  
  
##  <a name="setmenubuttonrtc"></a>CMFCMenuBar::SetMenuButtonRTC  
 设置在用户创建菜单按钮时会使用该框架的运行时类信息。  
  
```  
void SetMenuButtonRTC(CRuntimeClass* pMenuButtonRTC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pMenuButtonRTC`  
 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)类信息派生自[CMFCMenuButton 类](../../mfc/reference/cmfcmenubutton-class.md)。  
  
### <a name="remarks"></a>备注  
 当用户将新按钮添加到菜单栏时，框架会动态地创建按钮。 默认情况下，它会创建`CMFCMenuButton`对象。 重写此方法以更改按钮在框架创建的对象的类型。  
  
##  <a name="setmenufont"></a>CMFCMenuBar::SetMenuFont  
 在您的应用程序中设置的所有菜单栏的字体。  
  
```  
static BOOL SetMenuFont(
    LPLOGFONT lpLogFont,  
    BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpLogFont`  
 一个指向[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/bb773327)结构，它定义要设置的字体。  
  
 [in] `bHorz`  
 如果您希望为`lpLogFont`参数，以使用垂直字体，FALSE，如果您希望其可用于水平字体。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法已成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 两种字体用于所有`CMFCMenuBar`对象。 这些单独的字体用于水平和垂直菜单栏。  
  
 字体设置是全局变量，并影响所有`CMFCMenuBar`对象。  
  
##  <a name="setrecentlyusedmenus"></a>CMFCMenuBar::SetRecentlyUsedMenus  
 控制是否菜单栏显示最近使用过的菜单命令。  
  
```  
static void SetRecentlyUsedMenus (BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bOn`  
 一个布尔值，控制是否显示最近使用的菜单命令。  
  
##  <a name="setshowallcommands"></a>CMFCMenuBar::SetShowAllCommands  
 控制菜单是否显示所有可用的命令。  
  
```  
static void SetShowAllCommands(BOOL bShowAllCommands = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bShowAllCommands`  
 一个布尔型参数，指定是否弹出菜单显示的所有菜单命令。  
  
### <a name="remarks"></a>备注  
 如果菜单未显示的所有菜单命令，它会隐藏很少使用的命令。 有关显示菜单命令的详细信息，请参阅[CMFCMenuBar 类](../../mfc/reference/cmfcmenubar-class.md)。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)

