---
title: "IErrorRecordsImpl::GetCustomErrorObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IErrorRecordsImpl::GetCustomErrorObject"
  - "IErrorRecordsImpl::GetCustomErrorObject"
  - "ATL.IErrorRecordsImpl.GetCustomErrorObject"
  - "IErrorRecordsImpl.GetCustomErrorObject"
  - "GetCustomErrorObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCustomErrorObject 方法"
ms.assetid: 96d3549b-a49c-4552-94b2-71babaf1bf20
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IErrorRecordsImpl::GetCustomErrorObject
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回指针对自定义错误对象的接口。  
  
## 语法  
  
```  
  
      STDMETHOD( GetCustomErrorObject )(  
   ULONG ulRecordNum,  
   REFIID riid,  
   IUnknown **ppObject   
);  
```  
  
#### 参数  
 请参见 [IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/en-us/library/ms725417.aspx)（在 *OLE DB 程序员参考手册* 中）。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IErrorRecordsImpl 类](../../data/oledb/ierrorrecordsimpl-class.md)