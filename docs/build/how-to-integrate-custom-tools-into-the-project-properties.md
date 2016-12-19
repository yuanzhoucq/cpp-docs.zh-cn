---
title: "如何：将自定义工具集成到项目属性中 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msbuild.cpp.howto.integratecustomtools"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "msbuild (c++), 如何：集成自定义工具"
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 如何：将自定义工具集成到项目属性中
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以通过创建基础 XML 架构文件，向 Visual Studio**“属性页”**窗口添加自定义工具选项。  
  
 **“属性页”**窗口的**“配置属性”**部分会显示称为“规则”的设置组。  每个规则都包含工具或一组功能的设置。  例如，**“链接器”**规则包含链接器工具的设置。  规则中的设置可以细分为类别。  
  
 本文档说明如何在即定目录中创建包含自定义工具属性的文件，以便这些属性能在 Visual Studio 启动时加载。  有关如何修改该文件的信息，请参见 Visual Studio 项目团队博客上的[Platform Extensibilty Part 2](http://go.microsoft.com/fwlink/?LinkID=191489)。  
  
### 添加或更改项目属性  
  
1.  在 XML 编辑器中创建一个 XML 文件。  
  
2.  将该文件保存在 %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\ 文件夹中。  **“属性页”**窗口中的每个规则都由此文件夹中的一个 XML 文件表示。  确保文件在该文件夹中具有唯一名称。  
  
3.  复制 %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\cl.xml 的内容，将其关闭而不保存更改，然后将内容粘贴到新 XML 文件中。  可以使用任何 XML 架构文件，这只是一个当作模板从其开始的文件。  
  
4.  在新 XML 文件中，可根据要求来修改内容。  确保更改位于文件顶部的**“Rule Name”**和**“Rule.DisplayName”**。  
  
5.  保存所做的更改并关闭该文件。  
  
6.  在 Visual Studio 启动时，会加载 %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\ 中的 XML 文件。  因此，若要测试新文件，请重新启动 Visual Studio。  
  
7.  在**“解决方案资源管理器”**中右击某个项目，然后单击**“属性”**。  在**“属性页”**窗口的左窗格中，验证是否存在具有您的规则名称的新节点。  
  
## 请参阅  
 [MSBuild \(Visual C\+\+\)](../build/msbuild-visual-cpp.md)