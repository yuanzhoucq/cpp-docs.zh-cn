---
title: "文档视图体系结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CView class [MFC], view architecture
- CDocument class [MFC]
- MFC, views
- views [MFC], MFC document/view model
- document objects [MFC]
- document objects [MFC], MFC document/view model
- MFC, documents
- documents [MFC], MFC document/view model
- document objects [MFC], document/view architecture
ms.assetid: 6127768a-553f-462a-b01b-a5ee6068c81e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 45c595b78b17ed00691533369ec4837345fcce03
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="documentview-architecture"></a>文档/视图体系结构
默认情况下，MFC 应用程序向导创建的应用程序主干具有文档类和视图类。 MFC 分隔到这两个类的数据管理。 该文档将数据存储和管理数据的打印和协调更新的数据的多个视图。 该视图显示的数据，并管理与它，包括选择和编辑的用户交互。  
  
 在此模型中，MFC 文档对象读取，并将数据写入持久存储。 各个位置 （例如，在数据库），该文档可能还提供对数据的接口。 单独的视图对象管理从呈现到用户选择窗口中的数据和编辑的数据的数据显示。 该视图从文档获取显示的数据，并将任何数据更改传递回文档。  
  
 尽管你可以轻松地重写或忽略文档/视图分离，有令人信服的理由需要遵循在大多数情况下此模型。 最佳之一时，你需要相同的文档，例如电子表格和图表视图的多个视图。 文档/视图模型允许表示每个视图的数据，而代码常见所有视图 （例如计算引擎） 可以都驻留在文档中的一个单独的视图对象。 文档还采用上的数据更改时更新所有视图的任务。  
  
 MFC 文档/视图体系结构可以轻松以支持多个视图、 多个文档类型、 拆分窗口和其他有价值的用户界面功能。  
  
 MFC 框架同时向用户和程序员来说，最明显的组成部分是文档和视图。 大部分开发框架的应用程序中的工作将进入编写文档和视图类。 本文章系列介绍：  
  
-   进行文档和视图和框架中进行的交互。  
  
-   你必须做什么来实现它们。  
  
 文档/视图的核心是四个关键类：  
  
 [CDocument](../mfc/reference/cdocument-class.md) (或[COleDocument](../mfc/reference/coledocument-class.md)) 类支持用来存储或控制您的程序数据的对象，提供程序员定义的文档类的基本功能。 文档表示用户通常使用文件菜单上打开的命令将打开并使用保存命令保存在文件菜单上的数据的单位。  
  
 [CView](../mfc/reference/cview-class.md) （或其许多的派生类之一） 提供程序员定义的视图类的基本功能。 查看附加到文档和充当文档和用户之间的中介： 视图呈现屏幕上显示文档的映像，并将用户输入解释为对文档的操作。 该视图还会呈现的图像打印和打印预览。  
  
 [CFrameWnd](../mfc/reference/cframewnd-class.md) （或其变体之一） 支持提供周围的文档的一个或多个视图的框架的对象。  
  
 [CDocTemplate](../mfc/reference/cdoctemplate-class.md) (或[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)或[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)) 支持协调的给定类型的一个或多个现有文档，并管理创建正确的对象文档、 视图和框架窗口对象，该类型。  
  
 下图显示文档及其视图之间的关系。  
  
 ![视图是显示的文档的一部分](../mfc/media/vc379n1.gif "vc379n1")  
文档和视图  
  
 类库中的文档/视图实现的数据区分开来本身从其显示和对数据的用户操作。 对数据的所有更改都管理通过文档类。 视图将调用此接口可访问和更新数据。  
  
 文档模板创建文档、 与其关联的视图和框架视图的框架窗口。 文档模板是负责创建和管理的一种文档类型的所有文档。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [文档/视图体系结构的纵览](../mfc/a-portrait-of-the-document-view-architecture.md)  
  
-   [文档/视图体系结构的优势](../mfc/advantages-of-the-document-view-architecture.md)  
  
-   [应用程序向导创建的文档和视图类](../mfc/document-and-view-classes-created-by-the-mfc-application-wizard.md)  
  
-   [文档/视图体系结构的替代方法](../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [向单个文档添加多个视图](../mfc/adding-multiple-views-to-a-single-document.md)  
  
-   [使用文档](../mfc/using-documents.md)  
  
-   [使用视图](../mfc/using-views.md)  
  
-   [多文档类型、视图和框架窗口](../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [初始化和清理文档和视图](../mfc/initializing-and-cleaning-up-documents-and-views.md)  
  
-   [初始化你自己添加到文档和视图类](../mfc/creating-new-documents-windows-and-views.md)  
  
-   [结合文档和视图使用数据库类](../data/mfc-using-database-classes-with-documents-and-views.md)  
  
-   [不结合文档和视图使用数据库类](../data/mfc-using-database-classes-without-documents-and-views.md)  
  
-   [示例](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>请参阅  
 [用户界面元素](../mfc/user-interface-elements-mfc.md)   
 [Windows](../mfc/windows.md)   
 [框架窗口](../mfc/frame-windows.md)   
 [文档模板和文档/视图创建过程](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [文档/视图创建](../mfc/document-view-creation.md)   
 [创建新文档、窗口和视图](../mfc/creating-new-documents-windows-and-views.md)

