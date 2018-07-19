---
title: TN047： 放宽数据库事务需求 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.data
dev_langs:
- C++
helpviewer_keywords:
- TN047
ms.assetid: f93c51cf-a8c0-43d0-aa47-7bcb8333d693
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be5870efacb61d5c0bb74f85427c41f787d2edd6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380928"
---
# <a name="tn047-relaxing-database-transaction-requirements"></a>TN047：放宽数据库事务需求
讨论 MFC ODBC 数据库类的事务要求，此技术说明现已过时。 在 MFC 4.2 版之前数据库类所需的记录集后保留游标**CommitTrans**或**回滚**操作。 ODBC 驱动程序和 DBMS 不支持此级别的光标保留，如果数据库类未不会启用交易。  
  
 从 MFC 4.2 开始，数据库类具有放宽需要光标保留限制。 如果该驱动程序支持它们，将启用事务。 但是，现在必须检查的效果**CommitTrans**或**回滚**上打开记录集的操作。 请参阅成员函数[CDatabase::GetCursorCommitBehavior](../mfc/reference/cdatabase-class.md#getcursorcommitbehavior)和[CDatabase::GetCursorRollbackBehavior](../mfc/reference/cdatabase-class.md#getcursorrollbackbehavior)有关详细信息。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

