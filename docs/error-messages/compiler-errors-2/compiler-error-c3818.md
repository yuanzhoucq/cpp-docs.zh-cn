---
title: "编译器错误 C3818 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3818"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3818"
ms.assetid: f9502f6a-0690-4135-ab88-cc97cf490f5c
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3818
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

数组属性声明“property1”不会重载索引属性“property2”  
  
 当一个属性是索引器，另一个属性是数组属性时，重载是不可能的。  有关更多信息，请参见 [\_\_property](../../misc/property.md)。  
  
 只有使用 **\/clr:oldSyntax** 才可能出现 C3818 错误。  
  
 下面的示例生成 C3818：  
  
```  
// C3818.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc class X {  
public:  
   __property int get_Int(int index) {  
      Console::WriteLine(S"Called indexed property");  
      return m_value;  
   }  
  
   __property int get_Int() __gc[] {   // C3818, rename a property  
      Console::WriteLine(S"Called array property");  
      return m_arr;  
   }  
  
   int m_arr __gc[];  
   int m_value;  
};  
  
int main() {  
   X* x = new X;  
   x->m_arr = new int __gc[3];  
   x->m_value = 3;  
  
   x->Int[0];  
}  
```