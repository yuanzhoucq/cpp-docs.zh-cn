---
title: 文档-视图体系结构
ms.date: 11/19/2018
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
ms.openlocfilehash: a74aeba651d385cf3a5386e94ec20e4e56b7cd57
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624789"
---
# <a name="documentview-architecture"></a>文档/视图体系结构

默认情况下，MFC 应用程序向导使用文档类和视图类创建应用程序主干。 MFC 将数据管理分隔到这两个类中。 该文档存储数据，并管理数据的打印，并协调更新多个数据视图。 视图显示数据并管理用户与之的交互，包括选择和编辑。

在此模型中，MFC 文档对象读取数据并将数据写入永久性存储。 文档还可以提供指向任何位置的数据的接口（如数据库中的数据）。 一个单独的视图对象，用于管理数据显示，从将窗口中的数据呈现给用户选择和编辑数据。 视图将从文档中获取显示数据，并向文档传回任何数据更改。

尽管您可以轻松地重写或忽略文档/视图分离，但在大多数情况下，在这种情况下也有一些很有说服力的原因。 最好的一种方法是，需要同一文档的多个视图，例如电子表格和图表视图。 文档/视图模型允许单独的 view 对象表示数据的每个视图，而所有视图共有的代码（如计算引擎）可以驻留在文档中。 文档还会考虑在数据更改时更新所有视图的任务。

MFC 文档/视图体系结构使你可以轻松地支持多个视图、多个文档类型、拆分窗口和其他有价值的用户界面功能。

MFC 框架的各个部分最适用于用户，而你是程序员，就是文档和视图。 使用框架开发应用程序的大部分工作都是编写文档和视图类。 本文系列介绍：

- 文档和视图的用途以及它们在框架中的交互方式。

- 实现它们必须执行的操作。

文档/视图的核心是四个关键类：

[CDocument](reference/cdocument-class.md) （或[COleDocument](reference/coledocument-class.md)）类支持用于存储或控制程序数据的对象，并为程序员定义的文档类提供基本功能。 文档表示用户通常使用 "文件" 菜单上的 "打开" 命令打开的数据单元，并使用 "文件" 菜单上的 "保存" 命令保存。

[CView](reference/cview-class.md) （或它的多个派生类之一）为程序员定义的视图类提供基本功能。 视图附加到文档并充当文档和用户之间的中介：视图在屏幕上呈现文档的图像，并将用户输入解释为文档上的操作。 此视图还会呈现打印和打印预览的图像。

[CFrameWnd](reference/cframewnd-class.md) （或其变体之一）支持在文档的一个或多个视图周围提供框架的对象。

[CDocTemplate](reference/cdoctemplate-class.md) （或[CSingleDocTemplate](reference/csingledoctemplate-class.md)或[CMultiDocTemplate](reference/cmultidoctemplate-class.md)）支持一个对象，该对象协调特定类型的一个或多个现有文档，并管理为该类型创建正确的文档、视图和框架窗口对象。

下图显示了文档和其视图之间的关系。

![视图是所显示文档的一部分](../mfc/media/vc379n1.gif "视图是所显示文档的一部分") <br/>
文档和视图

类库中的文档/视图实现将数据本身从其显示和数据中的用户操作中分离出来。 对数据所做的所有更改都通过 document 类进行管理。 视图调用此接口访问和更新数据。

文档、文档的关联视图，以及由文档模板创建视图的框架窗口。 文档模板负责创建和管理一种文档类型的所有文档。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [文档/视图体系结构的纵向](a-portrait-of-the-document-view-architecture.md)

- [文档/视图体系结构的优点](advantages-of-the-document-view-architecture.md)

- [应用程序向导创建的文档和视图类](document-and-view-classes-created-by-the-mfc-application-wizard.md)

- [文档/视图体系结构的替代项](alternatives-to-the-document-view-architecture.md)

- [向单个文档添加多个视图](adding-multiple-views-to-a-single-document.md)

- [使用文档](using-documents.md)

- [使用视图](using-views.md)

- [多文档类型、视图和框架窗口](multiple-document-types-views-and-frame-windows.md)

- [初始化和清理文档和视图](initializing-and-cleaning-up-documents-and-views.md)

- [将您自己的添加内容初始化为文档 & 视图类](creating-new-documents-windows-and-views.md)

- [结合使用数据库类与文档和视图](../data/mfc-using-database-classes-with-documents-and-views.md)

- [使用数据库类（而不使用文档和视图）](../data/mfc-using-database-classes-without-documents-and-views.md)

- [示例](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>另请参阅

[用户界面元素](user-interface-elements-mfc.md)<br/>
[Windows](windows.md)<br/>
[框架窗口](frame-windows.md)<br/>
[文档模板和文档/视图创建过程](document-templates-and-the-document-view-creation-process.md)<br/>
[文档/视图创建](document-view-creation.md)<br/>
[创建新文档、窗口和视图](creating-new-documents-windows-and-views.md)
