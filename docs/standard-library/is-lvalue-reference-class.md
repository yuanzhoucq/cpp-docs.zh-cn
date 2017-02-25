---
title: "is_lvalue_reference 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.is_lvalue_reference"
  - "std::tr1::is_lvalue_reference"
  - "is_lvalue_reference"
  - "std.is_lvalue_reference"
  - "std::is_lvalue_reference"
  - "type_traits/std::is_lvalue_reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_lvalue_reference 类 [TR1]"
  - "is_lvalue_reference"
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# is_lvalue_reference 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否是左值引用。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_lvalue_reference;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 是对某个对象或函数的引用，此类型谓词的实例将为 true，否则为 false。  请注意，`Ty` 可能不是右值引用。  有关右值的详细信息，请参阅[规则引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)