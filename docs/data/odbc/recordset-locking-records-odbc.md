---
title: 记录集： 锁定记录 (ODBC) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- locks [C++], recordsets
- optimistic locking
- pessimistic locking in ODBC
- recordsets [C++], locking records
- optimistic locking, ODBC
- ODBC recordsets [C++], locking records
- data [C++], locking
ms.assetid: 8fe8fcfe-b55a-41a8-9136-94a7cd1e4806
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 76d7ab2df01e485ffff70120609227b9fbae6ac5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-locking-records-odbc"></a>记录集：锁定记录 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 本主题说明：  
  
-   [类型的记录锁定可用](#_core_record.2d.locking_modes)。  
  
-   [如何在更新过程中锁定记录集中的记录集](#_core_locking_records_in_your_recordset)。  
  
 当使用记录集来更新数据源上的记录时，你的应用程序可以锁定记录，因此没有其他用户可以在同一时间更新记录。 在同一时间更新由两个用户记录的状态未定义的除非系统可以保证两个用户不能同时更新的记录。  
  
> [!NOTE]
>  本主题适用于派生自`CRecordset`中哪些批量行提取尚未实现。 如果你已实现批量行提取的某些信息不适用。 例如，不能调用**编辑**和**更新**成员函数。 有关批量行提取的详细信息，请参阅[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_record.2d.locking_modes"></a>记录锁定模式  
 数据库类提供两个[记录锁定模式](../../mfc/reference/crecordset-class.md#setlockingmode):  
  
-   开放式锁定 （默认值）  
  
-   保守式锁定  
  
 更新记录发生的三个步骤：  
  
1.  通过调用开始操作[编辑](../../mfc/reference/crecordset-class.md#edit)成员函数。  
  
2.  更改当前记录的相应字段。  
  
3.  结束操作，并通常提交更新 — 通过调用[更新](../../mfc/reference/crecordset-class.md#update)成员函数。  
  
 乐观锁定锁定仅在数据源上的记录**更新**调用。 如果你使用在多用户环境中的乐观锁定，则应用程序应处理**更新**失败条件。 只要你调用保守式锁定锁定记录**编辑**并不会释放它直到你调用**更新**(故障指示通过`CDBException`机制，不是按值**FALSE**返回**更新**)。 保守式锁定有潜在的性能，并为其他用户，因为并发访问同一个记录可能需要等到您的应用程序完成后才能**更新**过程。  
  
##  <a name="_core_locking_records_in_your_recordset"></a>锁定记录集中的记录集  
 如果你想要更改的记录集对象[锁定模式](#_core_record.2d.locking_modes)从默认情况下，你必须更改此模式，然后才能调用**编辑**。  
  
#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>若要更改你的记录集的当前锁定模式  
  
1.  调用[SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode)成员函数，指定**CRecordset::pessimistic**或**CRecordset::optimistic**。  
  
 新的锁定模式保持有效，直到你再次更改或关闭记录集。  
  
> [!NOTE]
>  相对较少的 ODBC 驱动程序目前支持保守式锁定。  
  
## <a name="see-also"></a>请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [记录集： 执行联接 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)   
 [记录集：添加、更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)