---
title: "TN025：文档、视图和框架创建 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.creation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "文档, 视图和框架创建"
  - "TN025"
ms.assetid: 09254d72-6e1d-43db-80e9-693887dbeda2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# TN025：文档、视图和框架创建
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此注释说明 WinApps、DocTemplates、文档、框架和视图的创建和公开问题。  
  
## WinApp  
 有一个 `CWinApp` 对象在系统中。  
  
 它被 `WinMain`的框架实现的内部静态构造和初始化。  必须从 `CWinApp` 派生执行有用的任何内容 \(异常：扩展 DLL 不应具有 `CWinApp` 实例 \- 初始化在 `DllMain` 完成\)。  
  
 这个 `CWinApp` 对象列表的文档模板 \( `CPtrList`\)。  有一个或多个文档模板每个应用程序。  DocTemplates 从资源文件 \(即字符串数组\) 通常在加载 `CWinApp::InitInstance`。  
  
```  
pTemplate = new CDocTemplate(IDR_MYDOCUMENT, ...);  
AddDocTemplate(pTemplate);  
```  
  
 这个 `CWinApp` 对象拥有在应用程序的任何框架窗口。  **CWinApp::m\_pMainWnd**应在存储应用程序的主框架窗口；通常在 `InitInstance` 实现的 `m_pMainWnd`，如果没有允许 AppWizard 执行断点。  对于单文档界面 \(SDI\) \(SDI\) 这是主应用作为框架窗口以及唯一的文档框架窗口的 `CFrameWnd`。  对于多文档界面 \(MDI\) \(MDI\) 这是 MDI 框架 \(类 `CMDIFrameWnd`\)。作为包含任何子 `CFrameWnd`的 . 的主要应用框架窗口。  每个子窗口可能是类 `CMDIChildWnd` \(从 `CFrameWnd`派生\) 和用作许多文档框架窗口之一。  
  
## DocTemplates  
 `CDocTemplate` 是记录的创建者和管理器。  它拥有它创建的文档。  如果应用程序使用下面基于资源的方法，不需要从 `CDocTemplate`派生。  
  
 对于 SDI 应用程序，`CSingleDocTemplate` 类记录一个打开文档。  在 MDI 应用程序，`CMultiDocTemplate` 类保留一个列表 \( `CPtrList`从该模板创建的\) 所有当前打开的文档。  `CDocTemplate::AddDocument` 和 `CDocTemplate::RemoveDocument` 提供添加或删除文档提供对虚拟成员函数从模板。  `CDocTemplate` 是 **CDocument** 的友元，因此我们可以将保护 **CDocument::m\_pDocTemplate** 返回的指针指向回创建文档的文档模板。  
  
 `CWinApp` 处理默认 `OnFileOpen` 实现，fprintf 又会查询所有文档模板。  实现包含查找已打开文档并确定新打开的文档的格式。  
  
 `CDocTemplate` 管理绑定对于文档和框架的用户界面。  
  
 `CDocTemplate` 保留未命名的文档数目的计数。  
  
## CDocument  
 **CDocument** 由 `CDocTemplate`拥有。  
  
 文档有当前打开的视图列表 \(从 `CView`派生\) 显示文档 \( `CPtrList`\)。  
  
 文档不创建\/销毁视图，但它们相互附加，在创建之后。  在文档关闭 \(即通过文件\/关闭\)，所有连接的视图将关闭。  在关闭文档的最后一个视图 \(例如窗口\/关闭\) 文档将关闭。  
  
 `CDocument::AddView`接口，`RemoveView` 用于在列表视图。  **CDocument** 是 `CView` 的友元，因此我们可以设置 **CView::m\_pDocument** 返回一个指针。  
  
## CFrameWnd  
 `CFrameWnd` \(也称为\) 帧播放角色与 MFC 1.0，但是，`CFrameWnd` 类现在设计在许多情况下，使用而派生新类。  派生类 `CMDIFrameWnd` 和 `CMDIChildWnd` 还会引发许多标准命令已实现。  
  
 `CFrameWnd` 负责创建帧在的工作区窗口中运行。  通常有填充的工作区框架的主窗口。  
  
 在 MDI 框架窗口，工作区由随后是所有 MDI 子框架窗口的父 MDICLIENT 控件。  SDI 对于框架窗口或 MDI 子框架窗口，工作区窗口通常用 `CView`派生的对象。  对于 `CSplitterWnd`，视图的工作区窗口由 `CSplitterWnd` 对象和 `CView`派生的每个拆分窗格的窗口对象 \(一个\) 会创建为 `CSplitterWnd`的子窗口。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)