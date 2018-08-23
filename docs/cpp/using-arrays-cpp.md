---
title: 使用数组 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arrays [C++]
ms.assetid: 7818a7fe-7e82-4881-a3d1-7d25162b7fc7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ff0716359c715431f9887f50be06e592d57787e
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463907"
---
# <a name="using-arrays-c"></a>使用数组 (C++)
您可以使用数组下标运算符 (`[ ]`) 访问数组的各个元素。 如果一维数组用于无下标的表达式中，则数组名称的计算结果为一个指向该数组中第一个元素的指针。  
  
```cpp 
// using_arrays.cpp  
int main() {  
   char chArray[10];  
   char *pch = chArray;   // Evaluates to a pointer to the first element.  
   char   ch = chArray[0];   // Evaluates to the value of the first element.  
   ch = chArray[3];   // Evaluates to the value of the fourth element.  
}  
```  
  
 使用多维数组时，可以在表达式中使用各种组合。  
  
```cpp 
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
  
 在前面的代码中，`multi`是类型的三维数组**double**。 `p2multi`指针指向的类型数组**double**大小为三。 在此示例中，该数组与一个、两个和三个下标一起使用。 尽管更为常见的是指定所有下标（如在 `cout` 语句中），但有时选择数组元素的特定子集会很有用，如 `cout` 后面的语句中所示。  
  
## <a name="see-also"></a>请参阅  
 [数组](../cpp/arrays-cpp.md)