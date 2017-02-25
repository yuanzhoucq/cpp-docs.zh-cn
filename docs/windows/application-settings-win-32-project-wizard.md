---
title: "Win 32 项目向导的应用程序设置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.win32.appset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序设置 [C++]"
  - "Win32 项目向导，应用程序设置"
ms.assetid: d6b818f0-9b23-4793-a6c5-df1c8c594bad
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Win 32 项目向导的应用程序设置
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用此向导页设置 Win32 项目选项。  
  
 **应用程序类型**  
 创建指定的应用程序类型。  
  
|选项|说明|  
|--------|--------|  
|**控制台应用程序**|创建控制台应用程序。  控制台程序是用[控制台函数](https://msdn.microsoft.com/en-us/library/ms813137.aspx)开发的，这些函数在控制台窗口中提供字符模式支持。  Visual C\+\+ [运行库](../c-runtime-library/c-run-time-library-reference.md)还利用标准 I\/O 函数（如 **printf\_s\(\)** 和 **scanf\_s\(\)**）提供控制台窗口的输出和输入。  控制台应用程序没有图形用户界面。  它编译成 .exe 文件并且可以作为独立应用程序从命令行运行。<br /><br /> 可以向控制台应用程序添加 MFC 和 ATL 支持。|  
|**Windows 应用程序**|创建 Win32 程序。  Win32 程序是用 C 或 C\+\+ 编写的可执行应用程序 \(EXE\)，使用 Win32 API 调用创建图形用户界面。<br /><br /> 不能向 Windows 应用程序添加 MFC 和 ATL 支持。|  
|**DLL**|创建 Win32 动态链接库 \(DLL\)。  Win32 DLL 是用 C 或 C\+\+ 编写的二进制文件，使用 Win32 API 调用而不是 MFC 类调用，并且用作可同时被多个应用程序使用的共享函数库。<br /><br /> 不能向 DLL 应用程序添加 MFC 和 ATL 支持。  可以指示 DLL 导出符号。|  
|**静态库**|创建静态库。  静态库是包含生成可执行文件时链接到程序中的对象及其函数和数据的文件。  该主题解释如何创建静态库的起始文件和[项目属性](../ide/property-pages-visual-cpp.md)。  静态库文件有以下优点：<br /><br /> -   如果处理的应用程序调用的是 Win32 API 而不是 MFC 类，则 Win32 静态库很有用。<br />-   不论 Windows 应用程序的其余部分是用 C 还是用 C\+\+ 编写的，链接过程都相同。<br />-   可以将静态库链接到基于 MFC 的程序或者非 MFC 程序。|  
  
 **附加选项**  
 根据应用程序的类型定义应用程序的支持和选项。  
  
|选项|说明|  
|--------|--------|  
|**空项目**|指定项目文件为空。  如果有一套源代码文件（如 .cpp 文件、头文件、图标、工具栏、对话框，等等）并且需要在 Visual C\+\+ 开发环境中创建项目，则必须首先创建一个空项目，然后向该项目中添加文件。<br /><br /> 此选项对静态库项目不可用。|  
|**导出符号**|指定 DLL 项目导出符号。|  
|**预编译头**|指定静态库项目使用预编译头。|  
|安全开发生命周期 \(SDL\)检测|有关 SDL 的更多信息，请参见 [Microsoft Security Development Lifecycle \(SDL\)  Process Guidance](84aed186-1d75-4366-8e61-8d258746bopq)。|  
  
 **添加支持，以用于**  
 为 Visual C\+\+ 中提供的某个库提供支持。  
  
|选项|说明|  
|--------|--------|  
|**ATL**|在项目中内置活动模板库 \(ATL\) 类支持。  仅限 Win32 控制台应用程序。<br /><br /> **注意** 此选项不表示支持使用 ATL 代码向导添加 ATL 对象。  只能将 ATL 对象添加到 ATL 项目或者具有 ATL 支持的 MFC 项目。|  
|**MFC**|生成 Microsoft 基础类 \(MFC\) 库支持。  仅限 Win32 控制台应用程序和静态库。|  
  
## 请参阅  
 [Win32 应用程序向导](../windows/win32-application-wizard.md)   
 [如何：创建 Windows 桌面应用程序](../Topic/How%20to:%20Create%20a%20Windows%20Desktop%20Application.md)