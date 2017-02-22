---
title: "编译器错误 C2087 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2087"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2087"
ms.assetid: 89761e83-415a-4468-a4c6-b6dedfd1dd6a
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2087
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 缺少下标  
  
 具有多个下标的数组的定义缺少大于 1 的维度的下标值。  
  
 下面的示例生成 C2087：  
  
```  
// C2087.cpp  
int main() {  
   char a[10][];   // C2087  
}  
```  
  
 可能的解决方案：  
  
```  
// C2087b.cpp  
int main() {  
   char b[4][5];  
}  
```