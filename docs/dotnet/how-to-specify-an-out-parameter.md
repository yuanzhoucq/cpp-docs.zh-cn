---
title: 如何：指定 out 参数
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
ms.openlocfilehash: 901257b92aaa5e13e6e79d612ca590b734e15881
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747480"
---
# <a name="how-to-specify-an-out-parameter"></a>如何：指定 out 参数

此示例演示如何指定函数参数是一个输出参数以及如何从 C# 程序调用该函数。

使用 Visual c + + 中指定的输出参数<xref:System.Runtime.InteropServices.OutAttribute>。

## <a name="example"></a>示例

此示例的第一个部分是 Visual c + + DLL 包含带有输出参数的函数的类型。

```
// cpp_out_param.cpp
// compile with: /LD /clr:safe
using namespace System;
public value struct TestStruct {
   static void Test([Runtime::InteropServices::Out] String^ %s) {
      s = "a string";
   }
};
```

## <a name="example"></a>示例

这是一个 C# 客户端使用在上一示例中创建的 Visual c + + 组件。

```
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

## <a name="see-also"></a>请参阅

[使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)
