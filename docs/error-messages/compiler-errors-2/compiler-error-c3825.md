---
title: 编译器错误 C3825 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3825
dev_langs:
- C++
helpviewer_keywords:
- C3825
ms.assetid: 18e204a1-f26e-42c6-8d74-2b49cc95f940
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fdc3b612ea1ce7bdcf83c72350b4d13a6790d11f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049717"
---
# <a name="compiler-error-c3825"></a>编译器错误 C3825

class： 托管或 WinRTclass 可以仅支持托管或 WinRTevents

托管类中只支持 .NET 事件。 Windows 运行时类中只支持 Windows 运行时事件。 要在托管代码中修复此错误，请将 `event_source` 和 `event_receiver` 的类型参数从 `native` 更改为 `managed`。 或者，删除该属性。

## <a name="example"></a>示例

下面的示例生成 C3825，并演示如何修复此错误：

```
// C3825a.cpp
// compile with: /clr
public delegate void del1();

[event_source(native)]           // To fix, change 'native' to 'managed' or delete this line
ref class CEventSrc
{
public:
   event del1^ event1;       // C3825

   void FireEvents() {
      event1();
   }
};

[event_receiver(native)]         // To fix, change 'native' to 'managed' or delete this line
ref class CEventRec
{
public:
   void handler1()
   {
      System::Console::WriteLine("Executing handler1().\n");
   }
   void HookEvents(CEventSrc^ pSrc)
   {
      pSrc->event1 += gcnew del1(this, &CEventRec::handler1);
   }
   void UnhookEvents(CEventSrc^ pSrc)
   {
      pSrc->event1 -= gcnew del1(this, &CEventRec::handler1);
   }
};

int main()
{
   CEventSrc^ pEventSrc = gcnew CEventSrc;
   CEventRec^ pEventRec = gcnew CEventRec;
   pEventRec->HookEvents(pEventSrc);
   pEventSrc->FireEvents();
   pEventRec->UnhookEvents(pEventSrc);
}
```