---
title: "多文档类型、视图和框架窗口 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "静态拆分窗口"
  - "多视图"
  - "多文档类型"
  - "多视图, 框架窗口"
  - "文档类, 多个"
  - "文档 [C++], 多种类型"
  - "拆分窗口, 动态"
  - "动态拆分窗口"
  - "窗口 [C++], 动态拆分器"
  - "窗口 [C++], 静态拆分器"
  - "多框架窗口"
  - "拆分窗口, 静态"
ms.assetid: c6b9e4e0-7c9c-45f1-a804-aeac39c9a128
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 多文档类型、视图和框架窗口
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[文档\/视图创建](../mfc/document-view-creation.md)中介绍了文档及其视图和架构窗口之间的标准关系。 许多应用程序都支持单文档类型，但可以出现该类型的多个打开的文档，单文档类型指在文档上具有单个视图，而且每个文档只有一个框架窗口的文档类型。 但某些应用程序可能需要改变一个或多个这些默认值。  
  
## 你想进一步了解什么？  
  
-   [多文档类型](#_core_multiple_document_types)  
  
-   [多视图](#_core_multiple_views)  
  
-   [多框架窗口](#_core_multiple_frame_windows)  
  
-   [拆分窗口](#_core_splitter_windows)  
  
##  <a name="_core_multiple_document_types"></a> 多文档类型  
 “MFC 应用程序”向导可为你创建单个文档类。 但在某些情况下，可能需要支持一个以上的文档类型 例如，你的应用程序可能需要工作表文档和图表文档。 每种文档类型由各自的文档类表示，可能的话还由各自的视图类表示。 当用户选择“新建文件”命令时，框架将显示出一个对话框，其中列出了受支持的文档类型。 然后，框架会创建用户所选类型的文档。 每个文档由各自的文档模板对象进行管理。  
  
 若要创建其他文档类，请参阅[添加类](../ide/adding-a-class-visual-cpp.md)。 选择 [CDocument](../mfc/reference/cdocument-class.md) 作为要从其派生的类类型并提供请求的文档信息。 然后，实现新类的数据。  
  
 若要使框架知道其他文档类，必须在应用程序类的 [InitInstance](../Topic/CWinApp::InitInstance.md) 再添加一个对 [AddDocTemplate](../Topic/CWinApp::AddDocTemplate.md) 的的调用。 有关信息信息，请参阅[文档模板](../mfc/document-templates-and-the-document-view-creation-process.md)。  
  
##  <a name="_core_multiple_views"></a> 多视图  
 许多文档只要求单个视图，但可能支持每个文档有一个以上的视图。 为了帮助实现多个视图，文档对象会保留其视图的列表，提供用于添加和删除视图的成员函数，以及提供 [UpdateAllViews](../Topic/CDocument::UpdateAllViews.md) 成员函数来通知各个视图关于文档数据发生更改的时间。  
  
 MFC 支持在同一文档上要求多个视图的三个通用用户界面。 这些模型为：  
  
-   同一类的视图对象，每个视图对象在一个单独的 MDI 文档框架窗口中。  
  
     可能要支持创建文档的第二个框架窗口。 用户可以选择“新建窗口”命令打开第二个具有同一文档视图的框架，然后使用这两个框架同时查看文档的不同部分。 通过复制最初附加到文档的框架窗口和视图，框架支持 MDI 应用程序“窗口”菜单上的“新建窗口”命令。  
  
-   同一文档框架窗口中同一类的视图对象。  
  
     拆分窗口将单个文档窗口的视图空间拆分成多个单独的文档视图。 框架从同一视图类创建多个视图对象。 有关详细信息，请参阅[拆分窗口](#_core_splitter_windows)。  
  
-   单个框架窗口中不同类的视图对象。  
  
     在此模型中，拆分窗口的变体（即多视图）共享单个框架窗口。 这些视图是从不同的类构造成的，因此每个视图可提供查看同一文档的不同方式。 例如，一个视图可以以正常模式显示字处理文档，而另一个视图则以大纲模式显示该文档。 拆分条控件使用户得以调整视图的相对大小。  
  
 下图被分成 a、b、c 三部分，按上面介绍的顺序显示三个用户界面模型。  
  
 ![多视图用户界面](../mfc/media/vc37a71.png "vc37A71")  
多视图用户界面  
  
 框架通过实现“新建窗口”命令和提供 [CSplitterWnd](../mfc/reference/csplitterwnd-class.md) 类来提供这些模型，请参见[拆分窗口](#_core_splitter_windows)中的讨论。 可以用这些作为起点实现其他模型。 有关阐释视图、框架窗口和拆分条的不同配置的示例程序，请参阅 [MFC 示例](../top/visual-cpp-samples.md)。  
  
 有关 `UpdateAllViews` 的详细信息，请参阅 *MFC 参考*中的 [CView](../mfc/reference/cview-class.md)类和 [Scribble 示例](../top/visual-cpp-samples.md)。  
  
##  <a name="_core_multiple_frame_windows"></a> 多框架窗口  
 可以使用 MDI 应用程序“窗口”菜单上的“新建窗口”命令创建同一文档的第二个框架窗口。 有关详细信息，请参阅[多视图用户界面](#_core_multiple.2d.view_user_interfaces)图中的第一个模型。  
  
##  <a name="_core_splitter_windows"></a> 拆分窗口  
 在拆分窗口中，窗口被（或可以）拆分为两个或更多的可滚动窗格。 窗口框架中滚动条旁边的拆分条控件（或“拆分框”）使用户得以调整窗格的相对大小。 每个窗格是同一文档的一个视图。 在“动态”拆分条中，视图属于同一类，如图[多视图用户界面](#_core_multiple.2d.view_user_interfaces)中的 b 部分所示。 在“静态”拆分条中，视图可以属于不同类。[CSplitterWnd](../mfc/reference/csplitterwnd-class.md) 类支持这两种拆分窗口。  
  
 动态拆分窗口具有同一类的视图，使用户得以随意将窗口拆分为多个窗格，然后滚动不同的窗格以查看文档的不同部分。 用户还可以撤销拆分窗口以删除其他视图。 添加到 [Scribble 示例](../top/visual-cpp-samples.md)的拆分窗口即属此例。 那个主题介绍了用于创建动态拆分窗口的方法。 该主题描述创建动态拆分窗口的技术。动态拆分窗口如图[多视图用户界面](#_core_multiple.2d.view_user_interfaces)的 b 部分所示。  
  
 静态拆分窗口具有不同类的视图，从被拆分为多个窗格的窗口开始，每个窗格都具有不同的用途。 例如，在 Visual C\+\+ 位图编辑器中，图像窗口并排显示两个窗格。 左窗格显示位图实物原样大小的图像。 右窗格显示同一位图的缩小或放大的图像。 窗格由“拆分条”分隔，用户可以拖动该“拆分条”更改窗格的相对大小。 静态拆分窗口如图[多视图用户界面](#_core_multiple.2d.view_user_interfaces)的 c 部分所示。  
  
 有关详细信息，请参阅 *MFC 参考*中的 [CSplitterWnd](../mfc/reference/csplitterwnd-class.md) 类和 [MFC 示例](../top/visual-cpp-samples.md)。  
  
## 请参阅  
 [文档\/视图体系结构](../mfc/document-view-architecture.md)