---
title: "使用数组 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数组 [C++]"
ms.assetid: 7818a7fe-7e82-4881-a3d1-7d25162b7fc7
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用数组 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用数组下标操作符 （`[ ]`） 访问数组的各个元素。  如果在无下标表达式中使用一维数组，组名计算为指向该数组中的第一个元素的指针。  
  
```  
// using_arrays.cpp  
int main() {  
   char chArray[10];  
   char *pch = chArray;   // Evaluates to a pointer to the first element.  
   char   ch = chArray[0];   // Evaluates to the value of the first element.  
   ch = chArray[3];   // Evaluates to the value of the fourth element.  
}  
```  
  
 使用多维数组时，在表达式中使用各种组合。  
  
```  
// using_arrays_2.cpp  
// compile with: /EHsc /W1  
#include <iostream>  
using namespace std;  
int main() {  
   double multi[4][4][3];   // Declare the array.  
   double (*p2multi)[3];  
   double (*p1multi);  
  
   cout << multi[3][2][2] << "\n";   // C4700 Use three subscripts.  
   p2multi = multi[3];               // Make p2multi point to  
                                     // fourth "plane" of multi.  
   p1multi = multi[3][2];            // Make p1multi point to  
                                     // fourth plane, third row  
                                     // of multi.  
}  
```  
  
 在前面的代码中， `multi` 是类型 `double` 的一个三维数组。  `p2multi` 指针指向大小为三的 `double` 类型数组。  本例中该数组用于一个，两个和三个下标。  尽管指定所有下标更为常见（如 `cout` 语句所示），但是如下的语句 `cout` 所示，有时其在选择数组元素的特定子集时非常有用。  
  
## 请参阅  
 [数组](../cpp/arrays-cpp.md)