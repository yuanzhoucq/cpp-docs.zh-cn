---
title: 使用存储的过程 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e5b49daa44fc8c88316134915945ad7ee01bb81a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112233"
---
# <a name="using-stored-procedures"></a>使用存储过程
存储的过程是在数据库中存储的可执行对象。 调用存储的过程是类似于调用 SQL 命令。 在数据源 （而不是执行或准备客户端应用程序中的语句） 上使用存储的过程可以提供几个好处，包括更高的性能，减少的网络开销，以及改进的一致性和准确性。  
  
 存储的过程可以具有任意数量的 （包括零） 输入或输出参数，并且可以通过返回的值。 可以将参数值硬编码为特定数据值，也可以使用参数标记 (问号？)。  
  
> [!NOTE]
>  必须使用编译使用 Visual c + + 创建的存储的过程的 CLR SQL Server **/clr: safe**编译器选项。  
  
 OLE DB 访问接口为 SQL Server (SQLOLEDB) 支持以下存储过程用于返回数据的机制：  
  
-   在过程中的每个 SELECT 语句生成的结果集。  
  
-   该过程可以返回通过输出参数的数据。  
  
-   该过程可以返回代码的整数。  
  
> [!NOTE]
>  你无法使用存储的过程的 OLE DB 访问接口为 Jet 因为该提供程序不支持存储的过程;查询字符串中允许使用仅常量。  
  
## <a name="see-also"></a>请参阅  
 [使用 OLE DB 使用者模板](../../data/oledb/working-with-ole-db-consumer-templates.md)