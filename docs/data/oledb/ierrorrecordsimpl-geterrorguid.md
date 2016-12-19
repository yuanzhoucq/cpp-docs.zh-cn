---
title: "IErrorRecordsImpl::GetErrorGUID | Microsoft Docs"
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
  - "GetErrorGUID"
  - "IErrorRecordsImpl.GetErrorGUID"
  - "IErrorRecordsImpl::GetErrorGUID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetErrorGUID 方法"
ms.assetid: 42c00755-50e5-401a-8246-adef9de5ced2
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IErrorRecordsImpl::GetErrorGUID
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从错误的记录获取错误 GUID。  
  
## 语法  
  
```  
  
      REFGUID GetErrorGUID(  
   ERRORINFO& rCurError   
);  
```  
  
#### 参数  
 `rCurError`  
 在 **IErrorInfo** 接口的 `ERRORINFO` 记录。  
  
## 返回值  
 错误 GUID 的引用。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IErrorRecordsImpl 类](../../data/oledb/ierrorrecordsimpl-class.md)