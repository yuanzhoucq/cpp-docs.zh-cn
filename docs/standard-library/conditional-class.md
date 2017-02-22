---
title: "conditional 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::tr1::conditional"
  - "std.tr1.conditional"
  - "conditional"
  - "std.conditional"
  - "std::conditional"
  - "type_traits/std::conditional"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "conditional 类 [TR1]"
  - "conditional"
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# conditional 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根据指定的条件，从两种类型之中选择其中一种。  
  
## 语法  
  
```  
template <bool B, class T1, class T2>  
    struct conditional;  
  
template <bool _Test, class _T1, class _T2>  
    using conditional_t = typename conditional<_Test, _T1, _T2>::type;  
```  
  
#### 参数  
 `B`  
 用于确定所选类型的值。  
  
 `T1`  
 当 B 为 true 时的类型结果。  
  
 `T2`  
 当 B 为 false 时的类型结果。  
  
## 备注  
 当 `B` 的计算结果为 `true` 时，模板成员 typedef `conditional<B, T1, T2>::type` 的计算结果为 `T1`，当 `B` 的计算结果为 `false`，其计算结果为 `T2`。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)