---
title: TN047:放宽数据库事务需求
ms.date: 11/04/2016
f1_keywords:
- vc.data
helpviewer_keywords:
- TN047
ms.assetid: f93c51cf-a8c0-43d0-aa47-7bcb8333d693
ms.openlocfilehash: 968420658a90c983d8e6c3eaf1e0c61603fc5441
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276801"
---
# <a name="tn047-relaxing-database-transaction-requirements"></a>TN047:放宽数据库事务需求

讨论 MFC ODBC 数据库类的事务要求的那样，此技术说明现已过时。 在 MFC 4.2 之前数据库类所需的记录集后保留游标**CommitTrans**或**回滚**操作。 如果 ODBC 驱动程序和 DBMS 不支持游标保留此级别，然后数据库类未启用的事务。

从 MFC 4.2 开始，数据库类具有放宽需要游标暂留的限制。 如果该驱动程序支持它们，将启用的事务。 但是，现在必须检查的效果**CommitTrans**或**回滚**上打开的记录集的操作。 请参阅成员函数[CDatabase::GetCursorCommitBehavior](../mfc/reference/cdatabase-class.md#getcursorcommitbehavior)并[CDatabase::GetCursorRollbackBehavior](../mfc/reference/cdatabase-class.md#getcursorrollbackbehavior)有关详细信息。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
