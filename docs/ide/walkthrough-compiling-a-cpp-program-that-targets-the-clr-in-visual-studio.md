---
title: "编译面向 CLR 的 c + + 程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
caps.latest.revision: "40"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: eca6960d23c43fbe27d753ab4f79a27dea7bd7e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-compiling-a-c-program-that-targets-the-clr-in-visual-studio"></a>演练：在 Visual Studio 中编译面向 CLR 的 C++ 程序
你可以创建使用.NET 类，并通过使用 Visual Studio 开发环境对其进行编译的 Visual c + + 程序。  
  
 对于此过程可以键入自己的 Visual c + + 程序，或使用的示例程序之一。 我们使用此过程中的示例程序创建一个名为 textfile.txt 文本文件，并将其保存到项目目录。  
  
## <a name="prerequisites"></a>系统必备  
 这些主题假定你了解 c + + 语言的基础知识。  
  
### <a name="to-create-a-new-project-in-visual-studio-and-add-a-new-source-file"></a>在 Visual Studio 中创建新项目并添加一个新的源文件  
  
1.  创建新项目。 在 **“文件”** 菜单上，指向 **“新建”**，然后单击 **“项目”**。  
  
2.  从 Visual c + + 项目类型中，单击**CLR**，然后单击**CLR 空项目**。  
  
3.  键入项目名称。  
  
     默认情况下包含项目的解决方案具有相同的名称为新的项目中，但你可以输入其他名称。 如果你想，可以输入项目的不同位置。  
  
     单击**确定**创建新项目。  
  
4.  如果解决方案资源管理器不可见，请单击**解决方案资源管理器**上**视图**菜单。  
  
5.  向项目添加新源文件：  
  
    -   右键单击**源文件**文件夹在解决方案资源管理器，指向**添加**单击**新项**。  
  
    -   单击**c + + 文件 (.cpp)**并键入文件名，然后单击**添加**。  
  
     **.Cpp**文件将显示在**源文件**在解决方案资源管理器和选项卡式的窗口中的文件夹将出现代码的键入想要在该文件中。  
  
6.  单击 Visual Studio 中新创建的选项卡中，键入有效的 Visual c + + 程序，或复制并粘贴示例程序之一。  
  
     例如，你可以使用[如何： 编写文本文件 (C + + /cli CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md)示例程序 (在**文件处理和 I/O**节点编程指南)。  
  
     如果你使用的示例程序，请注意，你将`gcnew`关键字而不是`new`创建.NET 对象，并且时`gcnew`返回的句柄 (`^`) 而不是一个指针 (`*`):  
  
     `StreamWriter^ sw = gcnew StreamWriter(fileName);`  
  
     新的 Visual c + + 语法的详细信息，请参阅[运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)。  
  
7.  在 **“生成”** 菜单上，单击 **“生成解决方案”**。  
  
     **输出**窗口显示有关的编译过程，请生成日志和消息，指明生成状态的位置等信息。  
  
     如果进行了更改，而无需执行生成运行程序时，对话框中可以指示项目已过期。 选择在该对话框中的复选框，再单击**确定**如果想要 Visual Studio，始终使用当前版本的文件，而不是提示每次生成应用程序。  
  
8.  上**调试**菜单上，单击**启动但不调试**。  
  
9. 如果你在运行程序时使用的示例程序，则显示命令窗口，指示已创建的文本文件。 按任意键关闭命令窗口。  
  
     **Textfile.txt**文本文件现在位于你的项目目录中。 可以通过使用记事本打开此文件。  
  
    > [!NOTE]
    >  选择空 CLR 项目模板会自动设置**/clr**编译器选项。 要验证这一点，请右键单击中的项目**解决方案资源管理器**并单击**属性**，，然后检查**公共语言运行时支持**中选项**常规**节点**配置属性**。  
  
## <a name="whats-next"></a>下一步  
 **上一步：** [演练： 编译本机 c + + 程序命令行上](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)&#124;**下一步：**[演练： 编译 C 程序命令行上](../build/walkthrough-compile-a-c-program-on-the-command-line.md)  
  
## <a name="see-also"></a>请参阅  
 [C + + 语言参考](../cpp/cpp-language-reference.md)   
 [生成 C/C++ 程序](../build/building-c-cpp-programs.md)