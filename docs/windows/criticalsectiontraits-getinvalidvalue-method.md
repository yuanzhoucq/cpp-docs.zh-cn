---
title: "CriticalSectionTraits::GetInvalidValue 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetInvalidValue 方法"
ms.assetid: 665f30a6-ca9c-4968-8c03-8f84e6b2329b
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# CriticalSectionTraits::GetInvalidValue 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

专用 CriticalSection 模板，以便模板中始终无效。  
  
## 语法  
  
```  
inline static Type GetInvalidValue();  
```  
  
## 返回值  
 始终返回指向无效关键部分。  
  
## 备注  
 *Type* 修饰符定义为 `typedef CRITICAL_SECTION* Type;`。  
  
## 要求  
 **标头：**corewrappers.h  
  
 Microsoft::WRL::Wrappers::HandleTraits **命名空间:**  
  
## 请参阅  
 [CriticalSectionTraits 结构](../windows/criticalsectiontraits-structure.md)