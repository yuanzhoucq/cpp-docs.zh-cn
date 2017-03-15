---
title: "bool (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "bool_cpp"
  - "bool"
  - "__BOOL_DEFINED"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__BOOL_DEFINED 宏"
  - "bool 关键字 [C++]"
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# bool (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此关键字是内置类型。  此类型的变量可以具有值 [true](../cpp/true-cpp.md) 和 [false](../cpp/false-cpp.md)。  条件表达式不仅具有类型 `bool`，还具有类型 `bool` 的值。  例如，`i!=0` 现在具有 **true** 或 **false**，具体取决于 `i` 的值。  
  
 值 **true**和 **false** 具有以下关系：  
  
```  
!false == true  
!true == false  
```  
  
 在下面的语句中：  
  
```  
if (condexpr1) statement1;   
```  
  
 如果 `condexpr1` 为 **true**，则始终执行 `statement1`；如果 `condexpr1` 为 **false**，则从不执行 `statement1`。  
  
 当后缀或前缀 `++` 运算符应用于类型 `bool` 的变量时，该变量将设置为 **true**。  后缀或前缀 `--` 运算符不能应用于此类型的变量。  
  
 `bool` 类型参与了整型提升。  类型 `bool` 的右值可以转换为类型 `int` 的右值，同时 **false** 会变为 0，且 **true** 会变为 1。  作为截然不同的类型，`bool` 参与重载决策。  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [基本类型](../cpp/fundamental-types-cpp.md)