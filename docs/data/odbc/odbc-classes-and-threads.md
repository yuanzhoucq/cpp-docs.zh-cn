---
title: "ODBC 类和线程 | Microsoft Docs"
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
  - "ODBC 类, 和线程"
  - "ODBC, 多线程应用程序"
  - "线程处理 [MFC], ODBC 支持"
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# ODBC 类和线程
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从 MFC 4.2 开始，提供对 MFC ODBC 类的多线程支持。  但是请注意，MFC 不提供对 DAO 类的多线程支持。  
  
 对 ODBC 类的多线程支持有一些限制。  因为这些类包装了 ODBC API，所以对 ODBC 类的多线程支持仅限于对它们所依赖的组件的多线程支持。  例如，许多 ODBC 驱动程序都不是线程安全的；因此如果 MFC ODBC 类和这样的一种驱动程序一起使用，这些类也不是线程安全的。  应该验证您的特定驱动程序是否是线程安全的。  
  
 创建多线程应用程序时，使用多线程处理同一对象一定要非常小心。  例如，在两个线程中使用同一 `CRecordset` 对象在检索数据时可能会引发问题；一个线程中的获取操作可能会覆盖在另一个线程中获取的数据。  MFC ODBC 类在单独的线程中的更常见用法是在这些线程中共享一个打开的 `CDatabase` 对象以使用同一个 ODBC 连接，而在每一个线程中都有单独的 `CRecordset` 对象。  注意不要将未打开的 `CDatabase` 对象传递给另一个线程中的 `CRecordset` 对象。  
  
> [!NOTE]
>  如果必须用多线程处理同一对象，则应该执行适当的同步机制，如临界区。  请注意对某些操作（如 **Open** 操作）没有提供保护。  您应该确保这些操作不会被单独的线程并行调用。  
  
 有关创建多线程应用程序的更多信息，请参见[多线程处理主题](../../parallel/multithreading-support-for-older-code-visual-cpp.md)。  
  
## 请参阅  
 [开放式数据库连接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)   
 [数据访问编程 \(MFC\/ATL\)](../../data/data-access-programming-mfc-atl.md)