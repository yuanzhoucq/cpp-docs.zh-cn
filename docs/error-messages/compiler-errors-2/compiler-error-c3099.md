---
title: 编译器错误 C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: beaa34bb9bed4824383cdad32c6bfd0aea19f6b7
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418565"
---
# <a name="compiler-error-c3099"></a>编译器错误 C3099

“关键字”：将 [System::AttributeUsageAttribute] 用于托管特性；将 [Windows::Foundation::Metadata::AttributeUsageAttribute] 用于 WinRT 特性

使用<xref:System.AttributeUsageAttribute>声明 **/clr**属性。 使用 `Windows::Foundation::Metadata::AttributeUsageAttribute` 声明 Windows 运行时特性。

有关 /CLR 特性的详细信息，请参阅[用户定义的特性](../../windows/user-defined-attributes-cpp-component-extensions.md)。 Windows 运行时中的受支持属性，请参阅[Windows.Foundation.Metadata 命名空间](/uwp/api/windows.foundation.metadata)

## <a name="example"></a>示例

下面的示例生成 C3099，并演示如何修复此错误。

```
// C3099.cpp
// compile with: /clr /c
using namespace System;
[usage(10)]   // C3099
// try the following line instead
// [AttributeUsageAttribute(AttributeTargets::All)]
ref class A : Attribute {};
```