---
title: "CXMLAccessor::GetXMLRowData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CXMLAccessor::GetXMLRowData"
  - "ATL.CXMLAccessor.GetXMLRowData"
  - "CXMLAccessor::GetXMLRowData"
  - "CXMLAccessor.GetXMLRowData"
  - "GetXMLRowData"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetXMLRowData 方法"
ms.assetid: 156b66e3-42fd-491c-8943-38cf5e36f687
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CXMLAccessor::GetXMLRowData
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

按行检索表的整个内容，如XML 格式的字符串数据。  
  
## 语法  
  
```  
  
      HRESULT GetXMLRowData(   
   CSimpleStringW& strOutput,   
   bool bAppend = false    
) throw( );  
```  
  
#### 参数  
 `strOutput`  
 \[out\] 缓冲包含检索表数据的引用。  数据格式化为字符串数据使用与数据存储区列名匹配的XML标记名称。  
  
 *bAppend*  
 \[in\] 布尔值指定是否追加字符串到输出数据的末尾。  
  
## 返回值  
 标准`HRESULT` 值之一。  
  
## 备注  
 以下显示行数据如何在 XML 格式化。  下面的`DATA` 表示行数据。  使用移动方法移动到所需行。  
  
 `<row>`  
  
 `<column name>DATA</column name>`  
  
 `</row>`  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CXMLAccessor 类](../../data/oledb/cxmlaccessor-class.md)