---
title: "Visual Studio 中的清单生成 | Microsoft Docs"
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
  - "清单 [C++]"
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Visual Studio 中的清单生成
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在项目的**“属性页”**对话中，可以控制生成特定项目的清单文件。  在**“配置属性”**选项卡上，单击**“链接器”**，再单击**“清单文件”**，然后单击**“生成清单”**。  默认情况下，新项目的项目属性会设置为生成清单文件。  但是，通过使用项目的**“生成清单”**属性，也可以禁用项目清单的生成。  当将此属性设置为**“是”**时，将生成该项目的清单。  否则，当链接器解析应用程序代码间的依赖关系时，将忽略程序集信息，且不会生成清单。  
  
 Visual Studio 中的生成系统允许将清单嵌入最终的二进制应用程序文件中，或生成为外部文件。  此行为由**“项目属性”**对话中的**“嵌入清单”**选项控制。  若要对此属性进行设置，请打开**“清单工具”**节点，然后选择**“输入和输出”**。  如果不嵌入清单，则它将被生成为外部文件，并保存在最终的二进制文件所在的目录中。  如果嵌入清单，则 Visual Studio 将使用以下过程嵌入最终清单：  
  
1.  将源代码编译为对象文件后，链接器将收集依赖程序集信息。  在链接最终二进制文件时，链接器会生成一个中间清单，稍后该清单将用于生成最终清单。  
  
2.  生成中间清单并完成链接后，将执行清单工具以合并成一个最终清单，并将它另存为外部文件。  
  
3.  然后，项目生成系统将进行检测，确定在由清单工具生成的清单中，其信息是否有别于已嵌入二进制文件中的清单所包含的信息。  
  
4.  如果二进制文件中嵌入的清单不同于清单工具生成的清单，或二进制文件中不包含嵌入的清单，则 Visual Studio 将再次调用链接器，将外部清单文件作为资源嵌入到二进制文件中。  
  
5.  如果二进制文件中嵌入的清单与清单工具生成的清单相同，则生成系统将继续下面的生成步骤。  
  
 清单会作为文本资源嵌入到最终二进制文件中，您可通过在 Visual Studio 中将最终二进制文件作为文件打开来查看该清单。  若要确保清单指向正确的库，请按照 [了解 Visual C\+\+ 应用程序的依赖项](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md) 中描述的步骤或[疑难解答](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)部分中介绍的建议进行操作。  
  
## 请参阅  
 [如何：将清单嵌入到 C\/C\+\+ 应用程序](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md)   
 [私有程序集](_win32_private_assemblies)   
 [清单工具](http://msdn.microsoft.com/library/aa375649)   
 [了解 C\/C\+\+ 程序的清单生成](../build/understanding-manifest-generation-for-c-cpp-programs.md)