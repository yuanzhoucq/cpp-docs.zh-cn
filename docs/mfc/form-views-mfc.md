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
ms.openlocfilehash: f93f65e949c18ddb1ad5dba859ba8c4832abac8f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289268"
---
# <a name="form-views-mfc"></a>窗体视图 (MFC)

您可以向支持 MFC 库，包括任何 Visual c + + 应用程序添加窗体[基于窗体的应用程序](../mfc/reference/creating-a-forms-based-mfc-application.md)(一个其视图类派生自`CFormView`)。 如果未最初创建应用程序以支持窗体，Visual c + + 将插入一个新的窗体时添加该支持。 在 SDI 或 MDI 应用程序，它可实现默认[文档/视图体系结构](../mfc/document-view-architecture.md)，当用户选择**新建**命令 (默认情况下，在**文件**菜单)，VisualC + + 会提示用户从可用的窗体中进行选择。

与 SDI 应用程序，当用户选择**新建**命令时，窗体的当前实例将继续运行，但如果找不到创建与所选的窗体应用程序的新实例。 在 MDI 应用程序，在窗体的当前实例继续运行时用户选择**新建**命令。

> [!NOTE]
>  你可以在基于对话框的应用程序中插入窗体 (基于其对话框类的一个`CDialog`，另一个类实现的任何视图中)。 但是，没有文档/视图体系结构，Visual c + + 不会自动实现**文件**&#124;**新建**功能。 必须创建用户可以查看附加的窗体，例如通过实现一个具有各种属性页的选项卡式的对话框一种方法。

当你的应用程序中插入一个新窗体时，Visual c + + 执行以下任务：

- 创建基于你选择的窗体样式类之一的类 (`CFormView`， `CRecordView`， `CDaoRecordView`，或`CDialog`)。

- 创建对话框资源具有适当的样式 （或可以使用尚未与类相关联的现有对话框资源）。

   如果选择现有的对话框资源，可能需要将这些样式设置为对话框的使用属性页。 必须包括一个对话框中的样式：

     **WS_CHILD**=On

     **WS_BORDER**=Off

     **WS_VISIBLE**=Off

     **WS_CAPTION**=Off

对于基于文档/视图体系结构，应用程序**新的窗体**命令 （右键单击类视图中） 还：

- 创建`CDocument`-基于类

   而不是创建一个新类，可以使用任何现有`CDocument`-基于你的项目中的类。

- 生成的文档模板 (派生自`CDocument`) 的字符串、 菜单和图标资源。

   此外可以创建基于模板的新类。

- 添加到调用`AddDocumentTemplate`在应用程序的`InitInstance`代码。

   Visual c + + 将添加这段代码用于每个新窗体创建，这将在窗体添加到可用的窗体的列表，当用户选择**新建**命令。 此代码包括窗体的关联的资源 ID 和关联的文档、 视图和框架类一起构成新的窗体对象的名称。

   文档模板用作文档、 框架窗口和视图之间的连接。 单个文档，可以创建多个模板。

有关详细信息，请参见:

- [创建基于窗体的应用程序](../mfc/reference/creating-a-forms-based-mfc-application.md)

- [在项目中插入窗体](../mfc/inserting-a-form-into-a-project.md)

## <a name="see-also"></a>请参阅

[用户界面元素](../mfc/user-interface-elements-mfc.md)
