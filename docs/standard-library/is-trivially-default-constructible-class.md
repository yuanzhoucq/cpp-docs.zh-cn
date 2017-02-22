---
title: "is_trivially_default_constructible 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_trivially_default_constructible"
  - "std.is_trivially_default_constructible"
  - "std::is_trivially_default_constructible"
  - "type_traits/std::is_trivially_default_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_trivially_default_constructible"
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# is_trivially_default_constructible 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否具有普通默认构造函数。  
  
## 语法  
  
```  
template<class Ty>  
    struct  is_trivially_default_constructible;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 是具有普通构造函数的类，则类型谓词的实例为 true；否则为 false。  
  
 类 `Ty` 的默认构造函数为普通构造函数，如果：  
  
-   它是一个隐式声明的默认构造函数  
  
-   类 `Ty` 没有虚函数  
  
-   类 `Ty` 没有虚拟基  
  
-   类 `Ty` 的所有直接基均具有普通构造函数  
  
-   类类型的所有非静态数据成员的类具有普通构造函数  
  
-   类的类型数组的所有非静态数据成员的类具有普通构造函数  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)