---
title: "MFC 应用程序体系结构类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.mfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序体系结构类"
  - "类 [C++], MFC"
  - "MFC [C++], 应用程序开发"
  - "MFC [C++], 类"
ms.assetid: 71b2de54-b44d-407e-9c71-9baf954e18d9
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# MFC 应用程序体系结构类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此类别的类使框架应用程序的体系结构。  这些提供通用功能。大多数应用程序。  通过填写框架添加应用程序特定的功能。  通常，您通过派生新类从结构类，然后添加新成员或者重写现有成员函数执行。  
  
 [应用程序向导](../mfc/reference/mfc-application-wizard.md) 生成应用程序的多种类型，在不同的方式使用应用程序框架。  SDI \(单文档界面\) 和 MDI \(多文档界面\) 应用程序充分利用调用文档框架的部分\/视图结构。  其他类型的应用程序，比如基于对话框的应用程序，基于窗体的应用程序，并且，DLL，使用少量文档\/视图体系结构功能。  
  
 文档\/视图应用程序包含一个或多个组文档、视图和框架窗口。  文档模板对象将每文档\/视图\/框架集中的类。  
  
 尽管您在 MFC 应用程序不必使用文档\/视图结构，有很多好处这样做。  MFC OLE、容器和服务器支持基于文档\/视图结构，如打印和"打印预览"的支持。  
  
 所有 MFC 应用程序都至少有两个对象：从派生的应用程序 [CWinApp](../mfc/reference/cwinapp-class.md)对象和某类主窗口对象派生 \(间接\)，通常从 [CWnd](../mfc/reference/cwnd-class.md)。\(通常，主窗口从 [CFrameWnd](../mfc/reference/cframewnd-class.md)[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)[CDialog](../mfc/reference/cdialog-class.md)、或派生，后者从 `CWnd`派生。\)  
  
 使用文档\/视图结构的应用程序包含其他对象。  主要对象有：  
  
-   从类派生的应用程序 [CWinApp](../mfc/reference/cwinapp-class.md)对象相同，如上面所述。  
  
-   从类派生的一个或多个类文档对象。[CDocument](../mfc/reference/cdocument-class.md) 文档对象类负责在视图来操作数据的内部表示形式运行。  它们可能与数据文件。  
  
-   从类派生的一个或多个视图对象。[CView](../mfc/reference/cview-class.md) 每个视图是附加到文档并与框架窗口的窗口。  视图显示和操作文档类对象中包含的数据。  
  
 文档\/视图应用程序还包含框架窗口 \(派生自 [CFrameWnd](../mfc/reference/cframewnd-class.md)\) 和文档模板 \(从派生\)。[CDocTemplate](../mfc/reference/cdoctemplate-class.md)  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)