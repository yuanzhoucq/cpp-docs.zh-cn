---
title: 使用类编写 Windows 应用程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows applications [MFC], MFC application framework
- MFC, application development
- applications [OLE], MFC application framework
- MFC ActiveX controls [MFC], creating
- OLE applications [MFC], MFC application framework
- database applications [MFC], creating
ms.assetid: 73f63470-857d-43dd-9a54-b38b7be0f1b7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa126f2772e1672a1484453fdffdd487b6c45959
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-classes-to-write-applications-for-windows"></a>使用类编写 Windows 应用程序
综上所述，Microsoft 基础类 (MFC) 库中的类，构成的"应用程序框架，"在其生成用于 Windows 操作系统的应用程序。 在非常一般的级别，框架的应用程序定义框架，并提供可以放置到该主干上的标准用户界面实现。 你的作业作为程序员是主干的填写其余中，这是主干的这些特定于你的应用程序的内容。 可以通过使用 MFC 应用程序向导创建非常全面初学者应用程序的文件中获取一个良好的开端。 使用 Microsoft Visual c + + 资源编辑器直观地设计用户界面元素类视图命令连接到代码中和类库的这些元素来实现你的应用程序特定逻辑。  
  
 3.0 版及更高版本的 MFC 框架版本支持 Win32 平台，包括 Microsoft Windows 95 和更高版本的编程和 Windows NT 版本 3.51 及更高版本。 MFC Win32 支持包括多线程处理。 使用版本 1.5*x*如果你需要执行 16 位编程。  
  
 本系列文章显示应用程序框架的全面概述。 它还探讨了构成你的应用程序和创建它们的方式的主要对象。 这些文章中涉及的主题如下所示：  
  
-   [框架](../mfc/framework-mfc.md)。  
  
-   框架和你中所述的代码之间的工作划分[基于框架生成](../mfc/building-on-the-framework.md)。  
  
-   [应用程序类](../mfc/cwinapp-the-application-class.md)，其中封装应用程序级功能。  
  
-   如何[文档模板](../mfc/document-templates-and-the-document-view-creation-process.md)创建和管理文档和与其关联的视图和框架窗口。  
  
-   类[CWnd](../mfc/window-objects.md)，所有窗口的根基本类。  
  
-   [图形对象](../mfc/graphic-objects.md)，如钢笔和画笔。  
  
 框架的其他部分包括：  
  
-   [窗口对象： 概述](../mfc/window-objects.md)  
  
-   [消息处理和映射](../mfc/message-handling-and-mapping.md)  
  
-   [CObject，MFC 中的根基类](../mfc/using-cobject.md)  
  
-   [文档/视图体系结构](../mfc/document-view-architecture.md)  
  
-   [对话框](../mfc/dialog-boxes.md)  
  
-   [控件](../mfc/controls-mfc.md)  
  
-   [控件条](../mfc/control-bars.md)  
  
-   [OLE](../mfc/ole-in-mfc.md)  
  
-   [内存管理](../mfc/memory-management.md)  
  
     除了为你提供在编写为 Windows 操作系统的应用程序的一个优点，MFC 还使它可以更轻松地编写的应用程序专门使用 OLE 链接和嵌入技术。 你会导致你的应用程序 OLE 可视编辑容器、 OLE 可视编辑服务器，或二者，并且你可以添加自动化，以便其他应用程序可以使用从应用程序的对象或甚至远程驱动器。  
  
-   [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)  
  
     与框架现在完全集成的 OLE 控件开发工具包 (CDK)。 本文章系列提供使用 MFC 的 ActiveX 控件开发的概述。 （ActiveX 控件已以前称为 OLE 控件。）  
  
-   [数据库编程](../data/data-access-programming-mfc-atl.md)  
  
     MFC 还提供了两个集的数据库类，用于简化编写数据访问应用程序。 使用 ODBC 数据库类，你可以连接到数据库通过开放式数据库连接 (ODBC) 驱动程序、 从表中，选择记录并显示中的记录信息联机窗体。 使用数据访问对象 (DAO) 类，你可以使用数据库通过 Microsoft Jet 数据库引擎或外部 (非 Jet) 数据源，包括 ODBC 数据源。  
  
     此外，MFC 完全启用编写的应用程序使用 Unicode 和多字节字符集 (MBCS)，具体而言双字节字符集 (DBCS)。  
  
 有关 MFC 文档的常规指南，请参阅[常规 MFC 主题](../mfc/general-mfc-topics.md)。  
  
## <a name="see-also"></a>请参阅  
 [常规 MFC 主题](../mfc/general-mfc-topics.md)

