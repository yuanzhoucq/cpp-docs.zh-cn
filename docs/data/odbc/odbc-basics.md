---
title: ODBC 基础知识 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC cursor library [ODBC], ODBC components
- ODBC components
- ODBC components, required components
- ODBC, about ODBC
- ODBC, components
ms.assetid: ec529702-0fb2-4754-b8de-d1efa8eca18f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 69b3694292171f00e03cdb941def27fd9e8ffc84
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090294"
---
# <a name="odbc-basics"></a>ODBC 基础
本主题提供的基础知识的开放式数据库连接 (ODBC):  
  
-   [ODBC 数据库类使用的工作原理](../../data/odbc/odbc-and-the-database-classes.md)  
  
-   [ODBC 驱动程序如何使用动态记录集](../../data/odbc/odbc-driver-requirements-for-dynasets.md)  
  
-   [与应用程序需要重新分发的哪些 ODBC 组件](../../data/odbc/redistributing-odbc-components-to-your-customers.md)  
  
 你将还想要阅读相关的主题[ODBC: ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)。  
  
> [!NOTE]
>  ODBC 数据源是通过 MFC ODBC 类，如本主题中所述，或通过 MFC 数据访问对象 (DAO) 类访问。  
  
> [!NOTE]
>  MFC ODBC 类支持 Unicode 和多线程处理。 有关多线程处理支持的详细信息，请参阅[ODBC 类和线程](../../data/odbc/odbc-classes-and-threads.md)  
  
 ODBC 是一个调用级接口，允许应用程序访问 ODBC 驱动程序任何数据库中的数据。 使用 ODBC，可以在访问你的最终用户对为其任何数据库具有 ODBC 驱动程序中创建数据库应用程序。 ODBC 提供了一个 API，使你的应用程序要独立于源数据库管理系统 (DBMS)。  
  
 ODBC 是数据库部分的 Microsoft Windows 打开服务体系结构 (WOSA) 中，它是一个接口，用于基于 Windows 的桌面应用程序无需重写每个平台的应用程序连接到多个计算环境。  
  
 ODBC 组件如下：  
  
-   ODBC API  
  
     已调用的函数库、 一组的错误代码和一个标准[SQL](../../data/odbc/sql.md)在 Dbms 中访问数据的语法。  
  
-   ODBC 驱动程序管理器  
  
     代表应用程序加载数据库的 ODBC 驱动程序的一个动态链接库 (所用的 Odbc32.dll)。 此 DLL 是透明的你的应用程序。  
  
-   ODBC 数据库驱动程序  
  
     一个或多个特定 Dbms 的进程 ODBC 函数调用的 Dll。 提供的驱动程序的列表，请参阅[ODBC 驱动程序列表](../../data/odbc/odbc-driver-list.md)。  
  
-   [ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)  
  
     一个动态链接库 (Odbccr32.dll) 驻留之间 ODBC 驱动程序管理器和驱动程序并处理滚动到的数据。  
  
-   [ODBC 管理器](../../data/odbc/odbc-administrator.md)  
  
     一个工具，用于配置 DBMS 以使其可作为应用程序的数据源。  
  
 应用程序，从而实现从 Dbms 通过 ODBC 驱动程序专门为 DBMS 编写的工作，而不是直接使用 DBMS 的独立性。 该驱动程序将转换到命令的调用，可以使用其 DBMS，从而简化了开发人员的工作并使其可用于各种数据源。  
  
 数据库类支持您对其具有 ODBC 驱动程序的任何数据源。 例如，，这可能会包括关系数据库、 索引顺序访问方法 (ISAM) 数据库、 Microsoft Excel 电子表格或文本文件。 ODBC 驱动程序管理数据源的连接，SQL 用于从数据库中选择记录。  
  
 有关此版本的 Visual c + + 中包含的 ODBC 驱动程序的列表以及有关获取其他驱动程序的信息，请参阅[ODBC 驱动程序列表](../../data/odbc/odbc-driver-list.md)。  
  
## <a name="see-also"></a>请参阅  
 [开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)