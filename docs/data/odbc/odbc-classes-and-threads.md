---
title: ODBC 类和线程
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
ms.openlocfilehash: 8cb5df605bef31e177e976798f975bb4ca14ced7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213150"
---
# <a name="odbc-classes-and-threads"></a>ODBC 类和线程

从 MFC 4.2 开始，为 MFC ODBC 类提供多线程支持。 但请注意，MFC 不为 DAO 类提供多线程支持。

对 ODBC 类的多线程支持有一些限制。 由于这些类包装了 ODBC API，因此它们被限制为对其生成的组件的多线程支持。 例如，许多 ODBC 驱动程序不是线程安全的;因此，如果将 MFC ODBC 类与其中一个驱动程序一起使用，则它们不是线程安全的。 你应验证特定驱动程序是否是线程安全的。

创建多线程应用程序时，应非常小心地使用多个线程来处理相同的对象。 例如，在两个线程中使用同一个 `CRecordset` 对象可能会在检索数据时导致问题;一个线程中的提取操作可能会覆盖在另一个线程中提取的数据。 在单独的线程中，MFC ODBC 类更常见的用法是在各个线程之间共享一个打开的 `CDatabase` 对象以使用同一 ODBC 连接，每个线程中有一个单独的 `CRecordset` 对象。 请注意，不应将未打开的 `CDatabase` 对象传递到另一个线程中的 `CRecordset` 对象。

> [!NOTE]
>  如果必须有多个线程处理同一个对象，则应实现适当的同步机制，如关键部分。 请注意，某些操作（如 `Open`）不受保护。 应确保不会从单独的线程同时调用这些操作。

有关创建多线程应用程序的详细信息，请参阅[多线程主题](../../parallel/multithreading-support-for-older-code-visual-cpp.md)。

## <a name="see-also"></a>另请参阅

[开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[数据访问编程 (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)
