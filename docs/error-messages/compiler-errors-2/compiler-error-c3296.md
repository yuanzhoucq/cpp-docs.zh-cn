---
title: 编译器错误 C3296
ms.date: 11/04/2016
f1_keywords:
- C3296
helpviewer_keywords:
- C3296
ms.assetid: fc4c9dcd-16cf-4eee-a1ac-c43e7c29e443
ms.openlocfilehash: 2e9787b063a5a37af8d0e0fdd04492a743792646
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588105"
---
# <a name="compiler-error-c3296"></a>编译器错误 C3296

“property”：已存在同名属性

编译器遇到具有相同名称的多个属性。 类型中的每个属性均必须具有唯一名称。

有关详细信息，请参阅 [property](../../windows/property-cpp-component-extensions.md)。

## <a name="example"></a>示例

以下示例生成 C3296。

```
// C3296.cpp
// compile with: /clr /c
using namespace System;

ref class R {
public:
   property int MyProp[int] { int get(int); }

   property String^ MyProp[int] { void set(int, String^); }   // C3296
};
```