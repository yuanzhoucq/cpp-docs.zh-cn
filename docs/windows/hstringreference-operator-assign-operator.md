---
title: "HStringReference::Operator= 运算符 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator="
dev_langs: 
  - "C++"
ms.assetid: ea100ed3-e566-4c9e-b6a8-f296088dea9c
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HStringReference::Operator= 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将另一 HStringReference 对象的值移动至当前 HStringReference 对象。  
  
## 语法  
  
```cpp  
HStringReference& operator=(HStringReference&& other) throw()  
```  
  
#### 参数  
 `other`  
 现有 HStringReference 对象。  
  
## 备注  
 现有 `other` 对象的值复制到当前 HStringReference 对象，然后会销毁 `other` 对象。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [HStringReference 类](../windows/hstringreference-class.md)