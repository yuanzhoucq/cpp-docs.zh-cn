---
title: MFC： 结合文档和视图使用数据库类 |Microsoft 文档
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
ms.openlocfilehash: fcaee376b53c1d592f02aafc830a35d72f64feeb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091863"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC：结合文档和视图使用数据库类
你可以使用 MFC 数据库类具有或不使用文档/视图体系结构。 本主题重点介绍使用结合文档和视图的数据库。 它还说明了：  
  
-   [如何编写一个基于窗体的应用程序](#_core_writing_a_form.2d.based_application)使用`CRecordView`对象作为文档上的主视图。  
  
-   [如何使用文档和视图中的记录集对象](#_core_using_recordsets_in_documents_and_views)。  
  
-   [其他注意事项](#_core_other_factors)。  
  
 有关其他信息，请参阅[MFC： 使用数据库类不结合文档和视图](../data/mfc-using-database-classes-without-documents-and-views.md)。  
  
##  <a name="_core_writing_a_form.2d.based_application"></a> 编写基于窗体的应用程序  
 许多数据访问应用程序都基于窗体。 用户界面是包含在其中用户将检查、 输入，或编辑数据控件的窗体。 若要使基于应用程序窗体，使用类`CRecordView`。 当你运行 MFC 应用程序向导并选择**ODBC**上的客户端类型**数据库支持**页上，项目使用`CRecordView`视图类。
  
 在基于窗体的应用中，每个记录视图对象存储指向的`CRecordset`对象。 框架的记录字段交换 (RFX) 机制交换记录集和数据源之间的数据。 对话框数据交换 (DDX) 的记录集对象的字段数据成员和窗体上的控件之间的机制交换数据。 `CRecordView` 此外提供了默认命令处理程序函数用于在记录间导航窗体上。  
  
 若要使用应用程序向导创建基于窗体的应用程序，请参阅[创建基于窗体的 MFC 应用程序](../mfc/reference/creating-a-forms-based-mfc-application.md)和[数据库支持，MFC 应用程序向导](../mfc/reference/database-support-mfc-application-wizard.md)。  
  
 有关窗体的完整讨论，请参阅[记录视图](../data/record-views-mfc-data-access.md)。  
  
##  <a name="_core_using_recordsets_in_documents_and_views"></a> 使用在文档和视图中的记录集  
 许多简单基于窗体的应用程序不需要的文档。 如果你的应用程序比较复杂，你可能想要使用文档作为代理的数据库，存储`CDatabase`连接到数据源的对象。 基于窗体的应用程序通常在视图中存储指向记录集对象的指针。 存储记录集的其他类型的数据库应用程序和`CDatabase`文档中的对象。 下面是一些可能的数据库应用程序中使用文档：  
  
-   如果你正在访问在本地上下文中的记录集，创建`CRecordset`根据需要本地对象中的文档或视图中，成员函数。  
  
     将记录集对象声明为函数中的本地变量。 传递**NULL**到构造函数中，这将导致产生框架，创建并打开一个临时`CDatabase`为你的对象。 作为替代方法，将传递指向的指针`CDatabase`对象。 使用在函数中的记录集并让它在函数退出时自动销毁。  
  
     传递时， **NULL**到记录集构造函数时，框架将使用返回的记录集的信息`GetDefaultConnect`成员函数来创建`CDatabase`对象并将其打开。 向导实现`GetDefaultConnect`为你。  
  
-   如果你的文档的生命周期内访问记录集，将嵌入到一个或多个`CRecordset`文档中的对象。  
  
     初始化该文档时，或根据需要请构造的记录集对象。 你可以编写将指针返回到记录集，如果已经存在或构造并打开记录集，如果尚不存在它的函数。 关闭、 删除和重新创建记录集，根据需要或调用其**Requery**成员函数以刷新记录。  
  
-   如果你的文档的生命周期内访问数据源，将嵌入到`CDatabase`对象或存储指向的指针`CDatabase`中它的对象。  
  
     `CDatabase`对象管理对数据源的连接。 对象在文档构造期间自动构造和调用其**打开**成员函数初始化该文档时。 在构造中文档成员函数的记录集对象时，将指针传递文档的`CDatabase`对象。 这会与其数据源关联每个记录集。 在文档关闭时，通常将销毁的数据库对象。 当它们退出函数的范围内时，通常会被销毁的记录集对象。  
  
##  <a name="_core_other_factors"></a> 其他因素  
 基于窗体的应用程序通常不具有任何用于框架的文档序列化机制，因此你可能想要删除、 禁用或替换`New`和**打开**上的命令**文件**菜单。 请参阅文章[序列化： 序列化 vs。数据库输入/输出](../mfc/serialization-serialization-vs-database-input-output.md)。  
  
 您可能还想要使用的框架可以支持的许多用户界面可能性。 例如，可以使用多个`CRecordView`对象在拆分器窗口中，在不同打开多个记录集，多文档界面 (MDI) 子窗口，依次类推。  
  
 你可能想要实现打印在视图中的所有内容，无论它是与实现的窗体`CRecordView`还是其他内容。 类派生自`CFormView`，`CRecordView`不支持打印，但你可以重写`OnPrint`成员函数，以允许打印。 有关详细信息，请参阅类[CFormView](../mfc/reference/cformview-class.md)。  
  
 你可能不想要在所有使用文档和视图。 在这种情况下，请参阅[MFC： 使用数据库类不结合文档和视图](../data/mfc-using-database-classes-without-documents-and-views.md)。  
  
## <a name="see-also"></a>请参阅  
 [MFC 数据库类 (.../ data/mfc-database-classes-odbc-and-dao.md）