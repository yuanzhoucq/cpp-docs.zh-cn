---
title: "编译器警告 （等级 1） C4683 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4683
dev_langs: C++
helpviewer_keywords: C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e0a8ca498a3c95a1b37229f6ac973cf74a8e28ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4683"></a>编译器警告（等级 1）C4683
**“**   
 ***函数*： 事件源具有输出的参数; 慎重操作时将多个事件处理程序挂钩**  
  
 如果多个事件接收器正在侦听的 COM 事件源，则可能会忽略输出参数的值。  
  
 请注意会在以下情况中发生内存泄漏：  
  
1.  如果方法具有输出参数内部分配，例如 BSTR *。  
  
2.  如果该事件具有多个处理程序 （是多路广播的事件）  
  
 泄漏的原因是，将设置多个处理程序，但只能由最后一个处理程序返回到调用站点的输出参数。  
  
 下面的示例生成 C4683:  
  
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