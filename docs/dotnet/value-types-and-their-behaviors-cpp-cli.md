---
title: 值类型及其行为 (C + + CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- value types
ms.assetid: 5cb872a6-1e0a-429d-853d-df4ab47e8f2a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4d2d980e48a6f948c35faf0c4e42969795ef8dc7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404652"
---
# <a name="value-types-and-their-behaviors-ccli"></a>值类型及其行为 (C++/CLI)

值类型的已更改以各种方式从托管扩展 c + + Visual c + +。 在本部分中，我们查看 CLR 枚举类型和值类类型，以及查看装箱和 CLR 堆上的已装箱实例访问权限，以及内部指针和钉住指针看。 在此区域中进行了广泛的语言更改。

## <a name="in-this-section"></a>本节内容

[CLR 枚举类型](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
讨论声明和行为的枚举中的更改。

[值类型的隐式装箱](../dotnet/implicit-boxing-of-value-types.md)<br/>
介绍隐式装箱的值类型和行为中的后续更改的动机。

[装箱值的跟踪句柄](../dotnet/a-tracking-handle-to-a-boxed-value.md)<br/>
讨论如何隐式装箱值的类型转换为的跟踪句柄的装箱的值对象。

[值类型语义](../dotnet/value-type-semantics.md)<br/>
讨论对值类型语义，包括继承的虚方法、 类默认构造函数、 内部指针和钉住指针更改。

## <a name="see-also"></a>请参阅

[C++/CLI 迁移入门](../dotnet/cpp-cli-migration-primer.md)<br/>
[类和结构](../windows/classes-and-structs-cpp-component-extensions.md)