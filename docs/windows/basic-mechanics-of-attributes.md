---
title: 特性的基本机制 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], inserting in code
- attributes [C++], about attributes
ms.assetid: dc2069c3-b9f3-4a72-965c-4e5208ce8e34
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3bb7ff68f9c17f7b90261c2c96630911454842a5
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462487"
---
# <a name="basic-mechanics-of-attributes"></a>特性的基本机制
有三种方法将属性插入你的项目。 首先，您可以将它们手动插入您的源代码。 第二，您可以将它们插入在项目中使用对象的属性网格。 最后，您可以插入它们使用不同的向导。 有关使用的详细信息**属性**窗口和各种向导，请参阅[创建和管理 Visual c + + 项目](../ide/creating-and-managing-visual-cpp-projects.md)。  
  
 作为之前，当生成项目时，编译器将分析每个 c + + 源代码文件，生成的对象文件。 但是，当编译器遇到属性，它分析并语法验证。 然后编译器将动态调用要插入代码或在编译时进行其他修改的属性提供程序。 具体取决于属性的类型不同的提供程序实现。 例如，由 Atlprov.dll 实现与 ATL 相关的属性。  
  
 下图演示了编译器和特性提供程序之间的关系。  
  
 ![组件特性通信](../windows/media/vccompattrcomm.gif "vcCompAttrComm")  
  
> [!NOTE]
>  特性用法不会更改源文件的内容。 在调试会话过程中是唯一一次生成的属性代码均可见。 此外，对于每个源项目文件中，可以生成显示属性替换结果的文本文件。 此过程的详细信息，请参阅[/Fx （合并插入的代码）](../build/reference/fx-merge-injected-code.md)并[调试插入代码](/visualstudio/debugger/how-to-debug-injected-code)。  
  
 大多数 c + + 构造，如属性具有一组特征定义其适当的使用情况。 这被称为属性的上下文并在每个属性参考主题的属性上下文表中解决。 例如，[组件类](../windows/coclass.md)属性仅对现有的类或结构，而不是应用[cpp_quote](../windows/cpp-quote.md)属性，可以插入 c + + 源代码文件中的任意位置。  
  
## <a name="see-also"></a>请参阅  
 [概念](../windows/attributed-programming-concepts.md)