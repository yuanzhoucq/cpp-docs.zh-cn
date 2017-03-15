---
title: "CriticalSectionTraits::Unlock 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Unlock 方法"
ms.assetid: 8fb382f5-6eda-407e-9673-71d77bda4962
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# CriticalSectionTraits::Unlock 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

专用 CriticalSection 模板，以便支持释放指定的临界区对象的所有权。  
  
## 语法  
  
```  
inline static void Unlock(  
   _In_ Type cs  
);  
```  
  
#### 参数  
 `cs`  
 与关键代码段对象的指针。  
  
## 备注  
 *Type* 修饰符定义为 `typedef CRITICAL_SECTION* Type;`。  
  
 有关更多信息，请参见“LeaveCriticalSection 函数”。Windows API 文档中“同步函数”一节。  
  
## 要求  
 **标头：**corewrappers.h  
  
 Microsoft::WRL::Wrappers::HandleTraits **命名空间:**  
  
## 请参阅  
 [CriticalSectionTraits 结构](../windows/criticalsectiontraits-structure.md)