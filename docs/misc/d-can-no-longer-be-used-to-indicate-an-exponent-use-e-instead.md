---
title: "“D”不能再用来表示指数，请改用“E” | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30827"
  - "bc30827"
helpviewer_keywords: 
  - "BC30827"
ms.assetid: 577f8c0b-9e8a-433f-b504-9ddaa936c250
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “D”不能再用来表示指数，请改用“E”
“D”字符不能用来表示乘方。  
  
 **错误 ID：**BC30827  
  
### 更正此错误  
  
-   使用 `^` 运算符或 `E+` 字符以指示指数是否存在。 例如:  
  
    ```  
    Const Mole = 6.02E+23 ' Same as 6.02D23 Const Mole2 = 6.02 * 10 ^ 23 ' Same as 6.02D23  
    ```  
  
## 请参阅  
 [^ 运算符](../Topic/%5E%20Operator%20\(Visual%20Basic\).md)   
 [数值型数据类型](../Topic/Numeric%20Data%20Types%20\(Visual%20Basic\).md)