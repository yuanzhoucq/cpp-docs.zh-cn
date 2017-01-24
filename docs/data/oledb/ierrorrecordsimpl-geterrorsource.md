---
title: "IErrorRecordsImpl::GetErrorSource | Microsoft Docs"
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
  - "IErrorRecordsImpl.GetErrorSource"
  - "GetErrorSource"
  - "IErrorRecordsImpl::GetErrorSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetErrorSource 方法"
ms.assetid: 5436f1ce-c5a4-403b-a62b-c58e70e5c925
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IErrorRecordsImpl::GetErrorSource
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取导致从错误记录错误的源代码。  
  
## 语法  
  
```  
  
      LPOLESTR GetErrorSource(  
   ERRORINFO& rCurError   
);  
```  
  
#### 参数  
 `rCurError`  
 在 **IErrorInfo** 接口的 `ERRORINFO` 记录。  
  
## 返回值  
 到包含错误的源代码字符串的指针。  
  
## 要求  
 **标头：** atldb.h  
  
## 请参阅  
 [IErrorRecordsImpl 类](../../data/oledb/ierrorrecordsimpl-class.md)