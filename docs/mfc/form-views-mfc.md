---
title: 窗体视图 (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces [MFC], forms
- forms [MFC]
- applications [MFC], forms-based
- forms-based applications [MFC]
- forms [MFC], adding to applications
ms.assetid: efbe73c1-4ca4-4613-aac2-30d916e92c0e
ms.openlocfilehash: 5e8912c9013175fe254b2f4a4a968a67fd071f39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365301"
---
# <a name="form-views-mfc"></a>窗体视图 (MFC)

您可以将窗体添加到支持 MFC 库的任何 Visual C++ 应用程序，包括[基于窗体的应用程序](../mfc/reference/creating-a-forms-based-mfc-application.md)（其视图类派生自`CFormView`的应用程序）。 如果您最初未创建应用程序以支持表单，则 Visual C++将在插入新窗体时添加此支持。 在 SDI 或 MDI 应用程序中，当用户选择**New**命令（默认情况下，在 **"文件"** 菜单上）[时，Visual](../mfc/document-view-architecture.md)C++提示用户从可用窗体中进行选择。

使用 SDI 应用程序时，当用户选择**New**命令时，窗体的当前实例将继续运行，但如果找不到选定窗体，则将创建具有所选窗体的应用程序的新实例。 在 MDI 应用程序中，当用户选择**New**命令时，窗体的当前实例将继续运行。

> [!NOTE]
> 您可以将窗体插入到基于对话框的应用程序（其对话框类基于`CDialog`的，并且没有实现视图类的应用程序）。 但是，如果没有文档/视图体系结构，Visual C++不会自动实现 **"文件**&#124;**新功能**。 您必须创建一种方法，以便用户查看其他窗体，例如，通过实现具有各种属性页的选项卡式对话框。

将新窗体插入到应用程序中时，Visual C++ 执行以下操作：

- 基于您选择的窗体样式类之一`CFormView`（、或`CRecordView``CDaoRecordView` `CDialog`） 创建类。

- 创建具有适当样式的对话框资源（或者可以使用尚未与类关联的现有对话框资源）。

   如果选择现有对话框资源，则可能需要使用对话框的"属性"页来设置这些样式。 对话框的样式必须包括：

     **WS_CHILD**= 打开

     **WS_BORDER**= 关闭

     **WS_VISIBLE**= 关闭

     **WS_CAPTION**= 关闭

对于基于文档/视图体系结构的应用程序 **，"新建窗体"** 命令（在类视图中右键单击）也：

- 创建`CDocument`基于的类

   您可以在项目中使用任何基于的现有`CDocument`类，而不是创建新类。

- 使用字符串、菜单和图标资源`CDocument`生成文档模板（派生自 ）。

   您还可以创建一个新类，以基于该模板。

- 在应用程序`AddDocumentTemplate``InitInstance`的代码中添加调用。

   Visual C++为创建的每个新窗体添加此代码，当用户选择 **"新建"** 命令时，该窗体将表单添加到可用窗体列表中。 此代码包括窗体的关联资源 ID 以及组成新窗体对象的关联文档、视图和框架类的名称。

   文档模板用作文档、框架窗口和视图之间的连接。 对于单个文档，您可以创建许多模板。

有关详细信息，请参阅：

- [创建基于表单的应用程序](../mfc/reference/creating-a-forms-based-mfc-application.md)

- [将窗体插入项目](../mfc/inserting-a-form-into-a-project.md)

## <a name="see-also"></a>另请参阅

[用户界面元素](../mfc/user-interface-elements-mfc.md)
