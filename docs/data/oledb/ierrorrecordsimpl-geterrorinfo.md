---
title: "IErrorRecordsImpl::GetErrorInfo | Microsoft Docs"
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
  - "GetErrorInfo"
  - "IErrorRecordsImpl.GetErrorInfo"
  - "IErrorRecordsImpl::GetErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetErrorInfo 方法"
ms.assetid: 44d0872f-f25f-4102-8f7f-a2cfb3eeb1a0
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IErrorRecordsImpl::GetErrorInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回 [IErrorInfo](https://msdn.microsoft.com/en-us/library/ms718112.aspx) 中指定记录的接口指针。  
  
## 语法  
  
```  
  
      STDMETHOD( GetErrorInfo )(  
   ULONG ulRecordNum,  
   LCID lcid,  
   IErrorInfo **ppErrorInfo   
);  
```  
  
#### 参数  
 有关详细信息，请参阅在 *OLE DB 程序员参考* 中 [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx)。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IErrorRecordsImpl 类](../../data/oledb/ierrorrecordsimpl-class.md)