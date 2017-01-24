---
title: "HStringReference::Operator== 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=="
dev_langs: 
  - "C++"
ms.assetid: cad3d52d-cd67-4194-a270-5239b1121a09
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HStringReference::Operator== 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示两个参数是否相等。  
  
## 语法  
  
```cpp  
  
inline bool operator==(  
               const HStringReference& lhs,   
               const HStringReference& rhs) throw()  
  
inline bool operator==(  
               const HSTRING& lhs,   
               const HStringReference& rhs) throw()  
  
inline bool operator==(  
               const HStringReference& lhs,   
               const HSTRING& rhs) throw()  
  
```  
  
#### 参数  
 `lhs`  
 要比较的第一个参数。  `lhs` 可以是 HStringReference 对象或 HSTRING 句柄。  
  
 `rhs`  
 要比较的第二个参数。`rhs` 可以是 HStringReference 对象或 HSTRING 句柄。  
  
## 返回值  
 如果 `lhs` 和 `rhs` 参数相等，则为 `true`；否则为 `false`。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [HStringReference 类](../windows/hstringreference-class.md)