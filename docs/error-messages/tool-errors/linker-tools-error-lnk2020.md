---
title: "链接器工具错误 LNK2020 | Microsoft Docs"
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
  - "LNK2020"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2020"
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK2020
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法解析的标记“token”  
  
 与未定义的外部错误类似，不同的是引用是通过元数据。  必须在元数据中定义所有函数和数据。  
  
 解决方案是：  
  
-   定义缺少的函数或数据，或者  
  
-   包括已在其中定义缺少的函数或数据的对象文件或库。  
  
## 示例  
 下面的示例生成 LNK2020。  
  
```  
// LNK2020.cpp  
// compile with: /clr /LD  
ref struct A {  
   A(int x);   // LNK2020  
   static int f();   // LNK2020  
};  
  
// OK  
ref struct B {  
   B(int x) {}  
   static int f() { return 0; }  
};  
```  
  
## 示例  
 如果创建托管模板类型的变量，也将发生 LNK2020，但同时不实例化该类型。  
  
 下面的示例生成 LNK2020。  
  
```  
// LNK2020_b.cpp  
// compile with: /clr   
  
template <typename T>  
ref struct Base {  
   virtual void f1() {};  
};  
  
template <typename T>  
ref struct Base2 {  
   virtual void f1() {};  
};  
  
int main() {  
   Base<int>^ p;   // LNK2020  
   Base2<int>^ p2 = gcnew Base2<int>();   // OK  
};  
```