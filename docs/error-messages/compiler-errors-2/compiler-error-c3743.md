---
title: "编译器错误 C3743 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3743
dev_langs:
- C++
helpviewer_keywords:
- C3743
ms.assetid: 7ca9a76e-7b60-46d1-ab8b-18600cf1a306
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 71e35535a7e6c9916c6dd6ac563cfd5bdf76fbce
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3743"></a>编译器错误 C3743
可以仅挂钩/解除挂钩整个接口 event_receiver layout_dependent 参数为 true 时  
  
 [__Unhook](../../cpp/unhook.md)函数在它传递给的值将基于的参数的数目会有所不同`layout_dependent`中的参数[event_receiver](../../windows/event-receiver.md)类。  
  
 下面的示例生成 C3743:  
  
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
