---
title: "CDBErrorInfo::GetBasicErrorInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDBErrorInfo::GetBasicErrorInfo"
  - "ATL.CDBErrorInfo.GetBasicErrorInfo"
  - "CDBErrorInfo.GetBasicErrorInfo"
  - "ATL::CDBErrorInfo::GetBasicErrorInfo"
  - "GetBasicErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetBasicErrorInfo 方法"
ms.assetid: 263cec53-63f6-48fe-b46e-31d20251863e
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CDBErrorInfo::GetBasicErrorInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

调用 [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/en-us/library/ms723907.aspx) 返回有关错误的基本信息，如返回代码并提供程序特定错误号。  
  
## 语法  
  
```  
  
      HRESULT GetBasicErrorInfo(   
   ULONG ulRecordNum,   
   ERRORINFO* pErrorInfo    
) const throw( );  
```  
  
#### 参数  
 有关更多信息，请参见 [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/en-us/library/ms723907.aspx)在 *OLE DB 程序员参考* 中。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDBErrorInfo 类](../../data/oledb/cdberrorinfo-class.md)