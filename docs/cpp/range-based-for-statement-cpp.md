---
title: "基于范围的 for 语句 (C++) | Microsoft Docs"
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
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 基于范围的 for 语句 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

语句 `statement` 按顺序反复执行语句 `expression` 中的每个元素。  
  
## 语法  
  
```  
  
      for ( for-range-declaration : expression )  
   statement   
```  
  
## 备注  
 使用基于范围的 `for` 语句构造一个必须执行的循环范围,可以定义为任意一个循环访问,例如 `std::vector`,或者其他任意用 `begin()` 和 `end()`定义的范围。  命名在 `for-range-declaration` 语句是属于 `for` 的，不能在 `expression` 或 `statement`中再次声明。  请注意 [自动](../cpp/auto-cpp.md) 关键字是在 `for-range-declaration` 中部分语句的首选。  
  
 这段代码展示了如何使用 `for` 范围的循环来遍历数组和向量：  
  
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
  
    for( const auto &y : x ) { // Type inference by reference.  
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
  
 一个基于 `for` 循环终止于 `statement` 执行完成： [break](../cpp/break-statement-cpp.md)， [return](../cpp/return-statement-cpp.md)，或者 [goto](../cpp/goto-statement-cpp.md) 转到一个语句外的 **for** 循环  [continue](../cpp/continue-statement-cpp.md) 与语句终止当前 `for` 循环的迭代。  
  
 记住这些关于范围 `for` 的事实  
  
-   自动识别数组。  
  
-   识别那些有 `.begin()` 和 `.end()` 的容器。  
  
-   使用基于自变量的查找 `begin()` 和 `end()` 。  
  
## 请参阅  
 [auto](../cpp/auto-cpp.md)   
 [迭代语句](../cpp/iteration-statements-cpp.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [While 语句 \(C\+\+\)](../cpp/while-statement-cpp.md)   
 [do\-while 语句 \(C\+\+\)](../cpp/do-while-statement-cpp.md)   
 [for 语句 \(C\+\+\)](../cpp/for-statement-cpp.md)