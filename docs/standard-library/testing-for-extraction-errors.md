---
title: "测试提取错误 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "提取错误"
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 测试提取错误
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

处理函数的输出错误，讨论 [处理函数的错误](../standard-library/output-file-stream-member-functions.md)，适用于内容。  错误的测试在提取很重要。  考虑这条语句：  
  
```  
cin >> n;  
```  
  
 如果 `n` 是有符号整数，大于 32,767 的值 \(最大数量提供的值或 MAX\_INT\) 流设置的位 `fail` 和 `cin` 对象变为不可用。  任何后续的提取立即返回而存储的值。  
  
## 请参阅  
 [输入流](../standard-library/input-streams.md)