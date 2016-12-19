---
title: "编译器错误 C2390 | Microsoft Docs"
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
  - "C2390"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2390"
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2390
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 不正确的存储类“specifier”  
  
 该存储类对于该全局范围标识符是无效的。  使用默认存储类替代了无效类。  
  
 可能的解决方案：  
  
-   如果该标识符是函数，则使用 `extern` 存储声明它。  
  
-   如果该标识符是形参或局部变量，则使用自动存储声明它。  
  
-   如果该标识符是全局变量，则在不使用存储类（自动存储）的情况下声明它。  
  
## 示例  
  
-   下面的示例生成 C2390：  
  
```  
// C2390.cpp  
register int i;   // C2390  
  
int main() {  
   register int j;   // OK  
}  
```