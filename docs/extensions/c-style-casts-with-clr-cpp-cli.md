---
title: 使用 -clr 时的 C 样式强制转换 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- C-style casts and /clr
ms.assetid: d2a4401a-156a-4da9-8d12-923743e26913
ms.openlocfilehash: daaf92e36550c5479903dec4869b1cb116c0a65a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219789"
---
# <a name="c-style-casts-with-clr-ccli"></a>C 风格的强制转换和 /clr (C++/CLI)

下面的主题仅适用于公共语言运行时。

编译器尝试将与 CLR 类型一起使用的 C 样式强制转换映射到下面按顺序列出的强制转换之一：

1. const_cast

2. safe_cast

3. safe_cast + const_cast

4. static_cast

5. static_cast + const_cast

如果上面列出的转换都无效，且表达式类型和目标类型是 CLR 引用类型，那么 C 样式强制转换会映射到运行时检查（castclass MSIL 指令）。 否则，认为 C 样式强制转换无效，且编译器抛出错误。

## <a name="remarks"></a>备注

不建议使用 C 样式强制转换。 使用 [/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)进行编译时，请使用 [safe_cast](safe-cast-cpp-component-extensions.md)。

下面的示例演示了一个映射到的 C 样式强制转换 **`const_cast`** 。

```cpp
// cstyle_casts_1.cpp
// compile with: /clr
using namespace System;

ref struct R {};
int main() {
   const R^ constrefR = gcnew R();
   R^ nonconstR = (R^)(constrefR);
}
```

下面的示例展示了映射到 safe_cast**** 的 C 样式强制转换。

```cpp
// cstyle_casts_2.cpp
// compile with: /clr
using namespace System;
int main() {
   Object ^ o = "hello";
   String ^ s = (String^)o;
}
```

下面的示例演示了一个映射到**safe_cast**加号的 C 样式强制转换 **`const_cast`** 。

```cpp
// cstyle_casts_3.cpp
// compile with: /clr
using namespace System;

ref struct R {};
ref struct R2 : public R {};

int main() {
   const R^ constR2 = gcnew R2();
   try {
   R2^ b2DR = (R2^)(constR2);
   }
   catch(InvalidCastException^ e) {
      System::Console::WriteLine("Invalid Exception");
   }
}
```

下面的示例演示了一个映射到的 C 样式强制转换 **`static_cast`** 。

```cpp
// cstyle_casts_4.cpp
// compile with: /clr
using namespace System;

struct N1 {};
struct N2 {
   operator N1() {
      return N1();
   }
};

int main() {
   N2 n2;
   N1 n1 ;
   n1 = (N1)n2;
}
```

下面的示例演示了一个映射到加号的 C 样式强制 **`static_cast`** 转换 **`const_cast`** 。

```cpp
// cstyle_casts_5.cpp
// compile with: /clr
using namespace System;
struct N1 {};

struct N2 {
   operator const N1*() {
      static const N1 n1;
      return &n1;
   }
};

int main() {
   N2 n2;
   N1* n1 = (N1*)(const N1*)n2;   // const_cast + static_cast
}
```

下面的示例展示了映射到运行时检查的 C 样式强制转换。

```cpp
// cstyle_casts_6.cpp
// compile with: /clr
using namespace System;

ref class R1 {};
ref class R2 {};

int main() {
   R1^ r  = gcnew R1();
   try {
      R2^ rr = ( R2^)(r);
   }
   catch(System::InvalidCastException^ e) {
      Console::WriteLine("Caught expected exception");
   }
}
```

下面的示例展示了导致编译器抛出错误的无效 C 样式强制转换。

```cpp
// cstyle_casts_7.cpp
// compile with: /clr
using namespace System;
int main() {
   String^s = S"hello";
   int i = (int)s;   // C2440
}
```

## <a name="requirements"></a>要求

编译器选项：`/clr`

## <a name="see-also"></a>另请参阅

[适用于 .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)
