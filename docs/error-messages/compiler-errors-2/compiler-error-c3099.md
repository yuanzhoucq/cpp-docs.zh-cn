---
title: 编译器错误 C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: e9a76fa2e0dc5602a88324cfd2fef85457ad7e99
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512107"
---
# <a name="compiler-error-c3099"></a>编译器错误 C3099

“关键字”：将 [System::AttributeUsageAttribute] 用于托管特性；将 [Windows::Foundation::Metadata::AttributeUsageAttribute] 用于 WinRT 特性

使用<xref:System.AttributeUsageAttribute>声明 **/clr**属性。 使用 `Windows::Foundation::Metadata::AttributeUsageAttribute` 声明 Windows 运行时特性。

有关 /CLR 特性的详细信息，请参阅[用户定义的特性](../../windows/user-defined-attributes-cpp-component-extensions.md)。 Windows 运行时中的受支持属性，请参阅[Windows.Foundation.Metadata 命名空间](https://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.aspx)

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