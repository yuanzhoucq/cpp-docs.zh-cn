---
title: MFC：结合文档和视图使用数据库类
ms.date: 11/04/2016
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
ms.openlocfilehash: e2b073b20b9518667b43c30e7ee3199a84a3ad38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213377"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC：结合文档和视图使用数据库类

你可以使用或不使用文档/视图体系结构的 MFC 数据库类。 本主题重点介绍如何使用文档和视图。 说明：

- 如何使用 `CRecordView` 对象[编写基于窗体的应用程序](#_core_writing_a_form.2d.based_application)作为文档的主视图。

- [如何在文档和视图中使用记录集对象](#_core_using_recordsets_in_documents_and_views)。

- [其他注意事项](#_core_other_factors)。

有关替代方法，请参阅[MFC：使用没有文档和视图的数据库类](../data/mfc-using-database-classes-without-documents-and-views.md)。

##  <a name="writing-a-form-based-application"></a><a name="_core_writing_a_form.2d.based_application"></a>编写基于窗体的应用程序

许多数据访问应用程序都基于窗体。 用户界面是一种包含控件的窗体，用户在其中检查、输入或编辑数据。 若要使应用程序基于窗体，请使用类 `CRecordView`。 当你运行 MFC 应用程序向导并在**数据库支持**页上选择 " **ODBC**客户端类型" 时，该项目将为视图类使用 `CRecordView`。

在基于窗体的应用程序中，每个记录视图对象均存储一个指向 `CRecordset` 对象的指针。 框架的记录字段交换（RFX）机制在记录集和数据源之间交换数据。 对话框数据交换（DDX）机制在记录集对象的字段数据成员与窗体上的控件之间交换数据。 `CRecordView` 还提供了用于在窗体上从记录导航到记录的默认命令处理程序函数。

若要使用应用程序向导创建基于窗体的应用程序，请参阅[Mfc 应用程序向导](../mfc/reference/database-support-mfc-application-wizard.md)[创建基于窗体的 mfc 应用程序](../mfc/reference/creating-a-forms-based-mfc-application.md)和数据库支持。

有关窗体的完整讨论，请参阅[记录视图](../data/record-views-mfc-data-access.md)。

##  <a name="using-recordsets-in-documents-and-views"></a><a name="_core_using_recordsets_in_documents_and_views"></a>在文档和视图中使用记录集

许多简单的基于窗体的应用程序不需要文档。 如果您的应用程序更复杂，您可能需要使用文档作为数据库的代理，并存储连接到数据源的 `CDatabase` 对象。 基于窗体的应用程序通常在视图中存储指向记录集对象的指针。 其他类型的数据库应用程序将记录集和 `CDatabase` 对象存储在文档中。 下面是在数据库应用程序中使用文档的一些可能性：

- 如果要访问本地上下文中的记录集，请根据需要在文档或视图的成员函数中本地创建 `CRecordset` 对象。

   在函数中将记录集对象声明为局部变量。 将 NULL 传递给构造函数，该构造函数会使框架创建并打开临时 `CDatabase` 对象。 作为替代方法，传递指向 `CDatabase` 对象的指针。 使用函数中的记录集，并让它在函数退出时自动销毁。

   将 NULL 传递给记录集构造函数时，框架使用记录集的 `GetDefaultConnect` 成员函数返回的信息创建 `CDatabase` 对象并将其打开。 向导将为你实现 `GetDefaultConnect`。

- 如果在文档的生存期内访问记录集，请将一个或多个 `CRecordset` 对象嵌入文档中。

   当您初始化文档或根据需要构造记录集对象时。 您可以编写一个函数，该函数返回指向记录集的指针（如果它已存在），或者构造并打开该记录集（如果它尚不存在）。 根据需要关闭、删除和重新创建记录集，或调用其 `Requery` 成员函数来刷新记录。

- 如果在文档的生存期内访问数据源，请嵌入 `CDatabase` 对象，或在其中存储指向 `CDatabase` 对象的指针。

   `CDatabase` 对象管理与数据源的连接。 对象是在文档构造过程中自动构造的，在您初始化文档时调用其 `Open` 成员函数。 在文档成员函数中构造记录集对象时，会将指针传递到文档的 `CDatabase` 对象。 这会将每个记录集与其数据源关联。 当文档关闭时，数据库对象通常被销毁。 当记录集对象退出函数的作用域时，通常会销毁它们。

##  <a name="other-factors"></a><a name="_core_other_factors"></a>其他因素

基于窗体的应用程序通常不会使用框架的文档序列化机制，因此，您可能想要删除、禁用或替换 "**文件**" 菜单上的 "**新建**" 和 "**打开**" 命令。 请参阅文章[序列化：序列化与数据库输入/输出](../mfc/serialization-serialization-vs-database-input-output.md)。

你可能还希望利用框架可以支持的许多用户界面的可能性。 例如，可以在拆分窗口中使用多个 `CRecordView` 对象，在不同的多文档界面（MDI）子窗口中打开多个记录集，等等。

你可能想要打印视图中的任何内容，无论它是使用 `CRecordView` 还是其他内容实现的窗体。 作为从 `CFormView`派生的类，`CRecordView` 不支持打印，但你可以重写 `OnPrint` 成员函数以允许打印。 有关详细信息，请参阅类[CFormView](../mfc/reference/cformview-class.md)。

您可能根本不想使用文档和视图。 在这种情况下，请参阅[MFC：不使用文档和视图的数据库类](../data/mfc-using-database-classes-without-documents-and-views.md)。

## <a name="see-also"></a>另请参阅

[MFC 数据库类](../data/mfc-database-classes-odbc-and-dao.md)
