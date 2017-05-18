---
title: "CControlBar 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CControlBar
- AFXEXT/CControlBar
- AFXEXT/CControlBar::CControlBar
- AFXEXT/CControlBar::CalcDynamicLayout
- AFXEXT/CControlBar::CalcFixedLayout
- AFXEXT/CControlBar::CalcInsideRect
- AFXEXT/CControlBar::DoPaint
- AFXEXT/CControlBar::DrawBorders
- AFXEXT/CControlBar::DrawGripper
- AFXEXT/CControlBar::EnableDocking
- AFXEXT/CControlBar::GetBarStyle
- AFXEXT/CControlBar::GetBorders
- AFXEXT/CControlBar::GetCount
- AFXEXT/CControlBar::GetDockingFrame
- AFXEXT/CControlBar::IsFloating
- AFXEXT/CControlBar::OnUpdateCmdUI
- AFXEXT/CControlBar::SetBarStyle
- AFXEXT/CControlBar::SetBorders
- AFXEXT/CControlBar::SetInPlaceOwner
- AFXEXT/CControlBar::m_bAutoDelete
- AFXEXT/CControlBar::m_pInPlaceOwner
dev_langs:
- C++
helpviewer_keywords:
- CControlBar class
- OLE resize bars
- OLE resize bars, base class
- dialog bars, base class
- toolbars [C++], base class
- control bars [C++], base class
- status bars, base class
ms.assetid: 4d668c55-9b42-4838-97ac-cf2b3000b82c
caps.latest.revision: 22
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
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 17702c4ca8559f1990cbbc183f1e409a6b2be484
ms.contentlocale: zh-cn
ms.lasthandoff: 03/31/2017

---
# <a name="ccontrolbar-class"></a>CControlBar Class
控件条类的基类[CStatusBar](../../mfc/reference/cstatusbar-class.md)， [CToolBar](../../mfc/reference/ctoolbar-class.md)， [CDialogBar](../../mfc/reference/cdialogbar-class.md)， [CReBar](../../mfc/reference/crebar-class.md)，和[COleResizeBar](../../mfc/reference/coleresizebar-class.md)。  
  
## <a name="syntax"></a>语法  
  
```  
class CControlBar : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CControlBar::CControlBar](#ccontrolbar)|构造 `CControlBar` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CControlBar::CalcDynamicLayout](#calcdynamiclayout)|返回作为动态控件条的大小[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。|  
|[CControlBar::CalcFixedLayout](#calcfixedlayout)|返回作为控件条的大小[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。|  
|[CControlBar::CalcInsideRect](#calcinsiderect)|返回的控件栏区域; 的当前尺寸这包括边框。|  
|[CControlBar::DoPaint](#dopaint)|呈现的边框和控件条的控制手柄。|  
|[CControlBar::DrawBorders](#drawborders)|呈现控件条的边框。|  
|[CControlBar::DrawGripper](#drawgripper)|呈现控件条的控制手柄。|  
|[CControlBar::EnableDocking](#enabledocking)|允许要停靠或浮动的控件条。|  
|[CControlBar::GetBarStyle](#getbarstyle)|检索控件栏样式设置。|  
|[CControlBar::GetBorders](#getborders)|检索控件条的边框值。|  
|[CControlBar::GetCount](#getcount)|返回的非数`HWND`控件条中的元素。|  
|[CControlBar::GetDockingFrame](#getdockingframe)|将指针返回到停靠控件条的帧。|  
|[CControlBar::IsFloating](#isfloating)|如果控件条问题是浮动的控件条，则返回非零值。|  
|[CControlBar::OnUpdateCmdUI](#onupdatecmdui)|调用命令 UI 处理程序。|  
|[CControlBar::SetBarStyle](#setbarstyle)|修改控件栏样式设置。|  
|[CControlBar::SetBorders](#setborders)|设置控件条的边框值。|  
|[CControlBar::SetInPlaceOwner](#setinplaceowner)|更改的控件条的就地所有者。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CControlBar::m_bAutoDelete](#m_bautodelete)|如果不为零，`CControlBar`销毁 Windows 控件条时删除对象。|  
|[CControlBar::m_pInPlaceOwner](#m_pinplaceowner)|控件条的就地所有者。|  
  
## <a name="remarks"></a>备注  
 控件条是左侧或右侧的框架窗口通常与对齐一个窗口。 它可能包含子项都是`HWND`基于控件，是用于生成和响应 Windows 消息，或非窗口- `HWND`-基于项，而不是窗口由应用程序代码或框架代码。 列表框和编辑控件都属于`HWND`-基于的控件; 状态栏窗格和位图按钮都属于非- `HWND`-基于控件。  
  
 控件条 windows 通常是父框架窗口的子窗口，而是通常的客户端视图或框架窗口的 MDI 客户端所在的文件夹。 A`CControlBar`对象使用父窗口的客户端矩形有关的信息来为自身定位。 然后，它通知父窗口并在父窗口的工作区中剩余未分配多少空间。  
  
 有关详细信息`CControlBar`，请参阅︰  
  
- [控件条](../../mfc/control-bars.md)  
  
- [技术说明 31︰ 控件条](../../mfc/tn031-control-bars.md)。  
  
-   知识库文章 Q242577: PRB︰ 更新命令 UI 处理程序执行不工作的菜单附加到对话框中  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CControlBar`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxext.h  
  
##  <a name="calcdynamiclayout"></a>CControlBar::CalcDynamicLayout  
 框架调用此成员函数以计算动态工具栏的维度。  
  
```  
virtual CSize CalcDynamicLayout(
    int nLength,  
    DWORD nMode);
```  
  
### <a name="parameters"></a>参数  
 `nLength`  
 控件条，水平或垂直，具体取决于请求的维度`dwMode`。  
  
 `nMode`  
 以下预定义的标志用于确定的高度和动态控件条的宽度。 使用按位 OR (|) 运算符来组合标志。  
  
|布局模式标志|其中的含义|  
|-----------------------|-------------------|  
|`LM_STRETCH`|指示是否将控件条被拉伸到的帧的大小。 如果栏不是停靠栏 （不可用于停靠），设置。 未设置栏时停靠或浮动 （适用于停靠）。 如果设置，`LM_STRETCH`忽略`nLength`并返回维度基于`LM_HORZ`状态。 `LM_STRETCH`工作原理类似于`bStretch`参数中使用[CalcFixedLayout](#calcfixedlayout); 请参阅有关拉伸和方向之间的关系的详细信息该成员函数。|  
|`LM_HORZ`|指示该拆分条是水平或垂直方向。 只有当栏为水平方向，并且如果它是垂直方向，未设置设置。 `LM_HORZ`工作原理类似于`bHorz`参数中使用[CalcFixedLayout](#calcfixedlayout); 请参阅有关拉伸和方向之间的关系的详细信息该成员函数。|  
|**LM_MRUWIDTH**|最近使用过的动态宽度。 将忽略`nLength`参数，并使用记忆个最近使用的宽度。|  
|`LM_HORZDOCK`|水平停靠维度。 将忽略`nLength`参数并返回最大宽度的动态大小。|  
|`LM_VERTDOCK`|垂直停靠维度。 将忽略`nLength`参数和返回使用的最大高度的动态大小。|  
|`LM_LENGTHY`|如果设置`nLength`指示高度 （Y 轴方向） 而不是宽度。|  
|`LM_COMMIT`|重置**LM_MRUWIDTH**到浮点控件条的当前宽度。|  
  
### <a name="return-value"></a>返回值  
 控件条的大小，以像素为单位的[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。  
  
### <a name="remarks"></a>备注  
 重写该成员函数以提供您自己在从派生的类中的动态布局`CControlBar`。 MFC 类派生自`CControlBar`，如[CToolbar](../../mfc/reference/ctoolbar-class.md)，重写该成员函数，并且提供自己的实现。  
  
##  <a name="calcfixedlayout"></a>CControlBar::CalcFixedLayout  
 调用此成员函数来计算的控件条的水平大小。  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>参数  
 `bStretch`  
 指示是否应被栏拉伸到的帧的大小。 `bStretch`时栏 （不可用于停靠） 停靠栏并不为 0 时停靠或浮动 （适用于停靠），则为非零参数。  
  
 `bHorz`  
 指示该拆分条是水平或垂直方向。 `bHorz`如果栏是水平方向和垂直方向是否为 0，则为非零参数。  
  
### <a name="return-value"></a>返回值  
 控件条的大小，以像素为单位的`CSize`对象。  
  
### <a name="remarks"></a>备注  
 如工具栏的控件条可以水平拉伸或垂直以适应按钮包含在控件条。  
  
 如果`bStretch`是**TRUE**，拉伸方向由沿维度`bHorz`。 换而言之，如果`bHorz`是**FALSE**，垂直拉伸控件条。 如果`bStretch`是**FALSE**，没有拉伸时发生。 下表显示可能的排列和生成的控件条样式的`bStretch`和`bHorz`。  
  
|bStretch|bHorz|拉伸|方向|停靠/未停靠|  
|--------------|-----------|----------------|-----------------|--------------------------|  
|**TRUE**|**TRUE**|水平拉伸|水平方向|不停靠|  
|**TRUE**|**FALSE**|垂直拉伸|垂直方向|不停靠|  
|**FALSE**|**TRUE**|没有拉伸可用|水平方向|停靠|  
|**FALSE**|**FALSE**|没有拉伸可用|垂直方向|停靠|  
  
##  <a name="calcinsiderect"></a>CControlBar::CalcInsideRect  
 框架调用此函数可计算控件条的工作区。  
  
```  
virtual void CalcInsideRect(
    CRect& rect,  
    BOOL bHorz) const;  
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 包含控件条中; 当前维度这包括边框。  
  
 `bHorz`  
 指示该拆分条是水平或垂直方向。 `bHorz`如果栏是水平方向和垂直方向是否为 0，则为非零参数。  
  
### <a name="remarks"></a>备注  
 控件条绘制之前调用此函数。  
  
 重写此函数可自定义的边框和控件条的手柄栏的呈现。  
  
##  <a name="ccontrolbar"></a>CControlBar::CControlBar  
 构造 `CControlBar` 对象。  
  
```  
CControlBar();
```  
  
##  <a name="dopaint"></a>CControlBar::DoPaint  
 由框架调用以呈现边框和控件条的手柄栏。  
  
```  
virtual void DoPaint(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向设备上下文以用于呈现边框和控件条的控制手柄。  
  
### <a name="remarks"></a>备注  
 重写此函数可自定义控件条的绘制行为。  
  
 另一种自定义方法是重写`DrawBorders`和`DrawGripper`函数，并添加边框和控制手柄的自定义绘图代码。 因为默认情况下调用这些方法`DoPaint`方法，重写`DoPaint`不需要。  
  
##  <a name="drawborders"></a>CControlBar::DrawBorders  
 由框架调用以呈现控件条的边框。  
  
```  
virtual void DrawBorders(
    CDC* pDC,  
    CRect& rect);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向设备上下文以用于呈现控件条的边框。  
  
 `rect`  
 A`CRect`对象，它包含控件条的维度。  
  
### <a name="remarks"></a>备注  
 重写此函数可自定义控件栏边框的外观。  
  
##  <a name="drawgripper"></a>CControlBar::DrawGripper  
 由框架调用以呈现控件条的控制手柄。  
  
```  
virtual void DrawGripper(
    CDC* pDC,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向设备上下文以用于呈现控件栏控制手柄。  
  
 `rect`  
 A`CRect`对象，它包含控件栏控制手柄的尺寸。  
  
### <a name="remarks"></a>备注  
 重写此函数可自定义控件栏控制手柄的外观。  
  
##  <a name="enabledocking"></a>CControlBar::EnableDocking  
 调用此函数可启用要停靠的控件条。  
  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>参数  
 `dwDockStyle`  
 指定是否将控件条支持停靠和到可停靠控件条，其父窗口的侧，如果受支持。 可以是一个或多个以下︰  
  
- `CBRS_ALIGN_TOP`允许在客户端区域的顶部停靠。  
  
- `CBRS_ALIGN_BOTTOM`允许在工作区底部停靠。  
  
- `CBRS_ALIGN_LEFT`允许客户端区域的左侧停靠。  
  
- `CBRS_ALIGN_RIGHT`允许客户端区域右侧停靠。  
  
- `CBRS_ALIGN_ANY`允许在客户端区域的任何一侧上停靠。  
  
- `CBRS_FLOAT_MULTI`允许多个控件条，以在单个微型框架窗口中浮动。  
  
 如果为 0 （即，指示没有标志），将不停靠控件条。  
  
### <a name="remarks"></a>备注  
 指定四条边必须匹配的一端为停靠在目标框架窗口中，启用或不能为该框架窗口停靠控件条。  
  
##  <a name="getbarstyle"></a>CControlBar::GetBarStyle  
 调用此函数可确定哪些**CBRS_**控件栏的当前设置 （控件栏样式） 设置。  
  
```  
DWORD GetBarStyle();
```  
  
### <a name="return-value"></a>返回值  
 当前**CBRS_**控件条的 （控件栏样式） 设置。 请参阅[CControlBar::SetBarStyle](#setbarstyle)可用样式的完整列表。  
  
### <a name="remarks"></a>备注  
 不处理**WS_** （窗口样式） 样式。  
  
##  <a name="getborders"></a>CControlBar::GetBorders  
 返回控件条的当前边框的值。  
  
```  
CRect GetBorders() const;  
```  
  
### <a name="return-value"></a>返回值  
 A`CRect`对象，其中包含的每一方的控件条对象的当前宽度 （以像素为单位）。 例如，值为`left`成员的[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，是左侧边框的宽度。  
  
##  <a name="getcount"></a>CControlBar::GetCount  
 返回的非数`HWND`项上`CControlBar`对象。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 非数`HWND`项上`CControlBar`对象。 此函数将返回 0 [CDialogBar](../../mfc/reference/cdialogbar-class.md)对象。  
  
### <a name="remarks"></a>备注  
 项的类型取决于派生的对象︰ 窗格[CStatusBar](../../mfc/reference/cstatusbar-class.md)对象、 按钮和分隔符[CToolBar](../../mfc/reference/ctoolbar-class.md)对象。  
  
##  <a name="getdockingframe"></a>CControlBar::GetDockingFrame  
 调用此成员函数以获取指向当前的框架窗口到其停靠控件条的指针。  
  
```  
CFrameWnd* GetDockingFrame() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则框架窗口指向的指针否则为**NULL**。  
  
 如果 （即，如果控件条浮动） 框架窗口不停靠控件条，此函数将返回一个指针，到其父[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)。  
  
### <a name="remarks"></a>备注  
 有关可停靠控件条的详细信息，请参阅[CControlBar::EnableDocking](#enabledocking)和[CFrameWnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar)。  
  
##  <a name="isfloating"></a>CControlBar::IsFloating  
 调用此成员函数可确定是否浮动或停靠控件条。  
  
```  
BOOL IsFloating() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果控件条浮动; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 若要更改的状态中的控件栏的停靠变为浮动，调用[CFrameWnd::FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar)。  
  
##  <a name="m_bautodelete"></a>CControlBar::m_bAutoDelete  
 如果不为零，`CControlBar`销毁 Windows 控件条时删除对象。  
  
```  
BOOL m_bAutoDelete;  
```  
  
### <a name="remarks"></a>备注  
 `m_bAutoDelete`是类型的公共变量**BOOL**。  
  
 控件条对象通常会嵌入在框架窗口对象中。 在这种情况下，`m_bAutoDelete`为 0，因为嵌入的控件条对象被销毁时销毁框架窗口。  
  
 将此变量设置为非零值，如果分配`CControlBar`对象堆和你不打算调用**删除**。  
  
##  <a name="m_pinplaceowner"></a>CControlBar::m_pInPlaceOwner  
 控件条的就地所有者。  
  
```  
CWnd* m_pInPlaceOwner;  
```  
  
##  <a name="onupdatecmdui"></a>CControlBar::OnUpdateCmdUI  
 此成员函数调用由框架更新工具栏或状态栏的状态。  
  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler) = 0;  
```  
  
### <a name="parameters"></a>参数  
 `pTarget`  
 指向应用程序的主框架窗口。 此指针用于路由更新消息。  
  
 `bDisableIfNoHndler`  
 该标志指示没有更新处理程序的控件是否应自动显示为已禁用。  
  
### <a name="remarks"></a>备注  
 若要更新的单个按钮或窗格中，使用`ON_UPDATE_COMMAND_UI`消息映射适当地设置一个更新处理程序中的宏。 请参阅[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui)有关使用此宏的详细信息。  
  
 `OnUpdateCmdUI`当应用程序处于空闲状态时，是由框架调用。 要更新的框架窗口必须是子窗口，至少间接可见框架窗口。 `OnUpdateCmdUI`是一个高级可重写。  
  
##  <a name="setbarstyle"></a>CControlBar::SetBarStyle  
 调用此函数可设置所需**CBRS_**控件条的样式。  
  
```  
void SetBarStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 控件条所需的样式。 可以是一个或多个以下︰  
  
- `CBRS_ALIGN_TOP`允许到框架窗口的工作区顶部停靠控件条。  
  
- `CBRS_ALIGN_BOTTOM`允许到框架窗口的工作区底部停靠控件条。  
  
- `CBRS_ALIGN_LEFT`允许的客户端区域的框架窗口的左侧停靠控件条。  
  
- `CBRS_ALIGN_RIGHT`允许控件条停靠框架窗口的工作区的右侧。  
  
- `CBRS_ALIGN_ANY`允许到框架窗口的工作区的任何一侧停靠控件条。  
  
- `CBRS_BORDER_TOP`将导致边框要绘制的控件条的顶部边缘时可见。  
  
- `CBRS_BORDER_BOTTOM`导致时可见要绘制的控件条的下边缘的边框。  
  
- `CBRS_BORDER_LEFT`将导致边框要绘制的控件条的左边缘时可见。  
  
- `CBRS_BORDER_RIGHT`将导致边框时可见要绘制的控件条的右边缘上。  
  
- `CBRS_FLOAT_MULTI`允许多个控件条，以在单个微型框架窗口中浮动。  
  
- `CBRS_TOOLTIPS`导致要为控件条显示的工具提示。  
  
- `CBRS_FLYBY`会导致将消息文本在工具提示在同一时间更新。  
  
- **CBRS_GRIPPER**导致的控制手柄，类似于上带区中使用**CReBar**对象，要绘制任何`CControlBar`-派生类。  
  
### <a name="remarks"></a>备注  
 不会影响**WS_** （窗口样式） 设置。  
  
##  <a name="setborders"></a>CControlBar::SetBorders  
 调用此函数可设置控件条的边框的大小。  
  
```  
void SetBorders(
    int cxLeft = 0,  
    int cyTop = 0,  
    int cxRight = 0,  
    int cyBottom = 0);  
  
void SetBorders(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
 *cxLeft*  
 控件条的左边框宽度 （以像素为单位）。  
  
 *cyTop*  
 控件条的边框的高度 （以像素为单位）。  
  
 *cxRight*  
 控件条的右边框的宽度 （以像素为单位）。  
  
 *cyBottom*  
 控件条下边框的高度 （以像素为单位）。  
  
 `lpRect`  
 指向的指针[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，其中包含每个边框的控件条对象的当前宽度 （以像素为单位）。  
  
### <a name="example"></a>示例  
 下面的代码示例将 5 个像素，将控件栏顶部和底部边界和左、 右边框设置为 2 个像素︰  
  
 [!code-cpp[NVC_MFCControlLadenDialog # 61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]  
  
##  <a name="setinplaceowner"></a>CControlBar::SetInPlaceOwner  
 更改的控件条的就地所有者。  
  
```  
void SetInPlaceOwner(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向的指针`CWnd`对象。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 CTRLBARS](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CToolBar 类](../../mfc/reference/ctoolbar-class.md)   
 [CDialogBar 类](../../mfc/reference/cdialogbar-class.md)   
 [CStatusBar 类](../../mfc/reference/cstatusbar-class.md)   
 [CReBar 类](../../mfc/reference/crebar-class.md)

