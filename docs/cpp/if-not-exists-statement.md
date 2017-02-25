---
title: "__if_not_exists 语句 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__if_not_exists"
  - "__if_not_exists_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__if_not_exists 关键字 [C++]"
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# __if_not_exists 语句
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`__if_not_exists` 语句测试指定的标识符是否存在。  如果该标识符不存在，则执行指定的语句块。  
  
## 语法  
  
```  
__if_not_exists ( identifier ) {   
statements  
};  
```  
  
#### 参数  
  
|参数|说明|  
|--------|--------|  
|`identifier`|要测试其存在性的标识符。|  
|`statements`|`identifier` 不存在时要执行的一个或多个语句。|  
  
## 备注  
  
> [!CAUTION]
>  若要实现最可靠的结果，请在以下约束条件下使用 `__if_not_exists` 语句。  
  
-   只将 `__if_not_exists` 语句应用于简单类型而不是模板。  
  
-   将 `__if_not_exists` 语句应用于类的内部或外部的标识符。  不要将 `__if_not_exists` 语句应用于局部变量。  
  
-   仅在函数的主体中使用 `__if_not_exists` 语句。  在函数主体的外部，`__if_not_exists` 语句仅能测试完全定义的类型。  
  
-   在测试重载函数时，不能测试特定形式的重载。  
  
 `__if_not_exists` 语句的补集为 [\_\_if\_exists](../cpp/if-exists-statement.md) 语句。  
  
## 示例  
 有关如何使用 `__if_not_exists` 的示例，请参阅 [\_\_if\_exists 语句](../cpp/if-exists-statement.md)。  
  
## 请参阅  
 [选择语句](../cpp/selection-statements-cpp.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [\_\_if\_exists 语句](../cpp/if-exists-statement.md)