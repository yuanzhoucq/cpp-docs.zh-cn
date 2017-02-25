---
title: "CRowset::IsSameRow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRowset::IsSameRow"
  - "CRowset.IsSameRow"
  - "IsSameRow"
  - "ATL::CRowset::IsSameRow"
  - "ATL.CRowset.IsSameRow"
  - "CRowset<TAccessor>::IsSameRow"
  - "ATL.CRowset<TAccessor>.IsSameRow"
  - "CRowset<TAccessor>.IsSameRow"
  - "ATL::CRowset<TAccessor>::IsSameRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsSameRow 方法"
ms.assetid: 53cba847-52f5-4dd9-973f-bbe7454c425c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CRowset::IsSameRow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将当前的行与指定的行进行比较。  
  
## 语法  
  
```  
  
      HRESULT IsSameRow(   
   HROW hRow    
) const throw( );  
```  
  
#### 参数  
 `hRow`  
 \[in\] 给比较的行的句柄为当前行。  
  
## 返回值  
 标准版`HRESULT`。  `S_OK` 指示行相同。  有关其他值，请参阅《*OLE DB 程序员参考》\) 中的*[IRowsetIndentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx) [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]中。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)