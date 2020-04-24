---
title: 变量自变量列表 (...) (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
ms.openlocfilehash: 8ea4d71bf9a22fc96c794a92ba43bed6548cf5d1
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032299"
---
# <a name="variable-argument-lists--ccli"></a>变量自变量列表 (...) (C++/CLI)

此示例展示了如何在 C++/CLI 中使用 `...` 语法来实现包含可变数量实参的函数。

> [!NOTE]
> 本主题是关于 C++/CLI。 有关在 ISO`...`标准C++中使用 的信息，请参阅[省略号和可变模板](../cpp/ellipses-and-variadic-templates.md)以及["后修复"表达式](../cpp/postfix-expressions.md)中的省略号和省略号和默认参数。

使用 `...` 的形参必须是形参列表中的最后一个形参。

## <a name="example"></a>示例

### <a name="code"></a>代码

```cpp
// mcppv2_paramarray.cpp
// compile with: /clr
using namespace System;
double average( ... array<Int32>^ arr ) {
   int i = arr->GetLength(0);
   double answer = 0.0;

   for (int j = 0 ; j < i ; j++)
      answer += arr[j];

   return answer / i;
}

int main() {
   Console::WriteLine("{0}", average( 1, 2, 3, 6 ));
}
```

```Output
3
```

## <a name="code-example"></a>代码示例

下面的示例展示了如何在 C# 中调用需要使用可变数量实参的 Visual C++ 函数。

```cpp
// mcppv2_paramarray2.cpp
// compile with: /clr:safe /LD
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};
```

可以在 C# 或 Visual Basic（举个例子）中调用函数 `f`，就好像它是可以使用可变数量实参的函数一样。

在 C# 中，可以通过可变数量实参调用传递给 `ParamArray` 形参的实参。 下面的示例代码是用 C# 编写。

```csharp
// mcppv2_paramarray3.cs
// compile with: /r:mcppv2_paramarray2.dll
// a C# program

public class X {
   public static void Main() {
      // Visual C# will generate a String array to match the
      // ParamArray attribute
      C myc = new C();
      myc.f("hello", "there", "world");
   }
}
```

在 Visual C++ 中调用 `f` 可以传递初始化数组或长度可变数组。

```cpp
// mcpp_paramarray4.cpp
// compile with: /clr
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};

int main() {
   C ^ myc = gcnew C();
   myc->f("hello", "world", "!!!");
}
```

## <a name="see-also"></a>请参阅

[数组](arrays-cpp-component-extensions.md)
