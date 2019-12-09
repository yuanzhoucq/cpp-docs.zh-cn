---
title: 编译器错误 C3707
ms.date: 11/04/2016
f1_keywords:
- C3707
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
ms.openlocfilehash: 6faf035c0f4f68b10b187c56bea4cafc776998cf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757951"
---
# <a name="compiler-error-c3707"></a>编译器错误 C3707

"function"：调度接口方法必须有 dispid

如果使用 `dispinterface` 方法，则必须向其分配一个 `dispid`。 若要修复此错误，请将 `dispid` 分配给 `dispinterface` 方法，例如，通过取消注释下面的示例中方法的 `id` 特性。 有关详细信息，请参阅属性[调度接口](../../windows/dispinterface.md)和[id](../../windows/id.md)。

下面的示例生成 C3707：

```cpp
// C3707.cpp
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(name="xx")];
[dispinterface]
__interface IEvents : IDispatch
{
   HRESULT event1([in] int i);   // C3707
   // try the following line instead
   // [id(1)] HRESULT event1([in] int i);
};

int main() {
}
```
