---
title: "Windows 桌面应用程序 (Visual C++) | Microsoft Docs"
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
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
caps.latest.revision: 17
caps.handback.revision: 12
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Windows 桌面应用程序 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当你想创建具有基于窗口的用户界面且能在从 Windows XP 到 Windows 10 版本的 Windows 桌面上运行的本机桌面应用程序时，可以创建 Windows 桌面应用程序。  
  
 *Windows 桌面应用程序*（有时为阐释 Win32 应用程序而提及）是一个惯例术语，指那些使用消息循环直接处理 Windows 消息而不使用 Microsoft 基础类 \(MFC\)、活动模板库 \(ATL\) 或 .NET Framework 等框架的应用程序。 使用 C\+\+ 的 Windows 桌面应用程序可使用 C 运行库 \(CRT\) 及标准模板库 \(STL\) 类和函数、COM 对象、任意公共 Windows 函数，它们统称 Windows API。 有关使用 C\+\+ 的 Windows 桌面应用程序，请参阅[了解如何使用 C\+\+ 编写适用于 Windows 的程序](http://go.microsoft.com/fwlink/p/?LinkId=262281)。  
  
 Windows 桌面应用程序是创建适用于 Windows 的本机桌面应用程序的一种方法；另一种方法是 MFC 应用程序。 MFC 是具有众多用户界面控件或自定义用户控件的应用（尤其是企业行应用）的默认选择。 MFC 可提供用于序列化、文本操作、打印和功能区等现代用户界面元素的帮助程序类。 这些类对于 Windows 桌面应用程序不可用。  
  
## 相关文章  
  
|标题|说明|  
|--------|--------|  
|[Windows 开发](http://go.microsoft.com/fwlink/p/?LinkId=262282)|包含有关 Windows API 和 COM 的信息。 （某些 Windows API 和第三方 DLL 是作为 COM 对象实现的。）|  
|[Hilo：开发适用于 Windows 7 的 C\+\+ 应用程序](http://go.microsoft.com/fwlink/p/?LinkId=262284)|描述如何创建使用 Windows Animation 和 Direct2D 创建基于传送的用户界面的、客户端丰富的 Windows 桌面应用程序。|  
|[控制台应用程序](../windows/console-applications-in-visual-cpp.md)|包含有关控制台应用的信息。 Win32（或 Win64）控制台应用程序本身不具有窗口，且不使用消息循环。 它在控制台窗口中运行，并通过命令行处理输入和输出。|  
|[Visual C\+\+](../top/visual-cpp-in-visual-studio-2015.md)|描述 Visual C\+\+ 在 Visual Studio 中的主要功能，并链接到 Visual C\+\+ 文档的剩余部分。|  
|MSDN 网站上的 [Visual C\+\+ 开发人员中心](http://go.microsoft.com/fwlink/p/?LinkId=252885)|包含 Windows 桌面应用程序相关的教程、博客文章和论文。|  
|[如何：在 Windows 桌面应用程序中使用 Windows 10 SDK](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|包含使用 Windows 10 SDK 设置项目以便生成的步骤。|