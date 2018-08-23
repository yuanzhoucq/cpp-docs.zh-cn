---
title: 用于生成 MFC 应用程序的操作顺序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], developing
ms.assetid: 6973c714-fe20-48c6-926b-de88356b3a3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1bafcec75643c292a887b54de1b852609dd251c0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383804"
---
# <a name="sequence-of-operations-for-building-mfc-applications"></a>用于生成 MFC 应用程序的操作顺序
下表说明您开发 MFC 应用程序时通常应遵循的一般顺序。  
  
### <a name="sequence-for-building-an-application-with-the-framework"></a>使用框架生成应用程序的顺序  
  
|任务|您执行的操作|框架执行的操作|  
|----------|------------|------------------------|  
|创建一个主干应用程序。|运行[MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)。 在选项页中指定您需要的选项。 选项包括使应用程序成为 COM 组件、容器或两者；添加自动化；以及让应用程序可识别数据库。|MFC 应用程序向导为主干应用程序创建文件，包括应用程序的源文件、文档、视图和框架窗口；一个资源文件；一个项目文件；以及其他内容（全部根据您的规范定制）。|  
|了解即使在不添加你自己的任何一行代码的情况下，框架和 MFC 应用程序向导也能提供的内容。|生成主干应用程序并在 Visual C++ 中运行它。|正在运行的主干应用程序派生了很多标准**文件**，**编辑**，**视图**，和**帮助**框架中的菜单命令。 对于 MDI 应用程序，您还将获得一个完整的功能性 Windows 菜单，而框架将管理 MDI 子窗口的创建、排列和析构。|  
|构造应用程序的用户界面。|使用 Visual c + +[资源编辑器](../windows/resource-editors.md)直观地编辑应用程序的用户界面：<br /><br /> -创建菜单。<br />-定义快捷键。<br />-创建对话框。<br />-创建并编辑位图、 图标和光标。<br />-编辑 MFC 应用程序向导为你创建的工具栏。<br />-创建和编辑其他资源。<br /><br /> 你还可以在对话框编辑器中测试对话框。|MFC 应用程序向导创建的默认资源文件提供了很多您需要的资源。 利用 Visual C++，您可以轻松直观地编辑现有资源和添加新资源。|  
|将菜单映射到处理程序函数。|使用**事件**按钮[属性窗口](/visualstudio/ide/reference/properties-window)将菜单和快捷键连接到你的代码中的处理程序函数。|“属性”窗口将消息映射项和空函数模板插入你指定的源文件并管理很多手动编码任务。|  
|编写处理程序代码。|使用类视图直接跳转到在源代码编辑器中的代码。 为处理程序函数填写代码。 有关如何使用类视图以及向项目添加代码的向导的详细信息，请参阅[用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)。|类视图打开编辑器，滚动到空函数模板并为您放置光标。|  
|将工具栏按钮映射到命令。|通过为工具栏上的每个按钮分配相应的命令 ID 来将其映射到菜单或快捷键命令。|框架控制工具栏按钮的绘制、启用、禁用、检查和其他可视方面。|  
|测试处理程序函数。|重新生成程序并使用内置调试工具来测试处理程序是否正常工作。|你可以逐步执行代码或跟踪代码以了解处理程序的调用情况。 如果已填写处理程序代码，处理程序将执行命令。 框架将自动禁用未处理的菜单项和工具栏按钮。|  
|添加[对话框](../mfc/dialog-boxes.md)。|使用对话框编辑器设计对话框模板资源。 然后创建对话框类和处理对话框的代码。|框架管理对话框并帮助检索用户输入的信息。|  
|初始化、验证和检索对话框数据。|您还可以定义初始化和验证对话框的控件的方式。 使用 Visual Studio 将成员变量添加到对话框类，并将这些变量映射到对话框控件。 指定要在用户输入数据时应用于每个控件的验证规则。 根据需要提供您自己的自定义验证。|框架管理对话框初始化和验证。 如果用户输入无效的信息，框架将显示消息框并让用户重新输入数据。|  
|创建其他类。|除 MFC 应用程序向导自动创建的参数之外，使用类视图创建附加文档、视图和框架窗口类。 您可以创建其他数据库记录集类、对话框类等。 （利用类视图，您可以创建并非派生自 MFC 类的类。）|类视图这些类添加到您的源文件并帮助您定义它们与所处理的任何命令的关联。|  
|将可以立即使用的组件添加到应用程序。|使用 `New Item dialog box` 添加各种项。|这些项可轻松集成到应用程序中，从而显著减少了您的工作量。|  
|实现文档类。|实现特定于应用程序的文档类。 添加成员变量以保留数据结构。 添加成员函数以提供数据的接口。|框架已经知道如何与文档数据文件交互。 它可以打开和关闭文档文件、读取和写入文档的数据以及处理其他用户界面。 您可以重点关注如何操作文档的数据。|  
|实现“打开”、“保存”和“另存为”命令。|为文档的 `Serialize` 成员函数编写代码。|框架显示对话框，**打开**，**保存**，和**另存为**上的命令**文件**菜单。 该对话框使用 `Serialize` 成员函数中指定的数据格式写回和读回文档。|  
|实现视图类。|实现与文档对应的一个或多个视图类。 使用类视图实现您映射到用户界面的视图的成员函数。 各种[CView](../mfc/reference/cview-class.md)-派生的类是可用，包括[CListView](../mfc/reference/clistview-class.md)和[CTreeView](../mfc/reference/ctreeview-class.md)。|框架管理文档及其视图之间的大多数关系。 该视图的成员函数访问视图的文档，以便在屏幕或打印页上呈现其图像和更新文档的数据结构以响应用户编辑命令。|  
|增强默认打印。|如果需要支持多页打印，请重写视图成员函数。|框架支持**打印**，**页面设置**，和**打印预览**上的命令**文件**菜单。 您必须告诉它如何将文档分为多个页。|  
|添加滚动。|如果你需要支持滚动，派生视图类或从类[CScrollView](../mfc/reference/cscrollview-class.md)。|当视图窗口变得过小时，视图将自动添加滚动条。|  
|创建窗体视图。|如果你想要该视图基于对话框模板资源，派生视图类或从类[CFormView](../mfc/reference/cformview-class.md)。|该视图使用对话框模板资源来显示控件。 用户可以使用 Tab 键切换视图中的控件。|  
|创建数据库窗体。|如果你想基于窗体的数据访问应用程序，派生视图类从[CRecordView](../mfc/reference/crecordview-class.md) （对于 ODBC 编程）。|该视图的工作方式类似的窗体视图，但其控件连接到的各个字段[CRecordset](../mfc/reference/crecordset-class.md)表示数据库表对象。 MFC 将为您在控件和记录集之间移动数据。|  
|创建简单文本编辑器。|如果你想让视图成为简单文本编辑器，派生视图类或从类[CEditView](../mfc/reference/ceditview-class.md)或[CRichEditView](../mfc/reference/cricheditview-class.md)。|该视图提供了编辑函数、剪贴板支持和文件输入/输出。 `CRichEditView` 提供了带样式的文本。|  
|增加拆分窗口|如果你想要支持拆分窗口，添加[CSplitterWnd](../mfc/reference/csplitterwnd-class.md)到 SDI 框架窗口或 MDI 子窗口对象和其挂钩到窗口的[OnCreateClient](../mfc/reference/cframewnd-class.md#oncreateclient)成员函数。|框架在滚动条旁边提供拆分框控件并管理将您的视图拆分为多个窗格。 如果用户拆分了一个窗口，框架将创建视图对象并将其附加到文档。|  
|生成、测试和调试应用程序。|使用 Visual C++ 的工具生成、测试和调试应用程序。|Visual C++ 可让您调整编译、链接和其他选项。 它还可让你浏览源代码和类结构。|  
  
## <a name="see-also"></a>请参阅  
 [用于创建 OLE 应用程序的操作顺序](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [用于创建 ActiveX 控件的操作顺序](../mfc/sequence-of-operations-for-creating-activex-controls.md)   
 [用于创建数据库应用程序的操作顺序](../mfc/sequence-of-operations-for-creating-database-applications.md)   
 [基于框架生成](../mfc/building-on-the-framework.md)

