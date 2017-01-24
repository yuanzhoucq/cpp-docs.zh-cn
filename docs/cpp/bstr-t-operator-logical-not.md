---
title: "_bstr_t::operator ! | Microsoft Docs"
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
  - "_bstr_t::operator!"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "! 运算符"
  - "运算符 !, bstr"
  - "运算符!, bstr"
ms.assetid: 6e60b5a5-2d28-4eec-9e12-790da8f1fdd4
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t::operator !
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 检查封装的 `BSTR` 是否为 **NULL** 字符串。  
  
## 语法  
  
```  
  
bool operator!( ) const throw( );  
  
```  
  
## 返回值  
 如果是，则返回 **true**；如果不是，则返回 **false**。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_bstr\_t 类](../cpp/bstr-t-class.md)