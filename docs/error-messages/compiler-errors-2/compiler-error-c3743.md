---
title: "编译器错误 C3743 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3743"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3743"
ms.assetid: 7ca9a76e-7b60-46d1-ab8b-18600cf1a306
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3743
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当 event\_receiver 的“layout\_dependent”参数为 true 时才能挂钩\/解除挂钩整个接口  
  
 根据向 [event\_receiver](../../windows/event-receiver.md) 类中的 `layout_dependent` 参数传递的值，[\_\_unhook](../../cpp/unhook.md) 函数采用的参数的数目有所不同。  
  
 下面的示例生成 C3743：  
  
```  
// C3743.cpp  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
[module(name="xx")];  
[object] __interface I { HRESULT f(); };  
  
[event_receiver(com, layout_dependent=true), coclass]  
struct R : I {  
        HRESULT f() {  
      return 0;  
   }  
        R() {  
   }  
  
   R(I* a) {  
      __hook(I, a, &R::f);   // C3743  
      // The following line resolves the error.  
      // __hook(I, a);  
   }  
};  
```