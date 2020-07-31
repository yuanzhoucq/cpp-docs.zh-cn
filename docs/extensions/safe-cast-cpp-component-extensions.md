---
title: safe_cast（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- safe_cast
- safe_cast_cpp
- stdcli::language::safe_cast
helpviewer_keywords:
- safe_cast keyword [C++]
ms.assetid: 4fa688bf-a8ec-49bc-a4c5-f48134efa4f7
ms.openlocfilehash: 2eb09680ef6e7d1ee90b62eee8c8971fb4963212
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225119"
---
# <a name="safe_cast-ccli-and-ccx"></a>safe_cast（C++/CLI 和 C++/CX）

如果成功，safe_cast**** 操作返回指定表达式作为指定类型；否则，抛出 `InvalidCastException`。

## <a name="all-runtimes"></a>所有运行时

（此语言功能没有适用于所有运行时的备注。）

### <a name="syntax"></a>语法

```cpp
[default]:: safe_cast< type-id >( expression )
```

## <a name="windows-runtime"></a>Windows 运行时

使用 safe_cast****，可以更改指定表达式的类型。 在完全期望变量或参数可转换为特定类型的情况下，可以使用不含 try-catch**** 块的 safe_cast****，以在开发过程中检测编程错误。 有关详细信息，请参阅[强制转换 (C++/CX)](../cppcx/casting-c-cx.md)。

### <a name="syntax"></a>语法

```cpp
[default]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>参数

*类型 id*<br/>
要将 expression** 转换为的目标类型。 引用或值类型的句柄、值类型或是对引用或值类型的跟踪引用。

*expression*<br/>
一个表达式，计算结果是引用或值类型的句柄、值类型或是对引用或值类型的跟踪引用。

### <a name="remarks"></a>备注

**safe_cast** `InvalidCastException` 如果无法将*expression*转换为*类型 id*指定的类型，则 safe_cast 引发。若要捕获 `InvalidCastException` ，请指定[/EH （异常处理模型）](../build/reference/eh-exception-handling-model.md)编译器选项，并使用**try/catch**语句。

### <a name="requirements"></a>要求

编译器选项：`/ZW`

### <a name="examples"></a>示例

下面的代码示例展示了如何将 safe_cast**** 用于Windows 运行时。

```cpp
// safe_cast_ZW.cpp
// compile with: /ZW /EHsc

using namespace default;
using namespace Platform;

interface class I1 {};
interface class I2 {};
interface class I3 {};

ref class X : public I1, public I2 {};

int main(Array<String^>^ args) {
   I1^ i1 = ref new X;
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead
   try {
      I3^ i4 = safe_cast<I3^>(i1);   // Fails because i1 is not derived from I3.
   }
   catch(InvalidCastException^ ic) {
   wprintf(L"Caught expected exception: %s\n", ic->Message);
   }
}
```

```Output
Caught expected exception: InvalidCastException
```

## <a name="common-language-runtime"></a>公共语言运行时

使用 safe_cast****，可以更改表达式的类型，并生成可验证的 MSIL 代码。

### <a name="syntax"></a>语法

```cpp
[cli]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>参数

*类型 id*<br/>
引用或值类型的句柄、值类型或是对引用或值类型的跟踪引用。

*expression*<br/>
一个表达式，计算结果是引用或值类型的句柄、值类型或是对引用或值类型的跟踪引用。

### <a name="remarks"></a>备注

表达式 `safe_cast<` *类型 id* `>(` *表达式* `)` 将操作数*表达式*转换为类型*id*类型的对象。

在大多数接受 safe_cast**** 的情况下，编译器也接受 [static_cast](../cpp/static-cast-operator.md)。  但是，可以保证**safe_cast**生成可验证的 msil，因为这样 **`static_cast`** 可以生成无法验证的 msil。  若要详细了解可验证的代码，请参阅[纯代码和可验证的代码 (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md) 和 [Peverify.exe（PEVerify 工具）](/dotnet/framework/tools/peverify-exe-peverify-tool)。

与类似 **`static_cast`** ， **safe_cast**会调用用户定义的转换。

若要详细了解强制转换，请参阅[强制转换运算符](../cpp/casting-operators.md)。

**safe_cast**不应用 **`const_cast`** （强制转换 **`const`** ）。

safe_cast**** 位于 cli 命名空间中。  有关详细信息，请参阅[平台默认 cli 命名空间](platform-default-and-cli-namespaces-cpp-component-extensions.md)。

若要详细了解 safe_cast****，请参阅：

- [采用/clr 的 C 样式强制转换（c + +/CLI）](c-style-casts-with-clr-cpp-cli.md)

- [如何：在 C++/CLI 中使用 safe_cast](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

例如，编译器将不接受， **`static_cast`** 但将接受**safe_cast**用于不相关的接口类型之间的转换。  使用 safe_cast**** 时，编译器不会发出转换错误，而是在运行时执行检查，以确定能否进行强制转换

```cpp
// safe_cast.cpp
// compile with: /clr
using namespace System;

interface class I1 {};
interface class I2 {};
interface class I3 {};

ref class X : public I1, public I2 {};

int main() {
   I1^ i1 = gcnew X;
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead
   try {
      I3^ i4 = safe_cast<I3^>(i1);   // fail at runtime, no common type
   }
   catch(InvalidCastException^) {
      Console::WriteLine("Caught expected exception");
   }
}
```

```Output
Caught expected exception
```

## <a name="see-also"></a>另请参阅

[适用于 .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)
