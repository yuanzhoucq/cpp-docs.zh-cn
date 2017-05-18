---
title: "CStatusBar 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 7f394d6519bcf86a4de3966bb958923aab8dd0c6
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

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
|[CStatusBar::CommandToIndex](#commandtoindex)|给定的指示器 id 获取索引|  
|[CStatusBar::Create](#create)|创建状态栏，将其附加到`CStatusBar`对象，并设置初始的字体和栏高度。|  
|[CStatusBar::CreateEx](#createex)|创建`CStatusBar`有其他样式的嵌入对象`CStatusBarCtrl`对象。|  
|[CStatusBar::DrawItem](#drawitem)|当所有者描述状态栏控件会发生变化的可视方面时调用。|  
|[CStatusBar::GetItemID](#getitemid)|获取给定索引的指示器 ID。|  
|[CStatusBar::GetItemRect](#getitemrect)|获取显示给定索引的矩形。|  
|[CStatusBar::GetPaneInfo](#getpaneinfo)|获取给定索引的指示器 ID、 样式和宽度。|  
|[CStatusBar::GetPaneStyle](#getpanestyle)|获取给定索引的指示器样式。|  
|[CStatusBar::GetPaneText](#getpanetext)|获取给定索引的指示器文本。|  
|[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)|允许直接访问基础的公共控件。|  
|[CStatusBar::SetIndicators](#setindicators)|设置指示器 Id。|  
|[CStatusBar::SetPaneInfo](#setpaneinfo)|设置指示器 ID、 样式和给定索引的宽度。|  
|[CStatusBar::SetPaneStyle](#setpanestyle)|设置给定索引的指示器样式。|  
|[CStatusBar::SetPaneText](#setpanetext)|设置给定索引的指示器文本。|  
  
## <a name="remarks"></a>备注  
 输出窗格通常用作消息行和状态指示器用于。 示例包括简短解释选定的菜单命令的菜单帮助消息行和指示器显示 SCROLL LOCK、 NUM LOCK 和其他键的状态。  
  
 [CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)，成员函数新到 MFC 4.0，使你可以利用的状态栏自定义项和其他功能的 Windows 公共控件的支持。 `CStatusBar`成员函数为您提供的大多数 Windows 公共控件; 功能但是，当调用`GetStatusBarCtrl`，你可让你状态栏甚至多个 Windows 95/98 状态栏的特征。 当调用`GetStatusBarCtrl`，它将返回到引用`CStatusBarCtrl`对象。 请参阅[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)有关设计使用 Windows 公共控件的工具栏的详细信息。 公共控件有关的更多常规信息，请参阅[公共控件](http://msdn.microsoft.com/library/windows/desktop/bb775493)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 框架将指示器信息存储在带有最左侧指示器位置 0 处的数组。 当你创建一个状态栏时，你将使用字符串框架将与相应的指示器相关联的 Id 的数组。 你可以使用字符串 ID 或索引访问指示器。  
  
 默认情况下，第一个标记是"弹性": 其占用状态栏长度不由其他指示器窗格，以便其他窗格呈右对齐。  
  
 若要创建一个状态栏，请按照下列步骤︰  
  
1.  构造 `CStatusBar` 对象。  
  
2.  调用[创建](#create)(或[CreateEx](#createex)) 函数来创建状态栏窗口，然后将其附加到`CStatusBar`对象。  
  
3.  调用[SetIndicators](#setindicators)要与每个指示器关联字符串 ID。  
  
 有三种方法来更新状态栏窗格中的文本︰  
  
1.  调用[CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)更新仅窗格 0 中的文本。  
  
2.  调用[CCmdUI::SetText](../../mfc/reference/ccmdui-class.md#settext)中状态栏的`ON_UPDATE_COMMAND_UI`处理程序。  
  
3.  调用[SetPaneText](#setpanetext)更新任何窗格的文本。  
  
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
 获取给定 id 对应的指示器索引  
  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIDFind`  
 字符串 ID 的索引是要检索的指示器。  
  
### <a name="return-value"></a>返回值  
 如果成功，则该指示器的索引如果不成功，则为-1。  
  
### <a name="remarks"></a>备注  
 第一个指示器的索引为 0。  
  
##  <a name="create"></a>CStatusBar::Create  
 创建状态栏 （子窗口），并将其与关联`CStatusBar`对象。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>参数  
 `pParentWnd`  
 指向[CWnd](../../mfc/reference/cwnd-class.md)其 Windows 窗口是状态栏的父对象。  
  
 `dwStyle`  
 状态栏样式中。 除了标准的 Windows[样式](../../mfc/reference/window-styles.md)，支持这些样式。  
  
- `CBRS_TOP`控件条是在框架窗口的顶部。  
  
- `CBRS_BOTTOM`控件条是在框架窗口的底部。  
  
- `CBRS_NOALIGN`父级调整大小时，将不会重新定位控件条。  
  
 `nID`  
 工具栏的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此外设置初始字体，然后将状态设置为默认值的栏的高度。  
  
##  <a name="createex"></a>CStatusBar::CreateEx  
 调用此函数可创建状态栏 （子窗口），并将其与关联`CStatusBar`对象。  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = 0,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>参数  
 `pParentWnd`  
 指向[CWnd](../../mfc/reference/cwnd-class.md)其 Windows 窗口是状态栏的父对象。  
  
 `dwCtrlStyle`  
 为创建的嵌入其他样式[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)对象。 默认值指定状态栏不带大小调整手柄或工具提示支持。 支持的状态栏样式包括︰  
  
- **SBARS_SIZEGRIP**状态栏控件包括位于状态栏的右端大小调整手柄。 大小调整手柄类似于大小调整边框；它是用户可以通过单击和拖动来重设父窗口大小的矩形区域。  
  
- **SBT_TOOLTIPS**状态栏支持工具提示。  
  
 有关这些样式的详细信息，请参阅[CStatusBarCtrl 的设置](../../mfc/settings-for-the-cstatusbarctrl.md)。  
  
 `dwStyle`  
 状态栏样式。 默认值指定在框架窗口的底部创建一个可见的状态栏。 应用状态栏控件样式中列出的任意组合[窗口样式](../../mfc/reference/window-styles.md)和[CDialogBar::Create](../../mfc/reference/cdialogbar-class.md#create)。 但是，此参数应始终包含 WS_CHILD 和 WS_VISIBLE 样式。  
  
 `nID`  
 状态栏的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数还设置初始字体，然后将状态设置为默认值的栏的高度。  
  
 使用`CreateEx`，而不是[创建](#create)，当某些样式需要在嵌入的状态栏控件的创建过程。 例如，设置`dwCtrlStyle`到**SBT_TOOLTIPS**中的状态栏对象显示工具提示。  
  
##  <a name="cstatusbar"></a>CStatusBar::CStatusBar  
 构造`CStatusBar`对象，创建一个默认状态栏的字体如有必要，并将字体特征设置为默认值。  
  
```  
CStatusBar();
```  
  
##  <a name="drawitem"></a>CStatusBar::DrawItem  
 由框架在所有者绘制状态栏会发生变化的可视方面时调用此成员函数。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpDrawItemStruct`  
 指向的指针[DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802)结构，其中包含有关所需的绘图的类型的信息。  
  
### <a name="remarks"></a>备注  
 **ItemAction**的成员`DRAWITEMSTRUCT`结构定义要执行的绘制操作。 重写该成员函数以实现所有者描述的绘图`CStatusBar`对象。 应用程序应还原选择的显示上下文中提供的所有图形设备接口 (GDI) 对象`lpDrawItemStruct`之前的此成员函数终止。  
  
##  <a name="getitemid"></a>CStatusBar::GetItemID  
 返回由指定指示器的 ID `nIndex`。  
  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指示器的 ID 是要检索的索引。  
  
### <a name="return-value"></a>返回值  
 指定指示器的 ID `nIndex`。  
  
##  <a name="getitemrect"></a>CStatusBar::GetItemRect  
 将复制指定指示器的坐标`nIndex`为指向结构`lpRect`。  
  
```  
void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指示器矩形坐标是要检索的索引。  
  
 `lpRect`  
 指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象将接收指定指示器的坐标`nIndex`。  
  
### <a name="remarks"></a>备注  
 坐标是以相对于状态栏的左上角的像素为单位。  
  
##  <a name="getpaneinfo"></a>CStatusBar::GetPaneInfo  
 集`nID`， `nStyle`，和`cxWidth`到 ID、 样式和在指定的位置指示器窗格的宽度`nIndex`。  
  
```  
void GetPaneInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& cxWidth) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 获取其信息是要检索的窗格中的索引。  
  
 `nID`  
 引用**UINT**是否设置为窗格中的 ID。  
  
 `nStyle`  
 引用**UINT**是否设置为窗格中的样式。  
  
 `cxWidth`  
 对一个整数，它设置为窗格的宽度的引用。  
  
##  <a name="getpanestyle"></a>CStatusBar::GetPaneStyle  
 调用此成员函数可检索的状态栏窗格中的样式。  
  
```  
UINT GetPaneStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 其样式是要检索的窗格中的索引。  
  
### <a name="return-value"></a>返回值  
 指定状态栏窗格中的样式`nIndex`。  
  
### <a name="remarks"></a>备注  
 窗格中的样式确定窗格中的显示方式。  
  
 有关可用于状态栏的样式的列表，请参阅[创建](#create)。  
  
##  <a name="getpanetext"></a>CStatusBar::GetPaneText  
 调用此成员函数以检索在状态栏窗格中显示的文本。  
  
```  
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 其文本是要检索的窗格中的索引。  
  
 `rString`  
 对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含要检索的文本。  
  
### <a name="return-value"></a>返回值  
 A`CString`对象，其中包含窗格的文本。  
  
### <a name="remarks"></a>备注  
 此成员的第二种形式函数填充`CString`具有字符串文本对象。  
  
##  <a name="getstatusbarctrl"></a>CStatusBar::GetStatusBarCtrl  
 此成员函数允许直接访问基础的公共控件。  
  
```  
CStatusBarCtrl& GetStatusBarCtrl() const;  
```  
  
### <a name="return-value"></a>返回值  
 包含对引用[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)对象。  
  
### <a name="remarks"></a>备注  
 使用`GetStatusBarCtrl`以利用功能的 Windows 公共状态栏控件上，并利用支持[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)提供状态栏自定义项。 例如，通过使用公共控件，你可以指定包含上的状态栏中，大小调整手柄的样式也可以指定要具有将出现在父窗口的工作区顶部的状态栏的样式。  
  
 公共控件有关的更多常规信息，请参阅[公共控件](http://msdn.microsoft.com/library/windows/desktop/bb775493)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setindicators"></a>CStatusBar::SetIndicators  
 每个指示器 ID 设置为指定数组的相应元素的值`lpIDArray`、 加载指定的每个 ID 的字符串资源和将指示器的文本设置为字符串。  
  
```  
BOOL SetIndicators(
    const UINT* lpIDArray,  
    int nIDCount);
```  
  
### <a name="parameters"></a>参数  
 `lpIDArray`  
 指向一个 Id 数组的指针。  
  
 `nIDCount`  
 指向数组中的元素数目`lpIDArray`。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
##  <a name="setpaneinfo"></a>CStatusBar::SetPaneInfo  
 将指定的指示器窗格设置为新的 ID、 样式和宽度。  
  
```  
void SetPaneInfo(
    int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int cxWidth);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指示器窗格都要设置其样式的索引。  
  
 `nID`  
 指示器窗格的新 ID。  
  
 `nStyle`  
 指示器窗格的新样式。  
  
 `cxWidth`  
 指示器窗格的新宽度。  
  
### <a name="remarks"></a>备注  
 支持以下指示器样式︰  
  
- **SBPS_NOBORDERS**周围窗格没有三维边框。  
  
- **SBPS_POPOUT**反向边框，以便文本"弹出闩锁。"  
  
- **SBPS_DISABLED**不绘制文本。  
  
- **SBPS_STRETCH** Stretch 窗格中，以填充未使用的空间。 只有一个窗格中，每个状态栏可将此样式。  
  
- **SBPS_NORMAL**没有 stretch、 边框或弹出。  
  
##  <a name="setpanestyle"></a>CStatusBar::SetPaneStyle  
 调用此成员函数以设置状态栏的窗格中的样式。  
  
```  
void SetPaneStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 都要设置其样式窗格中的索引。  
  
 `nStyle`  
 窗格都要设置其样式的样式。  
  
### <a name="remarks"></a>备注  
 窗格中的样式确定窗格中的显示方式。  
  
 有关可用于状态栏的样式的列表，请参阅[SetPaneInfo](#setpaneinfo)。  
  
##  <a name="setpanetext"></a>CStatusBar::SetPaneText  
 调用此成员函数可设置为指向字符串的窗格文本`lpszNewText`。  
  
```  
BOOL SetPaneText(
    int nIndex,  
    LPCTSTR lpszNewText,  
    BOOL bUpdate = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 其文本是设置窗格中的索引。  
  
 `lpszNewText`  
 指向新的窗格文本指针。  
  
 *bUpdate*  
 如果**TRUE**，窗格中设置文本后失效。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 调用后`SetPaneText`，必须添加的用户界面更新处理程序，在状态栏中显示新文本。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView # 176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocView # 177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCDocView # 178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 CTRLBARS](../../visual-cpp-samples.md)   
 [MFC 示例 DLGCBR32](../../visual-cpp-samples.md)   
 [CControlBar 类](../../mfc/reference/ccontrolbar-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CStatusBarCtrl 类](../../mfc/reference/cstatusbarctrl-class.md)   
 [CControlBar 类](../../mfc/reference/ccontrolbar-class.md)

