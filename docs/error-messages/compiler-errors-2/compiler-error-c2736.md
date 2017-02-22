---
title: "编译器错误 C2736 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2736"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2736"
ms.assetid: 95a6bc28-c0cb-49dc-87e6-e993dbbba881
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2736
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不允许在强制转换中使用“keyword”关键字  
  
 该关键字在转换中无效。  
  
 下面的示例生成 C2736：  
  
```  
// C2736.cpp  
int main() {  
   return (virtual) 0;   // C2736  
   // try the following line instead  
   // return 0;  
}  
```