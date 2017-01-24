---
title: "vector&lt;bool&gt;::reference::flip | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vector<bool>::reference::flip"
  - "std::vector<bool>::reference::flip"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reference::flip 方法"
ms.assetid: ef940365-cbe4-4a87-a3e2-1f3cfa357e29
caps.latest.revision: 21
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vector&lt;bool&gt;::reference::flip
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

反转引用的 [vector\<bool\>](../standard-library/vector-bool-class.md) 元素的布尔值。  
  
## 语法  
  
```  
void flip();  
```  
  
## 示例  
  
```cpp  
// vector_bool_ref_flip.cpp  
// compile with: /EHsc /W4  
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    cout << boolalpha;  
  
    vector<bool> vb = { true, false, false, true, true };  
  
    cout << "The vector is: " << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
  
    vector<bool>::reference vbref = vb.front();  
    vbref.flip();  
  
    cout << "The vector with first element flipped is: " << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
}  
  
```  
  
## 输出  
  
```  
The vector is:  
    true false false true true  
The vector with first element flipped is:  
    false false false true true  
```  
  
## 要求  
 **标头：**\<vector\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [vector\<bool\>::reference 类](../standard-library/vector-bool-reference-class.md)   
 [标准模板库](../misc/standard-template-library.md)