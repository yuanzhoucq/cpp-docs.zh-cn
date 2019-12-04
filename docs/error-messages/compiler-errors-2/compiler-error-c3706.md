---
title: 编译器错误 C3706
ms.date: 11/04/2016
f1_keywords:
- C3706
helpviewer_keywords:
- C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
ms.openlocfilehash: 810ec59a814b04349913648fb49a03eb63912cd9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757977"
---
# <a name="compiler-error-c3706"></a>编译器错误 C3706

"function"：必须是用于激发 COM 事件的 COM 接口

用于激发 COM 事件的事件接口必须是 COM 接口。 在这种情况下，应使用视觉对象C++定义接口，或使用 #import 的 embedded_idl 属性的类型库中的[#import](../../preprocessor/hash-import-directive-cpp.md)导入接口。

请注意，以下示例中显示的 ATL 标头文件的 `#include` 行是使用 COM 事件所必需的。 若要修复此错误，请通过将以下属性之一应用于接口定义来使 `IEvents` （事件接口）成为 COM 接口： [object](../../windows/object-cpp.md)、[双重](../../windows/dual.md)或[调度](../../windows/dispinterface.md)接口。

如果接口来自 MIDL 生成的标头文件，则编译器将不会将其识别为 COM 接口。

下面的示例生成 C3706：

```cpp
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
