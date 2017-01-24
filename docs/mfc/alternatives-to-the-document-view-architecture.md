---
title: "文档/视图结构的替换选项 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDocument 类, 空间要求"
  - "文档, 应用程序"
  - "视图, 应用程序"
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 文档/视图结构的替换选项
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 应用程序通常使用文档\/视图体系结构管理信息、文件格式和数据的可视表示。  对于大多数桌面应用程序，文档\/视图结构是正确和有效的应用程序结构。  此体系结构从视图分离数据，大多数情况下，简化应用程序并减少冗余代码。  
  
 但是，文档\/视图体系结构在某些情况是不正确的。  请考虑下列示例：  
  
-   如果您用 C 编写Windows应用程序，您可能要在添加文档\/视图支持之前完成端口编写。  
  
-   如果您编写某个轻量级实用工具，您可能会发现可以不用文档\/视图结构。  
  
-   如果原始代码与数据视图的数据管理混合，将代码移植到文档\/视图模型不值得，因为您必须移植两个。  您可能更愿意将代码写成这样。  
  
 若要创建不使用文档\/视图结构的应用程序，请清除在 MFC 应用程序向导的步骤 1 的 **文档\/视图结构支持 \(V\)** 复选框。  有关详细信息，请参见 [MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)。  
  
> [!NOTE]
>  MFC 应用程序向导生成的基于对话框的应用程序不使用文档\/视图结构，因此，如果选中对话框的应用程序，**文档\/视图结构支持 \(V\)** 复选框也是不可选的。  
  
 Visual C\+\+ 向导，以及源文件和对话框编辑器，与生成的应用程序一起工作就像处理其他任何向导生成的应用程序一样。  应用程序可以支持的工具栏、滚动和状态栏，并具有 **关于** 框。  应用程序将不注册任何文档模板，并不包含一个文档类。  
  
 注意生成的应用程序有视图类，**CChildView**，从 `CWnd`中派生。  MFC 创建并确定应用程序的框架窗口中创建的视图类的实例。  MFC 将强制使用视图窗口，因为它简化定位和管理应用程序的内容。  可以在该类的 `OnPaint` 成员中添加绘制代码。  代码将滚动添加到视图而不是到框架。  
  
 由于 MFC 提供的文档\/视图体系结构负责实现许多应用程序的基本功能，项目要是没有它意味着应用程序就要负责实现程序的许多重要功能：  
  
-   根据提供由 MFC 应用程序向导所提供的，应用程序中的**文件** 菜单仅包含 `New` 和 `Exit`命令。\( MDI 应用程序仅支持 `New` 命令，没有 SDI 应用程序不支持无文档\/视图支持。\)生成的菜单资源不支持 MRU \(最近使用的\)列表。  
  
-   必须添加句柄函数和应用程序支持的所有命令的实现，包括位于 **文件**菜单的**打开** 和 **保存**按钮 。  MFC 通常提供支持这些功能的代码，但是，支持与文档\/视图结构紧密相连。  
  
-   如果请求一个应用程序的工具栏，将是最小的实现。  
  
 强烈建议您使用 MFC 应用程序向导创建应用程序，不使用文档\/视图结构，因为向导保证一个正确 MFC 体系结构。  但是，如果一定要避免使用向导，这里有几种方法可以跳过代码的文档\/视图结构：  
  
-   将文档视为未使用的附加物和实现视图类的数据管理代码，如上述所建议。  文档的开销相对较低。  单个[CDocument](../mfc/reference/cdocument-class.md)对象产生少量系统开销，以及小量 **CDocument** 基类、[CCmdTarget](../mfc/reference/ccmdtarget-class.md)和[CObject](../mfc/reference/cobject-class.md)的系统开销。  后面两个类都很小。  
  
     在**CDocument**中声明:  
  
    -   两个 `CString` 对象。  
  
    -   三个 **BOOL**变量。  
  
    -   一个 `CDocTemplate` 指针。  
  
    -   一个 `CPtrList` 对象，该对象包含文档视图中的列表。  
  
     此外，文档需要时间创建文档对象、视图对象、框架窗口和文档模板对象。  
  
-   视文档和视图为未使用的附加物。  将数据管理和绘图代码放置在框架窗口而不是视图。  此方法更接近 C 语言编程模型。  
  
-   重写创建文档和视图的 MFC 框架的一部分。  文档创建过程将以`CWinApp::AddDocTemplate`调用开始。  从应用程序类的 `InitInstance` 成员函数来消除该调用，相反，创建 `InitInstance` 中的框架窗口。  将数据管理代码放置在框架窗口类。  文档\/视图创建过程在[文档\/视图创建](../mfc/document-view-creation.md)中说明。  需要更多的工作并要求对更深入的理解框架，但它完全抽象化文档\/视图。  
  
 文章 [MFC:不结合文档和视图使用数据库类](../data/mfc-using-database-classes-without-documents-and-views.md) 给定在数据库应用程序中文档\/视图的特定实例。  
  
## 请参阅  
 [文档\/视图体系结构](../mfc/document-view-architecture.md)