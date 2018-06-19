---
title: CMDIFrameWnd 类 |Microsoft 文档
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
ms.openlocfilehash: 7bb9f87ed5ae3027e7743a36c2484017d6381f95
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374034"
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
|[CMDIFrameWnd::CreateClient](#createclient)|创建 Windows **MDICLIENT**此窗口`CMDIFrameWnd`。 由调用`OnCreate`成员函数`CWnd`。|  
|[CMDIFrameWnd::CreateNewChild](#createnewchild)|创建一个新的子窗口。|  
|[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)|返回窗口弹出菜单。|  
|[CMDIFrameWnd::MDIActivate](#mdiactivate)|激活一个不同的 MDI 子窗口。|  
|[CMDIFrameWnd::MDICascade](#mdicascade)|排列的级联格式中的所有子窗口。|  
|[CMDIFrameWnd::MDIGetActive](#mdigetactive)|检索当前处于活动状态的 MDI 子窗口，同时还有一个标志，指示子最大化。|  
|[CMDIFrameWnd::MDIIconArrange](#mdiiconarrange)|排列所有最小化的文档子窗口。|  
|[CMDIFrameWnd::MDIMaximize](#mdimaximize)|最大化 MDI 子窗口。|  
|[CMDIFrameWnd::MDINext](#mdinext)|激活立即后面当前处于活动状态的子窗口的子窗口，并将当前处于活动状态的子窗口放在所有其他子窗口的后面。|  
|[CMDIFrameWnd::MDIPrev](#mdiprev)|激活上一个子窗口，并将其背后的当前活动子窗口。|  
|[CMDIFrameWnd::MDIRestore](#mdirestore)|最大化或最小化大小从还原的 MDI 子窗口。|  
|[CMDIFrameWnd::MDISetMenu](#mdisetmenu)|MDI 框架窗口的菜单和 / 或窗口弹出菜单中，替换。|  
|[CMDIFrameWnd::MDITile](#mditile)|所有子以都排列窗口平铺的格式。|  
  
## <a name="remarks"></a>备注  
 若要创建你的应用程序有用 MDI 框架窗口，从派生类`CMDIFrameWnd`。 将成员变量添加到派生的类，以存储特定于你的应用程序数据。 可派生类中实现消息处理程序成员函数和消息映射，以指定在消息定向到窗口时所发生的情况。  
  
 您可以通过调用构造 MDI 框架窗口[创建](../../mfc/reference/cframewnd-class.md#create)或[LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)成员函数`CFrameWnd`。  
  
 在调用之前**创建**或`LoadFrame`，您必须先构造使用 c + + 堆上的框架窗口对象**新**运算符。 之前调用**创建**还可以注册窗口类[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全局函数，若要设置帧的图标和类样式。  
  
 使用**创建**成员函数将为快速的自变量传递帧的创建参数。  
  
 `LoadFrame` 需要更少的自变量比**创建**，并改为从资源，包括帧的标题、 图标、 快捷键对应表和菜单中检索大多数其默认值。 为可供`LoadFrame`，所有这些资源必须具有相同的资源 ID (例如， **IDR_MAINFRAME**)。  
  
 尽管**MDIFrameWnd**派生自`CFrameWnd`，框架窗口类派生自`CMDIFrameWnd`不需要使用声明`DECLARE_DYNCREATE`。  
  
 `CMDIFrameWnd`类继承从其默认实现大部分`CFrameWnd`。 有关这些功能的详细列表，请参阅[CFrameWnd](../../mfc/reference/cframewnd-class.md)类的说明。 `CMDIFrameWnd`类具有下列附加功能：  
  
-   MDI 框架窗口管理**MDICLIENT**窗口中，其进行重新定位控件条结合。 MDI 客户端窗口是直接 MDI 子框架窗口的父级。 **WS_HSCROLL**和**WS_VSCROLL**中指定的窗口样式`CMDIFrameWnd`适用于 MDI 客户端窗口，而不是主框架窗口，以便用户可以滚动 （如 Windows 的 MDI 客户端区域例如程序管理器中，）。  
  
-   MDI 框架窗口拥有一个默认菜单，在没有任何活动的 MDI 子窗口时用作菜单栏。 如果没有活动 MDI 子窗体，MDI 框架窗口的菜单栏会自动替换 MDI 子窗口菜单。  
  
-   MDI 框架窗口结合使用与当前 MDI 子窗口，如果有一个。 例如，命令消息委托给当前活动 MDI 子窗体之前 MDI 框架窗口。  
  
-   MDI 框架窗口具有下列标准窗口菜单命令的默认处理程序：  
  
    - **ID_WINDOW_TILE_VERT**  
  
    - **ID_WINDOW_TILE_HORZ**  
  
    - **ID_WINDOW_CASCADE**  
  
    - **ID_WINDOW_ARRANGE**  
  
-   MDI 框架窗口还提供了的实现**ID_WINDOW_NEW**，这将创建一个新帧和当前文档的视图。 应用程序可以重写这些默认命令实现，以自定义 MDI 窗口处理。  
  
 不使用 c + +**删除**运算符销毁框架窗口。 请改用 `CWnd::DestroyWindow`。 `CFrameWnd`实现`PostNcDestroy`销毁窗口时，将删除 c + + 对象。 当用户关闭帧窗口时，默认值`OnClose`处理程序将调用`DestroyWindow`。  
  
 有关详细信息`CMDIFrameWnd`，请参阅[框架窗口](../../mfc/frame-windows.md)。  
  
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
 调用**创建**或`LoadFrame`成员函数来创建可见的 MDI 框架窗口。  
  
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
 `lpCreateStruct`  
 指向的长指针[CREATESTRUCT](../../mfc/reference/createstruct-structure.md)结构。  
  
 `pWindowMenu`  
 指向窗口弹出菜单的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果你重写应调用此成员函数`OnCreate`直接成员函数。  
  
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
 `pClass`  
 要创建的子窗口运行时类。  
  
 *nResource*  
 与子窗口关联的共享资源的 ID。  
  
 `hMenu`  
 子窗口的菜单。  
  
 `hAccel`  
 子窗口的快捷键。  
  
### <a name="remarks"></a>备注  
 此函数用于创建子窗口的 MDI 框架窗口。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]  
  
 此示例摘自知识库文章 Q201045，"如何： 将多个窗口类型添加到非文档/视图 MDI 应用程序。" 知识库文章位于[ http://support.microsoft.com ](http://support.microsoft.com/)。  
  
##  <a name="getwindowmenupopup"></a>  CMDIFrameWnd::GetWindowMenuPopup  
 调用此成员函数可获取名为"窗口"（与 MDI 窗口管理的菜单项的弹出菜单） 的当前弹出菜单的句柄。  
  
```  
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```  
  
### <a name="parameters"></a>参数  
 *hMenuBar*  
 当前的菜单栏中。  
  
### <a name="return-value"></a>返回值  
 如果一个窗口弹出菜单存在;否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 默认实现查找如包含标准窗口菜单命令的弹出菜单**ID_WINDOW_NEW**和**ID_WINDOW_TILE_HORZ**。  
  
 如果你有一个不使用标准菜单命令 Id 的窗口菜单，重写该成员函数。  
  
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
 此成员函数将发送[WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate)正在激活的子窗口和正在停用的子窗口的消息。  
  
 这是，如果用户将焦点更改到 MDI 子窗口通过使用鼠标或键盘发送同一条消息。  
  
> [!NOTE]
>  MDI 子窗口激活独立于 MDI 框架窗口中。 当帧变为活动状态时，发送的子窗口的上次激活[WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate)消息来绘制活动窗口框架和标题栏中，但它不会收到另一个`WM_MDIACTIVATE`消息。  
  
### <a name="example"></a>示例  
 请参阅示例[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)。  
  
##  <a name="mdicascade"></a>  CMDIFrameWnd::MDICascade  
 排列 cascade 格式中的所有 MDI 子窗口。  
  
```  
void MDICascade();  
void MDICascade(int nType);
```  
  
### <a name="parameters"></a>参数  
 `nType`  
 指定级联标志。 可以指定仅以下标志： `MDITILE_SKIPDISABLED`，从而防止已禁用的 MDI 子窗口正在级联。  
  
### <a name="remarks"></a>备注  
 第一个版本`MDICascade`，不带任何参数，级联所有 MDI 子窗口，包括已禁用的。 第二个版本 （可选） 不禁用的级联 MDI 子窗口，如果你指定`MDITILE_SKIPDISABLED`为`nType`参数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]  
  
##  <a name="mdigetactive"></a>  CMDIFrameWnd::MDIGetActive  
 检索当前活动 MDI 子窗口，以及一个标志，指示子窗口是否最大化。  
  
```  
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;  
```  
  
### <a name="parameters"></a>参数  
 *pbMaximized*  
 指向的指针**BOOL**返回值。 设置为**TRUE**如果的窗口为最大化; 否则为返回**FALSE**。  
  
### <a name="return-value"></a>返回值  
 指向活动的 MDI 子窗口的指针。  
  
### <a name="example"></a>示例  
 请参阅示例[CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize)。  
  
##  <a name="mdiiconarrange"></a>  CMDIFrameWnd::MDIIconArrange  
 排列所有最小化的文档子窗口。  
  
```  
void MDIIconArrange();
```  
  
### <a name="remarks"></a>备注  
 它不会影响不最小化的子窗口。  
  
### <a name="example"></a>示例  
 请参阅示例[CMDIFrameWnd::MDICascade](#mdicascade)。  
  
##  <a name="mdimaximize"></a>  CMDIFrameWnd::MDIMaximize  
 将指定的 MDI 子窗口最大化。  
  
```  
void MDIMaximize(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向窗口将最大化。  
  
### <a name="remarks"></a>备注  
 当子窗口最大化时，Windows 调整大小以使客户端窗口填充其工作区。 Windows 会将子窗口控件菜单放在帧的菜单栏中，以便用户可以恢复或关闭子窗口。 此外，它还会将子窗口的标题添加到框架窗口标题。  
  
 如果另一个 MDI 子窗口激活当前处于活动状态的 MDI 子窗口最大化时，Windows 将还原当前活动子窗体，并将新激活的子窗口最大化。  
  
### <a name="example"></a>示例  
 请参阅示例[CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize)。  
  
##  <a name="mdinext"></a>  CMDIFrameWnd::MDINext  
 激活立即后面当前处于活动状态的子窗口的子窗口，并将当前处于活动状态的子窗口放在所有其他子窗口的后面。  
  
```  
void MDINext();
```  
  
### <a name="remarks"></a>备注  
 如果当前活动的 MDI 子窗口最大化时，成员函数将还原当前活动子窗体，并将新激活的子最大化。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]  
  
##  <a name="mdiprev"></a>  CMDIFrameWnd::MDIPrev  
 激活上一个子窗口，并将其背后的当前活动子窗口。  
  
```  
void MDIPrev();
```  
  
### <a name="remarks"></a>备注  
 如果当前活动的 MDI 子窗口最大化时，成员函数将还原当前活动子窗体，并将新激活的子最大化。  
  
##  <a name="mdirestore"></a>  CMDIFrameWnd::MDIRestore  
 最大化或最小化大小从还原的 MDI 子窗口。  
  
```  
void MDIRestore(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向要还原的窗口。  
  
### <a name="example"></a>示例  
 请参阅示例[CMDIChildWnd::MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore)。  
  
##  <a name="mdisetmenu"></a>  CMDIFrameWnd::MDISetMenu  
 MDI 框架窗口的菜单和 / 或窗口弹出菜单中，替换。  
  
```  
CMenu* MDISetMenu(
    CMenu* pFrameMenu,  
    CMenu* pWindowMenu);
```  
  
### <a name="parameters"></a>参数  
 *pFrameMenu*  
 指定新的框架窗口菜单的菜单。 如果**NULL**，菜单不会更改。  
  
 `pWindowMenu`  
 指定新的窗口弹出菜单的菜单。 如果**NULL**，菜单不会更改。  
  
### <a name="return-value"></a>返回值  
 指向替换为此消息的框架窗口菜单的指针。 该指针可能是暂时的，不应存储起来供将来使用。  
  
### <a name="remarks"></a>备注  
 在调用`MDISetMenu`，应用程序必须调用[DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar)成员函数`CWnd`更新菜单栏。  
  
 如果此调用将替换窗口弹出菜单，MDI 子窗口菜单项会从以前的窗口菜单中删除并添加到新的窗口弹出菜单。  
  
 如果 MDI 子窗口最大化，并且此调用将替换 MDI 框架窗口菜单上，会从以前的框架窗口菜单中删除控件菜单和还原控件并将其添加到新的菜单。  
  
 如果你使用框架来管理你的 MDI 子窗口，请勿调用此成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]  
  
##  <a name="mditile"></a>  CMDIFrameWnd::MDITile  
 所有子以都排列窗口平铺的格式。  
  
```  
void MDITile();  
void MDITile(int nType);
```  
  
### <a name="parameters"></a>参数  
 `nType`  
 指定一个平铺标志。 此参数可以是任何一种以下标志：  
  
- `MDITILE_HORIZONTAL` 磁贴 MDI 子窗口使该窗口显示上面另一个。  
  
- `MDITILE_SKIPDISABLED` 正在平铺会阻止已禁用的 MDI 子窗口。  
  
- `MDITILE_VERTICAL` 磁贴 MDI 子窗口以便该窗口显示另一个的旁边。  
  
### <a name="remarks"></a>备注  
 第一个版本`MDITile`，不带参数，平铺窗口垂直下 Windows 版本 3.1 和更高版本。 第二个版本平铺窗口垂直或水平，具体取决于值`nType`参数。  
  
### <a name="example"></a>示例  
 请参阅示例[CMDIFrameWnd::MDICascade](#mdicascade)。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 MDI](../../visual-cpp-samples.md)   
 [MFC 示例 MDIDOCVW](../../visual-cpp-samples.md)   
 [MFC 示例 SNAPVW](../../visual-cpp-samples.md)   
 [CFrameWnd 类](../../mfc/reference/cframewnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CMDIChildWnd 类](../../mfc/reference/cmdichildwnd-class.md)
