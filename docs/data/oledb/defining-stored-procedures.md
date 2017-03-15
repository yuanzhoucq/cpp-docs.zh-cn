---
title: "定义存储过程 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB, 存储过程"
  - "存储过程, 定义"
  - "存储过程, OLE DB"
  - "存储过程, 语法"
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 定义存储过程
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

调用存储过程之前，必须首先使用 [DEFINE\_COMMAND](../../data/oledb/define-command.md) 宏对其进行定义。  定义该命令时，用问号 \(?\) 作为参数标记表示参数：  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{INSERT {name, phone} into shippers  (?,?)}")  
```  
  
 注意，在本主题中的代码示例中所使用的语法（使用大括号等）均特定于 SQL Server。  在存储过程中使用的语法可能随使用的提供程序的不同而不同。  
  
 接下来，在参数映射中指定命令中所使用的参数，将这些参数按照在命令中出现的顺序列出：  
  
```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param  
END_PARAM_MAP()  
```  
  
 前面的示例实际上定义了一个存储过程。  为了有效地重复使用代码，数据库通常会包含一组具有名称（如“Sales by Year”或“dt\_adduserobject”）的预定义存储过程。可以使用 SQL Server 企业管理器查看这些存储过程的定义。  可以用如下方式调用它们（“?”参数的位置取决于存储过程的接口）：  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }")  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }")  
```  
  
 下一步，声明命令类：  
  
```  
class CMySProc : public CCommand<CAccessor<CMySProcAccessor> >  
```  
  
 最后，在 `OpenRowset` 中调用存储过程，如下所示：  
  
```  
CSession m_session;  
HRESULT OpenRowset()  
{  
   return CCommand<CAccessor<CMySProcAccessor> >::Open(m_session);  
}  
```  
  
 注意，还可使用数据库特性 [db\_command](../../windows/db-command.md) 定义存储过程，如下所示：  
  
```  
db_command("{ ? = CALL dbo.dt_adduserobject }")  
```  
  
## 请参阅  
 [使用存储过程](../../data/oledb/using-stored-procedures.md)