---
title: 访问 ODBC 和 SQL |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- API calls [C++], calling DAO or ODBC directly
- Windows API [C++], calling from MFC
- ODBC API functions [C++]
- ODBC API functions [C++], calling from MFC
- SQL [C++], calling ODBC API functions
- ODBC [C++], API functions
ms.assetid: 5613d7dc-00b7-4646-99ae-1116c05c52b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 40b88cd7db95a05edd6174701c04724a6f245223
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018712"
---
# <a name="access-to-odbc-and-sql"></a>访问 ODBC 和 SQL

Microsoft 基础类库封装许多 Windows API 调用，而仍可在直接调用任何 Windows API 函数。 数据库类为您提供了有关 ODBC API 那样灵活。 尽管数据库类可使您从 ODBC 复杂性在很大，可以直接从任何位置调用 ODBC API 函数在程序中。  
  
同样，数据库类使您无需使用大量[SQL](../../data/odbc/sql.md)，但如果你想，您可以直接使用 SQL。 可以通过传递自定义 SQL 语句 （或默认语句设置部分） 自定义记录集对象打开记录集时。 此外可以使用直接 SQL 调用[ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql)类的成员函数[CDatabase](../../mfc/reference/cdatabase-class.md)。  
  
有关详细信息，请参阅[ODBC： 直接调用 ODBC API 函数](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)并[SQL： 进行直接 SQL 调用 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)。  
  
## <a name="see-also"></a>请参阅  

[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)