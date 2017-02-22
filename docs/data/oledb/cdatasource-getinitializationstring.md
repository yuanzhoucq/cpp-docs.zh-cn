---
title: "CDataSource::GetInitializationString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CDataSource::GetInitializationString"
  - "CDataSource.GetInitializationString"
  - "GetInitializationString"
  - "CDataSource::GetInitializationString"
  - "ATL.CDataSource.GetInitializationString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetInitializationString 方法"
ms.assetid: 97134723-6e99-4004-a56d-ec57543dbf3b
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDataSource::GetInitializationString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索当前打开数据源的初始化字符串。  
  
## 语法  
  
```  
  
      HRESULT GetInitializationString(   
   BSTR* pInitializationString,   
   bool bIncludePassword = false    
) throw( );  
```  
  
#### 参数  
 *pInitializationString*  
 \[out\] 为初始化字符串的指针。  
  
 *bIncludePassword*  
 \[in\] **true**，如果字符串包含一个密码；为 **false**。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 发生的初始化字符串可用于以后重新打开此数据源的连接。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDataSource 类](../../data/oledb/cdatasource-class.md)