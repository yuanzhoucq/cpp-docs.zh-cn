---
title: __identifier (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- __identifier
- __identifier_cpp
helpviewer_keywords:
- __identifier keyword [C++]
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
ms.openlocfilehash: 5f95e9fc55acd33705b855c7c4f0ef268d4776a0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219685"
---
# <a name="__identifier-ccli"></a>__identifier (C++/CLI)

允许使用 C++ 关键字作为标识符。

## <a name="all-platforms"></a>所有平台

### <a name="syntax"></a>语法

```cpp
__identifier(C++_keyword)
```

### <a name="remarks"></a>备注

允许对不是关键字的标识符使用 _identifier**** 关键字，但强烈建议不要这样做。

## <a name="windows-runtime"></a>Windows 运行时

### <a name="requirements"></a>要求

编译器选项：`/ZW`

### <a name="examples"></a>示例

**示例**

在下面的示例中，使用 c # 创建一个名为的类 `template` ，并将其作为 DLL 进行分发。 在使用类的 c + +/CLI 程序中 `template` ， **`__identifier`** 关键字隐藏 `template` 了是标准 c + + 关键字的事实。

```csharp
// identifier_template.cs
// compile with: /target:library
public class template {
   public void Run() { }
}
```

```cpp
// keyword__identifier.cpp
// compile with: /ZW
#using <identifier_template.dll>
int main() {
   __identifier(template)^ pTemplate = ref new __identifier(template)();
   pTemplate->Run();
}
```

## <a name="common-language-runtime"></a>公共语言运行时

### <a name="remarks"></a>备注

_identifier**** 关键字对 `/clr` 编译器选项有效。

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

在下面的示例中，使用 c # 创建一个名为的类 `template` ，并将其作为 DLL 进行分发。 在使用类的 c + +/CLI 程序中 `template` ， **`__identifier`** 关键字隐藏 `template` 了是标准 c + + 关键字的事实。

```csharp
// identifier_template.cs
// compile with: /target:library
public class template {
   public void Run() { }
}
```

```cpp
// keyword__identifier.cpp
// compile with: /clr
#using <identifier_template.dll>

int main() {
   __identifier(template) ^pTemplate = gcnew __identifier(template)();
   pTemplate->Run();
}
```

## <a name="see-also"></a>另请参阅

[适用于 .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)<br/>
[适用于 .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)
