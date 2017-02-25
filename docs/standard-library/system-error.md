---
title: "&lt;system_error&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.<system_error>"
  - "std::<system_error>"
  - "<system_error>"
  - "system_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "system_error 标头"
ms.assetid: 5e046c6e-48d9-4740-8c8a-05f3727c1215
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# &lt;system_error&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包含标头定义异常类 `system_error` 和处理的低系统错误相关模板的 `<system_error>`。  
  
## 语法  
  
```  
#include <system_error>  
```  
  
### 对象  
  
|||  
|-|-|  
|[generic\_category](../Topic/generic_category.md)|表示一般错误的类别。|  
|[system\_category](../Topic/system_category.md)|表示低系统溢出引起的错误的类别。|  
  
### Typedef  
  
|||  
|-|-|  
|[generic\_errno](../Topic/generic_errno.md)|表示枚举的所有错误代码宏提供符号的类型由 `<errno.h>`中的 Posix 定义。|  
  
### 函数  
  
|||  
|-|-|  
|[make\_error\_code](../Topic/make_error_code.md)|创建一个 `error_code` 对象。|  
|[make\_error\_condition](../Topic/make_error_condition.md)|创建一个 `error_condition` 对象。|  
  
### 运算符  
  
|||  
|-|-|  
|[运算符\=\=](../Topic/operator==%20\(%3Csystem_error%3E\).md)|测试，如果运算符左侧的对象与右侧的对象相等。|  
|[运算符\!\=](../Topic/operator!=%20\(%3Csystem_error%3E\).md)|测试，如果运算符左侧的对象与右侧的对象不等于。|  
|[operator\<](../Topic/operator%3C%20\(%3Csystem_error%3E\).md)|测试，如果对象比为比较传入的对象较少。|  
  
### 枚举  
  
|||  
|-|-|  
|[errc](../Topic/errc%20Enumeration.md)|提供在`<errno.h>`由Posix定义的为错误代码的符号名。|  
  
### 类和结构  
  
|||  
|-|-|  
|[error\_category](../standard-library/error-category-class.md)|描述错误类别表示代码的抽象基，为对象。|  
|[error\_code](../standard-library/error-code-class.md)|表示为实现特定的低系统错误。|  
|[error\_condition](../standard-library/error-condition-class.md)|表示用户定义的错误代码。|  
|[is\_error\_code\_enum](../standard-library/is-error-code-enum-class.md)|表示测试枚举类型的谓词。[error\_code 类](../standard-library/error-code-class.md)|  
|[is\_error\_condition\_enum](../standard-library/is-error-condition-enum-class.md)|表示测试枚举类型的谓词。[error\_condition 类](../standard-library/error-condition-class.md)|  
|[system\_error](../standard-library/system-error-class.md)|所有表示引发的异常的基类。报告一个低系统溢出。|  
  
## 要求  
 **标头:** \<system\_error\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)