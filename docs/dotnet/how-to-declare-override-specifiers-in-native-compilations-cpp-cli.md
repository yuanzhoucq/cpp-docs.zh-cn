---
title: 如何：声明覆盖指定器（C++/CLI）
ms.date: 11/04/2016
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
ms.openlocfilehash: 9f3f6855f257d0af250b9bbdd2c0360b308ce775
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374449"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>如何：声明本机编译中的重写说明符 (C++/CLI)

[密封](../extensions/sealed-cpp-component-extensions.md)、[抽象](../extensions/abstract-cpp-component-extensions.md)和[重写](../extensions/override-cpp-component-extensions.md)在不使用 **/ZW**或[/clr](../build/reference/clr-common-language-runtime-compilation.md)的编译中可用。

> [!NOTE]
> ISO C++11 标准语言具有[重写](../cpp/override-specifier.md)标识符和[最终](../cpp/final-specifier.md)标识符，并且两者都在 Visual Studio`final`使用中`sealed`支持，而不是在旨在编译为本机代码的代码中。

## <a name="example"></a>示例

### <a name="description"></a>描述

下面的示例显示在`sealed`本机编译中有效。

### <a name="code"></a>代码

```cpp
// sealed_native_keyword.cpp
#include <stdio.h>
__interface I1 {
   virtual void f();
   virtual void g();
};

class X : public I1 {
public:
   virtual void g() sealed {}
};

class Y : public X {
public:

   // the following override generates a compiler error
   virtual void g() {}   // C3248 X::g is sealed!
};
```

## <a name="example"></a>示例

### <a name="description"></a>描述

下一个示例显示`override`在本机编译中有效。

### <a name="code"></a>代码

```cpp
// override_native_keyword.cpp
#include <stdio.h>
__interface I1 {
   virtual void f();
};

class X : public I1 {
public:
   virtual void f() override {}   // OK
   virtual void g() override {}   // C3668 I1::g does not exist
};
```

## <a name="example"></a>示例

### <a name="description"></a>描述

此示例显示在`abstract`本机编译中有效。

### <a name="code"></a>代码

```cpp
// abstract_native_keyword.cpp
class X abstract {};

int main() {
   X * MyX = new X;   // C3622 cannot instantiate abstract class
}
```

## <a name="see-also"></a>另请参阅

[覆盖指定器](../extensions/override-specifiers-cpp-component-extensions.md)
