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
ms.openlocfilehash: 0da32aae9a8c2c7f21ee9576e1e1147822314a36
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172173"
---
# <a name="__identifier-ccli"></a>__identifier (C++/CLI)

允许使用 C++ 关键字作为标识符。

## <a name="all-platforms"></a>所有平台

### <a name="syntax"></a>语法

```cpp
__identifier(C++_keyword)
```

### <a name="remarks"></a>备注

允许对不是关键字的标识符使用 _identifier 关键字，但强烈建议不要这样做。

## <a name="windows-runtime"></a>Windows 运行时

### <a name="requirements"></a>要求

编译器选项：`/ZW`

### <a name="examples"></a>示例

**示例**

在下面的示例中，名为“template”的类在 C# 中创建，并作为 DLL 分发。 在使用 template 类的 C++/CLI 程序中，_identifier 关键字掩盖了 template 是标准 C++ 关键字这一事实。

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

_identifier 关键字对 `/clr` 编译器选项有效。

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

在下面的示例中，名为“template”的类在 C# 中创建，并作为 DLL 分发。 在使用 template 类的 C++/CLI 程序中，_identifier 关键字掩盖了 template 是标准 C++ 关键字这一事实。

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

[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)<br/>
[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)
