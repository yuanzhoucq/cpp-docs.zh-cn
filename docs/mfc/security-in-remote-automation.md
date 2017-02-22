---
title: "远程自动化中的安全性 | Microsoft Docs"
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
  - "激活对象"
  - "AllowRemoteActivation"
  - "自动化对象, 安全选项"
  - "对象激活"
  - "远程自动化, 安全性"
  - "安全性 [MFC]"
  - "安全性 [MFC], 远程自动化"
ms.assetid: 276b300d-c0b5-4bd8-8bf5-0270994b9cfa
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 远程自动化中的安全性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

远程的自动化支持安全性的基本级别可以允许一个服务器应用程序的编写人员\(或，相当，其管理员\) 指定特定对象如何能够远程激活。  在特定的系统的所有自动对象可以全局设置“禁止远程的激活”或“允许远程的激活”。  此外，更多的时候，可能给出单个对象这样的功能。  远程的自动化在每个对象的注册表设置中使用密钥，**AllowRemoteActivation**，决定给定服务器是否能远程激活。  如果系统级设置使用此模式，则注册表的每个对象可能已分配此密钥，因此，每个对象的单个状态可以相应设置成“yes”或“no”。  
  
 如果服务器系统是 Windows NT 或 Windows 2000，则替代的安全窗体是允许的。  在这种情况下，远程自动化使用 NT 访问控制列表 \(ACL\) 指定哪些用户或组或用户组可能远程激活已指定的服务器。  
  
 注意应用于整个对象的安全选项；在该对象上设置特定接口或单个属性或方法的特性是不可能的。  
  
 所有安全选项可通过远程自动化连接\(RAC\) 管理器设置。  
  
## 请参阅  
 [远程自动化](../mfc/remote-automation.md)