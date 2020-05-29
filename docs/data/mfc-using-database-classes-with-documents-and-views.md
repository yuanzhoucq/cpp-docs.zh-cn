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
ms.openlocfilehash: 9e071e0cc25492073cd74ed517284476b6e49ef8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368902"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC：结合文档和视图使用数据库类

您可以使用具有或不带文档/视图体系结构的 MFC 数据库类。 本主题强调使用文档和视图。 它解释了：

- 如何使用`CRecordView`对象作为文档的主视图[编写基于窗体的应用程序](#_core_writing_a_form.2d.based_application)。

- [如何在文档和视图中使用记录集对象](#_core_using_recordsets_in_documents_and_views)。

- [其他注意事项](#_core_other_factors)。

有关备选方案，请参阅[MFC：使用没有文档和视图的数据库类](../data/mfc-using-database-classes-without-documents-and-views.md)。

## <a name="writing-a-form-based-application"></a><a name="_core_writing_a_form.2d.based_application"></a>编写基于表单的应用程序

许多数据访问应用程序都基于表单。 用户界面是一个窗体，其中包含用户检查、输入或编辑数据的控件。 要使应用程序表单基于，请使用 类`CRecordView`。 当您运行 MFC 应用程序向导并在**数据库支持**页上选择**ODBC**客户端类型时，项目将`CRecordView`用于视图类。

在基于窗体的应用程序中，每个记录视图对象都存储指向对象的`CRecordset`指针。 框架的记录字段交换 （RFX） 机制在记录集和数据源之间交换数据。 对话框数据交换 （DDX） 机制在记录集对象的字段数据成员和窗体上的控件之间交换数据。 `CRecordView`还提供默认命令处理程序函数，用于在窗体上从记录导航到记录。

要使用应用程序向导创建基于表单的应用程序，请参阅[创建基于窗体的 MFC 应用程序](../mfc/reference/creating-a-forms-based-mfc-application.md)和[数据库支持，MFC 应用程序向导](../mfc/reference/database-support-mfc-application-wizard.md)。

有关窗体的完整讨论，请参阅[记录视图](../data/record-views-mfc-data-access.md)。

## <a name="using-recordsets-in-documents-and-views"></a><a name="_core_using_recordsets_in_documents_and_views"></a>在文档和视图中使用记录集

许多简单的基于表单的应用程序不需要文档。 如果应用程序比较复杂，则可能需要将文档用作数据库的代理，存储连接到数据源`CDatabase`的对象。 基于窗体的应用程序通常将指向视图中的记录集对象的指针存储。 其他类型的数据库应用程序在文档中存储记录集和`CDatabase`对象。 以下是在数据库应用程序中使用文档的一些可能性：

- 如果要访问本地上下文中的记录集，请根据需要在文档或视图的成员函数`CRecordset`中本地创建对象。

   将记录集对象声明为函数中的局部变量。 将 NULL 传递给构造函数，这将导致框架为您创建并打开临时`CDatabase`对象。 作为替代方法，将指针传递给对象`CDatabase`。 使用函数中的记录集，并在函数退出时自动销毁它。

   将 NULL 传递给记录集构造函数时，框架将使用记录集`GetDefaultConnect`成员函数返回的信息创建`CDatabase`对象并打开它。 向导为您实现`GetDefaultConnect`。

- 如果在文档的生存期内访问记录集，请将一个或多个`CRecordset`对象嵌入到文档中。

   在初始化文档时或根据需要构造记录集对象。 如果记录集已存在或构造，则可以编写返回指向记录集的指针的函数，如果记录集尚不存在，则该函数将打开该记录集。 根据需要关闭、删除和重新创建记录集，或调用其成员`Requery`函数刷新记录。

- 如果在文档的生存期内访问数据源，请嵌入`CDatabase`对象或存储指向其中对象的`CDatabase`指针。

   该`CDatabase`对象管理与数据源的连接。 对象在文档构造期间自动构造，并在初始化文档时`Open`调用其成员函数。 在文档成员函数中构造记录集对象时，会传递指向文档`CDatabase`对象的指针。 这将将每个记录集与其数据源关联。 数据库对象通常在文档关闭时销毁。 记录集对象通常会在退出函数范围时销毁它们。

## <a name="other-factors"></a><a name="_core_other_factors"></a>其他因素

基于窗体的应用程序通常对框架的文档序列化机制没有任何用，因此您可能需要删除、禁用或替换 **"文件**"菜单上的 **"新建**"和 **"打开"** 命令。 请参阅文章[序列化：序列化与数据库输入/输出](../mfc/serialization-serialization-vs-database-input-output.md)。

您可能还希望利用框架可以支持的许多用户界面可能性。 例如，您可以在拆分器窗口中使用`CRecordView`多个对象，在不同的多个文档接口 （MDI） 子窗口中打开多个记录集，等等。

您可能希望实现对视图中任何内容的打印，无论是使用`CRecordView`或其他方式实现的形式。 由于派生自`CFormView`的`CRecordView`类不支持打印，但您可以重写`OnPrint`成员函数以允许打印。 有关详细信息，请参阅类[CFormView](../mfc/reference/cformview-class.md)。

您可能根本不想要使用文档和视图。 在这种情况下，请参阅[MFC：使用没有文档和视图的数据库类](../data/mfc-using-database-classes-without-documents-and-views.md)。

## <a name="see-also"></a>另请参阅

[MFC 数据库类](../data/mfc-database-classes-odbc-and-dao.md)
