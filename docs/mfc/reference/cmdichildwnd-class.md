---
title: "CMDIChildWnd 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMDIChildWnd
dev_langs:
- C++
helpviewer_keywords:
- MDI [C++], child windows
- windows [C++], MDI
- CMDIChildWnd class
- child windows, CMDIChildWnd class
ms.assetid: 6d07f5d4-9a3e-4723-9fa5-e65bb669fdd5
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 240af1fe5f3afa4cdb7d4d585dc74cc4836799cc
ms.lasthandoff: 02/24/2017

---
# <a name="cmdichildwnd-class"></a>CMDIChildWnd 类
提供 Windows 多文档界面 (MDI) 子窗口功能，并提供管理窗口的成员。  
  
## <a name="syntax"></a>语法  
  
```  
class CMDIChildWnd : public CFrameWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMDIChildWnd::CMDIChildWnd](#cmdichildwnd)|构造 `CMDIChildWnd` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMDIChildWnd::Create](#create)|创建与关联的 Windows MDI 子窗口`CMDIChildWnd`对象。|  
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|返回的父级的 MDI 客户端窗口的 MDI 框架。|  
|[CMDIChildWnd::MDIActivate](#mdiactivate)|激活此 MDI 子窗口。|  
|[CMDIChildWnd::MDIDestroy](#mdidestroy)|销毁此 MDI 子窗口。|  
|[CMDIChildWnd::MDIMaximize](#mdimaximize)|最大化此 MDI 子窗口。|  
|[CMDIChildWnd::MDIRestore](#mdirestore)|将已最大化或最小化大小中还原此 MDI 子窗口。|  
|[CMDIChildWnd::SetHandles](#sethandles)|设置菜单和快捷键资源的句柄。|  
  
## <a name="remarks"></a>备注  
 MDI 子窗口看上去像一个典型的框架窗口，只不过 MDI 子窗口将显示在 MDI 框架窗口而不是在桌面上。 MDI 子窗口不具有其自己的菜单栏，但改为共享 MDI 框架窗口的菜单。 框架将自动更改来表示当前处于活动状态的 MDI 子窗口的 MDI 框架菜单。  
  
 若要创建您的应用程序的有用 MDI 子窗口，从派生类`CMDIChildWnd`。 将成员变量添加到派生的类来存储特定于您的应用程序的数据。 可派生类中实现消息处理程序成员函数和消息映射，以指定在消息定向到窗口时所发生的情况。  
  
 有三种方法来构造的 MDI 子窗口︰  
  
-   直接构造使用**创建**。  
  
-   直接构造使用`LoadFrame`。  
  
-   间接构造通过文档模板。  
  
 在调用之前**创建**或`LoadFrame`，您必须先构造使用 c + + 堆上的框架窗口对象**新**运算符。 之前，先调用**创建**还可以注册窗口类[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全局函数可设置的帧图标和类样式。  
  
 使用**创建**成员函数以将为快速参数传递的帧的创建参数。  
  
 `LoadFrame`需要较少的参数比**创建**，并改为从资源，包括框架的标题、 图标、 快捷键对应表和菜单检索大部分其默认值。 可由`LoadFrame`，所有这些资源都必须具有相同的资源 ID (例如， **IDR_MAINFRAME**)。  
  
 当`CMDIChildWnd`对象包含视图和文档，就会创建间接的框架，而不是直接由程序员。 `CDocTemplate`对象协调的框架的创建、 包含视图的创建和连接到相应的文档的视图。 参数`CDocTemplate`构造函数指定`CRuntimeClass`的三个类涉及 （文档、 框架和视图）。 一个`CRuntimeClass`框架使用对象来动态地创建新帧时由用户指定 （例如，通过使用新建文件命令或 MDI 窗口新建命令）。  
  
 框架窗口类派生自`CMDIChildWnd`必须使用声明`DECLARE_DYNCREATE`使上述`RUNTIME_CLASS`机制才能正常工作。  
  
 `CMDIChildWnd`类继承从其默认实现大部分`CFrameWnd`。 有关这些功能的详细列表，请参阅[CFrameWnd](../../mfc/reference/cframewnd-class.md)类的说明。 `CMDIChildWnd`类具有下列附加功能︰  
  
-   结合`CMultiDocTemplate`类，多个`CMDIChildWnd`从同一个文档模板对象共享相同的菜单上，保存 Windows 系统资源。  
  
-   当前处于活动状态的 MDI 子窗口菜单完全替换 MDI 框架窗口的菜单上，并且当前处于活动状态的 MDI 子窗口的标题添加到 MDI 框架窗口的标题。 实现结合 MDI 框架窗口的 MDI 子窗口函数的其他示例，请参阅`CMDIFrameWnd`类的说明。  
  
 请不要使用 c + +**删除**要销毁框架窗口的运算符。 请改用 `CWnd::DestroyWindow` 。 `CFrameWnd`实现`PostNcDestroy`销毁窗口时，将删除 c + + 对象。 当用户关闭帧窗口时，默认值`OnClose`处理程序将调用`DestroyWindow`。  
  
 有关详细信息`CMDIChildWnd`，请参阅[框架窗口](../../mfc/frame-windows.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMDIChildWnd`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="a-namecmdichildwnda--cmdichildwndcmdichildwnd"></a><a name="cmdichildwnd"></a>CMDIChildWnd::CMDIChildWnd  
 调用以构造`CMDIChildWnd`对象。  
  
```  
CMDIChildWnd();
```  
  
### <a name="remarks"></a>备注  
 调用**创建**来创建可见的窗口。  
  
### <a name="example"></a>示例  
  请参阅示例[CMDIChildWnd::Create](#create)。  
  
##  <a name="a-namecreatea--cmdichildwndcreate"></a><a name="create"></a>CMDIChildWnd::Create  
 调用此成员函数以创建一个 Windows MDI 子窗口，并将其附加到`CMDIChildWnd`对象。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_OVERLAPPEDWINDOW,  
    const RECT& rect = rectDefault,  
    CMDIFrameWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszClassName`  
 指向 null 结尾的字符串名称的 Windows 类 string ( [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)结构)。 类名可以是任何名称注册[AfxRegisterWndClass](http://msdn.microsoft.com/library/62c7d4b1-7a29-4abb-86f7-dec541659db0)全局函数。 应为**NULL**标准`CMDIChildWnd`。  
  
 `lpszWindowName`  
 指向以 null 结尾的字符串表示窗口名称。 用作标题栏文本。  
  
 `dwStyle`  
 指定的窗口[样式](../../mfc/reference/window-styles.md)属性。 **WS_CHILD**样式是必需的。  
  
 `rect`  
 包含的大小和窗口的位置。 `rectDefault`值使 Windows 可以指定的大小和位置的新`CMDIChildWnd`。  
  
 `pParentWnd`  
 指定窗口的父级。 如果**NULL**，使用主应用程序窗口。  
  
 `pContext`  
 指定[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构。 此参数可以为**NULL**。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 当前处于活动状态的 MDI 子框架窗口可以确定父框架窗口的标题。 此功能被禁用通过关闭**FWS_ADDTOTITLE**子框架窗口样式位。  
  
 框架调用此成员函数以响应用户命令创建一个子窗口，并使用该框架`pContext`参数以便正确地连接到应用程序的子窗口。 当您调用**创建**，`pContext`可以是**NULL**。  
  
### <a name="example"></a>示例  
 示例 1:  
  
 [!code-cpp[NVC_MFCWindowing #&7;](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]  
  
### <a name="example"></a>示例  
 示例 2：  
  
 [!code-cpp[NVC_MFCWindowing #&8;](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing #&9;](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]  
  
##  <a name="a-namegetmdiframea--cmdichildwndgetmdiframe"></a><a name="getmdiframe"></a>CMDIChildWnd::GetMDIFrame  
 调用此函数可返回 MDI 父框架。  
  
```  
CMDIFrameWnd* GetMDIFrame();
```  
  
### <a name="return-value"></a>返回值  
 指向 MDI 父框架窗口的指针。  
  
### <a name="remarks"></a>备注  
 返回的帧是从删除的两个父级`CMDIChildWnd`是类型的窗口的父级**MDICLIENT**管理`CMDIChildWnd`对象。 调用[GetParent](../../mfc/reference/cwnd-class.md#getparent)成员函数来返回`CMDIChildWnd`对象的即时**MDICLIENT**作为临时的父`CWnd`指针。  
  
### <a name="example"></a>示例  
  请参阅示例[CMDIFrameWnd::MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu)。  
  
##  <a name="a-namemdiactivatea--cmdichildwndmdiactivate"></a><a name="mdiactivate"></a>CMDIChildWnd::MDIActivate  
 调用该成员函数以激活独立于 MDI 框架窗口的 MDI 子窗口。  
  
```  
void MDIActivate();
```  
  
### <a name="remarks"></a>备注  
 当框架变为活动状态时，上次激活的子窗口也将被激活。  
  
### <a name="example"></a>示例  
  请参阅示例[CMDIFrameWnd::GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup)。  
  
##  <a name="a-namemdidestroya--cmdichildwndmdidestroy"></a><a name="mdidestroy"></a>CMDIChildWnd::MDIDestroy  
 调用此成员函数要销毁的 MDI 子窗口。  
  
```  
void MDIDestroy();
```  
  
### <a name="remarks"></a>备注  
 成员函数从框架窗口中删除子窗口的标题，并停用的子窗口。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&10;](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]  
  
##  <a name="a-namemdimaximizea--cmdichildwndmdimaximize"></a><a name="mdimaximize"></a>CMDIChildWnd::MDIMaximize  
 调用该成员函数以最大化的 MDI 子窗口。  
  
```  
void MDIMaximize();
```  
  
### <a name="remarks"></a>备注  
 当子窗口最大化窗口时、 Windows 调整大小以使其工作区填充框架窗口的工作区。 Windows 将放子窗口的控制菜单在框架的菜单栏中，以便用户可以恢复或关闭的子窗口，并将子窗口的标题添加到框架窗口标题。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&11;](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]  
  
##  <a name="a-namemdirestorea--cmdichildwndmdirestore"></a><a name="mdirestore"></a>CMDIChildWnd::MDIRestore  
 调用该成员函数以最大化或最小化大小从还原的 MDI 子窗口。  
  
```  
void MDIRestore();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&12;](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]  
  
##  <a name="a-namesethandlesa--cmdichildwndsethandles"></a><a name="sethandles"></a>CMDIChildWnd::SetHandles  
 设置菜单和快捷键资源的句柄。  
  
```  
void SetHandles(
    HMENU hMenu,  
    HACCEL hAccel);
```  
  
### <a name="parameters"></a>参数  
 `hMenu`  
 菜单资源的句柄。  
  
 `hAccel`  
 快捷键资源句柄。  
  
### <a name="remarks"></a>备注  
 调用此函数可设置的 MDI 子窗口对象使用的菜单和快捷键资源。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 MDI](../../visual-cpp-samples.md)   
 [MFC 示例 MDIDOCVW](../../visual-cpp-samples.md)   
 [MFC 示例 SNAPVW](../../visual-cpp-samples.md)   
 [CFrameWnd 类](../../mfc/reference/cframewnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CMDIFrameWnd 类](../../mfc/reference/cmdiframewnd-class.md)

