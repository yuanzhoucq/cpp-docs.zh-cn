---
title: "编译器错误 C3744 | Microsoft Docs"
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
  - "C3744"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3744"
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3744
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

对托管事件 \_\_unhook 必须有至少 3 个参数  
  
 在为 C\+\+ 托管扩展编译的程序中使用时，[\_\_unhook](../../cpp/unhook.md) 函数必须采用三个参数。  
  
 `__hook` 和 `__unhook` 与 \/clr 编程不兼容。  请改用 \+\= 和 \-\= 运算符。  
  
 只有使用 **\/clr:oldSyntax** 才可能出现 C3744 错误。  
  
 下面的示例生成 C3744：  
  
```  
// C3744.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
public __delegate void delegate1();  
  
[ event_source(managed) ]  
public __gc class CPSource {  
public:  
   __event delegate1* event1;  
};  
  
[event_receiver(managed)]  
public __gc class CReceiver {  
public:  
   void Handler1() {  
   }  
  
   void UnhookAll1(CPSource* pSrc, CReceiver* pRec) {  
      pRec;  
      __unhook(pSrc);   // C3744  
      // The following line resolves the error.  
      // __unhook(&CPSource::event1, pSrc, &CReceiver::Handler1);  
   }  
};  
  
int main() {  
}  
```