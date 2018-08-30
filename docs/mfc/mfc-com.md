---
title: MFC COM |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MFC COM (MFC)
dev_langs:
- C++
helpviewer_keywords:
- MFC, COM support
- MFC ActiveX controls [MFC], COM support in MFC
- MFC COM [MFC]
- ActiveX controls [MFC], COM object model
- Active technology [MFC]
- COM [MFC], MFC support
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3e8c3af361e1ffb5928132727fa124f03a99e81e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205644"
---
# <a name="mfc-com"></a>MFC COM
MFC 的子集旨在支持 COM，而大多数活动模板库 (ATL) 设计用于 COM 编程。 本部分的主题介绍了 MFC 的支持的 com。  
  
 Active 技术 （如 ActiveX 控件、 活动文档包容、 OLE 和等等） 使用组件对象模型 (COM) 来启用软件组件进行交互与另一个在联网环境中，无论它们是一样的语言创建。 Active 技术可以用于创建在桌面或 Internet 运行的应用程序。 有关详细信息请参阅[COM 简介](../atl/introduction-to-com.md)或[组件对象模型](/windows/desktop/com/the-component-object-model)。  
  
 Active 技术包括客户端和服务器技术，包括以下：  
  
-   [活动文档包容](../mfc/active-document-containment.md)、 MFC 版本 4.2 中支持和更高版本，使用户可以查看[活动文档](../mfc/active-documents.md)（如 Microsoft Excel 或 Word 文件） 和激活的文档的本机的整个接口应用程序中的整个工作区[活动文档容器](../mfc/active-document-containers.md)如 Microsoft Office Binder 或 Microsoft Internet Explorer。 容器充当客户端，而通过提供文档[活动文档服务器](../mfc/active-document-servers.md)。 Internet 应用程序中使用活动文档的详细信息，请参阅： [Internet 上的活动文档](../mfc/active-documents-on-the-internet.md)。  
  
-   ActiveX 控件是交互式可以等 Web 站点容器中使用的对象。 ActiveX 控件的详细信息，请参阅：  
  
    -   [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)  
  
    -   [Internet 上的 ActiveX 控件](../mfc/activex-controls-on-the-internet.md)  
  
    -   [概述： Internet](../mfc/mfc-internet-programming-basics.md)  
  
    -   [升级现有 ActiveX 控件来在 Internet 上使用](../mfc/upgrading-an-existing-activex-control.md)  
  
    -   [调试 ActiveX 控件](/visualstudio/debugger/how-to-debug-an-activex-control)  
  
-   活动脚本控制的一个或多个 ActiveX 控件从浏览器或服务器集成的行为。 活动脚本的详细信息，请参阅[Internet 上的 Active 技术](../mfc/active-technology-on-the-internet.md)。  
  
-   [自动化](../mfc/automation.md)（以前称为 OLE 自动化） 使一个应用程序能够操作在另一个应用程序中实现的对象，或"公开"对象以便操作它们。  
  
     自动化的对象可能是本地或远程 （在另一台计算机可访问的网络）。 自动化可用于 OLE 和 COM 对象。  
  
-   本部分还介绍如何编写使用 MFC，例如，在 COM 组件[连接点](../mfc/connection-points.md)。  
  
 什么仍然会调用 OLE 与现在称为 active 技术的讨论，请参阅主题上[OLE](../mfc/ole-in-mfc.md)。  
  
 此外，请参阅知识库文章 Q248019： 如何： 防止服务器忙对话框框中使其不显示期间耗时较长 COM 操作。  
  
## <a name="in-this-section"></a>本节内容  
 [活动文档包容](../mfc/active-document-containment.md)  
  
 [自动化](../mfc/automation.md)  
  
 [连接点](../mfc/connection-points.md)  
  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)  
  
## <a name="see-also"></a>请参阅  
 [概念](../mfc/mfc-concepts.md)

