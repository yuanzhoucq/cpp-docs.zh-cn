---
title: "_com_error::HelpFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "HelpFile"
  - "_com_error::HelpFile"
  - "_com_error.HelpFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HelpFile 方法"
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _com_error::HelpFile
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 调用 **IErrorInfo::GetHelpFile** 函数。  
  
## 语法  
  
```  
  
_bstr_t HelpFile() const;  
  
```  
  
## 返回值  
 为 `_com_error` 对象中记录的 **IErrorInfo** 对象返回结果 **IErrorInfo::GetHelpFile**。  生成的 BSTR 封装在 `_bstr_t` 对象中。  如果未记录 **IErrorInfo**，它将返回空 `_bstr_t`。  
  
## 备注  
 调用 **IErrorInfo::GetHelpFile** 方法时会忽略所有失败。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_com\_error 类](../cpp/com-error-class.md)