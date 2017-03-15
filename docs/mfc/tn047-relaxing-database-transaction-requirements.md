---
title: "TN047：放宽数据库事务要求 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TN047"
ms.assetid: f93c51cf-a8c0-43d0-aa47-7bcb8333d693
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# TN047：放宽数据库事务要求
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此技术注释，讨论 MFC ODBC 数据库类中要求事务，现已过时。  在 MFC 4.2 版之前，数据库类需要光标位于记录集保留在 **CommitTrans** 或 **回滚** 操作之后。  如果 ODBC 驱动程序与 DBMS 不支持此级别光标保存，则数据库类不支持事务。  
  
 从 MFC 4.2 开始，数据库类放宽了游标保存的限制。  如果您的驱动程序支持事务，它们将启用。  但是，现在必须检查 **CommitTrans** 或 **回滚** 操作的效果打开记录集。  参见成员函数 [CDatabase::GetCursorCommitBehavior](../Topic/CDatabase::GetCursorCommitBehavior.md) 和 [CDatabase::GetCursorRollbackBehavior](../Topic/CDatabase::GetCursorRollbackBehavior.md)。更多信息。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)