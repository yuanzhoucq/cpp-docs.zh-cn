---
title: "UNION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "union"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "UNION directive"
ms.assetid: 52504abf-7dc1-47c5-944c-b886803a0c6a
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# UNION
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

声明一个或多个数据类型的联合。  *fielddeclarations* 必须是有效的数据定义。  省略在嵌套 **联合** 定义的 [结束](../../assembler/masm/ends-masm.md)*名称* 标签。  
  
## 语法  
  
```  
  
      name   
      UNION [[alignment]] [[, NONUNIQUE]]  
   fielddeclarations  
[[name]] ENDS  
```  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)