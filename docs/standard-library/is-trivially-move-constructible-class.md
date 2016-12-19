---
title: "is_trivially_move_constructible 类 | Microsoft Docs"
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
  - "is_trivially_move_constructible"
  - "std.is_trivially_move_constructible"
  - "std::is_trivially_move_constructible"
  - "type_traits/std::is_trivially_move_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_trivially_move_constructible"
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
caps.latest.revision: 11
caps.handback.revision: 1
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_trivially_move_constructible 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否具有普通移动构造函数。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_trivially_move_constructible;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 是一个具有普通移动构造函数的类，则类型谓词的实例为 true，否则为 false。  
  
 如果符合以下条件，则类 `Ty` 的移动构造函数为普通构造函数：  
  
 它被隐式声明  
  
 其参数类型等效于那些隐式声明的参数类型  
  
 类 `Ty` 没有虚函数  
  
 类 `Ty` 没有虚拟基  
  
 类没有任何不稳定的非静态数据成员  
  
 类 `Ty` 的所有直接基均具有普通构造函数  
  
 类类型的所有非静态数据成员的类具有普通构造函数  
  
 类的类型数组的所有非静态数据成员的类具有普通构造函数  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)