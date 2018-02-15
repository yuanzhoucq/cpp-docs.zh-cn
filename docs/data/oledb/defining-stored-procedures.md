---
title: "定义存储的过程 |Microsoft 文档"
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
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5f11994ea34e79d9a4d4d8ae5c13ad67529755e0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="defining-stored-procedures"></a>定义存储过程
在调用之前存储的过程，你必须首先定义它，使用[DEFINE_COMMAND](../../data/oledb/define-command.md)宏。 在定义该命令时，作为参数标记表示用问号 （？） 的参数：  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{INSERT {name, phone} into shippers  (?,?)}")  
```  
  
 请注意，本主题中的代码示例中使用的语法 （使用大括号等等） 特定于 SQL Server。 你的存储过程中使用的语法可能会因你使用的提供程序。  
  
 接下来，在参数映射中，指定你在命令中，使用参数按照在命令中出现的顺序列出的参数：  
  
```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param  
END_PARAM_MAP()  
```  
  
 前面的示例，因为它将定义存储的过程。 通常情况下，对于高效地重复使用代码，数据库包含一组预定义的存储过程，如"销售额按年度"或"dt_adduserobject。"的名称 你可以查看其使用 SQL Server 企业管理器的定义。 如下所示调用 (放置的？ 参数取决于存储的过程的接口):  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }")  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }")  
```  
  
 接下来，声明命令类：  
  
```  
class CMySProc : public CCommand<CAccessor<CMySProcAccessor>>  
```  
  
 最后，调用存储的过程`OpenRowset`，如下所示：  
  
```  
CSession m_session;  

HRESULT OpenRowset()  
{  
   return CCommand<CAccessor<CMySProcAccessor>>::Open(m_session);  
}  
```  
  
 另请注意，你可以定义存储的过程，请使用数据库特性[db_command](../../windows/db-command.md) ，如下所示：  
  
```  
db_command("{ ? = CALL dbo.dt_adduserobject }")  
```  
  
## <a name="see-also"></a>请参阅  
 [使用存储过程](../../data/oledb/using-stored-procedures.md)