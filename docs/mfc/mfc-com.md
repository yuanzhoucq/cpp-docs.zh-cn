---
title: "MFC COM |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MFC COM (MFC)
dev_langs: C++
helpviewer_keywords:
- MFC, COM support
- MFC ActiveX controls [MFC], COM support in MFC
- MFC COM [MFC]
- ActiveX controls [MFC], COM object model
- Active technology [MFC]
- COM [MFC], MFC support
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 827bef034eeb7fc46b397c50f5ddf0c4cb6e48fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-com"></a>MFC COM
MFC 的子集旨在为支持 COM，虽然大多数的活动模板库 (ATL) 专为 COM 编程。 此部分的主题介绍 MFC 的支持的 com。  
  
 Active 技术 （如 ActiveX 控件、 活动文档包容、 OLE 和等等） 使用组件对象模型 (COM) 启用软件组件进行交互与另一个在网络环境中，无论它们是一样的语言创建。 Active 技术可以用于创建在桌面或 Internet 运行的应用程序。 有关详细信息请参阅[简介 COM](../atl/introduction-to-com.md)或[组件对象模型](http://msdn.microsoft.com/library/windows/desktop/ms694363)。  
  
 Active 技术包括客户端和服务器技术，包括以下：  
  
-   [活动文档包容](../mfc/active-document-containment.md)、 支持的 MFC 版本 4.2 和更高版本，允许用户查看[活动文档](../mfc/active-documents.md)（例如 Microsoft Excel 或 Word 文件） 并激活该文档的本机整个接口应用程序中的整个工作区[活动文档容器](../mfc/active-document-containers.md)如 Microsoft Office Binder 或 Microsoft Internet Explorer。 容器充当客户端，而文档由[活动文档服务器](../mfc/active-document-servers.md)。 Internet 应用程序中使用活动文档的详细信息，请参阅： [Internet 上的活动文档](../mfc/active-documents-on-the-internet.md)。  
  
-   ActiveX 控件是可在网站等容器的交互式对象。 ActiveX 控件的详细信息，请参阅：  
  
    -   [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)  
  
    -   [Internet 上的 ActiveX 控件](../mfc/activex-controls-on-the-internet.md)  
  
    -   [概述： Internet](../mfc/mfc-internet-programming-basics.md)  
  
    -   [升级现有 ActiveX 控件在 Internet 上使用](../mfc/upgrading-an-existing-activex-control.md)  
  
    -   [调试 ActiveX 控件](/visualstudio/debugger/how-to-debug-an-activex-control)  
  
-   活动脚本控制集成从浏览器或服务器的一个或多个 ActiveX 控件的行为。 活动脚本的详细信息，请参阅[Internet 上的 Active 技术](../mfc/active-technology-on-the-internet.md)。  
  
-   [自动化](../mfc/automation.md)（以前称为 OLE 自动化） 使一个应用程序能够操作在另一个应用程序中实现的对象，或"公开"对象以便它们能够被操作。  
  
     自动的对象可能是本地或[远程](../mfc/remote-automation.md)（在另一个计算机可访问在网络上）。 自动化可用于 OLE 和 COM 对象。  
  
-   本部分还提供有关如何编写使用 MFC，例如中的 COM 组件的信息[连接点](../mfc/connection-points.md)。  
  
 仍所谓 OLE 与什么现在称为 active 技术的讨论，请参阅主题上[OLE](../mfc/ole-in-mfc.md)。  
  
 此外，请参阅知识库文章 Q248019： 如何： 防止服务器忙对话框框中从显示期间长 COM 的操作。  
  
## <a name="in-this-section"></a>本节内容  
 [活动文档包容](../mfc/active-document-containment.md)  
  
 [自动化](../mfc/automation.md)  
  
 [远程自动化](../mfc/remote-automation.md)  
  
 [连接点](../mfc/connection-points.md)  
  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)  
  
## <a name="see-also"></a>请参阅  
 [概念](../mfc/mfc-concepts.md)

