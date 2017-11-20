---
title: "编译器错误 C3710 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3710
dev_langs: C++
helpviewer_keywords: C3710
ms.assetid: 18bec009-5b6f-464a-a21e-5d58a6936504
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fc39cd77bc9316024d0980be3a432e332f09cbb7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3710"></a>编译器错误 C3710
function： 不正确的语法，用于指定事件处理程序中 __hook /\__unhook  
  
 当你指定事件处理程序替换[__hook](../../cpp/hook.md)或[__unhook](../../cpp/unhook.md)，该处理程序必须是有效的方法。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3710  
  
```  
// C3710.cpp  
// compile with: /link /opt:noref  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlctl.h>  
#include <stdio.h>  
  
[event_source(native)]  
class CEventSrc  
{  
public:  
    __event void event1();  
};  
  
[event_receiver(native)]  
class CEventRec  
{  
public:  
    void handler1()  
    {  
        printf_s("Executing handler1().\n");  
    }  
  
    void HookEvents(CEventSrc* pSrc)   
    {  
        __hook(&CEventSrc::event1, pSrc, 0);   // C3710  
        // try the following line instead  
        // __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);  
    }  
  
    void UnhookEvents(CEventSrc* pSrc)  
    {  
        __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1);  
    }  
};  
  
int main()  
{  
    CEventSrc eventSrc;  
    CEventRec eventRec;  
    eventRec.HookEvents(&eventSrc);  
    eventSrc.event1();  
    eventRec.UnhookEvents(&eventSrc);  
}  
```