---
title: "OLE 后台：实现策略 | Microsoft Docs"
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
  - "应用程序 [OLE], 实现 OLE"
  - "OLE [C++], 开发策略"
  - "OLE 应用程序 [C++], 实现 OLE"
ms.assetid: 0875ddae-99df-488c-82c6-164074a81058
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# OLE 后台：实现策略
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根据您的应用程序，将的 OLE 支持四项可能的实现策略：  
  
-   编写新应用程序。  
  
     这种情况通常需要最小工作。  在运行" MFC 应用程序向导并选择高级功能或支持复合文档创建主干应用程序。  有关这些选项的信息以及使用系统执行什么，请参见的文章 [创建 MFC ActiveX EXE 程序](../mfc/reference/mfc-application-wizard.md)。  
  
-   将程序编写与不支持 OLE 的 Microsoft 基础类 \(MFC\) 库版本 2.0 或更高版本。  
  
     如前所述创建具有 MFC 应用程序向导的新应用程序，然后将其复制并插入来自新应用程序的代码到现有的应用程序。  对于服务器、容器或自动化应用程序中的工作。  在这个示例策略中看一个MFC[SCRIBBLE](../top/visual-cpp-samples.md)的例子。  
  
-   有一个实现 OLE 版本 1.0 支持的 Microsoft 基础类库程序。  
  
     对此转换策略参见 [MFC 技术说明 41](../mfc/tn041-mfc-ole1-migration-to-mfc-ole-2.md)。  
  
-   您有未编写使用 Microsoft 基础类 \(MFC\)，可以或不能已实现 OLE 支持的应用程序。  
  
     这种情况需要大部分工作。  一个方法是创建新应用程序，第一种策略，然后复制并粘贴现有的代码到该。  如果现有的代码在 C\# 中编写，则可能需要修改它，以便可以编译为 C\+\+ 代码。  如果 C\# 代码调用 Windows API，则不必更改其使用 Microsoft 基础类。  此方法可能需要程序的某种更改结构支持的版本使用文档\/视图体系结构高 2.0 和 Microsoft 基础类。  有关使用此结构的更多信息，请参见 [技术说明 25](../mfc/tn025-document-view-and-frame-creation.md)。  
  
 一旦确定的策略，则应阅读或文章 [容器](../mfc/containers.md) [服务器](../mfc/servers.md) \(取决于编写\) 应用程序或的类型检查示例程序和\/或。  MFC OLE 和示例 [OCLIENT](../top/visual-cpp-samples.md) [HIERSVR](../top/visual-cpp-samples.md) 显示如何实现容器和服务器的各个方面。  在整个这些情景中的各个点，将在这些示例中引用的某些函数，因为讨论，技术的示例。  
  
## 请参阅  
 [OLE 后台](../mfc/ole-background.md)   
 [容器：实现容器](../mfc/containers-implementing-a-container.md)   
 [服务器：实现服务器](../mfc/servers-implementing-a-server.md)   
 [MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)