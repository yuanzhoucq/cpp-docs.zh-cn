---
title: "编译器错误 C3717 | Microsoft Docs"
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
  - "C3717"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3717"
ms.assetid: ae4fceb1-2583-4577-b2f1-40971a017055
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3717
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“method”: 不能定义激发事件的方法  
  
 您声明了包含实现的事件方法。  [\_\_event](../../cpp/event.md) 方法声明不能有定义。  若要修复此错误，请确保事件方法声明都没有定义。  例如，以下面的代码中，按注释的指示从 `event1` 声明中移除函数体。  
  
 下面的示例生成 C3717：  
  
```  
// C3717.cpp  
[event_source(native)]  
class CEventSrc {  
public:  
   __event void event1() {   // C3717  
   }  
  
   // remove definition for event1 and substitute following declaration  
   // __event void event1();  
};  
  
[event_receiver(native)]  
class CEventRec {  
public:  
   void handler1() {  
   }  
  
   void HookEvents(CEventSrc* pSrc) {  
      __hook(CEventSrc::event1, pSrc, CEventRec::handler1);  
   }  
  
   void UnhookEvents(CEventSrc* pSrc) {  
      __unhook(CEventSrc::event1, pSrc, CEventRec::handler1);  
   }  
};  
  
int main() {  
}  
```