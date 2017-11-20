---
title: "Win 32 项目向导的应用程序设置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.win32.appset
dev_langs: C++
helpviewer_keywords:
- application settings [C++]
- Win32 Project Wizard, application settings
ms.assetid: d6b818f0-9b23-4793-a6c5-df1c8c594bad
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f18b0690b6205f8e7b0f07fdfa6f0b88c75a3a91
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="application-settings-win-32-project-wizard"></a>Win 32 项目向导的应用程序设置
使用向导的此页为 Win32 项目设置选项。  
  
 **应用程序类型**  
 创建指定的应用程序类型。  
  
|选项|描述|  
|------------|-----------------|  
|**控制台应用程序**|创建控制台应用程序。 使用开发的控制台程序[控制台函数](https://msdn.microsoft.com/en-us/library/ms813137.aspx)，它提供的信息在控制台窗口中的字符模式支持。 Visual c + +[运行时库](../c-runtime-library/c-run-time-library-reference.md)还提供输出并输入从控制台窗口与标准 I/O 函数，如**printf_s()**和**scanf_s()**。 一个控制台应用程序有没有图形用户界面。 它将编译为一个.exe 文件，并可以作为独立的应用程序从命令行运行。<br /><br /> 你可以添加 MFC 和 ATL 支持到控制台应用程序。|  
|**Windows 应用程序**|创建 Win32 程序。 Win32 程序是用 C 或 c + +，使用 Win32 api 调用创建的图形用户界面编写的可执行应用 (EXE)。<br /><br /> 无法添加 MFC 或 ATL 支持到 Windows 应用程序。|  
|**DLL**|创建 Win32 动态链接库 (DLL)。 Win32 DLL 是用 C 或 c + +，使用调用 Win32 API，而不是 MFC 类，以及作为多个应用程序可同时使用的函数的共享库中编写的二进制文件。<br /><br /> 无法添加 MFC 或 ATL 支持到 DLL 应用程序。 你可以指示 DLL 导出符号。|  
|**静态库**|创建一个静态库。 静态库是一个包含对象及其函数和生成的可执行文件时，链接到你的程序的数据文件。 本主题说明如何创建初学者文件和[项目属性](../ide/property-pages-visual-cpp.md)为静态库。 静态库文件提供以下好处：<br /><br /> -A Win32 静态库是如果您正在使用的应用程序执行调用 Win32 API，而不是 MFC 类很有用。<br />不论你的 Windows 应用程序的其余部分编写 C 或 c + +，-链接的过程都是相同的。<br />-你可以将静态库链接到一个基于 MFC 的程序或非 MFC 程序。|  
  
 **其他选项**  
 定义的支持和应用程序，具体取决于其类型的选项。  
  
|选项|描述|  
|------------|-----------------|  
|**空项目**|指定项目文件为空。 如果你有一套 （如.cpp 文件、 头文件、 图标、 工具栏、 对话框框中和等等） 的源代码文件，并想要在 Visual c + + 开发环境中创建一个项目，你必须首先创建一个空白项目，然后将文件添加到项目。<br /><br /> 对于静态库项目，选择此选项不可用。|  
|**导出符号**|指定 DLL 项目导出符号。|  
|**预编译头**|指定的静态库项目使用预编译标头。|  
|安全开发生命周期 (SDL) 检查|有关 SDL 的详细信息，请参阅[Microsoft 安全开发生命周期 (SDL) 过程指南](../build/reference/sdl-enable-additional-security-checks.md)|  
  
 **添加对的支持**  
 添加对其中一个提供 Visual c + + 库支持。  
  
|选项|描述|  
|------------|-----------------|  
|**ATL**|将嵌入到类中活动模板库 (ATL) 中的项目支持。 适用于仅 Win32 控制台应用。<br /><br /> **请注意**此选项并不表示对使用 ATL 的 ATL 对象代码向导添加的支持。 你可以仅向 ATL 项目添加 ATL 对象或与 ATL 的 MFC 项目支持。|  
|**MFC**|将嵌入到 Microsoft 基础类 (MFC) 库的项目支持。 Win32 控制台应用程序和仅限静态库。|  
  
## <a name="see-also"></a>另请参阅  
 [Win32 应用程序向导](../windows/win32-application-wizard.md)   
