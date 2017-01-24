---
title: "IErrorRecordsImpl::GetErrorParameters | Microsoft Docs"
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
  - "IErrorRecordsImpl::GetErrorParameters"
  - "ATL.IErrorRecordsImpl.GetErrorParameters"
  - "IErrorRecordsImpl.GetErrorParameters"
  - "GetErrorParameters"
  - "ATL::IErrorRecordsImpl::GetErrorParameters"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetErrorParameters 方法"
ms.assetid: 9bafac52-399e-4e0e-8365-b9f83074cdd5
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IErrorRecordsImpl::GetErrorParameters
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回错误参数。  
  
## 语法  
  
```  
  
      STDMETHOD( GetErrorParameters )(  
   ULONG ulRecordNum,  
   DISPPARAMS *pdispparams   
);  
```  
  
#### 参数  
 请参见 [IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/en-us/library/ms715793.aspx)（在 *OLE DB 程序员参考手册* 中）。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IErrorRecordsImpl 类](../../data/oledb/ierrorrecordsimpl-class.md)