---
title: C 样式强制转换和-clr (C + + CLI) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- C-style casts and /clr
ms.assetid: d2a4401a-156a-4da9-8d12-923743e26913
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bc51d330e771d9861d510b77d1fbd69a9a790c7d
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2018
ms.locfileid: "49327981"
---
# <a name="c-style-casts-with-clr-ccli"></a>C 风格的强制转换和 /clr (C++/CLI)

下面的主题仅适用于公共语言运行时。

当与 CLR 类型一起使用，编译器将尝试映射 C 样式强制转换为下面列出，按以下顺序执行的转换之一：

1. const_cast

2. safe_cast

3. safe_cast plus const_cast

4. static_cast

5. static_cast plus const_cast

如果上面列出的转换都有效，并且该表达式的类型和目标类型是 CLR 引用类型，C 样式强制转换将映射到运行时检查 （castclass MSIL 指令）。 否则为 C 样式强制转换将被视为无效，则编译器会发出错误。

## <a name="remarks"></a>备注

不建议使用 C 样式强制转换。 使用编译时[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)，使用[safe_cast](../windows/safe-cast-cpp-component-extensions.md)。

下面的示例演示 C 样式强制转换映射到**const_cast**。

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

下面的示例演示 C 样式强制转换映射到**safe_cast**。

```cpp
// cstyle_casts_2.cpp
// compile with: /clr
using namespace System;
int main() {
   Object ^ o = "hello";
   String ^ s = (String^)o;
}
```

下面的示例演示 C 样式强制转换映射到**safe_cast**加上**const_cast**。

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

下面的示例演示 C 样式强制转换映射到**static_cast**。

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

下面的示例演示 C 样式强制转换映射到**static_cast**加上**const_cast**。

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

下面的示例演示 C 样式强制转换映射到运行时检查。

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

下面的示例演示无效 C 样式强制转换，这将导致编译器发出错误。

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

## <a name="see-also"></a>请参阅

[适用于.NET 和 UWP 组件扩展](../windows/component-extensions-for-runtime-platforms.md)