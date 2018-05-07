---
title: ODBC 类和线程 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dedd1f03bf14e0513f9f76a1e292b9180e4d60db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="odbc-classes-and-threads"></a>ODBC 类和线程
从 MFC 4.2 开始，没有针对 MFC ODBC 类的多线程处理支持。 但是，请注意，MFC DAO 类不提供多线程处理支持。  
  
 ODBC 类的多线程处理支持具有一些限制。 这些类包装 ODBC API，因为它们被限制为在其它们由生成的组件的多线程处理支持。 例如，许多 ODBC 驱动程序不是线程安全的;因此，MFC ODBC 类不是线程安全如果将它们用于这些驱动程序之一。 你应验证是否是线程安全的特定驱动程序。  
  
 在创建多线程应用程序，你应非常小心使用多个线程来处理同一对象。 例如，使用相同`CRecordset`中两个线程对象检索数据时可能会导致问题; 一个线程中的提取操作可能会覆盖在其他线程中提取的数据。 单独的线程中的 MFC ODBC 类的更常见用法是共享打开`CDatabase`跨使用相同的 ODBC 连接中，有一个单独的线程对象`CRecordset`中每个线程对象。 请注意，您不应传递未打开`CDatabase`对象传递给`CRecordset`另一线程中的对象。  
  
> [!NOTE]
>  如果你必须拥有多个线程处理同一对象，则应实现相应的同步机制，例如临界区。 请注意，某些操作，如**打开**，未受保护。 你应确保，这些操作将不会调用同时从单独的线程。  
  
 有关创建多线程应用程序的详细信息，请参阅[多线程处理主题](../../parallel/multithreading-support-for-older-code-visual-cpp.md)。  
  
## <a name="see-also"></a>请参阅  
 [开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [数据访问编程 (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)