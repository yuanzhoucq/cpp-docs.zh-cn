---
title: "MFC DLL 命名约定 | Microsoft Docs"
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
  - "DLL [C++], 库名"
  - "DLL [C++], 命名规则"
  - "库 [C++], MFC DLL 名称"
  - "MFC DLL [C++], 命名规则"
  - "MFC 库 [C++], 命名规则"
  - "命名规则 [C++], MFC DLL"
  - "共享的 DLL 版本 [C++]"
ms.assetid: 0db9c3f3-87d3-40e8-8964-250f9d2a2209
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# MFC DLL 命名约定
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 中包含的 DLL 和库遵循结构化命名约定。  这使了解应为什么目的使用哪个 DLL 或库变得更容易。  
  
 生成使用这些 DLL 的应用程序或扩展 DLL 所需的导入库与 DLL 具有相同的基名称，但带有 .lib 文件扩展名。  
  
### 共享 DLL 命名约定  
  
|DLL|说明|  
|---------|--------|  
|MFCx0.DLL|MFC DLL，ANSI 发布版本|  
|MFCx0U.DLL|MFC DLL，Unicode 发布版本|  
|MFCx0D.DLL|MFC DLL，ANSI 调试版本|  
|MFCx0UD.DLL|MFC DLL，Unicode 调试版本|  
  
 如果动态链接到 MFC 的共享 DLL 版本，则不论该版本来自应用程序还是扩展 DLL，都必须在产品中包括 MFCx0.DLL。  如果应用程序中需要 Unicode 支持，则改为包括 MFCx0U.DLL。  
  
 如果将 DLL 静态链接到 MFC，则必须将它与一个静态 MFC 库链接。  这些版本根据 \[N&#124;U\]AFXCW\[D\].LIB 约定进行命名。  有关更多信息，请参见[库命名约定](../mfc/library-naming-conventions.md) \(MFC\) 中的“静态链接库命名约定”表。  
  
 有关可随应用程序一同发布的 Visual C\+\+ DLL 列表，请参见 Visual Studio 安装目录中的 Redist.txt。  
  
## 您想进一步了解什么？  
  
-   [库的命名约定](../mfc/library-naming-conventions.md)  
  
## 请参阅  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)