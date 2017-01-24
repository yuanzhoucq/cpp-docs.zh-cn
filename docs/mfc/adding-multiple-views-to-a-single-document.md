---
title: "向单个文档添加多个视图 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "文档, 多个视图"
  - "多个视图, SDI 应用程序"
  - "单文档界面 (SDI), 添加视图"
  - "视图, SDI 应用程序"
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 向单个文档添加多个视图
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在单文档界面 \(MDI\) \(SDI\) 应用程序创建与 Microsoft 基础类 \(MFC\) \(MFC\) 库，每个文档类型与一个视图类型。  在某些情况下，可以切换一文档的当前的视图与新视图的是必需的。  
  
> [!TIP]
>  有关实现多视图的其他过程单个文件，请参见 [CDocument::AddView](../Topic/CDocument::AddView.md) [收集](../top/visual-cpp-samples.md) 和 MFC 示例。  
  
 可以通过添加新的 `CView`实现此功能 \(类派生和辅助代码动态切换的视图对现有 MFC 应用程序。  
  
 步骤如下所示：  
  
-   [修改现有应用程序类](#vcconmodifyexistingapplicationa1)  
  
-   [创建和修改新的视图类](#vcconnewviewclassa2)  
  
-   [创建并将新视图](#vcconattachnewviewa3)  
  
-   [实现转换函数。](#vcconswitchingfunctiona4)  
  
-   [添加切换支持的视图](#vcconswitchingtheviewa5)  
  
 本主题的其余部分假定以下操作：  
  
-   `CWinApp`的名称派生的对象是 `CMyWinApp`，因此，在 `CMyWinApp` MYWINAPP.H 和 MYWINAPP.CPP 声明和定义。  
  
-   `CNewView` 是新的 `CView`的名称派生对象和 `CNewView` 在 NEWVIEW.H 和 NEWVIEW.CPP 声明和定义。  
  
##  <a name="vcconmodifyexistingapplicationa1"></a> 修改现有应用程序类  
 对于应用程序切换视图，需要通过添加成员变量存储视图和方法应用程序切换类修改它们。  
  
 在 `CMyWinApp` 的声明后，将下面的代码添加到类：  
  
 [!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/CPP/adding-multiple-views-to-a-single-document_1.h)]  
  
 新成员变量、`m_pOldView` 和 `m_pNewView`\)，指向当前的视图和新创建一个。  新的方法 \(`SwitchView`\) 切换视图，则需要用户。  方法的主体位于 [实现 Transform 功能](#vcconswitchingfunctiona4)中添加本主题后面讨论。  
  
 对类应用程序的最后修改要求包括定义了转换功能。的窗口消息的新头文件 \(**WM\_INITIALUPDATE**\)  
  
 插入到 MYWINAPP.CPP 的包含节的代码行：  
  
 [!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/CPP/adding-multiple-views-to-a-single-document_2.cpp)]  
  
 保存更改并继续下一步。  
  
##  <a name="vcconnewviewclassa2"></a> 创建和修改新的视图类  
 创建新视图类从类视图可以轻松使用 **新类** 提供的命令。  此类的唯一要求是从 `CView`派生。  将此新类添加到应用程序中。  关于添加新类的具体信息。项目，请参见 [添加类](../ide/adding-a-class-visual-cpp.md)。  
  
 一旦添加到项目了类，您需要更改某些视图类成员的可访问性。  
  
 通过将从 `protected` 中访问说明符 NEWVIEW.H 修改语句构造函数和析构函数的 **public**。  在可见之前，类允许动态创建和销毁这和修改视图的外观。  
  
 保存更改并继续下一步。  
  
##  <a name="vcconattachnewviewa3"></a> 创建并将新视图  
 若要创建和附加新的视图，需要修改应用程序类的 `InitInstance` 函数。  修改添加创建新的视图对象并初始化 `m_pOldView` 和 `m_pNewView` 使用两个现有视图对象的新代码。  
  
 由于的新视图在 `InitInstance` 函数中，创建新的，并将现有视图对于应用程序生存期仍存在。  但是，应用程序可以有更简单动态创建新的视图。  
  
 调用后插入此代码为 `ProcessShellCommand`:  
  
 [!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/CPP/adding-multiple-views-to-a-single-document_3.cpp)]  
  
 保存更改并继续下一步。  
  
##  <a name="vcconswitchingfunctiona4"></a> 实现转换函数。  
 在上述步骤中，您将添加用于创建和初始化新的视图对象的代码。  最后一个主要部分是交换执行方法，`SwitchView`。  
  
 在应用程序类 \(\) MYWINAPP.CPP 实现文件的末尾，添加以下方法定义：  
  
 [!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/CPP/adding-multiple-views-to-a-single-document_4.cpp)]  
  
 保存更改并继续下一步。  
  
##  <a name="vcconswitchingtheviewa5"></a> 添加切换支持的视图  
 最后一步是添加调用 `SwitchView` 方法的代码，则应用程序需要切换视图时。  这可以用几种方法：通过内部添加用户的新菜单项可以选中或切换视图，在某些条件。  
  
 有关添加新菜单项和命令处理程序函数的更多信息，请参见 [命令和控件提供的通知的处理程序](../mfc/handlers-for-commands-and-control-notifications.md)。  
  
## 请参阅  
 [文档\/视图体系结构](../mfc/document-view-architecture.md)