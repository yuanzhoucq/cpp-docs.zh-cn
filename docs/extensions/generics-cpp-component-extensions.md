---
title: 泛型（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- generic_cpp
- generic
helpviewer_keywords:
- generics [C++]
ms.assetid: c7ccc316-a411-4c00-b2e2-f0c0eadc6cfd
ms.openlocfilehash: 29c6b22189ea1f644c0fa52ec0f4d605604361ba
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181988"
---
# <a name="generics--ccli-and-ccx"></a>泛型（C++/CLI 和 C++/CX）

泛型是参数化类型和方法。 在本节中，请了解 Windows 运行时和公共语言运行时共同支持的泛型功能，以及只有公共语言运行时支持的功能。 另请了解如何使用 C++/CLI 编写你自己的泛型方法和类型，以及如何将使用 .NET Framework 语言编写的泛型类型用于 C++/CLI。 最后，本节将比较泛型和 C++ 模板。

## <a name="in-this-section"></a>本节内容

### <a name="supported-by-the-windows-runtime-and-the-common-language-runtime"></a>Windows 运行时和公共语言运行时共同支持

[C++/CLI 中的泛型概述](overview-of-generics-in-visual-cpp.md)<br/>
有关泛型定义、语言功能的动机、用于描述泛型的术语定义以及将引用类型和值类型用作泛型的类型参数的信息。

[泛型接口 (C++/CLI)](generic-interfaces-visual-cpp.md)<br/>
有关定义和使用泛型接口的信息。

[泛型委托 (C++/CLI)](generic-delegates-visual-cpp.md)<br/>
有关定义和使用泛型委托的信息。

[泛型类型参数的约束 (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md)<br/>
有关在泛型类型中使用约束的信息。

[使用泛型 (C++/CLI)](consuming-generics-cpp-cli.md)<br/>
介绍了如何将 .NET 程序集中定义的且可能使用其他语言编写的泛型用于 C++/CLI。

[泛型与模板 (C++/CLI)](generics-and-templates-visual-cpp.md)<br/>
比较泛型和模板，分别何时使用以及如何有效地结合使用。

### <a name="supported-by-the-common-language-runtime"></a>只有公共语言运行时支持

[泛型函数 (C++/CLI)](generic-functions-cpp-cli.md)<br/>
有关定义和使用泛型函数和方法的信息。

[泛型类 (C++/CLI)](generic-classes-cpp-cli.md)<br/>
有关定义和使用泛型类的信息。

## <a name="related-sections"></a>相关章节

[如何：使用 for each 循环访问泛型集合](../dotnet/how-to-iterate-over-a-generic-collection-with-for-each.md)<br/>
对泛型集合使用 [for each、in](../dotnet/for-each-in.md) 关键字。

## <a name="see-also"></a>另请参阅

[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)
