---
title: "输入流操控器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "输入流对象"
  - "输入流, 操控器"
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 输入流操控器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

许多器，如 [setprecision](../Topic/setprecision.md)，`ios` 类定义从而适用于内容。  当操控器数量少，但是，实际影响内容对象。  这些，最重要的是的基数移动、`dec`、`oct`和 `hex`，用于确定转换基本使用数字输入流。  
  
 在提取，`hex` 器使处理各输入的格式。  例如，c、C\#、0xc、0xC、0Xc 和 0XC 都被解释为十进制整数 12。  为 0 到 9，A 到 F、从 a 到 f、x 和 X 之外的任何字符终止数值转换。  将 `"124n5"` 转换为序列。[basic\_ios::fail](../Topic/basic_ios::fail.md) bit 集的数字 124。  
  
## 请参阅  
 [输入流](../standard-library/input-streams.md)