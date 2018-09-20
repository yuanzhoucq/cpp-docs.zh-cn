---
title: 将托管类型 (c + +-CL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __gc types
- types [C++], CLR
ms.assetid: 1ddd114e-be02-4de7-a4dd-a2d72ad8ff81
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 382228b9e8364d90d7929b4633744071c5eb0c77
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408021"
---
# <a name="managed-types-ccl"></a>托管类型 (C++/CL)

托管的类型和创建的声明和使用这些类型的对象的语法已显著更改从托管扩展 c + + 的 Visual c + +。 这样做是为了提升它们 ISO c + + 类型系统中的集成。 以下各小节中详细介绍这些更改。

## <a name="in-this-section"></a>本节内容

[托管类类型的声明](../dotnet/declaration-of-a-managed-class-type.md)<br/>
讨论如何声明托管`class`， `struct`，或`interface`。

[CLR 引用类对象的声明](../dotnet/declaration-of-a-clr-reference-class-object.md)<br/>
讨论如何声明使用跟踪句柄的引用类类型对象。

[CLR 数组的声明](../dotnet/declaration-of-a-clr-array.md)<br/>
说明如何声明和初始化数组。

[以构造函数初始化顺序进行更改](../dotnet/changes-in-constructor-initialization-order.md)<br/>
讨论在类构造函数初始化顺序中的关键更改。

[析构函数语义的更改](../dotnet/changes-in-destructor-semantics.md)<br/>
讨论了非确定性定案`Finalize`而不是`Dispose`，引用对象和使用显式的后果`Finalize`。

**注意：** 委托的讨论将延迟，直到[委托和事件](../dotnet/delegates-and-events.md)以向他们提供的类的常规主题中的事件成员[类或接口中的成员声明(C + + CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md).

## <a name="see-also"></a>请参阅

[C++/CLI 迁移入门](../dotnet/cpp-cli-migration-primer.md)<br/>
[类和结构](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[数组](../windows/arrays-cpp-component-extensions.md)