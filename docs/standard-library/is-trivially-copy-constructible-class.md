---
title: "is_trivially_copy_constructible 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_trivially_copy_constructible"
  - "std.is_trivially_copy_constructible"
  - "std::is_trivially_copy_constructible"
  - "type_traits/std::is_trivially_copy_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_trivially_copy_constructible"
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# is_trivially_copy_constructible 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否包含普通的复制构造函数。  
  
## 语法  
  
```  
template<class T>  
    struct is_trivially_copy_constructible;  
```  
  
#### 参数  
 `T`  
 要查询的类型。  
  
## 备注  
 如果类型 `T` 是具有普通复制构造函数的类，则类型谓词的实例为 true；否则为 false。  
  
 复制构造函数为类 `T` 非常简单，如果它隐式声明的该类 `T` 没有虚函数或虚拟基类，所有直接基的类 `T` 具有普通的复制构造函数、 类类型的所有非静态数据成员的类具有普通的复制构造函数和类的类型数组的所有非静态数据成员的类具有普通的复制构造函数。  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)