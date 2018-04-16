---
title: "事务 (ODBC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets [C++], updating
- transactions [C++], MFC ODBC classes
- ODBC [C++], transactions
- recordsets [C++], updating
- databases [C++], transactions
- recordsets [C++], transactions
- ODBC recordsets [C++], transactions
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2816e1cfe3c62fecede5c909bc1593779aa90d54
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="transaction-odbc"></a>事务 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 事务是一种方法进行分组或批处理，对更新的一系列[数据源](../../data/odbc/data-source-odbc.md)，以便所有更改同时提交，或如果回滚事务，则不提交。 如果不使用事务，在而正在按需提交不是自动提交到数据源的更改。  
  
> [!NOTE]
>  并非所有 ODBC 数据库驱动程序都支持事务。 调用`CanTransact`成员函数你[CDatabase](../../mfc/reference/cdatabase-class.md)或[CRecordset](../../mfc/reference/crecordset-class.md)对象确定您的驱动程序是否支持给定的数据库的事务。 请注意，`CanTransact`不会告诉你数据源是否提供完整的事务支持。 你还必须调用`CDatabase::GetCursorCommitBehavior`和`CDatabase::GetCursorRollbackBehavior`后**CommitTrans**和**回滚**以检查事务的效果在打开`CRecordset`对象。  
  
 调用`AddNew`和**编辑**的成员函数`CRecordset`对象的数据源立即当调用的影响**更新**。 **删除**调用还会立即生效。 与此相反，你可以使用包含多个对的调用事务`AddNew`，**编辑**，**更新**，和**删除**，它是执行，但尚未提交之前你调用**CommitTrans**显式。 通过建立事务，可以在保留回滚它们的功能的同时执行一系列此类调用。 如果关键资源不可用或某些其他条件阻止从正在完成整个事务，可以回滚而不是中提交事务。 在这种情况下，任何属于事务更改会影响数据源。  
  
> [!NOTE]
>  目前，类`CRecordset`不支持到数据源的更新，如果已实现批量行提取。 这意味着您不能对进行调用`AddNew`，**编辑**，**删除**，或**更新**。 但是，你可以编写自己的函数来执行更新，然后调用给定的事务中的这些函数。 有关批量行提取的详细信息，请参阅[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
> [!NOTE]
>  除了影响记录集中，事务影响，只要你使用 ODBC 直接执行 SQL 语句**HDBC**与你`CDatabase`对象或一个 ODBC **HSTMT**基于**HDBC**。  
  
 当具有多个必须同时更新的记录时，事务是特别有用。 在这种情况下，你想要避免半完成事务，例如当上次更新进行之前引发了异常的情况下可能发生。 将这些更新组成事务允许恢复 （回滚） 所做的更改，并返回到事务前状态的记录。 例如，如果银行将钱从帐户 A 转移到帐户 B，同时从取款和存入 B 必须成功以便正确处理款项，否则整个事务必须失败。  
  
 在数据库类中，执行事务通过`CDatabase`对象。 A`CDatabase`对象表示为数据源的连接和与该关联的一个或多个记录集`CDatabase`对象在通过记录集成员函数的数据库的表上运行。  
  
> [!NOTE]
>  支持仅一个级别的事务。 不能嵌套事务，也不能跨多个数据库对象。  
  
 以下主题提供有关如何执行事务的详细信息：  
  
-   [事务：在记录集中执行事务 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)  
  
-   [事务：事务如何影响更新 (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)  
  
## <a name="see-also"></a>请参阅  
 [开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)