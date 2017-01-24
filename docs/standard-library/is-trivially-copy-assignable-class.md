---
title: "is_trivially_copy_assignable | Microsoft Docs"
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
  - "is_trivially_copy_assignable"
  - "std.is_trivially_copy_assignable"
  - "std::is_trivially_copy_assignable"
  - "type_traits/std::is_trivially_copy_assignable"
dev_langs: 
  - "C++"
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
caps.latest.revision: 12
caps.handback.revision: 1
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_trivially_copy_assignable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否具有普通复制赋值运算符。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_trivially_copy_constructible;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 是具有普通复制赋值运算符的类，则类型谓词的实例为 true；否则为 false。  
  
 如果符合以下条件，类 `Ty` 的赋值构造函数为普通构造函数：  
  
 它被隐式提供  
  
 类 `Ty` 没有虚函数  
  
 类 `Ty` 没有虚拟基  
  
 类类型的所有非静态数据成员的类具有普通赋值运算符  
  
 类的类型数组的所有非静态数据成员的类具有普通赋值运算符  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)