---
title: "_com_error::HelpContext | Microsoft Docs"
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
  - "_com_error::HelpContext"
  - "HelpContext"
  - "_com_error.HelpContext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HelpContext 方法"
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::HelpContext
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 调用 **IErrorInfo::GetHelpContext** 函数。  
  
## 语法  
  
```  
  
DWORD HelpContext( ) const throw( );  
  
```  
  
## 返回值  
 对于 `_com_error` 对象中记录的 **IErrorInfo** 对象，返回 **IErrorInfo::GetHelpContext** 的结果。  如果未记录 **IErrorInfo** 对象，则它将返回零。  
  
## 备注  
 调用 **IErrorInfo::GetHelpContext** 方法时出现的任何失败都将被忽略。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_com\_error 类](../cpp/com-error-class.md)