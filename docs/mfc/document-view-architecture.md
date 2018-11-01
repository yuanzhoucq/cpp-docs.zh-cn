---
title: 文档视图体系结构
ms.date: 11/04/2016
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
ms.openlocfilehash: 943199e2398bcb49c7dddf6b3a67f5556c9c81a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509274"
---
# <a name="documentview-architecture"></a>文档/视图体系结构

默认情况下，MFC 应用程序向导创建应用程序框架使用的文档类和视图类。 MFC 将为这两个类的数据管理。 文档将数据存储和管理数据的打印和协调更新数据的多个视图。 视图显示的数据，并管理与它，包括选择和编辑的用户交互。

在此模型中，MFC 文档对象读取，并将数据写入到持久存储。 各个位置 （例如数据库），该文档还可以提供对数据的接口。 单独的视图对象管理数据显示，从呈现在用户选择窗口中的数据和编辑数据。 该视图从文档获取显示数据，并将任何数据更改传递回文档。

虽然您可以轻松地重写或忽略文档/视图分离，有有说服力的理由，请遵循此模型在大多数情况下。 一个最佳都使用相同的文档，例如电子表格和图表视图的多个视图。 文档/视图模型，一个单独的视图对象，该对象表示的数据，而代码常见 （例如计算引擎） 对所有视图可以都驻留在文档中的每个视图。 文档还会在数据发生更改时，更新所有视图的任务。

MFC 文档/视图体系结构可以方便地支持多个视图、 多个文档类型、 拆分窗口和其他有价值的用户界面功能。

MFC 框架同时向用户和程序员来说，最明显的组成部分是文档和视图。 编写文档和视图类进入您的大部分工作在开发使用 framework 的应用程序。 本文章系列介绍：

- 文档和视图和框架中进行的交互的目的。

- 您必须做什么来实现它们。

文档/视图的核心是四个关键类：

[CDocument](../mfc/reference/cdocument-class.md) (或[COleDocument](../mfc/reference/coledocument-class.md)) 类支持用来存储或控制应用程序的数据的对象，并为程序员定义的文档类提供基本功能。 文档表示用户通常使用文件菜单打开的命令将打开，并将使用保存命令保存在文件菜单上的数据的单位。

[CView](../mfc/reference/cview-class.md) （或其多个派生类之一） 的程序员定义的视图类提供的基本功能。 一个视图附加到文档，并且可作为文档和用户之间的媒介： 视图呈现在屏幕上文档的图像并将用户输入解释为文档的操作。 该视图还会呈现打印和打印预览图像。

[CFrameWnd](../mfc/reference/cframewnd-class.md) （或其中一个及其变体） 支持提供的文档的一个或多个视图周围的框架的对象。

[CDocTemplate](../mfc/reference/cdoctemplate-class.md) (或[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)或[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)) 支持用于协调给定类型的一个或多个现有文档以及管理创建正确的对象文档、 视图和框架窗口对象，该类型。

下图显示了文档及其视图之间的关系。

![视图是显示文档的一部分](../mfc/media/vc379n1.gif "vc379n1")文档和视图

类库中的文档/视图实现该方法将数据本身从其显示和对数据的用户操作。 通过文档类，对数据的所有更改进行都管理。 视图将调用此接口来访问和更新的数据。

文档模板创建文档、 其关联的视图和帧视图的框架窗口。 文档模板负责创建和管理的一种文档类型的所有文档。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [文档/视图结构的纵览](../mfc/a-portrait-of-the-document-view-architecture.md)

- [文档/视图体系结构的优点](../mfc/advantages-of-the-document-view-architecture.md)

- [应用程序向导创建的文档和视图类](../mfc/document-and-view-classes-created-by-the-mfc-application-wizard.md)

- [文档/视图体系结构的替代方法](../mfc/alternatives-to-the-document-view-architecture.md)

- [向单个文档添加多个视图](../mfc/adding-multiple-views-to-a-single-document.md)

- [使用文档](../mfc/using-documents.md)

- [使用视图](../mfc/using-views.md)

- [多文档类型、视图和框架窗口](../mfc/multiple-document-types-views-and-frame-windows.md)

- [初始化和清理文档和视图](../mfc/initializing-and-cleaning-up-documents-and-views.md)

- [初始化你自己添加到文档和视图类](../mfc/creating-new-documents-windows-and-views.md)

- [结合文档和视图使用数据库类](../data/mfc-using-database-classes-with-documents-and-views.md)

- [使用数据库类不结合文档和视图](../data/mfc-using-database-classes-without-documents-and-views.md)

- [示例](../visual-cpp-samples.md)

## <a name="see-also"></a>请参阅

[用户界面元素](../mfc/user-interface-elements-mfc.md)<br/>
[Windows](../mfc/windows.md)<br/>
[框架窗口](../mfc/frame-windows.md)<br/>
[文档模板和文档/视图创建过程](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[文档/视图创建](../mfc/document-view-creation.md)<br/>
[创建新文档、窗口和视图](../mfc/creating-new-documents-windows-and-views.md)

