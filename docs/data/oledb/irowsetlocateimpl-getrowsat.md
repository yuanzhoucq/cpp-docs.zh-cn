---
title: "IRowsetLocateImpl::GetRowsAt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetRowsAt"
  - "IRowsetLocateImpl.GetRowsAt"
  - "ATL::IRowsetLocateImpl::GetRowsAt"
  - "IRowsetLocateImpl::GetRowsAt"
  - "ATL.IRowsetLocateImpl.GetRowsAt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetRowsAt 方法"
ms.assetid: 6aeb09dc-3aa8-4729-97a8-144dd27063f7
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetLocateImpl::GetRowsAt
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取启动行与书签的偏移量指定的行。  
  
## 语法  
  
```  
  
      STDMETHOD ( GetRowsAt )(  
   HWATCHREGION /* hReserved1 */,  
   HCHAPTER hReserved2,  
   DBBKMARK cbBookmark,  
   const BYTE* pBookmark,  
   DBROWOFFSET lRowsOffset,  
   DBROWCOUNT cRows,  
   DBCOUNTITEM* pcRowsObtained,  
   HROW** prghRows   
);  
```  
  
#### 参数  
 有关更多信息，请参见  [IRowsetLocate::GetRowsAt](https://msdn.microsoft.com/en-us/library/ms723031.aspx) in the *OLE DB Programmer's Reference*。  
  
## 备注  
 从光标位置若要获取，请使用 [IRowset::GetRowsAt](https://msdn.microsoft.com/en-us/library/ms723031.aspx)。  
  
 `IRowsetLocateImpl::GetRowsAt` 不更改光标位置。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IRowsetLocateImpl 类](../../data/oledb/irowsetlocateimpl-class.md)   
 [IRowsetLocateImpl::GetRowsByBookmark](../../data/oledb/irowsetlocateimpl-getrowsbybookmark.md)