---
title: "MFC COM | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MFC COM (MFC)"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Active 技术 [C++]"
  - "ActiveX 控件 [C++], COM 对象模型"
  - "COM [C++], MFC 支持"
  - "MFC [C++], COM 支持"
  - "MFC ActiveX 控件 [C++], MFC 中的 COM 支持"
  - "MFC COM [C++]"
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# MFC COM
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 的子集，旨在支持 COM，而大多数活动模板库 \(ATL\) 用于 COM 编程。  此节的主题介绍 MFC 的 COM 支持。  
  
 Active 技术 \(如 ActiveX 控件包容，OLE、活动文档，等等\) 在网络环境使用组件对象模型\(COM\) 使软件组件交互，无论创建的语言。  Active 技术来创建桌面上或 Internet 运行的应用程序。  有关更多信息请参见 [COM 引入](../atl/introduction-to-com.md) 或 [组件对象模型 \(COM\)](http://msdn.microsoft.com/library/windows/desktop/ms694363)。  
  
 Active 技术包括客户端和服务器技术，包括：  
  
-   [包容活动文档](../mfc/active-document-containment.md)支持，在 MFC 4.2 版及更高，用户可以查看 [活动文档](../mfc/active-documents.md) \(如 Microsoft Excel 或 Word 文件\) 和激活文档的本机应用程序的全部接口。[活动文档容器](../mfc/active-document-containers.md) 的整个工作区 \(如 Microsoft Office 活页夹或 Microsoft Internet Explorer）。  容器作为客户端，而文档是由[活动文档服务器](../mfc/active-document-servers.md)提供。  有关在Internet 应用程序使用活动文档中的更多信息，请参见：[Internet 上的活动文档](../mfc/active-documents-on-the-internet.md)。  
  
-   ActiveX 控件是可以使用容器 \(如网站）的交互的对象。  有关ActiveX控件更多信息，请参见：  
  
    -   [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)  
  
    -   [Internet 上的 ActiveX 控件](../mfc/activex-controls-on-the-internet.md)  
  
    -   [概述：Internet](../mfc/mfc-internet-programming-basics.md)  
  
    -   [升级在 Internet 使用的现有的 ActiveX 控件](../mfc/upgrading-an-existing-activex-control.md)  
  
    -   [调试 ActiveX 控件](../Topic/How%20to:%20Debug%20an%20ActiveX%20Control.md)  
  
-   活动脚本控制一个或多个 ActiveX 控件行为从浏览器或服务器集成。  有关活动脚本的更多信息，请参见 [在 Internet 上可用技术](../mfc/active-technology-on-the-internet.md)。  
  
-   [自动化](../mfc/automation.md) \(原来称作为 OLE 自动化\) 使该应用程序来操作应用程序中实施的对象，或者"公开"对象，所以它们可以进行操作。  
  
     自动化的对象可能是本地或 [远程的](../mfc/remote-automation.md) \(在其他计算机访问网络\)。  自动化对 OLE 和 COM 对象可用。  
  
-   本节还提供有关如何在MFC中编写 COM 组件，例如， [连接点](../mfc/connection-points.md)，。  
  
 有关不同的内容讨论仍调用 OLE 与什么现在调用活动方法，请参见 [OLE](../mfc/ole-in-mfc.md)的主题。  
  
 并且，请参见知识库文章 Q248019:如何：预防对话框显示在较长操作 COM 服务器正忙。  
  
## 本节内容  
 [活动文档包容](../mfc/active-document-containment.md)  
  
 [自动化](../mfc/automation.md)  
  
 [远程自动化](../mfc/remote-automation.md)  
  
 [连接点](../mfc/connection-points.md)  
  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)  
  
## 请参阅  
 [概念](../mfc/mfc-concepts.md)