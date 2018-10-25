---
title: __identifier (c + + CLI) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- __identifier
- __identifier_cpp
dev_langs:
- C++
helpviewer_keywords:
- __identifier keyword [C++]
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ee4aa1686980d2baecd0b261a615818fc5a6c0ee
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50082588"
---
# <a name="identifier-ccli"></a>__identifier (C++/CLI)

可以使用 c + + 关键字用作标识符。

## <a name="all-platforms"></a>所有平台

### <a name="syntax"></a>语法

```cpp
__identifier(C++_keyword)
```

### <a name="remarks"></a>备注

利用 **__identifier**允许使用，但强烈建议不要使用作为一种样式的关键字不是关键字的标识符。

## <a name="windows-runtime"></a>Windows 运行时

### <a name="requirements"></a>要求

编译器选项：`/ZW`

### <a name="examples"></a>示例

**示例**

在以下示例中，类名为**模板**是在 C# 中创建并分发作为 DLL。 在 C + + /cli CLI 程序，使用**模板**类， **_try**关键字对隐藏这一事实，**模板**是标准 c + + 关键字。

```cs
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

**__Identifier**关键字是有效，且`/clr`编译器选项。

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

在以下示例中，类名为**模板**是在 C# 中创建并分发作为 DLL。 在 C + + /cli CLI 程序，使用**模板**类， **_try**关键字对隐藏这一事实，**模板**是标准 c + + 关键字。

```cs
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

## <a name="see-also"></a>请参阅

[ .NET 和 UWP 的组件扩展](../windows/component-extensions-for-runtime-platforms.md)<br/>
[ .NET 和 UWP 的组件扩展](../windows/component-extensions-for-runtime-platforms.md)