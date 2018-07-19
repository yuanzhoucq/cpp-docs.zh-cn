---
title: CMDIFrameWnd 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMDIFrameWnd
- AFXWIN/CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CreateClient
- AFXWIN/CMDIFrameWnd::CreateNewChild
- AFXWIN/CMDIFrameWnd::GetWindowMenuPopup
- AFXWIN/CMDIFrameWnd::MDIActivate
- AFXWIN/CMDIFrameWnd::MDICascade
- AFXWIN/CMDIFrameWnd::MDIGetActive
- AFXWIN/CMDIFrameWnd::MDIIconArrange
- AFXWIN/CMDIFrameWnd::MDIMaximize
- AFXWIN/CMDIFrameWnd::MDINext
- AFXWIN/CMDIFrameWnd::MDIPrev
- AFXWIN/CMDIFrameWnd::MDIRestore
- AFXWIN/CMDIFrameWnd::MDISetMenu
- AFXWIN/CMDIFrameWnd::MDITile
dev_langs:
- C++
helpviewer_keywords:
- CMDIFrameWnd [MFC], CMDIFrameWnd
- CMDIFrameWnd [MFC], CreateClient
- CMDIFrameWnd [MFC], CreateNewChild
- CMDIFrameWnd [MFC], GetWindowMenuPopup
- CMDIFrameWnd [MFC], MDIActivate
- CMDIFrameWnd [MFC], MDICascade
- CMDIFrameWnd [MFC], MDIGetActive
- CMDIFrameWnd [MFC], MDIIconArrange
- CMDIFrameWnd [MFC], MDIMaximize
- CMDIFrameWnd [MFC], MDINext
- CMDIFrameWnd [MFC], MDIPrev
- CMDIFrameWnd [MFC], MDIRestore
- CMDIFrameWnd [MFC], MDISetMenu
- CMDIFrameWnd [MFC], MDITile
ms.assetid: fa8736e6-511b-4c51-8b4d-eba78378aeb9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a33158f438eaeaf6416540cdf7a03094ec3164d7
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336743"
---
# <a name="cmdiframewnd-class"></a>CMDIFrameWnd 类
提供 Windows 多文档界面 (MDI) 框架窗口功能，并提供管理窗口的成员。  
  
## <a name="syntax"></a>语法  
  
```  
class CMDIFrameWnd : public CFrameWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMDIFrameWnd::CMDIFrameWnd](#cmdiframewnd)|构造一个 `CMDIFrameWnd`。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMDIFrameWnd::CreateClient](#createclient)|为此创建一个 Windows MDICLIENT 窗口`CMDIFrameWnd`。 调用`OnCreate`成员函数的`CWnd`。|  
|[CMDIFrameWnd::CreateNewChild](#createnewchild)|创建一个新的子窗口。|  
|[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)|返回窗口弹出菜单。|  
|[CMDIFrameWnd::MDIActivate](#mdiactivate)|激活一个不同的 MDI 子窗口。|  
|[CMDIFrameWnd::MDICascade](#mdicascade)|排列的级联格式中的所有子窗口。|  
|[CMDIFrameWnd::MDIGetActive](#mdigetactive)|检索当前处于活动状态的 MDI 子窗口，以及一个标志，指示子最大化。|  
|[CMDIFrameWnd::MDIIconArrange](#mdiiconarrange)|排列所有最小化的文档子窗口。|  
|[CMDIFrameWnd::MDIMaximize](#mdimaximize)|最大化的 MDI 子窗口。|  
|[CMDIFrameWnd::MDINext](#mdinext)|激活立即隐藏当前处于活动状态的子窗口的子窗口，并将当前处于活动状态的子窗口放在所有其他子窗口的后面。|  
|[CMDIFrameWnd::MDIPrev](#mdiprev)|激活上一个子窗口，并将其背后当前处于活动状态的子窗口。|  
|[CMDIFrameWnd::MDIRestore](#mdirestore)|最大化或最小化大小从还原的 MDI 子窗口。|  
|[CMDIFrameWnd::MDISetMenu](#mdisetmenu)|替代了 MDI 框架窗口的菜单、 窗口弹出菜单中，或两者。|  
|[CMDIFrameWnd::MDITile](#mditile)|排列在平铺格式中的所有子窗口。|  
  
## <a name="remarks"></a>备注  
 若要创建有用的 MDI 框架窗口为你的应用程序，从派生类`CMDIFrameWnd`。 将成员变量添加到派生类，以存储特定于你的应用程序的数据。 可派生类中实现消息处理程序成员函数和消息映射，以指定在消息定向到窗口时所发生的情况。  
  
 您可以通过调用构造 MDI 框架窗口[创建](../../mfc/reference/cframewnd-class.md#create)或[LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)成员函数的`CFrameWnd`。  
  
 在调用之前`Create`或`LoadFrame`，必须构造框架窗口对象上使用 c + + 堆**新**运算符。 然后再调用`Create`您还可以注册窗口类[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全局函数设置的帧的图标和类样式。  
  
 使用`Create`成员函数将为快速参数传递的帧创建参数。  
  
 `LoadFrame` 需要较少的参数，而不是`Create`，并改为从资源，包括帧的标题、 图标、 快捷键对应表和菜单检索大部分其默认值。 若要访问的`LoadFrame`，所有这些资源必须具有相同的资源 ID (例如，IDR_MAINFRAME)。  
  
 尽管`MDIFrameWnd`派生自`CFrameWnd`，框架窗口类派生自`CMDIFrameWnd`不需要使用声明`DECLARE_DYNCREATE`。  
  
 `CMDIFrameWnd`类继承了其默认实现从大量`CFrameWnd`。 有关这些功能的详细列表，请参阅[CFrameWnd](../../mfc/reference/cframewnd-class.md)类说明。 `CMDIFrameWnd`类具有下列附加功能：  
  
-   MDI 框架窗口管理 MDICLIENT 窗口中，其与控件条结合使用进行重新定位。 MDI 客户端窗口是 MDI 子框架窗口的直接父级。 指定的 WS_HSCROLL 和 WS_VSCROLL 窗口样式`CMDIFrameWnd`不适用于 MDI 客户端窗口而不是主框架窗口，使用户可以滚动 MDI 客户端区域 （如 Windows 项目经理，例如）。  
  
-   MDI 框架窗口拥有一个默认菜单，在没有任何活动的 MDI 子窗口时用作菜单栏。 当没有活动 MDI 子窗体时，MDI 框架窗口的菜单栏将自动替换为 MDI 子窗口菜单。  
  
-   MDI 框架窗口结合使用与当前 MDI 子窗口，如果有的话。 例如，命令消息都委托给当前处于活动状态的 MDI 子 MDI 框架窗口之前。  
  
-   MDI 框架窗口具有以下标准的窗口菜单命令的默认处理程序：  
  
    - ID_WINDOW_TILE_VERT  
  
    - ID_WINDOW_TILE_HORZ  
  
    - ID_WINDOW_CASCADE  
  
    - ID_WINDOW_ARRANGE  
  
-   MDI 框架窗口还提供了 ID_WINDOW_NEW，创建一个新帧和当前文档的视图的实现。 应用程序可以重写这些默认命令实现，以自定义 MDI 窗口处理。  
  
 不使用 c + +**删除**运算符来销毁框架窗口。 请改用 `CWnd::DestroyWindow`。 `CFrameWnd`的实现`PostNcDestroy`销毁窗口时，将删除 c + + 对象。 当用户关闭帧窗口时，默认值`OnClose`处理程序将调用`DestroyWindow`。  
  
 有关详细信息`CMDIFrameWnd`，请参阅[帧 Windows](../../mfc/frame-windows.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMDIFrameWnd`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="cmdiframewnd"></a>  CMDIFrameWnd::CMDIFrameWnd  
 构造 `CMDIFrameWnd` 对象。  
  
```  
CMDIFrameWnd();
```  
  
### <a name="remarks"></a>备注  
 调用`Create`或`LoadFrame`成员函数来创建可见的 MDI 框架窗口。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]  
  
##  <a name="createclient"></a>  CMDIFrameWnd::CreateClient  
 创建管理 MDI 客户端窗口`CMDIChildWnd`对象。  
  
```  
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,  
    CMenu* pWindowMenu);
```  
  
### <a name="parameters"></a>参数  
 *lpCreateStruct*  
 指向的长指针[CREATESTRUCT](../../mfc/reference/createstruct-structure.md)结构。  
  
 *pWindowMenu*  
 指向窗口弹出菜单的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果重写应调用此成员函数`OnCreate`直接成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]  
  
##  <a name="createnewchild"></a>  CMDIFrameWnd::CreateNewChild  
 创建一个新的子窗口。  
  
```  
CMDIChildWnd* CreateNewChild(
    CRuntimeClass* pClass,  
    UINT nResource,  
    HMENU hMenu = NULL,  
    HACCEL hAccel = NULL);
```  
  
### <a name="parameters"></a>参数  
 *pClass*  
 若要创建的子窗口的运行时类。  
  
 *资源*  
 与子窗口相关联的共享资源的 ID。  
  
 *hMenu*  
 子窗口的菜单。  
  
 *hAccel*  
 子窗口的快捷键。  
  
### <a name="remarks"></a>备注  
 使用此函数以创建子窗口的 MDI 框架窗口。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]  
  
 此示例摘自知识库文章 Q201045，"如何： 将多个窗口类型添加到非文档/视图 MDI 应用程序。" 知识库文章位于[ http://support.microsoft.com ](http://support.microsoft.com/)。  
  
##  <a name="getwindowmenupopup"></a>  CMDIFrameWnd::GetWindowMenuPopup  
 调用此成员函数可获取名为"窗口"（使用 MDI 窗口管理的菜单项的弹出菜单） 的当前弹出菜单的句柄。  
  
```  
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```  
  
### <a name="parameters"></a>参数  
 *hMenuBar*  
 当前的菜单栏。  
  
### <a name="return-value"></a>返回值  
 窗口弹出菜单，如果一个存在;否则为，为 NULL。  
  
### <a name="remarks"></a>备注  
 默认实现将查找包含标准窗口菜单命令，如 ID_WINDOW_NEW 和 ID_WINDOW_TILE_HORZ 的弹出菜单。  
  
 重写此成员函数，如果您有一个不使用标准的菜单命令 Id 的窗口菜单。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]  
  
##  <a name="mdiactivate"></a>  CMDIFrameWnd::MDIActivate  
 激活一个不同的 MDI 子窗口。  
  
```  
void MDIActivate(CWnd* pWndActivate);
```  
  
### <a name="parameters"></a>参数  
 *pWndActivate*  
 指向要激活的 MDI 子窗口。  
  
### <a name="remarks"></a>备注  
 此成员函数将发送[WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate)到子窗口被激活并在停用的子窗口的消息。  
  
 这是当用户更改焦点通过使用鼠标或键盘的 MDI 子窗口发送同一消息。  
  
> [!NOTE]
>  独立于 MDI 框架窗口被激活的 MDI 子窗口。 当帧变为活动状态时，发送的子窗口的上一次激活[WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate)消息来绘制活动窗口框架和标题栏中，但它不会收到另一 WM_MDIACTIVATE 条消息。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)。  
  
##  <a name="mdicascade"></a>  CMDIFrameWnd::MDICascade  
 排列的级联格式中的所有 MDI 子窗口。  
  
```  
void MDICascade();  
void MDICascade(int nType);
```  
  
### <a name="parameters"></a>参数  
 *n 类型*  
 指定级联标志。 可以指定仅以下标志： MDITILE_SKIPDISABLED，这样可防止已禁用的 MDI 子窗口正在级联。  
  
### <a name="remarks"></a>备注  
 第一个版本`MDICascade`，不带任何参数，操作将级联所有 MDI 子窗口，其中包括已禁用的。 第二个版本可以选择不禁用的级联 MDI 子窗口，如果指定为 MDITILE_SKIPDISABLED *n 类型*参数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]  
  
##  <a name="mdigetactive"></a>  CMDIFrameWnd::MDIGetActive  
 检索当前活动的 MDI 子窗口，以及一个标志，指示子窗口已最大化。  
  
```  
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;  
```  
  
### <a name="parameters"></a>参数  
 *pbMaximized*  
 指向一个布尔值的返回值。 如果该窗口最大化; 返回时设置为 TRUE否则为 FALSE。  
  
### <a name="return-value"></a>返回值  
 指向活动的 MDI 子窗口的指针。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize)。  
  
##  <a name="mdiiconarrange"></a>  CMDIFrameWnd::MDIIconArrange  
 排列所有最小化的文档子窗口。  
  
```  
void MDIIconArrange();
```  
  
### <a name="remarks"></a>备注  
 它不会影响不最小化的子窗口。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[CMDIFrameWnd::MDICascade](#mdicascade)。  
  
##  <a name="mdimaximize"></a>  CMDIFrameWnd::MDIMaximize  
 最大化指定的 MDI 子窗口。  
  
```  
void MDIMaximize(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 *pWnd*  
 指向窗口将最大化。  
  
### <a name="remarks"></a>备注  
 当子窗口已最大化时，Windows 调整大小以使其填充客户端窗口的工作区。 Windows 将在菜单栏中帧的子窗口的控制菜单，这样用户可以还原或者关闭子窗口。 它还添加到框架窗口标题的子窗口的标题。  
  
 如果另一个 MDI 子窗口已激活当前处于活动状态的 MDI 子窗口最大化时，Windows 还原当前处于活动状态的子，并将新激活的子窗口最大化。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize)。  
  
##  <a name="mdinext"></a>  CMDIFrameWnd::MDINext  
 激活立即隐藏当前处于活动状态的子窗口的子窗口，并将当前处于活动状态的子窗口放在所有其他子窗口的后面。  
  
```  
void MDINext();
```  
  
### <a name="remarks"></a>备注  
 如果当前处于活动状态的 MDI 子窗口已最大化，成员函数将恢复当前处于活动状态的子，并将新激活的子最大化。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]  
  
##  <a name="mdiprev"></a>  CMDIFrameWnd::MDIPrev  
 激活上一个子窗口，并将其背后当前处于活动状态的子窗口。  
  
```  
void MDIPrev();
```  
  
### <a name="remarks"></a>备注  
 如果当前处于活动状态的 MDI 子窗口已最大化，成员函数将恢复当前处于活动状态的子，并将新激活的子最大化。  
  
##  <a name="mdirestore"></a>  CMDIFrameWnd::MDIRestore  
 最大化或最小化大小从还原的 MDI 子窗口。  
  
```  
void MDIRestore(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 *pWnd*  
 指向要还原的窗口。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[CMDIChildWnd::MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore)。  
  
##  <a name="mdisetmenu"></a>  CMDIFrameWnd::MDISetMenu  
 替代了 MDI 框架窗口的菜单、 窗口弹出菜单中，或两者。  
  
```  
CMenu* MDISetMenu(
    CMenu* pFrameMenu,  
    CMenu* pWindowMenu);
```  
  
### <a name="parameters"></a>参数  
 *pFrameMenu*  
 指定新的框架窗口菜单的菜单。 如果为 NULL，菜单不会更改。  
  
 *pWindowMenu*  
 指定新的窗口弹出菜单的菜单。 如果为 NULL，菜单不会更改。  
  
### <a name="return-value"></a>返回值  
 指向替换为此消息的框架窗口菜单的指针。 该指针可能是暂时的，不应存储起来供将来使用。  
  
### <a name="remarks"></a>备注  
 在调用`MDISetMenu`，应用程序必须调用[DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)成员函数的`CWnd`更新菜单栏。  
  
 如果此调用将替换窗口弹出菜单，MDI 子窗口菜单项是从以前的窗口菜单中删除和添加到新的窗口弹出菜单。  
  
 如果最大化的 MDI 子窗口，此调用将替换 MDI 框架窗口菜单控件菜单，然后还原控件是从以前的框架窗口菜单中删除和添加到新的菜单。  
  
 如果使用框架来管理 MDI 子窗口，则不调用此成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]  
  
##  <a name="mditile"></a>  CMDIFrameWnd::MDITile  
 排列在平铺格式中的所有子窗口。  
  
```  
void MDITile();  
void MDITile(int nType);
```  
  
### <a name="parameters"></a>参数  
 *n 类型*  
 指定平铺标志。 此参数可以是下列标志之一：  
  
- 使该窗口显示上面另一个 MDITILE_HORIZONTAL 磁贴 MDI 子窗口。  
  
- MDITILE_SKIPDISABLED 会阻止禁用从正在平铺的 MDI 子窗口。  
  
- MDITILE_VERTICAL 磁贴 MDI 子窗口以便该窗口将出现另一个的旁边。  
  
### <a name="remarks"></a>备注  
 第一个版本`MDITile`，不带参数，平铺窗口垂直下 Windows 3.1 及更高版本。 第二个版本平铺窗口垂直或水平，具体取决于值*n 类型*参数。  
  
### <a name="example"></a>示例  
 有关示例，请参阅[CMDIFrameWnd::MDICascade](#mdicascade)。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 MDI](../../visual-cpp-samples.md)   
 [MFC 示例 MDIDOCVW](../../visual-cpp-samples.md)   
 [MFC 示例 SNAPVW](../../visual-cpp-samples.md)   
 [CFrameWnd 类](../../mfc/reference/cframewnd-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CMDIChildWnd 类](../../mfc/reference/cmdichildwnd-class.md)
