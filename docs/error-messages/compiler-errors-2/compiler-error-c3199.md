---
title: "编译器错误 C3199 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3199"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3199"
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C3199
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用浮点 pragma 无效: 在非精确模式下不支持异常  
  
 [float\_control](../../preprocessor/float-control.md) 杂注用于在 [\/fp](../../build/reference/fp-specify-floating-point-behavior.md) 设置而非 **\/fp:precise** 设置下指定浮点异常模型。  
  
 下面的示例生成 C3199：  
  
```  
// C3199.cpp  
// compile with: /fp:fast  
#pragma float_control(except, on)   // C3199  
```