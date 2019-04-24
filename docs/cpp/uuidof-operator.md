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
ms.openlocfilehash: a14ef9043ec2196ff930a37d0eff95e90024d3d5
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58769194"
---
# <a name="uuidof-operator"></a>__uuidof 运算符

**Microsoft 专用**

检索附加到表达式的 GUID。

## <a name="syntax"></a>语法

```
__uuidof (expression)
```

## <a name="remarks"></a>备注

*表达式*可以是类型名称、 指针、 引用或该类型的数组，这些类型或这些类型的变量上专用化模板。 只要编译器可使用参数查找附加的 GUID，此参数就有效。

此内部函数的一种特殊情况是当任一**0**或作为自变量提供了空值。 在这种情况下， **__uuidof**将返回零组成的 GUID。

使用此关键字可将附加的 GUID 提取到：

- 一个对象的[uuid](../cpp/uuid-cpp.md)扩展的特性。

- 使用创建库块[模块](../windows/attributes/module-cpp.md)属性。

> [!NOTE]
> 在调试版本中， **__uuidof**始终初始化动态 （在运行时） 的对象。 在发布版本中， **__uuidof**可静态 （在编译时） 初始化的对象。

与以前版本的兼容性 **_uuidof**是的同义词 **__uuidof**除非编译器选项[/Za\(禁用语言扩展)](../build/reference/za-ze-disable-language-extensions.md)是指定。

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

在库名称的不再在作用域中的情况下，可以使用`__LIBID_`而不是 **__uuidof**。 例如：

```cpp
StringFromCLSID(__LIBID_, &lpolestr);
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)<br/>
[关键字](../cpp/keywords-cpp.md)