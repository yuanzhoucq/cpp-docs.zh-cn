---
title: "IRowsetImpl::RestartPosition | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.IRowsetImpl.RestartPosition"
  - "IRowsetImpl::RestartPosition"
  - "RestartPosition"
  - "ATL::IRowsetImpl::RestartPosition"
  - "IRowsetImpl.RestartPosition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RestartPosition 方法"
ms.assetid: 14de66ef-8d2c-4404-adb6-3f6c74ac6cf1
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetImpl::RestartPosition
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重新定位一获取位置到其初始位置；即，在某位置集中首次创建。  
  
## 语法  
  
```  
  
      STDMETHOD( RestartPosition )(  
   HCHAPTER /* hReserved */   
);  
```  
  
#### 参数  
 有关更多信息，请参见*OLE DB 程序员参考*中的[IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx)。  
  
## 备注  
 行集位置未定义，直到调用 **GetNextRow**。  在行集中可以向后移动通过调用 [RestartPosition](#vcrefirowsetimplrestartposition) 然后获取或向后滚动。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IRowsetImpl 类](../../data/oledb/irowsetimpl-class.md)