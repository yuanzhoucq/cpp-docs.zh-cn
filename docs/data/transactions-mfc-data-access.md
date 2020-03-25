---
title: 事务（MFC 数据访问）
ms.date: 11/04/2016
helpviewer_keywords:
- transactions [C++], support for
- transactions [C++]
- databases [C++], transactions
ms.assetid: f80afbfe-1517-4fec-8870-9ffc70a58b05
ms.openlocfilehash: 742e95d896d107fb89b3d65f0eeb6d418f1b2057
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209061"
---
# <a name="transactions--mfc-data-access"></a>事务（MFC 数据访问）

已开发出事务的概念以便根据一系列成功操作处理数据库结果状态的情况。 由于连续性操作可能修改先前操作的结果，因此可能会出现这种情况。 在这种情况下，如果任何一个操作失败，结果状态就有可能不确定。

要解决此问题，事务可以按以下这种方式对一系列操作进行分组，即以可以确定最后结果的完整性的这种方式分组。 所有操作必须成功，然后提交（写入到数据库），否则整个事务失败。 取消事务被称为回滚。 回滚允许恢复所做的更改，将数据库返回到事务前状态。

例如，在自动化银行事务中，如果将资金从帐户 A 转移到帐户 B，则从 A 取款和存入 B 的操作都必须成功以便正确处理款项，否则整个事务必须失败。

事务必须具有 ACID 属性，代表以下涵义：

- **原子**性事务是一个原子工作单元，只执行一次。所有工作都已完成，或者没有任何工作。

- **一致性**事务保留数据的一致性，将数据的一种一致状态转换为另一种一致的数据状态。 必须在语义上保留事务绑定的数据。

- **隔离**事务是一个隔离单元，每个都单独进行并独立于并发事务。 一个事务绝不可能看到另一个事务的中间阶段。

- **持久性**事务是恢复单元。 如果一个事务成功，它就会持续更新，即使该系统崩溃或已关闭。 如果事务失败，系统仍然处于之前提交事务的状态。

您可以在 OLE DB 中支持事务（请参阅[在 OLE DB 中支持事务](../data/oledb/supporting-transactions-in-ole-db.md)）或 ODBC （请参阅[Transaction （ODBC）](../data/odbc/transaction-odbc.md)）。

分布式事务是指更新分布式数据的事务，即多个连网计算机系统上的数据。 如果希望通过分布式系统支持事务，则应使用 ADO.NET，而不是 OLE DB 事务支持。

## <a name="see-also"></a>另请参阅

[数据访问编程 (MFC/ATL)](../data/data-access-programming-mfc-atl.md)
