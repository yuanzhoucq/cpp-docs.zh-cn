---
title: 使用类编写 Windows 应用程序
ms.date: 11/04/2016
helpviewer_keywords:
- Windows applications [MFC], MFC application framework
- MFC, application development
- applications [OLE], MFC application framework
- MFC ActiveX controls [MFC], creating
- OLE applications [MFC], MFC application framework
- database applications [MFC], creating
ms.assetid: 73f63470-857d-43dd-9a54-b38b7be0f1b7
ms.openlocfilehash: c8b3d7061c0ef06063d9c6993f24d23fc2e1f92e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265296"
---
# <a name="using-the-classes-to-write-applications-for-windows"></a>使用类编写 Windows 应用程序

合起来看，Microsoft 基础类 (MFC) 库中的类构成了一个"应用程序框架，"基于其构建用于 Windows 操作系统的应用程序。 在一般的级别，框架定义的应用程序框架，并提供标准的用户界面实现可放置到框架上。 您作为程序员的工作是主干的填写其余中，这是主干的特定于你的应用程序的事情。 可以通过使用 MFC 应用程序向导创建非常细致初学者应用程序的文件中获取一个良好的开端。 使用 Microsoft Visual c + + 资源编辑器，以直观地设计用户界面元素类视图命令连接到代码中和类库的这些元素来实现特定于应用程序逻辑。

3.0 版及更高版本的 MFC 框架版本支持的 Win32 平台，包括 Microsoft Windows 95 和更高版本，编程和 Windows NT 版本 3.51 及更高版本。 MFC Win32 支持包括多线程处理。 使用版本 1.5*x*如果需要执行 16 位编程。

本系列文章提供了应用程序框架的宽泛概述。 它还介绍了组成应用程序和创建方式的主要对象。 在这些文章中涉及的主题如下所示：

- [Framework](../mfc/framework-mfc.md)。

- 框架和你的代码，如中所述之间的工作划分[基于框架生成](../mfc/building-on-the-framework.md)。

- [应用程序类](../mfc/cwinapp-the-application-class.md)，它封装应用程序级别的功能。

- 如何[文档模板](../mfc/document-templates-and-the-document-view-creation-process.md)创建和管理文档和其关联的视图和框架窗口。

- 类[CWnd](../mfc/window-objects.md)，根基类的所有窗口。

- [图形对象](../mfc/graphic-objects.md)，如钢笔和画笔。

框架的其他部分包括：

- [窗口对象：概述](../mfc/window-objects.md)

- [消息处理和映射](../mfc/message-handling-and-mapping.md)

- [CObject，MFC 中的根基类](../mfc/using-cobject.md)

- [文档/视图体系结构](../mfc/document-view-architecture.md)

- [对话框](../mfc/dialog-boxes.md)

- [控件](../mfc/controls-mfc.md)

- [控件条](../mfc/control-bars.md)

- [OLE](../mfc/ole-in-mfc.md)

- [内存管理](../mfc/memory-management.md)

   除了为您提供在编写应用程序的 Windows 操作系统的一个优点，MFC 还使得更容易编写专门使用 OLE 链接和嵌入技术的应用程序。 您可使你的应用程序 OLE 可视编辑容器、 OLE 可视编辑服务器，或两者，并可以添加自动化，以便其他应用程序可以使用你的应用程序中的对象或甚至远程驱动器。

- [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)

   OLE 控件开发工具包 (CDK) 现与框架完全集成。 本文章系列提供了使用 MFC ActiveX 控件开发的概述。 （ActiveX 控件是以前称为 OLE 控件。）

- [数据库编程](../data/data-access-programming-mfc-atl.md)

   MFC 还提供了两个集的数据库类，用于简化编写数据访问应用程序。 使用 ODBC 数据库类，您可以通过开放式数据库连接 (ODBC) 驱动程序连接到数据库、 从表中选择记录和记录中显示信息屏幕上窗体。 使用的数据访问对象 (DAO) 类，您可以使用数据库通过 Microsoft Jet 数据库引擎或外部 (非 Jet) 数据源，包括 ODBC 数据源。

   此外，MFC 完全启用了写入使用 Unicode 的应用程序和多字节字符集 (MBCS)，特别是双字节字符集 (DBCS)。

MFC 文档的常规指南，请参阅[常规 MFC 主题](../mfc/general-mfc-topics.md)。

## <a name="see-also"></a>请参阅

[常规 MFC 主题](../mfc/general-mfc-topics.md)
