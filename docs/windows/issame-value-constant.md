---
title: "IsSame::value 常量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "internal/Microsoft::WRL::Details::IsSame::value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "value 常量"
ms.assetid: ee72deff-54a2-4482-9967-49a86d07f834
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# IsSame::value 常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
template <typename T1, typename T2>  
    struct IsSame  
    {  
        static const bool value = false;  
    };  
  
    template <typename T1>  
    struct IsSame<T1, T1>  
    {  
        static const bool value = true;  
    };  
  
```  
  
## 备注  
 指示某类型是否与另一个。  
  
 `value` 是 **true**，如果模板参数相同以及 **false**，如果模板参数不同。  
  
## 要求  
 **页眉：**internal.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [IsSame 结构](../windows/issame-structure.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)