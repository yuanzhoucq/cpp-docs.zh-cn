---
title: "CMDIFrameWnd Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMDIFrameWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMDIFrameWnd class"
  - "MDI frame windows"
ms.assetid: fa8736e6-511b-4c51-8b4d-eba78378aeb9
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CMDIFrameWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows多线程的功能与管理窗口的成员一起文档界面\(MDI\)框架窗口。  
  
## 语法  
  
```  
class CMDIFrameWnd : public CFrameWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMDIFrameWnd::CMDIFrameWnd](../Topic/CMDIFrameWnd::CMDIFrameWnd.md)|构造 `CMDIFrameWnd`。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMDIFrameWnd::CreateClient](../Topic/CMDIFrameWnd::CreateClient.md)|创建此 `CMDIFrameWnd`的Windows **MDICLIENT** 窗口。  调用 `CWnd`的 `OnCreate` 成员函数。|  
|[CMDIFrameWnd::CreateNewChild](../Topic/CMDIFrameWnd::CreateNewChild.md)|创建新的子窗口。|  
|[CMDIFrameWnd::GetWindowMenuPopup](../Topic/CMDIFrameWnd::GetWindowMenuPopup.md)|返回窗口弹出菜单。|  
|[CMDIFrameWnd::MDIActivate](../Topic/CMDIFrameWnd::MDIActivate.md)|激活不同的MDI子窗口。|  
|[CMDIFrameWnd::MDICascade](../Topic/CMDIFrameWnd::MDICascade.md)|让所有子窗口会级联样式表的格式。|  
|[CMDIFrameWnd::MDIGetActive](../Topic/CMDIFrameWnd::MDIGetActive.md)|具有指定子元素是否的标志一起检索当前活动的MDI子窗口，最大化。|  
|[CMDIFrameWnd::MDIIconArrange](../Topic/CMDIFrameWnd::MDIIconArrange.md)|具有最小化的所有文档子窗口。|  
|[CMDIFrameWnd::MDIMaximize](../Topic/CMDIFrameWnd::MDIMaximize.md)|关闭MDI子窗口。|  
|[CMDIFrameWnd::MDINext](../Topic/CMDIFrameWnd::MDINext.md)|活动子窗口立即在当前活动子窗口之后并在其他子窗口后将当前活动的子窗口。|  
|[CMDIFrameWnd::MDIPrev](../Topic/CMDIFrameWnd::MDIPrev.md)|激活前面的子窗口并立即在之后将当前活动的子窗口。|  
|[CMDIFrameWnd::MDIRestore](../Topic/CMDIFrameWnd::MDIRestore.md)|还原从最大化或最小化范围的MDI子窗口。|  
|[CMDIFrameWnd::MDISetMenu](../Topic/CMDIFrameWnd::MDISetMenu.md)|替换MDI框架窗口中的菜单上，窗口弹出菜单或两个。|  
|[CMDIFrameWnd::MDITile](../Topic/CMDIFrameWnd::MDITile.md)|让所有子窗口以平铺的格式。|  
  
## 备注  
 若要创建应用程序的一个有用的MDI框架窗口中，从 `CMDIFrameWnd`派生选件类。  添加成员变量添加到派生类来存储数据特定于您的应用程序。  实现消息处理程序成员函数和消息映射在派生类指定发生的情况，在处理消息到windows时。  
  
 通过调用 `CFrameWnd`的 [创建](../Topic/CFrameWnd::Create.md) 或 [LoadFrame](../Topic/CFrameWnd::LoadFrame.md) 成员函数构造MDI框架窗口。  
  
 在调用 **Create** 或 `LoadFrame`之前，使用C\+\+ **new** 运算符，则必须生成堆中的框架窗口对象。  在调用 **Create** 之前可以注册窗口选件类。也将框架的图标和选件类样式的 [AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md) 全局函数。  
  
 使用 **Create** 成员函数通过帧的创建参数作为即时参数。  
  
 `LoadFrame` 比 **Create**需要的参数和从资源中检索大多数其默认值，包括帧的说明、图标、快捷键对应表和菜单。  将由 `LoadFrame`访问，所有这些资源必须具有相同的资源ID \(例如，**IDR\_MAINFRAME**）。  
  
 虽然 **MDIFrameWnd** 从 `CFrameWnd`派生，框架窗口选件类从派生 `CMDIFrameWnd` 了不需要声明与 `DECLARE_DYNCREATE`。  
  
 `CMDIFrameWnd` 选件类继承 `CFrameWnd`的默认实现。  对于这些函数详细列表，请参见 [CFrameWnd](../../mfc/reference/cframewnd-class.md) 选件类声明。  `CMDIFrameWnd` 选件类具有以下附加功能:  
  
-   MDI框架窗口管理 **MDICLIENT** 窗口，重新定位其与控件条结合使用。  MDI客户端窗口是MDI子框架窗口直接父级。  在 `CMDIFrameWnd` 指定的 **WS\_HSCROLL** 和 **WS\_VSCROLL** 窗口样式应用于MDI客户端窗口而不是主框架窗口，以便用户可以移动MDI工作区\(例如在Windows管理器，）。  
  
-   MDI框架窗口拥有用作菜单栏的默认菜单，而没有活动的MDI子窗口时。  当具有活动的MDI子窗体时，MDI框架窗口菜单栏中MDI子窗口菜单自动替换。  
  
-   如果有一个，MDI框架窗口与当前MDI子窗口一同。  例如，命令消息将委托对MDI框架窗口之前的当前活动的MDI子窗体。  
  
-   MDI框架窗口具有以下标准windows菜单命令的默认处理程序:  
  
    -   **ID\_WINDOW\_TILE\_VERT**  
  
    -   **ID\_WINDOW\_TILE\_HORZ**  
  
    -   **ID\_WINDOW\_CASCADE**  
  
    -   **ID\_WINDOW\_ARRANGE**  
  
-   MDI框架窗口还有 **ID\_WINDOW\_NEW**的实现，创建新的帧，并且在当前文档的视图。  应用程序可以重写这些默认命令实现自定义MDI窗口操作。  
  
 不要使用C\+\+ **delete** 运算符销毁框架窗口。  请改用 `CWnd::DestroyWindow`。  当销毁，`PostNcDestroy` 的 `CFrameWnd` 实现会删除C\+\+对象窗口。  当用户关闭框架窗口，默认 `OnClose` 处理程序将调用 `DestroyWindow`。  
  
 有关 `CMDIFrameWnd`的更多信息，请参见 [Windows框架](../../mfc/frame-windows.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMDIFrameWnd`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC MDI示例](../../top/visual-cpp-samples.md)   
 [MFC MDIDOCVW示例](../../top/visual-cpp-samples.md)   
 [MFC SNAPVW示例](../../top/visual-cpp-samples.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CMDIChildWnd Class](../../mfc/reference/cmdichildwnd-class.md)