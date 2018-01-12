---
title: "ODBC 和数据库类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e3041a4fc027a8786fb62db7df6eaf486633ce97
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-and-the-database-classes"></a>ODBC 和数据库类
MFC ODBC 数据库类封装你将通常自行进行在成员中的函数的 ODBC API 函数调用[CDatabase](../../mfc/reference/cdatabase-class.md)和[CRecordset](../../mfc/reference/crecordset-class.md)类。 例如，复杂 ODBC 调用序列、 返回的记录到存储位置、 处理错误情况，以及其他操作的绑定是为你管理的数据库类。 因此，你可以使用相当简单的类接口来操作通过记录集对象的记录。  
  
> [!NOTE]
>  ODBC 数据源是通过 MFC ODBC 类，如本主题中所述，或通过 MFC 数据访问对象 (DAO) 类访问。  
  
 尽管数据库类封装 ODBC 功能，但它们不提供 ODBC API 函数的一对一映射。 数据库类提供更高级别的抽象，建模后找到 Microsoft Access 和 Microsoft Visual Basic 中的数据访问对象。 有关详细信息，请参阅[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)。  
  
## <a name="see-also"></a>请参阅  
 [ODBC 基础](../../data/odbc/odbc-basics.md)