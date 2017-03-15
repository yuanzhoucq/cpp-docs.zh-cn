---
title: "编译器错误 C2893 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2893"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2893"
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 编译器错误 C2893
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未能使函数模板“template name”专用化  
  
 编译器未能使函数模板专用化。  有多种原因可导致此错误。  
  
 通常，处理 C2893 错误的方法就是检查函数的签名，并确保可以实例化每个类型。  
  
## 示例  
 C2893 的发生是因为 `f` 的模板参数 `T` 被推导为 `std::map<int,int>`，但 `std::map<int,int>` 却没有 `data_type` 成员（`T::data_type` 不能使用 `T = std::map<int,int>` 实例化。）。  下面的示例生成 C2893。  
  
```  
// C2893.cpp  
// compile with: /c /EHsc  
#include<map>  
using namespace std;  
class MyClass {};  
  
template<class T>   
inline typename T::data_type  
// try the following line instead  
// inline typename  T::mapped_type  
f(T const& p1, MyClass const& p2);  
  
template<class T>  
void bar(T const& p1) {  
    MyClass r;  
    f(p1,r);   // C2893  
}  
  
int main() {  
   map<int,int> m;  
   bar(m);  
}  
```