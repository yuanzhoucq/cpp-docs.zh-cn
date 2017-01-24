---
title: "is_nothrow_move_assignable 类 | Microsoft Docs"
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
  - "is_nothrow_move_assignable"
  - "std.is_nothrow_move_assignable"
  - "std::is_nothrow_move_assignable"
  - "type_traits/std::is_nothrow_move_assignable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_nothrow_move_assignable"
ms.assetid: 000baa02-cbba-49de-9870-af730033348e
caps.latest.revision: 11
caps.handback.revision: 1
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_nothrow_move_assignable 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否具有 [nothrow](../cpp/nothrow-cpp.md) 移动赋值运算符。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_nothrow_move_assignable;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 具有 nothrow 移动赋值运算符，类型谓词的实例将为 true，否则为 false。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)