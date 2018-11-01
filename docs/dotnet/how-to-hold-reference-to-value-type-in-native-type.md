---
title: 如何：在本机类型中保存对值类型的引用
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- value type reference in native type
- reference to value type in native type
ms.assetid: 1eabf8be-7d4f-4339-9027-48d5c4244483
ms.openlocfilehash: 1219dbac5ba78229554aeb29cf9422e835ea8343
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470438"
---
# <a name="how-to-hold-reference-to-value-type-in-native-type"></a>如何：在本机类型中保存对值类型的引用

使用`gcroot`装箱类型上要在本机类型中保存对值类型的引用。

## <a name="example"></a>示例

```
// reference_to_value_in_native.cpp
// compile with: /clr
#using <mscorlib.dll>
#include <vcclr.h>

using namespace System;

public value struct V {
   String ^str;
};

class Native {
public:
   gcroot< V^ > v_handle;
};

int main() {
   Native native;
   V v;
   native.v_handle = v;
   native.v_handle->str = "Hello";
   Console::WriteLine("String in V: {0}", native.v_handle->str);
}
```

```Output
String in V: Hello
```

## <a name="see-also"></a>请参阅

[使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)