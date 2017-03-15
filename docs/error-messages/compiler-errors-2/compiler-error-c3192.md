---
title: "编译器错误 C3192 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3192"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3192"
ms.assetid: 8b0083d4-706f-46f6-858a-e1d9af464cf8
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3192
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

语法错误 :“^”不是前缀运算符\(是否希望使用“\*”?\)  
  
 句柄不能用作取消引用运算符。  
  
 下面的示例生成 C3192：  
  
```  
// C3192.cpp  
// compile with: /clr  
using namespace System;  
  
ref class MyClass {  
public:  
   MyClass () {}  
   MyClass(MyClass%) {}  
};  
  
int main() {  
   MyClass ^ s = gcnew MyClass;   
   MyClass b = ^s;   // C3192  
  
   // OK  
   MyClass b2 = *s;  
}  
```