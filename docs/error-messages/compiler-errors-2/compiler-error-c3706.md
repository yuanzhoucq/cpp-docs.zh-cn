---
title: 编译器错误 C3706
ms.date: 11/04/2016
f1_keywords:
- C3706
helpviewer_keywords:
- C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
ms.openlocfilehash: 2d474db5a4d50aed7b59e6f48fb5a3e8165f10c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468594"
---
# <a name="compiler-error-c3706"></a>编译器错误 C3706

function： 必须是一个 COM 接口激发 COM 事件

事件接口，用于激发 COM 事件必须是一个 COM 接口。 在此情况下，接口也应使用 Visual c + + 属性定义，或使用导入[#import](../../preprocessor/hash-import-directive-cpp.md)从 #import 的 embedded_idl 特性将类型库。

请注意，`#include`行下面的示例中所示的 ATL 标头文件是使用 COM 事件所必需的。 若要修复此错误，请`IEvents`（事件处理接口） 的 COM 接口，通过应用下列任一属性的接口定义：[对象](../../windows/object-cpp.md)，[双](../../windows/dual.md)，或[dispinterface](../../windows/dispinterface.md)。

如果接口是从由 MIDL 生成的标头文件，则编译器不就将其视为一个 COM 接口。

下面的示例生成 C3706:

```
// C3706.cpp
// compile with: /c
// C3706 expected
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(dll, name="idid", uuid="12341234-1234-1234-1234-123412341234")];

// Uncomment the following line to resolve.
// [object, uuid="12341234-1234-1234-1234-123412341237"]
__interface IEvents : IUnknown {
   HRESULT event1(/*[in]*/ int i);   // uncomment [in]
};

[dual, uuid="12341234-1234-1234-1234-123412341235"]
__interface IBase {
   HRESULT fireEvents();
};

[coclass, event_source(com), uuid="12341234-1234-1234-1234-123412341236"]
class CEventSrc : public IBase {
   public:
   __event __interface IEvents;

   HRESULT fireEvents() {
      HRESULT hr = IEvents_event1(123);
      return hr;
   }
};
```