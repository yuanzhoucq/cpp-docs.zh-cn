---
title: "error_code 类 | Microsoft Docs"
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
  - "error_code"
  - "std.error_code"
  - "std::error_code"
  - "system_error/std::error_code"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "error_code 类"
ms.assetid: c09b4a96-cb14-4281-a319-63543f9b2b4a
caps.latest.revision: 17
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# error_code 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示为实现特定的低系统错误。  
  
## 语法  
  
```  
class error_code;  
```  
  
## 备注  
 类型 `error_code` 类存储对象错误代码值和指向表示错误代码 [category](../standard-library/error-category-class.md) 描述进行低系统错误报告的对象。  
  
### 构造函数  
  
|||  
|-|-|  
|[error\_code](../Topic/error_code::error_code.md)|构造 `error_code` 类型的对象。|  
  
### Typedef  
  
|||  
|-|-|  
|[value\_type](../Topic/error_code::value_type.md)|表示存储区中的错误代码的值的类型。|  
  
### 成员函数  
  
|||  
|-|-|  
|[assign](../Topic/error_code::assign.md)|分配错误代码值和类别。错误代码。|  
|[类别](../Topic/error_code::category.md)|返回错误的类别。|  
|[clear](../Topic/error_code::clear.md)|清除错误代码值和类别。|  
|[default\_error\_condition](../Topic/error_code::default_error_condition.md)|错误返回默认状态。|  
|[message](../Topic/error_code::message.md)|返回了错误代码的名称。|  
  
### 运算符  
  
|||  
|-|-|  
|[运算符\=\=](../Topic/error_code::operator==.md)|相等性测试在 `error_code` 对象之间。|  
|[运算符\!\=](../Topic/error_code::operator!=.md)|不相等性测试在 `error_code` 对象之间。|  
|[operator\<](../Topic/error_code::operator%3C.md)|测试，如果 `error_code` 对象与 `error_code` 对象进行比较传入的是更少。|  
|[operator\=](../Topic/error_code::operator=.md)|赋新的枚举值设置为 `error_code` 对象。|  
|[布尔运算符](../Topic/error_code::operator%20bool.md)|转换 `error_code`类型的变量。|  
  
## 要求  
 **标头:** \<system\_error\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [error\_category 类](../standard-library/error-category-class.md)   
 [\<system\_error\>](../standard-library/system-error.md)