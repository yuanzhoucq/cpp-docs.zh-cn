---
title: "is_final 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_final"
  - "std.is_final"
  - "std::is_final"
  - "type_traits/std::is_final"
dev_langs: 
  - "C++"
  - "c++"
helpviewer_keywords: 
  - "is_final"
ms.assetid: 9dbad82f-6685-4909-94e8-98e4a93994b9
caps.latest.revision: 12
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_final 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否为标记的类类型 `final`。  
  
## 语法  
  
```  
template<class T>  
    struct is_final;  
```  
  
#### 参数  
 `T`  
 要查询的类型。  
  
## 备注  
 如果类型谓词的实例将为 true 类型 `T` 标记的类类型 `final`, ，否则为 false。 如果 `T` 是类类型，它必须是完整的类型。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [final 说明符](../cpp/final-specifier.md)