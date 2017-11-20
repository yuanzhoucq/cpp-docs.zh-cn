---
title: "远程自动化的适用条件 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Remote Automation, DCOM
ms.assetid: 4c4c8176-cfc0-44f7-bc87-b690f069ad2f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 101d34c9ed610cb375c0755e7698f45a1b16e935
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="where-does-remote-automation-fit-in"></a>远程自动化的适用条件
DCOM 在 1996 年发布，仅用于 32 位和 64 位平台。 Microsoft 的 Visual Basic 团队始终将 Visual Basic 视为使用自动化允许其组件通信。 缺少分布式版本严重限制了这些功能在企业环境中的使用，因此，开发 Visual Basic 4.0 Enterprise Edition 的团队决定调查自己的针对 OLE 和 COM 的自动化部件的一系列远程处理组件的创建。 显然，主要目标是确保结果与 DCOM 兼容，并确保在 DCOM 可用时可由它替换结果。 它们随后继续运行以便为 16 位和 32 位 Windows 平台实现远程自动化 (RA)。  
  
 远程自动化不依赖于任何特定语言，但直到 Visual C++ 4.2 Enterprise Edition 发布时，它才仅随 Visual Basic 4.0 提供。 请注意，远程自动化已完全被 DCOM 归入。 如果您有机会在应用程序中使用 DCOM 而不是远程自动化，则应执行此操作。 但是，在某些情况下，远程自动化更合适：  
  
-   当您有 16 位客户端时。  
  
-   如果您的组织还没有部署 DCOM 支持的版本的 Windows NT 或 Windows 95。  
  
-   如果要升级使用远程自动化的现有应用程序套件以便用 C++ 组件替换一个或多个 Visual Basic 组件。  
  
 为了使用远程自动化而创建的程序和为了使用通过 DCOM 实现的自动化而创建的程序不需要有区别，利用配置实用工具，您可以简化远程自动化和 DCOM 之间的操作切换。 因此，在基础结构到位后，将应用程序从远程自动化升级到 DCOM 并不困难。  
  
## <a name="see-also"></a>另请参阅  
 [远程自动化提供什么](what-does-remote-automation-provide-q.md)   
 [DCOM 历史记录](../mfc/history-of-dcom.md)
