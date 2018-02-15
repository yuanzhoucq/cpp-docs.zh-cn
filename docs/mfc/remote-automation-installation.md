---
title: "远程自动化安装 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Remote Automation [MFC], installation
- installing Remote Automation [MFC]
ms.assetid: 9a02c9f6-dfc6-4489-b240-a1afe25fa0c5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: acd8ee55261dfa03c68aef506dc90188d8d27d37
ms.sourcegitcommit: fa7a6dccddce3747389c91277a53e296f905305c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="remote-automation-installation"></a>远程自动化安装
远程自动化具有相对较少组件：  
  
-   远程自动化客户端代理，AUTPRX32。DLL。  
  
-   远程自动化服务器端组件，自动化管理器，AUTMGR32。EXE。  
  
-   RAC 管理器，RACMGR32。EXE，使用其匹配 RACREG32。DLL。  
  
 其中，在 Visual Basic 中编写 RAC 管理器并因此需要 Visual Basic 运行时支持。 安装 Visual c + + Enterprise Edition 时，这些文件和其他远程自动化文件被安装安装程序。  
  
 如果将远程自动化组件复制到计算机上的 Visual c + + 版本未安装 Enterprise Edition，请确保该 REGSRV32。EXE 位于该计算机的路径，并注册 RACREG32。使用以下命令行的 DLL:  
  
 REGSRVR32 RACREG32.DLL  
  
> [!NOTE]
>  RAC 管理器的 Visual c + + 5.0 要求 GUAGE32 之前的版本。OCX 和 TABCTL32。OCX。 这两项都是必需的版本的 RAC 管理器附带有 Visual c + + 企业版，版本 5.0 或更高版本。  
  
## <a name="in-this-section"></a>本节内容  
 [自动化管理器](../mfc/automation-manager-mfc.md)  
  
 [远程自动化连接管理器](../mfc/remote-automation-connection-manager.md)  
  
 [远程自动化用户组件](../mfc/remote-automation-user-components.md)  
  
## <a name="see-also"></a>请参阅  
 [远程自动化](../mfc/remote-automation.md)

