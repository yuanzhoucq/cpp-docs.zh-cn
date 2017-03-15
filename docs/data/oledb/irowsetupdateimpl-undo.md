---
title: "IRowsetUpdateImpl::Undo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.IRowsetUpdateImpl.Undo"
  - "ATL::IRowsetUpdateImpl::Undo"
  - "IRowsetUpdateImpl::Undo"
  - "IRowsetUpdateImpl.Undo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Undo 方法"
ms.assetid: f3dc7764-050c-4322-9b2f-9ca772a0fb88
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetUpdateImpl::Undo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

撤消对行的所有更改，因为最后获取或更新。  
  
## 语法  
  
```  
  
      STDMETHOD ( Undo )(  
   HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[ ],  
   DBCOUNTITEM* pcRowsUndone,  
   HROW** prgRowsUndone,  
   DBROWSTATUS** prgRowStatus   
);  
```  
  
#### 参数  
 `hReserved`  
 \[in\] 对应于 [IRowsetUpdate::Undo](https://msdn.microsoft.com/en-us/library/ms719655.aspx)的 `hChapter` 参数。  
  
 *pcRowsUndone*  
 \[out\] 对应于 [IRowsetUpdate::Undo](https://msdn.microsoft.com/en-us/library/ms719655.aspx)的 `pcRows` 参数。  
  
 *prgRowsUndone*  
 \[in\] 对应于 [IRowsetUpdate::Undo](https://msdn.microsoft.com/en-us/library/ms719655.aspx)*prgRows* 的参数。  
  
 有关其他参数，请参阅《*OLE DB 程序员参考》\) 中的*[IRowsetUpdate::Undo](https://msdn.microsoft.com/en-us/library/ms719655.aspx)。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [IRowsetUpdateImpl 类](../../data/oledb/irowsetupdateimpl-class.md)