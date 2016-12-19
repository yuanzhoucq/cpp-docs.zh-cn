---
title: "服务器 | Microsoft Docs"
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
  - "完全服务器"
  - "袖珍服务器"
  - "OLE 服务器应用程序"
  - "OLE 服务器应用程序, 激活"
  - "OLE 服务器应用程序, 服务器类型"
  - "服务器应用程序"
  - "服务器"
ms.assetid: e45172e8-eae3-400a-8139-0fa009a42fdc
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 服务器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

服务器应用程序 \(或组件\) 创建 OLE 项应用程序 \(或组件\) 给容器应用程序。  可视化编辑服务器应用还支持可视编辑或就地激活。  OLE 服务器另一个窗体是 [自动化服务器](../mfc/automation-servers.md)。  一些服务器应用支持嵌入项的仅创建；其他支持嵌入的资源和链接项的创建。  某些支持仅链接，但这很少见。  当用户想要编辑项时，所有服务器必须由应用容器应用程序支持激活。  应用程序可以是容器和服务器。  换句话说，它能将数据放入其文档中，并创建可将作为项到其他应用程序中的文档中的数据。  
  
 miniserver 可以只由容器中启动服务器应用程序的一个特定类型。  Microsoft Draw 和 Microsoft 的是 miniservers 的示例。  不 miniserver 文档作为存储在磁盘上的文件。  相反，它会读取其文档自并编写自己为容器属于文档的项。  因此，miniserver 只支持嵌入，而链接。  
  
 完整服务器中运行作为独立的应用程序或由容器应用程序开始。  完整服务器可以存储文档用作磁盘上的文件。  它可以只支持嵌入，并嵌入或链接仅链接。  容器应用程序的用户可以通过选择服务器中或复制和剪切命令在容器的粘贴命令创建嵌入的项。  的链接项通过在服务器上复制命令和容器中粘贴链接命令创建。  或者，使用插入对话框，用户可创建的链接的或嵌入项。  
  
 下表总结服务器不同类型的特性：  
  
### 服务器特性  
  
|服务器的类型|支持多个实例|每个文档项|文档的每个实例|  
|------------|------------|-----------|-------------|  
|Miniserver|是|1|1|  
|SDI 完整服务器|是|1 \(如果支持链接，1 个或多个\)|1|  
|MDI 完整服务器|非 \(不要求\)|1 \(如果支持链接，1 个或多个\)|0 或更多|  
  
 在超过容器将使用编辑嵌入式或链接的项情况下，服务器应用应同时支持多个容器。  如果服务器是 SDI 应用程序 \(或使用对话框接口的 miniserver\)，服务器的多个实例必须能够同时运行。  这允许应用程序一个单独的实例处理每个容器请求。  
  
 如果服务器是 MDI 应用程序，则可创建新的 MDI 子窗口时，容器需要编辑这些项。  这样，应用程序的单个实例用作支持多个容器。  
  
 服务器应用必须通知 OLE 系统 DLL，该怎么办如果服务器的一个实例已经在运行，在其他容器在请求其服务：是否应启动服务器的新实例或处理所有容器的服务器请求的实例。  
  
 有关更多详细信息在服务器，请参见：  
  
-   [服务器：实现服务器](../mfc/servers-implementing-a-server.md)  
  
-   [服务器：实现服务器文档。](../mfc/servers-implementing-server-documents.md)  
  
-   [服务器：实现就地框架窗口](../mfc/servers-implementing-in-place-frame-windows.md)  
  
-   [服务器：服务器项目](../mfc/servers-server-items.md)  
  
-   [服务器：用户界面问题](../mfc/servers-user-interface-issues.md)  
  
## 请参阅  
 [OLE](../mfc/ole-in-mfc.md)   
 [容器](../mfc/containers.md)   
 [容器：高级功能](../mfc/containers-advanced-features.md)   
 [菜单和资源 \(OLE\)](../mfc/menus-and-resources-ole.md)   
 [注册](../mfc/registration.md)   
 [自动化服务器](../mfc/automation-servers.md)