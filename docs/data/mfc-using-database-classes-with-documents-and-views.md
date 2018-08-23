---
title: MFC： 结合文档和视图使用数据库类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- documents [C++], database applications
- recordsets [C++], documents and views
- CRecordView class, using in database forms
- views [C++], database applications
- forms [C++], database applications
- record views [C++], form-based applications
- document/view architecture [C++], in databases
- database applications [C++], forms
- database classes [C++], MFC
- ODBC recordsets [C++], documents and views
- ODBC [C++], forms
ms.assetid: 83979974-fc63-46ac-b162-e8403a572e2c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 527de152f7eea9e71cb38a9ca2f51e15803df337
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337042"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC：结合文档和视图使用数据库类
使用或不使用文档/视图体系结构，可以使用 MFC 数据库类。 本主题重点介绍使用结合文档和视图的数据库。 说明：  
  
-   [如何编写基于窗体的应用程序](#_core_writing_a_form.2d.based_application)使用`CRecordView`对象作为您的文档上的主视图。  
  
-   [如何使用文档和视图中的记录集对象](#_core_using_recordsets_in_documents_and_views)。  
  
-   [其他注意事项](#_core_other_factors)。  
  
 有关其他信息，请参阅[MFC： 使用数据库类不结合文档和视图](../data/mfc-using-database-classes-without-documents-and-views.md)。  
  
##  <a name="_core_writing_a_form.2d.based_application"></a> 编写基于窗体的应用程序  
 许多数据访问应用程序基于窗体。 用户界面是包含的控件中的用户将检查、 输入，或编辑数据的窗体。 若要使基于应用程序窗体，请使用类`CRecordView`。 在运行 MFC 应用程序向导并选择**ODBC**上的客户端类型**数据库支持**页上，该项目使用`CRecordView`视图类。
  
 在基于窗体的应用程序中，每个记录视图对象存储指向`CRecordset`对象。 框架的记录字段交换 (RFX) 机制交换记录集和数据源之间的数据。 对话框数据交换 (DDX) 记录集对象的字段数据成员和窗体上的控件之间的机制交换数据。 `CRecordView` 此外提供了默认命令处理程序函数用于导航记录到记录窗体上。  
  
 若要使用的应用程序向导创建基于窗体的应用程序，请参阅[创建基于窗体的 MFC 应用程序](../mfc/reference/creating-a-forms-based-mfc-application.md)并[数据库支持，MFC 应用程序向导](../mfc/reference/database-support-mfc-application-wizard.md)。  
  
 窗体的完整讨论，请参阅[记录视图](../data/record-views-mfc-data-access.md)。  
  
##  <a name="_core_using_recordsets_in_documents_and_views"></a> 使用文档和视图中的记录集  
 许多简单的基于窗体应用程序不需要的文档。 如果应用程序是更复杂，你可能想要使用文档作为代理的数据库，将存储`CDatabase`连接到数据源的对象。 基于窗体的应用程序通常在视图中存储指向记录集对象的指针。 其他类型的数据库应用程序存储的记录集和`CDatabase`文档中的对象。 下面是在数据库应用程序中使用的文档的一些可能性：  
  
-   如果您正在访问本地上下文中的记录集，创建`CRecordset`根据需要本地对象中的文档或视图中，成员函数。  
  
     将记录集对象声明为一个函数中的本地变量。 将 NULL 传递给构造函数中，这会导致框架创建并打开一个临时`CDatabase`为您的对象。 作为替代方法，传递一个指向`CDatabase`对象。 使用记录集的函数中，使其在函数退出时自动销毁。  
  
     框架将 NULL 传递给记录集构造函数中，使用返回的记录集的信息`GetDefaultConnect`成员函数来创建`CDatabase`对象，并将其打开。 这些向导实现`GetDefaultConnect`为您。  
  
-   如果您的文档的生命周期内访问记录集，嵌入一个或多个`CRecordset`文档中的对象。  
  
     初始化此文档或根据需要来构造的记录集对象。 您可以编写将指针返回到记录集，如果它已存在或构造并打开记录集，如果它尚不存在的函数。 关闭、 删除和重新创建记录集，如有需要或调用其`Requery`成员函数以刷新记录。  
  
-   如果您的文档的生命周期内访问数据源，嵌入`CDatabase`对象或存储到指针`CDatabase`中它的对象。  
  
     `CDatabase`对象管理与数据源的连接。 在文档构造期间自动构造对象并调用其`Open`时初始化此文档成员函数。 在构造文档成员函数中的记录集对象时，将指针传递文档的`CDatabase`对象。 这将使用其数据源相关联每个记录集。 在文档关闭时，通常被破坏的数据库对象。 记录集对象通常被销毁时它们退出函数的作用域。  
  
##  <a name="_core_other_factors"></a> 其他因素  
 基于窗体的应用程序通常不具有任何使用框架的文档序列化机制，因此你可能想要删除、 禁用或替换**新建**并**打开**上的命令**文件**菜单。 请参阅文章[序列化： 序列化 vs。数据库输入/输出](../mfc/serialization-serialization-vs-database-input-output.md)。  
  
 您可能还想要使用的框架可以支持的许多用户界面可能方式。 例如，可以使用多个`CRecordView`在拆分器窗口中，对象在不同打开多个记录集，多文档界面 (MDI) 子窗口，依次类推。  
  
 你可能想要实现您的视图中的所有内容的打印，无论它是一个窗体实现与`CRecordView`还是其他内容。 类派生自`CFormView`，`CRecordView`不支持打印，但您可以重写`OnPrint`成员函数以允许进行打印。 有关详细信息，请参阅类[CFormView](../mfc/reference/cformview-class.md)。  
  
 可能不想要在所有使用文档和视图。 在这种情况下，请参阅[MFC： 使用数据库类不结合文档和视图](../data/mfc-using-database-classes-without-documents-and-views.md)。  
  
## <a name="see-also"></a>请参阅  
 [MFC 数据库类 (.../ data/mfc-database-classes-odbc-and-dao.md）