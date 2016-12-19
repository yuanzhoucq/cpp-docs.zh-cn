---
title: "_com_error::ErrorMessage | Microsoft Docs"
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
  - "_com_error::ErrorMessage"
  - "_com_error.ErrorMessage"
  - "ErrorMessage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ErrorMessage 方法"
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::ErrorMessage
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 检索存储在 `_com_error` 对象中的 `HRESULT` 的字符串消息。  
  
## 语法  
  
```  
  
const TCHAR * ErrorMessage( ) const throw( );  
  
```  
  
## 返回值  
 返回在 `_com_error` 对象中记录的 `HRESULT` 的字符串消息。  如果 `HRESULT` 是映射的 16 位 [wCode](../cpp/com-error-wcode.md)，则返回一般消息“`IDispatch error #<wCode>`”。  如果未找到消息，则返回一般消息“`Unknown error #<hresult>`”。  返回的字符串是 Unicode 或多字节字符串，具体取决于 **\_UNICODE** 宏的状态。  
  
## 备注  
 检索在 `_com_error` 对象中记录的 `HRESULT` 的对应系统消息文本。  系统消息文本通过调用 Win32 [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351) 函数获取。  返回的字符串由 `FormatMessage` API 分配，并在销毁 `_com_error` 对象后释放。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_com\_error 类](../cpp/com-error-class.md)