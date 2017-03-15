---
title: "CDynamicAccessor::GetColumnInfo | Microsoft Docs"
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
  - "ATL.CDynamicAccessor.GetColumnInfo"
  - "ATL::CDynamicAccessor::GetColumnInfo"
  - "CDynamicAccessor.GetColumnInfo"
  - "CDynamicAccessor::GetColumnInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetColumnInfo 方法"
ms.assetid: 7f2102ea-b7cc-4714-812f-3ca2857f4b9a
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicAccessor::GetColumnInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回大多数使用方需要的列元数据。  
  
## 语法  
  
```  
  
      HRESULT GetColumnInfo(   
   IRowset* pRowset,   
   DBORDINAL* pColumns,   
   DBCOLUMNINFO** ppColumnInfo,   
   OLECHAR** ppStringsBuffer    
) throw( );  
```  
  
#### 参数  
 `pRowset`  
 \[in\] 指向 [IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx)接口的指针。  
  
 *pColumns*  
 \[out\] 一个指向内存的指针，该内存用于返回行集合中的列数；此数字包括书签列（如果有书签列）。  
  
 *ppColumnInfo*  
 \[out\] 一个指向内存的指针，该内存用于返回  **DBCOLUMNINFO** 结构的数组。  请参见“DBCOLUMNINFO 在 *OLE DB 程序员参考》\) 中的*[IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) 生成”。  
  
 `ppStringsBuffer`  
 \[out\]一个指向内存的指针，该内存用于返回指向单个分配块内所有字符串值（在*columnid*内使用的名称或用作  *pwszName*的名称）的存储区的指针。  
  
## 返回值  
 标准`HRESULT` 值之一。  
  
## 备注  
 有关数据类型 **DBORDINAL**、**DBCOLUMNINFO**和 **OLECHAR**的信息，请参见在 *OLE DB 程序员参考》\) 中的*[IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)