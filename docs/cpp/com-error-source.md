---
title: "_com_error::Source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_error.Source"
  - "_com_error::Source"
  - "source"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Source 方法"
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _com_error::Source
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 调用 **IErrorInfo::GetSource** 函数。  
  
## 语法  
  
```  
  
_bstr_t Source() const;  
  
```  
  
## 返回值  
 对于 `_com_error` 对象中记录的 **IErrorInfo** 对象，返回 **IErrorInfo::GetSource** 的结果。  生成的 BSTR 封装在 `_bstr_t` 对象中。  如果未记录 **IErrorInfo**，它将返回空 `_bstr_t`。  
  
## 备注  
 调用 **IErrorInfo::GetSource** 方法时的所有错误都将忽略。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_com\_error 类](../cpp/com-error-class.md)