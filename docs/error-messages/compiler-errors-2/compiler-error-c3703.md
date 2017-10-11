---
title: "编译器错误 C3703 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3703
dev_langs:
- C++
helpviewer_keywords:
- C3703
ms.assetid: 7e3677d9-f2be-4c26-998f-423564e9023c
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: e6ef53628f3a24dd3e6f7f387491fc959d70aa04
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3703"></a>编译器错误 C3703
事件处理程序： 事件处理程序方法必须具有相同的存储类作为源 event  
  
 [事件](../../cpp/event-handling.md)具有不同的存储类它挂钩的事件处理程序。 例如，如果该事件处理程序的静态成员函数和事件不是静态的则会发生此错误。 若要修复此错误，给予事件和事件处理程序相同的存储类。  
  
 下面的示例生成 C3703:  
  
```  
// C3703.cpp  
// C3703 expected  
#include <stdio.h>  
  
[event_source(type=native)]  
class CEventSrc {  
public:  
   __event static void MyEvent();  
};  
  
[event_receiver(type=native)]  
class CEventHandler {  
public:  
   // delete the following line to resolve  
   void MyHandler() {}  
  
   // try the following line instead  
   // static void MyHandler() {}  
  
   void HookIt(CEventSrc* pSource) {  
      __hook(CEventSrc::MyEvent, pSource, &CEventHandler::MyHandler);  
   }  
  
   void UnhookIt(CEventSrc* pSource) {  
      __unhook(CEventSrc::MyEvent, pSource, &CEventHandler::MyHandler);  
   }  
};  
  
int main() {  
   CEventSrc src;  
   CEventHandler hnd;  
  
   hnd.HookIt(&src);  
   __raise src.MyEvent();  
   hnd.UnhookIt(&src);  
}  
```
