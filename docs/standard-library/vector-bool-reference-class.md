---
title: "vector&lt;bool&gt;::reference 类 | Microsoft Docs"
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
  - "vector<bool>::reference"
  - "std::vector<bool>::reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vector<bool> reference 类"
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
caps.latest.revision: 22
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vector&lt;bool&gt;::reference 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`vector<bool>::reference` 类是 [vector\<bool\> 类](../standard-library/vector-bool-class.md)为模拟 `bool&` 而提供的一种代理类。  
  
## 备注  
 必须使用模拟引用，因为 C\+\+ 不允许直接引用位。  `vector<bool>` 每个元素只使用一个位，这可以使用此代理类来引用。  但是，引用模拟不会完成，原因是某些赋值无效。  例如，因为无法采用 `vector<bool>::reference` 对象的地址，所以下列使用 [vector\<bool\>::operator&#91;&#93;](../Topic/vector%3Cbool%3E::operator.md) 的代码是错误的：  
  
```cpp  
    vector<bool> vb;  
...  
    bool* pb = &vb[1]; // conversion error - do not use  
    bool& refb = vb[1];   // conversion error - do not use  
  
```  
  
### 成员函数  
  
|||  
|-|-|  
|[flip](../standard-library/vector-bool-reference-flip.md)|反转向量元素的布尔值。|  
|[operator bool](../standard-library/vector-bool-reference-operator-bool.md)|提供从 `vector<bool>::reference` 到 `bool` 的隐式转换。|  
|[operator\=](../standard-library/vector-bool-reference-operator-assign.md)|将布尔值赋给一个位，或将引用的元素所保存的值赋给一个位。|  
  
## 要求  
 **标头**：\<vector\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<vector\>](../standard-library/vector.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)