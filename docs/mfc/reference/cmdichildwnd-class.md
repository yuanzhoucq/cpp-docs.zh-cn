---
title: "CMDIChildWnd Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMDIChildWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "子窗口, CMDIChildWnd class"
  - "CMDIChildWnd class"
  - "MDI [C++], 子窗口"
  - "windows [C++], MDI"
ms.assetid: 6d07f5d4-9a3e-4723-9fa5-e65bb669fdd5
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMDIChildWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows多线程的功能与管理窗口的成员。\(MDI\)文档界面\(mdi\)子窗口。  
  
## 语法  
  
```  
class CMDIChildWnd : public CFrameWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMDIChildWnd::CMDIChildWnd](../Topic/CMDIChildWnd::CMDIChildWnd.md)|构造 `CMDIChildWnd` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMDIChildWnd::Create](../Topic/CMDIChildWnd::Create.md)|创建Windows MDI子窗口与 `CMDIChildWnd` 对象。|  
|[CMDIChildWnd::GetMDIFrame](../Topic/CMDIChildWnd::GetMDIFrame.md)|返回MDI客户端窗口的父MDI框架。|  
|[CMDIChildWnd::MDIActivate](../Topic/CMDIChildWnd::MDIActivate.md)|激活此MDI子窗口。|  
|[CMDIChildWnd::MDIDestroy](../Topic/CMDIChildWnd::MDIDestroy.md)|销毁此MDI子窗口。|  
|[CMDIChildWnd::MDIMaximize](../Topic/CMDIChildWnd::MDIMaximize.md)|最大化此MDI子窗口。|  
|[CMDIChildWnd::MDIRestore](../Topic/CMDIChildWnd::MDIRestore.md)|还原从最大化或最小化范围的此MDI子窗口。|  
|[CMDIChildWnd::SetHandles](../Topic/CMDIChildWnd::SetHandles.md)|设置菜单和快捷键资源的句柄。|  
  
## 备注  
 MDI子窗口非常类似于典型的框架窗口，除此之外，MDI子窗口显示在MDI框架窗口中而不是在桌面。  MDI子窗口没有自己的菜单栏，表，而是共享MDI框架窗口的菜单。  框架会自动更改MDI框架菜单表示当前活动的MDI子窗口。  
  
 若要创建应用程序的一个有用的MDI子窗口，请 `CMDIChildWnd`派生选件类。  添加成员变量添加到派生类来存储数据特定于您的应用程序。  实现消息处理程序成员函数和消息映射在派生类指定发生的情况，在处理消息到windows时。  
  
 有三种构造MDI子窗口:  
  
-   使用 **Create**，请直接构造它。  
  
-   使用 `LoadFrame`，请直接构造它。  
  
-   将文档模板间接构造它。  
  
 在调用 **Create** 或 `LoadFrame`之前，使用C\+\+ **new** 运算符，则必须生成堆中的框架窗口对象。  在调用 **Create** 之前可以注册窗口选件类。也将框架的图标和选件类样式的 [AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md) 全局函数。  
  
 使用 **Create** 成员函数通过帧的创建参数作为即时参数。  
  
 `LoadFrame` 比 **Create**需要的参数和从资源中检索大多数其默认值，包括帧的说明、图标、快捷键对应表和菜单。  若要访问由 `LoadFrame`，所有这些资源必须具有相同的资源ID \(例如，**IDR\_MAINFRAME**）。  
  
 当 `CMDIChildWnd` 对象包含视图和文档时，它们是间接由框架创建的而不是直接程序员。  `CDocTemplate` 对象协调下帧，包含"视图中创建的创建，因此，视图的连接与相应文档。  `CDocTemplate` 构造函数的参数指定涉及的三选件类的 `CRuntimeClass` \(文档，则框架和视图）。  框架用于 `CRuntimeClass` 对象动态创建新框架，指定由用户\(例如，通过使用文件的命令或MDI窗口新的命令）。  
  
 必须声明从派生 `CMDIChildWnd` 框架窗口选件类与 `DECLARE_DYNCREATE` 为上面 `RUNTIME_CLASS` 结构才能正常工作。  
  
 `CMDIChildWnd` 选件类继承 `CFrameWnd`的默认实现。  对于这些函数详细列表，请参见 [CFrameWnd](../../mfc/reference/cframewnd-class.md) 选件类声明。  `CMDIChildWnd` 选件类具有以下附加功能:  
  
-   与 `CMultiDocTemplate` 选件类结合起来，从相同的多个 `CMDIChildWnd` 对象文档模板共享同一个菜单，保存Windows系统资源。  
  
-   当前活动的MDI子窗口菜单将完全替换MDI框架窗口菜单，并且，当前活动的MDI子窗口的标题添加到MDI框架窗口的标题。  有关MDI子与MDI框架窗口一起实现的windows函数的进一步示例，请参见 `CMDIFrameWnd` 选件类声明。  
  
 不要使用C\+\+ **delete** 运算符销毁框架窗口。  请改用 `CWnd::DestroyWindow`。  当销毁，`PostNcDestroy` 的 `CFrameWnd` 实现会删除C\+\+对象窗口。  当用户关闭框架窗口，默认 `OnClose` 处理程序将调用 `DestroyWindow`。  
  
 有关 `CMDIChildWnd`的更多信息，请参见 [Windows框架](../../mfc/frame-windows.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMDIChildWnd`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC MDI示例](../../top/visual-cpp-samples.md)   
 [MFC MDIDOCVW示例](../../top/visual-cpp-samples.md)   
 [MFC SNAPVW示例](../../top/visual-cpp-samples.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CMDIFrameWnd Class](../../mfc/reference/cmdiframewnd-class.md)