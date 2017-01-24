---
title: "编译器错误 C3731 | Microsoft Docs"
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
  - "C3731"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3731"
ms.assetid: 45f89fcd-464c-4bc8-8a42-edcb5416d26c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3731
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

事件“function1”和处理程序“function2”不兼容；事件源和事件处理程序必须有相同的类型  
  
 事件源和事件接收器必须有相同的类型（例如 `native` 与`com` 类型）。  若要修复此错误，请使事件源和事件处理程序二者的类型匹配。  
  
 下面的示例生成 C3731：  
  
```  
// C3731.cpp  
// compile with: /clr  
#using <mscorlib.dll>  
[event_source(native)]  
struct A {  
   __event void MyEvent();  
};  
  
[event_receiver(managed)]  
// try the following line instead  
// [event_receiver(native)]  
struct B {  
   void func();  
   B(A a) {  
      __hook(&A::MyEvent, &a, &B::func);   // C3731  
   }  
};  
  
int main() {  
}  
```