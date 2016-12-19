---
title: "_com_error::GUID | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "GUID"
  - "_com_error.GUID"
  - "_com_error::GUID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GUID 方法"
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::GUID
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 调用 **IErrorInfo::GetGUID** 函数。  
  
## 语法  
  
```  
  
GUID GUID( ) const throw( );  
  
```  
  
## 返回值  
 对于 `_com_error` 对象中记录的 **IErrorInfo** 对象，返回 **IErrorInfo::GetGUID** 的结果。  如果未记录 **IErrorInfo** 对象，则返回 `GUID_NULL`。  
  
## 备注  
 忽略调用 **IErrorInfo::GetGUID** 方法时的任何错误。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_com\_error 类](../cpp/com-error-class.md)