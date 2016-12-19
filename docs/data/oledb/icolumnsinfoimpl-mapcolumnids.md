---
title: "IColumnsInfoImpl::MapColumnIDs | Microsoft Docs"
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
  - "IColumnsInfoImpl<T>::MapColumnIDs"
  - "MapColumnIDs"
  - "ATL::IColumnsInfoImpl::MapColumnIDs"
  - "IColumnsInfoImpl.MapColumnIDs"
  - "ATL::IColumnsInfoImpl<T>::MapColumnIDs"
  - "IColumnsInfoImpl::MapColumnIDs"
  - "ATL.IColumnsInfoImpl<T>.MapColumnIDs"
  - "ATL.IColumnsInfoImpl.MapColumnIDs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MapColumnIDs 方法"
ms.assetid: 7aa2d011-75ba-440a-bafe-ab8fccd16dfb
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IColumnsInfoImpl::MapColumnIDs
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回行集合中列序号的数组，这些列序号由指定的列 ID 标识。  
  
## 语法  
  
```  
  
      STDMETHOD (MapColumnIDs)(  
   DBORDINAL cColumnIDs,  
   const DBID rgColumnIDs[],  
   DBORDINAL rgColumns[]   
);  
```  
  
#### 参数  
 有关更多信息，请参见 *OLE DB 程序引用*中的[IColumnsInfo::MapColumnIDs](https://msdn.microsoft.com/en-us/library/ms714200.aspx)。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IColumnsInfoImpl 类](../../data/oledb/icolumnsinfoimpl-class.md)   
 [IColumnsInfoImpl::GetColumnInfo](../../data/oledb/icolumnsinfoimpl-getcolumninfo.md)