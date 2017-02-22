---
title: "IRowsetLocateImpl::Compare | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.IRowsetLocateImpl.Compare"
  - "IRowsetLocateImpl::Compare"
  - "IRowsetLocateImpl.Compare"
  - "ATL::IRowsetLocateImpl::Compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "“比较”方法"
ms.assetid: 6f84052c-c68c-480a-982f-03748faa7d5d
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetLocateImpl::Compare
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

比较两个书签。  
  
## 语法  
  
```  
  
      STDMETHOD ( Compare )(  
   HCHAPTER /* hReserved */,  
   DBBKMARK cbBookmark1,  
   const BYTE* pBookmark1,  
   DBBKMARK cbBookmark2,  
   const BYTE* pBookmark2,  
   DBCOMPARE* pComparison   
);  
```  
  
#### 参数  
 有关更多信息，请参见 [IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx) in the *OLE DB Programmer's Reference*。  
  
## 备注  
 书签之一可以是标准 OLE DB 定义的 [标准书签](https://msdn.microsoft.com/en-us/library/ms712954.aspx) \(**DBBMK\_FIRST**、**DBBMK\_LAST**或 **DBBMK\_INVALID**\)。  `pComparison` 中返回的值指示两个书签之间的关系：  
  
-   **DBCOMPARE\_LT** \(`cbBookmark1` 是 `cbBookmark2`之前。\)  
  
-   **DBCOMPARE\_EQ** \(`cbBookmark1` 与 `cbBookmark2`相等。\)  
  
-   **DBCOMPARE\_GT** `cbBookmark1` \(位于 `cbBookmark2`之后。\)  
  
-   **DBCOMPARE\_NE** \(书签不相等和排序。\)  
  
-   **DBCOMPARE\_NOTCOMPARABLE** \(书签不能比较。\)  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IRowsetLocateImpl 类](../../data/oledb/irowsetlocateimpl-class.md)