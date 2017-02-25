---
title: "Compiler Error C3278 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3278"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3278"
ms.assetid: 56f818f5-85a6-4792-843b-54fe16327658
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Compiler Error C3278
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

接口或纯方法“method”的直接调用将在运行时失败  
  
 对接口方法或纯方法进行了调用，这是不允许的。  
  
 以下示例生成 C3278：  
  
```  
// C3278_2.cpp  
// compile with: /clr  
using namespace System;  
interface class I  
{  
   void vmf();  
};  
  
public ref class C: public I  
{  
public:  
   void vmf()  
   {  
      Console::WriteLine( "In C::vmf()" );  
      I::vmf(); // C3278  
   }  
  
};  
  
int main()  
{  
   C^ pC = gcnew C;  
   pC->vmf();  
}  
```