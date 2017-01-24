---
title: "is_trivially_move_assignable 类 | Microsoft Docs"
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
  - "is_trivially_move_assignable"
  - "std.is_trivially_move_assignable"
  - "std::is_trivially_move_assignable"
  - "type_traits/std::is_trivially_move_assignable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_trivially_move_assignable"
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
caps.latest.revision: 11
caps.handback.revision: 1
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_trivially_move_assignable 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否具有普通移动赋值运算符。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_trivially_move_assignable;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 是具有普通移动赋值运算符的类，则类型谓词的实例为 true；否则为 false。  
  
 如果符合以下条件，类 `Ty` 的移动赋值运算符是普通运算符：  
  
 它被隐式提供  
  
 类 `Ty` 没有虚函数  
  
 类 `Ty` 没有虚拟基  
  
 类类型的所有非静态数据成员的类具有普通移动赋值运算符  
  
 类的类型数组的所有非静态数据成员的类具有普通移动赋值运算符  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)