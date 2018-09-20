---
title: 语言关键字 (C + + CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keywords [C++]
ms.assetid: 021013b2-70ac-4df9-aa77-4af1c67a1a67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0b9deb25e203ea805b1430b2ec8e56f17a50123b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445433"
---
# <a name="language-keywords-ccli"></a>语言关键字 (C++/CLI)

Visual c + + 中与 c + + 托管扩展的多个语言关键字。

在新的 Visual c + + 语法中，双下划线删除从所有关键字的前缀 (有一个例外：`__identifier`保留)。 例如，现在属性声明为`property`，而不`__property`。

原因有两个主要在托管扩展中使用双下划线前缀：

- 它是提供本地扩展到 ISO-C + + 标准的符合的方法。 托管扩展设计的主要目标是不会引入与标准的语言，如新的关键字和令牌不兼容。 它是此原因，在很大程度，这样激励所选的托管的引用类型的对象的声明的指针语法。

- 使用双下划线，除了它的一致性方面，也是合理地保证不会破坏现有基本代码语言的用户。 这是托管扩展设计的第二个主目标。

尽管删除双下划线，Microsoft 仍致力于保持一致。 但是，对 CLR 动态对象模型表示新的和功能强大的编程模式的支持。 此新模式的支持需要其自己的高级关键字和令牌。 我们已致力于提供此新模式时将其集成和支持标准的语言的第一类表达式。 新语法设计提供了这两种完全不同的对象模型的第一类编程体验。

同样，我们所关注最大化这些新语言关键字的非入侵性特性。 完成此操作使用的上下文和空格分隔的关键字的使用。 我们看一下实际的新语言语法之前，让我们试着这些两种特殊关键字类型的有意义。

上下文关键字具有特殊含义内特定程序上下文。 在常规程序，例如，`sealed`视为一个普通的标识符。 但是，托管的引用类类型的声明部分中时，它被视为类声明的上下文中的关键字。 这可以尽量降低内容引入语言中的新关键字的潜在侵入性的影响，我们感觉这对具有现有基本代码的用户非常重要。 同时，它允许新功能的用户可以获得另一种语言功能-这是无法实现与托管扩展的一流体验。 有关如何的示例`sealed`使用请参阅[托管类类型的声明](../dotnet/declaration-of-a-managed-class-type.md)。

空格分隔的关键字，如`value class`，是一种特殊情况的上下文关键字。 它用空格分隔的上下文修饰符对现有的关键字。 对被视为单个单元而不是两个单独的关键字。

## <a name="see-also"></a>请参阅

[C++/CLI 迁移入门](../dotnet/cpp-cli-migration-primer.md)<br/>
[适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)