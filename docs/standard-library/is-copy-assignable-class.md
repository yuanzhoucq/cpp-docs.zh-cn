---
title: "is_copy_assignable 类 | Microsoft Docs"
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
  - "is_copy_assignable"
  - "std.is_copy_assignable"
  - "std::is_copy_assignable"
  - "type_traits/std::is_copy_assignable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_copy_assignable"
ms.assetid: 3ae6bca1-85fb-4829-9ee9-0183b081ff50
caps.latest.revision: 12
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_copy_assignable 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试是否可以在赋值时复制类型。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_copy_assignable;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 是具有复制赋值运算符的类，则类型谓词的实例为 true；否则为 false。  等效于 is\_assignable\<Ty&, const Ty&\>。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)