---
title: "远程自动化的适用条件 | Microsoft Docs"
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
  - "远程自动化, DCOM"
ms.assetid: 4c4c8176-cfc0-44f7-bc87-b690f069ad2f
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 远程自动化的适用条件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

DCOM 在 1996 年发布并且仅用于 32 位和 64 位平台。  Microsoft Visual Basic 团队始终了解了 Visual Basic 使用自动化允许其组件通信。  缺少分布式版本严重限制了这些功能在企业环境中的使用，因此，该团队开发的 Visual Basic 4.0 Enterprise Edition 决定调查其自己的一系列的针对 OLE 和 COM 的自动化部件创建的远程处理组件。  显然，一主要目标是确保结果兼容并且当可用时，可以由 DCOM 替换。  它们并继续实现 16 位和 32 位 Windows 平台的远程自动化 \(RA\)。  
  
 远程自动化不依赖于任何特定语言，但是，直到 Visual C\+\+ 4.2 Enterprise Edition 版本发布，仅迁移 Visual Basic 4.0。  意识到远程自动化由 DCOM 整个包含。  如果您有机会在应用程序中使用 DCOM 而不是远程的自动化，您应执行此操作。  但是，有一些场景更适合远程自动化：  
  
-   客户端为16 位。  
  
-   如果您的组织还没有铺开 Windows NT 或 Windows 95 的 DCOM 适用版本。  
  
-   如果使用以使用 C\+\+ 组件替代一个或多个 Visual Basic 组件的远程自动化升级现有应用程序套件。  
  
 使用远程自动化创建程序与使用 DCOM 自动化创建程序之间的没有差异，并且配置工具包能够非常简单操作远程自动化和 DCOM 之间的切换。  因而，基础结构配置好后，就地升级将应用程序从远程自动化升级到 DCOM 并不困难。  
  
## 请参阅  
 [远程自动化提供什么？](../mfc/what-does-remote-automation-provide-q.md)   
 [DCOM 历史记录](../mfc/history-of-dcom.md)