---
title: "输出参数 | Microsoft Docs"
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
  - "过程调用"
  - "过程调用, 存储过程"
  - "存储过程, 调用"
  - "存储过程, 参数"
ms.assetid: 4f7c2700-1c2d-42f3-8c9f-7e83962b2442
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 输出参数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

调用存储过程类似于调用 SQL 命令。  其差异主要在于存储过程使用输出参数（或“outparameter”）并返回值。  
  
 在下列存储过程中，第一个“?”是返回值（电话），第二个“?”是输入参数（姓名）：  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }")  
```  
  
 在参数映射中指定 in 和 out 参数：  
  
```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)  
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter  
END_PARAM_MAP()  
```  
  
 应用程序必须处理从存储过程返回的输出。  在结果处理期间，不同的 OLE DB 提供程序返回输出参数和返回值的时间不同。  例如，用于 SQL Server 的 Microsoft OLE DB 提供程序 \(SQLOLEDB\) 只有在使用者检索或取消由存储过程返回的结果集之后才会提供输出参数并返回代码。  输出在最后一个来自服务器的 TDS 数据包中返回。  
  
## 行数  
 如果使用 OLE DB 使用者模板执行具有输出参数的存储过程，则只有在关闭行集合之后才设置行计数。  
  
 例如，请看一个带有行集合和输出参数的存储过程：  
  
```  
create procedure sp_test  
   @_rowcount integer output  
as  
   select top 50 * from test  
   @_rowcount = @@rowcount  
return 0  
```  
  
 @\_rowcount 输出参数报告从 test 表实际返回的行数。  但该存储过程将行数的最大值限制为 50。  例如，如果在 test 中有 100 行，行计数将为 50（因为此代码只检索前 50 行）。  如果表中只有 30 行，则行计数将为 30。  必须在调用 **Close** 或 **CloseAll** 填充输出参数后才能获取其值。  
  
## 请参阅  
 [使用存储过程](../../data/oledb/using-stored-procedures.md)