---
title: "远程自动化安装 | Microsoft Docs"
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
  - "安装远程自动化"
  - "远程自动化, 安装"
ms.assetid: 9a02c9f6-dfc6-4489-b240-a1afe25fa0c5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 远程自动化安装
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

远程的自动化具有相对较少量组件：  
  
-   远程的自动化客户端代理，AUTPRX32.DLL。  
  
-   远程的自动化服务器端组件，自动化管理器，AUTMGR32.EXE。  
  
-   RAC 管理器，镭 CMGR32 .EXE，与其匹配的镭 CREG32 .DLL。  
  
 这些 RAC 管理器中，使用 Visual Basic 编写并需要 Visual Basic 运行时支持。  当安装 Visual C\+\+ 企业版时，这些操作和其他自动化文件由远程设置安装。  
  
 如果复制远程组件的自动化到 Visual C\+\+ 版本 Enterprise Edition 的计算机没有安装，请确保 REGSRV32.EXE 计算机上的路径使用下面的命令行，并注册镭 CREG32 .DLL:  
  
 REGSRVR32 镭 CREG32 .DLL  
  
> [!NOTE]
>  RAC 管理器版本，在 Visual C\+\+ 5.0 GUAGE32.OCX 和 .ocx CTL32 所需的选项卡上。  二者没有这些不需要的 RAC 管理器版本随 Visual C\+\+ 企业版，版本 5.0 或更是必需的。  
  
## 本节内容  
 [自动化管理器](../mfc/automation-manager-mfc.md)  
  
 [远程自动化连接管理器](../mfc/remote-automation-connection-manager.md)  
  
 [远程自动化用户组件](../mfc/remote-automation-user-components.md)  
  
## 请参阅  
 [远程自动化](../mfc/remote-automation.md)