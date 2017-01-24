---
title: "激活：谓词 | Microsoft Docs"
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
  - "激活 [C++], 谓词"
  - "编辑谓词"
  - "OLE [C++], 激活"
  - "OLE [C++], 编辑"
  - "OLE 激活"
  - "主谓词"
  - "谓词"
ms.assetid: eb56ff23-1de8-43ad-abeb-dc7346ba7b70
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 激活：谓词
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明的主要角色，并附属谓词 OLE 设置 [激活](../mfc/activation-cpp.md)。  
  
 通常，双击嵌入的项允许用户编辑它。  但是，某些项不这样的行为。  例如，双击项创建的录音机应用程序无法单独窗口中打开服务器；相反，它播放声音。  
  
 此行为不同的原因是录音机项具有不同的“master 谓词”。当用户双击一个 OLE 项时，谓词是主要执行的操作。  对于 OLE 项的大多数类型，主要谓词是编辑，启动服务器创建项。  对于项数组类型，如录音机项，主要谓词是一个播放。  
  
 OLE 项的许多类型只支持一谓词，并编辑是最常见一个。  但是，某些项类型支持多个谓词。  例如，录音机项支持编辑为附属谓词。  
  
 通常使用的另某一谓词打开。  打开与谓词编辑相同，但服务器应用在单独的窗口中启动。  该谓词，当容器应用程序或服务器应用不支持就地激活时，应当使用。  
  
 当选择某一项时，必须通过子菜单命令调用。主要谓词之外的所有谓词。  此子菜单包含项支持的所有谓词并通过在 **编辑** 菜单上的 **对象**。通常到达命令 *类型* 有关 *类型* **对象** 命令的信息，请参见 [菜单和资源：容器添加](../mfc/menus-and-resources-container-additions.md)文章。  
  
 谓词应用支持服务器在 Windows 注册数据库中。  如果服务器应用程序编写使用 Microsoft 基础类库，则将自动注册所有谓词，当服务器启动。  在服务器应用的初始化阶段，否则，应注册它们。  有关更多信息，请参见知识库文章 [注册](../mfc/registration.md)。  
  
## 请参阅  
 [激活](../mfc/activation-cpp.md)   
 [容器](../mfc/containers.md)   
 [服务器](../mfc/servers.md)