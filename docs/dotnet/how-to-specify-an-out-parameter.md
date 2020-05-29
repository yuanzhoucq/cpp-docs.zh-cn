---
title: 如何：指定 out 参数
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
ms.openlocfilehash: 4bd6ad1d3009adcc124bdeb90d9d67de07112de2
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "79545443"
---
# <a name="how-to-specify-an-out-parameter"></a>如何：指定 out 参数

此示例演示如何指定函数参数是 `out` 参数，以及如何从C#程序调用该函数。

使用 <xref:System.Runtime.InteropServices.OutAttribute> 在中C++指定 `out` 参数。

## <a name="example"></a>示例

此示例的第一部分创建一个C++ DLL。 它定义一个类型，该类型包含带有 `out` 参数的函数。

```cpp
// cpp_out_param.cpp
// compile with: /LD /clr
using namespace System;
public value struct TestStruct {
   static void Test([Runtime::InteropServices::Out] String^ %s) {
      s = "a string";
   }
};
```

此源文件是一个C#使用在上一个示例C++中创建的组件的客户端。

```csharp
// cpp_out_param_2.cs
// compile with: /reference:cpp_out_param.dll
using System;
class TestClass {
   public static void Main() {
      String t;
      TestStruct.Test(out t);
      System.Console.WriteLine(t);
   }
}
```

```Output
a string
```

## <a name="see-also"></a>另请参阅

[使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)
