---
title: "CStatusBar 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStatusBar
- AFXEXT/CStatusBar
- AFXEXT/CStatusBar::CStatusBar
- AFXEXT/CStatusBar::CommandToIndex
- AFXEXT/CStatusBar::Create
- AFXEXT/CStatusBar::CreateEx
- AFXEXT/CStatusBar::DrawItem
- AFXEXT/CStatusBar::GetItemID
- AFXEXT/CStatusBar::GetItemRect
- AFXEXT/CStatusBar::GetPaneInfo
- AFXEXT/CStatusBar::GetPaneStyle
- AFXEXT/CStatusBar::GetPaneText
- AFXEXT/CStatusBar::GetStatusBarCtrl
- AFXEXT/CStatusBar::SetIndicators
- AFXEXT/CStatusBar::SetPaneInfo
- AFXEXT/CStatusBar::SetPaneStyle
- AFXEXT/CStatusBar::SetPaneText
dev_langs:
- C++
helpviewer_keywords:
- indicators, status bar
- CStatusBar class
- status bars
- indicators
- status indicators
ms.assetid: a3bde3db-e71c-4881-a3ca-1d5481c345ba
caps.latest.revision: 24
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
ms.openlocfilehash: e96070041ef5bcee0865991a14b6484082d8fc91
ms.lasthandoff: 02/24/2017

---
# <a name="cstatusbar-class"></a>CStatusBar 类
含有文本输出窗格或“指示符”的控件条。  
  
## <a name="syntax"></a>语法  
  
```  
class CStatusBar : public CControlBar  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CStatusBar::CStatusBar](#cstatusbar)|构造 `CStatusBar` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CStatusBar::CommandToIndex](#commandtoindex)|获取索引为一个给定的指示符 id。|  
|[CStatusBar::Create](#create)|创建状态栏，并将其附加到`CStatusBar`对象，并将设置初始的字体和栏高度。|  
|[CStatusBar::CreateEx](#createex)|创建`CStatusBar`具有其他样式为嵌入对象`CStatusBarCtrl`对象。|  
|[CStatusBar::DrawItem](#drawitem)|当所有者描述状态栏控件会发生变化的可视方位时调用。|  
|[CStatusBar::GetItemID](#getitemid)|获取给定索引的指示符 ID。|  
|[CStatusBar::GetItemRect](#getitemrect)|获取显示给定索引的矩形。|  
|[CStatusBar::GetPaneInfo](#getpaneinfo)|获取给定索引的指标 ID、 样式和宽度。|  
|[CStatusBar::GetPaneStyle](#getpanestyle)|获取给定索引的指示器样式。|  
|[CStatusBar::GetPaneText](#getpanetext)|指示器文本获取给定的索引。|  
|[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)|允许直接访问基础的公共控件。|  
|[CStatusBar::SetIndicators](#setindicators)|设置指示符 Id。|  
|[CStatusBar::SetPaneInfo](#setpaneinfo)|设置指标 ID、 样式和宽度为给定的索引。|  
|[CStatusBar::SetPaneStyle](#setpanestyle)|设置给定索引的指示器样式。|  
|[CStatusBar::SetPaneText](#setpanetext)|设置给定索引的指示器文本。|  
  
## <a name="remarks"></a>备注  
 输出窗格通常用作消息行和状态指示器使用。 示例包括菜单帮助消息行简短解释了选定的菜单命令和指示器显示 SCROLL LOCK、 NUM LOCK 和其他键的状态。  
  
 [CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)，成员函数新增到 MFC 4.0，让您充分利用状态栏自定义项和其他功能的 Windows 公共控件的支持。 `CStatusBar`成员函数为您提供的大多数 Windows 公共控件; 功能但是，当您调用`GetStatusBarCtrl`，您可以为您状态栏更多 Windows 95/98 状态栏的特征。 当您调用`GetStatusBarCtrl`，它将返回到引用`CStatusBarCtrl`对象。 请参阅[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)有关设计使用 Windows 公共控件的工具栏的详细信息。 关于公共控件的详细信息，请参阅[公共控件](http://msdn.microsoft.com/library/windows/desktop/bb775493)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 框架将指示器信息存储在具有最左侧指示器位置 0 处的数组。 当您创建一个状态栏时，您使用框架将与相应的指示符相关联的 Id 的字符串的数组。 然后可以使用字符串 ID 或索引访问指示器。  
  
 默认情况下，第一个标记是"弹性": 它占用其他指示器窗格，请不使用的状态栏的长度，以使其他窗格右对齐。  
  
 若要创建一个状态栏，请按照下列步骤︰  
  
1.  构造 `CStatusBar` 对象。  
  
2.  调用[创建](#create)(或[CreateEx](#createex)) 函数来创建状态栏窗口中，并将其附加到`CStatusBar`对象。  
  
3.  调用[SetIndicators](#setindicators)将字符串 ID 与每个指示器相关联。  
  
 有三种方法来更新状态栏窗格中的文本︰  
  
1.  调用[CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)更新在仅限窗格 0 中的文本。  
  
2.  调用[CCmdUI::SetText](../../mfc/reference/ccmdui-class.md#settext)中状态栏的`ON_UPDATE_COMMAND_UI`处理程序。  
  
3.  调用[SetPaneText](#setpanetext)更新任意一个窗格的文本。  
  
 调用[SetPaneStyle](#setpanestyle)更新状态栏窗格的样式。  
  
 有关详细信息使用`CStatusBar`，请参阅文章[MFC 中的状态栏实现](../../mfc/status-bar-implementation-in-mfc.md)和[技术说明 31︰ 控件条](../../mfc/tn031-control-bars.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CStatusBar`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxext.h  
  
##  <a name="commandtoindex"></a>CStatusBar::CommandToIndex  
 获取给定 ID 的指示器索引  
  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIDFind`  
 字符串的索引是要从中检索的指标的 ID。  
  
### <a name="return-value"></a>返回值  
 如果成功，则该标记的索引如果未成功，则为 –&1;。  
  
### <a name="remarks"></a>备注  
 第一个指示器的索引为 0。  
  
##  <a name="create"></a>CStatusBar::Create  
 创建状态栏 （子窗口），并将其与`CStatusBar`对象。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>参数  
 `pParentWnd`  
 指向[CWnd](../../mfc/reference/cwnd-class.md)对象，其 Windows 窗口是状态栏的父级。  
  
 `dwStyle`  
 状态栏样式。 除了标准的 Windows[样式](../../mfc/reference/window-styles.md)，支持这些样式。  
  
- `CBRS_TOP`控件条是在框架窗口的顶部。  
  
- `CBRS_BOTTOM`控件条是在框架窗口的底部。  
  
- `CBRS_NOALIGN`父级调整大小时，则不会重新定位控件条。  
  
 `nID`  
 工具栏上的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此外设置初始字体并将状态设置为默认值的栏的高度。  
  
##  <a name="createex"></a>CStatusBar::CreateEx  
 调用此函数可创建一个状态栏 （子窗口） 并将其与关联`CStatusBar`对象。  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = 0,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>参数  
 `pParentWnd`  
 指向[CWnd](../../mfc/reference/cwnd-class.md)对象，其 Windows 窗口是状态栏的父级。  
  
 `dwCtrlStyle`  
 适用于创建嵌入其他样式[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)对象。 默认值指定一个状态栏，而无需大小调整手柄或工具提示支持。 支持的状态栏样式包括︰  
  
- **SBARS_SIZEGRIP**状态栏控件包括在右端状态栏的大小调整手柄。 大小调整手柄类似于大小调整边框；它是用户可以通过单击和拖动来重设父窗口大小的矩形区域。  
  
- **SBT_TOOLTIPS**状态栏支持工具提示。  
  
 有关这些样式的详细信息，请参阅[CStatusBarCtrl 的设置](../../mfc/settings-for-the-cstatusbarctrl.md)。  
  
 `dwStyle`  
 状态栏样式。 默认值指定在框架窗口的底部创建一个可见的状态栏。 应用状态栏控件样式中列出的任意组合[窗口样式](../../mfc/reference/window-styles.md)和[CDialogBar::Create](../../mfc/reference/cdialogbar-class.md#create)。 但是，此参数应始终包括 WS_CHILD 和 WS_VISIBLE 样式。  
  
 `nID`  
 状态栏的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数还设置初始字体并将状态设置为默认值的栏的高度。  
  
 使用`CreateEx`，而不是[创建](#create)，当某些样式需要在嵌入式的状态栏控件的创建过程。 例如，设置`dwCtrlStyle`到**SBT_TOOLTIPS**中的状态栏对象显示工具提示。  
  
##  <a name="cstatusbar"></a>CStatusBar::CStatusBar  
 构造`CStatusBar`对象，创建一个默认状态栏的字体，如有必要，并为默认值设置的字体特征。  
  
```  
CStatusBar();
```  
  
##  <a name="drawitem"></a>CStatusBar::DrawItem  
 当所有者描述的状态栏会发生变化的可视方位框架调用此成员函数。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpDrawItemStruct`  
 一个指向[DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802)结构，其中包含有关所需的绘图类型的信息。  
  
### <a name="remarks"></a>备注  
 **ItemAction**的成员`DRAWITEMSTRUCT`结构定义要执行的绘制操作。 重写该成员函数以实现所有者描述的绘图`CStatusBar`对象。 应用程序应还原选择用于显示上下文中提供的所有图形设备接口 (GDI) 对象`lpDrawItemStruct`之前终止该成员函数。  
  
##  <a name="getitemid"></a>CStatusBar::GetItemID  
 返回由指定指标的 ID `nIndex`。  
  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 其 ID 是要检索的指示器的索引。  
  
### <a name="return-value"></a>返回值  
 指定指标的 ID `nIndex`。  
  
##  <a name="getitemrect"></a>CStatusBar::GetItemRect  
 将复制的指示符，由指定的坐标`nIndex`到指向该结构`lpRect`。  
  
```  
void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 要从中检索其矩形坐标的指标的索引。  
  
 `lpRect`  
 指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，它将接收的指示符，由指定的坐标`nIndex`。  
  
### <a name="remarks"></a>备注  
 坐标是以相对于状态栏的左上角的像素为单位。  
  
##  <a name="getpaneinfo"></a>CStatusBar::GetPaneInfo  
 集`nID`， `nStyle`，和`cxWidth`ID、 样式和宽度指示器窗格中位于指定位置到`nIndex`。  
  
```  
void GetPaneInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& cxWidth) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 将为要检索其信息窗格中的索引。  
  
 `nID`  
 引用**UINT**已设置为窗格中的 ID。  
  
 `nStyle`  
 引用**UINT**它被设置为窗格中的样式。  
  
 `cxWidth`  
 对一个整数，它被设置为窗格中的宽度的引用。  
  
##  <a name="getpanestyle"></a>CStatusBar::GetPaneStyle  
 调用此成员函数以检索一个状态栏窗格中的样式。  
  
```  
UINT GetPaneStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 是要检索其样式窗格中的索引。  
  
### <a name="return-value"></a>返回值  
 状态栏窗格中所指定的样式`nIndex`。  
  
### <a name="remarks"></a>备注  
 窗格的形式决定窗格中的显示方式。  
  
 有关可用于状态栏的样式的列表，请参阅[创建](#create)。  
  
##  <a name="getpanetext"></a>CStatusBar::GetPaneText  
 调用该成员函数以检索状态栏窗格中显示的文本。  
  
```  
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;  ```  
  
### Parameters  
 `nIndex`  
 Index of the pane whose text is to be retrieved.  
  
 `rString`  
 A reference to a [CString](../../atl-mfc-shared/reference/cstringt-class.md) object that contains the text to be retrieved.  
  
### Return Value  
 A `CString` object containing the pane's text.  
  
### Remarks  
 The second form of this member function fills a `CString` object with the string text.  
  
##  <a name="getstatusbarctrl"></a>  CStatusBar::GetStatusBarCtrl  
 This member function allows direct access to the underlying common control.  
  
```  
CStatusBarCtrl & GetStatusBarCtrl() const;  
```  
  
### Return Value  
 Contains a reference to a [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) object.  
  
### Remarks  
 Use `GetStatusBarCtrl` to take advantage of the functionality of the Windows status-bar common control, and to take advantage of the support [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) provides for status-bar customization. For example, by using the common control, you can specify a style that includes a sizing grip on the status bar, or you can specify a style to have the status bar appear at the top of the parent window's client area.  
  
 For more general information about common controls, See [Common Controls](http://msdn.microsoft.com/library/windows/desktop/bb775493) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setindicators"></a>  CStatusBar::SetIndicators  
 Sets each indicator's ID to the value specified by the corresponding element of the array `lpIDArray`, loads the string resource specified by each ID, and sets the indicator's text to the string.  
  
```  
BOOL SetIndicators (const UINT * lpIDArray，  
    int nIDCount);
```  
  
### Parameters  
 `lpIDArray`  
 Pointer to an array of IDs.  
  
 `nIDCount`  
 Number of elements in the array pointed to by `lpIDArray`.  
  
### Return Value  
 Nonzero if successful; otherwise 0.  
  
##  <a name="setpaneinfo"></a>  CStatusBar::SetPaneInfo  
 Sets the specified indicator pane to a new ID, style, and width.  
  
```  
void SetPaneInfo (int nIndex，  
    UINT nID  
    UINT nStyle  
    int cxWidth);
```  
  
### Parameters  
 `nIndex`  
 Index of the indicator pane whose style is to be set.  
  
 `nID`  
 New ID for the indicator pane.  
  
 `nStyle`  
 New style for the indicator pane.  
  
 `cxWidth`  
 New width for the indicator pane.  
  
### Remarks  
 The following indicator styles are supported:  
  
- **SBPS_NOBORDERS** No 3-D border around the pane.  
  
- **SBPS_POPOUT** Reverse border so that text "pops out."  
  
- **SBPS_DISABLED** Do not draw text.  
  
- **SBPS_STRETCH** Stretch pane to fill unused space. Only one pane per status bar can have this style.  
  
- **SBPS_NORMAL** No stretch, borders, or pop-out.  
  
##  <a name="setpanestyle"></a>  CStatusBar::SetPaneStyle  
 Call this member function to set the style of a status bar's pane.  
  
```  
void SetPaneStyle (int nIndex，  
    UINT nStyle);
```  
  
### Parameters  
 `nIndex`  
 Index of the pane whose style is to be set.  
  
 `nStyle`  
 Style of the pane whose style is to be set.  
  
### Remarks  
 A pane's style determines how the pane appears.  
  
 For a list of styles available for status bars, see [SetPaneInfo](#setpaneinfo).  
  
##  <a name="setpanetext"></a>  CStatusBar::SetPaneText  
 Call this member function to set the pane text to the string pointed to by `lpszNewText`.  
  
```  
BOOL SetPaneText (int nIndex，  
    LPCTSTR lpszNewText  
    BOOL bUpdate = TRUE);
```  
  
### Parameters  
 `nIndex`  
 Index of the pane whose text is to be set.  
  
 `lpszNewText`  
 Pointer to the new pane text.  
  
 *bUpdate*  
 If **TRUE**, the pane is invalidated after the text is set.  
  
### Return Value  
 Nonzero if successful; otherwise 0.  
  
### Remarks  
 After you call `SetPaneText`, you must add a UI update handler to display the new text in the status bar.  
  
### Example  
 [!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]  
  
## See Also  
 [MFC Sample CTRLBARS](../../visual-cpp-samples.md)   
 [MFC Sample DLGCBR32](../../visual-cpp-samples.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [CStatusBarCtrl Class](../../mfc/reference/cstatusbarctrl-class.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)

