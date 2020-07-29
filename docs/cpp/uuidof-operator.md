---
title: __uuidof 运算符
ms.date: 10/10/2018
f1_keywords:
- __LIBID_cpp
- __uuidof_cpp
- __uuidof
- _uuidof
helpviewer_keywords:
- __uuidof keyword [C++]
- __LIBID_ keyword [C++]
ms.assetid: badfe709-809b-4b66-ad48-ee35039d25c6
ms.openlocfilehash: f7564270408d14f58d1528c1f41c0afd2dbe219c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226966"
---
# <a name="__uuidof-operator"></a>`__uuidof` 运算符

**Microsoft 专用**

检索附加到表达式的 GUID。

## <a name="syntax"></a>语法

> **`__uuidof (`***表达式***`)`**

## <a name="remarks"></a>备注

*表达式*可以是类型名称、指针、引用或该类型的数组、专用于这些类型的模板或这些类型的变量。 只要编译器可使用参数查找附加的 GUID，此参数就有效。

当将**0**或 NULL 作为参数提供时，此内部函数的特例就是这种情况。 在这种情况下， **`__uuidof`** 将返回由零组成的 GUID。

使用此关键字可将附加的 GUID 提取到：

- 按 [`uuid`](../cpp/uuid-cpp.md) 扩展特性的对象。

- 使用特性创建的库块 [`module`](../windows/attributes/module-cpp.md) 。

> [!NOTE]
> 在调试版本中， **`__uuidof`** 始终动态（在运行时）初始化对象。 在发布版本中， **`__uuidof`** 可静态（在编译时）初始化对象。

对于与以前版本的兼容性，为， **`_uuidof`** **`__uuidof`** 除非指定编译器选项 " [ `/Za` \( 禁用语言扩展](../build/reference/za-ze-disable-language-extensions.md)"，否则将是同义词。

## <a name="example"></a>示例

以下代码（使用 ole32.lib 编译的）将显示使用 module 特性创建的库块的 uuid。

```cpp
// expre_uuidof.cpp
// compile with: ole32.lib
#include "stdio.h"
#include "windows.h"

[emitidl];
[module(name="MyLib")];
[export]
struct stuff {
   int i;
};

int main() {
   LPOLESTR lpolestr;
   StringFromCLSID(__uuidof(MyLib), &lpolestr);
   wprintf_s(L"%s", lpolestr);
   CoTaskMemFree(lpolestr);
}
```

## <a name="comments"></a>注释

如果库名称不再位于范围内，则可以使用 `__LIBID_` 而不是 **`__uuidof`** 。 例如：

```cpp
StringFromCLSID(__LIBID_, &lpolestr);
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)<br/>
[关键字](../cpp/keywords-cpp.md)
