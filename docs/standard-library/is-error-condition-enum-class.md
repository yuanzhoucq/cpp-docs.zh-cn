---
title: "is_error_condition_enum 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::is_error_condition_enum"
  - "std.is_error_condition_enum"
  - "is_error_condition_enum"
  - "system_error/std::is_error_condition_enum"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_error_condition_enum 类"
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# is_error_condition_enum 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示测试枚举类型的谓词。[error\_condition](../standard-library/error-condition-class.md)  
  
## 语法  
  
```  
template<_Enum>  
    class is_error_condition_enum;  
```  
  
## 备注  
 如果类型 `_Enum` 是枚举值适合存储在类型 `error_condition`对象，此 [类型谓词](../standard-library/type-traits.md) 实例应用。  
  
 添加专用化给用户定义类型的此类型是允许的。  
  
## 要求  
 **标头:** \<system\_error\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [\<system\_error\>](../standard-library/system-error.md)