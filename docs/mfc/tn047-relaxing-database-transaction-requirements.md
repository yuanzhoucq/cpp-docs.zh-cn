---
title: "TN047： 放宽数据库事务需求 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.data
dev_langs: C++
helpviewer_keywords: TN047
ms.assetid: f93c51cf-a8c0-43d0-aa47-7bcb8333d693
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 92631d96e8782a80275695ef4bf2623dc1bff833
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tn047-relaxing-database-transaction-requirements"></a>TN047：放宽数据库事务需求
讨论 MFC ODBC 数据库类的事务要求，此技术说明现已过时。 在 MFC 4.2 版之前数据库类所需的记录集后保留游标**CommitTrans**或**回滚**操作。 ODBC 驱动程序和 DBMS 不支持此级别的光标保留，如果数据库类未不会启用交易。  
  
 从 MFC 4.2 开始，数据库类具有放宽需要光标保留限制。 如果该驱动程序支持它们，将启用事务。 但是，现在必须检查的效果**CommitTrans**或**回滚**上打开记录集的操作。 请参阅成员函数[CDatabase::GetCursorCommitBehavior](../mfc/reference/cdatabase-class.md#getcursorcommitbehavior)和[CDatabase::GetCursorRollbackBehavior](../mfc/reference/cdatabase-class.md#getcursorrollbackbehavior)有关详细信息。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

