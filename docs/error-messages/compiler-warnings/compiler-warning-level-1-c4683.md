---
title: "编译器警告（等级 1）C4683 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4683"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4683"
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 编译器警告（等级 1）C4683
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**“**   
 ***function* ”: 事件源有“输出”参数；当挂起多个事件处理程序时会遇到警告**  
  
 如果不止一个事件接收器正在侦听 COM 事件源，则可能会忽略输出参数的值。  
  
 要注意，在下列情况中将发生内存泄漏：  
  
1.  如果方法具有内部分配的输出参数，如 BSTR \*。  
  
2.  如果该事件具有多个处理程序（为多路广播事件）  
  
 泄漏的原因是：输出参数将被多个处理程序设置，但仅由最后一个处理程序返回到调用站点。  
  
 下面的示例生成 C4683：  
  
```  
// C4683.cpp  
// compile with: /W1 /LD  
#define _ATL_ATTRIBUTES 1  
#include "atlbase.h"  
#include "atlcom.h"  
  
[ module(name="xx") ];  
  
[ object ]  
__interface I {  
   HRESULT f([out] int* pi);  
   // try the following line instead  
   // HRESULT f(int* pi);  
};  
  
[ coclass, event_source(com) ]  
struct E {  
   __event __interface I;   // C4683  
};  
```