---
title: "IErrorRecordsImpl::GetErrorDescriptionString | Microsoft Docs"
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
  - "GetErrorDescriptionString"
  - "IErrorRecordsImpl.GetErrorDescriptionString"
  - "IErrorRecordsImpl::GetErrorDescriptionString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetErrorDescriptionString 方法"
ms.assetid: 8bc71c45-ca9f-4632-bb02-1aa9ed8086c4
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IErrorRecordsImpl::GetErrorDescriptionString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从错误的记录获取错误说明字符串。  
  
## 语法  
  
```  
  
      LPOLESTR GetErrorDescriptionString(  
   ERRORINFO& rCurError   
);  
```  
  
#### 参数  
 `rCurError`  
 在 **IErrorInfo** 接口的 `ERRORINFO` 记录。  
  
## 返回值  
 指向描述错误的字符串的指针。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [IErrorRecordsImpl 类](../../data/oledb/ierrorrecordsimpl-class.md)