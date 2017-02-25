---
title: "重写标准命令传送 | Microsoft Docs"
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
  - "命令处理, 传送命令"
  - "命令传送, 重写"
  - "MFC, 命令传送"
  - "重写, 标准命令传送"
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 重写标准命令传送
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有时，当必须实现标准框架的一些变体路由时，可以重写该成员。  目的是将一个或多个类的路由通过重写这些类的 `OnCmdMsg`。  所示：  
  
-   在中断顺序传递到非默认对象的类。  
  
-   在新的非默认的对象或在命令目标可能会传递命令。  
  
 如果插入某些新的路由到对象，则类必须是命令目标类。  在 `OnCmdMsg`的重写版本，请确保调用重写的版本。  参见 `CCmdTarget` 类。这些类与 `CView` 和 **CDocument** 的 [OnCmdMsg](../Topic/CCmdTarget::OnCmdMsg.md) 成员函数" *MFC 参考* 和生成中提供的源代码的示例。  
  
## 请参阅  
 [框架如何调用处理程序](../mfc/how-the-framework-calls-a-handler.md)