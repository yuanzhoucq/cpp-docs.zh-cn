---
title: "_com_error::Description | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_error.Description"
  - "_com_error::Description"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Description 方法"
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _com_error::Description
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 调用 **IErrorInfo::GetDescription** 函数。  
  
## 语法  
  
```  
  
_bstr_t Description( ) const;  
  
```  
  
## 返回值  
 为在 `_com_error` 对象中记录的 **IErrorInfo** 对象返回结果 **IErrorInfo::GetDescription**。  生成的 `BSTR` 封装在 `_bstr_t` 对象中。  如果未记录 **IErrorInfo**，它将返回空 `_bstr_t`。  
  
## 备注  
 调用 **IErrorInfo::GetDescription** 函数并检索在 `_com_error` 对象中记录的 **IErrorInfo**。  调用 **IErrorInfo::GetDescription** 方法时将忽略所有错误。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_com\_error 类](../cpp/com-error-class.md)