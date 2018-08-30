---
title: 如何： 创建 CLR 控制台应用程序 (C + + CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- console applications, templates
- CLR console applications, project template
ms.assetid: e89bce3c-706f-4ae0-8a90-cb1a0f674e70
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 60804b3863a4b44bc963f289b1d6a8c2f2d5cbf7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211152"
---
# <a name="how-to-create-clr-console-applications-ccli"></a>如何：创建 CLR 控制台应用程序 (C++/CLI)
你可以使用控制台应用程序模板创建已具有基本项目引用和文件的控制台应用程序项目。  
  
 通常，控制台应用程序被编译为独立的可执行文件，但它没有图形用户界面。 用户在命令提示符处运行控制台应用程序并使用命令提示符向正在运行的应用程序发出指令。 在命令提示符处，应用程序还将提供输出信息。 控制台应用程序的即时性使它成为了学习编程技术而不用考虑实现用户界面的绝佳方法。  
  
 当你使用控件台应用程序模板创建项目时，它会自动添加以下引用和文件：  
  
-   以下 .NET Framework 命名空间的参考信息：  
  
    -   [系统](https://msdn.microsoft.com/library/system.appdomainmanager.appdomainmanager.aspx)-包含基本类和基类，这些类用于定义常用使用值和引用数据类型、 事件和事件处理程序、 接口、 属性和处理异常。  
  
    -   mscorlib - 支持 .NET Framework 开发的程序集 DLL。  
  
-   源文件：  
  
    -   控制台（.cpp 文件）- 主源文件和进入你刚才创建的应用程序的入口点。 它标识项目的 .dll 文件和项目命名空间。 在此文件中提供你自己的代码。  
  
    -   AssemblyInfo.cpp - 包含可用于修改项目的程序集元数据的特性、文件、资源、类型、版本信息、签名信息等。 有关详细信息，请参阅[程序集内容](/dotnet/framework/app-domains/assembly-contents)。  
  
    -   Stdafx.cpp - 用于生成名为 Win32.pch 的预编译标头文件和名为 StdAfx.obj 的预编译类型文件。  
  
-   头文件：  
  
    -   Stdafx.h - 用于生成名为 Win32.pch 的预编译标头文件和名为 StdAfx.obj 的预编译类型文件。  
  
    -   resource.h - app.rc 的生成的包含文件。  
  
-   资源文件：  
  
    -   app.rc - 程序的资源脚本文件。  
  
    -   app.ico - 程序的图标文件。  
  
-   ReadMe.txt - 描述项目中的文件。  
  
## <a name="to-create-a-common-language-runtime-clr-console-app-project"></a>创建公共语言运行时 (CLR) 控制台应用程序项目  
  
1.  在菜单栏上，依次选择“文件” 、“新建” 、“项目” 。  
  
2.  在 **“新建项目”** 对话框中的 **“已安装的模块”** 窗口下，依次选择 **“Visual C++”** 节点、 **“CLR”** 节点和“控制台应用程序”模板。  
  
3.  在“名称”  框中，输入你的应用程序的唯一名称。  
  
     你可以指定其他项目和解决方案设置，但它们都不是必需的。  
  
4.  选择“确定”  按钮。  
  
## <a name="see-also"></a>请参阅  
 [CLR 项目](../ide/files-created-for-clr-projects.md)   


