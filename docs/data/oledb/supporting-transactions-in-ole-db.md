---
title: 在 OLE DB 中支持事务
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB consumer templates [C++], transaction support
- transactions [C++], OLE DB support for
- nested transactions [C++]
- OLE DB [C++], transaction support
- databases [C++], transactions
- distributed transactions [C++]
ms.assetid: 3d72e583-ad38-42ff-8f11-e2166d60a5a7
ms.openlocfilehash: 647112f480f6470f7d893ecd1d5177618dc23708
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556258"
---
# <a name="supporting-transactions-in-ole-db"></a>在 OLE DB 中支持事务

一个[事务](../../data/transactions-mfc-data-access.md)是一种方法进行分组或批处理中一系列的数据源的更新，以便所有成功，同时提交，或者 （如果任何一个发生故障） 不会提交和回滚整个事务。 此过程可确保数据源的结果的完整性。

OLE DB 提供以下三种方法支持事务：

- [ITransactionLocal::StartTransaction](https://docs.microsoft.com/previous-versions/windows/desktop/ms709786(v=vs.85))

- [ITransaction::Commit](https://docs.microsoft.com/previous-versions/windows/desktop/ms713008(v=vs.85))

- [ITransaction::Abort](https://docs.microsoft.com/previous-versions/windows/desktop/ms709833(v=vs.85))

## <a name="relationship-of-sessions-and-transactions"></a>会话和事务之间的关系

单个数据源对象可以创建一个或多个会话对象，其中每个可以是内部或外部事务在给定时间范围内。

如果会话不会进入一个事务，在每个方法调用后立即提交对数据存储在该会话中所做的所有工作。 （这有时称为自动提交模式或隐式模式。）

当一个会话进入事务时，对数据存储在该会话中所做的所有工作是该事务的一部分并提交或中止作为单个单元。 （这有时称为手动提交模式。）

事务支持是特定于提供程序。 如果要使用的提供程序支持事务，支持的会话对象`ITransaction`和`ITransactionLocal`可以输入 （非嵌套） 事务。 OLE DB 模板类[CSession](../../data/oledb/csession-class.md)并支持这些接口，则在 Visual c + + 中实现事务支持的建议的方法。

## <a name="starting-and-ending-the-transaction"></a>起始和结束事务

在调用`StartTransaction`， `Commit`，和`Abort`使用者中的行集对象中的方法。

调用`ITransactionLocal::StartTransaction`启动一个新的本地事务。 启动事务时，由更高版本的操作强制进行任何更改不会应用到数据存储区中，直到提交事务。

调用`ITransaction::Commit`或`ITransaction::Abort`结束事务。 `Commit` 导致要应用于数据存储区的事务范围内的所有更改。 `Abort` 在事务启动之前，必须的使要取消的事务和数据存储区的范围内的所有更改将都保持在状态它。

## <a name="nested-transactions"></a>嵌套的事务

一个[transaction](https://docs.microsoft.com/previous-versions/windows/desktop/ms716985(v=vs.85))发生时启动新的本地事务在会话中存在活动事务。 作为当前事务下的嵌套事务启动新事务。 如果提供程序不支持嵌套的事务，则调用`StartTransaction`时已存在对该会话的活动事务返回 XACT_E_XTIONEXISTS。

## <a name="distributed-transactions"></a>分布式事务

分布式的事务是指更新分布式的数据; 一个事务也就是说，多个联网的计算机系统上的数据。 如果你想要在分布式系统中支持事务，则应使用.NET Framework 而不是 OLE DB 事务支持。

## <a name="see-also"></a>请参阅

[使用访问器](../../data/oledb/using-accessors.md)