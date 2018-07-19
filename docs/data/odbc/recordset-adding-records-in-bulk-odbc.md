---
title: 记录集： 添加记录 (Odbc) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7bb39b910eae797f360513954ad0c32d5e99bb86
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089280"
---
# <a name="recordset-adding-records-in-bulk-odbc"></a>记录集：批量添加记录 (ODBC)
本主题适用于 MFC ODBC 类。  
  
 MFC [CRecordset](../../mfc/reference/crecordset-class.md)类具有一新优化方法，当你在添加新记录到表在大容量时可提高效率。  
  
> [!NOTE]
>  本主题适用于派生自`CRecordset`中哪些批量行提取尚未实现。 如果你将批量行提取，请参阅[记录集： 批量获取记录 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 新选项**dwOptions**参数[CRecordset::Open](../../mfc/reference/crecordset-class.md#open)成员函数， **optimizeBulkAdd**，当你要添加多个记录时可提高性能连续而不调用**Requery**或**关闭**。 脏之前第一个字段**更新**调用标记为脏的后续`AddNew` /**更新**调用。  
  
 如果你正在使用数据库类以利用 **:: SQLSetPos** ODBC API 函数用于添加、 编辑和删除记录，这种优化是不必要的。  
  
 如果加载 ODBC 游标库或 ODBC 驱动程序不支持添加、 编辑和删除通过 **:: SQLSetPos**，这种优化应提高大容量添加性能。 若要打开此优化，设置**dwOptions**中的参数**打开**调用你记录集到以下：  
  
```  
appendOnly | optimizeBulkAdd  
```  
  
## <a name="see-also"></a>请参阅  
 [记录集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [记录集： 添加、 更新和删除记录 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)   
 [记录集：锁定记录 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)