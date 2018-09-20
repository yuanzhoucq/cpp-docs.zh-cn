---
title: 类或接口中的成员声明 (C + + CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- members, declaration syntax
- class members, declaration syntax
ms.assetid: 95d312a4-198b-46f0-b8f5-15253807c55e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 80b872b4c614677c05b0d28b821d3a48255905c5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430627"
---
# <a name="member-declarations-within-a-class-or-interface-ccli"></a>类或接口中的成员声明 (C++/CLI)

声明属性和运算符的已经过广泛改写从托管扩展 c + + 的 Visual c + +，隐藏在托管扩展设计中公开的基础实现详细信息。 还修改了事件声明。

更改类别下有任何托管扩展支持，现在静态构造函数可以是定义的外部 （它们已要求托管扩展中的以内联方式定义），并委托构造函数的概念引入了。

## <a name="in-this-section"></a>本节内容

[属性声明](../dotnet/property-declaration.md)<br/>
讨论对属性声明的更改。

[属性索引声明](../dotnet/property-index-declaration.md)<br/>
讨论对索引的属性声明的更改。

[委托和事件](../dotnet/delegates-and-events.md)<br/>
讨论对声明委托和事件的语法更改。

[密封虚函数](../dotnet/sealing-a-virtual-function.md)<br/>
讨论对密封函数的语法更改。

[重载运算符](../dotnet/overloaded-operators.md)<br/>
讨论对运算符重载更改。

[转换运算符的更改](../dotnet/changes-to-conversion-operators.md)<br/>
讨论了转换运算符的更改。

[接口成员的显式重写](../dotnet/explicit-override-of-an-interface-member.md)<br/>
讨论对显式重写接口成员的方法更改。

[私有虚函数](../dotnet/private-virtual-functions.md)<br/>
讨论在派生类中处理私有虚函数的方式中的更改。

[静态 Const Int 链接不再是文本的](../dotnet/static-const-int-linkage-is-no-longer-literal.md)<br/>
讨论的方式发生改变`static const`整型成员链接，以及如何显式声明使用新的常数`literal`关键字。

## <a name="see-also"></a>请参阅

[C++/CLI 迁移入门](../dotnet/cpp-cli-migration-primer.md)