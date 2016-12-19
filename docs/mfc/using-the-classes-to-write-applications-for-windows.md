---
title: "使用类编写 Windows 应用程序 | Microsoft Docs"
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
  - "应用程序 [OLE], MFC 应用程序框架"
  - "数据库应用程序 [C++], 创建"
  - "MFC [C++], 应用程序开发"
  - "MFC ActiveX 控件, 创建"
  - "OLE 应用程序 [C++], MFC 应用程序框架"
  - "Windows 应用程序 [C++], MFC 应用程序框架"
ms.assetid: 73f63470-857d-43dd-9a54-b38b7be0f1b7
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用类编写 Windows 应用程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

类在 Microsoft 基础类 \(MFC\) \(MFC\) 库组成“application framework“，在此基础上生成针对 Windows 操作系统的应用程序。  在一般级别中，框架定义应用程序的主干并提供可能放置到主干中标准用户接口实现。  作为程序员的工作是填写其余部分，这些是特定于应用程序的。  可以以使用 MFC 应用程序向导创建一个非常全面的起始应用程序的文件为开端。  使用 Microsoft Visual C\+\+ 资源编辑器设计用户界面元素可视化，类视图命令连接这些元素代码和实现特定于应用程序的逻辑的类库。  
  
 MFC 框架版本 3.0 和更高版本支持编程 Win32 平台，包括 Microsoft Windows 95 和更高版本以及 Windows NT 3.51 版和更高。  MFC Win32 支持包括多线程处理。  如果需要执行 16 位编程，请使用 1.5*x*。  
  
 此系列文章有应用程序框架的广泛概述。  它还展示了应用程序测试的主要对象，以及如何创建。  这些文章包含的主题包括以下内容：  
  
-   [The framework](../mfc/framework-mfc.md)  
  
-   额外的工作划分在框架代码的和之间，如 [生成在 Framework](../mfc/building-on-the-framework.md)所述。  
  
-   [应用程序类](../mfc/cwinapp-the-application-class.md)，封装应用程序级别的功能。  
  
-   [文档模板](../mfc/document-templates-and-the-document-view-creation-process.md) 如何创建并管理文档及其关联视图和框架窗口。  
  
-   类[CWnd](../mfc/window-objects.md)，是所有 Windows 根基类。  
  
-   [图形对象](../mfc/graphic-objects.md)，如钢笔和画笔。  
  
 包含其他框架的部分：  
  
-   [窗口对象：概述](../mfc/window-objects.md)  
  
-   [消息处理和映射](../mfc/message-handling-and-mapping.md)  
  
-   [在 MFC中，基类CObject](../mfc/using-cobject.md)  
  
-   [文档\/视图体系结构](../mfc/document-view-architecture.md)  
  
-   [对话框](../mfc/dialog-boxes.md)  
  
-   [控件](../mfc/controls-mfc.md)  
  
-   [控件条](../mfc/control-bars.md)  
  
-   [OLE](../mfc/ole-in-mfc.md)  
  
-   [内存管理](../mfc/memory-management.md)  
  
     除了可以在编写程序的优点之外针对 Windows 操作系统，MFC 还可以更容易编写专门使用 OLE 嵌入链接和技术的应用程序。  您可以令应用程序为一个 OLE 可视化编辑容器， OLE 的可视化编辑服务器，或两者。可以添加自动，以便在其他应用程序可以从使用应用程序的对象或者远程驱动它。  
  
-   [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)  
  
     OLE 控件开发工具包 \(SDK\) \(CDK\) 完全集成到现有框架。  本文系列提供对 MFC ActiveX 控件开发的概述。\(ActiveX 控件 原来称作 OLE 控件。\)  
  
-   [数据库编程](../data/data-access-programming-mfc-atl.md)  
  
     MFC 还提供两组数据访问应用程序简化输入的数据库  使用 ODBC 数据库类中，可通过开放式数据库连接 \(ODBC\) 驱动程序连接到数据库。从表中选择记录，并显示信息记录在屏幕上的表格上。  使用数据访问对象\(DAO\) 类，可以通过 Microsoft Jet 数据库引擎或外部 \(非 Jet\) 数据源，包括 ODBC 数据源处理数据库。  
  
     此外， MFC 完全支持使用 Unicode 和多字节字符集 \(MBCS\)编写的应用程序，尤其是双字节字符集\(DBCS\)。  
  
 有关指向 MFC 文档的一般性指导，请参见 [泛 MFC 主题](../mfc/general-mfc-topics.md)。  
  
## 请参阅  
 [常规 MFC 主题](../mfc/general-mfc-topics.md)