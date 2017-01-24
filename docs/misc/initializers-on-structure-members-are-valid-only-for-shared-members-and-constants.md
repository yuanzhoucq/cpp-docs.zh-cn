---
title: "结构成员上的初始值设定项仅对“Shared”成员和常量有效 | Microsoft Docs"
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
  - "bc31049"
  - "vbc31049"
helpviewer_keywords: 
  - "BC31049"
ms.assetid: 8356978e-7f84-4932-be0f-dda005c9f8ca
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 结构成员上的初始值设定项仅对“Shared”成员和常量有效
结构成员变量已初始化为其声明的一部分。  
  
 **错误 ID：**BC31049  
  
### 更正此错误  
  
-   使用常量而非变量。  
  
-   将参数化构造函数添加到结构。 例如:  
  
    ```  
    Structure TestStruct Public t As Integer Sub New(ByVal Tval As Integer) t = Tval End Sub End Structure  
    ```  
  
## 请参阅  
 [如何：声明结构](../Topic/How%20to:%20Declare%20a%20Structure%20\(Visual%20Basic\).md)   
 [常量和枚举](../Topic/Constants%20and%20Enumerations%20in%20Visual%20Basic.md)