---
title: "error_condition 类 | Microsoft Docs"
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
  - "system_error/std::error_condition"
  - "std::error_condition"
  - "error_condition"
  - "std.error_condition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "error_condition 类"
ms.assetid: 6690f481-97c9-4554-a0ff-851dc96b7a06
caps.latest.revision: 16
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# error_condition 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示用户定义的错误代码。  
  
## 语法  
  
```  
class error_condition;  
```  
  
## 备注  
 类型 `error_condition` 对象存储错误代码值和指向表示用于报告的用户定义的错误代码的对象。[category](../standard-library/error-category-class.md)  
  
### 构造函数  
  
|||  
|-|-|  
|[error\_condition](../Topic/error_condition::error_condition.md)|构造 `error_condition` 类型的对象。|  
  
### Typedef  
  
|||  
|-|-|  
|[value\_type](../Topic/error_condition::value_type.md)|表示存储区中的错误代码的值的类型。|  
  
### 成员函数  
  
|||  
|-|-|  
|[assign](../Topic/error_condition::assign.md)|分配错误代码值和类别。错误状态。|  
|[类别](../Topic/error_condition::category.md)|返回错误的类别。|  
|[clear](../Topic/error_condition::clear.md)|清除错误代码值和类别。|  
|[message](../Topic/error_condition::message.md)|返回了错误代码的名称。|  
  
### 运算符  
  
|||  
|-|-|  
|[运算符\=\=](../Topic/error_condition::operator==.md)|相等性测试在 `error_condition` 对象之间。|  
|[运算符\!\=](../Topic/error_condition::operator!=.md)|不相等性测试在 `error_condition` 对象之间。|  
|[operator\<](../Topic/error_condition::operator%3C.md)|测试，如果 `error_condition` 对象与 `error_code` 对象进行比较传入的是更少。|  
|[operator\=](../Topic/error_condition::operator=.md)|赋新的枚举值设置为 `error_condition` 对象。|  
|[布尔运算符](../Topic/error_condition::operator%20bool.md)|转换 `error_condition`类型的变量。|  
  
## 要求  
 **标头:** \<system\_error\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [error\_category 类](../standard-library/error-category-class.md)   
 [\<system\_error\>](../standard-library/system-error.md)