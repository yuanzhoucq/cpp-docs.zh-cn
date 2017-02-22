---
title: "is_rvalue_reference 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.is_rvalue_reference"
  - "is_rvalue_reference"
  - "std::tr1::is_rvalue_reference"
  - "std.is_rvalue_reference"
  - "std::is_rvalue_reference"
  - "type_traits/std::is_rvalue_reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_rvalue_reference 类 [TR1]"
  - "is_rvalue_reference"
ms.assetid: 40a97072-7b5c-4274-9154-298d3dcf064a
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# is_rvalue_reference 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否是右值引用。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_rvalue_reference;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 是[规则引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)引用，则此类型谓词的实例保存 true。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)