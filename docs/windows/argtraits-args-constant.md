---
title: "ArgTraits::args 常量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::Details::ArgTraits::args"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "args 常量"
ms.assetid: a68100ab-254b-4571-a0bc-946f1633a46b
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ArgTraits::args 常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
static const int args = -1; ;  
```  
  
## 备注  
 数数目参数数量。委托接口的调用方法。  
  
## 备注  
 如果 `args` 等于时 \-1 指示不能具有调用最为匹配方法签名。  
  
## 要求  
 **标头：**event.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [ArgTraits 结构](../windows/argtraits-structure.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)