---
title: "CScrollBar 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CScrollBar
- AFXWIN/CScrollBar
- AFXWIN/CScrollBar::CScrollBar
- AFXWIN/CScrollBar::Create
- AFXWIN/CScrollBar::EnableScrollBar
- AFXWIN/CScrollBar::GetScrollBarInfo
- AFXWIN/CScrollBar::GetScrollInfo
- AFXWIN/CScrollBar::GetScrollLimit
- AFXWIN/CScrollBar::GetScrollPos
- AFXWIN/CScrollBar::GetScrollRange
- AFXWIN/CScrollBar::SetScrollInfo
- AFXWIN/CScrollBar::SetScrollPos
- AFXWIN/CScrollBar::SetScrollRange
- AFXWIN/CScrollBar::ShowScrollBar
dev_langs:
- C++
helpviewer_keywords:
- CScrollBar class
- SCROLLBAR window class
- scroll bars
- Windows common controls [C++], CScrollBar
- controls [MFC], scroll bar
ms.assetid: f3735ca5-73ea-46dc-918b-4d824c9fe47f
caps.latest.revision: 21
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
ms.openlocfilehash: 84b59f041f1a6cf73843c303e1a6b71adffc2101
ms.lasthandoff: 02/24/2017

---
# <a name="cscrollbar-class"></a>CScrollBar 类
提供 Windows 滚动条控件功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CScrollBar : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CScrollBar::CScrollBar](#cscrollbar)|构造 `CScrollBar` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CScrollBar::Create](#create)|创建 Windows 滚动条，并将其附加到`CScrollBar`对象。|  
|[CScrollBar::EnableScrollBar](#enablescrollbar)|启用或禁用滚动条的一个或两个箭头。|  
|[CScrollBar::GetScrollBarInfo](#getscrollbarinfo)|检索的滚动条使用有关的信息`SCROLLBARINFO`结构。|  
|[CScrollBar::GetScrollInfo](#getscrollinfo)|检索有关滚动条的信息。|  
|[CScrollBar::GetScrollLimit](#getscrolllimit)|检索的滚动条的限制|  
|[CScrollBar::GetScrollPos](#getscrollpos)|检索滚动框的当前位置。|  
|[CScrollBar::GetScrollRange](#getscrollrange)|检索给定的滚动条的当前最小值和最大的滚动条位置。|  
|[CScrollBar::SetScrollInfo](#setscrollinfo)|设置有关滚动条的信息。|  
|[CScrollBar::SetScrollPos](#setscrollpos)|设置滚动框的当前位置。|  
|[CScrollBar::SetScrollRange](#setscrollrange)|设置给定滚动条的最小和最大位置值。|  
|[CScrollBar::ShowScrollBar](#showscrollbar)|显示或隐藏滚动条。|  
  
## <a name="remarks"></a>备注  
 在两个步骤中创建的滚动条控件。 首先，调用构造函数`CScrollBar`构造`CScrollBar`对象，然后调用[创建](#create)成员函数来创建 Windows 滚动条控件和将其附加到`CScrollBar`对象。  
  
 如果您创建`CScrollBar`（通过对话框资源） 的对话框内的对象`CScrollBar`用户关闭对话框时自动销毁。  
  
 如果您创建`CScrollBar`对象在窗口中，您可能还需要将其销毁。  
  
 如果您创建`CScrollBar`对象在堆栈上，自动被销毁。 如果您创建`CScrollBar`使用堆上的对象**新**函数，则必须调用**删除**对象销毁它时在用户终止 Windows 滚动条上。  
  
 如果分配任何内存`CScrollBar`对象，请重写`CScrollBar`析构函数释放的分配。  
  
 有关使用的相关信息`CScrollBar`，请参阅[控件](../../mfc/controls-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CScrollBar`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="create"></a>CScrollBar::Create  
 创建 Windows 滚动条，并将其附加到`CScrollBar`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定滚动栏的样式。 应用的任意组合[滚动条样式](../../mfc/reference/scroll-bar-styles.md)到滚动条。  
  
 `rect`  
 指定滚动条的大小和位置。 可以是`RECT`结构或`CRect`对象。  
  
 `pParentWnd`  
 指定滚动栏的父窗口，通常`CDialog`对象。 它不能**NULL**。  
  
 `nID`  
 Scroll bar 控件 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 您构造`CScrollBar`两个步骤中的对象。 首先，调用构造函数构造`CScrollBar`对象; 然后，调用**创建**，它创建和初始化关联的 Windows 滚动条，并将其附加到`CScrollBar`对象。  
  
 将应用以下[窗口样式](../../mfc/reference/window-styles.md)到滚动条︰  
  
- **WS_CHILD**始终  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
- **WS_GROUP**控件组合  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CScrollBar #&1;](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]  
  
##  <a name="cscrollbar"></a>CScrollBar::CScrollBar  
 构造 `CScrollBar` 对象。  
  
```  
CScrollBar();
```  
  
### <a name="remarks"></a>备注  
 在构造该对象之后, 调用**创建**成员函数来创建和初始化 Windows 滚动条。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CScrollBar #&2;](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]  
  
##  <a name="enablescrollbar"></a>CScrollBar::EnableScrollBar  
 启用或禁用滚动条的一个或两个箭头。  
  
```  
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```  
  
### <a name="parameters"></a>参数  
 `nArrowFlags`  
 指定的滚动箭头是启用还是禁用和启用或禁用的箭头。 此参数可以是下列值之一︰  
  
- **ESB_ENABLE_BOTH**使这两个滚动条的滚动箭头。  
  
- **ESB_DISABLE_LTUP**禁用水平滚动条向左的箭头或垂直滚动条的向上箭头。  
  
- **ESB_DISABLE_RTDN**禁用水平滚动条向右箭头或垂直滚动条的向下箭头。  
  
- **ESB_DISABLE_BOTH**禁用这两个滚动条的滚动箭头。  
  
### <a name="return-value"></a>返回值  
 非零，如果启用或禁用指定; 箭头否则为 0，它表示箭头尚在请求的状态或出现错误。  
  
### <a name="example"></a>示例  
  请参阅示例[CScrollBar::SetScrollRange](#setscrollrange)。  
  
##  <a name="getscrollbarinfo"></a>CScrollBar::GetScrollBarInfo  
 检索的信息， **SCROLLBARINFO**结构维护有关滚动条。  
  
```  
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;  
```  
  
### <a name="parameters"></a>参数  
 *pScrollInfo*  
 一个指向[SCROLLBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb787535)结构。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**成功时， **FALSE**失败。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[SBM_SCROLLBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb787545)消息，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getscrollinfo"></a>CScrollBar::GetScrollInfo  
 检索 `SCROLLINFO` 结构维护的有关滚动条的信息。  
  
```  
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,  
    UINT nMask = SIF_ALL);
```  
  
### <a name="parameters"></a>参数  
 `lpScrollInfo`  
 一个指向[SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537)结构。 请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关此结构的详细信息。  
  
 `nMask`  
 指定要检索的滚动栏参数。 典型的用法，SIF_ALL，指定 SIF_PAGE、 SIF_POS、 SIF_TRACKPOS 和 SIF_RANGE 的组合。 请参阅`SCROLLINFO`nMask 值的详细信息。  
  
### <a name="return-value"></a>返回值  
 如果消息检索到的任何值，则返回值**TRUE**。 否则，它就是**FALSE**。  
  
### <a name="remarks"></a>备注  
 `GetScrollInfo`允许应用程序使用 32 位滚动位置。  
  
 [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537)结构包含有关滚动条，包括最小值和最大滚动位置、 页大小和滚动框 （缩略图） 的位置信息。 请参阅`SCROLLINFO`结构中的主题[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关更改结构的默认值的详细信息。  
  
 MFC 窗口消息处理程序指示滚动条位置[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)，提供只有 16 位的位置数据。 `GetScrollInfo`和`SetScrollInfo`提供 32 位的滚动条位置的数据。 因此，应用程序可以调用`GetScrollInfo`处理任何一个时`CWnd::OnHScroll`或`CWnd::OnVScroll`以获取 32 位滚动条位置的数据。  
  
### <a name="example"></a>示例  
  请参阅示例[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)。  
  
##  <a name="getscrolllimit"></a>CScrollBar::GetScrollLimit  
 检索滚动滚动条的位置的最大值。  
  
```  
int GetScrollLimit();
```  
  
### <a name="return-value"></a>返回值  
 指定如果成功，则一个滚动条的最大位置否则为 0。  
  
### <a name="example"></a>示例  
  请参阅示例[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)。  
  
##  <a name="getscrollpos"></a>CScrollBar::GetScrollPos  
 检索滚动框的当前位置。  
  
```  
int GetScrollPos() const;  
```  
  
### <a name="return-value"></a>返回值  
 指定如果成功，则滚动框的当前位置否则为 0。  
  
### <a name="remarks"></a>备注  
 当前位于取决于当前的滚动范围的相对值。 例如，如果滚动框位于中间栏的滚动范围是 100 到 200 个，当前的位置为 150。  
  
### <a name="example"></a>示例  
  请参阅示例[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)。  
  
##  <a name="getscrollrange"></a>CScrollBar::GetScrollRange  
 将给定的滚动条的当前最小值和最大的滚动条位置复制到由指定的位置`lpMinPos`和`lpMaxPos`。  
  
```  
void GetScrollRange(
    LPINT lpMinPos,  
    LPINT lpMaxPos) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpMinPos`  
 指向将接收的最小位置的整数变量。  
  
 `lpMaxPos`  
 指向将接收的最大位置的整数变量。  
  
### <a name="remarks"></a>备注  
 滚动条控件的默认范围为空 （这两个值都为 0）。  
  
### <a name="example"></a>示例  
  请参阅示例[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)。  
  
##  <a name="setscrollinfo"></a>CScrollBar::SetScrollInfo  
 设置的信息`SCROLLINFO`结构维护有关滚动条。  
  
```  
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `lpScrollInfo`  
 一个指向[SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537)结构。  
  
 `bRedraw`  
 指定是否重绘的滚动条，以反映新的信息。 如果`bRedraw`是**TRUE**，在重绘的滚动条。 如果它是**FALSE**，没有重绘。 默认情况下，重绘的滚动条。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回值**TRUE**。 否则，它就是**FALSE**。  
  
### <a name="remarks"></a>备注  
 您必须提供所需的值`SCROLLINFO`结构参数，其中包括标志值。  
  
 `SCROLLINFO`结构包含有关滚动条，包括最小值和最大滚动位置、 页大小和滚动框 （缩略图） 的位置信息。 请参阅[SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537)结构中的主题[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关更改结构的默认值的详细信息。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CScrollBar #&3;](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]  
  
##  <a name="setscrollpos"></a>CScrollBar::SetScrollPos  
 将滚动框的当前位置设置为指定的`nPos`并且，如果指定，将重新绘制的滚动条以反映新的位置。  
  
```  
int SetScrollPos(
    int nPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nPos`  
 指定滚动框的新位置。 它必须在滚动范围内。  
  
 `bRedraw`  
 指定是否重绘的滚动条，以反映新的位置。 如果`bRedraw`是**TRUE**，在重绘的滚动条。 如果它是**FALSE**，没有重绘。 默认情况下，重绘的滚动条。  
  
### <a name="return-value"></a>返回值  
 指定如果成功，则滚动框的前一个位置否则为 0。  
  
### <a name="remarks"></a>备注  
 设置`bRedraw`到**FALSE**将只要在给另一个函数的后续调用，以避免让两次在短的时间间隔内重绘的滚动条的重绘的滚动条。  
  
### <a name="example"></a>示例  
  请参阅示例[CScrollBar::SetScrollRange](#setscrollrange)。  
  
##  <a name="setscrollrange"></a>CScrollBar::SetScrollRange  
 设置给定滚动条的最小和最大位置值。  
  
```  
void SetScrollRange(
    int nMinPos,  
    int nMaxPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nMinPos`  
 指定的滚动位置的最小。  
  
 `nMaxPos`  
 指定的滚动位置的最大值。  
  
 `bRedraw`  
 指定是否重绘的滚动条，以反映更改。 如果`bRedraw`是**TRUE**，滚动条在重绘; 如果**FALSE**，没有重绘。 默认情况下重绘。  
  
### <a name="remarks"></a>备注  
 设置`nMinPos`和`nMaxPos`为 0 以隐藏标准滚动条。  
  
 请勿调用此函数可在处理滚动条通知消息时隐藏滚动条。  
  
 如果调用`SetScrollRange`紧随调用`SetScrollPos`成员函数设置`bRedraw`中`SetScrollPos`为 0，以防止两次重绘的滚动条。  
  
 指定的值之间的差异`nMinPos`和`nMaxPos`不得大于 32767。 滚动条控件的默认范围为空 (同时`nMinPos`和`nMaxPos`均为 0)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CScrollBar #&4;](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]  
  
##  <a name="showscrollbar"></a>CScrollBar::ShowScrollBar  
 显示或隐藏滚动条。  
  
```  
void ShowScrollBar(BOOL bShow = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bShow`  
 指定的滚动条是显示还是隐藏。 如果此参数为**TRUE**，显示滚动条，否则隐藏起来而已。  
  
### <a name="remarks"></a>备注  
 应用程序不应调用此函数可在处理滚动条通知消息时隐藏滚动条。  
  
### <a name="example"></a>示例  
  请参阅示例[CScrollBar::Create](#create)。  
  
## <a name="see-also"></a>另请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CButton 类](../../mfc/reference/cbutton-class.md)   
 [CComboBox 类](../../mfc/reference/ccombobox-class.md)   
 [CEdit 类](../../mfc/reference/cedit-class.md)   
 [CListBox 类](../../mfc/reference/clistbox-class.md)   
 [CStatic 类](../../mfc/reference/cstatic-class.md)   
 [CDialog 类](../../mfc/reference/cdialog-class.md)

