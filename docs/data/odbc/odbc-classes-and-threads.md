---
title: ODBC 类和线程
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
ms.openlocfilehash: aaf54a3a1d616cde5742dad45955bd415f612d60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368687"
---
# <a name="odbc-classes-and-threads"></a>ODBC 类和线程

从 MFC 4.2 开始，MFC ODBC 类具有多线程支持。 但是请注意，MFC 不为 DAO 类提供多线程支持。

ODBC 类的多线程支持有一些限制。 由于这些类包装了 ODBC API，因此它们仅限于构建它们的组件的多线程支持。 例如，许多 ODBC 驱动程序不是线程安全的;因此，许多 ODBC 驱动程序并不安全。因此，如果将 MFC ODBC 类与其中一个驱动程序一起使用，则它们不是线程安全的。 您应该验证您的特定驱动程序是否为线程安全。

创建多线程应用程序时，在使用多个线程操作同一对象时应非常小心。 例如，在两个线程`CRecordset`中使用同一对象可能会导致检索数据时出现问题;因此，在两个线程中使用相同的对象可能会导致问题。一个线程中的提取操作可能会覆盖另一个线程中获取的数据。 在单独的线程中，MFC ODBC 类更常见的用途是跨线程共享`CDatabase`打开的对象，以使用相同的 ODBC 连接，每个线程中`CRecordset`都有单独的对象。 请注意，不应将未打开`CDatabase`的对象传递给另一个`CRecordset`线程中的对象。

> [!NOTE]
> 如果必须有多个线程操作同一对象，则应实现相应的同步机制，如关键部分。 请注意，某些操作（如`Open`）不受保护。 应确保这些操作不会同时从单独的线程调用。

有关创建多线程应用程序的详细信息，请参阅[多线程主题](../../parallel/multithreading-support-for-older-code-visual-cpp.md)。

## <a name="see-also"></a>另请参阅

[开放数据库连接 （ODBC）](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[数据访问编程 (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)
