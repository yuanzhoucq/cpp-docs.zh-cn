---
title: "IColumnsInfoImpl::GetColumnInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetColumnInfo"
  - "ATL::IColumnsInfoImpl::GetColumnInfo"
  - "ATL.IColumnsInfoImpl.GetColumnInfo"
  - "ATL::IColumnsInfoImpl<T>::GetColumnInfo"
  - "IColumnsInfoImpl::GetColumnInfo"
  - "IColumnsInfoImpl<T>::GetColumnInfo"
  - "IColumnsInfoImpl.GetColumnInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetColumnInfo 方法"
ms.assetid: a6739a39-7402-496a-b544-a5b1ed05fadf
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IColumnsInfoImpl::GetColumnInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回大多数使用方需要的列元数据。  
  
## 语法  
  
```  
  
      STDMETHOD (GetColumnInfo)(  
   DBORDINAL* pcColumns,  
   DBCOLUMNINFO** prgInfo,  
   OLECHAR** ppStringsBuffer   
);  
```  
  
#### 参数  
 有关更多信息，请参见 [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx)（在 *OLE DB 程序员参考* 中）。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [IColumnsInfoImpl 类](../../data/oledb/icolumnsinfoimpl-class.md)   
 [IColumnsInfoImpl::MapColumnIDs](../../data/oledb/icolumnsinfoimpl-mapcolumnids.md)