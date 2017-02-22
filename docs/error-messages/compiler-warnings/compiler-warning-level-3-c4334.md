---
title: "编译器警告（等级 3）C4334 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4334"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4334"
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 3）C4334
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator”: 32 位移位的结果被隐式转换为 64 位\(是否希望进行 64 位移位?\)  
  
 32 位移位的结果被隐式转换为 64 位，编译器认为有意进行 64 位移位。若要解决此警告，请使用 64 位移位，或将移位结果显式强制转换为 64 位。  
  
## 示例  
 下面的示例生成 C4334。  
  
```  
// C4334.cpp  
// compile with: /W3 /c  
void SetBit(unsigned __int64 *p, int i) {  
   *p |= (1 << i);   // C4334  
   *p |= (1i64 << i);   // OK  
}  
```