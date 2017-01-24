---
title: "result_of 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "result_of"
  - "std.result_of"
  - "std::result_of"
  - "type_traits/std::result_of"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "result_of"
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# result_of 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

确定采用指定的参数类型的可调用类型的返回类型。  
  
## 语法  
  
```  
template <class Fn, class... ArgTypes>  
    struct result_of<Fn(ArgTypes...)>;  
```  
  
#### 参数  
 `Fn`  
 查询可调用类型。  
  
 `ArgTypes`  
 对查询的可调用类型参数列表的类型。  
  
## 备注  
 使用此模板可在编译时确定的结果类型 `Fn`\(`ArgTypes`\)，其中 `Fn` 调用时使用的参数列表中的类型是可调用类型 `ArgTypes`。`type` 的结果类型的模板类的成员名称 `decltype(INVOKE(declval<Fn>(), declval<ArgTypes>()...))` 如果未计算的表达式 `INVOKE(declval<Fn>(), declval<ArgTypes>()...)` 的格式是否正确。 否则，此模板类具有任何成员 `type`。 类型 `Fn` 和参数包中的所有类型 `ArgTypes` 必须是完整的类型， `void`, ，或未知绑定的数组。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)