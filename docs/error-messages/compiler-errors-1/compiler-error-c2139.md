---
title: "编译器错误 C2139 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2139"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2139"
ms.assetid: 31e047c0-5bf9-46c2-b6de-b627ea6a5768
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2139
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 未定义的类不允许作为编译器内部类型特征“trait”的参数  
  
 传递到类型特征的参数无效。  
  
 有关详细信息，请参阅[编译器使用类型特征支持](../../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C2139。  
  
```  
// C2139.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
template <class T>  
struct is_polymorphic {  
   static const bool value = __is_polymorphic(T);  
};  
  
class C;  
class D {};  
  
class E {  
public:  
   virtual void Test() {}  
};  
  
int main() {  
   cout << is_polymorphic<C>::value << endl;   // C2139  
   cout << is_polymorphic<D>::value << endl;   // OK  
   cout << is_polymorphic<E>::value << endl;   // OK  
}  
```