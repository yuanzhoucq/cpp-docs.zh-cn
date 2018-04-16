---
title: "输出参数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, calling
- stored procedures, parameters
- procedure calls
- procedure calls, stored procedures
ms.assetid: 4f7c2700-1c2d-42f3-8c9f-7e83962b2442
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 663ff735eea34c53ea56c2cc4f24b4aedf2a3434
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="output-parameters"></a>输出参数
调用存储的过程是类似于调用 SQL 命令。 主要区别是存储的过程使用输出参数 （或"输出"） 和返回值。  
  
 在以下存储过程中，第一个？ is 返回值 (phone) 和第二个？ 是输入的参数 （名称）：  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }")  
```  
  
 参数映射中指定了切入和切出参数：  
  
```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)  
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter  
END_PARAM_MAP()  
```  
  
 你的应用程序必须处理从存储过程返回的输出。 不同的 OLE DB 提供程序返回输出参数和返回值的结果处理过程中的不同时间。 例如，Microsoft OLE DB 提供程序的 SQL Server (SQLOLEDB) 不提供输出参数和返回之前的代码后使用者已检索到或取消的存储过程返回的结果集。 将输出从服务器返回的最后一个的 TDS 数据包中。  
  
## <a name="row-count"></a>行计数  
 如果使用 OLE DB 使用者模板来执行具有输出的存储的过程，直到您关闭行集未设置的行计数。  
  
 例如，考虑使用带有行集和输出参数为存储的过程：  
  
```  
create procedure sp_test  
   @_rowcount integer output  
as  
   select top 50 * from test  
   @_rowcount = @@rowcount  
return 0  
```  
  
 @_rowcount带有报告测试表中实际返回行数。 但是，此存储的过程限制为 50 的最大值的行数。 例如，如果在测试中没有 100 行，行计数应为 50 （因为此代码检索仅前 50 行）。 如果表中仅 30 行，行计数将为 30。 必须调用**关闭**或**CloseAll**来填充带有之前提取其值。  
  
## <a name="see-also"></a>请参阅  
 [使用存储过程](../../data/oledb/using-stored-procedures.md)