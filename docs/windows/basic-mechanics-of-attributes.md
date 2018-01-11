---
title: "特性的基本机制 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- attributes [C++], inserting in code
- attributes [C++], about attributes
ms.assetid: dc2069c3-b9f3-4a72-965c-4e5208ce8e34
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 99771e798e4957de5ff69601a5d3494e5fcacc35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="basic-mechanics-of-attributes"></a>特性的基本机制
有三种方法要插入到你的项目的属性。 首先，你可以将它们手动插入你的源代码。 其次，你可以将它们插入项目中使用对象的属性网格。 最后，你可以将它们插入使用各种向导。 使用属性窗口和各种向导的详细信息，请参阅[创建和管理 Visual c + + 项目](../ide/creating-and-managing-visual-cpp-projects.md)。  
  
 为之前，当生成项目时，编译器分析每个 c + + 源代码文件，生成的对象文件。 但是，当编译器遇到属性，它分析并语法验证。 然后，编译器动态调用要插入代码，或在编译时进行其他修改的属性提供程序。 提供程序的实现根据属性的类型而有所不同。 例如，由 Atlprov.dll 实现与 ATL 相关的属性。  
  
 下图演示了编译器和属性提供程序之间的关系。  
  
 ![组件特性通信](../windows/media/vccompattrcomm.gif "vcCompAttrComm")  
  
> [!NOTE]
>  特性用法不会更改源文件的内容。 生成的特性代码是可见的唯一时间是在调试会话期间。 此外，对于每个项目中的源文件，可以生成一个文本文件，显示的属性替换结果。 有关此过程的详细信息，请参阅[/Fx （合并插入的代码）](../build/reference/fx-merge-injected-code.md)和[调试插入代码](/visualstudio/debugger/how-to-debug-injected-code)。  
  
 大多数 c + + 构造，如属性具有定义其正确的使用情况的一组特征。 这被称为的属性的上下文，并在每个属性参考主题的特性上下文表中针对。 例如，[组件类](../windows/coclass.md)属性仅到现有的类或结构，而不是应用[cpp_quote](../windows/cpp-quote.md)属性，它可以插入 c + + 源代码文件中的任何位置。  
  
## <a name="see-also"></a>请参阅  
 [概念](../windows/attributed-programming-concepts.md)