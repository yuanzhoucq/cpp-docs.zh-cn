---
title: "CXMLAccessor::GetXMLColumnData | Microsoft Docs"
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
  - "ATL.CXMLAccessor.GetXMLColumnData"
  - "CXMLAccessor::GetXMLColumnData"
  - "CXMLAccessor.GetXMLColumnData"
  - "ATL::CXMLAccessor::GetXMLColumnData"
  - "GetXMLColumnData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetXMLColumnData 方法"
ms.assetid: 719e8efe-8758-4af7-a855-0e44ea196546
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CXMLAccessor::GetXMLColumnData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

按列检索表的列信息，XML 格式的字符串数据。  
  
## 语法  
  
```  
  
      HRESULT GetXMLColumnData(   
   CSimpleStringW& strOutput    
) throw( );  
```  
  
#### 参数  
 `strOutput`  
 \[out\] 为包含列信息的字符串缓冲区的引用中检索。  字符串格式的 XML 符合数据存储区的列名匹配的标记名称。  
  
## 返回值  
 标准`HRESULT` 值之一。  
  
## 备注  
 下面演示列信息在 XML 格式。  `type` 指定列的数据类型。  注意数据类型基于数据库的 OLE DB 数据类型，而不是访问的那些。  
  
 `<columninfo>`  
  
 `<column type = I2/> ColumnName`  
  
 `</columninfo>`  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CXMLAccessor 类](../../data/oledb/cxmlaccessor-class.md)