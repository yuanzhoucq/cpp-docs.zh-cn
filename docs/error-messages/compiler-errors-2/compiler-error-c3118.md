---
title: "编译器错误 C3118 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3118"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3118"
ms.assetid: 40fbe681-8868-4cb2-a2b2-4db4449319a7
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3118
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“interface”: 接口不支持虚拟继承  
  
 您尝试从接口虚拟继承。  例如，  
  
```  
// C3118.cpp  
__interface I1 {  
};  
  
__interface I2 : virtual I1 {   // C3118  
};  
```  
  
 生成此错误。