---
title: "使用 RDO RemoteData 控件更新数据 | Microsoft Docs"
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
  - "RDO RemoteData 控件"
  - "RDO RemoteData 控件, 更新数据"
  - "RemoteData 控件"
  - "RemoteData 控件, 更新数据"
ms.assetid: abb4175f-612e-4645-905e-c0fa918b0fd7
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 使用 RDO RemoteData 控件更新数据
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

RDO RemoteData 控件数据可以是只读的或可修改的。  
  
### 创建使用 RDO RemoteData 控件修改数据的应用程序  
  
1.  设置 RDO RemoteData 控件 **CursorDriver** 属性。  
  
    -   “服务器端”游标将返回的数据存储在服务器上。  
  
    -   “ODBC 客户端”游标将数据存储在客户端的本地存储区中。  
  
    -   “客户端批处理端”游标使用旨在处理并发问题的游标库。  
  
    -   执行操作查询时使用“无光标”选项，因此不需要游标。  
  
2.  设置 RDO RemoteData 控件 **LockType** 属性。  建议使用基于结果集选项的开放式并发。  
  
    -   如果希望数据可修改，不应使用只读并发。  
  
    -   保守式并发在更新期间锁定数据，使其他用户不会陷于提交不兼容数据更改的危险中。  
  
    -   开放式并发不锁定数据，但如果在提交期间它检测到另一个客户端已传递了不兼容状态，则 RDO RemoteData 控件引发错误。  
  
3.  设置 RDO RemoteData 控件 **ResultsetType** 属性。  确保 ODBC 驱动程序支持所选选项：  
  
    -   选择“创建静态游标”后，直到关闭并重新打开游标时才检测到更改。  
  
    -   选择“创建键集游标”后，游标允许在键集游标本身内随意进行插入、更新和删除。  
  
4.  根据需要设置数据绑定控件以允许更新。  注意某些控件不允许更新。  
  
 有关如何使用这些对象的信息，请参见 RDO RemoteData 控件的相关文档。  
  
## 请参阅  
 [RDO 数据绑定](../../data/ado-rdo/rdo-databinding.md)   
 [在 Visual C\+\+ 中使用 RDO 数据绑定](../../data/ado-rdo/using-rdo-databinding-in-visual-cpp.md)