---
title: "在 OLE DB 中支持事务 | Microsoft Docs"
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
  - "数据库 [C++], 事务"
  - "分布式事务 [C++]"
  - "嵌套事务 [C++]"
  - "OLE DB [C++], 事务支持"
  - "OLE DB 使用者模板 [C++], 事务支持"
  - "事务 [C++], OLE DB 支持"
ms.assetid: 3d72e583-ad38-42ff-8f11-e2166d60a5a7
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 在 OLE DB 中支持事务
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[事务](../../data/transactions-mfc-data-access.md)是一种对数据源的一系列更新进行分组或批处理以便当所有更新都成功时同时提交这些更新，或者如果任何一个更新失败则不提交任何更新并且回滚整个事务的方法。  此过程确保了数据源上结果的完整性。  
  
 OLE DB 通过下列三种方法支持事务：  
  
-   [\<caps:sentence id\="tgt4" sentenceid\="0699a86bb6d6316bff035b804a56f0aa" class\="tgtSentence"\>ITransactionLocal::StartTransaction\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms709786.aspx)  
  
-   [\<caps:sentence id\="tgt5" sentenceid\="39299b0fea086b86052550bd165334f7" class\="tgtSentence"\>ITransaction::Commit\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms713008.aspx)  
  
-   [\<caps:sentence id\="tgt6" sentenceid\="8e992150c28ae247d532408ca7828bfe" class\="tgtSentence"\>ITransaction::Abort\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms709833.aspx)  
  
## 会话和事务的关系  
 单个数据源对象可以创建一个或多个会话对象，每个会话对象都可以在给定时间位于事务范围内或范围外。  
  
 如果会话未进入事务，则在该会话中对数据存储区所做的所有工作都会在每个方法调用后立即提交。（这有时称为自动提交模式或隐式模式。）  
  
 如果会话进入事务，则在该会话中对数据存储区所做的所有工作都成为该事务的组成部分并作为单个单元提交或中止。（这有时称为手动提交模式。）  
  
 事务支持是特定于提供程序的。  如果所使用的提供程序支持事务，则支持 **ITransaction** 和 **ITransactionLocal** 的会话对象便可以进入简单（即非嵌套）的事务。  OLE DB 模板类 [CSession](../../data/oledb/csession-class.md) 支持这些接口，并且该类是一种在 Visual C\+\+ 中实现事务支持的推荐方法。  
  
## 启动和结束事务  
 在使用者的行集合对象中调用 `StartTransaction`、**Commit** 和 **Abort** 方法。  
  
 调用 **ITransactionLocal::StartTransaction** 将启动一个新的本地事务。  启动事务后，由随后的操作强制进行的任何更改只有在提交该事务时才会实际应用于数据存储区。  
  
 调用 **ITransaction::Commit** 或 **ITransaction::Abort** 将结束该事务。  **Commit** 使该事务范围内的所有更改都应用于数据存储区。  **Abort** 使该事务范围内的所有更改都被取消，并且数据存储区将保持在启动该事务之前的状态。  
  
## 嵌套事务  
 如果在会话中已经存在一个活动事务时启动一个新的本地事务，则发生[嵌套事务](https://msdn.microsoft.com/en-us/library/ms716985.aspx)。  新的事务将作为当前事务下的嵌套事务启动。  如果提供程序不支持嵌套事务，则在会话中已经存在一个活动事务时调用 `StartTransaction` 将返回 **XACT\_E\_XTIONEXISTS**。  
  
## 分布式事务  
 分布式事务是用于更新分布式数据（即位于一个以上网络计算机系统上的数据）的事务。  如果想在分布式系统中支持事务，则应使用 .NET Framework，而不是使用 OLE DB 事务支持。  
  
## 请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)