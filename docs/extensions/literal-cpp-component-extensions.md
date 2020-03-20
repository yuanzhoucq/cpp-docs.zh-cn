---
title: literal（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- literal
- literal_cpp
helpviewer_keywords:
- literal keyword [C++]
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
ms.openlocfilehash: d567f8270dcb8965ed2f882c9a0c005f295fc619
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "79545455"
---
# <a name="literal-ccli-and-ccx"></a>literal（C++/CLI 和 C++/CX）

在 /clr 编译中标记为 literal 的变量（数据成员）相当于本机 static const 变量。

## <a name="all-platforms"></a>所有平台

### <a name="remarks"></a>备注

（此语言功能没有适用于所有运行时的备注。）

## <a name="windows-runtime"></a>Windows 运行时

### <a name="remarks"></a>备注

(此语言功能没有只适用于 Windows 运行时的备注。）

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

## <a name="remarks"></a>备注

标记为 literal 的数据成员必须在声明时初始化，值必须为常量整型、枚举或字符串类型。 从初始化表达式类型转换为静态常量数据成员类型时，不能使用用户定义的转换。

没有在运行时为文本字段分配内存；编译器只将其值插入该类的元数据中。

元数据中标记为 static const 的变量不可用于其他编译器。

有关详细信息，请参阅 [Static](../cpp/storage-classes-cpp.md) 和 [const](../cpp/const-cpp.md)。

literal 是上下文相关关键字。 有关详细信息，请参阅[上下文相关关键字](context-sensitive-keywords-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例展示了 literal 变量表示 static。

```cpp
// mcppv2_literal.cpp
// compile with: /clr
ref struct X {
   literal int i = 4;
};

int main() {
   int value = X::i;
}
```

## <a name="example"></a>示例

下面的示例演示了对元数据的文本影响：

```cpp
// mcppv2_literal2.cpp
// compile with: /clr /LD
public ref struct A {
   literal int lit = 0;
   static const int sc = 1;
};
```

注意 `sc` 和 `lit` 在元数据上的区别：`modopt` 指令应用于 `sc`，表示其他编译器会将其忽略。

```
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)
```

```
.field public static literal int32 lit = int32(0x0000000A)
```

## <a name="example"></a>示例

下面的示例是用 C# 编写，它引用上一示例中创建的元数据，并展示了 literal 和 static const 变量的效果：

```csharp
// mcppv2_literal3.cs
// compile with: /reference:mcppv2_literal2.dll
// A C# program
class B {
   public static void Main() {
      // OK
      System.Console.WriteLine(A.lit);
      System.Console.WriteLine(A.sc);

      // C# does not enforce C++ const
      A.sc = 9;
      System.Console.WriteLine(A.sc);

      // C# enforces const for a literal
      A.lit = 9;   // CS0131

      // you can assign a C++ literal variable to a C# const variable
      const int i = A.lit;
      System.Console.WriteLine(i);

      // but you cannot assign a C++ static const variable
      // to a C# const variable
      const int j = A.sc;   // CS0133
      System.Console.WriteLine(j);
   }
}
```

## <a name="requirements"></a>要求

编译器选项：`/clr`

## <a name="see-also"></a>另请参阅

[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)