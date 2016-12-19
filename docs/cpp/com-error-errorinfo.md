---
title: "_com_error::ErrorInfo | Microsoft Docs"
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
  - "_com_error::ErrorInfo"
  - "ErrorInfo"
  - "_com_error.ErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ErrorInfo 方法"
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::ErrorInfo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 检索传递给构造函数的 **IErrorInfo** 对象。  
  
## 语法  
  
```  
  
IErrorInfo * ErrorInfo( ) const throw( );  
  
```  
  
## 返回值  
 传入到构造函数中的原始 **IErrorInfo** 项。  
  
## 备注  
 检索 `_com_error` 对象中的封装 **IErrorInfo** 项，如果 **IErrorInfo** 项未记录，则返回 **NULL**。  使用完返回的对象后，调用方必须对该对象调用 **Release**。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_com\_error 类](../cpp/com-error-class.md)