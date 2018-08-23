---
title: 托管类型 (c + + CL) |Microsoft 文档
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
ms.openlocfilehash: 42426c45f4b8caf3cd4cb61ee867470dc9ea639f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135854"
---
# <a name="managed-types-ccl"></a>托管类型 (C++/CL)
托管的类型和创建的声明和使用这些类型的对象的语法已显著更改从托管扩展的 c + + 到 Visual c + +。 这样做是为了提升它们在 ISO c + + 类型系统的集成。 以下各小节将详细介绍这些更改。  
  
## <a name="in-this-section"></a>本节内容  
 [托管类类型的声明](../dotnet/declaration-of-a-managed-class-type.md)  
 讨论如何声明托管`class`， `struct`，或`interface`。  
  
 [CLR 引用类对象的声明](../dotnet/declaration-of-a-clr-reference-class-object.md)  
 讨论如何声明使用跟踪句柄的引用类类型对象。  
  
 [CLR 数组的声明](../dotnet/declaration-of-a-clr-array.md)  
 说明如何声明和初始化的数组。  
  
 [以构造函数初始化顺序进行更改](../dotnet/changes-in-constructor-initialization-order.md)  
 讨论类构造函数初始化顺序中的重要变化。  
  
 [析构函数语义的更改](../dotnet/changes-in-destructor-semantics.md)  
 讨论非确定性终止`Finalize`与`Dispose`，引用对象，以及使用显式的后果，这`Finalize`。  
  
 **注意：** 的委托讨论将推迟至[委托和事件](../dotnet/delegates-and-events.md)以便提供一个类的常规主题中的事件成员[类或接口中的成员声明(C + + /CLI CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md).  
  
## <a name="see-also"></a>请参阅  
 [C + + /cli 迁移入门](../dotnet/cpp-cli-migration-primer.md)   
 [类和结构](../windows/classes-and-structs-cpp-component-extensions.md)   
 [数组](../windows/arrays-cpp-component-extensions.md)