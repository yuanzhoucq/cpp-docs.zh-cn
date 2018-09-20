---
title: 常规语言更改 (C + + CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 79a70768-225c-4ae2-84d1-178b20a9b042
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9b48ebdf0bf25399b08f8a1cb1240a857cfad352
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418450"
---
# <a name="general-language-changes-ccli"></a>常规语言更改 (C++/CLI)

Visual c + + 中与 c + + 托管扩展的 CLR 语言功能数。

在本部分中所述的更改是一种语言杂注。 它包括更改的处理方式的字符串文本，省略号之间的重载决策中的更改并`Param`属性的更改`typeof`到`typeid`，调用构造函数初始值设定项列表中的更改和引入了新的强制转换表示法的`safe_cast`。

[字符串文本](../dotnet/string-literal.md)<br/>
讨论如何变化的字符串文本处理。

[参数数组和省略号](../dotnet/param-array-and-ellipsis.md)<br/>
讨论如何`ParamArray`的省略号上现在提供优先级 (`...`) 用于解析函数调用具有不同数量的参数。

[typeof 转到 T::typeid](../dotnet/typeof-goes-to-t-typeid.md)<br/>
讨论如何`typeof`运算符由`typeid`。

[初始值设定项列表](../dotnet/initializer-lists.md)<br/>
讨论了初始值设定项列表的调用顺序的更改。

[强制转换表示法和 safe_cast<> 介绍](../dotnet/cast-notation-and-introduction-of-safe-cast-angles.md)<br/>
讨论的引入的更改为强制转换表示法，具体`safe_cast`。

## <a name="see-also"></a>请参阅

[C++/CLI 迁移入门](../dotnet/cpp-cli-migration-primer.md)