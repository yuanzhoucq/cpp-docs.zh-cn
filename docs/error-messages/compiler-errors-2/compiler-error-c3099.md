---
title: 编译器错误 C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: 0f3eac1c232ef159d220a347d6b6dc3aed2fdd9a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59775954"
---
# <a name="compiler-error-c3099"></a>编译器错误 C3099

“关键字”：将 [System::AttributeUsageAttribute] 用于托管特性；将 [Windows::Foundation::Metadata::AttributeUsageAttribute] 用于 WinRT 特性

使用<xref:System.AttributeUsageAttribute>声明 **/clr**属性。 使用 `Windows::Foundation::Metadata::AttributeUsageAttribute` 声明 Windows 运行时特性。

有关 /CLR 特性的详细信息，请参阅[用户定义的特性](../../extensions/user-defined-attributes-cpp-component-extensions.md)。 Windows 运行时中的受支持属性，请参阅[Windows.Foundation.Metadata 命名空间](/uwp/api/windows.foundation.metadata)

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