---
title: MFC：不结合文档和视图使用数据库类
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC applications [C++], without views
- documents [C++], applications without
- ODBC applications [C++]
- document/view architecture [C++], in databases
- files [C++], MFC
- database classes [C++], MFC
- CRecordView class, using in database applications
- database applications [C++], without views
- database applications [C++], application wizard options
- application wizards [C++], creating database applications
- ODBC [C++], file support in database applications
- ODBC applications [C++], without documents
- database applications [C++], without documents
- user interface [C++], drawing information
ms.assetid: 15bf52d4-91cf-4b1d-8b37-87c3ae70123a
ms.openlocfilehash: c914a449b73e7da876d2e05b894c016b53881c3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360675"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC：不结合文档和视图使用数据库类

有时，您可能不希望在数据库应用程序中使用框架的文档/视图体系结构。 本主题介绍：

- [当您不需要使用文档](#_core_when_you_don.92.t_need_documents)（如文档序列化）时。

- [应用程序向导选项](#_core_appwizard_options_for_documents_and_views)，支持应用程序不序列化和没有文档相关的**文件**菜单命令，如**新建**、**打开**、**保存**和**保存为**。

- [如何使用使用最小文档的应用程序](#_core_applications_with_minimal_documents)。

- [如何构建没有文档或视图的应用程序](#_core_applications_with_no_document)。

## <a name="when-you-do-not-need-documents"></a><a name="_core_when_you_don.92.t_need_documents"></a>当您不需要文档时

某些应用程序具有文档的不同概念。 这些应用程序通常使用**文件打开**命令将存储中的所有或大部分文件加载到内存中。 他们用**文件保存**或**保存为**命令一次将更新的文件写回存储。 用户看到的是一个数据文件。

但是，某些类别的应用程序不需要文档。 数据库应用程序在事务方面运行。 应用程序从数据库中选择记录，并将记录呈现给用户，通常一次一个。 用户看到的通常是单个当前记录，这可能是内存中唯一的记录。

如果应用程序不需要用于存储数据的文档，则可以免除框架的文档/视图体系结构的部分或全部内容。 你放弃多少取决于你喜欢的方法。 您可以：

- 使用最小文档作为存储与数据源的连接的位置，但无需使用常规文档功能（如序列化）。 当您想要数据的几个视图并且想要同步所有视图、一次更新所有视图等时，这非常有用。

- 使用直接绘制的帧窗口，而不是使用视图。 在这种情况下，您省略文档并将任何数据或数据连接存储在框架窗口对象中。

## <a name="application-wizard-options-for-documents-and-views"></a><a name="_core_appwizard_options_for_documents_and_views"></a>文档和视图的应用程序向导选项

MFC 应用程序向导在 **"选择数据库支持"** 中有几个选项，这些选项列在下表中。 如果使用 MFC 应用程序向导创建应用程序，所有这些选项都会产生包含文档和视图的应用程序。 某些选项提供忽略不需要的文档功能的文档和视图。 有关详细信息，请参阅[数据库支持 MFC 应用程序向导](../mfc/reference/database-support-mfc-application-wizard.md)。

|选项|查看|Document|
|------------|----------|--------------|
|**无**|从 `CView`派生。|不提供数据库支持。 这是默认选项。<br /><br /> 如果在["应用程序类型"MFC 应用程序向导](../mfc/reference/application-type-mfc-application-wizard.md)页上选择**文档/视图体系结构支持**选项，则可以在 **"文件"** 菜单上获得完整的文档支持，包括序列化和**新建**、**打开**、**保存**和**保存为**命令。 请参阅[没有文档的应用程序](#_core_applications_with_no_document)。|
|**仅标题文件**|从 `CView`派生。|为应用程序提供基本级别的数据库支持。<br /><br /> 包括 Afxdb.h. 添加链接库，但不创建任何特定于数据库的类。 您可以稍后创建记录集，并使用它们来检查和更新记录。|
|**没有文件支持的数据库视图**|来自`CRecordView`|提供文档支持，但不提供序列化支持。 文档可以存储记录集并协调多个视图;不支持序列化或**新建**、**打开**、**保存**和**保存为**命令。 请参阅[具有最小文档的应用程序](#_core_applications_with_minimal_documents)。 如果包含数据库视图，则必须指定数据源。<br /><br /> 包括数据库标头文件、链接库、记录视图和记录集。 （仅适用于在["应用程序类型"MFC 应用程序向导](../mfc/reference/application-type-mfc-application-wizard.md)页面上选择**的文档/视图体系结构支持**选项的应用程序。|
|**支持文件的数据库视图**|来自`CRecordView`|提供完整的文档支持，包括序列化和文档相关的**文件**菜单命令。 数据库应用程序通常以每记录为基础，而不是基于每个文件运行，因此不需要序列化。 但是，您可能有序列化的特殊用途。 请参阅[具有最小文档的应用程序](#_core_applications_with_minimal_documents)。 如果包含数据库视图，则必须指定数据源。<br /><br /> 包括数据库标头文件、链接库、记录视图和记录集。 （仅适用于在["应用程序类型"MFC 应用程序向导](../mfc/reference/application-type-mfc-application-wizard.md)页面上选择**的文档/视图体系结构支持**选项的应用程序。|

有关序列化的替代和序列化的替代用途的讨论，请参阅[序列化：序列化与数据库输入/输出](../mfc/serialization-serialization-vs-database-input-output.md)。

## <a name="applications-with-minimal-documents"></a><a name="_core_applications_with_minimal_documents"></a>具有最小文档的应用程序

MFC 应用程序向导有两个选项支持基于表单的数据访问应用程序。 每个选项都创建`CRecordView`一个派生视图类和一个文档。 他们留下的文件不同。

### <a name="document-without-file-support"></a><a name="_core_a_document_without_file_support"></a>没有文件支持的文档

如果不需要文档序列化，请选择应用程序向导数据库选项**数据库选项数据库视图，而无需文件支持**。 本文档具有以下有用目的：

- 这是存储对象的`CRecordset`方便场所。

   此用法与普通文档概念类似：文档存储数据（或，在本例中为一组记录），视图是文档的视图。

- 如果应用程序显示多个视图（如多个记录视图），则文档支持协调视图。

   如果多个视图显示相同的数据，则可以使用`CDocument::UpdateAllViews`成员函数协调所有视图的更新，当任何视图更改数据时。

通常，对于简单的基于表单的应用程序，通常使用此选项。 应用程序向导自动支持此类应用程序的便捷结构。

### <a name="document-with-file-support"></a><a name="_core_a_document_with_file_support"></a>包含文件支持的文档

当您对文档相关的**文件**菜单命令和文档序列化具有替代用途时，选择**具有文件支持的应用程序向导数据库选项数据库视图**。 对于程序的数据访问部分，可以使用文档的方式与["无文件支持文档"](#_core_a_document_without_file_support)中所述的方式相同。 例如，可以使用文档的序列化功能读取和写入存储用户首选项或其他有用信息的序列化用户配置文件文档。 有关详细信息，请参阅[序列化：序列化与数据库输入/输出](../mfc/serialization-serialization-vs-database-input-output.md)。

应用程序向导支持此选项，但必须编写序列化文档的代码。 将序列化信息存储在文档数据成员中。

## <a name="applications-with-no-document"></a><a name="_core_applications_with_no_document"></a>无文档的应用程序

有时，您可能希望编写不使用文档或视图的应用程序。 如果没有文档，则可以将数据（如`CRecordset`对象）存储在框架窗口类或应用程序类中。 任何其他要求取决于应用程序是否提供用户界面。

### <a name="database-support-with-a-user-interface"></a><a name="_core_database_support_with_a_user_interface"></a>具有用户界面的数据库支持

如果您有用户界面（例如，控制台命令行界面），则应用程序将直接绘制到框架窗口的工作区，而不是到视图中。 此类应用程序不使用`CRecordView`或`CFormView``CDialog`用于其主用户界面，但它通常用于`CDialog`普通对话框。

### <a name="writing-applications-without-documents"></a><a name="_core_writing_applications_without_documents"></a>编写无文档的应用程序

由于应用程序向导不支持在没有文档的情况下创建应用程序，因此必须编写自己的`CWinApp`派生类，如果需要，还必须创建 或`CFrameWnd``CMDIFrameWnd`类。 重写`CWinApp::InitInstance`应用程序对象并将其声明为：

```cpp
CYourNameApp theApp;
```

该框架仍然提供消息映射机制和许多其他功能。

### <a name="database-support-separate-from-the-user-interface"></a><a name="_core_database_support_separate_from_the_user_interface"></a>数据库支持独立于用户界面

某些应用程序不需要用户界面或只需要最少的用户界面。 例如，假设您正在编写：

- 其他应用程序（客户端）要求在应用程序和数据源之间特殊处理数据的中间数据访问对象。

- 处理数据而不进行用户干预的应用程序，例如将数据从一种数据库格式移动到另一种数据库格式或执行批处理更新的应用程序。

由于没有文档拥有该`CRecordset`对象，因此您可能希望将其存储为`CWinApp`派生应用程序类中的嵌入式数据成员。 替代方案包括：

- 根本不保留永久`CRecordset`对象。 您可以将 NULL 传递给记录集类构造函数。 在这种情况下，框架使用记录集`CDatabase``GetDefaultConnect`的成员函数中的信息创建一个临时对象。 这是最有可能的替代方法。

- 使`CRecordset`对象成为全局变量。 此变量应指向在`CWinApp::InitInstance`重写中动态创建的记录集对象的指针。 这样可以避免在初始化框架之前尝试构造对象。

- 在文档或视图的上下文中使用记录集对象。 在应用程序或框架窗口对象的成员函数中创建记录集。

## <a name="see-also"></a>另请参阅

[MFC 数据库类](../data/mfc-database-classes-odbc-and-dao.md)
