---
title: "error_category 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::error_category"
  - "system_error/std::error_category"
  - "error_category"
  - "std.error_category"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "error_category 类"
ms.assetid: e0a71e14-852d-4905-acd6-5f8ed426706d
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# error_category 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示对象描述的错误代码类别的抽象的通用基。  
  
## 语法  
  
```  
class error_category;  
```  
  
## 备注  
 两个预定义的对象实现 `error_category`: [generic\_category](../Topic/generic_category.md) 和 [system\_category](../Topic/system_category.md)。  
  
### TypeDefs  
  
|||  
|-|-|  
|[value\_type](../Topic/error_category::value_type.md)|一种表示存储的错误代码值的类型。|  
  
### 成员函数  
  
|||  
|-|-|  
|[default\_error\_condition](../Topic/error_category::default_error_condition.md)|存储错误条件对象的错误代码值。|  
|[equivalent](../Topic/error_category::equivalent.md)|返回一个值，指定错误对象是否相等。|  
|[消息](../Topic/error_category::message.md)|返回指定的错误代码的名称。|  
|[name](../Topic/error_category::name.md)|返回该类别的名称。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\=\=](../Topic/error_category::operator==.md)|测试之间是否相等 `error_category` 对象。|  
|[operator\!\=](../Topic/error_category::operator!=.md)|测试是否不相等之间 `error_category` 对象。|  
|[operator\<](../Topic/error_category::operator%3C.md)|如果测试 [error\_category](../standard-library/error-category-class.md) 对象是早于 `error_category` 传入的对象进行比较。|  
  
## 要求  
 **标头：**\<system\_error\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<system\_error\>](../standard-library/system-error.md)