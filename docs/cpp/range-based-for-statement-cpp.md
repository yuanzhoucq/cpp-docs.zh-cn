---
title: "基于范围的 for 语句 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 43ded324227878b44f997e6539e060145ad0fb66
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="range-based-for-statement-c"></a>基于范围的 for 语句 (C++)
对 `statement` 中的每个元素按顺序重复执行 `expression`。  
  
## <a name="syntax"></a>语法  
  
```  
  
      for ( for-range-declaration : expression )  
   statement   
```  
  
## <a name="remarks"></a>备注  
 使用基于范围的`for`语句构造必须在"范围"，吞吐量被定义为可循环访问的任何内容执行的循环 — 例如， `std::vector`，或其范围由定义的任何其他c++标准库序列`begin()`和`end()`。 `for-range-declaration` 部分中声明的名称是 `for` 语句是的本地名称，且无法在 `expression` 或 `statement` 中重新声明它。 请注意，[自动](../cpp/auto-cpp.md)关键字首选的中`for-range-declaration`语句部分。 

 **Visual Studio 自 2017 年中的新增功能：**基于范围的循环不再要求 begin （） 和 end （） 返回相同类型的对象。 这使得 end() 能够返回类似于 Ranges-V3 方案中定义的 ranges 所使用的那种 sentinel 对象。 有关详细信息，请参阅 [Generalizing the Range-Based For Loop](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html)（通用化基于范围的 for 循环）和 [range-v3 library on GitHub](https://github.com/ericniebler/range-v3)（GitHub 上的 range-v3 库）。
  
 此代码演示如何使用基于范围的`for`循环来循环访问数组和矢量：  
  
```cpp  
// range-based-for.cpp  
// compile by using: cl /EHsc /nologo /W4  
#include <iostream>  
#include <vector>  
using namespace std;  
  
int main()   
{  
    // Basic 10-element integer array.  
    int x[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };  
  
    // Range-based for loop to iterate through the array.  
    for( int y : x ) { // Access by value using a copy declared as a specific type.   
                       // Not preferred.  
        cout << y << " ";  
    }  
    cout << endl;  
  
    // The auto keyword causes type inference to be used. Preferred.  
  
    for( auto y : x ) { // Copy of 'x', almost always undesirable  
        cout << y << " ";  
    }  
    cout << endl;  
  
    for( auto &y : x ) { // Type inference by reference.  
        // Observes and/or modifies in-place. Preferred when modify is needed.  
        cout << y << " ";  
    }  
    cout << endl;  
  
    for( const auto &y : x ) { // Type inference by const reference.  
        // Observes in-place. Preferred when no modify is needed.  
        cout << y << " ";  
    }  
    cout << endl;  
    cout << "end of integer array test" << endl;  
    cout << endl;  
  
    // Create a vector object that contains 10 elements.  
    vector<double> v;  
    for (int i = 0; i < 10; ++i) {  
        v.push_back(i + 0.14159);  
    }  
  
    // Range-based for loop to iterate through the vector, observing in-place.  
    for( const auto &j : v ) {  
        cout << j << " ";  
    }  
    cout << endl;  
    cout << "end of vector test" << endl;  
}  
  
```  
  
 输出如下：  
  
 `1 2 3 4 5 6 7 8 9 10`  
  
 `1 2 3 4 5 6 7 8 9 10`  
  
 `1 2 3 4 5 6 7 8 9 10`  
  
 `1 2 3 4 5 6 7 8 9 10`  
  
 `end of integer array test`  
  
 `0.14159 1.14159 2.14159 3.14159 4.14159 5.14159 6.14159 7.14159 8.14159 9.14159`  
  
 `end of vector test`  
  
 基于范围的`for`循环将终止时其中一种在`statement`执行：[中断](../cpp/break-statement-cpp.md)，[返回](../cpp/return-statement-cpp.md)，或[goto](../cpp/goto-statement-cpp.md)到体外的标记语句基于范围的**为**循环。 A[继续](../cpp/continue-statement-cpp.md)中基于范围的语句`for`循环仅终止当前迭代。  
  
 请记住这些有关基于范围的 `for` 的情况：  
  
-   自动识别数组。  
  
-   识别拥有 `.begin()` 和 `.end()` 的容器。  
  
-   对于任何其他内容，使用依赖于参数的查找 `begin()` 和 `end()`。  
  
## <a name="see-also"></a>请参阅  
 [自动](../cpp/auto-cpp.md)   
 [迭代语句](../cpp/iteration-statements-cpp.md)   
 [关键字](../cpp/keywords-cpp.md)   
 [while Statement (C++)](../cpp/while-statement-cpp.md) （while 语句 (C++)）  
 [do-while 语句 (C++)](../cpp/do-while-statement-cpp.md)   
 [for 语句 (C++)](../cpp/for-statement-cpp.md)