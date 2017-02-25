---
title: "编译器错误 C2203 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2203"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2203"
ms.assetid: 5497df43-86f6-43d5-b6cb-723c4c589b10
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2203
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

删除运算符不能指定数组的边界  
  
 利用 **\/Za** \(ANSI\) 选项，`delete` 运算符可以删除整个数组，但不能删除部分数组或数组的特定成员。  
  
 下面的示例生成 C2203：  
  
```  
// C2203.cpp  
// compile with: /Za  
int main() {  
   int *ar = new int[10];  
   delete [4] ar;   // C2203  
   // try the following line instead  
   // delete [] ar;  
}  
```