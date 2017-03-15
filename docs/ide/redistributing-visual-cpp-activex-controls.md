---
title: "重新分发 Visual C++ ActiveX 控件 | Microsoft Docs"
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
  - "控件 [C++], 分发"
  - "控件 [C++], 重新分发"
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 重新分发 Visual C++ ActiveX 控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 6.0 提供可在应用程序中使用然后重新发布的 ActiveX 控件。  Visual C\+\+ 中不再包括这些控件。  按照 Visual C\+\+ 6.0 的许可协议，可以与在 Visual C\+\+ 中开发的应用程序一起重新发布这些控件。  
  
> [!NOTE]
>  Microsoft 不再支持 Visual C\+\+ 6.0。  
  
 有关可重新发布的 Visual C\+\+ 6.0 ActiveX 控件的列表，请参见 Visual C\+\+ 6.0 产品 CD 的第一张光盘上的 Common\\Redist\\Redist.txt。  
  
 在分发应用程序时，必须（使用 Regsvr32.exe）为 ActiveX 控件安装和注册 .ocx。  此外，应确保目标计算机有下列系统文件的当前版本（星号指出需要注册的文件）：  
  
-   Asycfilt.dll  
  
-   Comcat.dll \*  
  
-   Oleaut32.dll \*  
  
-   Olepro32.dll \*  
  
-   Stdole2.tlb  
  
 如果这些 DLL 在目标系统中不可用，则需要使用为更新相应的操作系统所规定的机制更新它们。  可以从 [http:\/\/windowsupdate.microsoft.com](http://windowsupdate.microsoft.com) 下载 Windows 操作系统的最新 Service Pack。  
  
 如果应用程序使用一个与数据库连接的 ActiveX 控件，则必须在目标系统上安装 Microsoft 数据访问组件 \(MDAC\)。  有关更多信息，请参见[重新发布数据库支持文件](../ide/redistributing-database-support-files.md)。  
  
 在使用与数据库连接的 ActiveX 控件时，还需要复制目标计算机上的数据源名称。  可以用函数（如 `ConfigDSN`）以编程方式来完成此操作。  
  
 一些可重新发布的 ActiveX 控件还有附加依赖项。  对于 Visual C\+\+ 6.0 产品 CD 中的 Os\\System 文件夹中的每个 .ocx 文件，还有一个 .dep 文件。  对于要重新发布的每个 .ocx 文件，请在相应的 .dep 文件中查找一个或多个 USES 项。  如果列出了某文件，则必须确保该文件出现在目标计算机上。  直接支持 .ocx 文件的任何 DLL 都需要注册。  （为使 Regsvr32.exe 成功，目标计算机必须首先包含控件静态加载的所有 DLL。）而且，如果作为依赖项列出的 DLL 在 Visual C\+\+ 6.0 CD 中的 Os\\System 文件夹中也有 .dep 文件，则还必须研究该 .dep 文件中的 USES 项。  
  
## 请参阅  
 [重新分发 Visual C\+\+ 文件](../ide/redistributing-visual-cpp-files.md)