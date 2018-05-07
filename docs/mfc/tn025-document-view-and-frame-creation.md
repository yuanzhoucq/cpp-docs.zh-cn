---
title: TN025： 文档、 视图和框架创建 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.creation
dev_langs:
- C++
helpviewer_keywords:
- documents [MFC], view and frame creation
- TN025
ms.assetid: 09254d72-6e1d-43db-80e9-693887dbeda2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a5fd603fdb45ac0f754858384df1455f559222e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="tn025-document-view-and-frame-creation"></a>TN025：文档、视图和框架创建
> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 本说明介绍 WinApps、DocTemplate、文档、框架和视图的创建和所有权问题。  
  
## <a name="winapp"></a>WinApp  
 系统中有一个 `CWinApp` 对象。  
  
 它由框架的 `WinMain` 内部实现以静态方式构造和初始化。 你必须从中派生`CWinApp`以执行任何有用 (异常： MFC 扩展 Dll 不应具有`CWinApp`实例-初始化完成`DllMain`相反)。  
  
 一个 `CWinApp` 对象拥有一个文档模板列表 (`CPtrList`)。 每个应用程序有一个或多个文档模板。 DocTemplate 通常从 `CWinApp::InitInstance` 中的资源文件（即字符串数组）中加载。  
  
```  
pTemplate = new CDocTemplate(IDR_MYDOCUMENT, ...);

AddDocTemplate(pTemplate);
```  
  
 一个 `CWinApp` 对象拥有应用程序中的所有框架窗口。 应用程序的主框架窗口应存储在**M_pmainwnd**; 通常设置`m_pMainWnd`中`InitInstance`实现，如果您没有让 AppWizard 为您完成此操作。 对于单文档界面 (SDI)，这是充当主应用程序框架窗口以及唯一的文档框架窗口的一个 `CFrameWnd`。 对于多文档界面 (MDI)，这是充当包含所有子 `CMDIFrameWnd` 的主应用程序框架窗口的 MDI 框架（类 `CFrameWnd`）。 每个子窗口属于类 `CMDIChildWnd`（派生自 `CFrameWnd`）并充当可能数量较多的文档框架窗口中的一个。  
  
## <a name="doctemplates"></a>DocTemplate  
 `CDocTemplate` 是文档的创建者和管理者。 它对自己创建的文档具有所有权。 如果应用程序使用了下面所述的基于资源的方法，则不需要从 `CDocTemplate` 派生。  
  
 对于 SDI 应用程序，类 `CSingleDocTemplate` 将跟踪一个打开的文档。 对于 MDI 应用程序，类 `CMultiDocTemplate` 类将保留所有当前打开的从该模板创建的文档的列表 (`CPtrList`)。 `CDocTemplate::AddDocument` 和 `CDocTemplate::RemoveDocument` 提供了用于在模板中添加或删除文档的虚拟成员函数。 `CDocTemplate` 是的友元**CDocument**以便我们可以设置受保护**cdocument:: M_pdoctemplate**后向指针以指回创建文档的文档模板。  
  
 `CWinApp` 处理默认 `OnFileOpen` 实现，该实现反过来又会查询所有文档模板。 该实现包括查找已打开的文档和确定打开新文档的格式。  
  
 `CDocTemplate` 管理文档和框架的 UI 绑定。  
  
 `CDocTemplate` 保留未命名的文档的计数。  
  
## <a name="cdocument"></a>CDocument  
 A **CDocument**归`CDocTemplate`。  
  
 文档具有当前打开的、用来查看文档 (`CView`) 的视图（派生自 `CPtrList`）的列表。  
  
 文档不创建/销毁视图，但它们在创建后会相互连接。 当文档关闭（通过“文件”/“关闭”）时，所有连接的视图都将关闭。 当文档中的最后一个视图关闭（通过“窗口”/“关闭”）时，文档将关闭。  
  
 `CDocument::AddView`（`RemoveView` 接口）用于维护视图列表。 **CDocument**为友元的`CView`以便我们可以设置**M_pdocument**后向指针。  
  
## <a name="cframewnd"></a>CFrameWnd  
 `CFrameWnd`（也称为“框架”）的作用与在 MFC 1.0 中的作用相同，但现在 `CFrameWnd` 类可以在很多情况下使用，而不用派生新类。 派生类 `CMDIFrameWnd` 和 `CMDIChildWnd` 也已增强，因此很多标准命令已经实现。  
  
 `CFrameWnd` 负责在框架的工作区中创建窗口。 通常，有一个填充框架的工作区的主窗口。  
  
 对于 MDI 框架窗口，工作区将使用 MDICLIENT 控件填充，该控件又是所有 MDI 子框架窗口的父级。 对于 SDI 框架窗口或 MDI 子框架窗口，工作区通常用 `CView` 派生的窗口对象填充。 对于 `CSplitterWnd`，视图的工作区用 `CSplitterWnd` 窗口对象填充，`CView` 派生窗口对象（每个拆分窗格一个）将作为 `CSplitterWnd` 的子窗口创建。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

