---
title: 窗体视图 (MFC) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user interfaces [MFC], forms
- forms [MFC]
- applications [MFC], forms-based
- forms-based applications [MFC]
- forms [MFC], adding to applications
ms.assetid: efbe73c1-4ca4-4613-aac2-30d916e92c0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 87775c8afa1fa6eec8fbbdbbaa11bc9b5e6f1faa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349038"
---
# <a name="form-views-mfc"></a>窗体视图 (MFC)
你可以将窗体添加到任何 Visual c + + 应用程序支持的 MFC 库，包括[基于窗体的应用程序](../mfc/reference/creating-a-forms-based-mfc-application.md)(一个其视图类派生自`CFormView`)。 如果你未最初创建你的应用程序以支持窗体，Visual c + + 将时插入一个新的窗体添加这种对你支持。 在 SDI 或 MDI 应用程序，它实现默认[文档/视图体系结构](../mfc/document-view-architecture.md)，当用户选择`New`命令 (默认情况下上,**文件**菜单)，Visual c + + 会提示用户从可用的窗体中选择。  
  
 SDI 应用程序后，当用户选择`New`命令时，窗体的当前实例继续运行，但如果找不到创建具有所选表单的应用程序的新实例。 在 MDI 应用程序，该窗体的当前实例继续运行时用户选择`New`命令。  
  
> [!NOTE]
>  您可以在基于对话框的应用程序中插入窗体 (基于其对话框类的一个`CDialog`，另一个类实现的任何视图中)。 但是，没有文档/视图体系结构，Visual c + + 不自动实现**文件**&#124;**新建**功能。 你必须创建一个要查看其他窗体，例如通过实现具有各种属性页的选项卡式的对话框的用户的方式。  
  
 当你的应用程序中插入一个新窗体时，Visual c + + 实现以下功能：  
  
-   创建基于你选择的窗体样式类之一的类 (`CFormView`， `CRecordView`， `CDaoRecordView`，或`CDialog`)。  
  
-   创建对话框资源具有适当的样式 （或者可以使用尚未与类相关联的现有对话框资源）。  
  
     如果你选择现有的对话框资源，你可能需要通过在对话框中使用属性页中设置这些样式。 必须包括有关对话框中的样式：  
  
     **WS_CHILD**= On  
  
     `WS_BORDER`= 关闭  
  
     **WS_VISIBLE**= 关闭  
  
     **WS_CAPTION =** 关闭  
  
 为应用程序基于文档/视图体系结构，**新窗体**命令 （右键单击类视图中） 还：  
  
-   创建**CDocument**-基于类  
  
     而不是让创建的新类，你可以使用任何现有**CDocument**-基于你的项目中的类。  
  
-   生成的文档模板 (派生自**CDocument**) 与字符串、 菜单和图标资源。  
  
     你还可以创建基于模板的新类。  
  
-   添加对的调用**AddDocumentTemplate**应用程序中`InitInstance`代码。  
  
     Visual c + + 将为每个新窗体创建，这将窗体添加到可用的窗体的列表，当用户选择此代码添加`New`命令。 此代码包括窗体的关联的资源 ID 和关联的文档、 视图和框架类共同构成新的窗体对象的名称。  
  
     文档模板用作文档、 框架窗口和视图之间的连接。 单个文档，你可以创建多个模板。  
  
 有关详细信息，请参见:  
  
-   [创建基于窗体的应用程序](../mfc/reference/creating-a-forms-based-mfc-application.md)  
  
-   [在项目中插入窗体](../mfc/inserting-a-form-into-a-project.md)  
  
## <a name="see-also"></a>请参阅  
 [用户界面元素](../mfc/user-interface-elements-mfc.md)
