---
title: "DQ | Microsoft Docs"
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
  - "DQ"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DQ directive"
ms.assetid: 15de9c41-db90-4bca-affc-426eeb38ebc0
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# DQ
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

分配和 \(可选\) 初始化 8 个字节每 `initializer`的存储。  可以用作类型说明符任何位置类型是非法的。  `DQ` 是 [QWORD](../../assembler/masm/qword.md)同义词。  
  
## 语法  
  
```  
[[name]] DQ initializer [[, initializer]]...  
```  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)   
 [QWORD](../../assembler/masm/qword.md)