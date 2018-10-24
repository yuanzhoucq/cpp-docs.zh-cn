---
title: 定义存储的过程 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 769f2bf2c0ef6c2c92b4c0468569e91d399cea59
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808441"
---
# <a name="defining-stored-procedures"></a>定义存储过程

在调用之前的存储的过程，您必须首先定义它，使用[DEFINE_COMMAND](../../data/oledb/define-command.md)宏。 在定义该命令时，表示用问号 （？） 参数作为参数标记：  
  
```cpp  
DEFINE_COMMAND(CMySProcAccessor, _T("{INSERT {name, phone} into shippers  (?,?)}")  
```  
  
本主题中的代码示例中使用的语法 （使用大括号，等等） 是特定于 SQL Server。 在您的存储过程中使用的语法可能因你使用的提供程序。  
  
接下来，在参数映射中，指定你在命令中，使用参数按照在命令中出现的顺序列出的参数：  
  
```cpp  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param  
END_PARAM_MAP()  
```  
  
按照其设想，前面的示例定义存储的过程。 通常情况下，对于高效重用代码，数据库包含一组预定义存储过程使用的名称如"销售额按年度"或"dt_adduserobject。" 您可以查看使用 SQL Server 企业管理器及其定义。 按如下所示调用 (的位置？ 参数取决于存储的过程的接口):  
  
```cpp  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }")  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }")  
```  
  
接下来，声明命令类：  
  
```cpp  
class CMySProc : public CCommand<CAccessor<CMySProcAccessor>>  
```  
  
最后，调用存储的过程`OpenRowset`，如下所示：  
  
```cpp  
CSession m_session;  

HRESULT OpenRowset()  
{  
   return CCommand<CAccessor<CMySProcAccessor>>::Open(m_session);  
}  
```  
  
此外请注意，您可以定义存储的过程，请使用数据库特性[db_command](../../windows/db-command.md) ，如下所示：  
  
```cpp  
db_command("{ ? = CALL dbo.dt_adduserobject }")  
```  
  
## <a name="see-also"></a>请参阅  

[使用存储过程](../../data/oledb/using-stored-procedures.md)