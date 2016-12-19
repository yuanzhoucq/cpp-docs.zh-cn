---
title: "is_nothrow_default_constructible 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_nothrow_default_constructible"
  - "std.is_nothrow_default_constructible"
  - "std::is_nothrow_default_constructible"
  - "type_traits/std::is_nothrow_default_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_nothrow_default_constructible"
ms.assetid: c576fcc9-5be1-43aa-b93a-64d3f1848887
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_nothrow_default_constructible 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否具有非引发默认构造函数。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_nothrow_default_constructible;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 具有 nothrow 默认构造函数，类型谓词的实例将保留为 true，否则保留为 false。  类型谓词的实例等效于 `is_nothrow_constructible<Ty>`。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)