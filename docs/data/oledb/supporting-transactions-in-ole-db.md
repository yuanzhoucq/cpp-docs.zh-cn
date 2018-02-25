---
title: "OLE DB 中支持事务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates [C++], transaction support
- transactions [C++], OLE DB support for
- nested transactions [C++]
- OLE DB [C++], transaction support
- databases [C++], transactions
- distributed transactions [C++]
ms.assetid: 3d72e583-ad38-42ff-8f11-e2166d60a5a7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 84849b2d9bfd899a0ffd8a5d8eafe12f91a4adce
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="supporting-transactions-in-ole-db"></a>在 OLE DB 中支持事务
A[事务](../../data/transactions-mfc-data-access.md)是组，或批处理，一系列与数据源的更新，以便所有成功并同时提交，或 （如果任何之一失败） 会提交任何一种方法并回滚整个事务。 此过程可确保数据源上的结果的完整性。  
  
 OLE DB 提供以下三种方法支持事务：  
  
-   [ITransactionLocal::StartTransaction](https://msdn.microsoft.com/en-us/library/ms709786.aspx)  
  
-   [ITransaction::Commit](https://msdn.microsoft.com/en-us/library/ms713008.aspx)  
  
-   [ITransaction::Abort](https://msdn.microsoft.com/en-us/library/ms709833.aspx)  
  
## <a name="relationship-of-sessions-and-transactions"></a>会话和事务之间的关系  
 单个数据源对象可以创建一个或多个会话对象，其中每个可以是内部或外部事务在给定时间范围。  
  
 如果会话未进入事务，则在每个方法调用后立即提交对数据存储在该会话中所做的所有工作。 （这有时称为自动提交模式或隐式的模式。）  
  
 当会话进入事务时，对数据存储在该会话中所做的所有工作是该事务的一部分并提交或中止作为单个单元。 （这有时称为手动提交模式。）  
  
 事务支持是特定于提供程序。 如果你使用的提供程序支持事务，支持会话对象**itransaction::**和**ITransactionLocal**可以输入一个简单 (即非嵌套) 事务。 OLE DB 模板类[CSession](../../data/oledb/csession-class.md)并支持这些接口，则在 Visual c + + 中实现的事务支持的建议的方法。  
  
## <a name="starting-and-ending-the-transaction"></a>起始和结束事务  
 你调用`StartTransaction`，**提交**，和**中止**中使用者中的行集对象的方法。  
  
 调用**ITransactionLocal::StartTransaction**启动新的本地事务。 当你启动事务时，由后续操作强制进行任何更改实际不适用于数据存储区之前提交事务。  
  
 调用**itransaction:: 提交**或**ITransaction::Abort**结束事务。 **提交**导致要应用到数据存储在事务范围内的所有更改。 **中止**在事务开始之前要取消的事务和数据存储区的作用域内的所有更改都处于状态它的原因。  
  
## <a name="nested-transactions"></a>嵌套的事务  
 A[嵌套事务](https://msdn.microsoft.com/en-us/library/ms716985.aspx)启动一个新的本地事务活动事务已在会话中存在时发生。 作为当前事务下的嵌套事务启动新事务。 如果提供程序不支持嵌套的事务，则调用`StartTransaction`会话上已活动事务时返回**XACT_E_XTIONEXISTS**。  
  
## <a name="distributed-transactions"></a>分布式事务  
 分布式的事务是指更新分布式的数据; 的事务也就是说，多个连网的计算机系统上的数据。 如果你想要支持分布式系统上的事务，则应使用.NET Framework 而不是 OLE DB 事务支持。  
  
## <a name="see-also"></a>请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)