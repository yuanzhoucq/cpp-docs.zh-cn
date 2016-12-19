---
title: "编译器错误 C2588 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2588"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2588"
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2588
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“::~identifier”: 非法的全局析构函数  
  
 为类、结构或联合以外的其他内容定义了析构函数。  这是不允许的。  
  
 在范围解析 \(`::`\) 运算符的左边缺少类名、结构名或联合名会引起此错误。  
  
 下面的示例生成 C2588：  
  
```  
// C2588.cpp  
~F();   // C2588  
```