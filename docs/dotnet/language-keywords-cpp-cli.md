---
title: "语言关键字 (C + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: keywords [C++]
ms.assetid: 021013b2-70ac-4df9-aa77-4af1c67a1a67
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e1107ad45feaae470ed2a7481f80bb17c389042d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="language-keywords-ccli"></a>语言关键字 (C++/CLI)
从托管扩展的 c + + 更改，为 Visual c + + 的多个语言关键字。  
  
 在新的 Visual c + + 语法中，双下划线删除与所有关键字的前缀 (有一个例外：`__identifier`保留)。 例如，现在某个属性声明为`property`，而不`__property`。  
  
 没有在托管扩展中使用双下划线前缀的两个主要的原因：  
  
-   它是 ISO c + + 标准提供本地扩展符合的方法。 托管扩展设计的主要目标是不引入不兼容内容的标准语言，如新的关键字和令牌。 在很大程度，推动的托管的引用类型的对象的声明的指针语法的选择，正是这个原因。  
  
-   使用双下划线，除了它符合的方面外, 也是合理地保证不会破坏现有基本代码的语言的用户。 这是托管扩展设计的第二个主要目标。  
  
 而不考虑删除双下划线，Microsoft 仍致力于保持一致。 但是，支持的 CLR 动态对象模型表示新且功能强大的编程范例。 这一新模式的支持，需要其自己的高级关键字和令牌。 我们都致力于提供此新的范例集成并支持标准语言时的第一类表达式。 新的语法设计提供这两种不同的对象模型的第一类编程体验。  
  
 同样，我们非常关心最大化这些新语言关键字的非入侵性性质。 此操作具有使用上下文和空格分隔的关键字的使用已完成。 我们将看看实际的新语言语法之前，让我们尝试这些两种特殊关键字风格的有意义。  
  
 上下文关键字具有特定程序上下文中的具有特殊含义。 在常规程序，例如，`sealed`视为一个普通的标识符。 但是，托管的引用类类型的声明部分中时，它被视为该类声明的上下文中的关键字。 这将大大减少内容引入在语言中，一个新的关键字的潜在侵入性影响，我们认为的与现有的基本代码的用户非常重要。 同时，它允许使用新功能的用户获得其他语言功能-正是，可以使用托管扩展的一流体验。 有关如何的示例`sealed`使用请参阅[托管类类型的声明](../dotnet/declaration-of-a-managed-class-type.md)。  
  
 空格分隔的关键字，如`value class`，是一种特殊情况的上下文关键字。 它用以空格分隔的上下文修饰符对现有的关键字。 对被视为单个单元，而不是两个单独的关键字。  
  
## <a name="see-also"></a>请参阅  
 [C + + /cli 迁移入门](../dotnet/cpp-cli-migration-primer.md)   
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)