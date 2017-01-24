---
title: "演练：创建 Win32 控制台程序 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "vcfirstapp"
  - "vccreatefirst"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令行应用程序 [C++], 标准"
  - "标准应用程序 [C++]"
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
caps.latest.revision: 36
caps.handback.revision: 36
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：创建 Win32 控制台程序 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用 Visual C\+\+ 在 Visual Studio 集成开发环境 \(IDE\) 中创建标准 C\+\+ 程序。  通过采用此演练中的步骤，您可以创建一个项目，向该项目添加一个新文件，修改该文件以添加 C\+\+ 代码，然后使用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 编译并运行程序。  
  
 您可以键入自己的 C\+\+ 程序，或者使用示例程序之一。  此演练中的示例程序是一个控制台应用程序。  此应用程序使用标准模板库 \(STL\) 中的 `set` 容器。  
  
 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 使用 2003 C\+\+ 标准进行编译，但有以下几点主要例外之处：两阶段名称查找、异常规范和导出。  此外，[!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 支持若干 C\+\+0x 功能，例如，lambda、自动、static\_assert、rvalue 引用和 extern 模板。  
  
> [!NOTE]
>  如果要求符合标准，请使用 **\/Za** 编译器选项来禁用对该标准的 Microsoft 扩展。  有关详细信息，请参阅[\/Za、\/Ze（禁用语言扩展）](../build/reference/za-ze-disable-language-extensions.md)。  
  
## 系统必备  
 若要完成本演练，你必须了解 C\+\+ 语言的基础知识。  
  
### 创建项目并添加源文件  
  
1.  通过以下方式创建一个项目：指向**“文件”**菜单上的**“新建”**，然后单击**“项目”**。  
  
2.  在**“Visual C\+\+”**项目类型窗格中，单击**“Win32”**，然后单击**“Win32 控制台应用程序”**。  
  
3.  键入项目名称。  
  
     默认情况下，包含项目的解决方案与项目同名，但您可以键入其他名称。  您也可以为项目键入其他位置。  
  
     单击“确定”创建项目。  
  
4.  在**“Win32 应用程序向导”**中，单击**“下一步”**，选择**“空项目”**，然后单击**“完成”**。  
  
5.  如果未显示**“解决方案资源管理器”**，请在**“视图”**菜单上，单击**“解决方案资源管理器”**。  
  
6.  将一个新源文件添加到项目，如下所示。  
  
    1.  在**“解决方案资源管理器”**中，右击**“源文件”**文件夹，指向**“添加”**，然后单击**“新建项”**。  
  
    2.  在**“代码”**节点中单击**“C\+\+ 文件\(.cpp\)”**，为文件键入名称，然后单击**“添加”**。  
  
     该 .cpp 文件即显示在**“解决方案资源管理器”**中的“源文件”文件夹中，并且文件将在 Visual Studio 编辑器中打开。  
  
7.  在编辑器内的文件中，键入使用标准 C\+\+ 库的有效 C\+\+ 程序，或者复制示例程序之一并将其粘贴在文件中。  
  
     例如，您可以使用 [set::find](../misc/set-find-stl-samples.md)示例程序，该程序是帮助中附带的标准模板库示例之一。  
  
     如果使用该示例程序，请注意 `using namespace std;` 指令。  此指令使程序能够使用 `cout` 和 `endl`，而无需完全限定名（`std::cout` 和 `std::endl`）。  
  
8.  保存该文件。  
  
9. 在**“生成”**菜单上，单击**“生成解决方案”**。  
  
     **“输出”**窗口显示有关编译过程的信息，例如，生成日志的位置，以及指示生成状态的消息。  
  
10. 在**“调试”**菜单上，单击**“开始执行\(不调试\)”**。  
  
     如果使用了示例程序，将显示一个命令窗口，其中显示是否在集合中找到了特定的整数。  
  
## 后续步骤  
 **上一部分：** [Creating Command\-Line Applications \(C\+\+\)](http://msdn.microsoft.com/zh-cn/2505d9ed-aca4-426a-9071-078a2d707254)。  **下一部分：** [演练：在命令行上编译本机 C\+\+ 程序](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)。  
  
## 请参阅  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/zh-cn/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [C\+\+ 语言参考](../cpp/cpp-language-reference.md)   
 [C\+\+ 标准库](../standard-library/cpp-standard-library-reference.md)