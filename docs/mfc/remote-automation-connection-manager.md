---
title: "远程自动化连接管理器 | Microsoft Docs"
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
  - "自动化客户端, 针对远程自动化的配置"
  - "自动化服务器, 针对远程自动化的配置"
  - "RAC 管理器工具"
  - "注册表, 远程自动化"
  - "远程自动化连接管理器"
  - "远程自动化, 配置客户端和服务器计算机"
ms.assetid: 562eb7bc-f95c-46ad-ac97-f0dfa98362af
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 远程自动化连接管理器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要配置客户端和服务器机器，则需要进行注册表更改。  而不是手动执行此，使用远程自动化连接 \(RAC\) 管理器工具更为方便。  此工具，RACMGR32 .EXE，以及 RACREG32 .DLL 外，还需要复制到您选择的所有目录。  通过将其放入路径，使用运行可能从任务栏中执行。  或者，在开头菜单中创建快捷方式或将对它引用。  
  
 RACMGR32 在 Visual Basic 编写的并需要某些 Visual Basic 支持 DLL。  这些文件位于目录放置和在 CD\-ROM 中 RACMGR32 相同。  由 Visual C\+\+ 企业版中设置安装这些文件的版本与 Visual Basic Enterprise Edition 5.0 的这些等效或接近。  Visual C\+\+ Setup 以复制 Visual Basic 文件的新版本到系统目录。  对于 Windows 9x，该目录通常是 C:\\Windows\\System.  对于 Windows 2000 和 Windows NT，它通常是 C:\\WINNT\\system32.  设置也用操作系统注册这些文件。  可以从 Visual Basic 安装中移除它们。  
  
## 请参阅  
 [自动化管理器 \(MFC\)](../mfc/automation-manager-mfc.md)   
 [远程自动化用户组件](../mfc/remote-automation-user-components.md)   
 [远程自动化安装](../mfc/remote-automation-installation.md)