---
title: "IRowsetNotifyCP::Fire_OnRowChange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetNotifyCP.Fire_OnRowChange"
  - "ATL.IRowsetNotifyCP.Fire_OnRowChange"
  - "Fire_OnRowChange"
  - "ATL::IRowsetNotifyCP::Fire_OnRowChange"
  - "IRowsetNotifyCP::Fire_OnRowChange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Fire_OnRowChange 方法"
ms.assetid: 6f9beed6-7a69-4c92-936f-422e98f3de5c
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetNotifyCP::Fire_OnRowChange
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

广播 [OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx) 事件到连接点 **IID\_IRowsetNotify** 上的所有侦听器通知消费者整行的一个更改影响列。  
  
## 语法  
  
```  
  
      HRESULT Fire_OnRowChange(  
   IRowset* pRowset,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBREASON eReason,  
   DBEVENTPHASE ePhase,  
   BOOL fCantDeny   
);  
```  
  
#### 参数  
 有关更多信息，请参见 *OLE DB Programmer's Reference*中的[IRowsetNotify::OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx)。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IRowsetNotifyCP 类](../../data/oledb/irowsetnotifycp-class.md)