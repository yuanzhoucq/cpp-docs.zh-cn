---
title: "IRowsetLocateImpl::GetRowsByBookmark | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetLocateImpl::GetRowsByBookmark"
  - "IRowsetLocateImpl.GetRowsByBookmark"
  - "GetRowsByBookmark"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetRowsByBookmark 方法"
ms.assetid: 07906e42-3582-427e-812a-aa19791e3c56
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetLocateImpl::GetRowsByBookmark
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提取与指定书签的一个或多个行。  
  
## 语法  
  
```  
  
      STDMETHOD ( GetRowsByBookmark )(  
   HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const DBBKMARK rgcbBookmarks[],  
   const BYTE* rgpBookmarks,  
   HROW rghRows[],  
   DBROWSTATUS* rgRowStatus[]   
);  
```  
  
#### 参数  
 `hReserved`  
 \[in\] `hChapter` 参数对应于 [IRowsetLocate::GetRowsByBookmark](https://msdn.microsoft.com/en-us/library/ms725420.aspx)。  
  
 有关其他参数，请参阅《*OLE DB 程序员参考》\) 中的*[IRowsetLocate::GetRowsByBookmark](https://msdn.microsoft.com/en-us/library/ms725420.aspx)。  
  
## 备注  
 书签可以是您定义或 OLE DB [标准书签](https://msdn.microsoft.com/en-us/library/ms712954.aspx) 值 \(**DBBMK\_FIRST** 或 **DBBMK\_LAST**\)。   不更改光标位置。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IRowsetLocateImpl 类](../../data/oledb/irowsetlocateimpl-class.md)   
 [IRowsetLocateImpl::GetRowsAt](../../data/oledb/irowsetlocateimpl-getrowsat.md)