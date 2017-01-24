---
title: "Basic Mechanics of Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "attributes [C++], inserting in code"
  - "attributes [C++], about attributes"
ms.assetid: dc2069c3-b9f3-4a72-965c-4e5208ce8e34
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Basic Mechanics of Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可通过三种方式插入属性添加到项目中。  首先，您手动可以插入到源代码中。  接下来，您可以将它们使用对象的属性网格在项目。  最后，使用不同的向导，您可以插入记录。  有关使用 " 属性 " 窗口和各个向导的更多信息，请参见 [创建和管理 Visual C\+\+ 项目](../ide/creating-and-managing-visual-cpp-projects.md)。  
  
 启动从 Visual C\+\+ .NET 中，编译器识别属性显示在源文件中并可以在编译时动态地分析和验证它们。  
  
 ，在中，，在项目生成前，编译器分析每个 C\+\+ 源文件，生成对象文件。  但是，在中，当编译器遇到属性时，它将分析和语法上可以通过验证。  编译器动态然后调用属性提供程序插入代码或进行其他修改在编译时。  该提供程序的实现基于属性的类型不同。  例如， ATL 相关的属性。 Atlprov.dll 实现。  
  
 下图演示编译器和属性提供程序之间的关系。  
  
 ![组件特性通信](../windows/media/vccompattrcomm.png "vcCompAttrComm")  
  
> [!NOTE]
>  特性用法不修改源文件的内容。  在调试会话期间，只有当生成的特性代码可见为。  此外，对于在项目中的每个源文件，您可以生成显示属性替换的结果的文本文件。  有关此过程的更多信息，请参见 [\/Fx \(将插入的代码\)](../build/reference/fx-merge-injected-code.md) 和 [调试注入的代码](../Topic/How%20to:%20Debug%20Injected%20Code.md)。  
  
 象大多数 C\+\+ 构造，属性具有定义它们正确使用的设置属性。  这将在每个特性的属性上下文表中引用属性的上下文和解决参考主题。  例如， [coclass](../windows/coclass.md) 特性只能应用于现有的类或结构，与 [cpp\_quote](../windows/cpp-quote.md) 属性相反，可以任意位置在 c. C\+\+ 源文件中插入。  
  
## 请参阅  
 [Concepts](../windows/attributed-programming-concepts.md)