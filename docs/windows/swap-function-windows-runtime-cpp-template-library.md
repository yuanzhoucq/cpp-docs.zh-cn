---
title: "Swap 函数（Windows 运行时 C++ 模板库） | Microsoft Docs"
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
  - "internal/Microsoft::WRL::Details::Swap"
dev_langs: 
  - "C++"
ms.assetid: ed134a08-ceb7-4279-aa02-a183c3a426ea
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Swap 函数（Windows 运行时 C++ 模板库）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
WRL_NOTHROW inline void Swap(  
   _Inout_ T& left,  
   _Inout_ T& right  
);  
```  
  
#### 参数  
 `left`  
 第一个参数。  
  
 `right`  
 第二个参数。  
  
## 返回值  
  
## 备注  
 交换两个指定参数的值。  
  
## 要求  
 **页眉：**internal.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)