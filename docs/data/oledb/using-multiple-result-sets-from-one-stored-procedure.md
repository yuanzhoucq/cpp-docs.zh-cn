---
title: "使用一个存储过程返回的多个结果集 | Microsoft Docs"
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
  - "多重结果集"
  - "存储过程, 返回结果集"
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 使用一个存储过程返回的多个结果集
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

大多数存储过程都返回多个结果集。  这样的存储过程通常包含一个或多个 Select 语句。  使用者需要考虑到这一点以便处理所有结果集。  
  
### 处理多个结果集  
  
1.  创建 `CCommand` 类，将 `CMultipleResults` 用作模板参数，同时使用所选择的访问器。  这通常是动态访问器或手动访问器。  如果使用其他类型的访问器，则可能无法确定每个行集合的输出列。  
  
2.  照常执行存储过程并绑定列（请参见[如何获取数据](../../data/oledb/fetching-data.md)）。  
  
3.  使用数据。  
  
4.  对 `CCommand` 类调用 `GetNextResult`。  如果还有其他可用的结果行集合，则 `GetNextResult` 返回 S\_OK，如果使用的是手动访问器，则应重新绑定列。  如果 `GetNextResult` 返回错误，则表示没有其他可用的结果集。  
  
## 请参阅  
 [使用存储过程](../../data/oledb/using-stored-procedures.md)