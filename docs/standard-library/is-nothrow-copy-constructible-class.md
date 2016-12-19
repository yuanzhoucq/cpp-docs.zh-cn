---
title: "is_nothrow_copy_constructible 类 | Microsoft Docs"
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
  - "is_nothrow_copy_constructible"
  - "std.is_nothrow_copy_constructible"
  - "std::is_nothrow_copy_constructible"
  - "type_traits/std::is_nothrow_copy_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_nothrow_copy_constructible"
ms.assetid: f13a0bea-63b1-492a-9a45-d445df35c282
caps.latest.revision: 22
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_nothrow_copy_constructible 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否具有 [nothrow](../cpp/nothrow-cpp.md) 复制构造函数。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_nothrow_copy_constructible;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 具有 nothrow 复制构造函数，则类型谓词的实例将保留为 true，否则保留为 false。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)