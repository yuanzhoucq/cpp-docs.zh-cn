---
title: "IRowsetNotifyCP::Fire_OnRowsetChange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Fire_OnRowsetChange"
  - "IRowsetNotifyCP::Fire_OnRowsetChange"
  - "IRowsetNotifyCP.Fire_OnRowsetChange"
  - "ATL::IRowsetNotifyCP::Fire_OnRowsetChange"
  - "ATL.IRowsetNotifyCP.Fire_OnRowsetChange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Fire_OnRowsetChange 方法"
ms.assetid: 412a9ec2-5041-4c56-acda-dc8f8e9b35f3
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetNotifyCP::Fire_OnRowsetChange
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

广播 [OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx) 事件到连接点 **IID\_IRowsetNotify** 上的所有侦听器通知消费者整行的一个更改影响。  
  
## 语法  
  
```  
  
      HRESULT Fire_OnRowsetChange(  
   IRowset* pRowset,  
   DBREASON eReason,  
   DBEVENTPHASE ePhase,  
   BOOL fCantDeny   
);  
```  
  
#### 参数  
 有关更多信息，请参见 *OLE DB 程序员参考* 中的 [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx)。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IRowsetNotifyCP 类](../../data/oledb/irowsetnotifycp-class.md)