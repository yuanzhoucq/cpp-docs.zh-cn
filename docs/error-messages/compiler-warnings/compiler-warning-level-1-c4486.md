---
title: "编译器警告（等级 1）C4486 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4486"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4486"
ms.assetid: 2c0c59e3-d025-4d97-8da2-fa27df1402fc
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# 编译器警告（等级 1）C4486
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: ref 类或值类的私有虚方法应标记为“sealed”  
  
 由于不能访问或重写托管类或结构的私有虚成员函数，因此应将其标记为 [sealed](../../windows/sealed-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C4486。  
  
```  
// C4486.cpp  
// compile with: /clr /c /W1  
ref class B {  
private:  
   virtual void f() {}   // C4486  
   virtual void f1() sealed {}   // OK  
};  
```  
  
## 示例  
 下面的示例演示一种可能使用私有的密封虚函数的情况。  
  
```  
// C4486_b.cpp  
// compile with: /clr /c  
ref class B {};  
  
ref class D : B {};  
  
interface class I {  
   B^ mf();  
};  
  
ref class E : I {  
private:  
   virtual B^ g() sealed = I::mf {  
      return gcnew B;  
   }  
  
public:  
   virtual D^ mf() {  
      return gcnew D;  
   }  
};  
```