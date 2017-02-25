---
title: "编译器错误 C3153 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3153"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3153"
ms.assetid: d775d97e-2480-484f-81f1-88406b10f947
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3153
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“interface”: 不能创建接口实例  
  
 不能实例化接口。  若要使用接口的成员，请从该接口派生类，实现接口成员，然后使用这些成员。  
  
 下面的示例生成 C3153：  
  
```  
// C3153.cpp  
// compile with: /clr  
interface class A {  
};  
  
int main() {  
   A^ a = gcnew A;   // C3153  
}  
```  
  
 下面的示例生成 C3153：  
  
```  
// C3153b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
__interface A {  
};  
  
int main() {  
   A *a = new A;   // C3153  
}  
```