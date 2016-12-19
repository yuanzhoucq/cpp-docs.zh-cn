---
title: "远程自动化用户组件 | Microsoft Docs"
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
  - "DLL [C++], 自动化"
  - "远程自动化 [C++], 用户组件"
ms.assetid: 601591cc-a442-440a-988e-baf3284b0d46
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 远程自动化用户组件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您将需要确保每台客户端包含客户端程序和它所需的任何支持 DLL。  还需要确保服务器应用程序和它所需服务器计算机上的任何支持 DLL。  最后，您需要确保服务器程序在每台客户端注册，然后 RAC 管理器可以运行配置连接。  如果程序注册自 \(大多数为是\)，则只需对客户端的服务器程序注册它。  失败时，可能必须执行您提供的注册表，或者手动编辑注册表。  
  
## 请参阅  
 [自动化管理器 \(MFC\)](../mfc/automation-manager-mfc.md)   
 [远程自动化连接管理器](../mfc/remote-automation-connection-manager.md)   
 [远程自动化安装](../mfc/remote-automation-installation.md)