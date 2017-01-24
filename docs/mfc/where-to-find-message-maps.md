---
title: "消息映射的位置 | Microsoft Docs"
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
  - "定位消息映射"
  - "宏, 消息映射"
  - "消息映射, 查找"
  - "消息映射宏"
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 消息映射的位置
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在创建向导时使用应用程序的主干应用程序，应用程序向导编写时为您创建的每个命令目标类的消息映射。  这包含派生的应用程序、文档、视图和框架窗口类。  某些消息映射已具有某些消息和预定义命令的应用程序向导提供的输入，而且，数组是要添加的处理程序的占位符。  
  
 类的消息映射。类的 .cpp 文件中。  与应用程序向导创建的基本消息映射时，使用"属性"窗口添加消息的输入和命令每个类处理。  在添加一些项后，典型的消息映射可能类似于：  
  
 [!CODE [NVC_MFCMessageHandling#1](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCMessageHandling#1)]  
  
 消息映射包括宏的集合。  两宏，[BEGIN\_MESSAGE\_MAP](../Topic/BEGIN_MESSAGE_MAP.md)[END\_MESSAGE\_MAP](../Topic/END_MESSAGE_MAP.md)，括号和消息映射。  其他宏，如 `ON_COMMAND`，则填充消息映射的内容。  
  
> [!NOTE]
>  消息映射宏不用分号。  
  
 当使用向导添加类创建新类时，它会针对类提供了消息映射。  或者，使用源代码编辑器，可以手动创建消息映射。  
  
## 请参阅  
 [框架如何搜索消息映射](../mfc/how-the-framework-searches-message-maps.md)