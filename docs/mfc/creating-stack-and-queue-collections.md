---
title: "创建堆栈和队列集合 | Microsoft Docs"
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
  - "集合类, 创建"
  - "集合, 队列"
  - "集合, 堆栈"
  - "MFC 集合类, 队列集合"
  - "MFC 集合类, 堆栈集合"
  - "队列集合"
  - "堆栈"
  - "堆栈集合"
ms.assetid: 3c7bc198-35f0-4fc3-aaed-6005a0f22638
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 创建堆栈和队列集合
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明如何创建MFC 类列表中其他数据结构，例如 [堆栈](#_core_stacks) 和 [队列](#_core_queues)。  示例使用从 `CList`派生的类，但是，可以直接使用 `CList`，除非您需要添加功能。  
  
##  <a name="_core_stacks"></a> Stacks  
 由于标准列表集合具有列表头和尾，创建模仿一个后进先出 \(LIFO\) 堆栈的行为的派生列表集合很容易。  堆栈是像在堆盘子自助餐厅。  当任务添加到堆栈，它们在它转到上面堆栈。  最后栏添加第一个中移除。  列表集合成员函数 `AddHead` 和 `RemoveHead` 可用于从列表的报头特别添加和移除元素；因此，新添加的元素为第一中移除。  
  
#### 创建栈集合：  
  
1.  从一个现有 MFC 类派生列表的新列表类并添加更多成员函数支持堆栈操作的功能。  
  
     下面的示例显示如何将成员函数添加到元素偷看推送到堆栈，在堆栈的顶级元素和从堆栈弹出顶部元素：  
  
     [!code-cpp[NVC_MFCCollections#20](../mfc/codesnippet/CPP/creating-stack-and-queue-collections_1.h)]  
  
 请注意此方法公开基础 `CObList` 类。  用户可以调用任何 `CObList` 成员函数，使其堆栈中有意义。  
  
##  <a name="_core_queues"></a> 队列  
 由于标准列表集合具有列表头和尾，创建模仿一个先进先出 \(FIFO\) 队列的行为的派生列表集合很容易。  队列与配置自助餐厅行中。  行的第人是第个服务。  随着更多的人是，则转到行结束等待其关闭。  列表集合成员函数 `AddTail` 和 `RemoveHead` 可用于从列表的报头或尾特别添加和移除元素；因此，新添加的元素为最后移除。  
  
#### 创建队列集合：  
  
1.  从某个预定义的列表类派生新的列表类随 Microsoft 基础类 \(MFC\) 库并添加更多支持成员函数语义排队操作。  
  
     下面的示例显示可如何追加成员函数将元素添加到队列的结尾和从队列前面的获取元素。  
  
     [!code-cpp[NVC_MFCCollections#21](../mfc/codesnippet/CPP/creating-stack-and-queue-collections_2.h)]  
  
## 请参阅  
 [集合](../mfc/collections.md)