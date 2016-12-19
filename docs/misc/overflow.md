---
title: "Overflow. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_OVERFLOW"
  - "vs.message.0x800A0097"
ms.assetid: 632387b9-be9c-4744-bcc5-842c45582347
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Overflow.
赋值超出了赋值目标的限制。  该错误通常发生在下列情况之一为真时：  
  
-   赋值、计算或数据类型转换的结果太大，以至于不能在那种类型变量允许的取值范围内表示。  
  
-   对属性的赋值超过了该属性可以接受的最大值。  
  
-   尝试在计算中使用一个数并且将该数转换成整数，但结果大于整数。  
  
### 更正此错误  
  
1.  将该数值赋给其类型能够支持更大数值范围的变量。  
  
     \- 或 \-  
  
     确保赋值在属性接受的赋值范围内。