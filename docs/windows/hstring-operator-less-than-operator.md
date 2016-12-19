---
title: "HString::Operator&lt; 运算符 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HString::operator<"
dev_langs: 
  - "C++"
ms.assetid: 48a051cb-4609-42be-b48c-d35fc99d1eab
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HString::Operator&lt; 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示第一个参数是否小于第二个参数。  
  
## 语法  
  
```cpp  
  
inline bool operator<(  
    const HString& lhs,   
    const HString& rhs) throw()  
  
```  
  
#### 参数  
 `lhs`  
 要比较的第一个参数。  `lhs` 可以是对 HString 的引用。  
  
 `rhs`  
 要比较的第二个参数。  `rhs` 可以是对 HString 的引用。  
  
## 返回值  
 `true`，如果 `lhs` 参数大于；小于 `rhs` 参数否则，返回 `false`。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [HString 类](../windows/hstring-class.md)