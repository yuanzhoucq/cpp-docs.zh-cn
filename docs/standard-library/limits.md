---
title: "&lt;limits&gt; | Microsoft Docs"
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
  - "std.<limits>"
  - "std::<limits>"
  - "limits/std::<limits>"
  - "<limits>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "limits 标头"
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
caps.latest.revision: 18
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;limits&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义模板类 `numeric_limits` 以及两个有关浮点表示形式和舍入的枚举。  
  
## 语法  
  
```  
  
#include <limits>  
  
```  
  
## 备注  
 `numeric_limits` 类的显式专用化描述基本类型（包括字符、整数、浮点类型和由实现定义而非由 C\+\+ 语言规则固定的 `bool`）的许多属性。  \<limits\> 中描述的属性包括准确性、最小和最大尺寸表示形式、舍入和信号类型错误。  
  
### 枚举  
  
|||  
|-|-|  
|[float\_denorm\_style](../Topic/float_denorm_style.md)|此枚举描述实现可以选择用于表示非标准化浮点值的各种方法，这种浮点值由于太小而无法表示为规范化值：|  
|[float\_round\_style](../Topic/float_round_style.md)|此枚举描述实现可以选择用于将浮点值舍入为整数值的各种方法。|  
  
### 类  
  
|||  
|-|-|  
|[numeric\_limits 类](../standard-library/numeric-limits-class.md)|此模板类描述内置数值类型的算术属性。|  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)