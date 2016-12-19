---
title: "如何：创建 CLR 控制台应用程序 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "控制台应用程序, 模板"
  - "CLR 控制台应用程序, 项目模板"
ms.assetid: e89bce3c-706f-4ae0-8a90-cb1a0f674e70
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：创建 CLR 控制台应用程序 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

你可以使用控制台应用程序模板创建已具有基本项目引用和文件的控制台应用程序项目。  
  
 通常，控制台应用程序被编译为独立的可执行文件，但它没有图形用户界面。 用户在命令提示符处运行控制台应用程序并使用命令提示符向正在运行的应用程序发出指令。 在命令提示符处，应用程序还将提供输出信息。 控制台应用程序的即时性使它成为了学习编程技术而不用考虑实现用户界面的绝佳方法。  
  
 当你使用控件台应用程序模板创建项目时，它会自动添加以下引用和文件：  
  
-   以下 .NET Framework 命名空间的参考信息：  
  
    -   [System](https://msdn.microsoft.com/en-us/library/system.appdomainmanager.appdomainmanager.aspx) \- 包含基本类和基类，这些类定义常用值和引用数据类型、事件\/事件处理程序、接口、特性和处理异常。  
  
    -   mscorlib \- 支持 .NET Framework 开发的程序集 DLL。  
  
-   源文件：  
  
    -   控制台（.cpp 文件）\- 主源文件和进入你刚才创建的应用程序的入口点。 它标识项目的 .dll 文件和项目命名空间。 在此文件中提供你自己的代码。  
  
    -   AssemblyInfo.cpp \- 包含可用于修改项目的程序集元数据的特性、文件、资源、类型、版本信息、签名信息等。 有关详细信息，请参阅 [程序集内容](../Topic/Assembly%20Contents.md)。  
  
    -   Stdafx.cpp \- 用于生成名为 Win32.pch 的预编译标头文件和名为 StdAfx.obj 的预编译类型文件。  
  
-   头文件：  
  
    -   Stdafx.h \- 用于生成名为 Win32.pch 的预编译标头文件和名为 StdAfx.obj 的预编译类型文件。  
  
    -   resource.h \- app.rc 的生成的包含文件。  
  
-   资源文件：  
  
    -   app.rc \- 程序的资源脚本文件。  
  
    -   app.ico \- 程序的图标文件。  
  
-   ReadMe.txt \- 描述项目中的文件。  
  
## 创建公共语言运行时 \(CLR\) 控制台应用程序项目  
  
1.  在菜单栏上，依次选择“文件”、“新建”、“项目”。  
  
2.  在**“新建项目”**对话框中的**“已安装的模块”**窗口下，依次选择**“Visual C\+\+”**节点、**“CLR”**节点和“控制台应用程序”模板。  
  
3.  在“名称”框中，输入你的应用程序的唯一名称。  
  
     你可以指定其他项目和解决方案设置，但它们都不是必需的。  
  
4.  选择“确定”按钮。  
  
## 请参阅  
 [NOTINBUILD 如何：创建 CLR 控制台应用程序](http://msdn.microsoft.com/zh-cn/b8af4197-e65f-4b17-b18e-b9e92965d026)   
 [CLR 项目](../ide/files-created-for-clr-projects.md)   
 [NIB：项目中的项管理](http://msdn.microsoft.com/zh-cn/762e606b-7f44-4b66-97a1-e30a703654a0)