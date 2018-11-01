---
title: ODBC 类和线程
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
ms.openlocfilehash: 1d470e79ba5a6a73a30743a21da0462a6b89e7da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608164"
---
# <a name="odbc-classes-and-threads"></a>ODBC 类和线程

从 MFC 4.2 开始，没有对 MFC ODBC 类的多线程处理支持。 但是，请注意，MFC DAO 类不提供多线程处理支持。

ODBC 类的多线程处理支持具有一些限制。 这些类可封装 ODBC API，因为它们被限制为它们构建的组件的多线程处理支持。 例如，很多 ODBC 驱动程序不是线程安全的。因此，MFC ODBC 类不是线程安全如果使用这些驱动程序之一。 应验证您的特定驱动程序是否是线程安全。

创建多线程的程序时，你应非常小心使用多个线程来处理同一对象。 例如，使用的相同`CRecordset`检索数据时，两个线程中的对象可能会导致问题; 在一个线程中的提取操作可能会覆盖在其他线程中提取的数据。 单独的线程中的 MFC ODBC 类的更常见用法是共享一种开放`CDatabase`跨同一个 ODBC 连接使用一个单独的线程对象`CRecordset`中每个线程对象。 请注意，您不应传递未打开`CDatabase`对象传递给`CRecordset`另一线程中的对象。

> [!NOTE]
>  如果你必须拥有多个线程处理同一个对象，应实现合适的同步机制，如临界区。 请注意，某些操作，如`Open`，不受保护。 您应确保，这些操作不会调用同时从单独的线程。

有关创建多线程应用程序的详细信息，请参阅[多线程主题](../../parallel/multithreading-support-for-older-code-visual-cpp.md)。

## <a name="see-also"></a>请参阅

[开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[数据访问编程 (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)