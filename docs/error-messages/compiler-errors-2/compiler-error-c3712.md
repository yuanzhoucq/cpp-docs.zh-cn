---
title: "编译器错误 C3712 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3712
dev_langs:
- C++
helpviewer_keywords:
- C3712
ms.assetid: 65b1fcaf-be89-4c55-9e40-25ec03457253
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 69f23d7192bc72f5f287a3a5b84b7840f9d25310
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3712"></a>编译器错误 C3712
method： 事件处理程序方法必须返回与源相同的类型 method  
  
 您定义未返回与源事件方法的类型相同的事件处理程序方法。 若要修复此错误，给予事件处理程序方法相同的源事件方法的返回类型。  
  
 下面的示例生成 C3712:  
  
```  
// C3712.cpp  
// compile with: /c  
[event_source(native)]  
class CEventSrc {  
public:  
   __event void event1();  
};  
  
[event_receiver(native)]  
class CEventRec {  
public:  
   int handler1() { return 0; }  
   // try the following line instead  
   // void handler1() {}  
  
   void HookEvents(CEventSrc* pSrc) {  
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3712  
   }  
   void UnhookEvents(CEventSrc* pSrc) {  
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3712  
   }  
};  
```
