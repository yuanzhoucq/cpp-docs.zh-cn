---
title: "创建并显示对话框 | Microsoft Docs"
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
  - "MFC 对话框, 创建"
  - "MFC 对话框, 显示"
  - "有模式对话框, 创建"
  - "无模式对话框, 创建"
  - "打开对话框"
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 创建并显示对话框
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建对话框对象是个两阶段操作。  首先，请构造对话框对象，然后创建对话框窗口。  模式和无模式对话框。用于的进程不同一些创建并显示它们。  下表列出模式和无模式对话框通常如何构造并显示。  
  
### 创建对话框  
  
|对话框类型|如何创建|  
|-----------|----------|  
|[Modeless](../mfc/creating-modeless-dialog-boxes.md)|构造 `CDialog`，然后调用 **创建** 成员函数。|  
|[模式](../mfc/creating-modal-dialog-boxes.md)|构造 `CDialog`，然后调用 `DoModal` 成员函数。|  
  
 可以，如果需要，创建从已从对话框模板资源了构造而不是上的 [内存对话框模板](../mfc/using-a-dialog-template-in-memory.md) 的对话框。  这是一个高级主题，包括：  
  
## 请参阅  
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)