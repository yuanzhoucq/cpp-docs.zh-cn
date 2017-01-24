---
title: "循环控制变量不能是属性或后期绑定索引数组 | Microsoft Docs"
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
  - "bc30039"
  - "vbc30039"
helpviewer_keywords: 
  - "BC30039"
ms.assetid: 63846449-b1df-4626-bf99-36fa9b187799
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 循环控制变量不能是属性或后期绑定索引数组
用于循环访问 `For` 循环的变量必须为数值数据类型。  
  
 **错误 ID：**BC30039  
  
### 更正此错误  
  
-   更改指定 `Integer`、`Short`、`Long`、`Byte`、`Single`、`Double` 或 `Decimal` 的循环控制变量的声明。  
  
## 请参阅  
 [For...Next 语句](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)