---
title: "_com_error::operator = | Microsoft Docs"
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
  - "_com_error::operator="
  - "_com_error.operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "= 运算符, 具有特定的 Visual C++ 对象"
  - "运算符 = _com_error 对象"
  - "运算符 = _com_error 对象"
ms.assetid: b9cc4094-d055-450c-b45a-0a95317488f8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::operator =
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 将现有 `_com_error` 对象赋给另一个对象。  
  
## 语法  
  
```  
  
      _com_error& operator = (  
   const _com_error& that   
) throw ( );  
```  
  
#### 参数  
 `that`  
 一个 `_com_error` 对象。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_com\_error 类](../cpp/com-error-class.md)