---
title: "创建纯资源 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], 创建"
  - "纯资源 DLL [C++], 创建"
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 创建纯资源 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

纯资源 DLL 是仅包含资源（如图标、位图、字符串和对话框）的 DLL。  使用纯资源 DLL 是在多个程序之间共享同一组资源的好方法。  提供其资源被针对多种语言进行本地化的应用程序也是一种好方法（请参见 [MFC 应用程序中的本地化资源：附属 DLL](../build/localized-resources-in-mfc-applications-satellite-dlls.md)）。  
  
 若要创建纯资源 DLL，请创建一个新的 Win32 DLL（非 MFC）项目，并将资源添加到此项目。  
  
-   在**“新建项目”**对话框中选择“Win32 项目”，并在“Win32 项目向导”中指定 DLL 项目类型。  
  
-   为 DLL 创建一个包含资源（如字符串或菜单）的新资源脚本，并保存该 .rc 文件。  
  
-   在**“项目”**菜单上单击**“添加现有项”**，然后在项目中插入这个新的 .rc 文件。  
  
-   指定 [\/NOENTRY](../build/reference/noentry-no-entry-point.md) 链接器选项。\/NOENTRY 防止链接器将 \_main 引用链接到 DLL 中；此选项是创建纯资源 DLL 所必需的。  
  
-   生成 DLL。  
  
 使用纯资源 DLL 的应用程序应调用 **LoadLibrary** 来[显式链接到 DLL](../build/loadlibrary-and-afxloadlibrary.md)。  若要访问资源，请调用一般函数 **FindResource** 和 **LoadResource**，这两个函数对任何类型的资源都有效，或调用下列资源特定的函数之一：  
  
-   `FormatMessage`  
  
-   **LoadAccelerators**  
  
-   `LoadBitmap`  
  
-   `LoadCursor`  
  
-   `LoadIcon`  
  
-   `LoadMenu`  
  
-   `LoadString`  
  
 使用完资源后，应用程序应调用 **FreeLibrary**。  
  
## 您想进一步了解什么？  
  
-   [DELETE\_PENDING\_Editing Resources](http://msdn.microsoft.com/zh-cn/c29d31c7-2d94-40ca-8aa0-c7262883529c)  
  
## 请参阅  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)