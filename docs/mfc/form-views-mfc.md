---
title: "窗体视图 (MFC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序 [MFC], 基于窗体"
  - "窗体 [C++]"
  - "窗体 [C++], 添加到应用程序"
  - "基于窗体的应用程序"
  - "用户界面, 窗体"
ms.assetid: efbe73c1-4ca4-4613-aac2-30d916e92c0e
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 窗体视图 (MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以将该窗体添加到支持 MFC 库的任何 Visual C\+\+ 应用程序，包括 [基于窗体的应用程序](../mfc/reference/creating-a-forms-based-mfc-application.md) \(视图类从 `CFormView`派生\) 中。  如果您最初创建时不应用程序窗体支持，Visual C\+\+ 会将的这种支持，在插入新窗体。  在 SDI 或 MDI 应用程序，实现默认，[文档\/视图结构](../mfc/document-view-architecture.md)，当用户选择 `New` 命令 \(默认情况下，在 **文件** 菜单\)，Visual C\+\+ 会提示用户从可用选择窗体。  
  
 SDI 应用程序，那么，当用户选择 `New` 命令时，窗体的当前实例继续运行，但应用程序的新实例。选择窗体的创建，如果一种没有找到。  在 MDI 应用程序，那么，当用户选择 `New` 命令时，窗体的当前实例继续运行。  
  
> [!NOTE]
>  可以插入窗体到基于对话框的应用程序 \(对话框类视图基于 `CDialog` 类未实现\) 的一。  但是，不带文档\/视图结构，Visual C\+\+ 不自动实现 **文件** &#124;**新建** 功能。  您必须为用户创建一种显示附加的窗体，如通过实现带有各属性页的选项卡式对话框。  
  
 在插入新窗体到应用程序时，Visual C\+\+ 将执行下列操作：  
  
-   创建根据您选择的一个样式类窗体类 \(`CFormView`、`CRecordView`、`CDaoRecordView`或 `CDialog`\)。  
  
-   创建具有适当的样式 \(或您的对话框资源可以使用没有与类\) 的现有对话框资源。  
  
     如果选择一个现有对话框资源，通过使用的属性页对话框，您可能需要设置这些样式。  对话框的样式必须包括：  
  
     **WS\_CHILD**\=On  
  
     `WS_BORDER`\=Off  
  
     **WS\_VISIBLE**\=Off  
  
     **WS\_CAPTION\=**  
  
 对于基于文档\/视图体系结构还的应用程序，则 **New Form** 命令 \(右击类视图中\):  
  
-   创建 **CDocument**\- 基类  
  
     除了使新的类，创建可以将现有的任意 **CDocument**\- 项目中的基类。  
  
-   生成文档模板 \(从 **CDocument**派生\)。字符串、菜单和图标资源。  
  
     还可以创建基于模板的新类。  
  
-   调用添加到应用程序中的 `InitInstance` 代码的 **AddDocumentTemplate**。  
  
     Visual C\+\+ 将所创建，将该窗体添加到提供窗体列表的每个新窗体中提供此代码，当用户选择 `New` 命令时。  此代码包括在一起构成新窗体对象关联文档、视图和帧类的窗体关联的资源 ID 和名称。  
  
     文档模板用作文档之间的连接，框架窗口和视图。  对于单个文件，可以创建许多模板。  
  
 有关详细信息，请参阅：  
  
-   [创建基于窗体的应用程序](../mfc/reference/creating-a-forms-based-mfc-application.md)  
  
-   [将一个窗体添加到项目中](../mfc/inserting-a-form-into-a-project.md)  
  
## 请参阅  
 [用户界面元素](../mfc/user-interface-elements-mfc.md)