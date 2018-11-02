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
ms.openlocfilehash: 558917f1a1485f1a886356b3c272842579f6b03e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602210"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC：不结合文档和视图使用数据库类

有时可能不想要使用在数据库应用程序框架的文档/视图体系结构。 本主题说明：

- [不需要使用文档](#_core_when_you_don.92.t_need_documents)如文档序列化。

- [应用程序向导选项](#_core_appwizard_options_for_documents_and_views)以支持应用程序而不需要序列化并与文档相关**文件**菜单命令，如**新建**，**打开****保存**，并**另存为**。

- [如何使用最小的文档的应用程序使用](#_core_applications_with_minimal_documents)。

- [如何构造没有文档或视图的应用程序](#_core_applications_with_no_document)。

##  <a name="_core_when_you_don.92.t_need_documents"></a> 当不需要的文档

某些应用程序具有完全不同的文档。 这些应用程序通常所有或大多数文件从存储加载到内存中，**文件打开**命令。 这些更新将文件写回到一次性使用的存储**文件保存**或**另存为**命令。 哪些用户看到的是数据文件。

但是，某些类别的应用程序，不需要一个文档。 数据库应用程序运行在事务方面。 应用程序从数据库选择记录，并将它们提供给用户，通常一次一个。 哪些用户将看到通常是单个的当前记录，这可能是内存中仅有的。

如果你的应用程序不需要用于存储数据的文档，可完成部分或全部框架的文档/视图体系结构中进行分配。 摒弃的多少取决于你首选的方法。 您可能会：

- 使用作为的位置的最小的文档存储到你的数据源的连接，但摒弃常规文档功能，如序列化。 当你想数据的多个视图并想要同步所有视图中，更新其一次性等，这很有用。

- 使用在其中您描述直接，而不是使用视图的框架窗口。 在这种情况下中, 省略文档，并在框架窗口对象中存储任何数据或数据连接。

##  <a name="_core_appwizard_options_for_documents_and_views"></a> 文档和视图的应用程序向导选项

MFC 应用程序向导提供了若干选项**选择数据库支持**下, 表中列出的。 如果使用 MFC 应用程序向导创建的应用程序，所有这些选项将生成具有文档和视图的应用程序。 某些选项提供文档和省略不必要的文档功能的视图。 有关详细信息，请参阅[数据库支持，MFC 应用程序向导](../mfc/reference/database-support-mfc-application-wizard.md)。

|选项|视图|Document|
|------------|----------|--------------|
|**无**|从 `CView`派生。|提供了不支持数据库。 这是默认选项。<br /><br /> 如果选择**文档/视图体系结构支持**选项卡上[应用程序类型、 MFC 应用程序向导](../mfc/reference/application-type-mfc-application-wizard.md)页中，获取完整的文档支持，包括序列化和**新建**，**开放**，**保存**，并且**另存为**上命令**文件**菜单。 请参阅[应用程序与任何文档](#_core_applications_with_no_document)。|
|**仅头文件**|从 `CView`派生。|为应用程序提供基本级别的数据库支持。<br /><br /> 包括 Afxdb.h。 添加链接库，但不会创建任何数据库特定的类。 您可以更高版本创建记录集，并使用它们来检查和更新记录。|
|**不支持文件的数据库视图**|派生自 `CRecordView`|提供文档支持，但没有序列化支持。 文档可以存储记录集和协调多个视图;不支持序列化或**新建**，**打开**，**保存**，以及**另存为**命令。 请参阅[应用程序的最小的文档](#_core_applications_with_minimal_documents)。 如果包含的数据库视图，则必须指定数据源。<br /><br /> 包括数据库标头文件、 链接库、 记录视图和一个记录集。 (仅适用于应用程序与**文档/视图体系结构支持**上选择的选项[应用程序类型、 MFC 应用程序向导](../mfc/reference/application-type-mfc-application-wizard.md)页。)|
|**提供文件支持的数据库视图**|派生自 `CRecordView`|提供了完整的文档支持，包括序列化和与文档相关**文件**菜单命令。 数据库应用程序通常运行在每个记录的基础上而不是每个文件中的基础，因此不需要序列化。 但是，您可能必须序列化的特殊用法。 请参阅[应用程序的最小的文档](#_core_applications_with_minimal_documents)。 如果包含的数据库视图，则必须指定数据源。<br /><br /> 包括数据库标头文件、 链接库、 记录视图和一个记录集。 (仅适用于应用程序与**文档/视图体系结构支持**上选择的选项[应用程序类型、 MFC 应用程序向导](../mfc/reference/application-type-mfc-application-wizard.md)页。)|

有关序列化和序列化的其他用途的替代方法的讨论，请参阅[序列化： 序列化 vs。数据库输入/输出](../mfc/serialization-serialization-vs-database-input-output.md)。

##  <a name="_core_applications_with_minimal_documents"></a> 具有最小的文档的应用程序

MFC 应用程序向导有支持基于窗体的数据访问应用程序的两个选项。 每个选项创建`CRecordView`-派生视图类和文档。 它们的区别在于它们所排除的文档之外。

###  <a name="_core_a_document_without_file_support"></a> 不支持文件的文档

选择应用程序向导数据库选项**数据库不支持文件的视图**如果不需要文档序列化。 该文档具有下列用途：

- 它是一个方便的位置来存储`CRecordset`对象。

   这种用法与普通文档概念： 文档存储的数据 （或，在这种情况下，一组记录） 和该视图是文档的视图。

- 如果你的应用程序提供多个视图 （如多个记录视图），则文档支持协调视图。

   如果多个视图显示相同的数据，则可以使用`CDocument::UpdateAllViews`成员函数以协调对所有视图的更新时任何视图中更改的数据。

通常情况下，为简单的基于窗体的应用程序需要使用此选项。 应用程序向导自动支持此类应用程序的方便使用的结构。

###  <a name="_core_a_document_with_file_support"></a> 提供文件支持的文档

选择应用程序向导数据库选项**数据库支持文件的视图**如果有其他用途与文档相关**文件**菜单命令和文档序列化。 对于您的程序的数据访问部分，您可以使用文档相同的方式中所述[文档不带文件支持](#_core_a_document_without_file_support)。 可用于文档的序列化功能，例如，读取和写入存储用户的首选项或其他有用信息的序列化的用户配置文件文档。 有关详细信息，请参阅[序列化： 序列化 vs。数据库输入/输出](../mfc/serialization-serialization-vs-database-input-output.md)。

应用程序向导支持此选项，但必须编写将文档序列化的代码。 文档数据成员中存储的序列化的信息。

##  <a name="_core_applications_with_no_document"></a> 没有文档的应用程序

有时可能想要编写的应用程序不使用文档或视图。 无文档时，您将数据存储 (如`CRecordset`对象) 框架窗口类或应用程序类中。 任何其他要求取决于是否在应用程序提供了一个用户界面。

###  <a name="_core_database_support_with_a_user_interface"></a> 使用用户界面的数据库支持

如果您有一个用户界面 （不是，例如，控制台命令行接口），则应用程序直接在框架窗口的工作区而不是视图。 此类应用程序不使用`CRecordView`， `CFormView`，或`CDialog`主用户界面，但它通常使用`CDialog`普通的对话框。

###  <a name="_core_writing_applications_without_documents"></a> 没有文档编写应用程序

因为应用程序向导不支持无文档创建应用程序，必须编写您自己`CWinApp`的派生类，并且如果需要还创建`CFrameWnd`或`CMDIFrameWnd`类。 重写`CWinApp::InitInstance`和将应用程序对象声明为：

```cpp
CYourNameApp theApp;
```

框架还提供的消息映射机制和许多其他功能。

###  <a name="_core_database_support_separate_from_the_user_interface"></a> 数据库支持独立于用户界面

某些应用程序需要的用户界面或仅一个最小。 例如，假设你正在编写：

- 中间数据访问对象的其他应用程序 （客户端） 调用进行特殊处理的应用程序和数据源之间的数据。

- 处理数据而无需用户干预，例如将数据从一个数据库格式移到另一种或进行计算，因此执行批处理更新的应用程序的应用程序。

由于没有文档拥有`CRecordset`对象，你可能想要将其存储中的嵌入的数据成员为你`CWinApp`-派生应用程序类。 备用方法包括：

- 不保留一个永久`CRecordset`根本对象。 可以将 NULL 传递到记录集类构造函数。 在这种情况下，框架将创建一个临时`CDatabase`记录集的对象信息`GetDefaultConnect`成员函数。 这是最有可能的另一种方法。

- 使`CRecordset`对象的全局变量。 此变量应为指向您创建动态中的记录集对象的指针在`CWinApp::InitInstance`重写。 这样可避免尝试初始化框架之前构造对象。

- 就像一个文档或视图的上下文中，请使用记录集对象。 在成员中的应用程序或框架窗口对象的函数创建记录集。

## <a name="see-also"></a>请参阅

[MFC 数据库类](../data/mfc-database-classes-odbc-and-dao.md)