---
title: "值类型和它们的行为 (C + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- value types
ms.assetid: 5cb872a6-1e0a-429d-853d-df4ab47e8f2a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ccb26e1f054e6914f24982b36f6655fa62fc9f99
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="value-types-and-their-behaviors-ccli"></a>值类型及其行为 (C++/CLI)
值类型已以多种方式从托管扩展中的 c + + 更改为 Visual c + +。 在本部分中，我们看看 CLR 枚举类型以及值类类型，以及查看装箱和到 CLR 堆上的装箱实例的访问，以及一看内部和钉住指针。 在此区域中进行了广泛的语言更改。  
  
## <a name="in-this-section"></a>本节内容  
 [CLR 枚举类型](../dotnet/value-types-and-their-behaviors-cpp-cli.md)  
 讨论中的声明和枚举的行为的更改。  
  
 [值类型的隐式装箱](../dotnet/implicit-boxing-of-value-types.md)  
 讨论动机是针对隐式装箱的值类型和行为中的后续更改。  
  
 [装箱值的跟踪句柄](../dotnet/a-tracking-handle-to-a-boxed-value.md)  
 讨论如何隐式装箱的值类型转换为装箱的值对象的跟踪句柄。  
  
 [值类型语义](../dotnet/value-type-semantics.md)  
 讨论对值类型语义，包括继承的虚方法、 类默认构造函数、 内部指针，并钉住指针的更改。  
  
## <a name="see-also"></a>请参阅  
 [C + + /cli 迁移入门](../dotnet/cpp-cli-migration-primer.md)   
 [类和结构](../windows/classes-and-structs-cpp-component-extensions.md)