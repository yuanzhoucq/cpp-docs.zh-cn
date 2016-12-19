---
title: "对话框数据验证 | Microsoft Docs"
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
  - "数据验证 [C++], 对话框"
  - "数据验证 [C++], 消息框"
  - "DDV（对话框数据验证）[C++]"
  - "对话框 [C++], 验证数据"
  - "验证数据 [C++], 对话框数据输入"
  - "验证数据 [C++], 消息框"
ms.assetid: f070c309-2044-4ff2-8c92-1ec1ea84af58
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 对话框数据验证
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以指定要验证以及数据交换。通过调用 DDV 函数，如该示例所示在 [对话框数据交换](../mfc/dialog-data-exchange.md)。  示例中的 `DDV_MaxChars` 调用验证。文本框控件中输入的字符串的长度不超过 20 个字符。  DDV 函数通常通知具有 MessageBox 的用户，并且在验证失败的问题在控件上并将焦点置于，因此用户可以重新输入数据。  必须在同一控件的 DDX 函数之后调用特定控件的 DDV 函数。  
  
 您还可以定义自己的自定义 DDV DDX 和例程。  有关详细信息和 DDV 上的 DDX 和其他特性，请参见 [MFC 技术说明 26](../mfc/tn026-ddx-and-ddv-routines.md)。  
  
 [添加成员变量向导](../ide/add-member-variable-wizard.md) 编写中所有数据映射的 DDX 和 DDV 调用您的。  
  
## 请参阅  
 [对话框数据交换和验证](../mfc/dialog-data-exchange-and-validation.md)   
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)   
 [对话框数据交换](../mfc/dialog-data-exchange.md)