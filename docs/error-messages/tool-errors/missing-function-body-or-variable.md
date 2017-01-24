---
title: "缺少函数体或变量 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函数体"
  - "变量, 缺少"
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 缺少函数体或变量
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果只有函数原型，编译器继续运行而不会出现任何错误，但由于没有保留的函数代码或变量空间，链接器将无法解析地址调用。  只有创建对链接器必须解析的函数的调用时才会碰到此错误。  
  
## 示例  
 main 中的函数调用将导致 LNK2019，因为该原型会使编译器认为函数存在。而链接器发现它根本不存在。  
  
```  
// LNK2019_MFBV.cpp  
// LNK2019 expected  
void DoSomething(void);  
int main() {  
   DoSomething();  
}  
```  
  
## 示例  
 在 C\+\+ 中，确保在类定义中包括类的特定函数的实现，而不只是原型。  如果在头文件的外部定义类，则一定要在函数的前面包括类名 \(`Classname``::``memberfunction`\)。  
  
```  
// LNK2019_MFBV_2.cpp  
// LNK2019 expected  
struct A {  
   static void Test();  
};  
  
// Should be void A::Test() {}  
void Test() {}  
  
int main() {  
   A AObject;  
   AObject.Test();  
}  
```  
  
## 请参阅  
 [链接器工具错误 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)